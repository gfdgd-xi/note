（懒了，直接丢读写的函数了）

## 调用的库
要调用的库：os

```python
import os
```

## 函数

**创建文本文档**
函数：
```python
无
```
调用方法：
```python
os.mknod() # 创建文本文档
           # 第一个参数：创建路径
           # 返回值：无返回值
```

**读取文本文档**
函数：
```python
# 读取文本文档
def read_txt(path):
    f = open(path,"r") # 设置文件对象
    str = f.read() # 获取内容
    f.close() # 关闭文本对象
    return str # 返回结果
```
调用方法：

```python
read_txt() # 读取文本文档
           # 第一个参数：要读取的文本文档的路径
           # 返回值：读取到的内容
           # 提示：读取时需保证文本文档存在
```

**写入文本文档**
函数：
```python
# 写入文本文档
def write_txt(path, things):
    file = open(path, 'w', encoding='UTF-8') # 设置文件对象
    file.write(things) # 写入文本
    file.close() # 关闭文本对象
```
调用方法：

```python
write_txt() # 写入文本文档
            # 第一个参数：要写入的文本文档路径
            # 第二个参数：要写入文本文档的内容
            # 提示：写入时需保证文本文档存在
```

