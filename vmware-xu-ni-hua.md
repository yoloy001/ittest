# VMware虚拟化

### 虚拟化应用VMware ESXi和vcenter介绍

#### 核心组件

VMware ESXi 安装文件可以从VMware的官方网站上直接下载（注册时需提供一个有效的邮箱），下载得到的是一个iso 文件，可以刻录成光盘或量产到U盘使用，由于ESXi 本身就是一个操作系统(Linux内核)，因此在初次安装时要用它来引导系统；**vSphere 的两个核心组件是ESXi和vCenter Server。ESXi是用于创建并运行虚拟机和虚拟设备的虚拟化平台。vCenter Server是一项服务，用于管理网络中连接的多个主机，并将主机资源池化。ESXi是直接安装在物理机器上的，是采用Linux内核的虚拟化专用操作系统。**Esxi主机是物理机器真是存在的一个物理主机（当然也可以是虚拟机），其实就是一个装了系统的电脑。ESXI是一个系统，就跟windows，linux系统一样的一个系统。

#### 1、VMware ESXi:

基于linux内核的基础虚拟系统，主要使用在物理硬件上，特别是大型服务器，可以更有效利用硬件资源。在它的基础上，可以布置各种虚拟机操作系统，包括windows,linux等。

#### 2、VMware vCenter Server：

有linux与windows版。主要是对ESXI物理主机进行管理的一个系统。配合适当的数据库系统，特别是在esxi主机集群中，可以通过一套或者两套vcenter server进行方便快捷的统一管理。包括管理硬件，物理资源，虚拟机操作系统。基操作主要是基于WEB页面的。当esxi服务器比较少时，vcenter可以不装。数量大时，建议一定安装，方便 管理。\
使用环境：ESXI 将多个服务器整合到同一硬件资源上，方便管理。vCenter：搭建虚拟化平台，将多个ESXI主机资源池化，安装多个虚拟机远程办公和提供网络等服务。\
1.平台搭建、安装部署2.平台管理、调整3.平台维护、故障修复4.服务器快照管理Linux系统：红帽redhat、centos、Ubuntu、Debian[虚拟化基础功能(HA\DRS\vMotion\FT)-2022.05](https://www.bilibili.com/read/cv16886425/)

一、什么是**vMotion**

1、vMotion的概念\
VMware vMotion允许虚拟机在不停机的情况下更改其运行位置。例如，我可以将虚拟机从一个ESXi主机移动到另一个ESXi主机，而正在使用此虚拟机的用户并不会感觉到这个迁移的发生。通过vMotion可以实现零停机时间和连续可用的服务，并能全面保证业务的完整性和连续性。\
2、vMotion工作原理\
Vmotion操作需要在不同ESXi主机之间传输虚拟机状态信息。如右图，一个可以运行vMotion的环境需要包括共享存储、共享网络和用于转移虚拟机状态的网络。这三个要素是vMotion运行必须具备的先决条件。虚拟机的状态信息是指内存中的内容（虚拟机正在做什么），以及关于虚拟机的一些唯一标识信息。这些信息包括BIOS、设备、CPU、以太网卡的MAC地址、芯片组状态、寄存器等等。\
三种：主机、存储、both

二、什么是**HA**\
1、vSphere HA\
为集群中的VM提供高可用，群集中的主机均会受到监控，如果发生故障，故障主机上的虚拟机将在备用主机上重新启动。vSphere HA会持续监控资源池中的所有物理服务器，并重启受服务器故障影响的虚拟机。\
● 监控和检测虚拟机的“客户操作系统”故障，并在用户指定的时间间隔后自动启动虚拟机。

● 使用服务器上的“心跳信号”来自动检测服务器故障。

● 无需人工干预立即在同一资源池中的其它物理主机上重启虚拟机。

● 与DRS配合使用，选择要在其上重启虚拟机的资源池中的最佳物理主机。\
2、vSphere HA的工作原理\
HA不间断地监控集群中所有ESXi服务器，并检测故障。放置在每台主机上的代理程序不断向集群中的其它主机发出“心跳信号”。如果“心跳信号”终止，将触发所有受影响的虚拟机在其它主机上的重启过程。\
三、什么是**DRS**\
1、VMware DRS代表分布式资源调度程序：\
是VMware vSphere集群的一部分，它查看集群中的主机，并平衡它们之间的CPU和内存利用率。如果一台主机超载，它将分散工作负载，以确保性能不受影响。这是对VMware DRS功能的一个非常简单的解释。\
VMware DRS跨聚合到逻辑资源池中的硬件资源集合来动态的分配和平衡计算容量，DRS会不间断的监控资源利用率，并根据需要和不断变化的优先级的预定义规则，在多台虚拟机之间智能地分配可用资源，当虚拟机负载增大时，DRS会通过在资源池中的物理主机之间重新分发虚拟机来自动分配额外的资源。\
2、VMware DRS的前提条件：\
与VMware vMotion一样，VMware DRS也有一些要求，因为它是vSphere集群的一部分，所以必须有一个有效的ESXi集群才能打开DRS。其中一些要求是大家熟悉的，例如:\
&#x20; ● 共享存储&#x20;

&#x20;● ESXi主机上兼容的处理器 &#x20;

● vMotion已经启用（Vmotion不依赖DRS，但是DRS依赖VMotion）\
四、什么是Vmware **FT**\
主虚拟机位于一台主机之上，备虚拟机位于另一台主机之上。VMware vLockstep技术确保虚拟机处于同步状态。如果主虚拟机发生故障，那么备虚拟机将会实时接管业务。用户不会感觉到中断或者连接丢失。\
FT无业务中断，HA会有中断时间在不同的主机上同步运行相同的虚拟机\
出现硬件故障时，所有虚拟机均可实现零宕机时间、零数据损失故障切换\
零宕机时间、零数据损失\
无需复杂的集群或专用硬件\
所有应用程序和操作系统通用的单一机制
