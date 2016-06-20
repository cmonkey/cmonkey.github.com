---
layout: post
title: firefox 假死问题
date: Sat Jun  9 13:01:36 CST 2012
comments: true
---

系统:
    ArchLinux
桌面:
    Awesome

安装firefox 13后，经常遇到firefox假死的问题，折腾了很久，换版本，重新安装，删除.mozilla 目录都试过了。
但是问题依然存在，完全没有头绪。

看一篇帖子，帖子里提到是否安装包有问题，那么就需要验证一下安装包。

新建一个系统用户，然后在该用户下用一下firefox，看看是否firefox安装包的问题。

经确认不是安装包的问题，那么就是用户配置的问题，最后将用户配置文件都删除后，firefox恢复正常工作。

<!-- more -->

Updateing:

可能的问题是flash导致的，将.macromedia 作为/dev/null的软链接。
<code>
    ln -s /dev/null .macromedia
</code>

目前发现可以解决不能点击菜单，以及右键失效的问题。
