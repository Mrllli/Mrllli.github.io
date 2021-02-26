---
layout: post
title: linux之select,poll,epoll再理解
---

> linux中网络IO有多种方式，如BIO，NIO，AIO等，其中非阻塞IO是重点。由于BIO是一个连进来的Socket需要开一个线程去对应跟踪，因此在高并发场景下，cpu上下文切换以及内存都会成为瓶颈，为了解决这个问题Linux有Select，poll，epoll来优化场景
>
> Select其实就是在用户态遍历Socket集合，但是需要从用户空间传入内核空间，然后再传回用户空间，走一个系统调用，且限制最大连接数为1024，水平触发方式LT
>
> poll和select类似，只是没有最大连接数的限制了
>
> epoll是直接在内核态遍历，不需要系统调用，有LT水平触发和ET边缘触发两种方式，水平触发就是需要遍历，边缘触发就是谁状态变了我就读谁，但是需要一次将数据IO完，如果没IO完，剩下的数据就读不到了
>
> redis使用的LT模式，而Nginx使用的是ET模式