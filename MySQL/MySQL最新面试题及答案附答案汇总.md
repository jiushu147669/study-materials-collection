# MySQL 最新面试题及答案附答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、在高并发情况下，如何做到安全的修改同一行数据？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#1在高并发情况下如何做到安全的修改同一行数据)

要安全的修改同一行数据，就要保证一个线程在修改时其它线程无法更新这行记录。一般有悲观锁和乐观锁两种方案~

### [2、索引有哪些优缺点？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#2索引有哪些优缺点)

**索引的优点**

**1、** 可以大大加快数据的检索速度，这也是创建索引的最主要的原因。

**2、** 通过使用索引，可以在查询的过程中，使用优化隐藏器，提高系统的性能。

**索引的缺点**

**1、** 时间方面：创建索引和维护索引要耗费时间，具体地，当对表中的数据进行增加、删除和修改的时候，索引也要动态的维护，会降低增/改/删的执行效率；

**2、** 空间方面：索引需要占物理空间。

### [3、非聚簇索引一定会回表查询吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#3非聚簇索引一定会回表查询吗)

不一定，这涉及到查询语句所要求的字段是否全部命中了索引，如果全部命中了索引，那么就不必再进行回表查询。

**举个简单的例子**

假设我们在员工表的年龄上建立了索引，那么当进行`select age from employee where age < 20`的查询时，在索引的叶子节点上，已经包含了 age 信息，不会再次进行回表查询。

### [4、MySQL 数据库 cpu 飙升的话，要怎么处理呢？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#4mysql数据库cpu飙升的话要怎么处理呢)

**「排查过程：」**

使用 top 命令观察，确定是 MySQLd 导致还是其他原因。

如果是 MySQLd 导致的，show processlist，查看 session 情况，确定是不是有消耗资源的 sql 在运行。

找出消耗高的 sql，看看执行计划是否准确， 索引是否缺失，数据量是否太大。

**「处理：」**

kill 掉这些线程(同时观察 cpu 使用率是否下降)，

进行相应的调整(比如说加索引、改 sql、改内存参数)

重新跑这些 SQL。

**「其他情况：」**

也有可能是每个 sql 消耗资源并不多，但是突然之间，有大量的 session 连进来导致 cpu 飙升，这种情况就需要跟应用一起来分析为何连接数会激增，再做出相应的调整，比如说限制连接数等

### [5、Hash 索引和 B+树区别是什么？你在设计索引是怎么抉择的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#5hash索引和b+树区别是什么你在设计索引是怎么抉择的)

**1、** B+树可以进行范围查询，Hash 索引不能。

**2、** B+树支持联合索引的最左侧原则，Hash 索引不支持。

**3、** B+树支持 order by 排序，Hash 索引不支持。

**4、** Hash 索引在等值查询上比 B+树效率更高。

**5、** B+树使用 like 进行模糊查询的时候，like 后面（比如%开头）的话可以起到优化的作用，Hash 索引根本无法进行模糊查询。

### [6、数据库自增主键可能遇到什么问题。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#6数据库自增主键可能遇到什么问题。)

**1、** 使用自增主键对数据库做分库分表，可能出现诸如主键重复等的问题。解决方案的话，简单点的话可以考虑使用 UUID 哈

**2、** 自增主键会产生表锁，从而引发问题

**3、** 自增主键可能用完问题。

### [7、事务特性：](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#7事务特性：)

（1）原子性：即不可分割性，事务要么全部被执行，要么就全部不被执行。

（2）一致性或可串性。事务的执行使得数据库从一种正确状态转换成另一种正确状态

（3）隔离性。在事务正确提交之前，不允许把该事务对数据的任何改变提供给任何其他事务，

（4） 持久性。事务正确提交后，其结果将永久保存在数据库中，即使在事务提交后有了其他故障，事务的处理结果也会得到保存。

或者这样理解：

