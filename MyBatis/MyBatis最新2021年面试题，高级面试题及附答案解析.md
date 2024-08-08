# MyBatis 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、Mybatis 的一级、二级缓存](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#1mybatis的一级二级缓存)

**1、** 一级缓存: 基于 PerpetualCache 的 HashMap 本地缓存，其存储作用域为 Session，当 Session flush 或 close 之后，该 Session 中的所有 Cache 就将清空，默认打开一级缓存。

**2、** 二级缓存与一级缓存其机制相同，默认也是采用 PerpetualCache，HashMap 存储，不同在于其存储作用域为 Mapper(Namespace)，并且可自定义存储源，如 Ehcache。默认不打开二级缓存，要开启二级缓存，使用二级缓存属性类需要实现 Serializable 序列化接口(可用来保存对象的状态),可在它的映射文件中配置`<cache/>`

**3、** 对于缓存数据更新机制，当某一个作用域(一级缓存 Session/二级缓存 Namespaces)的进行了 C/U/D 操作后，默认该作用域下所有 select 中的缓存将被 clear。

### [2、简述 Mybatis 的 Xml 映射文件和 Mybatis 内部数据结构之间的映射关系？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#2简述mybatis的xml映射文件和mybatis内部数据结构之间的映射关系)

Mybatis 将所有 Xml 配置信息都封装到 All-In-One 重量级对象 Configuration 内部。在 Xml 映射文件中，`<parameterMap>`标签会被解析为 ParameterMap 对象，其每个子元素会被解析为 ParameterMapping 对象。`<resultMap>`标签会被解析为 ResultMap 对象，其每个子元素会被解析为 ResultMapping 对象。每一个`<select>`、`<insert>`、`<update>`、`<delete>`标签均会被解析为 MappedStatement 对象，标签内的 sql 会被解析为 BoundSql 对象。

### [3、Mybatis 是否支持延迟加载？如果支持，它的实现原理是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#3mybatis是否支持延迟加载如果支持它的实现原理是什么)

Mybatis 仅支持 association 关联对象和 collection 关联集合对象的延迟加载，association 指的就是一对一，collection 指的就是一对多查询。在 Mybatis 配置文件中，可以配置是否启用延迟加载 lazyLoadingEnabled=true|false。

它的原理是，使用 CGLIB 创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用 a.getB().getName()，拦截器 invoke()方法发现 a.getB()是 null 值，那么就会单独发送事先保存好的查询关联 B 对象的 sql，把 B 查询上来，然后调用 a.setB(b)，于是 a 的对象 b 属性就有值了，接着完成 a.getB().getName()方法的调用。这就是延迟加载的基本原理。

当然了，不光是 Mybatis，几乎所有的包括 Hibernate，支持延迟加载的原理都是一样的。

### [4、什么是 MyBatis 的接口绑定？有哪些实现方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#4什么是mybatis的接口绑定有哪些实现方式)

接口绑定，就是在 MyBatis 中任意定义接口,然后把接口里面的方法和 SQL 语句绑定, 我们直接调用接口方法就可以,这样比起原来了 SqlSession 提供的方法我们可以有更加灵活的选择和设置。

接口绑定有两种实现方式,一种是通过注解绑定，就是在接口的方法上面加上 @Select、@Update 等注解，里面包含 Sql 语句来绑定；另外一种就是通过 xml 里面写 SQL 来绑定, 在这种情况下,要指定 xml 映射文件里面的 namespace 必须为接口的全路径名。当 Sql 语句比较简单时候,用注解绑定, 当 SQL 语句比较复杂时候,用 xml 绑定,一般用 xml 绑定的比较多。

### [5、Mapper 编写有几种方式 ？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#5mapper-编写有几种方式-)

**1、** 接口实现类集成`SQLSessionDaoSupport`\*\* 此方法需要编写`mapper`接口，`mapper`接口的实现类,`mapper.xml`文件。

**2、** 使用`org.mybatis.spring.mapper.MapperFactoryBean`\*\* 此方法需要在`SqlMapConfig.xml`中配置`mapper.xml`的位置，还需定义`mapper`接口。

**3、** 使用`mapper`扫描器\*\* 需要编写`mapper.xml`文件，需要`mapper`接口，配置`mapper`扫描器，使用扫描器从`spring`容器中获取`mapper`的实现对象。

### [6、Mybatis 动态 sql 有什么用？执行原理？有哪些动态 sql？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#6mybatis动态sql有什么用执行原理有哪些动态sql)

Mybatis 动态 sql 可以在 Xml 映射文件内，以标签的形式编写动态 sql，执行原理是根据表达式的值 完成逻辑判断并动态拼接 sql 的功能。

Mybatis 提供了 9 种动态 sql 标签：`trim | where | set | foreach | if | choose | when | otherwise | bind`。

### [7、MyBatis 实现一对一有几种方式?具体怎么操作的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#7mybatis实现一对一有几种方式具体怎么操作的)

有联合查询和嵌套查询,联合查询是几个表联合查询,只查询一次, 通过在 resultMap 里面配置 association 节点配置一对一的类就可以完成；

