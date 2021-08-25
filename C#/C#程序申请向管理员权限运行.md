> 最近在写一个系统OEM信息修改器，但实现这个功能就需要管理员权限，不可能打开一个文本框提示用户需要右键管理员权限运行吧，于是写下了这个经验

# 准备工作

1、Visual Studio 编辑器
**2、一个高于Windows Vista的电脑（要求管理员权限的软件会显示一个小盾牌）**
3、要更改权限的程序文件

这里是以Windows 8.1，Visual Studio 2017 Enterprise为例
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080214363882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802143730496.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802143943284.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

# 正式开始

1、打开Visual Studio ，创建一个C#程序。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802144246235.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020080214554848.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

2、右键项目文件，点击“属性”（或者按下Alt+Enter）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802144357208.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
3、**点击“安全性”，先将“□启用ClickOnce”选项打开，再把它关上**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802144623322.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
4、接下来到右侧“解决方案资源管理器”，**双击“Properties”里面的“app.manifest”文件**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802144825342.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
这是该文件里的代码（可能其他电脑是不一样的）

```xml
<?xml version="1.0" encoding="utf-8"?>
<assembly manifestVersion="1.0" xmlns="urn:schemas-microsoft-com:asm.v1">
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app" />
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">
    <security>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!-- UAC 清单选项
             如果想要更改 Windows 用户帐户控制级别，请使用
             以下节点之一替换 requestedExecutionLevel 节点。n
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

            指定 requestedExecutionLevel 元素将禁用文件和注册表虚拟化。
            如果你的应用程序需要此虚拟化来实现向后兼容性，则删除此
            元素。
        -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
      <applicationRequestMinimum>
        <defaultAssemblyRequest permissionSetReference="Custom" />
        <PermissionSet class="System.Security.PermissionSet" version="1" Unrestricted="true" ID="Custom" SameSite="site" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- 设计此应用程序与其一起工作且已针对此应用程序进行测试的
           Windows 版本的列表。取消评论适当的元素，Windows 将
           自动选择最兼容的环境。 -->
      <!-- Windows Vista -->
      <!--<supportedOS Id="{e2011457-1546-43c5-a5fe-008deee3d3f0}" />-->
      <!-- Windows 7 -->
      <!--<supportedOS Id="{35138b9a-5d96-4fbd-8e2d-a2440225f93a}" />-->
      <!-- Windows 8 -->
      <!--<supportedOS Id="{4a2f28e3-53b9-4441-ba9c-d69d4a4a6e38}" />-->
      <!-- Windows 8.1 -->
      <!--<supportedOS Id="{1f676c76-80e1-4239-95bb-83d0f6d0da78}" />-->
      <!-- Windows 10 -->
      <!--<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />-->
    </application>
  </compatibility>
  <!-- 指示该应用程序可以感知 DPI 且 Windows 在 DPI 较高时将不会对其进行
       自动缩放。Windows Presentation Foundation (WPF)应用程序自动感知 DPI，无需
       选择加入。选择加入此设置的 Windows 窗体应用程序(目标设定为 .NET Framework 4.6 )还应
       在其 app.config 中将 "EnableWindowsFormsHighDpiAutoResizing" 设置设置为 "true"。-->
  <!--
  <application xmlns="urn:schemas-microsoft-com:asm.v3">
    <windowsSettings>
      <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
    </windowsSettings>
  </application>
  -->
  <!-- 启用 Windows 公共控件和对话框的主题(Windows XP 和更高版本) -->
  <!--
  <dependency>
    <dependentAssembly>
      <assemblyIdentity
          type="win32"
          name="Microsoft.Windows.Common-Controls"
          version="6.0.0.0"
          processorArchitecture="*"
          publicKeyToken="6595b64144ccf1df"
          language="*"
        />
    </dependentAssembly>
  </dependency>
  -->
</assembly>
```
5、最重要的一步，将文件里

```xml
<requestedExecutionLevel level="asInvoker" uiAccess="false" />
```
改为

```xml
<requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
```
（注释上是有标明的，默认注释是这样写的）

```xml
<!-- UAC 清单选项
             如果想要更改 Windows 用户帐户控制级别，请使用
             以下节点之一替换 requestedExecutionLevel 节点。n
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

            指定 requestedExecutionLevel 元素将禁用文件和注册表虚拟化。
            如果你的应用程序需要此虚拟化来实现向后兼容性，则删除此
            元素。
        -->
```

5、现在按下`F5`，编译程序，会提示一下情况
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802145454993.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
提示需要管理员权限了，现在定位到软件的程序生成目录，查看一下结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802145641701.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
会发现程序出现了一个小盾牌，双击程序会出现一个UAC的对话框（前提是电脑有设置UAC）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200802145848822.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

# 提示

如果将修改后的代码

```xml
<requestedExecutionLevel level="requireAdministrator" uiAccess="false" />
```
改回一开始的代码

```xml
<requestedExecutionLevel  level="asInvoker" uiAccess="false" />
```
将会打回原形哦


