# Spring 最新面试题及答案整理，汇总版

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是 Spring 配置文件？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#1什么是-spring-配置文件)

Spring 配置文件是 XML 文件。 该文件主要包含类信息。 它描述了这些类是如何配置以及相互引入的。 但是，XML 配置文件冗长且更加干净。 如果没有正确规划和编写，那么在大项目中管理变得非常困难。

### [2、保护 SpringBoot 应用有哪些方法？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#2保护-springboot-应用有哪些方法)

**1、** 在生产中使用 HTTPS

**2、** 使用 Snyk 检查你的依赖关系

**3、** 升级到最新版本

**4、** 启用 CSRF 保护

**5、** 使用内容安全策略防止 XSS 攻击

### [3、@RestController 和@Controller 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#3@restcontroller和@controller的区别)

共同点：① 都是加在类级别上的 ② 都可以处理 http 请求

区 别：@RestController 是@Controller 和@ResponseBody 的结合体

### [4、如何启用/禁用执行器？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#4如何启用/禁用执行器)

启用/禁用致动器很容易；最简单的方法是使特性能够将依赖项(Maven/Gradle)添加到 spring-boot-starter-actuator，即启动器。如果不想启用致动器，那么就不要添加依赖项。

Maven 依赖项：

```
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
</dependencies>
```

### [5、@LoadBalanced 注解的作用](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#5@loadbalanced注解的作用)

开启客户端负载均衡。

### [6、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#6springboot-的核心配置文件有哪几个它们的区别是什么)

**1、** SpringBoot 的核心配置文件是 application 和 bootstrap 配置文件。

**2、** application 配置文件这个容易了解，主要用于 SpringBoot 项目的自动化配置。

**3、** bootstrap 配置文件有以下几个应用场景。

**4、** 使用 Spring Cloud Config 配置中心时，这时需要在 bootstrap 配置文件中增加连接到配置中心的配置属性来加载外部配置中心的配置信息；

**5、** 少量固定的不能被覆盖的属性；

**6、** 少量加密/解密的场景；

### [7、spring boot 核心的两个配置文件：](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#7spring-boot-核心的两个配置文件：)

**1、** bootstrap (.yml 或.properties)：boostrap 由父 ApplicationContext 加载的，比 applicaton 优先加载，配置在应用程序上下文的引导阶段生效。一般来说我们在 Spring Cloud Config 或者 Nacos 中会用到它。且 boostrap 里面的属性不能被覆盖；

**2、** application (. yml 或者 . properties)：由 ApplicatonContext 加载，用于 spring boot 项目的自动化配置。

### [8、为什么需要域驱动设计（DDD）？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#8为什么需要域驱动设计ddd)

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_11.png#alt=img%5C_11.png)

图 9：我们需要 DDD 的因素 – 微服务面试问题

### [9、解释对象/关系映射集成模块。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#9解释对象/关系映射集成模块。)

Spring 通过提供 ORM 模块，支持我们在直接 JDBC 之上使用一个对象/关系映射映射(ORM)工具，Spring 支持集成主流的 ORM 框架，如 Hiberate,JDO 和 iBATIS SQL Maps。Spring 的事务管理同样支持以上所有 ORM 框架及 JDBC。

### [10、如何在 SpringBoot 中禁用 Actuator 端点安全性?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案整理，汇总版.md#10如何在-springboot中禁用-actuator端点安全性)

默认情况下，所有敏感的 HTTP 端点都是安全的，只有具有 `http ACTUATOR`角色的用户才能访问它们。安全性是使用标准的 `httpservletrequest. isuserinrole..isusernrole`方法实施的。可以使用 `management. security. enabled= false`来禁用安全性。只有在执行机构端点在防火墙后访问时，才建议禁用安全性。

### 11、什么是有界上下文？

### 12、什么是 spring?

### 13、您使用了哪些 starter maven 依赖项？

### 14、Spring Cloud Security

### 15、SpringBoot 的配置文件有哪几种格式？区别是什么？

### 16、spring 中有多少种 IOC 容器？

### 17、什么是 Spring Cloud Zuul（服务网关）

### 18、SpringBoot 中的监视器是什么？

### 19、PACT 在微服务架构中的用途是什么？

### 20、什么是 Spring 引导的执行器？

### 21、什么是 Spring IOC 容器？

### 22、SpringBoot 中的监视器是什么?

### 23、Spring Framework 中有多少个模块，它们分别是什么？

### 24、@SpringBootApplication 注释在内部有什么用处?

### 25、SpringBoot 多数据源事务如何管理

### 26、spring bean 容器的生命周期是什么样的？

### 27、什么是 Spring IOC 容器？

### 28、Actuator 在 SpringBoot 中的作用

### 29、什么是凝聚力？

### 30、如何在 SpringBoot 中禁用 Actuator 端点安全性？

### 31、SpringBoot 事物的使用

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
