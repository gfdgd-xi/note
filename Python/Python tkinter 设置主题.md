**开头说明：设置的主题只对使用`tkinter.ttk`创建的控件有效**

## 安装库

```bash
sudo apt install python3-tk python3-pip   # 安装 tkinter 和 pip（对于 debian 发行版及其分支）
pip3 install ttkthemes  # 重点在此
```

## 获取主题

```python
import ttkthemes         # 用于设置主题
print(ttkthemes.THEMES)  # 获取主题列表并打印
```

```bash
gfdgd_xi@gfdgd-xi-PC:~/Documents/vscode$ /usr/bin/python3 /home/gfdgd_xi/Documents/Python/example/CSDN/ttkthemes/GetThemes.py 
['adapta', 'aquativo', 'arc', 'black', 'blue', 'breeze', 'clearlooks', 'elegance', 'equilux', 'itft1', 'keramik', 'kroc', 'plastik', 'radiance', 'scidblue', 'scidgreen', 'scidgrey', 'scidmint', 'scidpink', 'scidpurple', 'scidsand', 'smog', 'ubuntu', 'winxpblue', 'yaru']
```
![主题列表](https://img-blog.csdnimg.cn/d3498044e71f4f83ab2010c53480d6c1.png)


## 模板

```python
import tkinter as tk                   # 用于创建窗口
import tkinter.ttk as ttk              # 用于创建控件
import ttkthemes                       # 用于设置主题
window = tk.Tk()                       # 创建窗口实例
window.geometry("800x600")             # 设置窗口大小（可略），有控件这个可以不用
win = ttk.Frame(window)                # 因为 ttkthemes 设置的主题对 tkinter 创建的窗口没有效果，
                                       # 并且部分主题要设置背景
                                       # 所以创建一个 ttk.Frame 承载控件
style = ttkthemes.ThemedStyle(window)  # 设置需要设置主题的窗口
style.set_theme("ubuntu")              # 向对应窗口设置主题
'''
创建控件，省略
'''
win.pack()                             # 显示用于承载控件的 ttk.Frame
window.mainloop()                      # 常驻窗口
```
![例子截图](https://img-blog.csdnimg.cn/6ac246bb1ba84e14833c3dce744b9080.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
看起来好像没什么变化，但如果创建一些控件呢？


## 例子

```python
import tkinter as tk                                                   # 用于创建窗口
import tkinter.ttk as ttk                                              # 用于创建控件
import tkinter.messagebox as messagebox                                # 用于创建对话框
import ttkthemes                                                       # 用于设置主题
                                                                       #
def ButtonClick():                                                     # 创建一个函数，用途：
    messagebox.showinfo(title="Hello World!", message="Hello World!")  # 显示一个对话框
                                                                       #
window = tk.Tk()                                                       # 创建窗口实例
win = ttk.Frame(window)                                                # 因为 ttkthemes 设置的主题对 tkinter 创建的窗口没有效果，
                                                                       # 并且部分主题要设置背景
                                                                       # 所以创建一个 ttk.Frame 承载控件
style = ttkthemes.ThemedStyle(window)                                  # 设置需要设置主题的窗口
style.set_theme("ubuntu")                                              # 向对应窗口设置主题
label = ttk.Label(win, text="Hello World!")                            # 创建一个 Label 标签
progress = ttk.Progressbar(win)                                        # 创建一个 progress 进度条
button = ttk.Button(win, text="Hello World!", command=ButtonClick)     # 创建一个 button 按钮
progress['value'] = 50                                                 # 设置进度条的值
label.pack()                                                           # 显示 label 标签
progress.pack()                                                        # 显示进度条
button.pack()                                                          # 显示按钮
win.pack()                                                             # 显示用于承载控件的 ttk.Frame
window.mainloop()                                                      # 常驻窗口
```
效果：
![效果图](https://img-blog.csdnimg.cn/41868fa409714084b17d555653a96f53.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)
如果不用主题（不用主题的代码扔在最后）
![去掉主题](https://img-blog.csdnimg.cn/e58a1c20893f41c0bf3b42fe25680d02.png)
差别好明显……

## 结尾
这里还有一个有关这个点例子：[系统资源查看小工具](https://gitee.com/gfdgd-xi/CPU-And-RAW/)，也用到了 ttkthemes

```python
import tkinter as tk                                                   # 用于创建窗口
import tkinter.ttk as ttk                                              # 用于创建控件
import tkinter.messagebox as messagebox                                # 用于创建对话框
import ttkthemes                                                       # 用于设置主题
                                                                       #
def ButtonClick():                                                     # 创建一个函数，用途：
    messagebox.showinfo(title="Hello World!", message="Hello World!")  # 显示一个对话框
                                                                       #
window = tk.Tk()                                                       # 创建窗口实例
win = ttk.Frame(window)                                                # 因为 ttkthemes 设置的主题对 tkinter 创建的窗口没有效果，
                                                                       # 并且部分主题要设置背景
                                                                       # 所以创建一个 ttk.Frame 承载控件
label = ttk.Label(win, text="Hello World!")                            # 创建一个 Label 标签
progress = ttk.Progressbar(win)                                        # 创建一个 progress 进度条
button = ttk.Button(win, text="Hello World!", command=ButtonClick)     # 创建一个 button 按钮
progress['value'] = 50                                                 # 设置进度条的值
label.pack()                                                           # 显示 label 标签
progress.pack()                                                        # 显示进度条
button.pack()                                                          # 显示按钮
win.pack()                                                             # 显示用于承载控件的 ttk.Frame
window.mainloop()                                                      # 常驻窗口
```

