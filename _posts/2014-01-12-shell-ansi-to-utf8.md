---
layout: post
title: "一行命令将ANSI批量转换成UTF-8"
description: "自动化可以节省时间"
category: linux
tags: [shell]
---
先把命令写下来，这行命令可以将当前目录包括子目录下的文本文件全部转换成UTF-8编码：

    for f in $(find .); do if [ ! -d "$f" ]; then enconv -L zh_CN -x UTF-8 $f; fi done;

现在一直使用linux系统，之前linux上保存的一些文本文件都是存的ANSI，在linux打开是乱码，我就想法把它们转成可以正常查看的。在网上搜一些资料，然后按自己的需求组合成了这一行命令。

主要参考了一个[百度知道的回答](http://zhidao.baidu.com/question/271695820.html)，上边提到了可以通过配置.vimrc来查看文件

    set encoding=utf-8 fileencodings=ucs-bom,utf-8,cp936

但是文件的编码并没有改变，这个回答也给了转换方式

    enconv -L zh_CN -x UTF-8 filename

使用linux的一个优势就可以编写各种脚本实现自动化，于是我就加了个for循环来给它批量处理

`find .`是列出当前目录包括子目录的文件

for循环的语法：

    for name [ [ in [ word ... ] ] ; ] do list ; done

if语句：

    if [ conditional expression ]
    then
	statement1
	statement2
    fi

`[ ! -d "$f" ];` 过滤掉子目录
{% include JB/setup %}
