---
layout: post
title: lock和synchronized比较
---

> **synchronized**是非公平锁，**lock**(ReentrantLock)可以是非公平锁也可以是公平锁
>
> **公平锁：**先到先得，线程按顺序得到锁，先前节点的线程会唤醒后一个节点的线程
>
> **非公平锁：**与顺序无关，谁先抢到谁得到锁，非公平锁的效率高于公平锁，因为减少了对于线程挂起的开销

> **synchronized**是JVM层面的锁，**lock**是接口层面的锁

> **synchronzied**可以主动释放锁，**lock**不能主动释放锁，且操作必须放到try,catch里，防止释放不了锁

> lock有方法trylock()尝试获得锁，如果获取不到则立即返回，不会一直在那里尝试获得锁

>**ReentrantLock**和**synchronized**都是可重入锁

> **synchronized** 不可中断，除非抛出异常或者正常运行完成，**ReentrantLock** 可中断，trylock(time,time.unit)就是一种中断机制，当等待了time时间还没得到锁，则可以直接去干别的事，不会一直在那里获得锁
