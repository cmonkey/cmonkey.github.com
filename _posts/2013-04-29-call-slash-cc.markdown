---
layout: post
title: "call/cc"
date: 2013-04-29 16:24
comments: true
categories: 
---

在晚上搜索了半天的call/cc 的知识。看了半天，并且尝试了半天。
才得到一下的结果。

<code>
    (define (t x y)
        (sqr (call/cc (lambda (k)
                        (k (+ x y))))))

    (t 5 10)

    225
</code>

在这里的k 相当于这个表达式，也就是sqr 函数，所以k = sqr ,然后(sqr (+ x y))

但是这并不是想要的，想实现的效果

<code>
    (lambda () 
        (+ x y) sqr)
</code>

传入x,y,将x,y相加，然后将结果给sqr.
但是不知道如何实现。

