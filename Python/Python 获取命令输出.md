首先调用对应的库

```python
import os
```
**按行读取内容**

```python
cmd = "" # 要获取输出的命令
result = os.popen(cmd)
    res = result.read()
    for line in res.splitlines():
        # line 变量就是行输出的内容
        pass
```
**一次性输出全部内容**
和上面的差不多，区别在于将获取到每一行的输出合在一起

```python
cmd = "" # 要获取输出的命令
thing = "" # 获取到的命令所有输出内容
result = os.popen(cmd)
    res = result.read()
    for line in res.splitlines():
        # line 变量就是行输出的内容
        things += line + "\n"
```
我自己还写了一个小函数可以调用

```python
def get_cmd(cmd):
	# cmd 是要获取输出的命令
	thing = "" # 获取到的命令所有输出内容
	result = os.popen(cmd)
    res = result.read()
    for line in res.splitlines():
        # line 变量就是行输出的内容
        things += line + "\n"
    return thing
```
调用方法，如下：

```python
get_cmd("echo \"a\"") # 输出命令的全部内容
                      # 第一个参数：要获取输出的命令
                      # 返回值：命令所有输出内容
```
（再更）
其实还有更简单的，可以获取报错，如图：
![报错](https://img-blog.csdnimg.cn/20210509074244243.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)


```python
import subprocess
# ...........
print(subprocess.getoutput("echo 'a'"))
```
套函数：

```python
# 需引入 subprocess
def GetCommand(cmd):
    # cmd 是要获取输出的命令
    return subprocess.getoutput(cmd)
```
调用方法，如下：

```python
GetCommand("echo 'a'") # 输出命令的全部内容
                      # 第一个参数：要获取输出的命令
                      # 返回值：命令所有输出内容
```
