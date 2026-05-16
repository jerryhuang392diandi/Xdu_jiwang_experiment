# 实验总览

本目录按实验编号保存 Packet Tracer 拓扑、课件、截图素材和实验说明。建议先打开对应实验的 `README.md` 看拓扑和验收点，再打开 `.pkt` 文件复现实验。

| 实验 | 主题 | 核心能力 | 文件 |
| --- | --- | --- | --- |
| 实验 1 | VLAN 划分 | access/trunk、广播域隔离、同 VLAN 连通性 | [README](<1/README.md>)、[1.pkt](<1/1.pkt>) |
| 实验 2 | 静态路由 | 逐跳地址规划、默认网关、静态路由表 | [README](<2/README.md>)、[2.pkt](<2/2.pkt>) |
| 实验 3 | RIP 与网络自愈 | RIP 宣告、跳数限制、链路故障后的路由更新 | [README](<3/README.md>)、[3.pkt](<3/3.pkt>)、[3.1.pkt](<3/3.1.pkt>)、[3.2.pkt](<3/3.2.pkt>) |
| 实验 4 | 单臂路由 | 子接口、802.1Q 封装、跨 VLAN 通信 | [README](<4/README.md>)、[4.pkt](<4/4.pkt>) |
| 实验 5 | DHCP 地址获取 | DHCP 地址池、默认网关、跨网段地址获取 | [README](<5/README.md>)、[5.pkt](<5/5.pkt>) |
| 实验 6 | NAT 配置 | inside/outside、私网到公网地址转换、连通性验证 | [README](<6/README.md>)、[6.pkt](<6/6.pkt>)、[6.1.pkt](<6/6.1.pkt>) |
| 实验 7 | NAT 与 ACL | 单臂路由、NAT、ACL 方向判断 | [README](<7/README.md>)、[7.pkt](<7/7.pkt>) |
| 实验 8 | 预留目录 | 当前暂无拓扑、课件和截图素材 | [README](<8/README.md>) |

## 文件命名约定

- `.pkt`：Packet Tracer 拓扑文件，可直接打开复现实验。
- `assets/expXX-NN.png`：实验截图，`XX` 是实验编号，`NN` 是截图序号。
- `README.md`：分实验说明，包含实验目标、拓扑、配置要点、验证方法和排错清单。
- `.ppt` / `.pptx`：教师课件或实验要求原始资料。

## 通用检查顺序

1. 先确认 PC 的 IP、掩码、默认网关是否和拓扑标注一致。
2. 再确认交换机 VLAN、access 口、trunk 口是否配置正确。
3. 路由器接口需要 `no shutdown`，直连网段地址不要配反。
4. 静态路由、RIP、NAT、ACL 等功能配置完成后，再做端到端 ping 或 PDU 验证。
5. 报告截图优先保留拓扑、关键配置页、路由表或 NAT/ACL 表、最终连通性结果。

## 常用命令

```bash
show ip interface brief
show vlan brief
show interfaces trunk
show ip route
show ip protocols
show ip nat translations
show access-lists
show running-config
```

## 报告截图建议

每个实验至少保留以下截图，方便写实验报告和复盘：

1. 完整拓扑图。
2. PC 地址配置或 DHCP 获取结果。
3. 交换机 VLAN / trunk 状态。
4. 路由器接口状态和路由表。
5. NAT、ACL、RIP 等本实验核心功能的配置或运行表。
6. 最终 ping / PDU 连通性验证结果。
