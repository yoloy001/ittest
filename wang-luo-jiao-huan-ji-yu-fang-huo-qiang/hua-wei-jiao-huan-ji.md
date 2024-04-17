# 华为交换机

### &#x20;**查看配置**

```
system-view #系统编辑视图
display current-configuration #查看当前所有配置信息
undo 配置命令 #清除配置命令
display interface brief #查看接口信息
display vlan #查看vlan信息
```

### **DHCP配置**

**1.基于接口的DHCP配置**

方法一：vlan开启dhcp

```
vlan batch 10#创建vlan 10（进入系统视图下)
dhcp enable #必须先在系统视图下开启dhcp
interface vlanif10
ip address 192.168.10.1 24 #设置ip地址
dhcp select global #开启全局dhcp
```

方法二：

```
dhcp enable #必须先在系统视图下开启dhcp
interface Gigabithernet 0/0/1 #系统视图下，进入接口
dhcp select interface #设置DHCP基于接口
dhcp server dns-list 10.1.1.2 #设置dns地址
dhcp server excluded-ip-address 10.1.1.2 #设置需要排除分配的ip
dhcp server lease day 1 hour 1 minute 1 #设置ip租约时间
dhcp server domain-name jtt.com
```

**2.基于全局地址池的DHCP配置**

```
dhcp enable #必须先在系统视图下开启dhcp
ip pool vlan10 #创建地址池vlan10
network 192.168.10.0 mask 24 #设置网段
gateway-list 192.168.10.1 #设置网关地址
lease day 1 #设置租约时间（只能设置天数）
interface Gigabithernet 0/0/1 #系统视图下，进入接口
dhcp select global #开启全局dhcp
dis ip pool name vlan10 used #查看地址池已使用ip
```

实例:

1.创建多个vlan时开启dhcp，路由器会根据接口ip段分配相应网段的地址。接口需要配置ip地址。

2.多台路由器，设置好静态路由表，可以实现不同网段间互相访问。

3.一台路由器，不同接口设置不同网段，可以互相访问。实验故障点:未设置网关，设置网关地址后即可互通。

### **端口类配置**

**1.设置端口类型及可通过vlan**

1.1设置端口为trunk（可允许通过多个vlan）

```
interface Gigabithernet 0/0/1 #系统视图下，进入接口
port link-type trunk #设置端口类型为trunk口，可允许通过多个vlan
port trunk allow-pass vlan 10 #设置端口允许通过vlan 10
```

1.2设置端口为access（只允许通过单个vlan）

```
interface Gigabithernet 0/0/1 #系统视图下，进入接口
port link-type access #设置端口类型为trunk口，可允许通过多个vlan
port default vlan 10 #设置端口默认vlan 10
```

**2.限制端口mac地址**

```
port-security max-mac-num 2 #设置端口mac地址数（端口视图下）
port-security protect-action restrict #数量超出时限制多余主机通讯
```

### **路由类配置**

```
display ip routing-table #查看静态路由表
ip route-static 192.168.1.0 24 g0/0/0 192.168.2.0 #配置静态路由
```

注：第一个IP地址是目标地址，第二个地址是下一跳地址，中间的是出口接口。 需要配置回执地址，才能正确传送数据包。
