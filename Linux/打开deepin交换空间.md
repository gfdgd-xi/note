> 在一些内存小的电脑上，在不开启交换空间的情况下，电脑会变的非常的卡，于是写下了这个博客


# 方法

1、按下Ctrl+Alt+T，打开终端
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200806114740839.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

2、输入以下命令（建议先输入`su`或`sudo -i`先进入root用户模式，省得后面执行命令时需要多次输入root用户密码）

```powershell
sudo dd if=/dev/zero of=/root/swapfile bs=1M count=4096
sudo mkswap /root/swapfile
sudo swapon /root/swapfile
echo "/root/swapfile swap swap defaults 0 0" | sudo tee -a /etc/fstab
```
（这里由于已经开启过了，所以显示的结果和大家不一样）
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080611531481.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

最后可以打开系统资源管理器，查看情况了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200806122117945.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
# 懒人操作

我写了一个打开交换空间的小程序，下载地址：
[CSDN下载地址：https://download.csdn.net/download/weixin_46403483/12691481](https://download.csdn.net/download/weixin_46403483/12691481)
[百度网盘下载地址，提取码: ffbw：https://pan.baidu.com/s/1F9ourHYRl05EZC4VQSQs4w](https://pan.baidu.com/s/1F9ourHYRl05EZC4VQSQs4w) 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200819193300777.png#pic_center)


源码（可以直接复制到g++编译）：

```cpp
#include <iostream>
using namespace std;
int main()
{
	cout<<"Now is open Swap, please wait some time......\n";
	// important
	// open Swap for Shell
	system("sudo dd if=/dev/zero of=/root/swapfile bs=1M count=4096 ");
	system("sudo mkswap /root/swapfile");
	system("sudo swapon /root/swapfile");
	system("echo \"/root/swapfile swap swap defaults 0 0\" | sudo tee -a /etc/fstab ");
	cout<<"\nEnd!The Swap is open!\n"; // Tips User
	return 0; // Software End
}

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200819191544511.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)


