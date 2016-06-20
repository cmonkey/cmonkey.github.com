---
layout: post
title: rvm 安装和使用
date: Fri Feb 17 13:32:07 CST 2012
comments: true
---

rvm 常用两种方法进行安装

第一种是:
    $bash < <( curl http://rvm.beginrescueend.com/releases/rvm-install-head)

第二种是通过git获得源码，然后进行安装，推荐使用这种方式安装rvm
    git clone git://github.com/wayneeseguin/rvm.git
    cd rvm
    ./install

<!-- more -->

然后在.zshrc 中配置rvm的PATH
    [[-s $"$HOME/.rvm/scripts/rvm"]] && . "$HOME/.rvm/scripts/rvm"
    source .zshrc
就可以使用rvm来管理ruby的版本了。

安装ruby 某个版本
    rvm install 1.9.2
将ruby 1.9.2 设置为系统默认版本
    rvm use 1.9.2 --default
安装 RubyGems
    rvm rubygems latest
查看当前版本
    rvm info
列出版本
    rvm list
