# Spring 高级面试题合集，附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、既然 Nginx 可以实现网关？为什么还需要使用 Zuul 框架](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#1既然nginx可以实现网关为什么还需要使用zuul框架)

Zuul 是 SpringCloud 集成的网关，使用 Java 语言编写，可以对 SpringCloud 架构提供更灵活的服务。

### [2、JPA 和 Hibernate 有哪些区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#2jpa-和-hibernate-有哪些区别)

简而言之

JPA 是一个规范或者接口

Hibernate 是 JPA 的一个实现

当我们使用 JPA 的时候，我们使用 javax.persistence 包中的注释和接口时，不需要使用 hibernate 的导入包。

我们建议使用 JPA 注释，因为哦我们没有将其绑定到 Hibernate 作为实现。后来（我知道 - 小于百分之一的几率），我们可以使用另一种 JPA 实现。

### [3、什么是持续监测？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#3什么是持续监测)

持续监控深入监控覆盖范围，从浏览器内前端性能指标，到应用程序性能，再到主机虚拟化基础架构指标。

### [4、Spring 应用程序有哪些不同组件？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#4spring-应用程序有哪些不同组件)

**Spring 应用一般有以下组件：**

**1、** 接口 - 定义功能。

**2、** Bean 类 - 它包含属性，setter 和 getter 方法，函数等。

**3、** Spring 面向切面编程（AOP） - 提供面向切面编程的功能。

**4、** Bean 配置文件 - 包含类的信息以及如何配置它们。

**5、** 用户程序 - 它使用接口。

### [5、服务注册和发现是什么意思？Spring Cloud 如何实现？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#5服务注册和发现是什么意思spring-cloud如何实现)

当我们开始一个项目时，我们通常在属性文件中进行所有的配置。随着越来越多的服务开发和部署，添加和修改这些属性变得更加复杂。有些服务可能会下降，而某些位置可能会发生变化。手动更改属性可能会产生问题。Eureka 服务注册和发现可以在这种情况下提供帮助。由于所有服务都在 Eureka 服务器上注册并通过调用 Eureka 服务器完成查找，因此无需处理服务地点的任何更改和处理。

### [6、项目中前后端分离部署，所以需要解决跨域的问题。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#6项目中前后端分离部署所以需要解决跨域的问题。)

我们使用 cookie 存放用户登录的信息，在 spring 拦截器进行权限控制，当权限不符合时，直接返回给用户固定的 json 结果。

当用户登录以后，正常使用；当用户退出登录状态时或者 token 过期时，由于拦截器和跨域的顺序有问题，出现了跨域的现象。

我们知道一个 http 请求，先走 filter，到达 servlet 后才进行拦截器的处理，如果我们把 cors 放在 filter 里，就可以优先于权限拦截器执行。

```
@Configuration
public class CorsConfig {

    @Bean
    public CorsFilter corsFilter() {
        CorsConfiguration corsConfiguration = new CorsConfiguration();
        corsConfiguration.addAllowedOrigin("*");
        corsConfiguration.addAllowedHeader("*");
        corsConfiguration.addAllowedMethod("*");
        corsConfiguration.setAllowCredentials(true);
        UrlBasedCorsConfigurationSource urlBasedCorsConfigurationSource = new UrlBasedCorsConfigurationSource();
        urlBasedCorsConfigurationSource.registerCorsConfiguration("/**", corsConfiguration);
        return new CorsFilter(urlBasedCorsConfigurationSource);
    }

}
```

### [7、Spring Cloud Stream](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#7spring-cloud-stream)

轻量级事件驱动微服务框架，可以使用简单的声明式模型来发送及接收消息，主要实现为 Apache Kafka 及 RabbitMQ。

### [8、如何设置服务发现？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#8如何设置服务发现)

有多种方法可以设置服务发现。我将选择我认为效率最高的那个，Netflix 的 Eureka。这是一个简单的程序，不会对应用程序造成太大影响。此外，它支持多种类型的 Web 应用程序。 Eureka 配置包括两个步骤 - 客户端配置和服务器配置。

使用属性文件可以轻松完成客户端配置。在 clas spath 中，Eureka 搜索一个 eureka-client.properties 文件。它还搜索由特定于环境的属性文件中的环境引起的覆盖。

对于服务器配置，您必须首先配置客户端。完成后，服务器启动一个客户端，该客户端用于查找其他服务器。。默认情况下，Eureka 服务器使用客户端配置来查找对等服务器。

### [9、path=”users”, collectionResourceRel=”users” 如何与 Spring Data Rest 一起使用？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#9path=users,-collectionresourcerel=users-如何与-spring-data-rest-一起使用)

path- 这个资源要导出的路径段。

collectionResourceRel- 生成指向集合资源的链接时使用的 rel 值。在生成 HATEOAS 链接时使用。

### [10、Spring Cloud 实现服务注册和发现的原理是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring高级面试题合集，附答案解析.md#10spring-cloud-实现服务注册和发现的原理是什么)

**1、** 服务在发布时指定对应的服务名（服务名包括了 IP 地址和端口）将服务注册到注册中心（Eureka 或者 Zookeeper）这一过程是 Spring Cloud 自动实现的，只需要在 main 方法添加 @EnableDisscoveryClient 即可，同一个服务修改端口就可以启动多个实例。

**2、** 调用方法：传递服务名称通过注册中心获取所有的可用实例，通过负载均衡策略调用（Ribbon 和 Feign）对应的服务。

### 11、我们可以用微服务创建状态机吗？

### 12、开启 SpringBoot 特性有哪几种方式？

### 13、Spring MVC 怎么样设定重定向和转发的？

### 14、开启 SpringBoot 特性有哪几种方式？

### 15、Zuul 与 Nginx 有什么区别？

### 16、Spring MVC 用什么对象从后台向前台传递数据的？

### 17、什么是编织（Weaving）？

### 18、各服务之间通信，对 Restful 和 Rpc 这 2 种方式如何做选择？

### 19、什么是 YAML?

### 20、如何使用 SpringBoot 实现分页和排序？

### 21、如何在不使用 BasePACKAGE 过滤器的情况下排除程序包？

### 22、是否可以在 Spring boot 中更改嵌入式 Tomcat 服务器的端口?

### 23、什么是 Feign？

### 24、SpringBoot 是否可以使用 XML 配置 ?

### 25、PACT 如何运作？

### 26、解释 AOP

### 27、Ribbon 和 Feign 的区别？

### 28、如何实现 SpringBoot 应用程序的安全性?

### 29、您对 Distributed Transaction 有何了解？

### 30、什么是 WebSockets？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
