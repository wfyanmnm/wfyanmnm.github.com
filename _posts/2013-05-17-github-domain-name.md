---
layout: post
title: "github page绑定独立域名"
description: "github page使用godaddy域名"
category: blog
tags: [godaddy, github]
---
看到[webfrogs](http://webfrogs.me/)的博客绑定的独立域名，我也想搞一个。

我先到知乎上搜了下哪个运营商比较好，都推荐name.com和godaddy，我先上name.com，不知道为什么注册不了用户，于是转向godaddy，支持支付宝，很快就完成支付，可以使用了。

在stack overflow上边搜到[一篇文章](http://stackoverflow.com/questions/9082499/custom-domain-for-github-project-pages)，照着这个把域名解析完成。

**操作如下**
1. 在项目根目录下建一个`CNAME`文件，内容为自己的域名`fushikai.me`
2. 在godaddy中添加两条记录，把`@`改成`204.232.175.78`，添加A记录`www`地址`204.232.175.78`

保存并等待修改生效

{% include JB/setup %}