# 思科交换机

### 远程连接

telnet 10.25.1.1  ssh 10.25.1.1  exit 退出

### 基础查询

```sh
enable                   #进入特权模式
configure terminal       #进入全局配置模式
show vlan                #查看vlan信息
show log                 #查看日志
show processes cpu       #查看cpu运行状态
show interface           #查看端口详细状态
show running-configure   #查看交换机当前起作用的配置信息
```

### 端口配置

进入特权模式后，再进入指定端口进行配置

enable

configure terminal

interface GigabitEthernet1/0/15

**trunk口配置**

```
interface GigabitEthernet1/0/15
description connect-WH-C2960S-POE-01/P23-24    #端口描述信息
switchport trunk encapsulation dot1q           #统一封装
switchport mode trunk
spanning-tree portfast
```

**access口配置**

```
interface GigabitEthernet1/0/14
description Connect-D-link-1048/p48
switchport access vlan 7
switchport mode access
spanning-tree portfast
```

**对多个端口进行配置**

```
interface range GigabitEthernet1/0/1-12
```
