# 前言

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726062942892.png)

最近查看C盘空间时，发现149GB的分区居然只剩23.1GB了，整整用了125.9GB！现在应该考虑一下怎样释放C盘的空间了

# 磁盘清理程序

我首先想到的就是用磁盘清理程序来清理空间，听说有个叫做Dism++的清理工具，不知道行不行，试一试吧，不行还可以用系统自带的磁盘清理程序（或者大家推荐其他的磁盘清理程序也行）[官网：http://www.chuyu.me/zh-Hans/](http://www.chuyu.me/zh-Hans/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726063834486.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
清理后系统结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726064522511.png)
整整省了13.7GB的空间，这个程序挺牛。
如果这时再用系统自带的磁盘清理程序的话……
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726065138795.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
系统自带的磁盘清理程序能清理的东西非常少，如果说是因为上面这个Dism++的程序影响，我尝试在虚拟机的另外一个操作系统尝试（Windows XP）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726065524123.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
只能清理817919KB（≈799MB，四舍五入到个位），可以清理的量还挺多的吗。
如果是用Dism++检测
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726065919988.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
这种情况有点尴尬呀，打不开，我现在居然无言以对。（官网上已经标明支持的有Windows Vista、Windows 7、Windows 8、Windows 8.1 和 Windows 10，不审题的老毛病又犯了）
算了，不管他，释放空间最重要！

# 删除无用程序

大家电脑上应该有许多程序吧，可能有些是不需要的，如果不需要，可以把它卸载掉，建议使用专门的卸载工具，这里用到的是Get Uninstaller，[官网链接：https://geekuninstaller.com/](https://geekuninstaller.com/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726070712200.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
这里卸载360驱动大师、KMSpico、Microsoft Visual Studio 2017 Enterprise 便携精简版
结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726072834178.png)
释放了7.3GB的空间，C盘舒服多了。

# 转移用户文件

自从上次我存放在Windows.Old的程序源码被系统自动删除，我这次就要尝试转移用户文件，不然系统误删（也可以节省C盘空间）
先看一下用户文件夹占多少GB
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726073407458.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
整整15.4GB，看来要开始转移了
转移的文件有：
用户桌面
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726073612795.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
用户的文档库
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726073757659.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
用户的下载文件夹
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726074311277.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
用户的音乐文件夹
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726074415236.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
用户的图片文件夹：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726074519399.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
用户的视频文件夹：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072607463119.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
（程序源码文件夹，只有在安装Visual Studio后才有）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726074954356.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
转移结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726075128992.png)
已经节省了6.2GB的空间，接下来继续。


# 删除C盘无用文件

为什么这样说呢？如果你用过一些软件会知道，它会在C盘根目录创建文件夹，有些文件夹占用空间非常大，例如说迅雷的下载文件夹等等，根据自己实际情况将其删除即可。
例如：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072611585780.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
删除后结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200726115945601.png)
释放了4.2GB的空间，可用空间非常多

# End

目前就这样，有什么建议尽管提出。
