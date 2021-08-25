> 之前尝试给自己的Ubuntu 
> 20添加Deepin的桌面，但出现如下面的情况
> 
> ```bash gfdgd_xi@gfdgd-xi-Vostro-220s-Series:~/桌面$ sudo
> add-apt-repository ppa:leaeasy/dde [sudo] gfdgd_xi 的密码：   You can
> install deepin desktop environment by run
> 
> sudo add-apt-repository ppa:leaeasy/dde sudo apt-get update apt-get
> install dde
> ------ Ubuntu Bionic: https://drive.google.com/file/d/1xkQPb4tWocknuYeY-t41W--kz-9SSL0V/view?usp=sharing
> ------ Important Issue: Q: Can dde on Ubuntu 16.04? A: Sorry, the dde depends on qt version above than 5.6.
>      If you want to install dde, please upgrade to 17.04 or above.  更多信息： https://launchpad.net/~leaeasy/+archive/ubuntu/dde 按 [ENTER] 继续或
> Ctrl-c 取消安装。
> 
> 命中:1 http://mirrors.aliyun.com/ubuntu focal InRelease 命中:2
> http://mirrors.aliyun.com/ubuntu focal-security InRelease 命中:3
> http://mirrors.aliyun.com/ubuntu focal-updates InRelease 命中:4
> http://mirrors.aliyun.com/ubuntu focal-proposed InRelease 命中:5
> http://mirrors.aliyun.com/ubuntu focal-backports InRelease 忽略:6
> http://ppa.launchpad.net/leaeasy/dde/ubuntu focal InRelease 错误:7
> http://ppa.launchpad.net/leaeasy/dde/ubuntu focal Release   404  Not
> Found [IP: 91.189.95.83 80] 正在读取软件包列表... 完成 
> E: 仓库 “http://ppa.launchpad.net/leaeasy/dde/ubuntu focal Release” 没有 Release 文件。
> N: 无法安全地用该源进行更新，所以默认禁用该源。
> N: 参见 apt-secure(8) 手册以了解仓库创建和用户配置方面的细节。
> gfdgd_xi@gfdgd-xi-Vostro-220s-Series:~/桌面$ 
> ```
> 
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809123429908.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
> 安装失败，以后更新原的时候都会提示以下信息
> ```bash 
> gfdgd_xi@gfdgd-xi-Vostro-220s-Series:~/桌面$ sudo apt update
> [sudo] gfdgd_xi 的密码：  命中:1 http://mirrors.aliyun.com/ubuntu focal
> InRelease 命中:2 http://mirrors.aliyun.com/ubuntu focal-security
> InRelease 命中:3 http://mirrors.aliyun.com/ubuntu focal-updates
> InRelease 命中:4 http://mirrors.aliyun.com/ubuntu focal-proposed
> InRelease 命中:5 http://mirrors.aliyun.com/ubuntu focal-backports
> InRelease 忽略:6 http://ppa.launchpad.net/leaeasy/dde/ubuntu focal
> InRelease 错误:7 http://ppa.launchpad.net/leaeasy/dde/ubuntu focal
> Release   404  Not Found [IP: 91.189.95.83 80] 正在读取软件包列表... 完成 E: 仓库
> “http://ppa.launchpad.net/leaeasy/dde/ubuntu focal Release” 没有 Release
> 文件。 N: 无法安全地用该源进行更新，所以默认禁用该源。 N: 参见 apt-secure(8) 手册以了解仓库创建和用户配置方面的细节。
> gfdgd_xi@gfdgd-xi-Vostro-220s-Series:~/桌面$ 
> ```
> 
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809130202614.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
> 而且以后更新系统也很慢，于是就需要删除这个PPA库

# 步骤

1、打开终端
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809130517888.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

2、定位到`/etc/apt/sources.list.d`，也就是输入命令

```bash
cd /etc/apt/sources.list.d/
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809130639239.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

3、输入命令

```bash
ls
```
查看目录下所有文件，这里显示的结果如下

```bash
gfdgd_xi@gfdgd-xi-Vostro-220s-Series:/etc/apt/sources.list.d$ ls
leaeasy-ubuntu-dde-focal.list       vscode.list.save
leaeasy-ubuntu-dde-focal.list.save
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809130835174.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
4、你会发现这里就是存放PPA库所在的地方，根据需求删除即可，这里以全部删除为例
命令：

```bash
sudo rm -rf *
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809131038916.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)删除后可以输入命令

```bash
sudo apt-get update
```
查看结果

```bash
gfdgd_xi@gfdgd-xi-Vostro-220s-Series:/etc/apt/sources.list.d$ sudo apt-get update
命中:1 http://mirrors.aliyun.com/ubuntu focal InRelease
命中:2 http://mirrors.aliyun.com/ubuntu focal-security InRelease
命中:3 http://mirrors.aliyun.com/ubuntu focal-updates InRelease
命中:4 http://mirrors.aliyun.com/ubuntu focal-proposed InRelease
命中:5 http://mirrors.aliyun.com/ubuntu focal-backports InRelease
正在读取软件包列表... 完成                            
gfdgd_xi@gfdgd-xi-Vostro-220s-Series:/etc/apt/sources.list.d$ 
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200809131244231.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
