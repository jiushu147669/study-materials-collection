# MySQL 最新面试题及答案整理，汇总版

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、MySQL 中 DATETIME 和 TIMESTAMP 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#1mysql中datetime和timestamp的区别)

存储精度都为秒

**区别：**

**1、** DATETIME 的日期范围是 1001——9999 年；TIMESTAMP 的时间范围是 1970——2038 年

**2、** DATETIME 存储时间与时区无关；TIMESTAMP 存储时间与时区有关，显示的值也依赖于时区

**3、** DATETIME 的存储空间为 8 字节；TIMESTAMP 的存储空间为 4 字节

**4、** DATETIME 的默认值为 null；TIMESTAMP 的字段默认不为空(not null)，默认值为当前时间(CURRENT_TIMESTAMP)

### [2、简单描述 MySQL 中，索引，主键，唯一索引，联合索引的区别，对数据库的性能有什么影响（从读写两方面）](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#2简单描述mysql中索引主键唯一索引联合索引的区别对数据库的性能有什么影响从读写两方面)

索引是一种特殊的文件(InnoDB 数据表上的索引是表空间的一个组成部分)，它们包含着对数据表里所有记录的引用指针。

普通索引(由关键字 KEY 或 INDEX 定义的索引)的唯一任务是加快对数据的访问速度。

普通索引允许被索引的数据列包含重复的值。如果能确定某个数据列将只包含彼此各不相同的值，在为这个数据列创建索引的时候就应该用关键字 UNIQUE 把它定义为一个唯一索引。也就是说，唯一索引可以保证数据记录的唯一性。

主键，是一种特殊的唯一索引，在一张表中只能定义一个主键索引，主键用于唯一标识一条记录，使用关键字 PRIMARY KEY 来创建。

索引可以覆盖多个数据列，如像 INDEX(columnA, columnB)索引，这就是联合索引。

索引可以极大的提高数据的查询速度，但是会降低插入、删除、更新表的速度，因为在执行这些写操作时，还要操作索引文件。

### [3、什么是 SQL？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#3什么是sql)

结构化查询语言(Structured Query Language)简称 SQL，是一种数据库查询语言。

**作用：**

用于存取数据、查询、更新和管理关系数据库系统。

### [4、MyISAM 表格将在哪里存储，并且还提供其存储格式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#4myisam表格将在哪里存储并且还提供其存储格式)

**每个 MyISAM 表格以三种格式存储在磁盘上：**

**1、** ·“.frm”文件存储表定义

**2、** ·数据文件具有“.MYD”（MYData）扩展名

**3、** 索引文件具有“.MYI”（MYIndex）扩展名

### [5、MySQL 支持事务吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#5mysql支持事务吗)

在缺省模式下，MySQL 是 autocommit 模式的，所有的数据库更新操作都会即时提交，所以在缺省情况下，MySQL 是不支持事务的。

但是如果你的 MySQL 表类型是使用 InnoDB Tables 或 BDB tables 的话，你的 MySQL 就可以使用事务处理,使用 SET

AUTOCOMMIT=0 就可以使 MySQL 允许在非 autocommit 模式，在非 autocommit 模式下，你必须使用 COMMIT 来提交你的更改，或者用 ROLLBACK 来回滚你的更改。

### [6、从锁的类别角度讲，MySQL 都有哪些锁呢？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#6从锁的类别角度讲mysql都有哪些锁呢)

**从锁的类别上来讲，有共享锁和排他锁**

**1、** 共享锁: 又叫做读锁。当用户要进行数据的读取时，对数据加上共享锁。共享锁可以同时加上多个。

**2、** 排他锁: 又叫做写锁。当用户要进行数据的写入时，对数据加上排他锁。排他锁只可以加一个，他和其他的排他锁，共享锁都相斥。

锁兼容性如下：

