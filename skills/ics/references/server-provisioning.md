# VPN 服务器部署与运维

每个组织的 VPN 网络都依赖一台（或多台）OpenVPN server。server 运行在 Kubernetes 上，由 vpn-controller 管理。

## 查看服务器

```bash
ics server list --oid <oid>
ics server get <id> --oid <oid>
ics server networks <id> --oid <oid>   # 绑定到该服务器的网络
```

> **私钥脱敏**：`server get/list/create` 默认对服务器 RSA 私钥（`keyPair.key`）做脱敏。**不要**主动加 `--show-secrets`，也不要把私钥写进日志或外部输出。只有用户明确要求查看私钥时才用 `--show-secrets`。

## 创建与部署

`server create` 默认 `--deploy=false`，**只写 DB 记录、不真正起 Pod**：

```bash
ics server create ... --oid <oid>            # 仅 DB 记录
ics server create ... --deploy --oid <oid>   # 创建并在 K8s 部署 OpenVPN Pod
ics server deploy <id> --oid <oid>           # 对已有记录部署/重新部署
```

> 部署会在 Kubernetes 上拉起 Pod，影响面大且较难快速回收。`--deploy` 或 `deploy` 前必须向用户说明影响并确认。先创建 DB 记录、确认参数无误，再单独 `deploy` 是更稳的两步法。

## 停服与恢复

```bash
ics server stop --oid <oid>      # 停止该组织的服务器（VPN 全断！）
ics server recover --oid <oid>   # 恢复
```

> `stop` 会中断该组织所有 VPN 连接，属于高风险操作，执行前务必确认。计费侧欠费停服也走这条路径。

## 密钥对与命令

```bash
ics server issue-keypair --oid <oid>    # 签发新服务器密钥对
ics server command --oid <oid> ...      # 向组织服务器发送命令
```

若 `router create` / `user create` 返回 error_code 10001（资源已建但证书签发失败），用对应的 `issue-keypair` 重试签发。

## 路由器跨组织迁移（transfer）的前置条件

`ics router transfer <id> --to <target-oid> --oid <src-oid>` 有严格前置：

- 需 **ROOT** 账号
- 目标组织必须**已部署 VPN server**
- 路由器的 Real-IP 接入必须**关闭**（`router set-rip <id> --enable=false`），否则后端拒绝（error_code 20005）
- 操作**不是**跨 site + vpn-controller 的原子操作

执行前先 `ics router transfer --help` 看完整参数，逐条确认前置条件，再谨慎操作。
