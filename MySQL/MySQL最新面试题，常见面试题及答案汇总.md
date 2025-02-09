# MySQL 最新面试题，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、超大分页怎么处理？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#1超大分页怎么处理)

**超大的分页一般从两个方向上来解决.**

**1、** 数据库层面,这也是我们主要集中关注的(虽然收效没那么大),类似于`select * from table where age > 20 limit 1000000,10`这种查询其实也是有可以优化的余地的、这条语句需要 load1000000 数据然后基本上全部丢弃,只取 10 条当然比较慢、当时我们可以修改为`select * from table where id in (select id from table where age > 20 limit 1000000,10)`.这样虽然也 load 了一百万的数据,但是由于索引覆盖,要查询的所有字段都在索引中,所以速度会很快、同时如果 ID 连续的好,我们还可以`select * from table where id > 1000000 limit 10`,效率也是不错的,优化的可能性有许多种,但是核心思想都一样,就是减少 load 的数据.

**2、** 从需求的角度减少这种请求…主要是不做类似的需求(直接跳转到几百万页之后的具体某一页.只允许逐页查看或者按照给定的路线走,这样可预测,可缓存)以及防止 ID 泄漏且连续被人恶意攻击.

解决超大分页,其实主要是靠缓存,可预测性的提前查到内容,缓存至 Redis 等 k-V 数据库中,直接返回即可

### [2、存储引擎分类有哪些以及使用场景？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#2存储引擎分类有哪些以及使用场景)

**存储引擎主要有**

**1、** MyIsam

**2、** InnoDB

**3、** Memory

**4、** Archive

**5、** Federated

默认为:InnoDB 引擎。InnoDB 底层存储结构为 B+树， B 树的每个节点对应 innodb

的一个 page，page 大小是固定的，一般设为 16k

**使用场景**

**1、** 经常更新的表，适合处理多重并发的更新请求

**2、** 支持事务。

**3、** 可以从灾难中恢复(通过 bin-log 日志等)

**4、** 外键约束。只有他支持外键。

**5、** 支持自动增加列属性 auto_increment

### [3、视图有哪些特点？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#3视图有哪些特点)

**视图的特点如下:**

**1、** 视图的列可以来自不同的表，是表的抽象和在逻辑意义上建立的新关系。

**2、** 视图是由基本表(实表)产生的表(虚表)。

**3、** 视图的建立和删除不影响基本表。

**4、** 对视图内容的更新(添加，删除和修改)直接影响基本表。

**5、** 当视图来自多个基本表时，不允许添加和删除数据。

视图的操作包括创建视图，查看视图，删除视图和修改视图。

### [4、什么是存储过程？有哪些优缺点？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#4什么是存储过程有哪些优缺点)

「存储过程」，就是一些编译好了的 SQL 语句，这些 SQL 语句代码像一个方法一样实现一些功能（对单表或多表的增删改查），然后给这些代码块取一个名字，在用到这个功能的时候调用即可。

**「优点：」**

**1、** 存储过程是一个预编译的代码块，执行效率比较高

**2、** 存储过程在服务器端运行，减少客户端的压力

**3、** 允许模块化程序设计，只需要创建一次过程，以后在程序中就可以调用该过程任意次，类似方法的复用

**4、** 一个存储过程替代大量 T_SQL 语句 ，可以降低网络通信量，提高通信速率

**5、** 可以一定程度上确保数据安全

**「缺点：」**

**1、** 调试麻烦

**2、** 可移植性不灵活

**3、** 重新编译问题

### [5、日常工作中你是怎么优化 SQL 的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#5日常工作中你是怎么优化sql的)

可以从这几个维度回答这个问题：

**1、** 加索引

**2、** 避免返回不必要的数据

**3、** 适当分批量进行

**4、** 优化 sql 结构

**5、** 分库分表

**6、** 读写分离

### [6、创建索引的原则](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#6创建索引的原则)

**索引虽好，但也不是无限制的使用，最好符合一下几个原则**

**1、** 最左前缀匹配原则，组合索引非常重要的原则，MySQL 会一直向右匹配直到遇到范围查询(>、<、between、like)就停止匹配，比如 a = 1 and b = 2 and c > 3 and d = 4 如果建立(a,b,c,d)顺序的索引，d 是用不到索引的，如果建立(a,b,d,c)的索引则都可以用到，a,b,d 的顺序可以任意调整。

**2、** 较频繁作为查询条件的字段才去创建索引

**3、** 更新频繁字段不适合创建索引

**4、** 若是不能有效区分数据的列不适合做索引列(如性别，男女未知，最多也就三种，区分度实在太低)

