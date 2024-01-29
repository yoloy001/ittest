# 常见故障

### Windows系统

* **EXE病毒：**文件夹变成EXE，设置显示隐藏文件，属性改为不隐藏，删除exe病毒文件。
* **部分国外网站打不卡：**切换DNS 电信 114.114.114.114 谷歌 8.8.8.8
* **Win7安装软件无反应或闪退失败：**大概率是.net版本过低或者系统缺失补丁包。也是可能被杀毒软件拦截导致，查看杀毒软件拦截日志，关闭杀毒软件后安装。
* **开机应用程序错误：**卸载重装或修复相关软件即可。
* **浏览器网址被劫持，清除hosts文件网址：**/windows/system32/dirver/etc/hosts
* **清理C盘空间：**空间大小和实际占用不符，软件缓存被隐藏了，打开查看隐藏文件。打开系统高级配置，用户配置文件，查看每个用户占用空间大小。
* **Win10进系统显示系统故障，修复无效：**进安全模式，扫描系统修复 scanfnow
* **Win7登录输入用户名默认为中文输入：**控制面板-区域和语言-管理-勾选将当前设置复制到欢迎屏幕，应用即可

![](https://w2027riewk.feishu.cn/space/api/box/stream/download/asynccode/?code=NGRkMWY3NDE0MGFhNzc5NjUyZjg1MDAwMDYxYTE5OGNfNkkyajNBb1V6eTBibTBvZFRJb1Z6RjJ6NzVHZWRxdlFfVG9rZW46UFVwYmJRTGc4b0JiRzZ4SmhlbGMyQ0tNbk5jXzE3MDY1Mzg5MzQ6MTcwNjU0MjUzNF9WNA)

* **加密文件夹方法：**右键文件夹-属性-高级-加密
* **远程桌面：**需开启后才能访问，电脑默认为关闭。笔记本休眠后再开启可能会导致远程桌面无法连接，电脑重新连接网络即可。开启 Windows hello会导致无法使用微软账户进行远程桌面，本地账户不影响。关闭后退出账户重新登陆即可。
* **重启后桌面图标，快捷方式消失：**域用户使用临时配置文件导致。组策略删除后配置文件重新生成即可。

**解决方法：**

1.win+r”打开运行栏，输入“[regedit](https://so.csdn.net/so/search?q=regedit\&spm=1001.2101.3001.7020)”

2.接着在打开的“[注册表编辑器](https://so.csdn.net/so/search?q=%E6%B3%A8%E5%86%8C%E8%A1%A8%E7%BC%96%E8%BE%91%E5%99%A8\&spm=1001.2101.3001.7020)”窗口中依次开：“HKEY\_LOCAL\_MACHINE/SOFTWARE/Microsoft/WindowsNT/CurrentVersion/ProfileList”子项

3.接着点击“S-1-5-21”开头的配置文件，然后在右边窗口中找到“ProfileImagePath”项，我们在“ProfileImagePath”中能看到登录账号名

4.最后将出问题的账号的“S-1-5-21”开头的配置项删除，其中有一个以.bak结尾的也一并删除，之后退出注册表，重启电脑后系统会自动帮助我们重新配置文件。

### Office

* 2 013打开闪退：从主程序打开并设置为默认打开程序。wps篡改默认启动导致。
* office Excel2010 打开文件提示向程序发送命令错误：“Excel选项”-“高级”-“常规”-去掉“忽略使用动态数据交换DDE的其它应用程序”
* office单个ptt修改内容，一动就卡死：版本过低文件与软件不兼容，升级版本。
* 安装office2010 提示1935 ：.net版本过低，升级.net版本。
* outlook打开提示olmapis32.dll错误：使用安装程序选择第一次安装状态修复。
* 设置outlook让邮件自动保存到本地方法 https://zhidao.baidu.com/question/881648312896991012.html outlook2010
* http://m.meiriyixue.cn/post/216.html outlook2016及新版本设置方法
* 第二种方法：新建本地outlook后，创建接收规则，当接收到指定关键字时移动到指定文件夹。
* 设置成本地后云端邮箱接收不到
* outlook规则：对人，主题正文关键字，抄送，发送人，标记，邮件地址，类别，附件，时间

操作：删除，移动，转发，标记，指定答复，桌面通知，播放声音，打印，打开软件，运行脚本等最后设置例外操作。垃圾邮件：指定发信人设置为垃圾邮件，设置安全收件人。实用规则：移动某一类邮件至指定文件夹

* office ppt文件打开乱码：系统缺失字体，选择替换字体或者安装字体。
* Excel文件关闭卡死： 文件与程序版本不兼容，另存份文件
* 加密office文件：文件-信息-保护账户簿-加密

### WPS

* wps打开文档格式变了：另存为2003-2007版本文件。
* wps卡顿：更换2019版wps。
* 重装后页面边距不对:打开视图-标尺，调整缩进

### Adobe

* cad安装失败：日志提示，net4.7安装失败：原因：缺少证书，导入证书后安装正常。

解决方法：https://mp.weixin.qq.com/s/C1IERtg6XzkP5-PTNmx7tQ

* adobe reader dc带云文档功能，去掉dc不带；pro版可编辑。

1.1登录提示连接不到服务器，更新ie浏览器。1.2dc版登录提示拒绝访问，暂未找到解决方法。1.3pro版可使用安装adobe cloud安装，或独立安装pro版登录。

* adobe 常见问题处理

https://itsc.nju.edu.cn/adobe/listm.htm

### 其他软件

* 360浏览器点击链接不跳转：设置—标签设置—总是跳转到新标签页。
* Microsoft Teams 一直正在加载：右击teams，点击兼容性疑难解答，选择第一个

相关链接：https://zhuanlan.zhihu.com/p/334726877

* win7谷歌浏览器字体模糊：新版本109.0.5414.75导致。更换浏览器或降低版本

系统安装kb2670838后正常

* 电脑微信登录卡死，扫码显示后手机已登录，但电脑微信卡死:b. 输入“%appdata%”并按回车键打开应用程序数据文件夹； c. 找到“Tencent”文件夹，然后找到“WeChat”文件夹； d. 打开“Temp”文件夹，然后删除其中的所有文件
* 压缩包内文件名乱码:升级压缩软件版本即可

![](https://w2027riewk.feishu.cn/space/api/box/stream/download/asynccode/?code=NjBhMWIxNGU5NGIxMzBkMzMxMzExYmFhNjhjYzZkZmVfMEY0Zk9OSHBpNVVMMWJPZ1l0Q3FlZTdDU1lRd0J6TWtfVG9rZW46SFNacmJibkR2bzBrVUd4QVFlN2NJYlJIbk5oXzE3MDY1Mzg5MzQ6MTcwNjU0MjUzNF9WNA)![](https://w2027riewk.feishu.cn/space/api/box/stream/download/asynccode/?code=NTliOTg5OGM1N2M1ZWQ1OGFlNjViNDlkMDU2ZDY4NDBfbTVUMEpyUThSWTRCZUxhb3lBekJWR0xkMXRLQmlCajNfVG9rZW46TUZ0bmJLdjBWbzBKNWR4Szg0aGNDSkJ4bmtjXzE3MDY1Mzg5MzQ6MTcwNjU0MjUzNF9WNA)苹果压缩文件解压后有两个https://www.betterzipcn.com/faq/better-fgur.html

* 解除edge强制打开IE：https://baijiahao.baidu.com/s?id=1759166046784512253\&wfr=spider\&for=pc

近期Windows更新补丁取消了这一方法，需要卸载补丁后才能生效。
