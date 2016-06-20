---
layout: post
title: "kernel_SysRq"
date: 2013-02-06 17:21
comments: true
categories: 
---

最近awesome 更新到了3.5版本，由于未知的原因，有时候可能造成awesome+xorg都不响应了。
以前都是直接按住电源键关机，然后重启，问题倒是没有，但是总归很危险的操作。

linux中针对这种情况，可以通过reisub来进行系统重启。
在archlinux中默认关闭了通过reisub 来重启系统的功能。
需要：  
    echo "1" > /proc/sys/kernel/sysrq
或者： 
    edit /etc/sysctl.conf and set kernel.sysrq = 1

来开启reisub 功能，使系统在不能响应时，可以通过按Alt+SysRq + reisub 重启系统。

link: [Keyboard_Shortcuts](https://wiki.archlinux.org/index.php/Keyboard_Shortcuts) 

<!-- more -->
