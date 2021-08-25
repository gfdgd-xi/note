# 引入
> 在品牌机的系统属性上一般都会有自己的OEM信息，如图
> （这是网上找的图片）![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802175935614.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
> 但是，对于部分用户来说，电脑就不会有这些OEM信息了（如组装机、重置系统后的系统等等），但这就可以找到方法（甚至可以造出个人品牌）。


# 准备工作

1、**一个Windows Vista及以上版本的Windows**（因为Windows XP的OEM显示方法不一样）
2、注册表编辑器（如果懒可以使用最后通过自制的OEM信息修改器）

# 手工修改

1、按下“Windows+R”键，打开“运行”窗口
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080218042751.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、输入命令“regedit”打开注册表编辑器（如果你在系统的Windows文件夹里找也没问题）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802180538193.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802180610772.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080218064578.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、定位到`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OEMInformation`，**如果没有该项就新建**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802180905721.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
4、根据需求创建字符串值
|值项说明| 字符串值名称 | 填的内容 |
|--|--|--|
|OEM图片| Logo | OEM图片所在位置（一般为绝对路径，**注意别填错了**） |
|电脑型号|Manufacturer|随便填|
|电脑型号|Model|随便填，看起来正常即可|
|技术支持电话|SupportPhone|随便填，建议填电话，看起来正常点|
|技术支持时间|SupportHours|随便填，建议填时间|
|技术支持网站|SupportURL|**填网址，不然点击后用浏览器打不开**|

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802181928263.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
5、如果有设置OEM图片显示的话，要将图片拷贝在对应的目录里
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802182100152.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080218213694.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

# 工具修改

1、下载OEM修改工具，然后运行它
[百度网盘下载地址，提取码：fh5m](https://pan.baidu.com/s/1bVVqdx1oQ3OzOZ_wH35Fxg)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802182609716.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、根据提示进行设置
（最后一个选项“技术支持选项（Technical support information”打错了，应该是“技术支持网站”）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802182840257.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、点击“设置（Setting）”，如看到提示窗，及更改成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802182932161.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802183013862.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

# OEM信息删除

再好的内容也会看腻，所以也通过了删除的方法

**手工删除方法：**
1、打开注册表编辑器，定位到`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OEMInformation`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802183612908.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
2、将里面的值项全部或部分删除就可以达到结果了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802183702443.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802183734691.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
**软件删除法：**
1、下载上方通过的OEM修改工具
2、由于打开后所有内容都是为空的，所以直接点击“设置”即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802183908705.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802183946220.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


# OEM修改器源码

O(∩_∩)O哈哈~我这人挺好的，不止把源码贴出来，还可以给大家下
（**其实源码文件就在上面那个分享链接里↑**）

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.Win32;

namespace OEM
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            if (openFileDialog1.ShowDialog() == DialogResult.OK) // 如果用户选择了文件
            {
                try
                {
                    pictureBox1.Image = new Bitmap(openFileDialog1.FileName); // 打开图片
                }
                catch(Exception ex) // 如果有错误
                {
                    MessageBox.Show(ex.Message, "错误(Error)", MessageBoxButtons.OK, MessageBoxIcon.Error); // 提示错误信息
                }
            }
        }

        private void button4_Click(object sender, EventArgs e)
        {
            textBox1.Text = ""; // 将文本框清空
            textBox2.Text = "";
            textBox3.Text = "";
            textBox4.Text = "";
            textBox5.Text = "";
            pictureBox1.Image = null; // 将图片显示控件设置为空
        }

        private void button1_Click(object sender, EventArgs e)
        {
            this.Close(); // 退出程序
        }

        private void button2_Click(object sender, EventArgs e)
        {
            try
            {
                string Windows = Environment.GetFolderPath(Environment.SpecialFolder.Windows); // 获取系统“Windows”文件夹所在路径
                RegistryKey OEM = Registry.LocalMachine; // 定位到HKEY_LOCAL_MACHINE项
                RegistryKey OEMs = OEM.OpenSubKey("SOFTWARE\\Microsoft\\Windows\\CurrentVersion", true); // 定位到SOFTWARE\Microsoft\Windows\CurrentVersion
                OEMs.DeleteSubKeyTree("OEMInformation"); // 删除OEMInformation值项，确定系统不会有任何OEM信息
                OEM = OEMs.CreateSubKey("OEMInformation"); // 创建OEMInformation值项
                if (pictureBox1.Image != null) // 如果用户选择了图片
                {
                    OEM.SetValue("Logo", Windows + "\\OEM.bmp"); // 创建对应的值项
                    pictureBox1.Image.Save(Windows + "\\OEM.bmp", System.Drawing.Imaging.ImageFormat.Bmp); // 将图片保存在系统根目录
                }
                if (textBox1.Text != "") // 如果设置了制造商名称
                {
                    OEM.SetValue("Manufacturer", textBox1.Text); // 创建对应的值项
                }
                if (textBox2.Text != "") // 如果设置了电脑行号名称
                {
                    OEM.SetValue("Model", textBox2.Text); // 创建对应的值项
                }
                if (textBox3.Text != "") // 如果设置了技术支持电话
                {
                    OEM.SetValue("SupportPhone", textBox3.Text); // 创建对应的值项
                }
                if (textBox4.Text != "") // 如果设置了技术支持时间
                {
                    OEM.SetValue("SupportHours", textBox4.Text); // 创建对应的值项
                }
                if (textBox1.Text != "") // 如果设置了技术支持网站
                {
                    OEM.SetValue("SupportURL", textBox5.Text); // 创建对应的值项
                }
                MessageBox.Show("OEM信息设置完毕！重新开启系统属性就可以查看结果。\nOEM information set up! Re open the system properties to see the results.", 
                    "提示(Tips)",
                    MessageBoxButtons.OK, 
                    MessageBoxIcon.Information); // 提示结果
            }
            catch(Exception ex) // 如果在执行过程中出现错误
            {
                MessageBox.Show(ex.Message,
                    "错误(Error)", 
                    MessageBoxButtons.OK, 
                    MessageBoxIcon.Error); // 提示错误信息
            }
        }
    }
}

