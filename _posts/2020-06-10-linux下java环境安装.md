---
layout: post
title: linux下java环境安装
tags: java环境
---

> 1.上oracle官网下载jdk包，由于本人是ubuntu64位系统，因此下载x64.tar.gz包，如果是32位的则下载另一个.tar.gz包
>
> 2.下载到linux后，运行
>
> ```bash
> tar zxvf jdk-8uversion-linux-x64.tar.gz
> ```
>
> 命令，解压到当前目录下
>
> 3.配置环境变量
>
> ```bash
> sudo chmod 777 /etc/profile                      //修改读写权限
> ```
>
> ```
> vim /etc/profile                                //进入文件编辑
> ```
>
> ```bash
> export JAVA_HOME = /home/ubuntu/jdk1.8.0_251
> export CLASSPATH = $JAVA_HOME/lib:$CLASSPATH
> export PATH = $JAVA_HOME/bin:$PATH
> ```
>
> 配置好后，刷新环境
>
> ```
> source /etc/profile
> ```
>
> 测试
>
> ```
> java -version
> ```
>
> 如果输出java版本号则说明配置成功



