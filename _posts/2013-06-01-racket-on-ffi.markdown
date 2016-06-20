---
layout: post
title: "Racket on ffi"
date: 2013-06-01 23:28
comments: true
categories: 
---
link:[The Racke tForeign-Function Interface](http://www.cs.grinnell.edu/~rebelsky/Glimmer/Summer2012/RacketFFI/tutorial.html)
    // mylib1.c
    #include <stdio.h>
    #include <stdlib.h>


    // Square an integer
    int isquare (int i){
        return i * i;
    }

command 中执行:    

    gcc --shared -o mylib1.so mylib1.c


mylib.rkt  
    #lang racket

    (require ffi/unsafe
    ffi/unsafe/define)

    (define-ffi-definer mylib-define (ffi-lib "mylib1"))
    (mylib-define isquare (_fun _int -> _int))

    (isquare 5)

mylib1.rkt

    #lang racket
    (require ffi/unsafe)

    (define mylib (ffi-lib "mylib1.so"))


    (define isquare
    (get-ffi-obj "isquare"
            mylib 
            (_fun _int -> _int)))

    (isquare 1000)







