# SpringCloud 最新 2023 年面试题及答案，汇总版

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、Spring Cloud 和各子项目版本对应关系](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#1spring-cloud和各子项目版本对应关系)

**1、** Edgware.SR6：我理解为最低版本号

**2、** Greenwich.SR2 :我理解为最高版本号

**3、** Greenwich.BUILD-SNAPSHOT（快照）：是一种特殊的版本，指定了某个当前的开发进度的副本。不同于常规的版本，几乎每天都要提交更新的版本，如果每次提交都申明一个版本号那不是版本号都不够用？

| Component                 | Edgware.SR6    | Greenwich.SR2        | Greenwich.BUILD-SNAPSHOT |
| ------------------------- | -------------- | -------------------- | ------------------------ |
| spring-cloud-aws          | 1.2.4.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-bus          | 1.3.4.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-cli          | 1.4.1.RELEASE  | 2.0.0.RELEASE        | 2.0.1.BUILD-SNAPSHOT     |
| spring-cloud-commons      | 1.3.6.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-contract     | 1.2.7.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-config       | 1.4.7.RELEASE  | 2.1.3.RELEASE        | 2.1.4.BUILD-SNAPSHOT     |
| spring-cloud-netflix      | 1.4.7.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-security     | 1.2.4.RELEASE  | 2.1.3.RELEASE        | 2.1.4.BUILD-SNAPSHOT     |
| spring-cloud-cloudfoundry | 1.1.3.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-consul       | 1.3.6.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-sleuth       | 1.3.6.RELEASE  | 2.1.1.RELEASE        | 2.1.2.BUILD-SNAPSHOT     |
| spring-cloud-stream       | Ditmars.SR5    | Fishtown.SR3         | Fishtown.BUILD-SNAPSHOT  |
| spring-cloud-zookeeper    | 1.2.3.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-boot               | 1.5.21.RELEASE | 2.1.5.RELEASE        | 2.1.8.BUILD-SNAPSHOT     |
| spring-cloud-task         | 1.2.4.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-vault        | 1.1.3.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-gateway      | 1.0.3.RELEASE  | 2.1.2.RELEASE        | 2.1.3.BUILD-SNAPSHOT     |
| spring-cloud-openfeign    | 2.1.2.RELEASE  | 2.1.3.BUILD-SNAPSHOT |                          |
| spring-cloud-function     | 1.0.2.RELEASE  | 2.0.2.RELEASE        | 2.0.3.BUILD-SNAPSHOT     |

### [2、什么是客户证书？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#2什么是客户证书)

客户端系统用于向远程服务器发出经过身份验证的请求的一种数字证书称为客户端证书。客户端证书在许多相互认证设计中起着非常重要的作用，为请求者的身份提供了强有力的保证。

### [3、Spring Cloud OpenFeign](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#3spring-cloud-openfeign)

基于 Ribbon 和 Hystrix 的声明式服务调用组件，可以动态创建基于 Spring MVC 注解的接口实现用于服务调用，在 Spring Cloud 2.0 中已经取代 Feign 成为了一等公民。

Spring Cloud 的版本关系

Spring Cloud 是一个由许多子项目组成的综合项目，各子项目有不同的发布节奏。为了管理 Spring Cloud 与各子项目的版本依赖关系，发布了一个清单，其中包括了某个 Spring Cloud 版本对应的子项目版本。

为了避免 Spring Cloud 版本号与子项目版本号混淆，Spring Cloud 版本采用了名称而非版本号的命名，这些版本的名字采用了伦敦地铁站的名字，根据字母表的顺序来对应版本时间顺序，例如 Angel 是第一个版本，Brixton 是第二个版本。

当 Spring Cloud 的发布内容积累到临界点或者一个重大 BUG 被解决后，会发布一个"service releases"版本，简称 SRX 版本，比如 Greenwich.SR2 就是 Spring Cloud 发布的 Greenwich 版本的第 2 个 SRX 版本。目前 Spring Cloud 的最新版本是 Hoxton。

### [4、在使用微服务架构时，您面临哪些挑战？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#4在使用微服务架构时您面临哪些挑战)

开发一些较小的微服务听起来很容易，但开发它们时经常遇到的挑战如下。

自动化组件：难以自动化，因为有许多较小的组件。因此，对于每个组件，我们必须遵循 Build，Deploy 和 Monitor 的各个阶段。

易感性：将大量组件维护在一起变得难以部署，维护，监控和识别问题。它需要在所有组件周围具有很好的感知能力。

配置管理：有时在各种环境中维护组件的配置变得困难。

调试：很难找到错误的每一项服务。维护集中式日志记录和仪表板以调试问题至关重要。

### [5、springcloud 核⼼组件及其作⽤，以及 springcloud ⼯作原理：](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#5springcloud核⼼组件及其作⽤以及springcloud⼯作原理：)

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_9.png#alt=45%5C_9.png)

**springcloud 由以下⼏个核⼼组件构成：**

**1、** Eureka：各个服务启动时，Eureka Client 都会将服务注册到 Eureka Server，并且 Eureka Client 还可以反过来从 Eureka Server 拉取注册表，从⽽知道其他服务在哪⾥

**2、** Ribbon：服务间发起请求的时候，基于 Ribbon 做负载均衡，从⼀个服务的多台机器中选择⼀台

**3、** Feign：基于 Feign 的动态代理机制，根据注解和选择的机器，拼接请求 URL 地址，发起请求

**4、** Hystrix：发起请求是通过 Hystrix 的线程池来⾛的，不同的服务⾛不同的线程池，实现了不同服务调⽤的隔离，避免了服务雪崩的问题

**5、** Zuul：如果前端、移动端要调⽤后端系统，统⼀从 Zuul ⽹关进⼊，由 Zuul ⽹关转发请求给对应的服务

### [6、接⼝限流⽅法？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#6接⼝限流⽅法)

**限制 总并发数（⽐如 数据库连接池、线程池）**

**1、** 限制 瞬时并发数（如 nginx 的 limit_conn 模块，⽤来限制 瞬时并发连接数）

**2、** 限制 时间窗⼝内的平均速率（如 Guava 的 RateLimiter、nginx 的 limit_req 模块，限制每秒的平均速率）

**3、** 限制 远程接⼝ 调⽤速率

**4、** 限制 MQ 的消费速率

**5、** 可以根据⽹络连接数、⽹络流量、CPU 或内存负载等来限流

### [7、Spring Cloud Task](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#7spring-cloud-task)

Spring Cloud Task 的目标是为 SpringBoot 应用程序提供创建短运行期微服务的功能。在 Spring Cloud Task 中，我们可以灵活地动态运行任何任务，按需分配资源并在任务完成后检索结果。Tasks 是 Spring Cloud Data Flow 中的一个基础项目，允许用户将几乎任何 SpringBoot 应用程序作为一个短期任务执行。

### [8、什么是 Oauth？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#8什么是oauth)

开放授权协议，这允许通过在 HTTP 服务上启用客户端应用程序（例如第三方提供商 Facebook，GitHub 等）来访问资源所有者的资源。因此，您可以在不使用其凭据的情况下与另一个站点共享存储在一个站点上的资源。

OAuth 允许像 Facebook 这样的第三方使用最终用户的帐户信息，同时保证其安全（不使用或暴露用户的密码）。它更像是代表用户的中介，同时为服务器提供访问所需信息的令牌。

### [9、为什么在微服务中需要 Reports 报告和 Dashboards 仪表板？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#9为什么在微服务中需要reports报告和dashboards仪表板)

报告和仪表板主要用于监视和维护微服务。有多种工具可以帮助实现此目的。报告 和仪表板可用于： 找出哪些微服务公开了哪些资源。 找出组件发生变化时受影响的服务。 提供一个简单的点，只要需要文档，就可以访问它。 部署的组件的版本。

### [10、什么是微服务架构中的 DRY？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题及答案，汇总版.md#10什么是微服务架构中的dry)

DRY 代表不要重复自己。它基本上促进了重用代码的概念。这导致开发和共享库，这反过来导致紧密耦合。

### 11、服务雪崩？

### 12、什么是 Idempotence 以及它在哪里使用？

### 13、什么是服务熔断

### 14、SpringBoot 和 SpringCloud 的区别？

### 15、谈一下领域驱动设计

### 16、什么是 Feign？

### 17、什么是 Spring Cloud Bus？我们需要它吗？

### 18、什么是凝聚力？

### 19、eureka 和 zookeeper 都可以提供服务注册与发现的功能，请说说两个的区别？

### 20、Spring Cloud Bus

### 21、什么是 Spring Cloud Gateway?

### 22、SpringCloud 有几种调用接口方式

### 23、为什么要使用 Spring Cloud 熔断器？

### 24、Spring Cloud Config

### 25、什么是微服务中的反应性扩展？

### 26、列举微服务技术栈

### 27、什么是 Netflix Feign？它的优点是什么？

### 28、您对 Distributed Transaction 有何了解？

### 29、微服务架构的优缺点是什么？

### 30、访问 RESTful 微服务的方法是什么？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
