---
layout: post
title: ArrayList扩容
---

> ```java
> import java.util.*;
> 
> ArrayList arr = new ArrayList<>();//初始化的时候arr长度为0
> 
> ```
>
> 当加进去第一个数字的时候，将数组长度初始化为10，如果加进去了第十一个元素，再将数组扩容为原来的1.5倍
>
> ```java
> newLength = oldLength + oldLength(>>1)
> ```
>
> 扩容的方法
>
> ```java
> elements = array.copeof(elements,newLength);
> ```
>
> 这段代码的意思就是将原数组里的值赋到一个新的长度为newLength的数组中
>
> 如下：
>
> ```
> {1，2，3，4，5}--->{1,2,3,4,5,0,0,0,0,0}//int[5] -> int[10]
> ```

