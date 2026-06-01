# 路由器配置：四种来源的区别

InConnect 里有四个看起来相似、实则读写不同对象的配置命令。改配置前务必分清。

## 四种命令对照

| 命令 | 来源 | 方向 | 说明 |
|---|---|---|---|
| `router running-config <id>` | 设备上的**实时**配置，已解码 | 读 | 需设备在线。权威的当前状态 |
| `router device-config get <id>` | 平台**存储**的副本 | 读 | 可能与实时配置不一致 |
| `router device-config set <id>` | **你提供**的完整配置 | 写 | 下发整份设备配置；需设备在线 |
| `router config-send <id>` | 平台**渲染**的 VPN-only 配置 | 写 | 仅证书/CA/防火墙等；可在离线时排队 |

## 读取配置

```bash
ics router running-config <id> --oid <oid>        # 实时（在线时优先用这个判断现状）
ics router device-config get <id> --oid <oid>     # 平台存储副本
ics router device-config export <id> --oid <oid>  # 导出存储配置元数据
```

实时与存储不一致时，以 `running-config` 为准判断设备当前真实行为。

## 下发完整配置

```bash
ics router device-config set <id> --content-file cfg.txt --oid <oid>
```

- 这是下发**整份**设备配置，影响面大，下发前必须获得用户确认
- 先 `running-config` 取当前配置作为基线，改完再下发
- 需设备在线
- 批量下发前先在单台验证成功

## 下发平台渲染的 VPN 配置

```bash
ics router config-send <id> --oid <oid>
```

只推送平台渲染的 VPN 相关配置（证书/CA/防火墙），不动用户的其他配置；可在设备离线时排队，待上线后生效。

## 处理 content 字段的坑

`--jq '.content'` 会把配置字符串重新编码（带引号和字面量 `\n`）。若要把读出的配置回灌给 `device-config set --content-file`，先用真正的 `jq` 或 python `json.loads` 解码成原始文本。

## DRC 模板（批量统一配置）

需要对多台路由器下发统一配置时，用 DRC 模板而非逐台 `device-config set`：

```bash
ics drc list --oid <oid>
ics drc create --name <n> --content <...> --oid <oid>
ics drc devices <id> add ... --oid <oid>
```
