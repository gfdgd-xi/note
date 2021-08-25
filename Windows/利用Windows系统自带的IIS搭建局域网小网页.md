你用过Windows系统吗？你看过网页吗？估计大家都用过看过，但有没有利用Windows搭建一个局域网网页吗？方法很简单，就在下面：
1、打开控制面板，点击“程序”，然后点击“添加或移除Windows功能”
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072321174384.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、在弹出的窗口里勾选有关IIS的选项
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723212828506.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、点击“确定”，等待安装
4、安装完后，无需重启，即可进行下一步操作
5、打开开始菜单，找到IIS的快捷图标，运行它
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072321302193.png)
6、点击“网站”，点击“添加”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723213249959.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
7、在弹出的窗口设置网页名称、网页文件所在地，然后建议把IP设为全部不分配，就就可以输入IPv4的地址，又可以输入IPv6的地址
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723213525796.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
8、进入设置好的网站根目录，新建一个文本文档，然后将后缀名改为.html，然后用记事本打开。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723213842438.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
9、输入以下文本，然后保存

```yaml
<title>Hello World!</title>
<p>Hello World!</p>
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723214153783.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

10、打开浏览器，在地址栏内输入127.0.0.1，就可以看到刚刚设计的网站了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723214322137.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
11、在其他设备输入以下链接访问设计好的网页：
IPv4地址：http://你的IPv4地址
IPv6地址：http://[你的IPv6地址]
这里的IP地址是192.168.0.103
电脑上的访问情况（Windows 8.1）：
![电脑访问自制网页](https://img-blog.csdnimg.cn/20200723215240389.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
手机访问结果（小米3，Android 4.4.4）：
![小米3访问自制网页](https://img-blog.csdnimg.cn/20200723215555772.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
至于你如何学习网页编程，想创建什么样的网页，跟我就没什么关系了
付：电脑IP地址的访问方法
1、按下“Windows+R”键，打开运行窗口。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723214909310.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、然后输入“cmd”，并点击确定，打开命令提示符（cmd，后边简写为cmd）
![在这里插入图片描述](https://img-blog.csdnimg.cn/202007232149274.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、在cmd里输入“ipconfig”，即可查看IP地址
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723214943378.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

**注意：**
**一定要用连接搭建网页的电脑所在的网络才可以访问网页！不然提示找不到服务器！（例如使用手机移动数据访问网页）**

# 附

附Windows XP IIS网页搭建视频


[video(video-oC17GFo6-1596938188006)(type-youku)(url-https://player.youku.com/embed/XNDc2NTUxNTUzNg==)(image-https://vthumb.ykimg.com/054106015F1A7EDF00000168000E6A2A)(title-利用 Windows 自带的 IIS 来搭建局域网网页)]

