> 刚刚入门Linux，选择deepin作为入门系统，由于自己实际需求，需要使用英语操作系统，于是写下了这个记录

# 设置中心更换语言

如果你懒，可以通过设置中心设置
1、打开设置中心主面板
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805081942216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、点击“键盘与语言”，然后选择“系统语言”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805082110990.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

3、如果列表中没有自己想要设置的语言，请点击下方的加号，寻找自己想要设置的语言，这里是以American English（美式英语）为例
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805082327830.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
4、返回到语言列表，选择自己想要设置的语言，然后注销或重启系统即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805082449322.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805082512290.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805084122361.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


# 终端更换命令语言

这才是重点，因为小白是要多接触黑黑的终端的，所以更换系统语言的命令如下：
1、按下Ctrl+Alt+T，打开终端（或者按下Ctrl+Alt+F2～F6进入tty也可以）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805082846202.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、输入命令

```bash
sudo vim /etc/default/locale
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805083043732.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、按下i键（如果会用vim，就当我在这里说废话），将里面的文本改为如下：

```bash
LANG=”en_US.UTF-8″
LANGUAGE=”en_US:en”
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/202008050838197.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

4、按下“ESC”，然后输入`:wq`保存文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805112501576.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

5、输入命令

```bash
sudo locale-gen -en_US:en
```
更换语言
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805084024684.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
6、重启或注销即可


# 结果

修改前：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805113356465.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
修改后：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200805113632214.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

