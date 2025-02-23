# MySQL 最新 2023 年面试题及答案，汇总版

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是存储过程？用什么来调用？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#1什么是存储过程用什么来调用)

存储过程是一个预编译的 SQL 语句，优点是允许模块化的设计，就是说只需创建一次，以后在该程序中就可以调用多次。如果某次操作需要执行多次 SQL，使用存储过程比单纯 SQL 语句执行要快。可以用一个命令对象来调用存储过程。

### [2、优化数据库的方法](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#2优化数据库的方法)

**1、**   选取最适用的字段属性，尽可能减少定义字段宽度，尽量把字段设置 NOTNULL，例如’省份’、’性别’最好适用 ENUM

**2、**   使用连接(JOIN)来代替子查询

**3、**   适用联合(UNION)来代替手动创建的临时表

**4、**   事务处理

**5、**   锁定表、优化事务处理

**6、**   适用外键，优化锁定表

**7、**   建立索引

**8、**   优化查询语句

### [3、完整性约束包括哪些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#3完整性约束包括哪些)

数据完整性(Data Integrity)是指数据的精确(Accuracy)和可靠性(Reliability)。

**分为以下四类：**

**1、** 实体完整性：规定表的每一行在表中是惟一的实体。

**2、** 域完整性：是指表中的列必须满足某种特定的数据类型约束，其中约束又包括取值范围、精度等规定。

**3、** 参照完整性：是指两个表的主关键字和外关键字的数据应一致，保证了表之间的数据的一致性，防止了数据丢失或无意义的数据在数据库中扩散。

**4、** 用户定义的完整性：不同的关系数据库系统根据其应用环境的不同，往往还需要一些特殊的约束条件。用户定义的完整性即是针对某个特定关系数据库的约束条件，它反映某一具体应用必须满足的语义要求。

与表有关的约束：包括列约束(NOT NULL（非空约束）)和表约束(PRIMARY KEY、foreign key、check、UNIQUE) 。

### [4、使用 B 树的好处](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#4使用b树的好处)

B 树可以在内部节点同时存储键和值，因此，把频繁访问的数据放在靠近根节点的地方将会大大提高热点数据的查询效率。这种特性使得 B 树在特定数据重复多次查询的场景中更加高效。

### [5、视图有哪些特点？哪些使用场景？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#5视图有哪些特点哪些使用场景)

**「视图特点：」**

**1、** 视图的列可以来自不同的表，是表的抽象和在逻辑意义上建立的新关系。

**2、** 视图是由基本表(实表)产生的表(虚表)。

**3、** 视图的建立和删除不影响基本表。

**4、** 对视图内容的更新(添加，删除和修改)直接影响基本表。

**5、** 当视图来自多个基本表时，不允许添加和删除数据。

「视图用途：」 简化 sql 查询，提高开发效率，兼容老的表结构。

**「视图的常见使用场景：」**

**1、** 重用 SQL 语句；

**2、** 简化复杂的 SQL 操作。

**3、** 使用表的组成部分而不是整个表；

**4、** 保护数据

**5、** 更改数据格式和表示。视图可返回与底层表的表示和格式不同的数据。

### [6、事务是如何通过日志来实现的](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#6事务是如何通过日志来实现的)

因为事务在修改页时，要先记 undo，在记 undo 之前要记 undo 的 redo， 然后修改数据页，再记数据页修改的 redo。 Redo（里面包括 undo 的修改） 一定要比数据页先持久化到磁盘。

当事务需要回滚时，因为有 undo，可以把数据页回滚到前镜像的 状态，崩溃恢复时，如果 redo log 中事务没有对应的 commit 记录，那么需要用 undo 把该事务的修改回滚到事务开始之前。

如果有 commit 记录，就用 redo 前滚到该事务完成时并提交掉。

### [7、索引有哪几种类型？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#7索引有哪几种类型)

**1、** 主键索引: 数据列不允许重复，不允许为 NULL，一个表只能有一个主键。

**2、** 唯一索引: 数据列不允许重复，允许为 NULL 值，一个表允许多个列创建唯一索引。

**3、** 普通索引: 基本的索引类型，没有唯一性的限制，允许为 NULL 值。

**4、** 全文索引：是目前搜索引擎使用的一种关键技术，对文本的内容进行分词、搜索。

**5、** 覆盖索引：查询列要被所建的索引覆盖，不必读取数据行

**6、** 组合索引：多列值组成一个索引，用于组合搜索，效率大于索引合并

### [8、谈谈六种关联查询，使用场景。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#8谈谈六种关联查询使用场景。)

**1、** 交叉连接

**2、** 内连接

**3、** 外连接

**4、** 联合查询

**5、** 全连接

**6、** 交叉连接

### [9、试述视图的优点？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#9试述视图的优点)

(1) 视图能够简化用户的操作 (2) 视图使用户能以多种角度看待同一数据； (3) 视图为数据库提供了一定程度的逻辑独立性； (4) 视图能够对机密数据提供安全保护。

### [10、MySQL 自增主键用完了怎么办？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新2021年面试题及答案，汇总版.md#10mysql自增主键用完了怎么办)

自增主键一般用 int 类型，一般达不到最大值，可以考虑提前分库分表的。

### 11、为什么要尽量设定一个主键？

### 12、存储时期

### 13、创建索引的三种方式

### 14、为什么要使用数据库

### 15、实践中如何优化 MySQL

### 16、MySQL 如何优化 DISTINCT？

### 17、什么是触发器？触发器的使用场景有哪些？

### 18、如何显示前 50 行？

### 19、如何显示前 50 行？

### 20、B+树在满足聚簇索引和覆盖索引的时候不需要回表查询数据？

### 21、MySQL 中有哪几种锁，列举一下？

### 22、超键、候选键、主键、外键分别是什么？

### 23、为什么官方建议使用自增长主键作为索引？

### 24、什么情况下设置了索引但无法使用

### 25、MySQL 中有哪几种锁，列举一下？

### 26、什么是基本表？什么是视图？

### 27、索引哪些情况会失效

### 28、一个 6 亿的表 a，一个 3 亿的表 b，通过外间 tid 关联，你如何最快的查询出满足条件的第 50000 到第 50200 中的这 200 条数据记录。

### 29、视图有哪些特点？哪些使用场景？

### 30、数据表损坏的修复方式有哪些？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
