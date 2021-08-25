> 前一段时间学习了 deepin-wine（deepin=wine5）打包，这里遇到的几个坑记录一下


## 一、忘记修改 deb 配置文件

在打 deepin-wine（非 deepin-wine5） 的包时，会在 `DEBIAN` 目录有几个配置文件，记得修改，否则……
例如我使用的是 deepin-wine QQ 的 deb 包来修改，完成后忘记修改 DEBIAN 目录的文件，如果忘记修改 `control` 文件就直接覆盖 deepin-wine QQ，其他文件的效果就……

**小结：保证全部文件有修改以不影响其他软件**

## 二、打包的容器出现套娃或文件夹的情况

首先，我按照如下命令打包（打包的容器名为 spark-pinball 为例）：

```bash
7z a files.7z spark-pinball/
```
然后复制文件打包为 deb 后发现无法运行，报错是提示无法找到可执行文件，在排除路径填写错误后，发现容器解压后还套了一个文件夹，于是再尝试了这个命令：

```bash
7z a files.7z ~/spark-pinball/
```
结果如上，最后尝试下面这个命令才能打包出正常的容器

```bash
7z a files.7z ~/spark-pinball/*
```
但发现打包出的压缩包比容器还大，打开看后发现里面有一开始打包的套文件夹的容器和打包正常的容器，于是删除打包好的压缩包再重新打包容器

**小结：打包容器时记得删掉原来打包好的容器，并且命令后面记得要有“*”并检查是否有套娃或套文件夹的情况**



## 三、打包好的容器运行后运行的用户名是打包时的用户名

直接上截图（[点此直达](https://bbs.deepin.org/zh/post/206955)）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210113518811.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
直到现在我总是忘记做这个处理……![](https://img-blog.csdnimg.cn/img_convert/2951d862e3fa91653d1084f8ae73016f.gif#pic_center)


**小结：打包前记得输入下面这些命令**

```bash
cd 容器所在目录
sed -i "s#$USER#@current_user@#" ./*.reg
mv drive_c/users/用户名 drive_c/users/@current_user@
```


## 最后

参考：[https://bbs.deepin.org/zh/post/206955 中第 11 楼“sgb76”的回答](https://bbs.deepin.org/zh/post/206955)
