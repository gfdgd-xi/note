今天无聊写网页，遇到图片居中的问题
以下代码不能居中，

```html
<img src="Picture/桌面环境.png" align="center" />
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200915190749939.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)

但可以靠右

```html
<img src="Picture/桌面环境.png" align="right" />
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200915190840641.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)

但将代码改为如下，就可以了

```html
<p align="center"><img src="Picture/桌面环境.png"/></p>
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200915191009117.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70#pic_center)
不知道这样可以的原因是什么？