嵌套查询是先查一个表，根据这个表里面的结果的 外键 id，去再另外一个表里面查询数据,也是通过 association 配置，但另外一个表的查询通过 select 属性配置。

### [8、模糊查询 like 语句该怎么写](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#8模糊查询like语句该怎么写)

- 1 ’%${question}%’ 可能引起 SQL 注入，不推荐
- 2 "%"#{question}"%" 注意：因为#{…}解析成 sql 语句时候，会在变量外侧自动加单引号’ '，所以这里 % 需要使用双引号" "，不能使用单引号 ’ '，不然会查不到任何结果。
- 3 CONCAT(’%’,#{question},’%’) 使用 CONCAT()函数，（推荐）
- 4 使用 bind 标签（不推荐）

```
<select id="listUserLikeUsername" resultType="com.jourwon.pojo.User">
  <bind name="pattern" value="'%' + username + '%'" />
  select id,sex,age,username,password from person where username LIKE{pattern}
</select>
```

### [9、MyBatis 实现一对多有几种方式,怎么操作的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#9mybatis实现一对多有几种方式,怎么操作的)

有联合查询和嵌套查询。联合查询是几个表联合查询,只查询一次,通过在 resultMap 里面的 collection 节点配置一对多的类就可以完成；嵌套查询是先查一个表,根据这个表里面的 结果的外键 id,去再另外一个表里面查询数据,也是通过配置 collection,但另外一个表的查询通过 select 节点配置。

### [10、Mapper 编写有哪几种方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MyBatis/MyBatis最新2021年面试题，高级面试题及附答案解析.md#10mapper编写有哪几种方式)

第一种：接口实现类继承 SqlSessionDaoSupport：使用此种方法需要编写 mapper 接口，mapper 接口实现类、mapper.xml 文件。

**1、** 在 sqlMapConfig.xml 中配置 mapper.xml 的位置

```xml
<mappers>
    <mapper resource="mapper.xml文件的地址" />
    <mapper resource="mapper.xml文件的地址" />
</mappers>
```

**1、** 定义 mapper 接口

**3、** 实现类集成 SqlSessionDaoSupport

mapper 方法中可以 this.getSqlSession()进行数据增删改查。

**4、** spring 配置

```xml
<bean id=" " class="mapper接口的实现">
    <property name="sqlSessionFactory" ref="sqlSessionFactory"></property>
</bean>
```

第二种：使用`org.mybatis.spring.mapper.MapperFactoryBean`：

**1、** 在 sqlMapConfig.xml 中配置 mapper.xml 的位置，如果 mapper.xml 和 mappre 接口的名称相同且在同一个目录，这里可以不用配置

```xml
<mappers>
    <mapper resource="mapper.xml文件的地址" />
    <mapper resource="mapper.xml文件的地址" />
</mappers>
```

**2、** 定义 mapper 接口：

**1、** mapper.xml 中的 namespace 为 mapper 接口的地址

**2、** mapper 接口中的方法名和 mapper.xml 中的定义的 statement 的 id 保持一致

**3、** Spring 中定义

```xml
<bean id="" class="org.mybatis.spring.mapper.MapperFactoryBean">
    <property name="mapperInterface"   value="mapper接口地址" />
    <property name="sqlSessionFactory" ref="sqlSessionFactory" />
</bean>
```

第三种：使用 mapper 扫描器：

**1、** mapper.xml 文件编写：

mapper.xml 中的 namespace 为 mapper 接口的地址；

mapper 接口中的方法名和 mapper.xml 中的定义的 statement 的 id 保持一致；

如果将 mapper.xml 和 mapper 接口的名称保持一致则不用在 sqlMapConfig.xml 中进行配置。

**2、** 定义 mapper 接口：

注意 mapper.xml 的文件名和 mapper 的接口名称保持一致，且放在同一个目录

**3、** 配置 mapper 扫描器：

```xml
<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
    <property name="basePackage" value="mapper接口包地址"></property>
    <property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/>
</bean>
```

**4、** 使用扫描器后从 spring 容器中获取 mapper 的实现对象。

### 11、MyBatis 框架的缺点：

### 12、MyBatis 里面的动态 Sql 是怎么设定的?用什么语法?

### 13、简述 Mybatis 的插件运行原理，以及如何编写一个插件。

### 14、Mybatis 动态 SQL？

### 15、使用 MyBatis 的 mapper 接口调用时有哪些要求？

### 16、Mybatis 是如何进行分页的？分页插件的原理是什么？

### 17、如何获取自动生成的(主)键值？

### 18、Mybatis 能执行一对一、一对多的关联查询吗？都有哪些实现方式，以及它们之间的区

### 19、简述 Mybatis 的插件运行原理，以及如何编写一个插件？

### 20、模糊查询 like 语句该怎么写?

### 21、Mybatis 是如何将 sql 执行结果封装为目标对象并返回的？都有哪些映射形式？

### 22、Mybatis 中如何指定使用哪一种 Executor 执行器？

### 23、JDBC 编程有哪些不足之处，MyBatis 是如何解决的？

### 24、Mybatis 优缺点

### 25、{}里面的名称对应的是 Map 里面的 key 名称。

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
