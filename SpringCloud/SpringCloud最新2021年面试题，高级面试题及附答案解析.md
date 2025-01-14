# SpringCloud 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是有界上下文？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#1什么是有界上下文)

有界上下文是域驱动设计的核心模式。DDD 战略设计部门的重点是处理大型模型和团队。DDD 通过将大型模型划分为不同的有界上下文并明确其相互关系来处理大型模型。

### [2、ZuulFilter 常用有那些方法](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#2zuulfilter常用有那些方法)

**1、** Run()：过滤器的具体业务逻辑

**2、** shouldFilter()：判断过滤器是否有效

**3、** filterOrder()：过滤器执行顺序

**4、** filterType()：过滤器拦截位置

### [3、Spring Cloud Gateway](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#3spring-cloud-gateway)

Spring cloud gateway 是 spring 官方基于 Spring 5.0、SpringBoot2.0 和 Project Reactor 等技术开发的网关，Spring Cloud Gateway 旨在为微服务架构提供简单、有效和统一的 API 路由管理方式，Spring Cloud Gateway 作为 Spring Cloud 生态系统中的网关，目标是替代 Netflix Zuul，其不仅提供统一的路由方式，并且还基于 Filer 链的方式提供了网关基本的功能，例如：安全、监控/埋点、限流等。

### [4、Spring Cloud Netflix](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#4spring-cloud-netflix)

Netflix OSS 开源组件集成，包括 Eureka、Hystrix、Ribbon、Feign、Zuul 等核心组件。

**1、** Eureka：服务治理组件，包括服务端的注册中心和客户端的服务发现机制；

**2、** Ribbon：负载均衡的服务调用组件，具有多种负载均衡调用策略；

**3、** Hystrix：服务容错组件，实现了断路器模式，为依赖服务的出错和延迟提供了容错能力；

**4、** Feign：基于 Ribbon 和 Hystrix 的声明式服务调用组件；

**5、** Zuul：API 网关组件，对请求提供路由及过滤功能。

### [5、负载均衡的意义是什么?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#5负载均衡的意义是什么)

在计算中，负载均衡可以改善跨计算机，计算机集群，网络链接，中央处理单元或磁盘驱动器等多种计算资源的工作负载分布。负载均衡旨在优化资源使用，最大吞吐量，最小响应时间并避免任何单一资源的过载。使用多个组件进行负载均衡而不是单个组件可能会通过冗余来提高可靠性和可用性。负载平衡通常涉及专用软件或硬件，例如多层交换机或域名系统服务进程。

### [6、Spring Cloud OpenFeign](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#6spring-cloud-openfeign)

Feign 是一个声明性的 Web 服务客户端。它使编写 Web 服务客户端变得更容易。要使用 Feign，我们可以将调用的服务方法定义成抽象方法保存在本地添加一点点注解就可以了，不需要自己构建 Http 请求了，直接调用接口就行了，不过要注意，调用方法要和本地抽象方法的签名完全一致。

### [7、什么是耦合？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#7什么是耦合)

组件之间依赖关系强度的度量被认为是耦合。一个好的设计总是被认为具有高内聚力和低耦合性。

### [8、Eureka 和 ZooKeeper 都可以提供服务注册与发现的功能,请说说两个的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#8eureka和zookeeper都可以提供服务注册与发现的功能,请说说两个的区别)

ZooKeeper 保证的是 CP,Eureka 保证的是 AP，ZooKeeper 在选举期间注册服务瘫痪,虽然服务最终会恢复,但是选举期间不可用的。Eureka 各个节点是平等关系,只要有一台 Eureka 就可以保证服务可用,而查询到的数据并不是最新的自我保护机制会导致 Eureka 不再从注册列表移除因长时间没收到心跳而应该过期的服务。Eureka 仍然能够接受新服务的注册和查询请求,但是不会被同步到其他节点(高可用)。当网络稳定时,当前实例新的注册信息会被同步到其他节点中(最终一致性)。Eureka 可以很好的应对因网络故障导致部分节点失去联系的情况,而不会像 ZooKeeper 一样使得整个注册系统瘫痪。

**1、** ZooKeeper 有 Leader 和 Follower 角色,Eureka 各个节点平等

**2、** ZooKeeper 采用过半数存活原则,Eureka 采用自我保护机制解决分区问题

**3、** Eureka 本质上是一个工程,而 ZooKeeper 只是一个进程

### [9、网关的作用是什么](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#9网关的作用是什么)

统一管理微服务请求，权限控制、负载均衡、路由转发、监控、安全控制黑名单和白名单等

### [10、什么是 Eureka](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringCloud/SpringCloud最新2021年面试题，高级面试题及附答案解析.md#10什么是eureka)

Eureka 作为 SpringCloud 的服务注册功能服务器，他是服务注册中心，系统中的其他服务使用 Eureka 的客户端将其连接到 Eureka Service 中，并且保持心跳，这样工作人员可以通过 Eureka Service 来监控各个微服务是否运行正常。

### 11、什么是 Spring Cloud？

### 12、Spring Cloud Sleuth

### 13、您对微服务架构中的语义监控有何了解？

### 14、微服务的缺点：

### 15、我们如何在测试中消除非决定论？

### 16、谈谈服务降级、熔断、服务隔离

### 17、Spring Cloud 实现服务注册和发现的原理是什么？

### 18、Spring Cloud 和 dubbo 区别?

### 19、SpringBoot 支持哪些嵌入式容器？

### 20、您对微服务有何了解？

### 21、Spring Cloud 的版本关系

### 22、Spring Cloud Gateway

### 23、Spring Cloud Task

### 24、Spring Cloud Zookeeper

### 25、Spring Cloud Zookeeper

### 26、eureka 和 zookeeper 都可以提供服务注册与发现的功能，请说说两个的区别？

### 27、服务注册和发现是什么意思？Spring Cloud 如何实现？

### 28、Spring Cloud Consul

### 29、Actuator 在 SpringBoot 中的作用

### 30、22。你能否给出关于休息和微服务的要点？

### 31、什么是 Hystrix？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
