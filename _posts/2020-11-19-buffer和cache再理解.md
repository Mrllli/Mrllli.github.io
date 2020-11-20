---
layout: post
title: buffer和cache再理解
---

> 所谓buffer和cache都可以称作缓存，其中cache也叫page cache，中文叫页缓存。虽然都叫缓存，但是他们两个却有本质的区别，区别就是buffer缓存用于和磁盘裸IO时的缓存，cache用于通过文件系统跟磁盘IO时的缓存，早期的Linux通过文件系统和磁盘IO时需要经过buffer和cache，现在已经改为只需要经过cache了。缓存的作用主要是为了平衡快速的内存和慢速的磁盘之间的速度差，在读的时候，读到缓存中，以后再读就不需要和磁盘IO了，减少IO次数。在写的时候，写入缓存，当积累一定的量，再刷入磁盘中，减少IO次数，提高性能。
>
> PS:一般我们操作文件的读写都是通过文件系统，不要通过文件系统而进行裸IO的一般是存储系统，如数据库
>
> ```bash
> ubuntu@VM-0-16-ubuntu:~$ free
>               total        used        free      shared  buff/cache   available
> Mem:        1877504     1511628       71696       19172      294180      195116
> Swap:             0           0           0
> ```