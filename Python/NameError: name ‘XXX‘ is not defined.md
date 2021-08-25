> 第一次学习写Python函数，很简单，代码如下
> 
> ```python def writetxts(name,things):
>     # name是要保存txt的路径（含文件名）
>     # things是要写入的内容
>     file1 = open(name,'w')
>     file1.write(things)
>     file1.close()
>     return ""
>     ```
>
> 但就不知道为什么就报了错，报错如下：
> 
> ```python warnings.warn("Image was not the expected size") Traceback
> (most recent call last): File "png}textpng.py", line 48, in <module>
> writetxts(sys.argv[2],text)
> NameError: name 'writetxts' is not defined
>  ```
> 
> 意思大概是一个叫做“writetxts”的函数名称没有声明，但明明声明了啊？下面列出我解决的步骤

# First

既然说没声明，就**看看函数名是不是输错了**，毕竟是用vim编程（还不会设置）
然后认认真真的检查，没问题啊？真奇怪

```python
        # ......
        print(text)
    else:
        writetxts(sys.argv[2],text)
def writetxts(name,things):
    # name是要保存txt的路径（含文件名）
    # things是要写入的内容
    file1 = open(name,'w')
    file1.write(things)
    file1.close()
    return ""
# ......
```

# Second

在我疑惑之时，突然想到了一个对我来说不可思议的答案：**函数位置放错了**（毕竟C#就不太注意位置），然后将代码调节如下：

```python
# ......
import matplotlib.pyplot as plt
import sys
# 用于写入文本文档的函数
def writetxts(name,things):
    # name是要保存txt的路径（含文件名）
    # things是要写入的内容
    file1 = open(name,'w')
    file1.write(things)
    file1.close()
    return ""

show_heigth = 30
show_width = 40
# ......
        text += ascii_char[int(gray[y][x] / 256 * char_len)]
    if len(sys.argv) < 3 :
        print(text)
    else:
        writetxts(sys.argv[2],text)
# ......
```
就可以运行了？看来适应它还要时间

@[TOC](End)

就这样，发一下无聊写的源码（放心，100%有bug）：
修改前：

```python
import matplotlib.pyplot as plt
import sys
show_heigth = 30
show_width = 40
#这两个数字是调出来的

ascii_char = list("$@B%8&WM#*oahkbdpqwmZO0QLCJUYXzcvunxrjft/\|()1{}[]?-_+~<>i!lI;:,\"^`'. ")
#生成一个ascii字符列表
char_len = len(ascii_char)

pic = plt.imread(sys.argv[1])
#使用plt.imread方法来读取图像，对于彩图，返回size = heigth*width*3的图像
#matplotlib 中色彩排列是R G B
#opencv的cv2中色彩排列是B G R

pic_heigth,pic_width,_ = pic.shape
#获取图像的高、宽

gray = 0.2126 * pic[:,:,0] + 0.7152 * pic[:,:,1] + 0.0722 * pic[:,:,2]
#RGB转灰度图的公式 gray = 0.2126 * r + 0.7152 * g + 0.0722 * b

#思路就是根据灰度值，映射到相应的ascii_char
for i in range(show_heigth):
    #根据比例映射到对应的像素
    y = int(i * pic_heigth / show_heigth)
    text = ""
    for j in range(show_width):
        x = int(j * pic_width / show_width)
        text += ascii_char[int(gray[y][x] / 256 * char_len)]
    if len(sys.argv) < 3 :
        print(text)
    else:
        writetxts(sys.argv[2],text)
def writetxts(name,things):
    # name是要保存txt的路径（含文件名）
    # things是要写入的内容
    file1 = open(name,'w')
    file1.write(things)
    file1.close()
    return ""
```
修改后：

```python
import matplotlib.pyplot as plt
import sys
# 用于写入文本文档的函数
def writetxts(name,things):
    # name是要保存txt的路径（含文件名）
    # things是要写入的内容
    file1 = open(name,'w')
    file1.write(things)
    file1.close()
    return ""

show_heigth = 30
show_width = 40
#这两个数字是调出来的

ascii_char = list("$@B%8&WM#*oahkbdpqwmZO0QLCJUYXzcvunxrjft/\|()1{}[]?-_+~<>i!lI;:,\"^`'. ")
#生成一个ascii字符列表
char_len = len(ascii_char)

pic = plt.imread(sys.argv[1])
#使用plt.imread方法来读取图像，对于彩图，返回size = heigth*width*3的图像
#matplotlib 中色彩排列是R G B
#opencv的cv2中色彩排列是B G R

pic_heigth,pic_width,_ = pic.shape
#获取图像的高、宽

gray = 0.2126 * pic[:,:,0] + 0.7152 * pic[:,:,1] + 0.0722 * pic[:,:,2]
#RGB转灰度图的公式 gray = 0.2126 * r + 0.7152 * g + 0.0722 * b

#思路就是根据灰度值，映射到相应的ascii_char
for i in range(show_heigth):
    #根据比例映射到对应的像素
    y = int(i * pic_heigth / show_heigth)
    text = ""
    for j in range(show_width):
        x = int(j * pic_width / show_width)
        text += ascii_char[int(gray[y][x] / 256 * char_len)]
    if len(sys.argv) < 3 :
        print(text)
    else:
        writetxts(sys.argv[2],text)

```

