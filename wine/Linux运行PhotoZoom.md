> 最近了解到了PhotoZoom这个牛逼的图片缩放软件，这是PhotoZoom的中国官网介绍：
> 
> ```bash PhotoZoom Pro 8 新增功能 一款划时代的、技术上产生革命性影响的数码图片放大工具。
> 
> 1、通过全新的、更优质的照片优化技术提高图像质量
> 
> 2、可以有效提高提高照片的质量（如果不需要调整照片的大小）
> 
> 3、针对不同类型照片和图形提供不同的优化预设
> 
> 4、全新的、功能强大的图片批量处理功能
> 
> 5、增强了对原始图像的支持
> 
> 6、独立安装应用程序支持打开EXR图像（插件支持EXR）
> 7、Mac：暗模式支持（需要MacOS Mojave（10.14）或更高版本） ```
> 
> ```
> 但发现它居然没有for Linux的版本，这就有点坑了，而且百度上也没有有关的方法（可能是这个软件不常见吧），因此经过一段时间的摸索，找到了方法


# 准备工作

一个装有Linux系统的电脑（这里用的是Deepin），
系统**有安装wine/deepin-wine/CrossOver**，
有PhotoZoom 7/8 的安装包 ~~（最新的8无法使用）~~
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811161131577.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)



# 使用wine进行安装

1、输入命令

```bash
sudo apt-get install wine
```
安装wine（每个系统有区别，因分开对待）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811161331885.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

2、使用`cd`命令将命令提示符定位到存放PhotoZoom安装文件的位置
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811161702510.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、输入命令

```bash
wine 安装包名称
```
运行安装文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020081116183081.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

4、根据安装向导进行操作
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811161934720.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
5、你会发现开始菜单里会出现一个快捷方式，点击启动（别问我这里为什么会有两个快捷方式）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811162232546.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
安装完成
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811162446888.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

@[TOC](使用deepin-wine安装)

1、安装deepin-wine，deepin的用户只需要输入命令

```bash
sudo apt-get install deepin-wine5
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811165235984.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

即可安装命令，如是Ubuntu请在[这里](https://download.csdn.net/download/weixin_46403483/12704680)下载离线安装包/在线安装包进行安装
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811165144373.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、安装完后deepin用户输入命令

```bash
deepin-wine5 安装包名
```
UBuntu用户输入命令

```bash
deepin-wine 安装包名
```
进行安装，安装向导步骤省略
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811165414137.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、在开始菜单找到快捷方式，打开（懒了，直接在上方复制好了）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811165518232.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
OK
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811165618367.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


# 使用Crossover进行安装

1、安装Crossover，就不仔细讲了，偷偷跟deepin的用户说一下，如果你用

```bash
sudo apt-get install crossover-deepin
```
进行安装，会发现使用时无需授权！有图有真相
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811163338120.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811163415321.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
Ubuntu是无法安装的：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811174044585.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


2、安装完后，点击下方的“安装Windows 软件……”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811163502363.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、点击下方“查看所有可用程序……”，随便选择一项，这里选的是“未列出的应用程序”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811163728128.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
4、点击继续，点击“选择安装文件……”，进行选择
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020081116384266.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
5、容器就随便了，这里就改一下名称
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811163929317.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
6、点击“安装”，进行安装
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811164045370.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
7、出现安装向导，根据向导操作即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811164158578.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811164232123.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
8、在刚创建的容器里找到PhotoZoom的快捷图标，双击运行
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811164504641.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

# 最后小记

在有些时候使用deepin-wine会出现以下情况

```bash
gfdgd_xi@gfdgd-xi-Vostro-220s-Series:/media/gfdgd_xi/47e275e3-dd08-4da7-87d1-e303419d4bee/home/gfdgd_xi/Desktop$ deepin-wine PhotoZoom_Pro_7_Setup.exe 
wine: '/home/gfdgd_xi/.wine' is a 64-bit installation, it cannot be used with a 32-bit wineserver.
gfdgd_xi@gfdgd-xi-Vostro-220s-Series:/media/gfdgd_xi/47e275e3-dd08-4da7-87d1-e303419d4bee/home/gfdgd_xi/Desktop$ 
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200811174713927.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)删除掉这个 wine 容器即可


# （二期更新）


PhotoZoom Pro 7/8下载地址（非破解版，为官方原版，没钱者请忽略，如我）：
[百度网盘下载链接: https://pan.baidu.com/s/1q0n6BU5EnPrOVSYhPq1XJg 提取码: fidq](https://pan.baidu.com/s/1q0n6BU5EnPrOVSYhPq1XJg)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200819194232729.png#pic_center)

