---
layout: post
title: 增加man路径
comments: true
---

在*nix系统中，可能有一些用户自定义编译安装的软件，由于MANPATH的路径没有指定,
执行man XXX 会无效。

这时候就需要定义MANPATH这个环境变量，如下所示:
假如自定义安装memcached这个分布式缓存服务器在
    /usr/local/memcached
目录，没有指定MANPATH的时候，执行命令
    man memcached
是找不到memcached 的man信息的，
这种情况可以在.profile 文件中指定:
    export MANPATH=/usr/local/memcached/share/man:$MANPATH
也可以手动临时指定:

    man -M /usr/local/memcached/share/man memcached

<!-- more -->
