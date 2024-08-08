# Oracle 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、说下 怎样创建一个视图,视图的好处, 视图可以控制权限吗?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#1说下-怎样创建一个视图,视图的好处,-视图可以控制权限吗)

create view 视图名 as select 列名 [别名]  …  from 表 [unio [all] select … ] ]

好处：

**1、** 可以简单的将视图理解为 sql 查询语句，视图最大的好处是不占系统空间

**2、** 一些安全性很高的系统，不会公布系统的表结构，可能会使用视图将一些敏感信息过虑或者重命名后公布结构

**3、** 简化查询

**4、** 视图可以控制权限的，在使用的时候需要将视图的使用权限 grant 给用户

### [2、使用存储过程访问数据库比直接用 SQL 语句访问有何优点？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#2使用存储过程访问数据库比直接用sql语句访问有何优点)

**1、** 存储过程是预编译过的，执行时不须编译，执行速度更快。

**2、** 存储过程封装了多条 SQL，便于维护数据的完整性与一致性。

**3、** 实现代码复用。

### [3、当用户进程出错，哪个后台进程负责清理它](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#3当用户进程出错哪个后台进程负责清理它)

PMON

### [4、说下 Oracle 的导入导出有几种方式，有何区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#4说下-oracle的导入导出有几种方式有何区别)

**1、** 使用 oracle 工具 exp/imp

**2、** 使用 plsql 相关工具

方法 1、导入/导出的是二进制的数据，

方法 2、.plsql 导入/导出的是 sql 语句的文本文件

### [5、哪个 VIEW 用来判断 tablespace 的剩余空间](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#5哪个view用来判断tablespace的剩余空间)

DBA_FREE_SPACE

### [6、给出两个检查表结构的方法](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#6给出两个检查表结构的方法)

**1、** DESCRIBE 命令

**2、**  DBMS_METADATA.GET_DDL 包

### [7、ORA-01555 的应对方法?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#7ora-01555的应对方法)

具体的出错信息是 snapshot too old within rollback seg , 通常可以通过增大 rollback seg 来解决问题。当然也需要察看一下具体造成错误的 SQL 文本

### [8、解释 data block , extent 和 segment 的区别（这里建议用英文术语）](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#8解释data-block-,-extent-和-segment的区别这里建议用英文术语)

data block 是数据库中最小的逻辑存储单元。当数据库的对象需要更多的物理存储空间时，连续的 data block 就组成了 extent . 一个数据库对象拥有的所有 extents 被称为该对象的 segment.

### [9、解释冷备份和热备份的不同点以及各自的优点](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#9解释冷备份和热备份的不同点以及各自的优点)

热备份针对归档模式的数据库，在数据库仍旧处于工作状态时进行备份。而冷备份指在数据库关闭后，进行备份，适用于所有模式的

数据库。热备份的优点在于当备份时，数据库仍旧可以被使用并且可以将数据库恢复到任意一个时间点。冷备份的优点在于它的备份和恢复

操作相当简单，并且由于冷备份的数据库可以工作在非归档模式下,数据库性能会比归档模式稍好。（因为不必将 archive log 写入硬盘）

### [10、TEMPORARY tablespace 和 PERMANENT tablespace 的区别是？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新面试题2021年，常见面试题及答案汇总.md#10temporary-tablespace和permanent-tablespace-的区别是)

A temporary tablespace 用于临时对象例如排序结构而 permanent tablespaces 用来存储那些'真实'的对象(例如表，回滚段等)

### 11、事务的特性（ACID）是指什么？

### 12、说一下，什么是 Oracle 分区

### 13、在千万级的数据库查询中，如何提高效率？

### 14、索引是用来干什么的？有那些约束建立索引？

### 15、怎样查看数据库引擎的报错

### 16、哪个 column 可以用来区别 V$$视图和GV$$视图?

### 17、哪个 column 可以用来区别 V$$视图和GV$$视图?

### 18、如何判断数据库的时区？

### 19、比较 truncate 和 delete 命令

### 20、如何生成 explain plan?

### 21、举出两个判断 DDL 改动的方法？

### 22、解释 Oracle 表单服务组件包括什么?

### 23、解释 GLOBAL_NAMES 设为 TRUE 的用途？

### 24、解释 materialized views 的作用

### 25、如何增加 buffer cache 的命中率？

### 26、你刚刚编译了一个 PL/SQL Package 但是有错误报道，如何显示出错信息？

### 27、简述 oracle 中 dml、ddl、dcl 的使用

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
