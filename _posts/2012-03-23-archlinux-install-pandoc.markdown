---
layout: post
title:  archlinux install pandoc
date:  Fri Mar 23 10:24:22 CST 2012
comments: true
---

如果需要把文件从一种标记语言格式转换到另一种格式，[pandoc](http://johnmacfarlane.net/pandoc/)会是一把犀利的瑞士军刀。
它可以将[markdown](http://daringfireball.net/projects/markdown/),[reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html)等标记语言进行相互转换。

可以查看[install](http://johnmacfarlane.net/pandoc/installing.html),获得各平台的安装方式。

在archlinux 中安装pandoc 可以通过如下方式。
    yaourt cabal
    cabal update
    cabal install pandoc

<!-- more -->

没有错误基本就安装成功了。
一般安装在
    ~/cabal/  目录下
所以需要在.profile 文件中加入cabal 的PATH。
