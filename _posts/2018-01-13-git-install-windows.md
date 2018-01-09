---
layout: post
title: "git工具在windows环境的简单安装"
category: IT
tags: git noip IT
---
# git工具在windows环境的简单安装

## 下载git

下载地址：[git](http://p2anace2s.bkt.clouddn.com/Git-1.8.5.2-preview20131230.exe)

## 安装

安装时候选择第二个选项。

## 配置

gitbash启动后

```Java
ssh-keygen -t rsa -C "hshsvg@qq.com"
```

会在用户 .ssh目录下生成 id_rsa.pub文件，拷贝后，粘贴在github新增ssh key处。

```Java
git config --global user.name "hshsvg"
git config --global user.email "hshsvg@qq.com"
ssh -T git@github.com
```
用ssh测试。 通过以后就可以用

```Java
git clone https://github.com/hshsvg/xxxx.git
```

来生成本地库。

如果遇到远程推送的问题，则就修改这个repo下.git/config文件。把用户名和密码添加一下。就可以了。


# End
