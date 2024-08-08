# MySQL 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、对 MySQL 的锁了解吗](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#1对mysql的锁了解吗)

当数据库有并发事务的时候，可能会产生数据的不一致，这时候需要一些机制来保证访问的次序，锁机制就是这样的一个机制。

就像酒店的房间，如果大家随意进出，就会出现多人抢夺同一个房间的情况，而在房间上装上锁，申请到钥匙的人才可以入住并且将房间锁起来，其他人只有等他使用完毕才可以再次使用。

### [2、MySQL 中有哪几种锁？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#2mysql中有哪几种锁)

1.表级锁：开销小，加锁快；不会出现死锁；锁定粒度大，发生锁冲突的概率最高，并发度最低。

2.行级锁：开销大，加锁慢；会出现死锁；锁定粒度最小，发生锁冲突的概率最低，并发度也最高。

3\、页面锁：开销和加锁时间界于表锁和行锁之间；会出现死锁；锁定粒度界于表锁和行锁之间，并发度一般。

### [3、MySQL 一条 SQL 加锁分析](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#3mysql一条sql加锁分析)

一条 SQL 加锁，可以分 9 种情况进行：

**1、** 组合一：id 列是主键，RC 隔离级别

**2、** 组合二：id 列是二级唯一索引，RC 隔离级别

**3、** 组合三：id 列是二级非唯一索引，RC 隔离级别

**4、** 组合四：id 列上没有索引，RC 隔离级别

**5、** 组合五：id 列是主键，RR 隔离级别

**6、** 组合六：id 列是二级唯一索引，RR 隔离级别

**7、** 组合七：id 列是二级非唯一索引，RR 隔离级别

**8、** 组合八：id 列上没有索引，RR 隔离级别

**9、** 组合九：Serializable 隔离级别

### [4、索引能干什么?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#4索引能干什么)

索引非常关键，尤其是当表中的数据量越来越大时，索引对于性能的影响愈发重要。 索引能够轻易将查询性能提高好几个数量级，总的来说就是可以明显的提高查询效率。

### [5、创建索引的三种方式](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#5创建索引的三种方式)

在执行 CREATE TABLE 时创建索引

