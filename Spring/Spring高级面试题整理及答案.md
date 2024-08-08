# Spring 高级面试题整理及答案

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、如何给静态变量赋值？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#1如何给静态变量赋值)

SpringBoot 无法通过@Value 给静态变量赋值

此时需要给当前类加@Component 注解，通过 set 方法设置@Value 注解加载 set 方法上，set 方法的参数可以任意命名，不能同属性名，此后当前工具类下的静态方法可直接使用属性值。

### [2、如何重新加载 SpringBoot 上的更改，而无需重新启动服务器？SpringBoot 项目如何热部署？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#2如何重新加载-springboot-上的更改而无需重新启动服务器springboot项目如何热部署)

这可以使用 DEV 工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式 tomcat 将重新启动。SpringBoot 有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java 开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。开发人员可以重新加载 SpringBoot 上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。SpringBoot 在发布它的第一个版本时没有这个功能。这是开发人员最需要的功能。DevTools 模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供 H2 数据库控制台以更好地测试应用程序。

```
<dependency>
  <groupId>org、springframework、boot</groupId>
  <artifactId>spring-boot-devtools</artifactId>
</dependency>
```

### [3、spring bean 容器的生命周期是什么样的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#3spring-bean-容器的生命周期是什么样的)

**1、** spring bean 容器的生命周期流程如下：

**2、** Spring 容器根据配置中的 bean 定义中实例化 bean。

**3、** Spring 使用依赖注入填充所有属性，如 bean 中所定义的配置。

**4、** 如果 bean 实现 BeanNameAware 接口，则工厂通过传递 bean 的 ID 来调用 setBeanName()。

**5、** 如果 bean 实现 BeanFactoryAware 接口，工厂通过传递自身的实例来调用 setBeanFactory()。

**6、** 如果存在与 bean 关联的任何 BeanPostProcessors，则调用 preProcessBeforeInitialization() 方法。

**7、** 如果为 bean 指定了 init 方法（ 的 init-method 属性），那么将调用它。

**8、** 最后，如果存在与 bean 关联的任何 BeanPostProcessors，则将调用 postProcessAfterInitialization() 方法。

**9、** 如果 bean 实现 DisposableBean 接口，当 spring 容器关闭时，会调用 destory()。

**10、** 如果为 bean 指定了 destroy 方法（ 的 destroy-method 属性），那么将调用它。

###什么是 spring 的内部 bean？

只有将 bean 用作另一个 bean 的属性时，才能将 bean 声明为内部 bean。 为了定义 bean，Spring 的基于 XML 的配置元数据在 或 中提供了 元素的使用。 内部 bean 总是匿名的，它们总是作为原型。

###什么是 spring 装配

当 bean 在 Spring 容器中组合在一起时，它被称为装配或 bean 装配。

Spring 容器需要知道需要什么 bean 以及容器应该如何使用依赖注入来将 bean 绑定在一起，同时装配 bean。

###自动装配有哪些方式？

Spring 容器能够自动装配 bean。 也就是说，可以通过检查 BeanFactory 的内容让 Spring 自动解析 bean 的协作者。

**自动装配的不同模式：**

**1、** no - 这是默认设置，表示没有自动装配。 应使用显式 bean 引用进行装配。

**2、** byName - 它根据 bean 的名称注入对象依赖项。 它匹配并装配其属性与 XML 文件中由相同名称定义的 bean。

**3、** byType - 它根据类型注入对象依赖项。 如果属性的类型与 XML 文件中的一个 bean 名称匹配，则匹配并装配属性。

**4、** 构造函数 - 它通过调用类的构造函数来注入依赖项。 它有大量的参数。

**5、** autodetect - 首先容器尝试通过构造函数使用 autowire 装配，如果不能，则尝试通过 byType 自动装配。

### [4、SpringCloud 限流：](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#4springcloud限流：)

**1、** 我们可以通过 semaphore.maxConcurrentRequests,coreSize,maxQueueSize 和 queueSizeRejectionThreshold 设置信号量模式下的最⼤并发量、线程池⼤⼩、缓冲区⼤⼩和缓冲区降级阈值。

```
#不设置缓冲区，当请求数超过coreSize时直接降级
hystrix.threadpool.userThreadPool.maxQueueSize=-1超时时间⼤于我们的timeout接⼝返回时间
hystrix.command.userCommandKey.execution.isolation.thread.timeoutInMilliseconds=15000
```

这个时候我们连续多次请求/user/command/timeout 接⼝，在第⼀个请求还没有成功返回时，查看输出⽇志可以发现只有第⼀个请求正常的进⼊到 user-service 的接⼝中，其它请求会直接返回降级信息。这样我们就实现了对服务请求的限流。

**2、** 漏桶算法：⽔（请求）先进⼊到漏桶⾥，漏桶以⼀定的速度出⽔，当⽔流⼊速度过⼤会直接溢出，可以看出漏桶算法能强⾏限制数据的传输速率。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_7.png#alt=45%5C_7.png)

