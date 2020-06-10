---
layout: post
title: springboot详解
tags: springboot
---

> 废话不多说直接上代码：
>
> ```java
> package pk1;
> public interface Service{
>     void test();
> }
> -----------------------------------------------------------------------------------
> package pk2;
> import pk1.Service;
> 
> @Service("t1")
> public class MyClass1 implements Service{
>     @Override
>     public void test(){
>         ;
>     }
> }
> 
> -----------------------------------------------------------------------------------
> package pk3;
> import pk1.Service; 
>     
> public class Test{
>     @Autowired
>     Service ser;
>     ser.test()       //正常运行
> }
>     
> ```
>
> **解释：**`@Service("t1")`将它修饰的类注册成一个bean,相当于:
>
> ```
> <bean id="t1" class="pk2.MyClass1"></bean>
> ```
>
> `@Autowired`相当于依赖注入，意思就是ser指向的是MyClass1，因此调用ser.test()，就是调用MyClass1里的test()。这也就是传说中的**面向接口编程**

> 再来说说`@ComponentScan`，这个的意思就是组件扫描，告诉Spring到哪里去扫描bean,为包定义了组件扫描后，Spring将搜索所有包以及子包获取组件bean
>
> 但是在Springboot里`@ComponentScan`被替换成了`@SpringBootApplication`，它位于主应用程序里，它会扫描所有位于主应用程序下方或者同级的包以及子包，因此应该把它放在最外层和其它包处于一层，而它是个.java文件。有了它就可以扫描所有的bean组件，以及使用了
>
> 还有一个`@MapperScan`，它是可以扫描所有的mapper类注解，也就是Dao包内的注解，如@param和@return，因此跟`@SpringBootApplication`位于同一.java文件里。与之相关的就是配置文件里还应该配置一个*Dao.java对应\*Dao.xml相关的配置

