最新的 deepin 20.2.2 带来了可以运行安卓应用的uengine环境，如下图是安装在 uengine 环境上的应用：  
![](https://img-blog.csdnimg.cn/img_convert/f06eecb0ec5f74e23e9ed29486156c9f.png)
那么这些应用不是平白无故出现的吧，肯定是需要安装的，安装有许多方法，例如说下面这些方法来安装：
# 一、应用商店

打开![](https://img-blog.csdnimg.cn/img_convert/021a32f931718eadfee9523fa1292f56.png)，定位到“安卓应用”，就有很多 Android 应用可以安装  
![](https://img-blog.csdnimg.cn/img_convert/2b848ef156ff62d65b1b5449afc2a9ce.png)
这里都应该知道怎么装了，不细讲
# 二、在终端安装

（这里需要的水平有提升，首先要知道终端是什么，这里不讲）

首先打开终端，可以用
```bash
apt search uengine
```
来获取所有的包名，但太多了，就可以通过

但可以通过这样
```bash
apt search uengine XXX
```
缩小寻找范围，如图：
![](https://img-blog.csdnimg.cn/img_convert/3f7047d2f5e88685e532b5df56266965.png)
例如说安装QQ：
```bash
sudo apt install uengine.com.tencent.mobileqq
```
安装微信：
```bash
sudo apt install uengine.com.tencent.mm
```
以及 https://bbs.deepin.org/zh/post/222286 中的包名

当然还可以在 https://home-store-packages.uniontech.com/appstore/pool/appstore/u/  中下载，安装方法看下面
# 三、使用其他人打包的 deb 安装

应用商店的包是 deb，使用 apt 的也是 deb，肯定也有人打包了 deb 供我们使用，例如说 https://bbs.chinauos.com/zh/post/7339 就有大佬打包的deb包，这里以 Microsoft Todo for Android 为例

## （一）使用图形化 deb 安装器安装

首先打开下载的 deb 目录，然后使用 deb 安装器打开，然后点击“安装”输入密码即可
![](https://img-blog.csdnimg.cn/img_convert/985f0868a64e02781d907c5c58e08989.png)

## （二）使用终端安装
适用于上面的方法无法安装时使用

首先使用 cd 目录或者使用文件管理器定位然后右键终端打开
然后使用 dpkg 命令进行安装，格式如下
```bash
sudo dpkg -i XXX  # 一定要用 root 权限运行，XXX是 deb 包的文件名
```
然后输入用户密码进行安装
![](https://img-blog.csdnimg.cn/img_convert/8e9c63da382a83a934b339120b1d38ce.png)
但如果出现了依赖问题（我实在没图了），就输入
```bash
sudo apt install -f
```
修复其依赖关系

最后打开启动器运行即可
![](https://img-blog.csdnimg.cn/img_convert/5d3102ada3c4609d398ce06644df4880.png)
# 四、使用第三方软件安装 Android 应用

目前社区有两种安装器，第一种是我开发的运行器和打包器（运行器：https://bbs.deepin.org/zh/post/222293，打包器：https://bbs.deepin.org/zh/post/222729），还有就是 Maicss 大佬开发的 https://bbs.deepin.org/zh/post/223042 （推荐），这里以 Maicss 大佬开发的为例
## （一）安装

首先下载 Maicss 大佬的 deb 包安装，安装过程忽略
![](https://img-blog.csdnimg.cn/img_convert/3092c46f14f266ac22630a6451fbf173.png)

## （二）安装自己的应用

首先打开程序主界面，把需要的 apk 拖进去，然后识别图标，然后我们因为只是自己安装，所以直接点击“直接安装”
![](https://img-blog.csdnimg.cn/img_convert/48d77c22ab8753b0e9d03369d1c13182.png)
然后提示需要输入密码，输入密码继续安装
![](https://img-blog.csdnimg.cn/img_convert/b9831b844925e5b5f64027288ac6574b.png)
当提示安装成功时，就可以打开启动器运行了
![](https://img-blog.csdnimg.cn/img_convert/66d3e7d26fe5972defb87c2b612a902d.png)

# 五、使用命令安装 Android 应用

这个限制就比较少了,首先要有一个 APK,定位到 apk所在目录,然后输入
```bash
sudo /usr/bin/uengine-session-launch-helper -- uengine install --apk='XXX' 
# XXX是apk路径,如果是用pkexec调用root权限,请输入绝对路径,而非相对路径
# 注意:安装需要root权限,请注意!
```
# 其他

**接下来就是些其他的了，毕竟是总结吗，还要其他的东西**
## 打包 deb 包给他人使用

在用第三方的安装器时，你会发现有一个打包成 deb 的功能，点击对于的按钮后就会让你选择保存位置，选择完好即可，使用它就可以打包一个属于自己的 deb 包
![](https://img-blog.csdnimg.cn/img_convert/78ef9a3c955b1e0baf994459d453a415.png)
打包后的 deb 包就可以发给其他人使用了，安装方法如上面的第三点

## 打开程序列表

在终端输入以下命令即可
```bash
/usr/bin/uengine-launch.sh --package=org.anbox.appmgr --component=org.anbox.appmgr.AppViewActivity
```
或者创建一个 .desktop 文件，把以下内容写入也可以
```bash
[Desktop Entry]
Categories=System;
Comment=uengine 程序菜单
Encoding=UTF-8n
Exec=/usr/bin/uengine-launch.sh --package=org.anbox.appmgr --component=org.anbox.appmgr.AppViewActivity
Icon=anbox
MimeType=
Name=uengine 程序菜单
StartupWMClass=uengine 程序菜单
Terminal=false
Type=Application
```
## 与 uengine 互通文件

在系统的很多地方，如桌面
![](https://img-blog.csdnimg.cn/img_convert/bdf9c43229182b5bdea6ca51c27c740e.png)
文件管理
![](https://img-blog.csdnimg.cn/img_convert/dce877bd34898d30c4bc8c08e3f4c8f5.png)
uengine 右键
![](https://img-blog.csdnimg.cn/img_convert/e84486f818d6953e8fc04f8401295805.png)
都能看到它的身影，你可以通过它和 uengine 交换文件（怎么截不了图）
![](https://img-blog.csdnimg.cn/img_convert/9f2547422344d39f9a2e788fbec8eec8.png)
但注意它访问的不是根目录，如果需要访问请安装Android的第三方文件管理器

## 卸载 Android 应用

### 1、右键卸载

有些通过 deb 或者 Maicss 大佬安装的都可以右键卸载，但有些不行，例如通过命令安装的以及用我的运行器安装的都不能用右键卸载，那么要用下面的方法

### 2、使用系统设置卸载

打开程序菜单或在终端输入
```bash
/usr/bin/uengine-launch.sh --action=android.intent.action.MAIN --package=com.android.settings --component=com.android.settings.Settings
```
 打开系统设置，然后点击应用部分
![](https://img-blog.csdnimg.cn/img_convert/84690dc6b8c58a5856e34f300838b70a.png)
然后这里就有安装的应用列表
![](https://img-blog.csdnimg.cn/img_convert/db2b3aa90ecd52712833d85df9826332.png)
然后点击进入你需要卸载的软件，然后点击卸载即可
![](https://img-blog.csdnimg.cn/img_convert/2889034847c4ad00b36a0d02e5aa0164.png)
### 3、使用第三方程序卸载

其实就指的是我的运行器，安装方法和Maicss 大佬的安装方法一样，然后打开运行器，选择要卸载软件对应的apk包或对应的包名（包名的获取方法请看下一点），输入密码卸载即可
![](https://img-blog.csdnimg.cn/img_convert/b70736922c633d6ab72defe1eac70282.png)
### 4、使用终端卸载

首先获取包名（需要有对应的 APK）（如果知道包名请忽略），首先安装 appt
```bash
sudo apt install aapt
```
然后定位到APK所在目录，输入
```bash
aapt dump badging XXX  # XXX为APK路径
```
获取 APK 信息，然后找到“package:”开头的那一行，找到“name”后面的那个包名

![点击并拖拽以移动](https://img-blog.csdnimg.cn/img_convert/acd373be72336e7fcef0f56cb6c635ab.png)

然后输入
```bash
sudo /usr/bin/uengine-session-launch-helper -- uengine uninstall --pkg='XXX'
# XXX 为包名
# 可以使用sudo或者pkexec，需要 root 权限卸载
```
![](https://img-blog.csdnimg.cn/img_convert/acd373be72336e7fcef0f56cb6c635ab.png)

即可

# 出现运行故障

部分 Android 软件是无法运行的，你可以去 anbox 的 Issues 去看看有没有解决方案，因为 uengine 是在 anbox 上二次开发

项目链接：https://github.com/anbox/anbox/
​