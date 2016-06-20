---
layout: post
title: "slideshow and ffi"
date: 2013-06-01 22:39
comments: true
categories: 
---

今天值得高兴的有两件事，是很有意思的一天。

学习Racket以来，一直很好奇Racket 中怎么实现调用动态库，Java中可以通过JNI技术，来实现对动态库的调用。
但是一直是不知道在Racket中如何调用。

这一切的疑问都在今天解决了，在逛github 的时候，看到了Racket中通过ffi 中的函数库来调用动态库。
一般有如下方法:     
    #lang racket
    (requive ffi/unsafe)
    (define libgit2 (ffi-lib "libgit2"))   

大体的代码结构就是这样，详细文档请见[ffi](http://docs.racket-lang.org/foreign/)

第二件高兴的事情是，在看[Macros Matter: Infrastructure for building new programming languages](http://www.mefeedia.com/video/26348171) 这个视频的时候。
看到简单使用slideshow 这个函数库中的slide 函数实现ppt的编写。

这东西也太酷了，所以简单的看了一下该函数库的文档，然后还用这写了一个简单的个人简介的ppt。
[slideshow](http://docs.racket-lang.org/slideshow/)
