---
layout: post
title: "Garbage Collection 初探"
date: 2013-01-25 10:44
comments: true
categories: 
---

link: [Garbage Collection](http://www.findfunaax.com/notes/file/157)

1. 原理

垃圾回收(Garbage Collection, GC)技术的源头可以追溯到1960年Lisp语言。 如今越来越多的高级语言采用垃圾回收技术，尤其是动态语言(Python, Lua)。 当然，最知名的还是Java这个静态类型语言把GC技术带给了广大的程序员， 解放了Memory Leak这个问题。更多GC技术的历史可以查阅参考文献1.

GC是关于内存的垃圾回收，在讨论回收之前，首先要知道内存是怎么分配的。 大多数主流语言或Virtual Machine支持三种最基本的那次分配方式：

    静态分配(Static Allocation)：静态变量和全局变量的分配方式。自动申请，无需释放。
    自动分配(Automatic Allocation)：栈中局部变量的分配方式。自动申请，自动释放。
    动态分配(Dynamic Allocation)：堆中内存的分配方式。手动申请，手动释放。

这里面最容易出问题的地方就是动态分配的内存。如果只有“手动申请(malloc/new)，忘记释放(free/delete)”，就会造成Memory Leak。 GC所作的事就是使得动态分配的内存“手动申请，自动释放”，解放程序员的生产力。

根据IBM T.J Watson Research Center的一篇总结性论文A Unified Theorg of Garbage Collection， 垃圾回收算法可以分为两大类：
    Reference Counting 引用计数型
    Tracing 追踪型

<!-- more -->

1.1 Reference Counting 引用计数型

引用技术算法对于每个对象增加一个引用技术值，记录对象某时被引用的计数。 当有新的变量指向这个对象时，引用计数加1。 当有变量不再引用这个对象时，引用计数减1。 当对象的引用的次数为0时，表示对象可以被垃圾回收。

引用计数型的算法回收速度较快，适合多线程实现。 但是算法对程序中每一次内存分配和指针操作提出了额外的要求（增加或减少对象的引用计数）。 更重要的是，引用计数算法无法正确解决循环引用(circular reference)问题(配合weak reference counting可以基本解决)。

C++的智能指针就是引用技术算法的一个例子。

1.2 Tracing 追踪型  

1.2.1 Mark-Sweep 标记－清除

Mark-Sweep算法是J. Mc Carthy等人在1960年提出并成功地应用于Lisp语言的GC算法，也是第一个实用和完善的算法。 算法分为Mark和Sweep两个阶段：

    Mark阶段：标记每个对象是否被引用
    Sweep阶段：清除没有被引用的变量

Mark-Sweep算法效率不高。

1.2.2 Copy 拷贝

1963年M. L. Minsky提出了Mark-Copy算法，改进了Mark-Sweep的效率问题。 Copy算法将堆空间一分为二，并使用简单的复制操作来完成收集工作。 在回收阶段，把正在使用的对象从堆空间的一般拷贝到另一半，未被使用对象不动。 这样同时解决了碎片问题。代价是可用内存少了一半。

1.2.3 Mark-Compact 标记-整理

Mark-Compact算法是Mark-Sweep和Copy算法的整合。 这个算法不需把堆空间分割成两块，整个过程也是两个阶段：

    Mark阶段：标记每个对象是否被引用
    Compact阶段：将被引用的对象拷贝至堆空间的一端

理论上Mark-Compact兼有Mark-Sweep算法的内存占用上的优点和Copy算法的执行效率。 因此在许多现代的垃圾收集器中，人们都使用了标记－整理算法或其改进版本。

参考: [http://blog.csdn.net/javafuns/article/details/1771535](http://blog.csdn.net/javafuns/article/details/1771535)


updateing: 
在使用java的时候，一般会知道关于java中是如何进行垃圾回收的，分为几个不同的代，然后在学racket 的时候，也会知道是有垃圾回收的，但是关于垃圾回收到底是怎么样的历史，是如何一步步发展，然后是怎么样的思想来实现垃圾回收的，就不得而知，读了这篇文章和参考链接后，对垃圾回收有一个思想上的认识，至于在各种语言中怎么具体实现的，是另一回事了。
