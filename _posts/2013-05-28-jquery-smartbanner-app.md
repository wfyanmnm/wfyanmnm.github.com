---
layout: post
title: "jquery.smartbanner使用说明-手机访问网站时提示下载app"
description: ""
category: jquery
tags: [jquery, mobile]
---
官网地址：[http://jasny.github.io/jquery.smartbanner/](http://jasny.github.io/jquery.smartbanner/)

应用实例：

    <html>
      <head>
        <title>澳洲网</title>
    	<script src="jquery-1.7.2.min.js"></script>	<!-- 必须先调用jquery -->
        <meta name="apple-itunes-app" content="app-id=590380009" /> <!-- 590380009是apple应用的id -->
        <meta name="google-play-app" content="app-id=com.bjhwzx.mobile.au123news" /> <!-- com.bjhwzx.mobile.au123news是android应用的id -->
        <link rel="stylesheet" href="jquery.smartbanner.css" type="text/css" media="screen" />
        <script src="jquery.smartbanner.js"></script>
        <script type="text/javascript">
    	$(document).ready(function(){
    		//title是应用的名字，author是应用的开发者信息，icon是应用就的logo地址，更多的参数可以参考官网
    		$.smartbanner({title: '澳洲网', author: 'PACIFIC MEDIA', icon: 'logo-mobile.png'});
    	});
        </script>
      </head>
      <body>

      </body>
    </html>

用移动客户端访问网站时会顶部会出现提示条，点击一次后生成cookie，下次访问网站时不再出现，测试时可以删除cookie让它重新出现。

可以用chrome测试不同客户端，方法如下：

* 按F12调出开发者工具
* 点击右下角的齿轮出现设置界面
* 点击`Overrides`
* 勾选`User Agent`，选择需要测试的客户端
* 刷新页面

可以用移动设备或模拟器访问[官网](http://jasny.github.io/jquery.smartbanner/)或者[澳洲网](http://www.au123.com)查看效果
{% include JB/setup %}
