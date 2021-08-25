# 引入
> 你有听错吗？你以为我是一个标题党吗？没有听错，我也不是标题党，方法很简单，只需要一个叫做wget的小软件（Linux、Windows可以用，MAC没用过）就可以做到了。


# 准备工作
 
先说Windows系统用户怎么获取该软件：
1、在[这里](https://eternallybored.org/misc/wget/)下载Wget（如果英语不好请上百度搜索下载）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730183233163.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

**注意：在第3方下载站千万不能点击高速下载选项，不然看到许多流氓软件和广告，哭的是自己**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730183405820.png)
2、将下载下来的wget文件复制到C:\Windows文件夹（C是系统盘符，视情况而定，一般会提示需要管理员权限，点击“继续”并在弹出的UAC窗口点击“是”即可）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730183552412.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、运行命令提示符，输入命令`wget`，如果出现提示就代表步骤完成！
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730183725472.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
Linux系统（没用过Centos系统，所以该系统安装程序命令yum不知道怎么用，这里以Deepin为例）：

```powershell
sudo apt install wget
```
输入以上命令即可安装
返回的结果：

```powershell
gfdgd_xi@gfdgd-xi-PC:~$ sudo apt install wget
[sudo] password for gfdgd_xi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cabextract python-wxgtk3.0 python-wxversion
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  wget
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 799 kB of archives.
After this operation, 2,813 kB of additional disk space will be used.
Get:1 http://packages.deepin.com/deepin lion/main amd64 wget amd64 1.18-5+deb9u2 [799 kB]
Fetched 799 kB in 0s (804 kB/s)
Selecting previously unselected package wget.
(Reading database ... 292849 files and directories currently installed.)
Preparing to unpack .../wget_1.18-5+deb9u2_amd64.deb ...
Unpacking wget (1.18-5+deb9u2) ...
Processing triggers for install-info (6.3.0.dfsg.1-1+b2) ...
Setting up wget (1.18-5+deb9u2) ...
Processing triggers for man-db (2.7.6.1-2) ...
gfdgd_xi@gfdgd-xi-PC:~$ 
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731073214903.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

@[TOC](网页递归下载)

**（小提示：这里Windows系统和Linux系统输入的命令是相同的，没有很大的区别）**
你可以尝试输入以下命令：

```powershell
wget -m 网站链接
```
**（可别把中文输进去哦）**
这里先测试下面的命令**（注：下网站都需要很久，一般不建议执行这些测试命令）**

```powershell
wget -m http://www.zgqyhsx.com.cn/
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730202131527.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731073258459.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

下载成功：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730202949834.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730203100903.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731073734381.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731073827652.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


但尝试以下代码时却出现了错误
（代码）

```powershell
wget -m https://sx.piao5yun.com/
```
（提示）

```powershell
C:\Users\gfdgd xi>wget -m https://sx.piao5yun.com/
--2020-07-30 20:32:30--  https://sx.piao5yun.com/
Resolving sx.piao5yun.com... 112.30.162.176
Connecting to sx.piao5yun.com|112.30.162.176|:443... connected.
ERROR: cannot verify sx.piao5yun.com's certificate, issued by `/C=US/O=DigiCert
Inc/OU=www.digicert.com/CN=Encryption Everywhere DV TLS CA - G1':
  Unable to locally verify the issuer's authority.
