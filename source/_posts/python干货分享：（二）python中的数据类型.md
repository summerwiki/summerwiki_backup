---
title: python干货分享：（二）python中的数据类型
word_count: true
toc: true
comments: true
original: true
fancybox: true
date: 2018-07-10 16:36:46
category:
tags:
---
python中数据类型大体分为：Number（数字）、String（字符串）、List（列表）、Dictionary（字典）、Tuple（元组）、Bool（布尔）

<!-- more -->

	Number（数字）                  包括int,long,float,complex   
	String（字符串）                例如：hello,"hello",hello   
	List（列表）                    例如：[1,2,3],[1,2,3,[1,2,3],4]   
	Dictionary（字典）              例如：{1:"nihao",2:"hello"}   
	Tuple（元组）                   例如：(1,2,3,abc)  
	Bool（布尔）                    包括True、False 

## 数字类型

	>>> i = 10  
	>>> type(i)  
	<type 'int'>  
	  
	>>> i=10000000000  
	>>> type(i)  
	<type 'long'> 
	
	>>> i = 10000.1212  
	>>> type(i)  
	<type 'float'> 

## 字符串类型

	>>> str1 = 'hello world'  
	>>> str2 = "hello world" 

### 常用方法

	str="hello world summer is summerwiki.com"
	print(str.find("world"))#找不到返回-1
	print(str.rfind("world"))#从右侧查找
	print(str.index("world"))#找不到报错
	print(str.rindex("world"))
	print(str.count("summer"))#str中"summer"的个数
	print(str.replace("summer","tom"))
	print(str.replace("summer","tom",1))#只替换第一处
	print(str.split(" ",2))#按照“ ”切分，只切分2次
	print(str.split(" "))
	print(str.split("is"))
	print(str.partition("is"))#按照“is”切分，但是保留“is”本身
	print(str.capitalize())#将首字母大写
	print(str.title())#将所有单词首字母大写
	print(str.upper())#将整个字符串转换为大写
	print(str.lower())
	print(str.endswith("com"))#判断是否是"com"结尾
	print(str.startswith("com"))
	print(str.ljust(50))#50个字符中左对齐
	print(str.rjust(50))
	print(str.center(50))#50个字符中居中显示
	print(str.isalpha())#判断是否是字符串
	print(str.isdigit())#判断是否是数字
	print(str.isalnum())#判断全部是字符串或者数字
	print(str.isspace())#判断全部是空格

## 列表类型

	>>> nums = [1,2,3,4]  
	>>> type(nums)  
	<type 'list'>  
	>>> print nums  
	[1, 2, 3, 4]  
	>>> strs = ["hello","world"]  
	>>> print strs  
	['hello', 'world']  
	>>> lst = [1,"hello",False,nums,strs]  
	>>> type(lst)  
	<type 'list'>  
	>>> print lst  
	[1, 'hello', False, [1, 2, 3, 4], ['hello', 'world']] 

### 索引方式访问列表

	lst = [1,2,3,4,5]
	print(lst[0])  #1
	print(lst[-1])  #5
	print(lst[-2])  #4

### 分片方式访问列表

	nums = [1,2,3,4,5]
	print nums[0:3]  #[1, 2, 3] #前三个元素
	print nums[3:]  #[4, 5]    #后两个元素  
	print nums[-3:]  #[3, 4, 5] #后三个元素 不支持nums[-3:0]  
	numsclone = nums[:]  
	print numsclone  #[1, 2, 3, 4, 5]  复制操作  
	print nums[0:4:2]  #[1, 3]    步长为2  
	nums[3:3] = ["three","four"]  #[1, 2, 3, 'three', 'four', 4, 5]  在3和4之间插入  
	nums[3:5] = []  #[1, 2, 3, 4, 5] 将第4和第5个元素替换为[] 即删除["three","four"]

### 常用方法

	nums = [1,2,3,4]
	strs = ["hello","world"]
	nums.append(5)  #[1,2,3,4,5]
	nums.insert(5,6)  #[1,2,3,4,5,6]
	nums.extend(strs)  #[1, 2, 3, 4, 5, 6, 'hello', 'world']
