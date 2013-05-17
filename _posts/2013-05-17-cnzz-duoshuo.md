---
layout: post
title: "在jekyll中使用cnzz和多说"
description: "修改模板解决"
category: blog
tags: [cnzz 多说]
---
CNZZ和多说都是使用javascript调用，所以只要想办法把代码加到页面的合适位置就可以。
## 加入cnzz
例如，想要把cnzz加到页面的底部，可以使用grep或在windows下使用notepad++的文件搜索底部文件的代码，我用的是默认的**Twitter Bootstrap**模板，底部代码是这样的

    <p>&copy; 2013 
          with help from <a href="http://jekyllbootstrap.com" target="_blank" title="The Definitive Jekyll Blogging Framework">Jekyll Bootstrap</a>
          and <a href="http://twitter.github.com/bootstrap/" target="_blank">Twitter Bootstrap</a>&nbsp;&nbsp;<script src="http://s95.cnzz.com/stat.php?id=5335860&web_id=5335860&show=pic" language="JavaScript"></script>
        </p>
我就搜索`with help from`，发现代码存在`\_includes\themes\twitter\default.html`中，就把**cnzz**统计代码加在后边
## 使用多说
模板默认的评论插件是`DISQUS`，从网页源代码看，disqus代码的前边是

    <div class="pagination">
      <ul>
      
        <li class="prev"><a href="/log/2013/05/16/new-post" title="2000年4月的几篇日记">&larr; Previous</a></li>
      
        <li><a href="/archive.html">Archive</a></li>
      
        <li class="next disabled"><a>Next &rarr;</a>
      
      </ul>
    </div>
    <hr>
用同样的方法搜得代码存在`\_includes\themes\twitter\post.html`，把`% include JB/comments %`替换成**多说**代码

{% include JB/setup %}