![](https://user-gold-cdn.xitu.io/2020/5/23/172412db1d202759?w=1045&h=229&f=png&s=68561#alt=)

### [7、MVCC 熟悉吗，它的底层原理？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#7mvcc熟悉吗它的底层原理)

MVCC,多版本并发控制,它是通过读取历史版本的数据，来降低并发事务冲突，从而提高并发性能的一种机制。

**「MVCC 需要关注这几个知识点：」**

**1、** 事务版本号

**2、** 表的隐藏列

**3、** undo log

**4、** read view

### [8、存储时期](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#8存储时期)

**1、** `Datatime:以 YYYY-MM-DD HH:MM:SS` 格式存储时期时间，精确到秒，占用 8 个字节得存储空间，datatime 类型与时区无关

**2、** Timestamp:以时间戳格式存储，占用 4 个字节，范围小 1970-1-1 到 2038-1-19，显示依赖于所指定得时区，默认在第一个列行的数据修改时可以自动得修改 timestamp 列得值

**3、** Date:（生日）占用得字节数比使用字符串.datatime.int 储存要少，使用 date 只需要 3 个字节，存储日期月份，还可以利用日期时间函数进行日期间得计算

**4、** Time:存储时间部分得数据

**5、** 注意:不要使用字符串类型来存储日期时间数据（通常比字符串占用得储存空间小，在进行查找过滤可以利用日期得函数）

**6、** 使用 int 存储日期时间不如使用 timestamp 类型

### [9、什么是 MySQL?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#9什么是mysql)

MySQL 是一个关系型数据库管理系统，由瑞典 MySQL AB 公司开发，属于 Oracle 旗下产品。MySQL 是最流行的关系型数据库管理系统之一，在 WEB 应用方面，MySQL 是最好的 RDBMS (Relational Database Management System，关系数据库管理系统) 应用软件之一。在 Java 企业级开发中非常常用，因为 MySQL 是开源免费的，并且方便扩展。

### [10、MySQL 的复制原理以及流程](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案整理，汇总版.md#10mysql的复制原理以及流程)

「主从复制原理，简言之，就三步曲，如下：」

**1、** 主数据库有个 bin-log 二进制文件，纪录了所有增删改 Sql 语句。（binlog 线程）

**2、** 从数据库把主数据库的 bin-log 文件的 sql 语句复制过来。（io 线程）

**3、** 从数据库的 relay-log 重做日志文件中再执行一次这些 sql 语句。（Sql 执行线程）

**上图主从复制分了五个步骤进行：**

步骤一：主库的更新事件(update、insert、delete)被写到 binlog

步骤二：从库发起连接，连接到主库。

步骤三：此时主库创建一个 binlog dump thread，把 binlog 的内容发送到从库。

步骤四：从库启动之后，创建一个 I/O 线程，读取主库传过来的 binlog 内容并写入到 relay log

步骤五：还会创建一个 SQL 线程，从 relay log 里面读取内容，从 Exec_Master_Log_Pos 位置开始执行读取到的更新事件，将更新内容写入到 slave 的 db

### 11、如何优化查询过程中的数据访问

### 12、如果某个表有近千万数据，CRUD 比较慢，如何优化。

### 13、如果要存储用户的密码散列，应该使用什么字段进行存储？

### 14、数据库存储日期格式时，如何考虑时区转换问题？

### 15、使用 B+树的好处

### 16、视图的缺点

### 17、数据库结构优化

### 18、索引有哪些优缺点？

### 19、非主键索引一定会查询多次吗？

### 20、按照锁的粒度分，数据库锁有哪些呢？锁机制与 InnoDB 锁算法

### 21、为什么要使用数据库

### 22、如何通俗地理解三个范式？

### 23、说说 MySQL 的基础架构图

### 24、什么是索引？

### 25、数据库索引的原理，为什么要用 B+树，为什么不用二叉树？

### 26、SQL 语句主要分为哪几类

### 27、覆盖索引、回表等这些，了解过吗？

### 28、什么是聚簇索引？何时使用聚簇索引与非聚簇索引

### 29、Innodb 的事务实现原理？

### 30、MySQL 中 InnoDB 引擎的行锁是怎么实现的？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
