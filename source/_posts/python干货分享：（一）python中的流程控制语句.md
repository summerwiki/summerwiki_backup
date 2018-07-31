---
title: python干货分享：（一）python中的流程控制语句
word_count: true
toc: true
comments: true
original: true
fancybox: true
date: 2018-07-10 16:02:54
category: 技术栈
tags: python
---
Python语言简单，且拥有庞大的外部库，如Matplotlib、Numpy、Pandas、SciPy、TensorFlow。这些库在Python中都是相当有名气的，使用起来也较为方便。因此，Python也成为了大数据、人工智能、机器学习的主要语言从而拥有相当多的学习者。

今天主要讲一下python中的流程控制语句，接下来我将会持续更新关于python的一系列教程，欢迎围观！
<!-- more -->

学习一门语言，当然要从hello world开始了，我们先来看一下python中输入输出

1、输出hello world

	print("hello world")

2、输入

	age = input("请输入年龄：")

python中的输入默认是字符串类型，如果需要转型可以使用**age = int(input("请输入年龄："))**

3、if else分支

	if age % 2 == 0:
		pass
	elif age % 2 == 1:
		pass
	else:
		pass

4、while 循环

	while True:
	或
	while age == 22:

5、for 循环

	for i in range(1,10):#range(1,10)指的是从1到9的整数范围，一个左闭右开的集合
		print(i)

	

练习1：输入一个学生的信息（姓名，年龄，地址），然后输出年龄是否为偶数

	name=input("请输入姓名：")
	age=int(input("请输入年龄："))
	address=input("请输入地址：")
	if age % 2 == 0 :
	    print("年龄为偶数！")
	else:
	    print("年龄为基数！")

练习2：打印九九乘法表

	for x in range(1,10):
	    for y in range(1,x+1):
	        print("%d*%d=%d\t" % (y, x, x * y), end="")
	    print("")

**总结：python语句末尾可以不用分号（;）结尾，python中一定要注意缩进**