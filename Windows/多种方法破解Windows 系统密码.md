> 破解Windows密码有4种方法，一是用Windows PE自带的密码破解工具破解，二是开机按F8进入安全模式破解，三是利用Windows
> PE所带的最高权限账户破解，最后一种是删除SAM文件破解。

## 方法一：用Windows PE自带的密码破解工具破解

1、准备安装Windows PE到U盘
2、开机按电脑的软件，进入启动选择你所制作好的Windows PE安装包，进入PE。
3、进入PE后，打开密码破解工具。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723194738412.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

4、选择操作系统的SAM文件（一般都选好了，SAM一般在“系统根目录\Windows\System32\Config”文件夹）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723194803541.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

5、选择完后，选择要破解的账户，点击下面“修改密码（M）”的按钮，在弹出的对话框里输入要更改的密码（如不需要设置密码，请留空）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723194823852.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


6、重新启动电脑，输入你设置的密码，就可以看见久违的桌面了。

## 方法二：安全模式破解法（确保Administrator账户密码没忘）

1、开机按F8，选择“带命令提示符的安全模式”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723194841692.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

2、进入后，选择账户“Administrator”，进入系统。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723194859642.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

3、进入账户后，输入命令“net user Admin 123456"（不要输入双引号，这里以Admin账户为例）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723194916901.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

4、输入命令“shutdown -r -t 0”（不要输入双引号）重新启动电脑
5、看一下可不可以看见久违的桌面了。

## 方法三：替换文件法（这里以Administrator账户为例）

1、重启进入Windows PE。
 2、进入“系统盘:\Windows\System32”文件夹，将文件“cmd.exe”重命名为“sethc.exe”，并把原“sethc.exe”文件备份以便还原。 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723194940974.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

3、重启返回操作系统，按下5次“Shift”键，打开命令提示符，输入命令输入命令“net user "administrator" 123456”把Administrator的密码更换为“123456”
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072319500444.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

 5、登录系统后重启电脑，进入Windows PE，把刚改的文件“sethc.exe”改回“cmd.exe”，把备份出来的“sethc.exe”恢复到原来的位置即可，重启电脑，大功告成。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723195021994.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


## 方法四：删除SAM文件

1、进入PE。
2、把“系统根目录:\Windows\repair\SAM”文件覆盖在“系统根目录:\Windows\System32\Config\SAM”文件（最好备份原来的文件，不然出现错误，得不偿失）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723195040704.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

3、重启直接进入系统，看见那久违的桌面了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723195110226.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

[百度网盘存放地址，提取码：hntm](https://pan.baidu.com/s/1p-ug0rYJerfZPvS78HoS8g)
CSDN的分享链接还要等一段时间。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200723195610393.png)
————————

## 小提示

如果在输入命令时提示权限不足，请尝试以下步骤：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724101641174.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
1、输入命令taskmgr打开任务管理器
![在这里插入图片描述](https://img-blog.csdnimg.cn/202007241017348.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、点击“文件”，然后点击“创建新进程”，弹出运行窗口
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724101850481.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、然后在文本框内输入cmd，注意要勾选以管理员权限运行的复选框
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724102000726.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
4、点击“确定”后弹出的命令提示符就是拥有管理员权限的了，输入命令即可生效。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724102124106.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
————————
手动破解Windows 密码（附）
[video(video-dhCa57ov-1595571678820)(type-youku)(url-https://player.youku.com/embed/XNDc2NTMzMDc5Mg==)(image-https://vthumb.ykimg.com/054106015F1A5EAB0000015D780E6F09)(title-Windows 系统密码手动破解方法（不借用外部程序）)]

希望对你有帮助。

