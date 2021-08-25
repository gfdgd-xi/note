> 最近逐渐向Linux系统转型，但由于自己不想抛弃学习一段时间的C#语言（主要入门没C++难），了解到了Mono这个开源项目，于是转向Mono开发。
> 但是，开始的第一步就出现了情况，就如标题所说，**Mono C# TextView 没有 Text属性**，于是经过几天的研究，找到了解决方法
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200821164546660.png#pic_center)


# 测试/调试平台

系统：Ubuntu 20.04.1 LTS
编辑器：MonoDevelop 5.10（使用阿里云Ubuntu源安装）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200821164419540.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200821164431471.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)



# 解决方法

在官方文档查看时，偶然发现一行代码，给我了启发（[https://www.monodevelop.com/documentation/stetic-gui-designer/](https://www.monodevelop.com/documentation/stetic-gui-designer/)）：

```csharp
protected virtual void OnOpen(object sender, System.EventArgs e)
{
   // Reset the logTreeView and change the window back to original size
   int width, height;
   this.GetDefaultSize( out width, out height );
   this.Resize( width, height );

   logTextView.Buffer.Text = "";

   // Create and display a fileChooserDialog
   FileChooserDialog chooser = new FileChooserDialog(
      "Please select a logfile to view ...",
      this,
      FileChooserAction.Open,
      "Cancel", ResponseType.Cancel,
      "Open", ResponseType.Accept );

   if( chooser.Run() == ( int )ResponseType.Accept )
   {
      // Open the file for reading.
      System.IO.StreamReader file =
      System.IO.File.OpenText( chooser.Filename );

      // Copy the contents into the logTextView
      logTextView.Buffer.Text = file.ReadToEnd();

      // Set the MainWindow Title to the filename.
      this.Title = "Nate's Log Viewer -- " + chooser.Filename.ToString();

      // Make the MainWindow bigger to accomodate the text in the logTextView
      this.Resize( 640, 480 );

      // Close the file so as to not leave a mess.
      file.Close();
   } // end if
   chooser.Destroy();
} // end method OnOpen

For the OnClose method:

protected virtual void OnClose(object sender, System.EventArgs e)
{
   // Reset the logTreeView and change the window back to original size
   int width, height;
   this.GetDefaultSize( out width, out height );
   this.Resize( width, height );

   logTextView.Buffer.Text = "";

   // Change the MainWindow Title back to the default.
   this.Title = "Nate's Log Viewer";
} // end method OnClose

```

其中`logTextView.Buffer.Text = "";`这一行代码给我了启发，因为在官方文档里，logTextView是一个TextView控件，且这是赋值代码
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200821165410613.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)所以，将上方代码修改如下：

```csharp
Build ();
textview1.Buffer.Text = "Text";
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200821165616259.png#pic_center)
即可成功编译。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200821165705398.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)






