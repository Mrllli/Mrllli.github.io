---
layout: post
title: LRU,LFU,FIFO
---

> FIFO是一种队列的模式，先进先出
>
> LRU核心思想是，如果数据最近被访问过，那么将来被访问的概率也会更高，适用于热点数据等，遇到大量冷数据可能会被污染
>
> LFU核心思想是每个访问都被引用计数一次，如果队列满了，则淘汰队列最后一个，就是引用计数最少的那个