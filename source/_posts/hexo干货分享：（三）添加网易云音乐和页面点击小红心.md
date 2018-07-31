---
title: hexo干货分享：（三）添加网易云音乐和页面点击小红心
date: 2018-05-07 00:00:00
category: 灯火阑珊
tags: hexo
word_count: true
toc: true
comments: true
original: true
fancybox: true
---
作为一名程序猿，怎能没点音乐，music！跟我一起摇摆！

<!-- more -->

## 集成网易云音乐

1、打开[网易云音乐网页版](http://music.163.com/)

2、MarkDown 是支持 h5 代码的，在网易云音乐找到外链代码：

![](https://i.imgur.com/C5IUpjd.png)

![](https://i.imgur.com/LZc2rls.png)

3、将代码拷贝至你想要显示的页面即可。

4、更新本地歌单，博客内的播放列表自动更新

5、生成的列表，点击播放按钮却不播放音乐。

解决方法：查看你播放列表的所有音乐是否都有版权，没有版权的音乐是不能播放的。

![](https://i.imgur.com/2O4wC8e.png)

## 页面点击小红心

1、在hexo\themes\yelee\source\js新建文件love.js

2、[点击该链接](http://7u2ss1.com1.z0.glb.clouddn.com/love.js)下载代码并拷贝到love.js

3、在hexo\themes\yelee\layout_partial下的after-footer.ejs添加如下代码：

	<!-- 页面点击小红心 -->
	<script type="text/javascript" src="/js/love.js"></script>

4、效果

![](https://i.imgur.com/iOnO30q.gif)