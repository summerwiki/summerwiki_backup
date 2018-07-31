---
title: hbase干货分享：集成phoenix
date: 2018-05-10 00:00:00
category: 大数据
tags: hbase
word_count: true
toc: true
comments: true
original: true
fancybox: true
---
由于Hbase不支持SQL语句和二级索引，导致业务上不能利用之前的开发经验来查询Hbase。目前业界已经有了很多方案支持Hbase的SQL查询，比如说：Hive、Impala、Phoenix等。三种产品各有各的优势，今天主要介绍下Phoenix与Hbase的集成。

<!-- more -->

## Hbase集成Phoenix

1、下载与Hbase版本对应的Phoenix，Phoenix下载地址，如图所示我选择0.98版本演示。

![](https://i.imgur.com/uqTRtis.png)

![](https://i.imgur.com/BykFQtq.png)

2、先停止Hbase集群。

	stop-hbase.sh

3、将下载好的Phoenix上传至你的需要执行SQL语句的节点上并解压，然后将phoenix／目录下的phoenix-core-4.8.0-HBase-0.98.jar, phoenix-4.8.0-HBase-0.98-server.jar复制到hbase/lib目录下。

	cp phoenix-core-4.8.0-HBase-0.98.jar hbase/lib
	cp phoenix-4.8.0-HBase-0.98-server.jar hbase/lib

4、修改hbse-site.xml文件，添加如下内容。
	
	<property>
	  <name>hbase.rpc.timeout</name>
	  <value>3600000</value>
	</property>

5、将hbase-site.xml文件拷贝至phoenix/bin目录下。

	cp hbase/conf/hbase-site.xml phoenix/bin

6、重启Hbase集群

	start-hbase.sh

7、启动phoenix/bin目录下的sqlline.py文件

	./sqlline.py

8、phoenix的帮助命令

	!help

9、查看HBase中所有的表

	!tables

10、刚开始如图看到只有4张系统表

![](https://i.imgur.com/ybo0PL1.png)

11、如果Hbase之前已经存在table数据，需要在phoenix创建同名的table或view才能看到之前Hbase的表。比如说现在我hbase有一张test_table的表，我想在phoenix中使用SQL语句操作这张表，目前在phoenix中看不到这张test_table表；

![](https://i.imgur.com/Dkldi5N.png)

首先我需要在phoenix中新建一张同名的表

	create table "test_table"("ROW" varchar primary key,"test_cf"."payload" varchar);

再来看phoenix中就已经有了这张表，并且已经将数据同步过来了。

![](https://i.imgur.com/gx3Cz3B.png)

我们可以用select命令查询一下

	select * from "test_table";

![](https://i.imgur.com/VRw4h5L.png)

12、这个地方有个小坑，选要注意一下。我们在phoenix中输入查询语句的时候，phoenix帮我们把SQL语句自动转换为大写，如果Hbase中table名原本就是小写的该怎么办呢？需要我们用双引号将table名括起来。否则会报错Error: ERROR 1012 (42M03): Table undefined. tableName=TEST_TABLE(state=42M03,code=1012)。

![](https://i.imgur.com/OT1PzKe.png)