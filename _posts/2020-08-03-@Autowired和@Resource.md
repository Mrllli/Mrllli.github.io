---
layout: post
title: Autowried和@Resource
---

> @Autowired默认是通过byType从ioc容器获取实现了接口的对象，但如果有两个实现类的话，就会产生冲突需要通过qualify指定具体实现类的名字
>
> @Resource默认是通过byName从ioc容器中找和当前引用相同的实现类的名字，如果没有再通过byType，同样如果有两个实现类，可以通过加一个name="xxx"解决

