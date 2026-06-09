# SSH 登设备做诊断（三层最小权限）

平台聚合数据不够、需要进设备内部拉日志/跑命令时用本文。**遵循最小权限**：能在上一层解决就不要往下走。

```
Layer 0  平台侧聚合（不进设备）   ← 先看 references/diagnostics.md，绝大多数排查到此为止
Layer 1  SSH 隧道 + 普通(limited) shell   ← 要看设备实时日志/模块状态时，默认走这层
Layer 2  SSH 隧道 + root shell             ← 仅当普通 shell 的 show 拿不到所需时才升级
```

> **`router exec` 不可用**：`inconnect router exec <id> <cmd>` 走 task type=2，CLI 能发、平台返 200，但**设备端 mqttagent 没有这个命令处理器**，任何命令都回 `data.response="handle ... failed"`、`state=-1`。要在设备上跑命令做诊断，**唯一可用路径是 SSH 隧道**。

---

## Layer 0：先穷尽平台侧

进设备前，先确认 `references/diagnostics.md` 里的平台聚合手段（router diagnose / connection-events / connection-log / vpn-event / 服务器日志 / 信号）都不够用。设备离线时根本进不去，只能靠 Layer 0。

---

## 开隧道（Layer 1/2 的共同前提）

```bash
inconnect router ssh <设备id> --server <ngrok:port> --oid <oid>
# 例：inconnect router ssh 675924... --server ngrok.10.5.17.73.nip.io:4443 --oid 6759...
```

输出里取两样：
- **Tunnel ID**（32 位小写 hex 的 uuid）—— 关隧道要用
- **Connect** 字符串 —— 形如 `ssh <uuid>+adm@<ngrok-host>`

**隧道生命周期 = 设备侧 keepalive 300s**：
- 开完隧道必须 **5 分钟内连进去并保持流量**，否则隧道连同 URL 一起消失（再连会 AuthenticationException）。
- 危险窗口只在「开隧道 → 首次连上」之间。脚本要拿到 URL 后**立即**连，中间别穿插别的等待。
- 会话一旦建立，命令交互/keepalive 包会持续重置计时器，长会话没问题；长时间「等响应」的操作要开 SSH 心跳（ServerAliveInterval）。

**连接方式**：ngrok proxy 按用户名里的 `<uuid>+` 前缀路由，`+` 后面才是 dropbear 真正的用户名。
```bash
ssh <uuid>+adm@<ngrok-host>      # dropbear 账号 adm，口令向用户索取
```
> dropbear 账号/口令是设备本地账号，**平台不存**，每次向用户索取。

**拉完即关**（省 keepalive、释放端口）：
```bash
inconnect router tunnel-close <uuid>
```
对已关闭/未知 uuid 幂等（返回 NotFound，不报错）。

---

## Layer 1：普通(limited) shell —— 诊断主力，无需 root

连上后是 InOS limited shell，提示符 `Router>`。它**只读**：`cat`/`ls`/`grep`/`whoami` 全回 `% 不支持的命令!`，**不能读任意文件、不能过滤**。但自带一套面向诊断的 `show` 子命令，**绝大多数日志/状态诊断到这层就够**。

| 命令 | 用途 |
|---|---|
| `show log lines <n>` | **★诊断主力★** 最近 n 行 syslog（tail 语义），内容**与 `/var/log/messages` 完全一致** |
| `show log` | 不带参数 = 吐 in-memory 全缓冲（几百~上千行，可能很大） |
| `show version` | 型号/序列号/固件/Bootloader |
| `show system` | 一行：uptime + load average |
| `show modem` | 蜂窝模块：型号、状态、信号(asu)、注册、IMSI/IMEI、4G |
| `show users` | 当前登录用户 |
| `show interface` / `show ip` / `show route` / `show arp` / `show clock` | 网络/时钟状态 |
| `show diagnose` | **❌ 别用** —— 吐 `$AES$` 约 169KB 加密大 blob（给官方支持上传解密用），加密且爆上下文，对诊断零价值 |

- **`show log lines <n>` 是核心原语**：要读当前日志根本不用进 root。实测 lines 5/30/500 逐级回溯。
- syslog 常见来源：`ngrok[...]`（状态机 Init→Config→Connecting→Connected / "ngrok exit" / "ngremote got an error"）、`mqttagent[...]`（task notice / cellular health / 流量）、`dropbear[...]`（连接 / auth / exit）、`crond`。
- limited shell 命令集（banner 列 11 个）：`help language show exit ping comredirect telnet ssh traceroute enable terminal`。

---

## Layer 2：root shell —— 仅在 Layer 1 不够时升级

**何时升级**（普通 shell 的 `show` 拿不到所需）：
1. 要 grep/过滤日志（普通 shell 只能整段 dump，靠 LLM 肉眼筛）；
2. 看滚动历史 `/var/log/messages.0`（`show log` 只覆盖当前缓冲）；
3. 读任意配置/状态文件；
4. 抓 ps / netstat / conntrack 等 `show` 没覆盖的明细。

root 是高敏盲输口令操作，能不用就不用。

**进 root 的精确序列**（在 `Router>` 提示符下）：
```
support enable            ← 隐藏命令，完全静默：无回显、无提示、提示符不变
<设备 root 口令>           ← 紧接着【直接盲输 root 口令】，设备不打印 "Password:"，向用户索取
/www #                    ← 拿到 root（BusyBox v1.26.2 ash）
```

**陷阱（务必记牢）**：
- **`support enable` 是静默密码门**：输完它**下一行直接盲输 root 口令**，中间**不要**等任何提示符。脚本里 `support enable\n` 后紧跟 `<root_pw>\n`。
- **不要走 `enable`**：`enable` 是 InOS 标准特权模式，会弹「请输入密码:」，但那要的是 enable-mode 口令，**输 root 口令会回 "% 密码错误"**。root shell 不经过 `enable`。
- BusyBox **没有 `whoami`、没有 `id`**。确认 root 看 `/www #` 提示符即可，或 `cat /proc/self/status`。
- 日志在 `/var/log/messages`（+ 滚动 `messages.0`）。内核 Linux 3.10.14 / Buildroot 2015.11。

---

## paramiko 自动化要点（如需脚本拉日志）

```python
# 1) 先 inconnect router ssh <id> --server <ngrok:port> 拿 uuid，立即连（5 分钟窗口）
# 2) cli.connect(host, port=22, username=uuid+"+adm", password=<dropbear口令>,
#                look_for_keys=False, allow_agent=False)
# 3) Layer 1：invoke_shell 后 send("show log lines 200\n")，idle 检测收齐输出
# 4) Layer 2（仅需要时）：send("support enable\n"); sleep(1.0); send(root_pw+"\n")
# 5) Windows：sys.stdout = io.TextIOWrapper(sys.stdout.buffer, encoding="utf-8", errors="replace")
#    否则设备 GBK 输出会触发 UnicodeEncodeError
# 6) 拉完 inconnect router tunnel-close <uuid>
```

---

## 安全注意

- **凭据向用户索取，不要写进脚本/日志/仓库**：dropbear 账号口令、root 口令都是设备侧 secret，平台不存。本文一律用占位符。
- 高敏操作建议留审计：oid / uid / router / 起止时间。
- 22 端口对外暴露在生产需 Security Group / 防火墙 ACL 限源 IP。
- 主机密钥目前为临时（pod 重启即变），客户端会 known_hosts 不匹配，属已知现象。
