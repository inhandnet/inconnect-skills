# 固件升级（OTA）

为路由器/网关安排固件升级并跟进进度。

## 流程概览

1. 查看/创建固件包记录
2. 添加要升级的设备（或先单台验证）
3. 触发升级
4. 跟进任务统计

## 命令

```bash
ics firmware list --oid <oid>                          # 固件包列表
ics firmware get <id> --oid <oid>                      # 包详情
ics firmware create ... --oid <oid>                    # 创建包记录
ics firmware update <id> ... --oid <oid>               # 更新
ics firmware delete <id> --oid <oid>                   # 删除
ics firmware upgrade <device-id> --firmware-id <id> --oid <oid>  # 升级单台
ics firmware devices <id> list --oid <oid>             # 升级任务中的设备
ics firmware devices <id> add ... --oid <oid>          # 添加设备到升级任务
ics firmware devices <id> remove ... --oid <oid>       # 移除设备
ics firmware job-stats <id> --oid <oid>                # 升级任务统计
```

## 规矩

- **先确认型号匹配**：固件包的 `model` 必须与目标设备型号一致，先 `router get` 查 `model`、`firmware get` 查包型号
- **先单台验证再批量**：高风险操作。先 `firmware upgrade` 升一台，确认成功后再 `firmware devices add` 批量
- **分批**：批量每批不超过 50 台
- **设备需在线**：升级需设备在线接收任务
- **升级前必须确认**：升级会导致设备重启、短暂离线，执行前向用户说明影响并获得确认
- **跟进进度**：用 `firmware job-stats` 看成功/失败/进行中分布；失败设备排查信号、在线状态后再重试

## 升级中掉线怎么办

升级过程中设备会重启离线，属正常。若长时间未恢复：

1. `ics router online-trend <id>` 看是否曾上线又掉线
2. `ics router signal <id>` 看信号是否足以完成下载
3. `ics firmware job-stats <id>` 看该设备的最终状态
