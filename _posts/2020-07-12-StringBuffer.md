---
layout: post
title: StringBuffer
---

> 一般创建字符串变量我们都是这样创建
>
> ```java
> String str = "abc";
> ```
>
> 但是这样创建是不建议对str值进行变化的
>
> ```java
> str = str + "d";
> ```
>
> 执行如下操作会现在内存中生成一个"d"，然后再生成一个"abcd"，同时之前的"abc"依然保存在内存空间中，会造成内存空间极大的浪费
>
> 因此我们使用如下方法创建
>
> ```java
> StringBuffer str = new StringBuffer("hello");
> StringBuilder str1 = new StringBuilder("world");
> ```
>
> StringBuffer和StringBuilder的不同点之处就在于，StringBuilder线程不安全，只能单线程情况下做，效率高。StringBuffer线程安全(由于方法中都加了synchronzied关键字)，适合多线程情况下去做，效率较低。

