---
layout: post
title: awesome 外接显示器
date: Thu Feb 23 21:02:11 CST 2012
comments: true
---

本文档几乎是下面两个blog的内容。

link: [http://www.cnblogs.com/pylemon/](http://www.cnblogs.com/pylemon/archive/2012/2/6.html)

link: [http://www.cnblogs.com/pylemon](http://www.cnblogs.com/pylemon/archive/2012/02/06/2340556.html)

awesome 外接显示器需要用到xrandr命令。
xrandr 有如下使用方法:
    $ xrandr
在我机器上获得如下输出:
      Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
      LVDS-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 303mm x 189mm
         1280x800       60.0 +   50.0
         1024x768       59.9*
         800x600        59.9
         640x480        59.4
         720x400        59.6
         640x400        60.0
         640x350        59.8
      VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
         1920x1080      60.0 +
         1280x1024      75.0     60.0
         1152x864       75.0
         1024x768       75.1     60.0*
         800x600        75.0     60.3
         640x480        75.0     60.0
         720x400        70.1
      DP-1 disconnected (normal left inverted right x axis y axis)
      DP-2 disconnected (normal left inverted right x axis y axis)
      DP-3 disconnected (normal left inverted right x axis y axis)

输出了当前机器所有的接口和支持的分辨率，刷新率。

<!-- more -->

打开外接显示器，与笔记本液晶屏幕显示同样内容（克隆）(--auto 最高分辨率)
    xrandr --output VGA-1 --same-as LVDS-1 --auto

打开外接显示器，与笔记本液晶屏幕显示同样内容（克隆） （分辨率为1280X800）
    xrandr --output VGA-1 --same-as LVDS-1 --mode 1280X800

打开外接显示器，设置为右侧扩展屏幕
    xrandr --output VGA-1 --right-of LVDS-1 --auto

打开外接显示器，同时关闭笔记本液晶屏幕（只用外接显示器工作）
    xrandr --output VGA-1 --auto --output LVDS-1 --off

关闭外接显示器，只用笔记本液晶屏幕
    xrandr --output VGA-1 --off --output LVDS-1 --auto

关闭外接显示器
    xrandr --output VGA-1 --off


VGA-1和LVDS-1 到底在其他机器上是笔记本的显示器还是外接的显示器，需要各自进行本地化测试。

Updateing:
有两个显示器的时候，需要有一下特别的设置，假若笔记本的显示器通过xrandr得出的结果是LVDS-0。
外接显示器通过xrandr得出的结果是VGA-0 , 现在需求是笔记本显示器正常显示，但外接显示器是坚屏的。
可以在.xinitrc 中进行如下配置:

    xrandr --output VGA-0 --mode 1920x10809 --rotate left
    xrandr --output LVDS-0 --mode 1280x800 --rotate normal

awesome 通过ctrl+mode+j 进行屏幕间跳转。
通过mode+o将某个应用发送到下一个屏幕。
