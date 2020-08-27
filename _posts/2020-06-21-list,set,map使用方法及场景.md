---
layout: post
title: list,set,map使用方法及场景
tags: java基础
---

> **List**
>
> ```java
> List<String> list1 = new ArrayList<String>();//创建只能存放String的ArrayList
> List<String> list2 = new LinkList<String>();//底层是链表
> list1.add("中国");
> list2.add("中国人");
> list1.add("Chinese");//增加元素
> list1.remove("中国");
> list1.remove("Chinese");//移除某一个元
> list2.clear();//清空所有元素
> ```
>
> ArrayList 更适合索引访问，LinkList更适合增加或者删除元素.这俩线程都不同步，都按顺序插入

> **Set**
>
> ```java
> Set<String> set1 = new HashSet<String>();
> set1.add("string");
> set1.add("string");//false
> set1.remove("string")
> ```
>
> 创建集合，集合内元素不能重复，底层通过HashMap实现，无法保证顺序。

> **Map**
>
> ```java
> Map<String,Integer> map1 = new HashMap<String,Integer>();
> map1.put("zs",3);
> map1.put("ls",4);	//加入entry
> map1.get("ls");	//获取对应value
> map1.remove("ls");	//移除entry
> map1.remove("zs",3);
> ```
>
> 创建Map，Map内key值不能重复，底层实现通过数组加链表加红红黑树实现。当链表长度超过8后将会自动转为红黑树。红黑树将在下一篇博客具体介绍

> **PS:hashMap的Key值可以为空，value也可以为空，默认长度是16**