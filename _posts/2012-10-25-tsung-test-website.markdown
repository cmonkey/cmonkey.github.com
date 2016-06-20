---
layout: post
title: "tsung-http-test"
date: 2012-10-25 21:40
comments: true
categories:
---

使用tsung 对网站进行测试,在对网站录制脚本后，我们可能需要对用户名，这种信息进行参数化。
在测试的时候，我们用户名不可以一样，但是密码，或者别的都可以在注册时，设置为一样用来测试。
所以userName, userId这种信息是需要读取一个文件来进行动态的参数化的。

在tsung中，在tsung.xml中设置:

  <options>
      <option name="file_server" id='userlist' value="/home/cmonkey/.tsung/userlist.csv"/>
  </options>


读取外部的文件。

在<session>节点下面设置:

    <setdynvars sourcetype="file" fileid="userlist" delimiter=";" order="iter">
        <var name="user_id"/>
        <var name="user_name" />
    </setdynvars>


在需要对url提交的参数这样设置：
    <request subst="true">
        <http url='/validateCaptcha' version='1.1'
        contents='userName=%%_user_name%%&amp;passWord=e19d5cd5af0378da05f63f891c7467af&amp;validateCode=0000&amp;submit=Login'
        content_type='application/x-www-form-urlencoded' method='POST'>
        </http>
    </request>


需要特别注意的是：
    <reuqest subst="true">
需要对参数化的request节点设置attribute
    subst="true"。

<!-- more -->
