**开机自动运行某bat脚本**

将bat脚本放到：C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp

# 常用程序
| 常用 |  | 服务编辑 |  | 其他 |  |
| --- | --- | --- | --- | --- | --- |
| msconfig  | 开机启动项管理 | gpedit.msc  | 组策略编辑器 | compmgmt.msc  | 计算机管理 |
| dxdiag  | 计算机详细信息 | service.msc  | 服务编辑器 | appwiz.cpl  | 卸载程序 |
| mstsc  | 远程控制 | regedit | 注册表编辑器  | taskschd.msc  | 自动计划任务 |
| control  | 控制面板 | secpol.msc | 本地安全策略 |  |  |
|||||||
|--|--|--|--|--|--|
|||||||
|||||||
*msconfig  可查看开机启动项，工具里可查看UAC，Internet选项，程序，计算机管理等

# 常用命令
## 网络端口、路由检测
netstat -ano 查看端口占用情况<br />netstat -ano | findstr "端口号",查找端口号是否被占用<br />netstat -ano | findstr "SYN_SENT" 查看正在发送请求的连接<br />telnet 192.168.0.1 80 检测端口号是否开启可用<br />tracert -d 网址、ip 查看经过路由点
## DNS解析检测
nslookup baidu.com [qq](http://kan1234.com/tags-147/)但是不能上网页，这种情况下一般我们就需要测试一下DNS是否正常<br />nslookup baidu.com 114.114.114.114 指定DNS地址解析
## PING及IP、主机、MAC信息
ping 192.168.0.1 -t 不间断ping主机ip<br />ping 192.168.0.1 -n 10 ping 10次主机ip<br />ping 192.168.0.1 -l 1024 加包ping<br />ipconfig /release 释放ip地址<br />ipconfig /renew 重新获取ip地址<br />**nbtstat -a 192.168.0.102 显示计算机名称及MAC地址**<br />netstat -a wh-panpeng 显示计算机的ip及MAC地址<br />arp /? 可以得到ARP命令的详细说明<br />arp -a 192.168.0.1 显示mac信息，需要ping过
# Windows查看激活期限命令
slmgr.vbs -xpr	查看激活状态<br />slmgr.vbs -dlv	查看激活详细信息<br />slmgr.vbs -dli	查询到操作系统版本、部分产品密钥、许可证状态等<br />slmgr.vbs /sai<br />设置未激活的客户端尝试连接 KMS 的时间间隔(分钟)。虽然建议了默认时间(2 小时)，但是激活间隔必须介于 15 分钟(最小值)到 30 天(最大值)之间。<br />slmgr.vbs /sri<br />设置激活的客户端尝试连接 KMS 的续订时间间隔(分钟)。虽然建议了默认时间(7 天)，但是续订时间间隔必须介于 15 分钟(最小值)和 30 天(最大值)之间。<br />**查看office激活有效期** <br />1.进入安装目录（C:\Program Files\Microsoft Office\Office16）<br />2.地址栏输入cmd，再输入 cscript ospp.vbs /dstatus<br />https://www.izshi.cn/article/1601143
# 基础命令
shutdown -t 3600 -s 1小时后关机<br />shutdown -a 取消关机<br />start 打开文件、程序或网址<br />d: 进入相应磁盘<br />dir 显示目录中的文件和子目录列表<br />cd .. 进入上一级目录<br />cd desktop 当前目录文件名<br />pause 暂停运行<br />cls 清除屏幕<br />exit 退出cmd程序<br />cmd 运行后还能继续输入<br />wmic product get name 显示已安装程序信息
## 其他命令
gpupdate 更新组策略<br />chkdsk i: /f 修复磁盘命令，i改成要修复的磁盘<br />sfc /scannow 自动检测修复系统文件<br />net start Spooler 启动Spooler服务<br />taskkill /f /t /im qq.exe 关闭QQ进程




