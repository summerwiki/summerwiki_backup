---
title: hexo干货分享：（二）添加字数统计和阅读时长
date: 2018-05-03 00:00:00
category: 灯火阑珊
tags: hexo
word_count: true
toc: true
comments: true
original: true
fancybox: true
---
通过不蒜子插件记录网站的PV、UV

<!-- more -->

1、安装hexo-wordcount插件

	npm i --save hexo-wordcount

2、在hexo\themes\yelee\layout_partial\post下创建word.ejs文件，并且键入一下代码：
	
	<div style="margin-top:10px;">
	    <span class="post-time">
	      <span class="post-meta-item-icon">
	        <i class="fa fa-keyboard-o"></i>
	        <span class="post-meta-item-text">  字数统计: </span>
	        <span class="post-count"><%= wordcount(post.content) %>字</span>
	      </span>
	    </span>
	    <span class="post-time">
	      &nbsp; | &nbsp;
	      <span class="post-meta-item-icon">
	        <i class="fa fa-hourglass-half"></i>
	        <span class="post-meta-item-text">  预计阅读时长: </span>
	        <span class="post-count"><%= min2read(post.content) %>分</span>
	        <span class="post-count"><%= totalcount(site) %></span>
	      </span>
	    </span>
	</div>

3、在hexo\themes\yelee\layout_partial的article.ejs如图位置

![](https://i.imgur.com/UwYHd7z.png)

添加如下代码：

	<% if(theme.word_count && !post.no_word_count){ %>
	    <%- partial('post/word') %>
	<% } %>

4、在主题配置文件中添加如下代码控制是否启用统计字数功能：

	#文章开头显示文字个数
	word_count: true

还可以在文章开头通过no_word_count控制当前页面是否显示字数统计功能

5、效果所示如图

![](https://i.imgur.com/dR9J0ZM.png)
