---
layout: post
title: ImageMagick 使用
date: Sunday, December 11, 2011  2:29:09 PM CST
comments: true
---

link: <http://jianlee.ylinux.org/Computer/Software/imagemagick.html>

### 1. convert

   对图像进行转换，它主要用来对图像进行格式的转化，同时还可以做缩放、剪切、模糊、反转等操作。

#### 格式转换
   有时候在论坛发帖想带图，Linux里面抓的图通常是 png 格式的，很大。使用下面一条目录就可以把 png 格式转换为 jpg 格式了。
    convert foo.png foo.jpg
   还可以使用 mogrify :
    mogrify -format png *.jpg    # 将当前目录下所有jpg文件转换为png格式。
   不过 convert 还可以把多种照片转换成 pdf 文件：
    convert *.png foo.pdf  # 厉害吧！

#### 缩放
    convert -resize 100x100 foo.jpg thumbnail.jpg
    convert -resize 50%x50% foo.jpg thumbnail.jpg
    mogrify -sample 80x60 *.jpg   # 注意，这条命令会覆盖源文件

#### 加边框
   下面两条语句都可以加边框
    convert -mattecolor "#333333" -frame 60x60 源文件.png 转换后文件.png
    convert -bordercolor "#666666" -border 60x60 源文件.png 转换后.png

#### 图片上加文字
    convert -fill green -pointsize 40 \
    -draw 'text 10,50 "jianlee.cn"' clutter-春江花月夜.png  tmp.png
    使用 -font 可以指定字体。

#### 模糊
   高斯模糊
    convert -blur 80  clutter-春江花月夜.png  tmp.png
   -blur参数还可以这样-blur 80x5。后面的那个5表示的是Sigma的值，它的值对模糊的效果起关键的作用。<!-- more -->

#### 翻转
   上下翻转
    convert -flip clutter-春江花月夜.png  tmp.png
   左右翻转
    convert -flop clutter-春江花月夜.png  tmp.png
   反色
    convert -negate clutter-春江花月夜.png  tmp.png
   单色（黑白照片）
    convert -monochrome clutter-春江花月夜.png  tmp.png
   加噪声
    convert -noise 3 clutter-春江花月夜.png  tmp.png
   油画效果
    /media/d_fat32/picture/h红楼/87版我的截图/右手.JPG
   旋转
    convert -rotate 30 hlm.JPG  tmp.jpg
   上面的30，表示向右旋转30度，如果要向左旋转，度数就是负数。
   炭笔效果(比素描更模糊,铅笔画)
    convert -charcoal 2 hlm.JPGtp.jpg
   散射（毛玻璃）效果
    convert -spread 10 hlm.JPG  tmp.jpg
   漩涡
   以图片中心为转轴，扭转图片形成漩涡效果
    convert -swirl 60 hlm.JPG  tmp.jpg
   同样，正负数表示左漩涡还是右漩涡
   突起效果
    convert -raise 10x10 hlm.JPG  tmp.jpg
   执行后，你会看到，照片的四周会一个10x10的边，如果你要一个凹下去的边，把-raise改为+raise就可以了。凸起和凹下好像没有区别。

   其他
   查看手册页可以得到更多的功能

### import (截图)

没有这么好的截图工具了！常用功能有：
截取屏幕任一矩形区域

    import tmp.png

执行上面命令后，鼠标变成 “十“ 字，选择区域截图就行了！
截取程序窗口

    import -pause 3 -frame tmp.png

回车后，用鼠标在你想截的窗口上点一下即可。参数-frame的作用是告诉 import，截图的时候把目标窗口的外框架带上，参数-pause的作用很重要，你可以试着把它去掉，对比一下，你会发现，目标窗口的标题栏是灰色的，pause就是让import稍微延迟一下，等你的目标窗口获得焦点了，才开始截图，这样的图才比较自然。
让截图倾斜

    import -rotate 30 -pause 3 -frame tmp.png

多了一个截图后倾斜功能。
全屏截图

    import -pause 3 -window root screen.png

### display

显示图片，处理图片
显示
    display 名字.png  # 或者 display *.png

幻灯片显示
    display -delay 5 *

快捷键
   1. space(空格): 显示下一张图片
   2. backspace(回删键):显示上一张图片
   3. h: 水平翻转
   4. v: 垂直翻转
   5. /:顺时针旋转90度
   6. \:逆时针旋转90度
   7. \>: 放大
   8. <: 缩小
   9. F7:模糊图片
   10. Alt+s:把图片中间的像素旋转
   11. Ctrl+s:图象另存
   12. Ctrl+d:删除图片
   13. q: 退出

其他
   ImageMagick还提供有丰富的编程接口，比如，你可以用php来调用它，用 ImageMagick来生成验证码图片，效果非常棒。
   ImageMagick还有一个小工具identify，它可以用来显示一个图片文件的详悉信息，比如格式、分辨率、大小、色深等等。
参考
   <http://www.bokee.net/bloggermodule/blog_viewblog.do?id=68625>
   <http://www.imagemagick.org>
