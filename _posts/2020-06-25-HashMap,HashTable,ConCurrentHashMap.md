---
layout: post
title: HashMap,HashTable,ConCurrentHashMap
---

> HashMap是非同步的，是线程不安全的，键值都允许null
>
> HashTable是同步的，是线程安全的，不允许null值出现，内部方法都经过synchronized的修饰
>
> ConCurrentHasMap是线程安全的HashMap的实现，对整个桶数组进行了分段分割(Segment),在每一个分段上都用lock锁进行保护，对比于HashTable的syn具有更好的并发性能，不允许有null值出现
>
> **PS：**HashSet，ArrayList,LinkedList都允许null值，lock锁是一个接口，需要实现类ReentrantLock等实例化后使用，syn是内置语言的实现。syn在发生异常时会自动释放占有的锁，lock发生异常时，如果没有通过unlock释放锁则很可能发生异常，造成死锁，因此，lock一般放在try,catch里，并在finally里释放锁，且lock可以让等待锁的线程相应中断，syn不能够响应中断