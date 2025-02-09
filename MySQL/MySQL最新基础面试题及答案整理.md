# MySQL 最新基础面试题及答案整理

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、NOW（）和 CURRENT_DATE（）有什么区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#1now和current_date有什么区别)

NOW（）命令用于显示当前年份，月份，日期，小时，分钟和秒。

CURRENT_DATE（）仅显示当前年份，月份和日期。

### [2、CHAR 和 VARCHAR 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#2char和varchar的区别)

1.CHAR 和 VARCHAR 类型在存储和检索方面有所不同

2.CHAR 列长度固定为创建表时声明的长度，长度值范围是 1 到 255

当 CHAR 值被存储时，它们被用空格填充到特定长度，检索 CHAR 值时需删除尾随空格。

### [3、主键索引与唯一索引的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#3主键索引与唯一索引的区别)

**1、** 主键是一种约束，唯一索引是一种索引，两者在本质上是不同的。

**2、** 主键创建后一定包含一个唯一性索引，唯一性索引并不一定就是主键。

**3、** 唯一性索引列允许空值，而主键列不允许为空值。

**4、** 主键列在创建时，已经默认为空值 ++ 唯一索引了。

**5、** 一个表最多只能创建一个主键，但可以创建多个唯一索引。

**6、** 主键更适合那些不容易更改的唯一标识，如自动递增列、身份证号等。

**7、** 主键可以被其他表引用为外键，而唯一索引不能。 ？

### [4、MySQL 中有哪些不同的表格？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#4mysql中有哪些不同的表格)

**共有 5 种类型的表格：**

**1、** MyISAM

**2、** Heap

**3、** Merge

**4、** INNODB

**5、** ISAM

### [5、SQL 的生命周期？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#5sql的生命周期)

**1、** 应用服务器与数据库服务器建立一个连接

**2、** 数据库进程拿到请求 sql

**3、** 解析并生成执行计划，执行

**4、** 读取数据到内存并进行逻辑处理

**5、** 通过步骤一的连接，发送结果到客户端

**6、** 关掉连接，释放资源

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/049/50/99_8.png#alt=99%5C_8.png)

### [6、你怎么看到为表格定义的所有索引？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#6你怎么看到为表格定义的所有索引)

索引是通过以下方式为表格定义的：

`SHOW INDEX FROM <tablename>;`

### [7、数据库为什么使用 B+树而不是 B 树](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#7数据库为什么使用b+树而不是b树)

**1、** B 树只适合随机检索，而 B+树同时支持随机检索和顺序检索；

**2、** B+树空间利用率更高，可减少 I/O 次数，磁盘读写代价更低。一般来说，索引本身也很大，不可能全部存储在内存中，因此索引往往以索引文件的形式存储的磁盘上。这样的话，索引查找过程中就要产生磁盘 I/O 消耗。B+树的内部结点并没有指向关键字具体信息的指针，只是作为索引使用，其内部结点比 B 树小，盘块能容纳的结点中关键字数量更多，一次性读入内存中可以查找的关键字也就越多，相对的，IO 读写次数也就降低了。而 IO 读写次数是影响索引检索效率的最大因素；

**3、** B+树的查询效率更加稳定。B 树搜索有可能会在非叶子结点结束，越靠近根节点的记录查找时间越短，只要找到关键字即可确定记录的存在，其性能等价于在关键字全集内做一次二分查找。而在 B+树中，顺序检索比较明显，随机检索时，任何关键字的查找都必须走一条从根节点到叶节点的路，所有关键字的查找路径长度相同，导致每一个关键字的查询效率相当。

**4、** B-树在提高了磁盘 IO 性能的同时并没有解决元素遍历的效率低下的问题。B+树的叶子节点使用指针顺序连接在一起，只要遍历叶子节点就可以实现整棵树的遍历。而且在数据库中基于范围的查询是非常频繁的，而 B 树不支持这样的操作。

**5、** 增删文件（节点）时，效率更高。因为 B+树的叶子节点包含所有关键字，并以有序的链表结构存储，这样可很好提高增删效率。

### [8、数据库三大范式是什么](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#8数据库三大范式是什么)

第一范式：每个列都不可以再拆分。

第二范式：在第一范式的基础上，非主键列完全依赖于主键，而不能是依赖于主键的一部分。

第三范式：在第二范式的基础上，非主键列只依赖于主键，不依赖于其他非主键。

在设计数据库结构的时候，要尽量遵守三范式，如果不遵守，必须有足够的理由。比如性能。事实上我们经常会为了性能而妥协数据库的设计。

### [9、怎么优化 SQL 查询语句吗](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#9怎么优化sql查询语句吗)

**1、** 对查询进行优化，应尽量避免全表扫描，首先应考虑在 where 及 order by 涉及的列上建立索引

**2、** 用索引可以提高查询

**3、** SELECT 子句中避免使用\*号，尽量全部大写 SQL

**4、** 应尽量避免在 where 子句中对字段进行 is null 值判断，否则将导致引擎放弃使用索引而进行全表扫描，使用 IS NOT NULL

**5、** where 子句中使用 or 来连接条件，也会导致引擎放弃使用索引而进行全表扫描

**6、** in 和 not in 也要慎用，否则会导致全表扫描

### [10、覆盖索引、回表等这些，了解过吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新基础面试题及答案整理.md#10覆盖索引回表等这些了解过吗)

**1、** 覆盖索引： 查询列要被所建的索引覆盖，不必从数据表中读取，换句话说查询列要被所使用的索引覆盖。

**2、** 回表：二级索引无法直接查询所有列的数据，所以通过二级索引查询到聚簇索引后，再查询到想要的数据，这种通过二级索引查询出来的过程，就叫做回表。

网上这篇文章讲得很清晰：

[MySQL 覆盖索引与回表](https://www.jianshu.com/p/8991cbca3854)

### 11、NULL 是什么意思

### 12、MySQL 中 in 和 exists 的区别。

### 13、500 台 db，在最快时间之内重启。

### 14、MySQL 数据库作发布系统的存储，一天五万条以上的增量，预计运维三年,怎么优化？

### 15、NOW（）和 CURRENT_DATE（）有什么区别？

### 16、超键、候选键、主键、外键分别是什么？

### 17、关心过业务系统里面的 sql 耗时吗？统计过慢查询吗？对慢查询都怎么优化过？

### 18、为什么要使用视图？什么是视图？

### 19、索引的一些潜规则

### 20、myisamchk 是用来做什么的？

### 21、如何在 Unix 和 MySQL 时间戳之间进行转换？

### 22、什么是索引？

### 23、日常工作中你是怎么优化 SQL 的？

### 24、MYSQL 的主从延迟，你怎么解决？

### 25、索引的底层实现

### 26、SQL 语言包括哪几部分？每部分都有哪些操作关键字？

### 27、500 台 db，在最快时间之内重启。

### 28、MySQL 中 TEXT 数据类型的最大长度

### 29、数据库存储日期格式时，如何考虑时区转换问题？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
