---
layout: post
title: package-query require pacman<3.6 错误
date: Wednesday, January 18, 2012 08:30:01 AM CST
comments: true
---

今天升级ArchLinux 的时候碰到下面的问题:

    error: failed to prepare transaction (could not satisfy dependencies)
    package-query: requires pacman<3.6

Google 多次后，得到如下办法 <!-- more -->

    pacman -R yaourt package-query
    pacman -Syu

修改
    /etc/pacman.conf.pacnew

去掉
    SigLevel = Optional TruslAll
前的#。

在
    SigLevel = Never
前添加#

修改
    /etc/pacman.d/gunpg/gpg.conf
中的
    keyserver hkp://keys.gnupg.net
为
    keyserver hkp://pgp.mit.edu
或者
    keyserver hkp://pgp.mit.edu:11371

复制pacman.conf 文件
    cp /etc/pacman.conf.pacnew /etc/pacman.conf

执行
    pacman-key --init

重新安装yaourt
    pacman -S yaourt
