# Oracle 最新 2023 年面试题大汇总，附答案

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、FACT Table 上需要建立何种索引?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#1fact-table上需要建立何种索引)

位图索引 (bitmap index)

### [2、给出两种相关约束?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#2给出两种相关约束)

主键和外键

### [3、解释归档和非归档模式之间的不同和它们各自的优缺点](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#3解释归档和非归档模式之间的不同和它们各自的优缺点)

归档模式是指你可以备份所有的数据库 transactions 并恢复到任意一个时间点。非归档模式则相反，不能恢复到任意一个时间点。

但是非归档模式可以带来数据库性能上的少许提高

### [4、delete 与 Truncate 区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#4delete-与truncate区别)

**1、** Truncate 是 DDL 语句，DELETE 是 DML 语句。

**2、** Truncate 的速度远快于 DELETE；

原因是： 当执行 DELETE 操作时所有表数据先被 COPY 到回滚表空间，数据量不同花费时间长短不一。而 TRUNCATE 是直接删除数据不进回滚表空间。

**1、** delete 数据可以运行 Rollback 进行数据回滚。而 Truncate 则是永久删除不能回滚。

**2、** Truncate 操作不会触发表上的 delete 触发器，而 delete 会正常触发。

**3、** Truncate 语句不能带 where 条件意味着只能全部数据删除，而 DELETE 可带 where 条件进行删除数据。

**4、** Truncate 操作会重置表的高水位线（High Water Mark）,而 delete 不会。

### [5、哪个后台进程刷新 materialized views?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#5哪个后台进程刷新materialized-views)

The Job Queue Processes.

### [6、MySQL 数据库与 Oracle 数据库有什么区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#6mysql数据库与oracle-数据库有什么区别)

**1、** 应用方面，MySQL 是中小型应用的数据库。一般用于个人和中小型企业。Oracle 属于大型数据库，一般用于具有相当规模的企业应用。

**2、** 自动增长的数据类型方面： MySQL 有自动增长的数据类型。Oracle 没有自动增长的数据类型。需要建立一个自增序列。

**3、** group by 用法： MySQL 中 group by 在 SELECT 语句中可以随意使用，但在 ORACLE 中如果查询语句中有组函数，那么其他列必须是组函数处理过的或者是 group by 子句中的列，否则会报错。

**4、** 引导方面： MySQL 中可以用单引号、双引号包起字符串，Oracle 中只可以用单引号包起字符串

### [7、Oracle 分区在什么情况下使用](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#7oracle-分区在什么情况下使用)

当一张表的数据量到达上亿行的时候，表的性能会严重降低，这个时候就需要用到分区了，通过划分成多个小表，并在每个小表上建立本地索引可以大大缩小索引数据文件的大小，从而更快的定位到目标数据来提升访问性能。

分区除了可以用来提升访问性能外，还因为可以指定分区所使用的表空间，因此也用来做数据的生命周期管理。当前需要频繁使用的活跃数据可以放到访问速度更快但价格也更贵的存储设备上，而 2、3 年前的历史数据，或者叫冷数据可以放到更廉价、速度更低的设备上。从而降低存储费用。

### [8、oracle 中存储过程，游标和函数的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#8oracle中存储过程游标和函数的区别)

**1、** 游标类似指针，游标可以执行多个不相关的操作.如果希望当产生了结果集后,对结果集中的数据进行多 种不相关的数据操作

**2、** 函数可以理解函数是存储过程的一种； 函数可以没有参数,但是一定需要一个返回值，存储过程可以没有参数,不需要返回值；两者都可以通过 out 参数返回值, 如果需要返回多个

**3、** 参数则建议使用存储过程；在 sql 数据操纵语句中只能调用函数而不能调用存储过程

### [9、如何增加 buffer cache 的命中率？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#9如何增加buffer-cache的命中率)

在数据库较繁忙时，适用 buffer cache advisory 工具，查询 v$db_cache_advice . 如果有必要更改，可以使用 alter system set

db_cache_size 命令

### [10、使用索引的理由](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题大汇总，附答案.md#10使用索引的理由)

快速访问表中的 data block

### 11、如何搜集表的各种状态数据？

### 12、FACT Table 上需要建立何种索引？

### 13、提及 11g 版本 2 中 Oracle Forms Services 中引入的新功能是什么?

### 14、说下如何使用 Oracle 的游标？

### 15、比较 truncate 和 delete 命令

### 16、如何判断谁往表里增加了一条纪录？

### 17、说一下，Oracle 的分区有几种

### 18、可以从表单执行动态 SQL 吗?

### 19、解释冷备份和热备份的不同点以及各自的优点

### 20、日志的作用是什么

### 21、说明如何在指定的块中迭代项目和记录?

### 22、描述什么是 redo logs

### 23、如何定位重要(消耗资源多)的 SQL

### 24、给出两个检查表结构的方法

### 25、如何加密 PL/SQL 程序？

### 26、本地管理表空间和字典管理表空间的特点，ASSM 有什么特点？

### 27、Audit trace 存放在哪个 oracle 目录结构中?

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
