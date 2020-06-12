---
layout: post 
title: group by和order by
tags: 数据库
---

> **group by** 就是将同种类的值组合在一起，一般和sum等函数连用，比如，统计某个同学的总分
>
> ```sql
> select sno,sum(grade) from table_name where sno=2 group by sno;
> ```
>
> 统计sno=2这位学生的总分

>**order by** 就是进行排序，比如将全班同学总分进行排序：
>
>```sql
>select sno,sum(grade) from table_name group by sno order by sum(grade) desc;
>```
>
>将每位同学成绩加和起来并进行排名排序，降序排序