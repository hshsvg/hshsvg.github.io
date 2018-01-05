---
layout: post
title: "Build a github blog with jekyll"
category: 实用技巧
tags: [github, jekyll, ruby]
---

# 用github和jekyll构建blog系统

## 构建ruby,jekyll本地环境

> 用来构造一套本地jekyll系统，github其实就是使用了jekyll系统，从而把markdown页面，转化为html页面。新建的系统为离线博客系统，只要最后把生成的md文件推送上去，就完成了发布，所以构造一个和github一样的jekyll系统非常重要。

有如下一些步骤：
* 安装ruby，尽量使用高版本的ruby，我们使用的是2.3版本，用源码安装。
* 安装rubygems，用的是2.6版本。运行setup.rb就可以了。
* 用gem install安装jekyll和rake，用rake的目的是为了随后自动生成post的md文件

指令主要有：
```
	curl ruby-****.tar.gz 
	tar -zxvf ruby-****.tar.gz
	cd ruby-****
	make
	sudo make install

	cd rubygems
	ruby setup.rb

	gem install rake
	gem install jekyll
```


## 构造vim的 markdown插件

> 使用的vim插件主要有语法高亮和预览等插件

* 首先安装了vundle管理插件，修改.vimrc文件，再安装语法高亮插件
	```
	Plugin 'godlygeek/tabular'
	Plugin 'plasticboy/vim-markdown'
	```
	紧接运行：（plasticboy/vim-markdown无法如此安装，只能先下载拷贝到bundle目录下)
	```
	:PluginInstall
	```
* 安装即时查看插件，编辑markdown文件时自动打开chrome浏览。需要nodejs支撑。
	```
	sudo add-apt-repository ppa:chris-lea/node.js
	sudo apt-get update
	sudo apt-get install nodejs
	sudo npm -g install instant-markdown-d
	```
	在vim配置文件中添加,然后再在vim处运行
	```
	Plugin 'suan/vim-instant-markdown'
	:PluginInstall
	```
完成以后，只要打开一个markdown文件，就会弹出一个chrome窗口提供预览。

## github支持
* 在
* github生成一个username.github.io的代码仓库。
* 在本地生成加密相关文件
	```
	ssh-keygen -t rsa -C "youremail"
	```
	在.ssh目录下会生成 id_rsa，和id_rsa.pub
* 在github个人设置处，新建一个ssh key，把id_rsa.pub的内容拷贝进去。
* 在本地设置git的账户信息
	```
	git config --global user.name "username"
	git config --global user.email "youremail"
	```
## 其他的工具
注册七牛，获取图床，再利用极简图床的chrome插件，来上传图片，并生成图片的url

## 使用流程
	1. 用rake指令生成一个带框架的.md文件。
	2. 用vim编辑该markdown文件，同时用chrome浏览。
	3. 用git命令推送到github上去。

