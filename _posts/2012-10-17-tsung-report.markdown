---
layout: post
title: "tsung-report"
date: 2012-10-17 18:00
comments: true
categories:
---

Tsung 报表分析
首先可以看[user_manual](http://tsung.erlang-projects.org/user_manual.html)_

一些常见的名词解析：
request：       每个请求的反应时间。
page：          每一系列请求的反应时间（a page 是一组不包含think-time 的一组请求）
connect：       连接建立的时间
reconnect：     重新连接的次数
size_rcv:       反应的大小（单位byte）
size_sent:      请求的大小（单位byte）
session:        用户会话时间
users:          同步用户数

<!-- more -->
