# Spring 最新面试题及答案附答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、SpringBoot 中如何解决跨域问题 ?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#1springboot-中如何解决跨域问题-)

跨域可以在前端通过 JSONP 来解决，但是 JSONP 只可以发送 GET 请求，无法发送其他类型的请求，在 RESTful 风格的应用中，就显得非常鸡肋，因此我们推荐在后端通过 （CORS，Cross-origin resource sharing） 来解决跨域问题。这种解决方案并非 SpringBoot 特有的，在传统的 SSM 框架中，就可以通过 CORS 来解决跨域问题，只不过之前我们是在 XML 文件中配置 CORS ，现在可以通过实现 WebMvcConfigurer 接口然后重写 addCorsMappings 方法解决跨域问题。

[@Configuration ](/Configuration)

public class CorsConfig implements WebMvcConfigurer {

```
@Override
public void addCorsMappings(CorsRegistry registry) {
    registry.addMapping("/**")
            .allowedOrigins("*")
            .allowCredentials(true)
            .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
            .maxAge(3600);
}
```

}

### [2、服务注册和发现是什么意思？Spring Cloud 如何实现？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#2服务注册和发现是什么意思spring-cloud如何实现)

当我们开始一个项目时，我们通常在属性文件中进行所有的配置。随着越来越多的服务开发和部署，添加和修改这些属性变得更加复杂。有些服务可能会下降，而某些位置可能会发生变化。手动更改属性可能会产生问题。 Eureka 服务注册和发现可以在这种情况下提供帮助。由于所有服务都在 Eureka 服务器上注册并通过调用 Eureka 服务器完成查找，因此无需处理服务地点的任何更改和处理。

### [3、如何集成 SpringBoot 和 ActiveMQ？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#3如何集成springboot和activemq)

对于集成 SpringBoot 和 ActiveMQ，我们使用

依赖关系。 它只需要很少的配置，并且不需要样板代码。

### [4、什么是 JavaConfig？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#4什么是javaconfig)

Spring JavaConfig 是 Spring 社区的产品，它提供了配置 Spring IoC 容器的纯 Java 方法。因此它有助于避免使用 XML 配置。使用 JavaConfig 的优点在于：

面向对象的配置。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的@Bean 方法等。

减少或消除 XML 配置。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。

JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。

从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将 JavaConfig 与 XML 混合匹配是理想的。

类型安全和重构友好。JavaConfig 提供了一种类型安全的方法来配置 Spring 容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找

### [5、什么是自动配置？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#5什么是自动配置)

Spring 和 SpringMVC 的问题在于需要配置大量的参数。

我们能否带来更多的智能？当一个 MVC JAR 添加到应用程序中的时候，我们能否自动配置一些 beans？

Spring 查看（CLASSPATH 上可用的框架）已存在的应用程序的配置。在此基础上，SpringBoot 提供了配置应用程序和框架所需要的基本配置。这就是自动配置。

### [6、Container 在微服务中的用途是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#6container在微服务中的用途是什么)

容器是管理基于微服务的应用程序以便单独开发和部署它们的好方法。您可以将微服务封装在容器映像及其依赖项中，然后可以使用它来滚动按需实例的微服务，而无需任何额外的工作。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_18.png#alt=img%5C_18.png)

图 15： 容器的表示及其在微服务中的使用方式 – 微服务访谈问题

### [7、保护 SpringBoot 应用有哪些方法？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#7保护-springboot-应用有哪些方法)

**1、** 在生产中使用 HTTPS

**2、** 使用 Snyk 检查你的依赖关系

**3、** 升级到最新版本

**4、** 启用 CSRF 保护

**5、** 使用内容安全策略防止 XSS 攻击

### [8、什么是 Spring Cloud Bus？我们需要它吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#8什么是spring-cloud-bus我们需要它吗)

考虑以下情况：我们有多个应用程序使用 Spring Cloud Config 读取属性，而 Spring Cloud Config 从 GIT 读取这些属性。

下面的例子中多个员工生产者模块从 Employee Config Module 获取 Eureka 注册的财产。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0814/02/img_6.png#alt=img%5C_6.png)

如果假设 GIT 中的 Eureka 注册属性更改为指向另一台 Eureka 服务器，会发生什么情况。在这种情况下，我们将不得不重新启动服务以获取更新的属性。

还有另一种使用执行器端点/刷新的方式。但是我们将不得不为每个模块单独调用这个 url。例如，如果 Employee Producer1 部署在端口 8080 上，则调用 http：// localhost：8080 / refresh。同样对于 Employee Producer2 http：// localhost：8081 / refresh 等等。这又很麻烦。这就是 Spring Cloud Bus 发挥作用的地方。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0814/02/img_7.png#alt=img%5C_7.png)

Spring Cloud Bus 提供了跨多个实例刷新配置的功能。因此，在上面的示例中，如果我们刷新 Employee Producer1，则会自动刷新所有其他必需的模块。如果我们有多个微服务启动并运行，这特别有用。这是通过将所有微服务连接到单个消息代理来实现的。无论何时刷新实例，此事件都会订阅到侦听此代理的所有微服务，并且它们也会刷新。可以通过使用端点/总线/刷新来实现对任何单个实例的刷新。

### [9、微服务中如何实现 session 共享 ?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#9微服务中如何实现-session-共享-)

在微服务中，一个完整的项目被拆分成多个不相同的独立的服务，各个服务独立部署在不同的服务器上，各自的 session 被从物理空间上隔离开了，但是经常，我们需要在不同微服务之间共享 session ，常见的方案就是 Spring Session + Redis 来实现 session 共享。将所有微服务的 session 统一保存在 Redis 上，当各个微服务对 session 有相关的读写操作时，都去操作 Redis 上的 session 。这样就实现了 session 共享，Spring Session 基于 Spring 中的代理过滤器实现，使得 session 的同步操作对开发人员而言是透明的，非常简便。

### [10、Spring MVC 的异常处理？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring最新面试题及答案附答案汇总.md#10spring-mvc的异常处理)

可以将异常抛给 Spring 框架，由 Spring 框架来处理；我们只需要配置简单的异常处理器，在异常处理器中添视图页面即可。

### 11、什么是 Netflix Feign？它的优点是什么？

### 12、Web，RESTful API 在微服务中的作用是什么？

### 13、双因素身份验证的凭据类型有哪些？

### 14、不同版本的 Spring Framework 有哪些主要功能？

### 15、Spring Framework 有哪些不同的功能？

### 16、什么是 JavaConfig？

### 17、[@RequestMapping ](/RequestMapping) 注解

### 18、使用 Spring 有哪些方式？

### 19、SpringBoot 中的 starter 到底是什么 ?

### 20、Spring Cloud Netflix

### 21、[@Autowired ](/Autowired) 注解有什么用？

### 22、Spring 支持的 ORM

### 23、spring boot 扫描流程?

### 24、什么是 OAuth？

### 25、Spring Cloud Task

### 26、如何重新加载 SpringBoot 上的更改，而无需重新启动服务器？

### 27、如何在 SpringBoot 中添加通用的 JS 代码？

### 28、什么是 Spring IOC 容器？

### 29、Spring 配置文件

### 30、什么是通知（Advice）？

### 31、如何使用 SpringBoot 实现分页和排序？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
