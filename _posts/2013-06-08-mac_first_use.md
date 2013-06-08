---
layout: post
title: "Mac使用心得"
description: ""
category: mac
tags: [mac, goagent, qq, php]
---
用了一周，没有想象中那么难用，原来系统上能做的现在基本已经实现。遇到的一些问题和解决方法写一下。
## 不知道开机密码
机器之前别人用过，但他把密码忘了，于是我从网上搜了解决方法，挺简单。

* 开机时按option，选择进入Recovery HD
* 实用工具->终端
* 在终端中输入resetpassword
* 点击选择Macintosh HD
* 选择用户帐户
* 输入新密码
* 确认密码
* 存储

## 更新python
最新版的goagent需要python3，从网上搜了安装方法
[更新mac自带的python.html](http://www.chenwg.com/python/%E6%9B%B4%E6%96%B0mac%E8%87%AA%E5%B8%A6%E7%9A%84python.html)

## goagent开机启动
[Mac OS X 如何开机启动](https://code.google.com/p/goagent/issues/detail?id=1166)

## 导入windows的QQ聊天记录
把QQ号文件夹复制到`~/Library/Containers/com.tencent.qq/Data/Library/Application\ Support/QQ/`文件夹下边
## PHP开发环境
这篇文章写得相当好 [Mac OSX Lion中Web开发环境配置](http://www.xiaoche.me/blog/2012/02/02/mac-php-mysql/)

{% include JB/setup %}