事务就是被绑定在一起作为一个逻辑工作单元的 SQL 语句分组，如果任何一个语句操作失败那么整个操作就被失败，以后操作就会回滚到操作前状态，或者是上有个节点。为了确保要么执行，要么不执行，就可以使用事务。要将有组语句作为事务考虑，就需要通过 ACID 测试，即原子性，一致性，隔离性和持久性。

### [8、优化数据库的方法](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#8优化数据库的方法)

**1、** 选取最适用的字段属性，尽可能减少定义字段宽度，尽量把字段设置 NOTNULL，例如’省份’、’性别’最好适用 ENUM

**2、** 使用连接(JOIN)来代替子查询

**3、** 适用联合(UNION)来代替手动创建的临时表

**4、** 事务处理

**5、** 锁定表、优化事务处理

**6、** 适用外键，优化锁定表

**7、** 建立索引

**8、** 优化查询语句

### [9、MySQL 中 int(10)和 char(10)以及 varchar(10)的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#9mysql中int10和char10以及varchar10的区别)

**1、** int(10)的 10 表示显示的数据的长度，不是存储数据的大小；chart(10)和 varchar(10)的 10 表示存储数据的大小，即表示存储多少个字符。

**2、** char(10)表示存储定长的 10 个字符，不足 10 个就用空格补齐，占用更多的存储空间

**3、** varchar(10)表示存储 10 个变长的字符，存储多少个就是多少个，空格也按一个字符存储，这一点是和 char(10)的空格不同的，char(10)的空格表示占位不算一个字符

### [10、简述在 MySQL 数据库中 MyISAM 和 InnoDB 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MySQL/MySQL最新面试题及答案附答案汇总.md#10简述在mysql数据库中myisam和innodb的区别)

**MyISAM：**

不支持事务，但是每次查询都是原子的；

支持表级锁，即每次操作是对整个表加锁；

**存储表的总行数；**

一个 MYISAM 表有三个文件：索引文件、表结构文件、数据文件；

采用菲聚集索引，索引文件的数据域存储指向数据文件的指针。辅索引与主索引基本一致，但是辅索引不用保证唯一性。

**InnoDb：**

支持 ACID 的事务，支持事务的四种隔离级别；

支持行级锁及外键约束：因此可以支持写并发；

**不存储总行数：**

一个 InnoDb 引擎存储在一个文件空间（共享表空间，表大小不受操作系统控制，一个表可能分布在多个文件里），也有可能为多个（设置为独立表空，表大小受操作系统文件大小限制，一般为 2G），受操作系统文件大小的限制；

主键索引采用聚集索引（索引的数据域存储数据文件本身），辅索引的数据域存储主键的值；因此从辅索引查找数据，需要先通过辅索引找到主键值，再访问辅索引；最好使用自增主键，防止插入数据时，为维持 B+树结构，文件的大调整。

### 11、数据库经常使用的函数

### 12、创建索引的三种方式

### 13、优化 UNION 查询

### 14、InnoDB 引擎中的索引策略，了解过吗？

### 15、MySQL 索引使用有哪些注意事项呢？

### 16、一条 SQL 语句在 MySQL 中如何执行的？

### 17、覆盖索引是什么？

### 18、怎样才能找出最后一次插入时分配了哪个自动增量？

### 19、按照锁的粒度分数据库锁有哪些？锁机制与 InnoDB 锁算法

### 20、为表中得字段选择合适得数据类型

### 21、如何通俗地理解三个范式？

### 22、什么叫视图？游标是什么？

### 23、数据库中的事务是什么?

### 24、视图的优点

### 25、MySQL 中 InnoDB 支持的四种事务隔离级别名称，以及逐级之间的区别？

### 26、MySQL 驱动程序是什么？

### 27、MySQL 事务得四大特性以及实现原理

### 28、什么是触发器？触发器的使用场景有哪些？

### 29、InnoDB 与 MyISAM 的区别

### 30、一条 SQL 语句在 MySQL 中如何执行的？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
