---
title: hexo干货分享：（一）集成畅言评论和打赏
date: 2018-05-01 00:00:00
category: 灯火阑珊
tags: hexo
word_count: true
toc: true
comments: true
original: true
fancybox: true
---
本篇文章记录一下自己在使用hexo搭建本博客的时候，使用的一些插件，以及踩过的一些坑。

<!-- more -->
Yelee是由MOxFIVE更改的主题，功能和外观都很不错。可以参考[Yelee主题使用说明](http://moxfive.xyz/yelee/)进行配置。

## 集成畅言评论系统

注册[畅言](http://changyan.kuaizhan.com/)账号,使用畅言之前域名先做先备案，通用配置如下：

![](https://i.imgur.com/lrL2DWp.png)

按照图片找到以下代码：

![](https://i.imgur.com/vQZyrzL.png)

以上是通用代码，根据自己使用的主题做适当的修改，Yelee修改如下：

	<section class="changyan" id="comments">
	<div id="SOHUCS"></div>
	<script charset="utf-8" type="text/javascript" src="https://changyan.sohu.com/upload/changyan.js" ></script>
	<script type="text/javascript">
	 var loadComment = function(){
	window.changyan.api.config({
	appid: '<%= theme.changyan.appid%>',
	conf: '<%= theme.changyan.appkey%>'
	});
	}
	</script>
	<%- partial('click2show') %>
	</section>


1、在hexo\themes\yelee\layout_partial\comments文件夹下新建changyan.ejs文件，并键入以上代码。

2、修改hexo\themes\yelee\layout_partial下的article.ejs文件如下：

![](https://i.imgur.com/9pRuFIM.png)

添加如下几行代码：

	<% } else if (theme.changyan.on) { %>
	    <%- partial('comments/changyan', {
	      }) %>
	<% } %> 

3、在hexo\themes\yelee下的_config.yml中添加如下代码，在appid和appkey填写你的畅言：

	# changyan
	changyan:
	  on: true
	  appid: ****
	  appkey: ****

4、获取appid和appkey：

![](https://i.imgur.com/TCl7htq.png)

5、这时候重新发布一下，一定要用你畅言配置的白名单域名访问，否则看不到效果：

![](https://i.imgur.com/3EjQr6Z.png)

## 集成打赏功能

1、在畅言后台的实验室找到打赏功能，配置如下：

![](https://i.imgur.com/dEhavL7.png)

2、复制代码

![](https://i.imgur.com/meuPU7z.png)

3、在hexo\themes\yelee\layout_partial下新建reward.ejs文件，键入刚刚复制的代码。

4、在hexo\themes\yelee\layout_partial下的article.ejs中添加如下代码：

	<!-- 添加打赏功能 只在文章详情中显示-->
	<% if (!index && theme.reward){ %>
	<%- partial('reward') %>
	<% } %>

5、在主题配置文件中添加如下代码：

	#是否开启打赏功能
	reward: true

效果如图所示：

![](https://i.imgur.com/qJgeZ8C.png)
