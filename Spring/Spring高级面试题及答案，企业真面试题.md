# Spring 高级面试题及答案，企业真面试题

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、如何在 spring 中启动注解装配？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#1如何在-spring-中启动注解装配)

默认情况下，Spring 容器中未打开注解装配。因此，要使用基于注解装配，我们必须通过配置 `<context：annotation-config/>` 元素在 Spring 配置文件中启用它。

### [2、dubbo 服务注册与发现原理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#2dubbo服务注册与发现原理)

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_5.png#alt=45%5C_5.png)

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_6.png#alt=45%5C_6.png)

调⽤关系说明：

**1、** 服务容器负责启动,加载,运⾏服务提供者。

**2、** 服务提供者在启动时,向注册中⼼注册⾃⼰提供的服务。

**3、** 服务消费者在启动时,向注册中⼼订阅⾃⼰所需的服务。

**4、** 注册中⼼返回服务提供者地址列表给消费者,如果有变更,注册中⼼将基于⻓连接推送变更数据给消费者。

**5、** 服务消费者,从提供者地址列表中,基于软负载均衡算法,选⼀台提供者进⾏调⽤,如果调⽤失败,再选另⼀台调⽤。

**6、** 服务消费者和提供者,在内存中累计调⽤次数和调⽤时间,定时每分钟发送⼀次统计数据到监控中⼼。

### [3、列举 spring 支持的事务管理类型](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#3列举-spring-支持的事务管理类型)

Spring 支持两种类型的事务管理：

**1、** 程序化事务管理：在此过程中，在编程的帮助下管理事务。它为您提供极大的灵活性，但维护起来非常困难。

**2、** 声明式事务管理：在此，事务管理与业务代码分离。仅使用注解或基于 XML 的配置来管理事务。

### [4、如何解决 POST 请求中文乱码问题，GET 的又如何处理呢？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#4如何解决post请求中文乱码问题get的又如何处理呢)

**解决 post 请求乱码问题：**

在 web.xml 中配置一个 CharacterEncodingFilter 过滤器，设置成 utf-8；

```
<filter>
    <filter-name>CharacterEncodingFilter</filter-name>
    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
    <init-param>
        <param-name>encoding</param-name>
        <param-value>utf-8</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>CharacterEncodingFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```

**get 请求中文参数出现乱码解决方法有两个：**

修改 tomcat 配置文件添加编码与工程编码一致，如下：

```
<ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
```

**另外一种方法对参数进行重新编码：**

String userName = new String(request.getParamter(“userName”).getBytes(“ISO8859-1”),“utf-8”)

ISO8859-1 是 tomcat 默认编码，需要将 tomcat 编码后的内容按 utf-8 编码。

### [5、@PathVariable 和@RequestParam 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#5@pathvariable和@requestparam的区别)

请求路径上有个 id 的变量值，可以通过@PathVariable 来获取 [@RequestMapping(value ](/RequestMapping(value) = “/page/{id}”, method = RequestMethod.GET)

@RequestParam 用来获得静态的 URL 请求入参 spring 注解时 action 里用到。

### [6、SpringBoot 多数据源拆分的思路](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#6springboot多数据源拆分的思路)

先在 properties 配置文件中配置两个数据源，创建分包 mapper，使用@ConfigurationProperties 读取 properties 中的配置，使用@MapperScan 注册到对应的 mapper 包中

### [7、分布式配置中心有那些框架？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#7分布式配置中心有那些框架)

Apollo、zookeeper、springcloud config。

### [8、Spring 支持的事务管理类型](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#8spring支持的事务管理类型)

Spring 支持两种类型的事务管理：

**1、** 编程式事务管理：这意味你通过编程的方式管理事务，给你带来极大的灵活性，但是难维护。

**2、** 声明式事务管理：这意味着你可以将业务代码和事务管理分离，你只需用注解和 XML 配置来管理事务。

### [9、为什么我们需要 spring-boot-maven-plugin?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#9为什么我们需要-spring-boot-maven-plugin)

spring-boot-maven-plugin 提供了一些像 jar 一样打包或者运行应用程序的命令。

spring-boot:run 运行你的 SpringBooty 应用程序。

spring-boot：repackage 重新打包你的 jar 包或者是 war 包使其可执行

spring-boot：start 和 spring-boot：stop 管理 SpringBoot 应用程序的生命周期（也可以说是为了集成测试）。

spring-boot:build-info 生成执行器可以使用的构造信息。

### [10、常用网关框架有那些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题及答案，企业真面试题.md#10常用网关框架有那些)

Nginx、Zuul、Gateway

### 11、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？

### 12、架构师在微服务架构中的角色是什么？

### 13、怎么设计无状态服务？

### 14、springcloud 如何实现服务的注册?

### 15、你可以在 Spring 中注入一个 null 和一个空字符串吗？

### 16、什么是 Hystrix？

### 17、你对 SpringBoot 有什么了解？

### 18、Spring Cloud Gateway

### 19、一个 Spring 的应用看起来象什么？

### 20、什么是 Hystrix 断路器？我们需要它吗？

### 21、微服务有什么特点？

### 22、[@RequestMapping ](/RequestMapping) 注解

### 23、微服务有哪些特点？

### 24、什么是 AOP 通知

### 25、什么是服务降级

### 26、在使用微服务架构时，您面临哪些挑战？

### 27、Spring Cloud Netflix(重点，这些组件用的最多)

### 28、Bean 工厂和 Application contexts 有什么区别？

### 29、SpringBoot 需要独立的容器运行吗？

### 30、如何给 Spring 容器提供配置元数据?

### 31、什么是幂等性?它是如何使用的？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
