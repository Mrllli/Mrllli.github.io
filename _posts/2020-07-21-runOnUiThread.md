---
layout: post
title: runOnUiThread
---
> runOnUiThread是android开发里的一个概念，意思就是将该线程里的run方法中所执行的任务丢到主线程中去执行，因为UI操作必须在主线程中执行才可以，在子线程中执行会报错

> 那么它是怎么做到将子线程中的任务丢给主线程的呢，这就涉及到消息队列，looper，任务以及handler。每个线程只能绑定一个消息队列一个looper，但是可以有多个handler和任务。
runOnUiThread通过内部判断当前线程是不是主线程，如果不是，则将任务丢给主线程的handler，handler.post(task)将任务丢到主线程的消息队列末尾，然后looper就可以从消息队列读任务
然后并执行。looper对于线程的作用是保持线程循环，使线程处于一个活着的状态。主线程默认包含，子线程默认不包含。
