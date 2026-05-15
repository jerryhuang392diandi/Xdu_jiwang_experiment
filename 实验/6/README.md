# 实验 6：NAT 配置实验

本实验在私网和公网混合拓扑中配置 NAT，理解 inside/outside 接口方向和地址转换表。

## 文件

- [6.pkt](<6.pkt>)：Packet Tracer 拓扑文件
- [assets](<assets/>)：拓扑、接口地址、NAT 配置和验证截图，共 16 张

## 拓扑

左侧和右侧是私有地址网络，中间模拟公网链路。标注为 NAT1、NAT2 的路由器负责地址转换。

![](assets/exp06-14.png)

## 地址线索

| 位置 | 地址 |
| --- | --- |
| 左侧 VLAN 19 | `192.168.19.0/24` |
| 左侧 VLAN 20 | `192.168.20.0/24` |
| 左侧 NAT 内侧链路 | `192.168.21.0/24` |
| 公网链路 1 | `174.1.0.0/16` |
| 公网链路 2 | `174.2.0.0/16` |
| 公网链路 3 | `174.3.0.0/16` |
| 右侧 NAT 内侧链路 | `192.168.22.0/24` |
| 右侧 VLAN 50 | `192.168.50.0/24` |
| 右侧 VLAN 37 | `192.168.37.0/24` |

## 配置要点

NAT 配置时先确定接口方向：

```text
私网侧接口：ip nat inside
公网侧接口：ip nat outside
```

静态 NAT 示例：

```bash
interface fa0/0
ip nat inside
exit

interface fa0/1
ip nat outside
exit

ip nat inside source static 192.168.19.1 174.1.1.1
```

如果实验要求多个内网地址共享一个公网地址，通常使用 PAT/overload；如果是一对一映射，则每台内网主机配置不同的 inside global 地址。

## 验证

1. 私网主机访问公网或对端网络后，查看 `show ip nat translations`。
2. 如果路由可达但 NAT 不生效，优先检查 inside/outside 是否配反。
3. 如果 NAT 表有记录但端到端不通，检查公网段和回程路由。
4. 截图中的 PDU 结果显示成功和失败并存，说明 NAT、路由或访问策略需要分别定位。
