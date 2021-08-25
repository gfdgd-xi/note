在调试程序时，在以下句子出现错误

```csharp
private void th()
        {
            Speech speech = new Speech();
            speech.Save("1.mp3",textBox1.Text, trackBar1.Value, trackBar2.Value);
        }
```
错误提示：
System.InvalidOperationException:“Cross-thread operation not valid: Control 'trackBar1' accessed from a thread other than the thread it was created on.”
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200724191452133.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
解决方法有两种：
1、在程序初始化模块

```csharp
        public Form1()
        {
            InitializeComponent();
        }
```
输入以下语句：

```csharp
CheckForIllegalCrossThreadCalls = false;
```
2、将出错语句放在下面代码的大括号里

```csharp
this.BeginInvoke(new Action(delegate()
                {
                
                }));
```

