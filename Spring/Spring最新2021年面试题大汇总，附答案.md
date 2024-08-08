# Spring 最新 2023 年面试题大汇总，附答案

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、SpringBoot 运行项目的几种方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#1springboot运行项目的几种方式)

打包用命令或者放到容器中运行

**1、** 打成 jar 包，使用 java -jar xxx.jar 运行

**2、** 打成 war 包，放到 tomcat 里面运行

直接用 maven 插件运行 maven spring-boot：run

直接执行 main 方法运行

### [2、IOC 的优点是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#2ioc的优点是什么)

IOC 或 依赖注入把应用的代码量降到最低。它使应用容易测试，单元测试不再需要单例和 JNDI 查找机制。最小的代价和最小的侵入性使松散耦合得以实现。IOC 容器支持加载服务时的饿汉式初始化和懒加载。

### [3、在 Spring MVC 应用程序中使用 WebMvcTest 注释有什么用处？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#3在spring-mvc应用程序中使用webmvctest注释有什么用处)

WebMvcTest 注释用于单元测试 Spring MVC 应用程序。我们只想启动 ToTestController。执行此单元测试时，不会启动所有其他控制器和映射。

```
@WebMvcTest(value = ToTestController.class, secure = false):
```

### [4、什么是 Spring Cloud？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#4什么是spring-cloud)

根据 Spring Cloud 的官方网站，Spring Cloud 为开发人员提供了快速构建分布式系统中一些常见模式的工具（例如配置管理，服务发现，断路器，智能路由，领导选举，分布式会话，集群状态）。

### [5、eureka 服务注册与发现原理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#5eureka服务注册与发现原理)

**1、** 每 30s 发送⼼跳检测重新进⾏租约，如果客户端不能多次更新租约，它将在 90s 内从服务器注册中⼼移除。

**2、** 注册信息和更新会被复制到其他 Eureka 节点，来⾃任何区域的客户端可以查找到注册中⼼信息，每 30s 发⽣⼀次复制来定位他们的服务，并进⾏远程调⽤。

**3、** 客户端还可以缓存⼀些服务实例信息，所以即使 Eureka 全挂掉，客户端也是可以定位到服务地址的。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_4.png#alt=45%5C_4.png)

### [6、SpringBoot 配置文件的加载顺序](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#6springboot-配置文件的加载顺序)

由 jar 包外向 jar 包内进行寻找;

优先加载带 profile

jar 包外部的 application-{profile}.properties 或 application.yml(带 spring.profile 配置文件

jar 包内部的 application-{profile}.properties 或 application.yml(带 spring.profile 配置文件

再来加载不带 profile

jar 包外部的 application.properties 或 application.yml(不带 spring.profile 配置文件

jar 包内部的 application.properties 或 application.yml(不带 spring.profile 配置文件

### [7、什么是 spring 装配](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#7什么是-spring-装配)

当 bean 在 Spring 容器中组合在一起时，它被称为装配或 bean 装配。Spring 容器需要知道需要什么 bean 以及容器应该如何使用依赖注入来将 bean 绑定在一起，同时装配 bean。

### [8、为什么要用 SpringBoot](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#8为什么要用springboot)

快速开发，快速整合，配置简化、内嵌服务容器

### [9、怎么样把 ModelMap 里面的数据放入 Session 里面？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#9怎么样把modelmap里面的数据放入session里面)

可以在类上面加上@SessionAttributes 注解,里面包含的字符串就是要放入 session 里面的 key。

### [10、什么是微服务架构中的 DRY？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新2021年面试题大汇总，附答案.md#10什么是微服务架构中的dry)

DRY 代表不要重复自己。它基本上促进了重用代码的概念。这导致开发和共享库，这反过来导致紧密耦合。

### 11、使用 Spring Cloud 有什么优势？

### 12、负载平衡的意义什么？

### 13、SpringBoot 中的 starter 到底是什么 ?

### 14、Spring 对 DAO 的支持

### 15、介绍一下 WebApplicationContext

### 16、什么是 Spring Framework？

### 17、为什么要使用 Spring Cloud 熔断器？

### 18、Spring Cloud 的版本关系

### 19、SpringBoot、Spring MVC 和 Spring 有什么区别

### 20、DiscoveryClient 的作用

### 21、什么是嵌入式服务器？我们为什么要使用嵌入式服务器呢?

### 22、什么是 Spring 的内部 bean？

### 23、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？

### 24、网关与过滤器有什么区别

### 25、描述一下 DispatcherServlet 的工作流程

### 26、SpringBoot 集成 mybatis 的过程

### 27、什么是 Aspect 切面

### 28、Spring Cloud Gateway

### 29、Zuul 网关如何搭建集群

### 30、什么是 JavaConfig？

### 31、使用 SpringBoot 启动连接到内存数据库 H2 的 JPA 应用程序需要哪些依赖项？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