```
CREATE TABLE `employee` (
  `id` int(11) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `age` int(11) DEFAULT NULL,
  `date` datetime DEFAULT NULL,
  `sex` int(1) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_name` (`name`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

使用 ALTER TABLE 命令添加索引

```
ALTER TABLE table_name ADD INDEX index_name (column);
```

使用 CREATE INDEX 命令创建

```
CREATE INDEX index_name ON table_name (column);
```

### [6、varchar 与 char 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#6varchar与char的区别)

**char 的特点**

**1、** char 表示定长字符串，长度是固定的；

**2、** 如果插入数据的长度小于 char 的固定长度时，则用空格填充；

**3、** 因为长度固定，所以存取速度要比 varchar 快很多，甚至能快 50%，但正因为其长度固定，所以会占据多余的空间，是空间换时间的做法；

**4、** 对于 char 来说，最多能存放的字符个数为 255，和编码无关

**varchar 的特点**

**1、** varchar 表示可变长字符串，长度是可变的；

**2、** 插入的数据是多长，就按照多长来存储；

**3、** varchar 在存取方面与 char 相反，它存取慢，因为长度不固定，但正因如此，不占据多余的空间，是时间换空间的做法；

**4、** 对于 varchar 来说，最多能存放的字符个数为 65532

**总之**

结合性能角度（char 更快）和节省磁盘空间角度（varchar 更小），具体情况还需具体来设计数据库才是妥当的做法

### [7、读写分离有哪些解决方案？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#7读写分离有哪些解决方案)

读写分离是依赖于主从复制，而主从复制又是为读写分离服务的。因为主从复制要求`slave`不能写只能读（如果对`slave`执行写操作，那么`show slave status`将会呈现`Slave_SQL_Running=NO`，此时你需要按照前面提到的手动同步一下`slave`）。

**方案一**

使用 MySQL-proxy 代理

**优点：**

直接实现读写分离和负载均衡，不用修改代码，master 和 slave 用一样的帐号，MySQL 官方不建议实际生产中使用

**缺点：**

降低性能， 不支持事务

**方案二**

**1、** 使用 AbstractRoutingDataSource+aop+annotation 在 dao 层决定数据源。

**2、** 如果采用了 mybatis， 可以将读写分离放在 ORM 层，比如 mybatis 可以通过 mybatis plugin 拦截 sql 语句，所有的 insert/update/delete 都访问 master 库，所有的 select 都访问 salve 库，这样对于 dao 层都是透明。 plugin 实现时可以通过注解或者分析语句是读写方法来选定主从库。不过这样依然有一个问题， 也就是不支持事务， 所以我们还需要重写一下 DataSourceTransactionManager， 将 read-only 的事务扔进读库， 其余的有读有写的扔进写库。

**方案三**

**1、** 使用 AbstractRoutingDataSource+aop+annotation 在 service 层决定数据源，可以支持事务.

**2、** 缺点：类内部方法通过 this.xx()方式相互调用时，aop 不会进行拦截，需进行特殊处理。

### [8、什么是幻读，脏读，不可重复读呢？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#8什么是幻读脏读不可重复读呢)

**1、** 事务 A、B 交替执行，事务 A 被事务 B 干扰到了，因为事务 A 读取到事务 B 未提交的数据,这就是**脏读**

**2、** 在一个事务范围内，两个相同的查询，读取同一条记录，却返回了不同的数据，这就是**不可重复读**。

**3、** 事务 A 查询一个范围的结果集，另一个并发事务 B 往这个范围中插入/删除了数据，并静悄悄地提交，然后事务 A 再次查询相同的范围，两次读取得到的结果集不一样了，这就是**幻读**。

### [9、如果一个表有一列定义为 TIMESTAMP，将发生什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#9如果一个表有一列定义为timestamp将发生什么)

每当行被更改时，时间戳字段将获取当前时间戳。

### [10、SQL 优化的一般步骤是什么，怎么看执行计划（explain），如何理解其中各个字段的含义。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题2021年，常见面试题及答案汇总.md#10sql优化的一般步骤是什么怎么看执行计划explain如何理解其中各个字段的含义。)

**1、** show status 命令了解各种 sql 的执行频率

**2、** 通过慢查询日志定位那些执行效率较低的 sql 语句

**3、** explain 分析低效 sql 的执行计划（这点非常重要，日常开发中用它分析 Sql，会大大降低 Sql 导致的线上事故）

### 11、什么是非标准字符串类型？

### 12、主键、外键和索引的区别？

### 13、数据库的乐观锁和悲观锁。

### 14、列的字符串类型可以是什么？

### 15、count(1)、count(\*) 与 count(列名) 的区别？

### 16、可以使用多少列创建索引？

### 17、MYSQL 数据库服务器性能分析的方法命令有哪些?

### 18、什么是死锁？怎么解决？

### 19、聚集索引与非聚集索引的区别

### 20、MySQL 数据库 cpu 飙升到 500%的话他怎么处理？

### 21、InnoDB 存储引擎的锁的算法有三种

### 22、MySQL 有哪些数据类型

### 23、B 树和 B+树的区别，数据库为什么使用 B+树而不是 B 树？

### 24、从锁的类别上分 MySQL 都有哪些锁呢？

### 25、什么是游标？

### 26、SQL 的执行顺序

### 27、事务的隔离级别有哪些？MySQL 的默认隔离级别是什么？

### 28、一条 sql 执行过长的时间，你如何优化，从哪些方面入手？

### 29、FLOAT 和 DOUBLE 的区别是什么？

### 30、什么是存储过程？有哪些优缺点？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
