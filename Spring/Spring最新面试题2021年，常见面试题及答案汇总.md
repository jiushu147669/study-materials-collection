# Spring 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、Spring Cloud 是什么](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#1spring-cloud-是什么)

**1、** Spring Cloud 是一系列框架的有序集合。它利用 SpringBoot 的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、智能路由、消息总线、负载均衡、断路器、数据监控等，都可以用 SpringBoot 的开发风格做到一键启动和部署。

**2、** Spring Cloud 并没有重复制造轮子，它只是将各家公司开发的比较成熟、经得起实际考验的服务框架组合起来，通过 SpringBoot 风格进行再封装屏蔽掉了复杂的配置和实现原理，最终给开发者留出了一套简单易懂、易部署和易维护的分布式系统开发工具包。

### [2、微服务限流 http 限流：我们使⽤ nginx 的 limitzone 来完成：](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#2微服务限流-http限流：我们使⽤nginx的limitzone来完成：)

```
//这个表示使⽤ip进⾏限流 zone名称为req_one 分配了10m 空间使⽤漏桶算法 每秒钟允许1个请求
limit_req_zone $binary_remote_addr zone=req_one:10m rate=1r/s; //这边burst表示可以瞬间超过20个请求 由于没有noDelay参数因此需要排队 如果超过这20个那么直接返回503
limit_req zone=req_three burst=20;
```

### [3、微服务架构如何运作？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#3微服务架构如何运作)

微服务架构具有以下组件：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_5.png#alt=img%5C_5.png)

图 5：微服务 架构 – 微服务面试问题

客户端 – 来自不同设备的不同用户发送请求。

身份提供商 – 验证用户或客户身份并颁发安全令牌。

API 网关 – 处理客户端请求。

静态内容 – 容纳系统的所有内容。

管理 – 在节点上平衡服务并识别故障。

服务发现 – 查找微服务之间通信路径的指南。

内容交付网络 – 代理服务器及其数据中心的分布式网络。

远程服务 – 启用驻留在 IT 设备网络上的远程访问信息。

### [4、REST 和 RPC 对比](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#4rest-和rpc对比)

**1、** RPC 主要的缺陷是服务提供方和调用方式之间的依赖太强，需要对每一个微服务进行接口的定义，并通过持续继承发布，严格版本控制才不会出现冲突。

**2、** REST 是轻量级的接口，服务的提供和调用不存在代码之间的耦合，只需要一个约定进行规范。

### [5、解释基于 XML Schema 方式的切面实现。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#5解释基于xml-schema方式的切面实现。)

在这种情况下，切面由常规类以及基于 XML 的配置实现。

### [6、区分构造函数注入和 setter 注入。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#6区分构造函数注入和-setter-注入。)

| 构造函数注入               | setter 注入                |
| -------------------------- | -------------------------- |
| 没有部分注入               | 有部分注入                 |
| 不会覆盖 setter 属性       | 会覆盖 setter 属性         |
| 任意修改都会创建一个新实例 | 任意修改不会创建一个新实例 |
| 适用于设置很多属性         | 适用于设置少量属性         |

### [7、SpringBoot 实现热部署有哪几种方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#7springboot-实现热部署有哪几种方式)

主要有两种方式：

**1、** Spring Loaded

**2、** Spring-boot-devtools

### [8、什么是代理?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#8什么是代理)

代理是通知目标对象后创建的对象。从客户端的角度看，代理对象和目标对象是一样的。

### [9、SpringBoot 支持什么前端模板，](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#9springboot支持什么前端模板)

thymeleaf，freemarker，jsp，官方不推荐 JSP 会有限制

### [10、什么是客户证书？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题2021年，常见面试题及答案汇总.md#10什么是客户证书)

客户端系统用于向远程服务器发出经过身份验证的请求的一种数字证书称为客户端证书。客户端证书在许多相互认证设计中起着非常重要的作用，为请求者的身份提供了强有力的保证。

### 11、什么是断路器

### 12、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？

### 13、SpringBoot 和 SpringCloud 的区别？

### 14、Spring 、SpringBoot 和 Spring Cloud 的关系?

### 15、Eureka 怎么实现高可用

### 16、解释不同方式的自动装配 。

### 17、什么是 Spring MVC 框架的控制器？

### 18、什么是 Spring Cloud？

### 19、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？

### 20、你更倾向用那种事务管理类型？

### 21、我们如何进行跨功能测试？

### 22、接⼝限流⽅法？

### 23、负载均衡的意义是什么?

### 24、在 Spring Initializer 中，如何改变一个项目的包名字？

### 25、[@Qualifier ](/Qualifier) 注解有什么用？

### 26、spring 支持集中 bean scope？

### 27、eureka 的缺点：

### 28、核心容器（应用上下文) 模块。

### 29、Spring Cloud OpenFeign

### 30、什么是 Spring 配置文件？

### 31、SpringBoot 打成的 jar 和普通的 jar 有什么区别 ?

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
