---
layout: post
title: @Autowired和IOC,监听
tags: spring
---

> **IOC**
>
> spring项目都是以一个容器**IOC**为核心，在这可以把他想象成一个装着糖的大盒子，大盒子里的一个个糖实例就是我们所说的bean，这个大盒子就是**IOC**

> **@Autowired**
>
> @Autowired就是自动注入的意思，与之相同的还有@Resource，自动注入的意思就是
>
> ```java
> @Autowired
> Object obj;
> ```
>
> 在IOC容器里，找到一个实例属于Object类，将该实例的值和属性全部给obj这个新创建的对象

> **监听**
>
> ```java
> @Component
> public class NettyBooter implements ApplicationListener{
> 	@Override
> 	public void onApplicationEvent(Application event){
> 		//方法体
> 	}
> }
> ```
>
> 在实例化所有bean之后，SpringIOC容器会有一个发布事件的动作，此时就会调用ApplicationListener 接口实例中的onApplicationEvent(E event)方法



