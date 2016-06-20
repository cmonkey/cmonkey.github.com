---
layout: post
title: update goagent 1.8.0
date: Sat Apr  7 13:09:14 CST 2012
comments: true
---

goagnet 更新到了1.8.0，需要在gae上对其进行更新。
但是按照作者的方法，在$GOAGNET_HOME/server下执行:
    python2 uploader.zip
不会成功，总是报:
    urllib2.URLError: <urlopen error [Errno 32] Broken pipe>

<!-- more -->

通过google，可以通过[appengine](https://code.google.com/appengine/downloads.html)下载Google appengine for python的sdk。
然后解压到目录，比如$HOME/develop/appengine,修改$GOAGENT_HOME/server/python/app.yaml中application
键的值。
然后执行:
    python2 ~/develop/appengine/appcfg.py update goagent/server/python/

Updateing:在firefox上先删除goagent的证书，然后重新倒入证书，最后重启浏览器，现在就可以正常的浏览twitter等网站了。
