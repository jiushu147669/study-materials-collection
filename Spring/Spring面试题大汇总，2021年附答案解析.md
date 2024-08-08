# Spring 面试题大汇总，2023 年附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、SpringBoot 常用的 starter 有哪些?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#1springboot常用的starter有哪些)

**1、** `spring-boot-starter-web` (嵌入 tomcat 和 web 开发需要 servlet 与 jsp 支持)

**2、** `spring-boot-starter-data-jpa` (数据库支持)

**3、** `spring-boot-starter-data-Redis` (Redis 数据库支持)

**4、** `spring-boot-starter-data-solr` (solr 搜索应用框架支持)

**5、** `mybatis-spring-boot-starter` (第三方的 mybatis 集成 starter)

### [2、前后端分离，如何维护接口文档 ?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#2前后端分离如何维护接口文档-)

前后端分离开发日益流行，大部分情况下，我们都是通过 SpringBoot 做前后端分离开发，前后端分离一定会有接口文档，不然会前后端会深深陷入到扯皮中。一个比较笨的方法就是使用 word 或者 md 来维护接口文档，但是效率太低，接口一变，所有人手上的文档都得变。在 SpringBoot 中，这个问题常见的解决方案是 Swagger ，使用 Swagger 我们可以快速生成一个接口文档网站，接口一旦发生变化，文档就会自动更新，所有开发工程师访问这一个在线网站就可以获取到最新的接口文档，非常方便。

### [3、有几种不同类型的自动代理？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#3有几种不同类型的自动代理)

BeanNameAutoProxyCreator

DefaultAdvisorAutoProxyCreator

Metadata autoproxying

### [4、什么是 FreeMarker 模板？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#4什么是freemarker模板)

FreeMarker 是一个基于 Java 的模板引擎，最初专注于使用 MVC 软件架构进行动态网页生成。使用 Freemarker 的主要优点是表示层和业务层的完全分离。程序员可以处理应用程序代码，而设计人员可以处理 html 页面设计。最后使用 freemarker 可以将这些结合起来，给出最终的输出页面。

### [5、什么是持续集成（CI）？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#5什么是持续集成ci)

持续集成（CI）是每次团队成员提交版本控制更改时自动构建和测试代码的过程。这鼓励开发人员通过在每个小任务完成后将更改合并到共享版本控制存储库来共享代码和单元测试。

### [6、Spring MVC 的优点](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#6spring-mvc的优点)

**1、** 可以支持各种视图技术,而不仅仅局限于 JSP；

**2、** 与 Spring 框架集成（如 IoC 容器、AOP 等）；

**3、** 清晰的角色分配：前端控制器(dispatcherServlet) , 请求到处理器映射（handlerMapping), 处理器适配器（HandlerAdapter), 视图解析器（ViewResolver）。

**4、** 支持各种请求资源的映射策略。

### [7、Spring Initializr 是创建 SpringBoot Projects 的唯一方法吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#7spring-initializr-是创建-springboot-projects-的唯一方法吗)

不是的。

Spring Initiatlizr 让创建 SpringBoot 项目变的很容易，但是，你也可以通过设置一个 maven 项目并添加正确的依赖项来开始一个项目。

在我们的 Spring 课程中，我们使用两种方法来创建项目。

第一种方法是 start.spring.io 。

另外一种方法是在项目的标题为“Basic Web Application”处进行手动设置。

手动设置一个 maven 项目

**这里有几个重要的步骤：**

**1、** 在 Eclipse 中，使用文件 - 新建 Maven 项目来创建一个新项目

**2、** 添加依赖项。

**3、** 添加 maven 插件。

**4、** 添加 SpringBoot 应用程序类。

到这里，准备工作已经做好！

### [8、使用 Spring 通过什么方式访问 Hibernate?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#8使用spring通过什么方式访问hibernate)

**在 Spring 中有两种方式访问 Hibernate：**

控制反转 Hibernate Template 和 Callback。

继承 HibernateDAOSupport 提供一个 AOP 拦截器。

### [9、什么是 bean 的自动装配？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#9什么是bean的自动装配)

Spring 容器能够自动装配相互合作的 bean，这意味着容器不需要和配置，能通过 Bean 工厂自动处理 bean 之间的协作。

### [10、[@Qualifier ](/Qualifier ) 注解](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Spring/Spring面试题大汇总，2021年附答案解析.md#10[@qualifier-]/qualifier--注解)

当有多个相同类型的 bean 却只有一个需要自动装配时，将[@Qualifier ](/Qualifier) 注解和[@Autowire ](/Autowire) 注解结合使用以消除这种混淆，指定需要装配的确切的 bean。

### 11、Spring Cloud Config

### 12、YAML 配置的优势在哪里 ?

### 13、服务注册和发现是什么意思？Spring Cloud 如何实现？

### 14、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？

### 15、什么是基于 Java 的 Spring 注解配置? 给一些注解的例子.

### 16、什么是 SpringBoot？

### 17、什么是 Eureka

### 18、自动装配有哪些局限性 ?

### 19、什么是 Swagger？你用 SpringBoot 实现了它吗？

### 20、Spring IoC 的实现机制。

### 21、[@Autowired ](/Autowired) 注解有什么用？

### 22、RequestMapping 和 GetMapping 的不同之处在哪里？

### 23、开启 SpringBoot 特性有哪几种方式？

### 24、Spring 支持的事务管理类型

### 25、什么是 Spring Initializer?

### 26、Spring AOP and AspectJ AOP 有什么区别？

### 27、什么是不同类型的双因素身份认证？

### 28、SpringBoot 与 SpringCloud 区别

### 29、我们如何在测试中消除非决定论？

### 30、什么是 Oauth？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
