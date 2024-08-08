# SpringBoot 最新 2023 年面试题大汇总，附答案

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、SpringBoot 自动配置的原理是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#1springboot自动配置的原理是什么)

SpringBoot 启动的时候通过@EnableAutoConfiguration 注解找到 META-INF/spring.factories 配置文件中所有的自动配置类，并对其进行加载，而这些自动配置类的类名都是以 AutoConfiguration 结尾来命名的，它实际上就是一个 javaConfig 形式的 Spring 容器配置类，它们都有一个@EnableConfigurationPerperties 的注解，通过这个注解启动 XXXProperties 命名的类去加载全局配置中的属性，如 server.port,而 XXXProperties 通过@ConfigurationProperties 注解将全局配置文件中的属性与自己的属性进行绑定。

### [2、SpringBoot 配置加载顺序?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#2springboot-配置加载顺序)

**1、** properties 文件 2、YAML 文件 3、系统环境变量 4、命令行参数

### [3、spring boot 初始化环境变量流程?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#3spring-boot初始化环境变量流程)

**1、** 调用`prepareEnvironment`方法去设置环境变量

**2、** 接下来有三个方法`getOrCreateEnvironment`，`configureEnvironment`，`environmentPrepared`

**3、** `getOrCreateEnvironment`去初始化系统环境变量

**4、** `configureEnvironment`去初始化命令行参数

**5、** `environmentPrepared`当广播到来的时候调用`onApplicationEnvironmentPreparedEvent`方法去使用`postProcessEnvironment`方法`load yml`和`properties变量`

### [4、运行 SpringBoot 有哪几种方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#4运行-springboot-有哪几种方式)

**1、** 打包用命令或者者放到容器中运行

**2、** 用 Maven/ Gradle 插件运行

**3、** 直接执行 main 方法运行

### [5、SpringBoot 中如何解决跨域问题 ?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#5springboot-中如何解决跨域问题-)

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

### [6、SpringBoot 如何配置 log4j？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#6springboot如何配置log4j)

在引用 log4j 之前，需要先排除项目创建时候带的日志，因为那个是 Logback，然后再引入 log4j 的依赖，引入依赖之后，去 src/main/resources 目录下的 log4j-spring.properties 配置文件，就可以开始对应用的日志进行配置使用。

### [7、SpringBoot 运行项目的几种方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#7springboot运行项目的几种方式)

打包用命令或者放到容器中运行

**1、** 打成 jar 包，使用 java -jar xxx.jar 运行

**2、** 打成 war 包，放到 tomcat 里面运行

直接用 maven 插件运行 maven spring-boot：run

直接执行 main 方法运行

### [8、什么是 JavaConfig？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#8什么是javaconfig)

Spring JavaConfig 是 Spring 社区的产品，它提供了配置 Spring IoC 容器的纯 Java 方法。因此它有助于避免使用 XML 配置。使用 JavaConfig 的优点在于：

面向对象的配置。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的@Bean 方法等。

减少或消除 XML 配置。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。

JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。

从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将 JavaConfig 与 XML 混合匹配是理想的。

类型安全和重构友好。JavaConfig 提供了一种类型安全的方法来配置 Spring 容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找

### [9、运行 SpringBoot 有哪几种方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#9运行-springboot-有哪几种方式)

**1、** 打包用命令或者放到容器中运行

**2、** 用 Maven/ Gradle 插件运行

**3、** 直接执行 main 方法运行

### [10、SpringBoot 常用的 Starter 有哪些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新2021年面试题大汇总，附答案.md#10springboot-常用的-starter-有哪些)

**1、** spring-boot-starter-web ：提供 Spring MVC + 内嵌的 Tomcat 。

**2、** spring-boot-starter-data-jpa ：提供 Spring JPA + Hibernate 。

**3、** spring-boot-starter-data-Redis ：提供 Redis 。

**4、** mybatis-spring-boot-starter ：提供 MyBatis 。

### 11、SpringBoot 与 SpringCloud 区别

### 12、如何集成 SpringBoot 和 ActiveMQ？

### 13、SpringBoot 有哪几种读取配置的方式？

### 14、SpringBoot 2.X 有什么新特性？与 1.X 有什么区别？

### 15、SpringData 项目所支持的关系数据存储技术：

### 16、如何在自定义端口上运行 SpringBoot 应用程序？

### 17、SpringBoot 默认支持的日志框架有哪些？可以进行哪些设置？

### 18、Spring Initializr 是创建 SpringBoot Projects 的唯一方法吗？

### 19、Async 异步调用方法

### 20、您使用了哪些 starter maven 依赖项？

### 21、SpringBoot 有哪些优点？

### 22、如何给静态变量赋值？

### 23、SpringBoot、Spring MVC 和 Spring 有什么区别？

### 24、如何实现 SpringBoot 应用程序的安全性？

### 25、SpringBoot 微服务中如何实现 session 共享 ?

### 26、SpringBoot 中的监视器是什么？

### 27、我们如何监视所有 SpringBoot 微服务？

### 28、你如何理解 SpringBoot 配置加载顺序？

### 29、如何禁用特定的自动配置类？

### 30、什么是 CSRF 攻击？

### 31、什么是 WebSockets？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
