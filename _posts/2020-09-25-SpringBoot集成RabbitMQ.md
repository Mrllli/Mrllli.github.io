---
layout: post
title: SpringBoot集成RabbitMQ
---

> **pom.xml**
>
> ```xml
> <dependency>
> 	<groupId>org.springframework.boot</groupId>
> 	<artifactId>spring-boot-starter-amqp</artifactId>
> </dependency>
> ```

> **application.properties**
>
> ```properties
> #rabbitmq
> spring.rabbitmq.host=129.211.61.234
> spring.rabbitmq.port=5672
> spring.rabbitmq.username=admin
> spring.rabbitmq.password=admin
> #rabbitmq消息确认
> spring.rabbitmq.publisher-confirms=true
> spring.rabbitmq.publisher-returns=true
> ```

> **RabbitConfig**
>
> ```java
> @Configuration
> public class RabbitTopicConfig {
> 
>     public static String message = "topic.message";
>     public static String messages = "topic.messages";
> 
>     //初始化两条消息队列，名称分别为topic.message，topic.messages
>     @Bean
>     public Queue queueMessage() {
>         return new Queue(RabbitTopicConfig.message);
>     }
> 
>     @Bean
>     public Queue queueMessages() {
>         return new Queue(RabbitTopicConfig.messages);
>     }
> 
>     //初始化exchange，名称为exchange
>     @Bean
>     TopicExchange exchange() {
>         return new TopicExchange("exchange");
>     }
> 
>     //将两条消息队列分别与exchange绑定，路由键分别为topic.message和topic.#(#为可以匹配任意单词)
>     @Bean
>     Binding bindingExchangeMessage(Queue queueMessage, TopicExchange exchange) {
>         return BindingBuilder.bind(queueMessage).to(exchange).with("topic.message");
>     }
> 
>     @Bean
>     Binding bindingExchangeMessages(Queue queueMessages, TopicExchange exchange) {
>         return BindingBuilder.bind(queueMessages).to(exchange).with("topic.#");
>     }
> }
> ```

> **publisher**
>
> ```java
> @Component
> public class RabbitTopicSender {
> 
>     @Autowired
>     RabbitTemplate rabbitTemplate;
> 
>     public void send1(){
>         String context = "hi, i am message 1";
> 		//第一个参数为交换机名称，第二个参数是路由键匹配参数，第三个参数为内容
>         this.rabbitTemplate.convertAndSend("exchange", "topic.message", context);
>     }
> 
>     public void send2(){
>         String context = "hi, i am message 2";
> 
>         this.rabbitTemplate.convertAndSend("exchange", "topic.messages", context);
>     }
> }
> ```

> **receiver**
>
> ```java
> @Component
> public class HelloReceiver {
> 
>     @RabbitListener(queues = "topic.message")
>     public void receiveTopic1(String hello){
>         System.out.println("TopicRec1  : " + hello);
>     }
> 
>     @RabbitListener(queues = "topic.messages")
>     public void receiveTopic2(String hello){
>         System.out.println("TopicRec2  : " + hello);
>     }
> 
> }
> ```

> **controller**
>
> ```java
> @RestController
> public class RabbitmqController {
> 
>     @Autowired
>     RabbitTopicSender rabbitTopicSender;
> 
>     @GetMapping("/sendRabbitMessage")
>     public void queryAll(){
>         
>         rabbitTopicSender.send1();
>         rabbitTopicSender.send2();
>     }
> }
> ```
>
> 