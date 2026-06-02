# VPN 网络管理

InConnect 的核心是 VPN 网络：把若干路由器、账号、端点组进同一张虚拟网络，使它们能安全互通。

## 概念

- **network**：一张 VPN 网络，承载成员之间的互通
- **成员**：路由器（router）+ 账号（account）
- **endpoint**：路由器下挂的端点（受保护的内网主机/网段）
- **center**：中心路由器（汇聚节点）
- 一张网络依赖组织已部署的 **VPN server**（见 `server-provisioning.md`）

## 常用流程

### 查看网络

```bash
inconnect network list --oid <oid>
inconnect network get <id> --oid <oid>
inconnect network routers <id> --oid <oid>      # 网络内路由器
inconnect network accounts <id> --oid <oid>     # 网络内账号
inconnect network endpoints <id> --oid <oid>    # 网络内端点
inconnect network centers <id> --oid <oid>      # 中心路由器
```

### 创建/更新/删除

```bash
inconnect network create --name net1 --oid <oid>
inconnect network update <id> --name net2 --oid <oid>
inconnect network delete <id> --oid <oid>
```

> 创建/删除/更新前先 `network get` 取现状；删除网络影响所有成员互通，务必先确认。

### 管理成员

```bash
inconnect network members <id> ... --oid <oid>  # 更新成员（路由器 + 账号）
```

修改成员前先用 `network routers` / `network accounts` 看当前成员，以现有列表为基线增删，避免误删。

## 端点

端点是挂在路由器后面的受保护内网资源：

```bash
inconnect endpoint list --oid <oid>
inconnect endpoint create ... --oid <oid>        # 在某台路由器上创建端点
inconnect endpoint update <id> ... --oid <oid>
inconnect endpoint delete <id> --oid <oid>
inconnect endpoint batch-delete ... --oid <oid>  # 批量删除（先确认范围）
```

## 子网与 VIP 分配

为路由器/端点分配地址时，用平台给出的下一个可用值，避免冲突：

```bash
inconnect router next-subnet <id> --oid <oid>   # 下一个可用子网
inconnect router next-vip <id> --oid <oid>      # 下一个可用端点 VIP
```

## 排查互通问题

1. 确认双方路由器都在线（`router list --online`）
2. 确认它们在同一张网络（`network routers`）
3. 确认组织 VPN server 已部署且正常（`server list`）
4. 确认端点网段配置正确、无重叠（`endpoint list`、`router running-config`）