**3、** 令牌桶算法：除了要求能够限制数据的平均传输速率外，还要求允许某种程度的突发传输。这时候漏桶算法可能就不合适了，令牌桶算法更为适合。 如图所示，令牌桶算法的原理是系统会以⼀个恒定的速度往桶⾥放⼊令牌，⽽如果请求需要被处理，则需要先从桶⾥获取⼀个令牌，当桶⾥没有令牌可取时，则拒绝服务。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_8.png#alt=45%5C_8.png)

### [5、什么是 Spring Cloud Config?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#5什么是spring-cloud-config)

Spring Cloud Config 为分布式系统中的外部配置提供服务器和客户端支持，可以方便的对微服务各个环境下的配置进行集中式管理。Spring Cloud Config 分为 Config Server 和 Config Client 两部分。Config Server 负责读取配置文件，并且暴露 Http API 接口，Config Client 通过调用 Config Server 的接口来读取配置文件。

### [6、Spring Cloud 解决了哪些问题？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#6spring-cloud解决了哪些问题)

在使用 SpringBoot 开发分布式微服务时，我们面临的问题很少由 Spring Cloud 解决。

与分布式系统相关的复杂性 – 包括网络问题，延迟开销，带宽问题，安全问题。

处理服务发现的能力 – 服务发现允许集群中的进程和服务找到彼此并进行通信。

解决冗余问题 – 冗余问题经常发生在分布式系统中。

负载平衡 – 改进跨多个计算资源（例如计算机集群，网络链接，中央处理单元）的工作负载分布。

减少性能问题 – 减少因各种操作开销导致的性能问题。

### [7、springcloud 核⼼组件及其作⽤，以及 springcloud ⼯作原理：](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#7springcloud核⼼组件及其作⽤以及springcloud⼯作原理：)

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_9.png#alt=45%5C_9.png)

**springcloud 由以下⼏个核⼼组件构成：**

**1、** Eureka：各个服务启动时，Eureka Client 都会将服务注册到 Eureka Server，并且 Eureka Client 还可以反过来从 Eureka Server 拉取注册表，从⽽知道其他服务在哪⾥

**2、** Ribbon：服务间发起请求的时候，基于 Ribbon 做负载均衡，从⼀个服务的多台机器中选择⼀台

**3、** Feign：基于 Feign 的动态代理机制，根据注解和选择的机器，拼接请求 URL 地址，发起请求

**4、** Hystrix：发起请求是通过 Hystrix 的线程池来⾛的，不同的服务⾛不同的线程池，实现了不同服务调⽤的隔离，避免了服务雪崩的问题

**5、** Zuul：如果前端、移动端要调⽤后端系统，统⼀从 Zuul ⽹关进⼊，由 Zuul ⽹关转发请求给对应的服务

### [8、什么是依赖注入？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#8什么是依赖注入)

在依赖注入中，您不必创建对象，但必须描述如何创建它们。您不是直接在代码中将组件和服务连接在一起，而是描述配置文件中哪些组件需要哪些服务。由 IoC 容器将它们装配在一起。

### [9、你能否举一个以 ReadOnly 为事务管理的例子？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#9你能否举一个以-readonly-为事务管理的例子)

当你从数据库读取内容的时候，你想把事物中的用户描述或者是其它描述设置为只读模式，以便于 Hebernate 不需要再次检查实体的变化。这是非常高效的。

### [10、什么是 SpringBoot？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题整理及答案.md#10什么是springboot)

Spring boot 是微服务面试问题的主要话题。 随着新功能的加入，Spring 变得越来越复杂。无论何时启动新项目，都必须添加新的构建路径或 Maven 依赖项。简而言之，你需要从头开始做每件事。SpringBoot 是一种帮助您避免所有代码配置的解决方案。

### 11、你如何理解 SpringBoot 中的 Starters？

### 12、SpringBoot 的缺点

### 13、什么是 AOP？

### 14、Eureka 和 ZooKeeper 都可以提供服务注册与发现的功能,请说说两个的区别

### 15、一个 Spring 的应用看起来象什么？

### 16、过渡到微服务时的常见错误

### 17、JdbcTemplate

### 18、Ribbon 底层实现原理

### 19、SpringBoot 日志框架：

### 20、SpringBoot 有哪几种读取配置的方式？

### 21、微服务限流 dubbo 限流：dubbo 提供了多个和请求相关的 filter：ActiveLimitFilter ExecuteLimitFilter TPSLimiterFilter

### 22、SpringCloud 的优缺点

### 23、什么是 Spring Cloud Bus？

### 24、[@RequestMapping ](/RequestMapping) 注解有什么用？

### 25、spring-boot-starter-parent 有什么用 ?

### 26、自动装配有什么局限？

### 27、如何使用 SpringBoot 自动重装我的应用程序？

### 28、什么是 Spring Cloud？

### 29、什么是 Spring Cloud Bus?

### 30、RequestMapping 和 GetMapping 的不同之处在哪里？

### 31、什么是 Spring Profiles？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
