当我玩一下 PyQt 时，问题出现了
问题代码：
```python
#! /usr/bin/env python
# -*- coding: utf-8 -*-
 
import sys
from PyQt5 import QtWidgets, QtCore
 
if __name__ == '__main__':
    app = QtWidgets.QApplication(sys.argv)
    widget = QtWidgets.QWidget()
    widget.resize(320, 240)
    widget.setWindowTitle("Hello PyQt5")
    widget.show()
    sys.exit(app.exec_())
```
报错
```bash
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, webgl, xcb.

已放弃
```
![错误](https://img-blog.csdnimg.cn/ec3c2dd2862c465aa564bfee82dbb0d1.png)

先看详细的报错信息
```bash
export QT_DEBUG_PLUGINS=1
```
报错：
```bash
Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqeglfs.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "eglfs"
        ]
    },
    "archreq": 0,
    "className": "QEglFSIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqlinuxfb.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "linuxfb"
        ]
    },
    "archreq": 0,
    "className": "QLinuxFbIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqminimal.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "minimal"
        ]
    },
    "archreq": 0,
    "className": "QMinimalIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqminimalegl.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "minimalegl"
        ]
    },
    "archreq": 0,
    "className": "QMinimalEglIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqoffscreen.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "offscreen"
        ]
    },
    "archreq": 0,
    "className": "QOffscreenIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqvnc.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "vnc"
        ]
    },
    "archreq": 0,
    "className": "QVncIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqwayland-egl.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "wayland-egl"
        ]
    },
    "archreq": 0,
    "className": "QWaylandEglPlatformIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqwayland-generic.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "wayland"
        ]
    },
    "archreq": 0,
    "className": "QWaylandIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqwayland-xcomposite-egl.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "wayland-xcomposite-egl"
        ]
    },
    "archreq": 0,
    "className": "QWaylandXCompositeEglPlatformIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqwayland-xcomposite-glx.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "wayland-xcomposite-glx"
        ]
    },
    "archreq": 0,
    "className": "QWaylandXCompositeGlxPlatformIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqwebgl.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "webgl"
        ]
    },
    "archreq": 0,
    "className": "QWebGLIntegrationPlugin",
    "debug": false,
    "version": 331520
}


Found metadata in lib /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqxcb.so, metadata=
{
    "IID": "org.qt-project.Qt.QPA.QPlatformIntegrationFactoryInterface.5.3",
    "MetaData": {
        "Keys": [
            "xcb"
        ]
    },
    "archreq": 0,
    "className": "QXcbIntegrationPlugin",
    "debug": false,
    "version": 331520
}


QLibraryPrivate::loadPlugin failed on "/home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqxcb.so" : "Cannot load library /home/gfdgd_xi/.local/lib/python3.7/site-packages/PyQt5/Qt5/plugins/platforms/libqxcb.so: (libxcb-util.so.1: 无法打开共享对象文件: 没有那个文件或目录)"
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, webgl, xcb.

已放弃
```
![详细报错](https://img-blog.csdnimg.cn/7d3c19d84d3349e38786017818ae1134.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)缺库

在[https://forum.qt.io/topic/93247/qt-qpa-plugin-could-not-load-the-qt-platform-plugin-xcb-in-even-though-it-was-found/100](https://forum.qt.io/topic/93247/qt-qpa-plugin-could-not-load-the-qt-platform-plugin-xcb-in-even-though-it-was-found/100)看到了解决方案，输入以下内容即可：
```bash
sudo apt install -qq libglu1-mesa-dev libx11-xcb-dev '^libxcb*'
```
![方案](https://img-blog.csdnimg.cn/9785f4e0fc7348f087db7cab76006b2d.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)附图：
![程序截图](https://img-blog.csdnimg.cn/868fe566a7ad4f1a9b7fb389aefbbef6.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjQwMzQ4Mw==,size_16,color_FFFFFF,t_70)附 PyQt5 安装方法：
```bash
python3 -m pip install PyQt5
```


