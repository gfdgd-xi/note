> 最近把自己的Deepin 20升级到Deepin 20 1001 update 1 社区版，
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200828191414860.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
> 但发现原来好看的终端升级成了平凡的样子
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200828191528389.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
> 因为我对原终端的喜爱，终于历经千辛万苦找到了方法（在此感谢星火商店）
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200828191724495.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
> 二更：经过尝试可以安装在Ubuntu 20.04上

# 方法

1、下载旧版Deepin终端安装包
[星火商店下载链接：http://dcstore.shenmo.tech/store/tools/deepin-terminal-legacy/deepin-terminal-legacy_3.2.1.1_plus_ds1-1_amd64.deb](http://dcstore.shenmo.tech/store/tools/deepin-terminal-legacy/deepin-terminal-legacy_3.2.1.1_plus_ds1-1_amd64.deb)
浏览器直接复制链接或单击超链接，终端可以输入以下命令进行下载（需要安装`wget`）：

```bash
wget http://dcstore.shenmo.tech/store/tools/deepin-terminal-legacy/deepin-terminal-legacy_3.2.1.1_plus_ds1-1_amd64.deb
```
或者（需要安装`aria2`，建议使用`aria2`下载）

```bash
aria2c http://dcstore.shenmo.tech/store/tools/deepin-terminal-legacy/deepin-terminal-legacy_3.2.1.1_plus_ds1-1_amd64.deb
```
如需安装wget请输入下方命令：

```bash
sudo apt-get install wget
```
如需安装aria2请输入下方命令：

```bash
sudo apt-get install aria2c
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020082819295937.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
2、输入命令进行安装

```bash
sudo dpkg -i deepin-terminal-legacy_3.2.1.1_plus_ds1-1_amd64.deb
```
返回结果（之前有安装过）：

```powershell
gfdgd_xi@gfdgd-xi-PC:~/Desktop$ sudo dpkg -i deepin-terminal-legacy_3.2.1.1_plus_ds1-1_amd64.deb 
请输入密码
[sudo] gfdgd_xi 的密码：
验证成功
(正在读取数据库 ... 系统当前共安装有 338524 个文件和目录。)
准备解压 deepin-terminal-legacy_3.2.1.1_plus_ds1-1_amd64.deb  ...
正在解压 deepin-terminal-legacy (3.2.1.1+ds1-1) 并覆盖 (3.2.1.1+ds1-1) ...
Error in file "/usr/share/applications/mitalk.desktop": "" is an invalid MIME type ("" does not contain a subtype)
Could not parse file "/usr/share/applications/screensavers/glitchpeg.desktop": Key file contains line ?several times a second.  After a while, finds a new image to corrupt. Written by Jamie Zawinski; 2018.? which is not a key-value pair, group, or comment
正在设置 deepin-terminal-legacy (3.2.1.1+ds1-1) ...
Error in file "/usr/share/applications/mitalk.desktop": "" is an invalid MIME type ("" does not contain a subtype)
Could not parse file "/usr/share/applications/screensavers/glitchpeg.desktop": Key file contains line ?several times a second.  After a while, finds a new image to corrupt. Written by Jamie Zawinski; 2018.? which is not a key-value pair, group, or comment
正在处理用于 lastore-daemon (5.1.0.10-1) 的触发器 ...
正在处理用于 bamfdaemon (0.5.4.1-1+eagle) 的触发器 ...
Rebuilding /usr/share/applications/bamf-2.index...
正在处理用于 desktop-file-utils (0.23-4) 的触发器 ...
正在处理用于 mime-support (3.62) 的触发器 ...
正在处理用于 hicolor-icon-theme (0.17-2) 的触发器 ...
正在处理用于 man-db (2.8.5-2) 的触发器 ...
gfdgd_xi@gfdgd-xi-PC:~/Desktop$ 

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020082819332787.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
如有依赖问题，请输入下发命令

```bash
sudo apt-get install -f
```

3、在启动器的系统管理选项即可找到旧版终端的快捷方式，打开如下图（之前有配置过终端）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200828193500770.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200828193553772.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)



4、现在按下“Ctrl+Alt+T”以及依旧是新版终端，可以打开控制中心→默认程序→终端，设置默认终端为旧版Deepin终端
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200828203740503.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)


# 二更

最近无聊作死Ubuntu，结果成功安装上了Deepin终端，详情请看截图（安装方法和Deepin一样）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200829154334161.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200829154557650.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200829154619479.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)



