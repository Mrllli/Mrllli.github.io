---
layout: post
title: zookeeper
tags: zookeeper
---

> 去apache官网下载zookeeper,我下的是[**https://mirrors.gigenet.com/apache/zookeeper/zookeeper-3.6.1/apache-zookeeper-3.6.1-bin.tar.gz**](https://mirrors.gigenet.com/apache/zookeeper/zookeeper-3.6.1/apache-zookeeper-3.6.1-bin.tar.gz)

> 下载完压缩包后在linux当前压缩包所在目录输入以下命令：
>
> ```bash
> tar -zxvf apache-zookeeper-3.6.1-bin.tar.gz               //解压
> ```
>
> 之后进入解压完后目录：
>
> ```bassh
> mkdir data
> ```
>
> 找到conf目录，重命名zoo_sample.cfg为zoo.cfg：
>
> ```
> cd conf
> mv zoo_sample.cfg zoo.cfg
> ```
>
> 之后输入命令：
>
> ```bash
> vim zoo.cfg
> ```
>
> 修改文件内**datadir = zookeeper整个项目所在目录/data** （就是刚刚创建的那个data里）
>
> 最后就可以启动zookeeper啦：
>
> ```bash
> cd ..
> cd bin                                //进入bin目录
> ./zkServer.sh start
> ```
>
> 大功告成...

