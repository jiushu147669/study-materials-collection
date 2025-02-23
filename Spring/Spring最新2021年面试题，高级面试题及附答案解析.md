# Spring 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是 REST / RESTful 以及它的用途是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#1什么是rest-/-restful以及它的用途是什么)

Representational State Transfer（REST）/ RESTful Web 服务是一种帮助计算机系统通过 Internet 进行通信的架构风格。这使得微服务更容易理解和实现。

微服务可以使用或不使用 RESTful API 实现，但使用 RESTful API 构建松散耦合的微服务总是更容易。

### [2、如何在 SpringBoot 中禁用 Actuator 端点安全性？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#2如何在springboot中禁用actuator端点安全性)

默认情况下，所有敏感的 HTTP 端点都是安全的，只有具有 ACTUATOR 角色的用户才能访问它们。安全性是使用标准的 HttpServletRequest.isUserInRole 方法实施的。 我们可以使用

来禁用安全性。只有在执行机构端点在防火墙后访问时，才建议禁用安全性。

### [3、您使用了哪些 starter maven 依赖项？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#3您使用了哪些-starter-maven-依赖项)

使用了下面的一些依赖项：

spring-boot-starter-activemq

spring-boot-starter-security

这有助于增加更少的依赖关系，并减少版本的冲突。

### [4、什么是 AOP 引入?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#4什么是-aop-引入)

引入允许我们在已存在的类中增加新的方法和属性。

### [5、我们如何监视所有 SpringBoot 微服务？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#5我们如何监视所有-springboot-微服务)

SpringBoot 提供监视器端点以监控各个微服务的度量。这些端点对于获取有关应用程序的信息（如它们是否已启动）以及它们的组件（如数据库等）是否正常运行很有帮助。但是，使用监视器的一个主要缺点或困难是，我们必须单独打开应用程序的知识点以了解其状态或健康状况。想象一下涉及 50 个应用程序的微服务，管理员将不得不击中所有 50 个应用程序的执行终端。

### [6、如何使用 SpringBoot 部署到不同的服务器？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#6如何使用-springboot-部署到不同的服务器)

你需要做下面两个步骤：

在一个项目中生成一个 war 文件。

将它部署到你最喜欢的服务器（websphere 或者 Weblogic 或者 Tomcat and so on）。

**第一步：**这本入门指南应该有所帮助：

[https://spring.io/guides/gs/convert-jar-to-war/](https://spring.io/guides/gs/convert-jar-to-war/)

**第二步：**取决于你的服务器。

### [7、SpringBoot 自动配置原理是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#7springboot-自动配置原理是什么)

注解 @EnableAutoConfiguration, @Configuration, [@ConditionalOnClass ](/ConditionalOnClass) 就是自动配置的核心，

@EnableAutoConfiguration 给容器导入 META-INF/spring.factories 里定义的自动配置类。

筛选有效的自动配置类。

每一个自动配置类结合对应的 xxxProperties.java 读取配置文件进行自动配置功能

### [8、SpringBoot 的配置文件有哪几种格式？它们有什么区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#8springboot-的配置文件有哪几种格式它们有什么区别)

.properties 和 .yml，它们的区别主要是书写格式不同。

**properties**

```
app.user.name = javastack
```

**yml**

```
app:
  user:
    name: javastack
```

### [9、Zookeeper 如何 保证 CP](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#9zookeeper如何-保证cp)

当向注册中⼼查询服务列表时，我们可以容忍注册中⼼返回的是⼏分钟以前的注册信息，但不能接受服务直接 down 掉不可⽤。也就是说，服务注册功能对可⽤性的要求要⾼于⼀致性。但是 zk 会出现这样⼀种情况，当 master 节点因为⽹络故障与其他节点失去联系时，剩余节点会重新进⾏ leader 选举。问题在于，选举 leader 的时间太⻓，30 ~ 120s, 且选举期间整个 zk 集群都是不可⽤的，这就导致在选举期间注册服务瘫痪。在云部署的环境下，因⽹络问题使得 zk 集群失去 master 节点是较⼤概率会发⽣的事，虽然服务能够最终恢复，但是漫⻓的选举时间导致的注册⻓期不可⽤是不能容忍的。

### [10、SpringCloud 主要项目](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题，高级面试题及附答案解析.md#10springcloud主要项目)

Spring Cloud 的子项目，大致可分成两类，一类是对现有成熟框架"SpringBoot 化"的封装和抽象，也是数量最多的项目；第二类是开发了一部分分布式系统的基础设施的实现，如 Spring Cloud Stream 扮演的就是 Kafka, ActiveMQ 这样的角色。

### 11、什么是 Spring Batch?

### 12、SpringBoot 如何设置支持跨域请求？

### 13、Spring Cloud Security

### 14、解释 Spring 框架中 bean 的生命周期。

### 15、我们如何连接一个像 MySQL 或者 Orcale 一样的外部数据库？

### 16、[@Required ](/Required) 注解有什么用？

### 17、什么是 Spring beans?

### 18、Spring Cloud 和 SpringBoot 版本对应关系

### 19、如果在拦截请求中，我想拦截 get 方式提交的方法,怎么配置

### 20、什么是 YAML？

### 21、运行 SpringBoot 有哪几种方式？

### 22、spring 提供了哪些配置方式？

### 23、如何在 SpringBoot 启动的时候运行一些特定的代码？

### 24、如果前台有很多个参数传入,并且这些参数都是一个对象的,那么怎么样快速得到这个对象？

### 25、康威定律是什么？

### 26、什么是 AOP Aspect 切面

### 27、什么是切点（JoinPoint）

### 28、SpringBoot 如何实现打包

### 29、如何使用 SpringBoot 实现分页和排序？

### 30、保护 SpringBoot 应用有哪些方法？

### 31、什么是 Netflix Feign？它的优点是什么？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
