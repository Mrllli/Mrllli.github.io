---
layout: post
title: Spring & quartz
tags: quartz
---

> 在spring中使用quartz的步骤如下
>
> 1.生成一个实例类entity,将实例类以及其属性配置进入**applicationContext.xml**spring配置文件里
>
> 2.写一个基本的Service类出来，将来Job将调用里面的方法
>
> 3.写一个实现Job接口的类(XxxJob)，并重写接口的方法，在方法里调用之前的Service。
>
> 4.在SpringIOC里配置JobDetail，并增加jobClass和jobDataAsMap两个属性，jobClass属性值为之前的XxxJob，jobDataAsMap里的key值配置属性为之前的实例
>
> 5.在SpringIOC里配置trigger，trigger里两个属性jobDetail和cronExpression，前者用于调用之前实例JobDetail，后者用于控制何时触发该方法，语法如下
>
> ```xml
> value = ""#{scheduleJobEntity.ceonExpression}""
> ```
>
> 6.最后配置调度器SchedulerFactoryBean，里面一个属性triggers，用于调用之前配置好的trigger

> **总结:**因此总体架构来说在Spring里就是调度器可以调度不同的trigger,将这些trigger储存在集合list中，而每个trigger又可以绑定一个jobDetail，每个jobDetail又对应着一个job类，job类中调用的是Service里提供的服务。