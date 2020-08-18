---
layout: post
title: CountDownLatch和CycliBarrier
---

> CountDownLatch是减法，而CycliBarrier是加法
>
> ```java
> public class Test{
> 	
>     public static void main(String[] args){
>         CountDownLatch cD = new CountDownLatch(5);
>         
>         long start = System.currentTimeMillis();
>         
>         for(int i=0;i<5;i++){
>             new Thread(){
>                 public void run(){
>                     System.out.println("这时第" + i + "个。。。");
>                     cD.countDown();
>                 }
>                 
>             }.start();
>         }
>         cD.await();
>         long end = System.currentTimeMillis();
>         System.out.println(end - start + "秒");
>     }
> 	
> }//当count减少为0的时候，主线程执行后面的代码。
> ```
>
> ```java
> public class Test1{
>     public static void main(String[] args){
>         CycliBarrier cB = new CycliBarrier(7,()->{System.out.println("lol")});
>         for(int i=0;i<7;i++){
>             new Thread(){
>                 public void run(){
>                     System.out.println("这是第" + i + "个线程");
>                     cB.await();
>                 }
>             }
>         }
>     }
> }//每一个线程执行run方法就会使计数加一，当计数等于7的时候打印lol
> ```
>
> 