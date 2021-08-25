这是用Windows自带的Microsoft Speech引用做成的，使用前要先添加System.Speech的引用，然后导入头文件System.Speech.Synthesis
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020072419235032.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


```csharp
/// <summary>
        /// 用Microsoft Speech制成的类
        /// </summary>
        public class Speech
        {
            SpeechSynthesizer speech = new SpeechSynthesizer();
            /// <summary>
            /// 文字转语言
            /// </summary>
            /// <param name="say">要朗读的文本</param>
            /// <param name="volume">音量（0~100）</param>
            /// <param name="yusu">语速（-10~10）</param>
            public void Say(string say = "文字转语言", int volume = 100, int yusu = 0)
            {
                speech.Volume = volume; // 设置音量
                speech.Rate = yusu;     // 设置语速
                speech.SetOutputToDefaultAudioDevice();
                speech.Speak(say);      // 朗读文本
                speech.Dispose();       // 释放资源
            }
            /// <summary>
            /// 将朗读文本转为WAV文件
            /// </summary>
            /// <param name="path">保存位置</param>
            /// <param name="saythings">要朗读的文本</param>
            /// <param name="volume">音量（0~100）</param>
            /// <param name="yusu">语速（-10~10）</param>
            public void Save(string path, string saythings = "文字转语言", int volume = 100, int yusu=0)
            {
                speech.SetOutputToWaveFile(path);        // 保存位置
                speech.Rate = yusu;                      // 设置语速
                speech.Volume = volume;                  // 设置音量
                speech.Speak(saythings);            // 读文本
                speech.SetOutputToDefaultAudioDevice();
            }
        }
```


朗读文本的调用方法：

```csharp
Speech speech = new Speech();
speech.Say("朗读文本", 100, 0);
// 其中“"朗读文本"”是要朗读的文本，
// “100”是朗读的音量，从0到100，注意是int类型
// “0”是朗读的语速，范围从-10到10，注意是int类型
```
保存音频文件的调用方法：

```csharp
Speech speech = new Speech();
speech.Save("保存路径","朗读文本", 100, 0);
// 其中“"保存路径"”是把音频文件保存的路径
// “"朗读文本"”是要朗读的文本，
// “100”是朗读的音量，从0到100，注意是int类型
// “0”是朗读的语速，范围从-10到10，注意是int类型
```
实例代码：

```csharp
/* 
 ************************************************************************
 * 程序信息：                                                           *
 *     更改/修改时间：2020年7月24日19:37:16                             *
 *     作者：gfdgd xi                                                   *
 *     调试平台：Visual Studio 2019 Professional 以及 Windows 8.1       *
 *     程序目的：通过 Windows 自带的 Speech 来朗读文本                  *
 ************************************************************************
 */
// 导入头文件
using System;
using System.Windows.Forms;
using System.Speech.Synthesis; // 重点是这个头文件！要加入“System.Speech”的引用
// using System.Collections.Generic;
// using System.ComponentModel;
// using System.Data;
// using System.Drawing;
// using System.Linq;
// using System.Text;
// 这些头文件和程序没什么关系，所以就注释掉了

namespace 语言转文本 // 命名空间
{
    public partial class Form1 : Form
    {
        public Form1() // 实例化程序
        {
            InitializeComponent();
        }
        /// <summary>
        /// 用Microsoft Speech制成的类
        /// </summary>
        public class Speech
        {
            SpeechSynthesizer speech = new SpeechSynthesizer();
            /// <summary>
            /// 文字转语言
            /// </summary>
            /// <param name="say">要朗读的文本</param>
            /// <param name="volume">音量（0~100）</param>
            /// <param name="yusu">语速（-10~10）</param>
            public void Say(string say = "文字转语言", int volume = 100, int yusu = 0)
            {
                speech.Volume = volume; // 设置音量
                speech.Rate = yusu;     // 设置语速
                speech.SetOutputToDefaultAudioDevice();
                speech.Speak(say);      // 朗读文本
                speech.Dispose();       // 释放资源
            }
            /// <summary>
            /// 将朗读文本转为WAV文件
            /// </summary>
            /// <param name="path">保存位置</param>
            /// <param name="saythings">要朗读的文本</param>
            /// <param name="volume">音量（0~100）</param>
            /// <param name="yusu">语速（-10~10）</param>
            public void Save(string path, string saythings = "文字转语言", int volume = 100, int yusu=0)
            {
                speech.SetOutputToWaveFile(path);        // 保存位置
                speech.Rate = yusu;                      // 设置语速
                speech.Volume = volume;                  // 设置音量
                speech.Speak(saythings);            // 读文本
                speech.SetOutputToDefaultAudioDevice();
            }
        }
        private void button1_Click(object sender, EventArgs e)
        {
            Speech speech = new Speech();
            speech.Say(textBox1.Text, trackBar1.Value, trackBar2.Value); // 播放音频
        }

        private void button2_Click(object sender, EventArgs e)
        {
            if(saveFileDialog1.ShowDialog()
                ==
                DialogResult.OK)
                // 如果用户在另存为对话框点击了“确定”
            {
                Speech speech = new Speech();
                speech.Save(saveFileDialog1.FileName, textBox1.Text, trackBar1.Value, trackBar2.Value); // 另存为音频
                MessageBox.Show("保存完成！", "提示", MessageBoxButtons.OK, MessageBoxIcon.Information); // 完成后提示结果
            }
        }
    }
}

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724195022275.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

