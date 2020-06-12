---
layout: post
title: LIMIT和OFFSET
tags: 数据库
---

> 单用LIMIT就是从第一个参数的位置开始，寻找第二个位置参数的值个个数的结果
>
> ```sql
> select * from table_name LIMIT 2,3;
> ```
>
> 从表中从的2+1个位置开始依次取3条结果返回

> LIMIT和OFFSET公用就是与单用LIMIT参数调换位置
>
> ```sql
> select * from table_name LIMIT 2 OFFSET 5;
> ```
>
> 从表中的第5+1个位置开始取两条结果返回

