# Oracle 最新面试题，2023 年面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、说下，内连接，左连接，右连接的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#1说下内连接左连接右连接的区别)

**内连接：**

指主表，从表中符合连接条件的记录全部显示

**左连接：**

外连接方式，主要是显示主表，从表中符合连接条件的记录，并且主表中所有不符合连接条件的记录也要显示。

**右连接：**

外连接方式，主要是显示主表，从表中所有符合连接条件的记录，并且从表中不符合的记录也要显示。

### [2、你必须利用备份恢复数据库，但是你没有控制文件，该如何解决问题呢?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#2你必须利用备份恢复数据库但是你没有控制文件该如何解决问题呢)

重建控制文件，用带 backup control file 子句的 recover 命令恢复数据库。

### [3、解释$$ORACLE_HOME和$$ORACLE_BASE 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#3解释$$oracle_home和$$oracle_base的区别)

ORACLE_BASE 是 oracle 的根目录，ORACLE_HOME 是 oracle 产品的目录。

### [4、说下 oracle 中 dml、ddl、dcl 的使用有哪些](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#4说下-oracle-中-dmlddldcl-的使用有哪些)

**1、** Dml 数据操纵语言，如 select、update、delete，insert

**2、** Ddl 数据定义语言，如 create table 、drop table 等等

**3、** Dcl 数据控制语言， 如 commit、 rollback、grant、 invoke 等

### [5、比较 truncate 和 delete 命令](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#5比较truncate和delete-命令)

两者都可以用来删除表中所有的记录。区别在于：truncate 是 DDL 操作，它移动 HWK，不需要 rollback segment .而 Delete 是 DML 操作, 需要 rollback segment 且花费较长时间.

### [6、如何增加 buffer cache 的命中率?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#6如何增加buffer-cache的命中率)

在数据库较繁忙时，适用 buffer cache advisory 工具，查询 v$db_cache_advice.如果有必要更改，可以使用 alter system set db_cache_size 命令

### [7、Oracle 跟 SQL Server 2005 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#7oracle跟sql-server-2005的区别)

**宏观上：**

**1、** 最大的区别在于平台，oracle 可以运行在不同的平台上，sql server 只能运行在 windows 平台上，由于 windows 平台的稳定性和安全性影响了 sql server 的稳定性和安全性

**2、** oracle 使用的脚本语言为 PL-SQL，而 sql server 使用的脚本为 T-SQL

**微观上：**

**1、** 从数据类型,数据库的结构等等回答

### [8、给出两个检查表结构的方法](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#8给出两个检查表结构的方法)

1.DESCRIBE 命令

**2、** DBMS_METADATA.GET_DDL 包

### [9、什么是绑定变量?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#9什么是绑定变量)

报表 6i 中使用了绑定变量来替换 select 语句中的单个参数。

### [10、如何在 tablespace 里增加数据文件？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题，2021年面试题及答案汇总.md#10如何在tablespace里增加数据文件)

ALTER TABLESPACE <tablespace_name> ADD DATAFILE <datafile_name> SIZE

### 11、truncate 和 delete 区别：

### 12、解释$$ORACLE\_HOME和$$ORACLE_BASE 的区别?

### 13、说明你可以将 FMX 转换或反向回到 FMB 文件吗?

### 14、简单描述 table / segment / extent / block 之间的关系？

### 15、创建数据库时自动建立的 tablespace 名称？

### 16、说下 Oracle 中 function 和 procedure 的区别？

### 17、解释 冷备份 和 热备份 的不同点，以及各自的优点？

### 18、解释 data block , extent 和 segment 的区别？

### 19、给出数据库正常启动所经历的几种状态 ?

### 20、解释 FUNCTION,PROCEDURE 和 PACKAGE 区别

### 21、Oralce 怎样存储文件，能够存储哪些文件？

### 22、解释 CALL_FORM，NEW_FORM 和 OPEN_FORM 之间有什么区别?

### 23、存储过程的操作 当它抛出异常的时候 你是如何解决的用了什么技术

### 24、解释什么是死锁，如何解决 Oracle 中的死锁？

### 25、在 Oracle Forms Report 中，Record 组列的最大长度是多少?什么是不同类型的记录组?

### 26、ORA-01555 的应对方法？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