```
# 效果图

Windows Vista：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802185335101.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080218532450.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
Windows 7：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802185823476.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802185830754.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

Windows 8.1：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802185928199.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802190016829.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)



# 感谢

非常感谢百度对该程序提供的软件翻译工作
[百度官网](https://www.baidu.com/)
[百度翻译官网](http://fanyi.baidu.com)

# 二更

对于想要上面程序的C#的代码，但苦恼于核心代码镶嵌在代码里的烦恼，这下有办法了，我专门写了一个类，有兴趣的同学**可以直接复制**（没听错，直接复制，当然前提你会调用类和方法）
代码如下（注释在这里显示比较差，下面会提供截图）：

```csharp
class OEM
        {
            // 通过修改“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OEMInformation”里面对应的选项来修改OEM信息
            //
            //  +--------------+--------------+--------------------------------------------------+
            //  |   值项说明   |    值项名称  |                     可以填的内容                 |
            //  +--------------+--------------+--------------------------------------------------+
            //  |    OEM图片   |      Logo    |   OEM图片所在位置（一般为绝对路径，注意别填错了）|
            //  +--------------+--------------+--------------------------------------------------+
            //  |  电脑开发商  | Manufacturer |                                                  |
            //  +--------------+--------------+                                                  |
            //  |   电脑型号   |    Model     |                                                  |
            //  +--------------+--------------+                       随便                       |
            //  | 技术支持电话 | SupportPhone |                                                  |
            //  +--------------+--------------+                                                  |
            //  | 技术支持时间 | SupportHours |                                                  |
            //  +--------------+--------------+--------------------------------------------------+
            //  | 技术支持网站 |  SupportURL  |            填网址，不要填成其他东西了            |
            //  +--------------+--------------+--------------------------------------------------+
            //
            static string Windows = Environment.GetFolderPath(Environment.SpecialFolder.System); // 获取系统文件所在路径
            static RegistryKey OE = Registry.LocalMachine; // 定位到HKEY_LOCAL_MACHINE项
            static RegistryKey OEMs = OE.CreateSubKey("SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\OEMInformation");
            // 然后新建“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OEMInformation”
            // 原变量报废（OE）
            /// <summary>
            /// 设置OEM图标
            /// </summary>
            /// <param name="picture">要设置的图片（不是图片路径）</param>
            public void 更改OEM图片(Bitmap picture = null)
            {
                OEMs.SetValue("Logo", Windows + "\\OEM.bmp"); // 创建对应的值项
                picture.Save(Windows + "\\OEM.bmp", ImageFormat.Bmp); // 将图片保存到指定位置
            }
            /// <summary>
            /// 设置OEM制造商
            /// </summary>
            /// <param name="name">制造商名称</param>
            public void 更改制作商(string name)
            {
                OEMs.SetValue("Manufacturer", name);
            }
            /// <summary>
            /// 设置OEM电脑型号
            /// </summary>
            /// <param name="name">电脑型号名称</param>
            public void 更改电脑型号(string name)
            {
                OEMs.SetValue("Model", name);
            }
            /// <summary>
            /// 设置OEM电脑技术支持电话
            /// </summary>
            /// <param name="name">技术支持电话</param>
            public void 更改技术支持电话(string name)
            {
                OEMs.SetValue("SupportPhone", name);
            }
            /// <summary>
            /// 设置OEM技术支持时间
            /// </summary>
            /// <param name="name">技术支持时间</param>
            public void 更改技术支持时间(string name)
            {
                OEMs.SetValue("SupportHours", name);
            }
            /// <summary>
            /// 设置OEM技术支持网站
            /// </summary>
            /// <param name="name">技术支持网站</param>
            public void 更改技术支持网站(string name)
            {
                OEMs.SetValue("SupportURL", name);
            }
            /// <summary>
            /// 清空OEM信息（这里能设置的信息，其他不能清空）
            /// </summary>
            public void 清空OEM信息()
            { 
                // 删除所有有关信息
                OEMs.DeleteValue("Logo");
                OEMs.DeleteValue("Manufacturer");
                OEMs.DeleteValue("Model");
                OEMs.DeleteValue("SupportPhone");
                OEMs.DeleteValue("SupportHours");
                OEMs.DeleteValue("SupportURL");
            }
        }
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080718054739.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


