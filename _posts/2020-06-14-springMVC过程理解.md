---
layout: post
title: springMVC过程理解
tags: springmvc
---

![如图所示](E:\GitHubBlog\pictures\springmvc.png)

> 具体步骤：**Dispatcher Servlet** 接受到请求之后给**HandlerMapping**进行处理，返回的**HandlerExecutionChain**根据**Handler**寻找对应对的适配器**HandlerAdapter**，然后调用**handler(Controller类)**中的方法**(RequestMapping对应的方法)**返回**ModelAndView**，通常返回一个字符串类型的值，再通过**ViewResolver(视图解析器)**解析出**view**,**view**其实也是一个接口，通过传入**model**，**request**等返回**response**对象给**Dispatcher Servlet**，然后**Dispatcher Servlet**再返回给容器，容器再返回给客户端浏览器呈现。