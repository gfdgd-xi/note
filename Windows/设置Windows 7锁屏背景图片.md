> 最近使用Windows 7时，看腻了默认的背景图片，想着如何更换（注意，锁屏是无法截图的），于是写下了这篇博客

# 软件操作

最简便的就是软件操作了，程序截图扔上来
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200812172618395.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)

下载链接也得留吧，不然大家怎么下载呢？
[https://gfdgdxi.lanzous.com/b01o4j99c，密码:7oha（推荐）](https://gfdgdxi.lanzous.com/b01o4j99c)
[坑人百度网盘下载链接，提取码：vc2o](https://pan.baidu.com/s/1eChhgV-s_uI0xS100sZcMQ)
可能有些人对源码感兴趣，这里扔出这个窗口的原代码（虽然没啥用）

```csharp
/*
 ****************************************************************************************
 * 窗体信息：                                                                           *
 *     作者：gfdgd xi                                                                   *
 *     调试平台：Visual Studio 2017 Enterprise 以及 Windows 8.1（+ Windows 7 虚拟机）   *
 *     作用：修改电脑的锁屏壁纸（只限 Windows 7）                                       *
 ****************************************************************************************
  */
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.IO;
using System.Security.AccessControl;
using System.Drawing.Imaging;
using System.Diagnostics;
using Microsoft.Win32;

namespace 系统个性化
{
    public partial class Windows_s_Wallpaper : Form
    {
        /*
         ********************
         * 程序启动事件     *
         * 获取锁屏背景图片 *
         ********************
         */
        public Windows_s_Wallpaper()
        {
            InitializeComponent();
            resolution.Text = "电脑分辨率(Computer resolution )："+SystemInformation.PrimaryMonitorSize.Width + "×" + SystemInformation.PrimaryMonitorSize.Height; // 获取屏幕分辨率
        }
        /*
         ***********************************
         * 浏览按钮事件                    *
         * 用于获取用户想要设置的背景图片  *
         ***********************************
         */
        private void brower_Click(object sender, EventArgs e)
        {
            if(openFileDialog1.ShowDialog() == 
                DialogResult.OK) // 如果用户选择了文件并点击了确定
            {
                try
                {
                    settingwallpaper.Image = new Bitmap(openFileDialog1.FileName); // 读取用户打开的图片
                }
                catch(Exception ex) // 如果读取有错误（及有可能图片有问题）
                {
                    MessageBox.Show(ex.Message, 
                        "错误(Error)", 
                        MessageBoxButtons.OK, 
                        MessageBoxIcon.Error); // 提示错误信息
                }
            }
        }
        /*
         ***************************
         * 设置按钮事件            *
         * 用于设置系统背景图片    *
         * 核心内容                *
         ***************************
         */
        private void settingbutton_Click(object sender, EventArgs e)
        {
            try
            {
                switch(checkBox1.Checked)
                {
                    case false:
                        Directory.CreateDirectory(Environment.SystemDirectory + "\\oobe\\info\\backgrounds");
                        Changefile(Environment.SystemDirectory + "\\oobe\\info"); // 设置文件权限为完全访问权限
                        settingwallpaper.Image.Save(Environment.SystemDirectory + "\\oobe\\info\\backgrounds\\backgroundDefault.jpg", ImageFormat.Jpeg); // 保存背景图片
                        // 修改注册表
                        RegistryKey im = Registry.LocalMachine;
                        RegistryKey lo = im.OpenSubKey("Software\\Microsoft\\Windows\\CurrentVersion\\Authentication\\LogonUI", true);
                        RegistryKey back = lo.CreateSubKey("Background");
                        back.SetValue("OEMBackground", 1, RegistryValueKind.DWord);
                        break;
                    default:
                        // 修改注册表
                        im = Registry.LocalMachine;
                        lo = im.OpenSubKey("Software\\Microsoft\\Windows\\CurrentVersion\\Authentication\\LogonUI", true);
                        back = lo.CreateSubKey("Background");
                        back.SetValue("OEMBackground", 0, RegistryValueKind.DWord);
                        break;
                }
                MessageBox.Show("完成(OK)", 
                    "提示(Tips)", 
                    MessageBoxButtons.OK, 
                    MessageBoxIcon.Information); // 提示信息
            }
            catch(Exception ex) // 如果出现错误
            {
                MessageBox.Show(ex.Message,
                    "错误(Error)",
                    MessageBoxButtons.OK,
                    MessageBoxIcon.Error); // 提示错误信息
            }
        }
        /// <summary>
        /// 通过命令提示符更改用户权限
        /// </summary>
        /// <param name="file">要更改权限的文件或文件夹所在路径</param>
        public void Changefile(string file)
        {
                Process CmdProcess = new Process();
                CmdProcess.StartInfo.FileName = "cmd.exe";
                CmdProcess.StartInfo.CreateNoWindow = true;         // 不创建新窗口    
                CmdProcess.StartInfo.UseShellExecute = false;       //不启用shell启动进程  
                CmdProcess.StartInfo.RedirectStandardInput = true;  // 重定向输入    
                CmdProcess.StartInfo.RedirectStandardOutput = true; // 重定向标准输出    
                CmdProcess.StartInfo.RedirectStandardError = true;  // 重定向错误输出  
                CmdProcess.StartInfo.Arguments = "/c " + "icacls "+file+" /t /grant:r everyone:f";//“/C”表示执行完命令后马上退出  
                CmdProcess.Start();//执行  
                CmdProcess.WaitForExit();//等待程序执行完退出进程  
                CmdProcess.Close();//结束 
        }
        /*
         ******************************************
         * 选择框事件                             *
         * 用于确定用户是否想要设置自定义背景图片 *
         ******************************************
         */
        private void checkBox1_CheckedChanged(object sender, EventArgs e)
        {
            switch(checkBox1.Checked)
            {
                case true:
                    brower.Enabled = false; // 不让用户选择自定义背景图片
                    settingwallpaper.Enabled = false; // 禁用图片控件
                    break;
                default:
                    brower.Enabled = true; // 允许用户选择自定义背景图片
                    settingwallpaper.Enabled = true; // 启用图片控件
                    break;
            }
        }
    }
}

```


# 手工修改

相信有些人看不懂吧，又想知道怎么做的，下面就是方法：
1、打开注册表编辑器（按下Windows+R键，输入“regedit”即可打开注册表编辑器）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200812172952964.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
2、定位到 “HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Authentication\LogonUI”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200812173009502.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)



3、在刚刚定位到的值项**新建或修改“Background”值项的值为1（DWORD）**（0为显示系统默认图片，改为0就没用了）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200812173021316.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)



4、然后把**要设置的图片保存在“系统盘（一般为C盘）\Windows\System32\oobe\info\backgrounds”文件夹（如果没有就新建）**，然后将要设置的图片**重命名为“backgroundDefault.jpg”**（**注意图片大小要小于200KB**，不然只会显示系统默认的图片，格式为JPG）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200812173041669.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)

5、锁定查看效果

