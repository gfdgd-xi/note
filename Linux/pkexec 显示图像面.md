如果按照正常使用 `pkexec` 的方法来使用：
```bash
pkexec ls /
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2fe1d265a3c641999f6a6507e583a516.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
没问题，但运行图形程序：
```bash
gfdgd_xi@gfdgd-xi-PC:~$ pkexec /home/gfdgd_xi/Documents/git/uengine-runner/main.py
Traceback (most recent call last):
  File "/home/gfdgd_xi/Documents/git/uengine-runner/main.py", line 609, in <module>
    win = tk.Tk()  # 创建窗口
  File "/usr/lib/python3.7/tkinter/__init__.py", line 2023, in __init__
    self.tk = _tkinter.create(screenName, baseName, className, interactive, wantobjects, useTk, sync, use)
_tkinter.TclError: no display name and no $DISPLAY environment variable
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/3fc5f2cb1a23483b8e5cd60bb029b825.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
解决方法如下：
```bash
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY XXX  # XXX 为命令
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f18965a59a344d0d9859b00c1e2b4b4d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)