ERROR: certificate common name `img.ucdl.pp.uc.cn' doesn't match requested host
name `sx.piao5yun.com'.
To connect to sx.piao5yun.com insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.
```

```powershell
gfdgd_xi@gfdgd-xi-PC:~$ wget -m https://sx.piao5yun.com/
--2020-07-31 07:38:39--  https://sx.piao5yun.com/
Resolving sx.piao5yun.com (sx.piao5yun.com)... 183.232.159.174
Connecting to sx.piao5yun.com (sx.piao5yun.com)|183.232.159.174|:443... connected.
ERROR: The certificate of ‘sx.piao5yun.com’ is not trusted.
ERROR: The certificate of ‘sx.piao5yun.com’ has expired.
The certificate has expired
gfdgd_xi@gfdgd-xi-PC:~$ 
```

百度翻译的结果（语法乱也就算了，只要知道错误在哪里就可以了）

```powershell
C： 用户sgfdgd xi>wget-mhttps://sx.piao5yun.com/
--2020-07-30 20:32:30--https://sx.piao5yun.com/
解析徐飘云-带着。。。112.30.162.176
正在连接到徐飘云.com.124；112.30.162.176.124；：443。。。有联系的。
错误：无法验证徐飘云.com的证书，由`/C=US/O=DigiCert颁发
公司/或www.digicert.com/CN=加密所有DV TLS CA-G1'：
无法本地验证颁发者的权限。
错误：证书公用名图片.ucdl.pp。是 啊。哇哦。与请求的主机不匹配
名称​​`name徐飘云.
连接到徐飘云.com不安全，请使用“-no check certificate”。
无法建立SSL连接。
```

```powershell
gfdgd@gfdgd xi个人电脑：$wget-m https://sx.piao5yun.com/
--2020-07-31 07:38:39--https://sx.piao5yun.com/
解析徐飘云.com网站徐飘云.com。。。183.232.159.174
正在连接到徐飘云.com网站徐飘云.com）（124183.232.159.174.124；443。。。有联系的。
错误：的证书徐飘云不被信任。
错误：的证书徐飘云.com'已过期。
证书已过期
gfdgd@gfdgd xi个人电脑~
```

**代表网页没有安全证书，因此用浏览器访问也提示是风险网页**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730203730936.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

```powershell

There is a problem with this website’s security certificate.
The security certificate presented by this website has expired or is not yet valid.
Security certificate problems may indicate an attempt to fool you or intercept any data you send to the server.  
We recommend that you close this webpage and do not continue to this website.  
Recommended iconClick here to close this webpage.   
Not recommended iconContinue to this website (not recommended). 
More information  More information  
•If you arrived at this page by clicking a link, check the website address in the address bar to be sure that it is the address you were expecting.
•When going to a website with an address such as https://example.com, try adding the 'www' to the address, https://www.example.com.
For more information, see "Certificate Errors" in Internet Explorer Help.
 

```

```powershell
此网站的安全证书有问题。
此网站提供的安全证书已过期或尚未生效。
安全证书问题可能表示有人试图欺骗您或截获您发送到服务器的任何数据。
我们建议您关闭此网页，不要继续访问此网站。
推荐图标单击此处关闭此网页。
不推荐iconContinue to this website（不推荐）。
更多信息更多信息
•如果您通过单击某个链接到达此页面，请检查地址栏中的网站地址，以确保它是您期望的地址。
•当访问一个地址为的网站时，例如https://example.com，尝试将“www”添加到地址，https://www.example.com。
有关详细信息，请参阅Internet Explorer帮助中的“证书错误”。
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731074320651.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

```powershell
警告：面临潜在的安全风险
Firefox 检测到问题而没有继续连接 sx.piao5yun.com。可能是该网站配置有误，或者您的计算机时钟设置有误。
很可能该网站的证书已过期，因而阻碍 Firefox 安全地连接。如果您继续访问该网站，攻击者可能尝试窃取您的密码、电子邮件或信用卡等信息。
您可以做什么？
您的计算机时钟目前设置为 2020/7/31。请确保您的计算机在系统设置中已设置了正确的日期、时间和时区，然后刷新 sx.piao5yun.com。
如果您的时钟已设置正确的时间，则此网站可能存在配置错误，您无法解决此问题。您可以向网站管理员反馈该问题。
详细了解…
报告此类错误，帮助 Mozilla 识别与拦截恶意网站
```


于是根据提示修改了命令

```powershell
wget -m https://sx.piao5yun.com/ --no-check-certificate
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730214537988.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731074614193.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

下载成功（只有2个文件，1个文件夹，下载不耗时间）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730214624355.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731074704880.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

但下载另一个网站又出现了情况：
输入了以下命令

```powershell
wget -m https://www.baidu.com/ --no-check-certificate
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730214849717.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731074750959.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020073021491754.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
（就两个文件？）
上了一下要下载的百度，**发现下载时被一个叫做“robots.txt”的文件给限制住了**，应该改成下面的命令

```powershell
wget -m -np -e robots=off http://www.baidu.com/ --no-check-certificate
```
于是又可以下载了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730215124250.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731074953852.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200730215154606.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200731075030556.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)最终总结一下语法（别把中文输进去哦）：

```powershell
wget -m -np -e robots=off 网页链接 --no-check-certificate
```


# 疑问

在下载部分网站时会提示403（无访问权限，如存放音乐的网址），请问各位大神如何处理，谢谢

# 更新情况

二更（２０２０年０７月３１日０７：３４：０６）：添加了Linux（Deepin）系统的截图
