---
description: 打印机驱动安装、连接、共享
---

# 打印机连接与共享

### 本地打印机

1.连接网络后或者系统本身内置驱动或者之前安装过驱动的电脑，插线后会自动安装。

2.没有自动安装的机器可以在对应的品牌官网下载相应的驱动，不插线的情况下，安装好驱动，最后插线。

### 网络打印机

注：网络打印机需要接入网络并设置固定的ip地址才能进行连接

1.先在对应官网下载好相应的驱动，安装好驱动，输入网络打印机ip地址进行连接

### 打印机共享

本地打印机共享：控制面板-右键打印机属性-开启共享。

win+r键输入：\\\共享主机ip地址，即可看到共享主机的打印机，右键连接后会自动安装驱动。如果显示找不到驱动，可以选择从本地进行安装。或者可以安装好本地驱动再重新使用上面的共享方式进行连接。

Tips：

1.需要关闭防火墙，部分没有设置权限的电脑需要设置好权限才能正常访问。

2.Windows更新的补丁可能会对打印机共享产生影响，需要手动卸载补丁才能正常访问。

### **打印机常见故障：**

卡纸：取出废纸

文件名过长不能打印：更改文件名

缩放导致文件打印机卡顿：重启打印机更改缩放

自动进纸失败：重启打印机

打印进程卡顿：重启电脑或者重启打印进程

打印一直有挂载：控制面板卸载驱动重新安装，或删除打印机重新打印

**打印部分文本乱码：**

1.打印机首选项-图像品质-设置字体-下载字体位图，取消勾选打印机字体。

2.打印字体缺失导致，更改源文件字体或者安装源文件所需字体。

**打印服务未启动：**

1.服务-启动print pool，查看启动项是否被禁止。

2.设置开机启动脚本net start spool

如无效:请在要打印的word文档的打印窗口中选择打印机然后进入打印首选项进行设置。