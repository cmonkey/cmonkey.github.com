---
layout: post
title: ArchLinux Gvim 不能输入中文
date: Sat Feb 11 18:05:24 CST 2012
comments: true
---

ArchLinux 系统中，使用fcitx输入法，在GVIM中不能输入中文的解决办法。

使用gvim -N -u NONE 启动，查看是否可以使用中文输入。

答案为真的话，基本可以确定是配置文件的错误。

用正常启动，在命令模式中输入
      :verbose set imi?
      :verbose set imd?

然后再次测试是否可以正常输入中文。 <!-- more -->

如果还是不可以，那么检查.vimrc,.gvimrc 文件。

最终解决的是因为在.vimrc中有如下配置
    try
      lang en_US
    catch
    endtry

注释掉这个配置就可以正常的在gvim中输入中文了。
