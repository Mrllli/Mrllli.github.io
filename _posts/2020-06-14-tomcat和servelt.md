---
layout: post
title: tomcat和servelt
tags: java
---

> **Servelt**
>
> servelt实质上是一个Java接口，它的作用是规范实现它的类。servelt有5个方法，因此实现他的类都需要有这5种方法。但是servelt并不能直接处理HTTP请求，需要把它放到容器里才可以使用它，因此这个容器就是我们所说的Tomcat，Tomcat监听TCP端口，根据请求的url等信息，交给对应的servelt类处理，然后调用处理的servelt的service的方法，返回一个response对象，然后tomcat把这个response返回给客户端

> **Tomcat**
>
> 前面讲了tomcat实质上是一个容器，里面放的是各种servelt实现类。但是，tomcat和nginx以及apache又是什么关系呢，apache和nginx都是http服务器，通过监听端口，绑定ip，响应浏览器的请求，并返回响应的资源给浏览器，但是他们有一个缺点，就是只能返回静态资源给浏览器，简单来说就是不同人使用的不同浏览器拿到的东西都一样。而tomcat能够动态的生成资源并返回给客户端，servelt技术以及jsp可以java也具有处理请求的能力。tomcat也可被认作是http服务器，但它通常会和nginx配合使用，有两点好处;
>
> **1.**动静态资源分离，通过Nginx的反向代理，所有动态资源请求给tomcat,静态资源交给Nginx，减轻tomcat压力
>
> **2.**负载均衡，通过Nginx的负载均衡功能可以将请求通过算法分给各个不同实例的tomcat进行处理，减轻压力

