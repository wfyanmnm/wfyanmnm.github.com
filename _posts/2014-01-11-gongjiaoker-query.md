---
layout: post
title: "使用公交客网站监测公交车的到达情况"
description: "生活中处处都要自动化"
category: jquery
tags: [公交]
---
开始的时候用公交客的android版，不知道啥时候开始，通过移动网络获取不了数据，于是就用网页版的服务。

网址是[http://gongjiaoker.com/](http://gongjiaoker.com/)

因为公司楼下灯市西口站的103路我下班点的车很少，而且我只能坐这趟，所以出门之前我都会查一下，已经发车我再下楼，因为车少，所以得一直查询，很浪费时间，我就想着可不可以把查询这个步骤自动化。

在网页上找到查询的js代码

    getDistance("103.down","灯市西口")

用Chrome的All JS Viewer插件查看function getDistance()，代码如下

    function getDistance(busline, value) {
    $.ajax({
    url: "/queryTime?busline=" + encodeURI(busline) + "&station=" +         encodeURI(value),
    cache: false,
    dataType: "json",
    success: function(data) {
    mesResult = "<span class='red'> " + data.station + "</span><br>";
    mesResult += "<div style=\"clear:none\">";
    if (data.status == 'notReady') {
    mesResult += data.msg;
    }
    $('title').html(data.times[0].howLong+'分钟 '+data.times[0].howFar+'米');
    $.each(data.times, function(index, value) {
    noBus = index + 1;
    mesResult += '<div style="text-align:left"><img src="images/butt-right_gray.gif">&nbsp;第 <span class="red">' + noBus + '</span> 辆 还有 <span class="red">' + value.howLong + '</span> 分钟/ <span class="red">' + value.howFar + '</span> 米 已经过 <span class="bold">' + value.lastStation_str + '</span></div>';
    });
    mesResult += "</div>";
    $("#mes_result").html(mesResult);
    }
    });
    }

其中的

    $('title').html(data.times[0].howLong+'分钟 '+data.times[0].howFar+'米');

是我自己加的，就是把网页的标题改成还有几分钟，几米到

最后再加上自动执行的代码

    $('title').html('开始监测!');
    setInterval(function(){getDistance("103.down","灯市西口")}, 60000);
这样每隔一分钟就会更新一次查询结果，而且在标题栏上显示，这样可以同时做其它事情也不耽误坐车。

没什么技术含量，但是能节省一些时间，回头试试做个chrome插件，练手用。
{% include JB/setup %}
