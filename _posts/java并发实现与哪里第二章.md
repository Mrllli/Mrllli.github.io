---
layout:post
title: java并发实现原理第二章读书笔记
---

首先，在类被加载时，需要加载native方法实现的动态链接库，因此这段加载代码必须是静态加载器中的程序段。比如下面的ExampleClass类：

```java
public class ExampleClass {
    static {
        System.load("example.dll");
    }
    
    public native void example();
}
```