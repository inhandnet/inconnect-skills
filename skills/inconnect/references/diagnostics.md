# 路由器离线诊断

路由器掉线/断网/连不上时的排查流程。

## 诊断步骤

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

### 3. 查看信号质量（蜂窝路由器）

```bash
inconnect router signal <id> --after <start> --before <end> --oid <oid>
```

信号趋势可反映是否因信号衰减导致断线。详见 `signal-analysis.md`。

### 4. 查看告警记录

```bash
inconnect alert list --oid <oid>
```

检查是否有离线告警、链路切换告警等。

### 5. 检查配置

```bash
inconnect router device-config get <id> --oid <oid>     # 平台存储副本
inconnect router running-config <id> --oid <oid>        # 设备实时配置（需在线）
```

确认 WAN 接口、APN、VPN 等关键配置是否正确。两者差异见 `router-config.md`。

### 6. 远程重启（需路由器在线）

```bash
inconnect router reboot <id> --oid <oid>
```

> **注意**：重启前必须获得用户确认。重启后会短暂离线，等待重新上线。设备需要 ack 才会执行。

### 7. 强制断开重连

状态异常（显示在线但无法通信）时，可强制踢下线让其重连（会自动重连）：

```bash
inconnect router kick <id> --oid <oid>
```

## 离线路由器的排查建议

路由器离线时，远程操作（exec、reboot、kick、web、running-config、device-config set）均无法执行。引导用户：

1. 确认设备供电正常
2. 检查 SIM 卡（蜂窝）或网线（有线）
3. 检查天线连接
4. 本地登录设备 Web 管理页面排查
5. 如有条件，尝试本地重启设备

## 批量离线排查

```bash
inconnect router list --online false --oid <oid>              # 所有离线路由器
inconnect router list --online false --query IR900 --oid <oid> # 按名称/SN 过滤
inconnect router stats --oid <oid>                             # 在线/离线计数 + 按型号分布
```