**5、** 尽量的扩展索引，不要新建索引。比如表中已经有 a 的索引，现在要加(a,b)的索引，那么只需要修改原来的索引即可。

**6、** 定义有外键的数据列一定要建立索引。

**7、** 对于那些查询中很少涉及的列，重复值比较多的列不要建立索引。

**8、** 对于定义为 text、image 和 bit 的数据类型的列不要建立索引。

### [7、什么是死锁？怎么解决？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#7什么是死锁怎么解决)

死锁是指两个或多个事务在同一资源上相互占用，并请求锁定对方的资源，从而导致恶性循环的现象。

**常见的解决死锁的方法**

**1、** 如果不同程序会并发存取多个表，尽量约定以相同的顺序访问表，可以大大降低死锁机会。

**2、** 在同一个事务中，尽可能做到一次锁定所需要的所有资源，减少死锁产生概率；

**3、** 对于非常容易产生死锁的业务部分，可以尝试使用升级锁定颗粒度，通过表级锁定来减少死锁产生的概率；

如果业务不好处理,可以用分布式事务锁或者使用乐观锁

### [8、为表中得字段选择合适得数据类型](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#8为表中得字段选择合适得数据类型)

字段类型优先级: 整形>date,time>enum,char>varchar>blob,text

优先考虑数字类型，其次是日期或者二进制类型，最后是字符串类型，同级别得数据类型，应该优先选择占用空间小的数据类型

### [9、MySQL 索引使用有哪些注意事项呢？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#9mysql-索引使用有哪些注意事项呢)

可以从三个维度回答这个问题：索引哪些情况会失效，索引不适合哪些场景，索引规则

**索引哪些情况会失效**

**1、** 查询条件包含 or，可能导致索引失效

**2、** 如何字段类型是字符串，where 时一定用引号括起来，否则索引失效

**3、** like 通配符可能导致索引失效。

**4、** 联合索引，查询时的条件列不是联合索引中的第一个列，索引失效。

**5、** 在索引列上使用 MySQL 的内置函数，索引失效。

**6、** 对索引列运算（如，+、-、\*、/），索引失效。

**7、** 索引字段上使用（！= 或者 < >，not in）时，可能会导致索引失效。

**8、** 索引字段上使用 is null， is not null，可能导致索引失效。

**9、** 左连接查询或者右连接查询查询关联的字段编码格式不一样，可能导致索引失效。

**10、** MySQL 估计使用全表扫描要比使用索引快,则不使用索引。

**索引不适合哪些场景**

**1、** 数据量少的不适合加索引

**2、** 更新比较频繁的也不适合加索引

**3、** 区分度低的字段不适合加索引（如性别）

**索引的一些潜规则**

**1、** 覆盖索引

2、回表

**3、** 索引数据结构（B+树）

**4、** 最左前缀原则

**5、** 索引下推

### [10、什么是锁？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题，常见面试题及答案汇总.md#10什么是锁)

数据库是一个多用户使用的共享资源。当多个用户并发地存取数据时，在数据库中就会产生多个事务同时存取同一数据的情况。若对并发操作不加控制就可能会读取和存储不正确的数据，破坏数据库的一致性。

加锁是实现数据库并发控制的一个非常重要的技术。当事务在对某个数据对象进行操作前，先向系统发出请求，对其加锁。加锁后事务就对该数据对象有了一定的控制，在该事务释放锁之前，其他的事务不能对此数据对象进行更新操作。

**基本锁类型：锁包括行级锁和表级锁**

### 11、索引有哪几种类型？

### 12、组合索引是什么？为什么需要注意组合索引中的顺序？

### 13、MySQL 中 InnoDB 支持的四种事务隔离级别名称，以及逐级之间的区别？

### 14、MySQL 如何获取当前日期？

### 15、关心过业务系统里面的 sql 耗时吗？统计过慢查询吗？对慢查询都怎么优化过？

### 16、MySQL 中 in 和 exists 区别

### 17、MySQL 中 DATETIME 和 TIMESTAMP 的区别

### 18、简单描述 MySQL 中，索引，主键，唯一索引，联合索引的区别，对数据库的性能有什么影响（从读写两方面）

### 19、列的字符串类型可以是什么？

### 20、MySQL 中 in 和 exists 的区别。

### 21、为什么要使用视图？什么是视图？

### 22、什么是非标准字符串类型？

### 23、创建索引时需要注意什么？

### 24、简单总结下

### 25、如果要存储用户的密码散列，应该使用什么字段进行存储？

### 26、SQL 注入漏洞产生的原因？如何防止？

### 27、说一下数据库的三大范式

### 28、什么是基本表？什么是视图？

### 29、索引设计的原则？

### 30、索引有哪些优缺点？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
