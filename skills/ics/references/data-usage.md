# VPN 流量用量分析

`data-usage` 是 vpn-controller 侧的 VPN 流量统计，**不同于** `router traffic-day`（后者是 site 的设备级流量）。

## 命令

```bash
ics data-usage summary --month <YYYY-MM> --oid <oid>   # 组织级汇总（--month 必填）
ics data-usage account --oid <oid>                     # 每日按账号
ics data-usage account-month --oid <oid>               # 每月按账号
ics data-usage router --oid <oid>                      # 每日按路由器
ics data-usage router-month --oid <oid>                # 每月按路由器
ics data-usage account-export --oid <oid>              # 导出账号用量 Excel
ics data-usage router-export --oid <oid>               # 导出路由器用量 Excel
```

## 用法要点

- `summary` 的 `--month` 必填，格式 `YYYY-MM` 或 `YYYYMM`
- 时间范围类命令遵循左闭右开 `start ≤ data < end`；查某天用 `--after 当天 --before 次日`
- 数据量单位通常是字节（bytes），向用户展示时按需换算为 MB/GB
- 要逐台路由器看用量用 `router` / `router-month`；要按 VPN 用户账号看用量用 `account` / `account-month`

## 与设备级流量的区别

| 需求 | 用 |
|---|---|
| VPN 隧道承载的用量（按账号/路由器/组织） | `ics data-usage *` |
| 单台设备的运营商口流量（按日/按月，site 侧） | `ics router traffic-day <id>` |

用户笼统说"看流量"时，先问清是要 VPN 用量还是设备运营商流量，再选对命令。

## 典型分析

1. 先 `summary --month` 看组织整体水位
2. 异常偏高时用 `router-month` / `account-month` 定位是哪台路由器或哪个账号贡献的
3. 需要给人对账时用 `*-export` 导出 Excel
