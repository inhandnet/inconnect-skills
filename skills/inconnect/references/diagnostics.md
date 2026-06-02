# 路由器离线诊断

路由器掉线/断网/连不上/VPN 认证失败时的排查流程。

## 先分清两层连接

路由器与平台之间有**两条相互独立的连接**，"掉线"要先确定断的是哪一层：

| 层 | 通道 | 数据来源 | 对应命令 |
| --- | --- | --- | --- |
| 管理通道 | MQTT（设备 ↔ 平台） | 设备上下线事件 | `router connection-events` |
| VPN 隧道 | OpenVPN（设备 ↔ VPN 服务器） | 会话日志 / 认证事件 / 服务器日志 | `connection-log` / `vpn-event` / `server logs` |

- 管理通道断 → 平台显示"离线"，远程操作（exec/reboot/web）不可用，但 VPN 隧道可能还在通
- VPN 隧道断 → 设备可能仍"在线"（MQTT 正常），但 VPN 内网络不通、端点访问不了

> 诊断类命令（`router diagnose` / `connection-events` / `connection-log` / `vpn-event` / `server logs`）均需 **admin** 权限。

## 第一步：一键聚合诊断

```bash
inconnect router diagnose <id> [--after <start> --before <end>] --oid <oid>
```

一条命令聚合该路由器的多源诊断数据，输出分区块 JSON：

- `router` — 路由器详情（在线状态、型号、子网等）
- `connectionLogs` — VPN 会话日志（连接/断开、时长、字节数、虚拟 IP）
- `vpnEvents` — VPN 认证/连接事件（含 `auth_failed` 及原因，如 `invalid_cert`）
- `connectionEvents` — 设备 MQTT 上下线事件（含断开原因 `timeout` / `kicked`）
- `registerEvents` — 设备注册事件

某个数据源查询失败时降级为空数组并在 stderr 打 warning，不中断整体输出。先跑它拿全貌，再按下面的分层步骤深挖可疑的那一层。

## 分层排查

### 1. 确认路由器状态

```bash
inconnect router get <id> --oid <oid> --verbose 100
```

关注字段：

- `online`：当前是否在线（这是最后一次上报的快照，离线后不反映实时）
- `lastSeen` / `updatedAt`：最后在线时间
- `model`：型号
- `subnet` / VPN 相关字段：VPN 组网是否正常

### 2. 查看上下线时间线

```bash
inconnect router online-trend <id> --after <start> --before <end> --oid <oid>
```

确认掉线发生的准确时间点、是否反复抖动。默认窗口约 24h。

### 3. 管理通道（MQTT）：上下线事件与断开原因

```bash
inconnect router connection-events <id> [--event-type connected|disconnected] [--after <start> --before <end>] --oid <oid>
```

每条事件包含 `eventType`、登录/登出时间、IP+端口（上线时）、以及断开原因 `reason`：

- `timeout` — 心跳超时，多为网络中断、信号差、断电
- `kicked` — 被平台主动踢下线（如 `router kick`、重复登录）

反复 `timeout` + 短在线时长 → 链路不稳定，继续看第 7 步信号质量。

### 4. VPN 隧道：会话日志

```bash
inconnect connection-log list --rid <id> [--status active|closed] [--after <start> --before <end>] --oid <oid>
```

VPN 层面谁连了/断了、会话时长、收发字节数、虚拟 IP。`--status active` 看当前在线会话；`--type user|router` 区分账号与路由器会话；也可用 `--uid` / `--username` 查某个 VPN 账号。

- 设备 MQTT 在线但 `connection-log` 无 active 会话 → VPN 隧道没建立，看第 5 步认证事件
- 会话频繁建立又关闭 → 隧道抖动，结合服务器日志与信号质量定位

### 5. VPN 隧道：认证/连接事件

```bash
inconnect vpn-event list --rid <id> [--type auth_failed] [--after <start> --before <end>] --oid <oid>
```

VPN 连不上最常见的原因是认证失败。`--type` 可逗号分隔多个事件类型；`auth_failed` 事件带失败原因，如：

- `invalid_cert` — 证书无效/过期/被吊销 → 用 `router ovpn <id>` 重新下发配置，或重签密钥对

也可用 `--uid` / `--username` 排查 VPN 账号的认证问题。

### 6. VPN 隧道：服务器端日志

```bash
inconnect server logs <server-id> [--tail 200] [--since 10m|1h] [--format text|json] --oid <oid>
```

直接看该组织 OpenVPN 服务器 Pod 的运行日志（服务端视角的握手、认证、断开记录）。`--tail` 默认 200、上限 2000。server-id 用 `inconnect server list --oid <oid>` 查。

### 7. 查看信号质量（蜂窝路由器）

```bash
inconnect router signal <id> --after <start> --before <end> --oid <oid>
```

信号趋势可反映是否因信号衰减导致断线。详见 `signal-analysis.md`。

### 8. 查看告警记录

```bash
inconnect alert list --oid <oid>
```

检查是否有离线告警、链路切换告警等。

### 9. 检查配置

```bash
inconnect router device-config get <id> --oid <oid>     # 平台存储副本
inconnect router running-config <id> --oid <oid>        # 设备实时配置（需在线）
```

确认 WAN 接口、APN、VPN 等关键配置是否正确。两者差异见 `router-config.md`。

### 10. 远程重启（需路由器在线）

```bash
inconnect router reboot <id> --oid <oid>
```

> **注意**：重启前必须获得用户确认。重启后会短暂离线，等待重新上线。设备需要 ack 才会执行。

### 11. 强制断开重连

状态异常（显示在线但无法通信）时，可强制踢下线让其重连（会自动重连）：

```bash
inconnect router kick <id> --oid <oid>
```

> kick 产生的 MQTT 断开事件 `reason` 为 `kicked`，事后在 `connection-events` 里可以核对。

## 常见症状速查

| 症状 | 先查 | 典型结论 |
| --- | --- | --- |
| 平台显示离线 | `connection-events`（断开原因） | `timeout` → 链路/供电问题；`kicked` → 有人踢的 |
| 设备在线但 VPN 不通 | `connection-log --status active` → `vpn-event --type auth_failed` | 无 active 会话 + auth_failed → 证书/账号问题 |
| VPN 认证失败 | `vpn-event list --type auth_failed` | `invalid_cert` → 重发 ovpn 配置 / 重签密钥 |
| 反复掉线抖动 | `online-trend` + `connection-events` + `router signal` | 信号衰减或链路不稳 |
| 整个组织 VPN 异常 | `server logs` + `server list` | 服务器 Pod 问题，看 `server-provisioning.md` |

## 离线路由器的排查建议

路由器离线时，远程操作（exec、reboot、kick、web、running-config、device-config set）均无法执行。引导用户：

1. 确认设备供电正常
2. 检查 SIM 卡（蜂窝）或网线（有线）
3. 检查天线连接
4. 本地登录设备 Web 管理页面排查
5. 如有条件，尝试本地重启设备

> 离线期间历史数据仍可查：`router diagnose`、`connection-events`、`connection-log`、`vpn-event` 都是平台侧记录，不要求设备在线。

## 批量离线排查

```bash
inconnect router list --online false --oid <oid>              # 所有离线路由器
inconnect router list --online false --query IR900 --oid <oid> # 按名称/SN 过滤
inconnect router stats --oid <oid>                             # 在线/离线计数 + 按型号分布
```
