---
layout: post
title: jdk remote debug
date: Thu Mar  8 16:46:14 CST 2012
comments: true
---

##JPDA

工作在DEBUG模式下，加入参数:
    -Xdebug -Xrunjdwp,transport=dt_socket,server=y,address=5432,suspend=n

-Xdebug 是通知JVM工作在debug模式下。
-Xrunjdwp 是通知jvm 使用(java debug wire protocol) 来运行测试环境。

<!-- more -->

-Xrunjdwp 有如下选项：
    transport 指定调试数据的传递方式。

    transport=dt_socket 是 socket模式。
    transport=dt_shmem 是共享内存方式，只适用于windows。

    address 是调试客户端连接到服务器的地址。

    server 是指定是否支持在server模式的vm中。

    suspend 是否在调试客户端建立起来后，在只想jvm。

    -XDebug               启用调试。
    -Xnoagent             禁用默认sun.tools.debug调试器。
    -Djava.compiler=NONE  禁止 JIT 编译器的加载。
    -Xrunjdwp             加载JDWP的JPDA参考执行实例。
    transport             用于在调试程序和 VM 使用的进程之间通讯。
    dt_socket             套接字传输。
    dt_shmem              共享内存传输，仅限于 Windows。
    server=y/n            VM 是否需要作为调试服务器执行。
    address=3999          调试服务器的端口号，客户端用来连接服务器的端口号。
    suspend=y/n           是否在调试客户端建立连接之后启动 VM 。

##JDB
    jdb -connect com.sun.jdi.SocketAttach:port=5432,hostname=192.168.11.213
