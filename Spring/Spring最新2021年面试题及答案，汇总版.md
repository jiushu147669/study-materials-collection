# Spring 最新 2023 年面试题及答案，汇总版

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是不同类型的微服务测试？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#1什么是不同类型的微服务测试)

在使用微服务时，由于有多个微服务协同工作，测试变得非常复杂。因此，测试分为不同的级别。

在底层，我们有面向技术的测试，如单元测试和性能测试。这些是完全自动化的。

在中间层面，我们进行了诸如压力测试和可用性测试之类的探索性测试。

在顶层， 我们的 验收测试数量很少。这些验收测试有助于利益相关者理解和验证软件功能。

### [2、Nginx 与 Ribbon 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#2nginx与ribbon的区别)

Nginx 是反向代理同时可以实现负载均衡，nginx 拦截客户端请求采用负载均衡策略根据 upstream 配置进行转发，相当于请求通过 nginx 服务器进行转发。Ribbon 是客户端负载均衡，从注册中心读取目标服务器信息，然后客户端采用轮询策略对服务直接访问，全程在客户端操作。

### [3、什么是 Hystrix 断路器？我们需要它吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#3什么是-hystrix-断路器我们需要它吗)

由于某些原因，employee-consumer 公开服务会引发异常。在这种情况下使用 Hystrix 我们定义了一个回退方法。如果在公开服务中发生异常，则回退方法返回一些默认值

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_13.png#alt=45%5C_13.png)

中断，并且员工使用者将一起跳过 firtsPage 方法，并直接调用回退方法。 断路器的目的是给第一页方法或第一页方法可能调用的其他方法留出时间，并导致异常恢复。可能发生的情况是，在负载较小的情况下，导致异常的问题有更好的恢复机会 。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_14.png#alt=45%5C_14.png)

### [4、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#4springboot-的核心注解是哪个它主要由哪几个注解组成的)

启动类上面的注解是@SpringBootApplication，它也是 SpringBoot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 [@Configuration ](/Configuration) 注解，实现配置文件的功能。

[@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：@SpringBootApplication(exclude ](/EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：@SpringBootApplication(exclude) = { DataSourceAutoConfiguration.class })。

@ComponentScan：Spring 组件扫描。

### [5、什么是 AOP 什么是目标对象?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#5什么是-aop什么是目标对象)

被一个或者多个切面所通知的对象。它通常是一个代理对象。也指被通知（advised）对象。

### [6、如何重新加载 SpringBoot 上的更改，而无需重新启动服务器？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#6如何重新加载springboot上的更改而无需重新启动服务器)

这可以使用 DEV 工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式 tomcat 将重新启动。

SpringBoot 有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java 开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。

开发人员可以重新加载 SpringBoot 上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。SpringBoot 在发布它的第一个版本时没有这个功能。

这是开发人员最需要的功能。DevTools 模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供 H2 数据库控制台以更好地测试应用程序。

### [7、如何在自定义端口上运行 SpringBoot 应用程序?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#7如何在自定义端口上运行-springboot应用程序)

在 `application.properties`中指定端口`serverport=8090`。

### [8、SpringBoot 有哪些优点？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#8springboot-有哪些优点)

**SpringBoot 主要有如下优点：**

**1、** 容易上手，提升开发效率，为 Spring 开发提供一个更快、更简单的开发框架。

**2、** 开箱即用，远离繁琐的配置。

**3、** 提供了一系列大型项目通用的非业务性功能，例如：内嵌服务器、安全管理、运行数据监控、运行状况检查和外部化配置等。

**4、** SpringBoot 总结就是使编码变简单、配置变简单、部署变简单、监控变简单等等

### [9、SpringBoot 常用的 starter 有哪些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#9springboot常用的starter有哪些)

**1、** spring-boot-starter-web 嵌入 tomcat 和 web 开发需要 servlet 与 jsp 支持

**2、** spring-boot-starter-data-jpa 数据库支持

**3、** spring-boot-starter-data-Redis Redis 数据库支持

**4、** spring-boot-starter-data-solr solr 支持

**5、** mybatis-spring-boot-starter 第三方的 mybatis 集成 starter

### [10、如何实现 SpringBoot 应用程序的安全性？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题及答案，汇总版.md#10如何实现-springboot-应用程序的安全性)

为了实现 SpringBoot 的安全性，我们使用 spring-boot-starter-security 依赖项，并且必须添加安全配置。它只需要很少的代码。配置类将必须扩展 WebSecurityConfigurerAdapter 并覆盖其方法。

### 11、什么是 Spring Actuator？它有什么优势？

### 12、SpringData 项目所支持的关系数据存储技术：

### 13、什么是 SpringBoot ？

### 14、Spring 框架的事务管理有哪些优点？

### 15、什么是 AOP 代理?

### 16、Async 异步调用方法

### 17、使用 Spring 框架的好处是什么？

### 18、解释 JDBC 抽象和 DAO 模块。

### 19、SpringBoot、Spring MVC 和 Spring 有什么区别？

### 20、@ResponseBody 注解的作用

### 21、什么是微服务

### 22、ZuulFilter 常用有那些方法

### 23、可以通过多少种方式完成依赖注入？

### 24、链路跟踪 Sleuth

### 25、SpringBoot 最大的优势是什么呢？

### 26、在 Spring AOP 中，关注点和横切关注的区别是什么？

### 27、开启 SpringBoot 特性有哪几种方式？（创建 SpringBoot 项目的两种方式）

### 28、[@Required ](/Required) 注解有什么用？

### 29、什么是 Spring 的 MVC 框架？

### 30、运行 SpringBoot 有哪几种方式？

### 31、如何实现动态 Zuul 网关路由转发

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
