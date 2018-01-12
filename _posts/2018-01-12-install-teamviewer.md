---
layout: post
title: "安装teamviewer软件,实现远程桌面共享"
sbutitle: 
date: 2018-01-12
category: IT
cover: 
tags: computer IT
---

# Install teamviewer to get access to remote desktop

## download 下载

```Java
wget http://download.teamviewer.com/download/version_10x/teamviewer_i386.deb --no-check-certificate
```

## install 安装

```Java
sudo dpkg -i teamviewer_10.0.46203_i386.deb
```

如果显示dpkg没有安装,就用sudo apt-get install dpkg 安装即可
这里需要输入密码
输入密码后即可完成安装

## launch 启动

从系统菜单开始启动![如图](http://p22lbw5jx.bkt.clouddn.com/18-1-12/22096153.jpg)

得到如下的界面,这样其他人就可以通过id和密码来进行连接了.
![如图](http://p22lbw5jx.bkt.clouddn.com/18-1-12/97123461.jpg)
