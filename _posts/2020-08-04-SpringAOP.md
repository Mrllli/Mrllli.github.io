---
layout: post
title: SpringAOP
---

> AOP面向切面编程
>
> ```Java
> @Aspect
> @Compenent
> public class SpringTest{
>     
>     @Pointcut("execution(*com.lhl.dao.*.*(..))")
>     public void name1(){}
>     
>     @Before("name1")
>     public void advice(){
>         System.out.println("增强方法的具体内容");
>     }
>     
> }
> //这段代码的主要意思就是在com.lhl.dao下的所有类所有方法执行前加入一个通知，这个通知就是advice()方法执行的内容，Before定义了是在所有方法执行之前执行
> //这个类就是一个切面，切点包含了连接点，因此什么是一个切面，切面就是通知，切点，连接点共同组成的那个类就是一个切点
> 
> @Repository
> public class UserDao{
>     
>     public void testMethod(){
>         System.out.println("UserDao")
>     }
> }
> 
> //增强方法的具体内容
> //UserDao
> ```
>
> 其实AOP很相似于动态代理，都是相当于增强某一个方法，都是相当于给目标类进行加强而得到一个代理类，其原理就是反射机制
>
> ```java
> public class Test1{
>     public static void main(String[] args){
>         Test2 test = new Test2();
>     	Method method = test.getClass().getMethod("Method1",String.class);
>     	method.invoke(test,"123");
>     }
> }
> //反射机制demo
> ```
>
> spring在给某个对象加上切面的时候就说明spring已经把原对象转换成代理对象了。
>
> 在spring初始化的过程中当进行到spring实例化对象的时候，先实例化出**目标对象**，再beanPostProcessor初始化出**代理对象**，之后获取的对象都是代理对象，原对象已经被抛弃。
>
> **PS:spring的bean是默认单例的**                
