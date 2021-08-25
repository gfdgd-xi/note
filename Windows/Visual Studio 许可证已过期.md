> 最近安装在电脑上的Visual Studio 2017 坏了，当打开很久没有开过的Visual Studio 2019 Professional ，发现许可证已过期的情况
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804133009866.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
> 怕再次出现这种情况再花时间尝试，在此记录一下

# 最初尝试

既然许可证已过期，那就点击“检查更新许可证”链接试试
登录Microsoft账户，继续
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804133156144.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804133252514.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

再点击“检查更新的许可证”试试，结果不行……
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804133429580.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


# 解决方法

其实最好的解决方法就是打开Visual Studio 2019的安装程序
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804133634923.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804133721580.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

然后找到要解决的Visual Studio 版本，点击“More”，然后点击“Repair”进行修复，但该方法非常耗时，就不说了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804134104564.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

其实还有一个更加简单的方法（不知道其他的电脑行不行）
1、关闭Visual Studio
2、打开到路径（32位）`C:\Program Files\Microsoft Visual Studio\2019\Professional\Common7\IDE`（注意，C:\为系统所在盘符，64位系统路径为`C:\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE`，然后Professiona和2019l是自己Visual Studio的版本）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804135620974.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、找到`DDConfigCA.exe`程序，然后运行
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804135728325.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
4、再次运行Visual Studio，会发现那个烦人的东西没了，注意别忘了输入注册码哦（估计这个编辑器也坏了）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200804140452875.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

后期发现，Visual Studio 2013对应的是`C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE`要注意哦（是Program File还是Program File(x86)就看自己电脑的系统位数了）
