---
layout: post
title: Object之hashCode()和equals()
---

> 当一个hashMap放置一个key时，它先比较的是这个对象的内存地址转换为hashCode后所位于数组的位置，然后用这个对象的equals()方法与这个位置上的元素进行逐一的比较,而Object类中的equals就是==，所以需要重写equals方法。意思就是你如果要重写equals方法一定要重写hashCode方法，且hashCode方法是根据类成员变来进行定义。需要满足相同对象的hashCode相同，但相同的hashCode不一定是同一个对象。