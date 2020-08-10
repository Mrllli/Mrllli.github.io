---
layout: post
title: TreeSet,TreeMap
---

> TreeSet是一种排序形式的Set集合，那它是通过什么排序的呢，它是通过加入treeSet的元素重写compareTo方法实现的，compareTo方法里比较的是什么属性那就是比较的是什么属性，底层跟TreeMap一样，是红黑树实现的
>
> TreeMap是一种排序的Map，底层结构是红黑树，根据key值的大小来进行红黑树的排序，如果key是个对象，同上所述。红黑树也就是个自平衡二叉树，查询复杂度logn。因此hashmap查询复杂度要低于TreeMap，为1，因此只是在需要排序的时候才用TreeMap和TreeSet。
>
> **PS:Arrays.sort(),也是根据comparable接口来的。**