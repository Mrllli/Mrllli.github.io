---
layout: post
title: java中关键字protected
tags: java
---

> 关于java中关键字protected，给出一点我自己的理解，代码如下：
>
> ```java
> package pk1;
> 
> public class Person{
>     protected int a;
> }
> ```
>
> ```java
> package pk1;
> 
> public class Test{
>     public void test1(){
>         Person per = new Person();
>     	per.a = 1;  //true
>     }
> }											//同一个包里可以访问		
> ```

> ```java
> package pk2;
> 
> public class Test2 extends Person{
>     public void test2(){
>         Person per = new Person();
>         per.a = 1;//false
>     }
>     
>     public void test3(){
>         a = 1; //true
>     }
> }
> ```

> **总结**:同一个包里可以访问,不同包里不可以访问,但子类可以继承protected修饰的属性,不可访问父类的属性