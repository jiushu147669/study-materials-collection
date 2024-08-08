# SpringBoot 最新面试题，2023 年面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是 JavaConfig？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#1什么是-javaconfig)

**1、** `面向对象的配置`。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的[@Bean ](/Bean) 方法等。

**2、** `减少或消除 XML 配置`。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将 JavaConfig 与 XML 混合匹配是理想的。

**3、** `类型安全和重构友好`。JavaConfig 提供了一种类型安全的方法来配置 Spring 容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找。

### [2、SpringBoot 多数据源拆分的思路](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#2springboot多数据源拆分的思路)

先在 properties 配置文件中配置两个数据源，创建分包 mapper，使用@ConfigurationProperties 读取 properties 中的配置，使用@MapperScan 注册到对应的 mapper 包中

### [3、前后端分离，如何维护接口文档 ?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#3前后端分离如何维护接口文档-)

前后端分离开发日益流行，大部分情况下，我们都是通过 SpringBoot 做前后端分离开发，前后端分离一定会有接口文档，不然会前后端会深深陷入到扯皮中。一个比较笨的方法就是使用 word 或者 md 来维护接口文档，但是效率太低，接口一变，所有人手上的文档都得变。在 SpringBoot 中，这个问题常见的解决方案是 Swagger ，使用 Swagger 我们可以快速生成一个接口文档网站，接口一旦发生变化，文档就会自动更新，所有开发工程师访问这一个在线网站就可以获取到最新的接口文档，非常方便。

### [4、什么是 Spring Data？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#4什么是-spring-data)

来自：[//projects.spring.io/spring-](//projects.spring.io/spring-) data/

Spring Data 的使命是在保证底层数据存储特殊性的前提下，为数据访问提供一个熟悉的，一致性的，基于 Spring 的编程模型。这使得使用数据访问技术，关系数据库和非关系数据库，map-reduce 框架以及基于云的数据服务变得很容易。

为了让它更简单一些，Spring Data 提供了不受底层数据源限制的 Abstractions 接口。

你可以定义一简单的库，用来插入，更新，删除和检索代办事项，而不需要编写大量的代码。

### [5、什么是 SpringBoot？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#5什么是-springboot)

SpringBoot 是 Spring 开源组织下的子项目，是 Spring 组件一站式解决方案，主要是简化了使用 Spring 的难度，简省了繁重的配置，提供了各种启动器，使开发者能快速上手。

### [6、SpringBoot 如何实现打包](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#6springboot如何实现打包)

进入项目目录在控制台输入 mvn clean package，clean 是清空已存在的项目包，package 进行打包

或者点击左边选项栏中的 Mavne，先点击 clean 在点击 package

### [7、Spring、SpringBoot、SpringMVC 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#7springspringbootspringmvc的区别)

**1、** Spring 框架就像一个家族，有众多衍生产品，例如 boot、mvc、jpa 等等。但他们的基础都是 Spring 的 ioc、aop。ioc 提供了依赖注入的容器，aop 解决了面向横切面编程，然后在此两者的基础上实现了其它延伸产品的高级功能；

**2、** springMVC 是基于 Servlet 的一个 MVC 框架主要解决 WEB 开发的问题；

**3、** 为了简化开发的使用，从而创造性地推出了 SpringBoot 框架，默认优于配置

### [8、你如何理解 SpringBoot 中的 Starters？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#8你如何理解-springboot-中的-starters)

Starters 可以理解为启动器，它包含了一系列可以集成到应用里面的依赖包，你可以一站式集成 Spring 及其他技术，而不需要到处找示例代码和依赖包。如你想使用 Spring JPA 访问数据库，只要加入 spring-boot-starter-data-jpa 启动器依赖就能使用了。

### [9、您使用了哪些 starter maven 依赖项？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#9您使用了哪些-starter-maven-依赖项)

**使用了下面的一些依赖项**

**1、** spring-boot-starter-web 嵌入 tomcat 和 web 开发需要 servlet 与 jsp 支持

**2、** spring-boot-starter-data-jpa 数据库支持

**3、** spring-boot-starter-data-Redis Redis 数据库支持

**4、** spring-boot-starter-data-solr solr 支持

**5、** mybatis-spring-boot-starter 第三方的 mybatis 集成 starter

自定义的 starter(如果自己开发过就可以说出来)

### [10、什么是 JavaConfig？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/SpringBoot/SpringBoot最新面试题，2021年面试题及答案汇总.md#10什么是-javaconfig)

Spring JavaConfig 是 Spring 社区的产品，它提供了配置 Spring IoC 容器的纯 Java 方法。因此它有助于避免使用 XML 配置。使用 JavaConfig 的优点在于：

**1、** 面向对象的配置。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的[@Bean ](/Bean) 方法等。

**2、** 减少或消除 XML 配置。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将 JavaConfig 与 XML 混合匹配是理想的。

**3、** 类型安全和重构友好。JavaConfig 提供了一种类型安全的方法来配置 Spring 容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找。

### 11、SpringBoot 有哪些优点？

### 12、什么是 Apache Kafka？

### 13、我们如何监视所有 SpringBoot 微服务？

### 14、如何使用 SpringBoot 实现异常处理？

### 15、什么是 starter?

### 16、什么是 Swagger？你用 SpringBoot 实现了它吗？

### 17、如何不通过任何配置来选择 Hibernate 作为 JPA 的默认实现？

### 18、SpringBoot 中如何实现定时任务 ?

### 19、开启 SpringBoot 特性有哪几种方式？

### 20、各服务之间通信，对 Restful 和 Rpc 这 2 种方式如何做选择？

### 21、@SpringBootApplication 注释在内部有什么用处?

### 22、SpringBoot 中的监视器是什么？

### 23、运行 SpringBoot 有哪几种方式？

### 24、什么是自动配置？

### 25、您使用了哪些 starter maven 依赖项？

### 26、SpringBoot 打成的 jar 和普通的 jar 有什么区别 ?

### 27、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？

### 28、SpringBoot 实现热部署有哪几种方式？

### 29、SpringBoot 常用的 starter 有哪些?

### 30、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？

### 31、为什么我们需要 spring-boot-maven-plugin?

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
