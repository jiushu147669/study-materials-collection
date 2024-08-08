# Oracle 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、如何重构索引？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#1如何重构索引)

ALTER INDEX <index_name> REBUILD;

### [2、说说 Oracle 中经常使用到的函数](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#2说说oracle中经常使用到的函数)

length 长度、lower 小写、upper 大写、to_date 转化日期、to_char 转化字符、to_number 转化数字 Ltrim 去左边空格、rtrim 去右边空格、substr 截取字符串、add_month 增加或减掉月份、

### [3、解释 data block , extent 和 segment 的区别(这里建议用英文术语)](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#3解释data-block-,-extent-和-segment的区别这里建议用英文术语)

data block 是数据库中最小的逻辑存储单元。当数据库的对象需要更多的物理存储空间时，连续的 data block 就组成了 extent . 一个数据库对象拥有的所有 extents 被称为该对象的 segment.

### [4、给出数据库正常启动所经历的几种状态 ?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#4给出数据库正常启动所经历的几种状态-)

STARTUP NOMOUNT ?C 数据库实例启动

STARTUP MOUNT - 数据库装载

STARTUP OPEN ?C 数据库打开

### [5、如何转换 init.ora 到 spfile?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#5如何转换initora到spfile)

使用 create spfile from pfile 命令.

### [6、举出 3 种可以收集 three advisory statistics](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#6举出3种可以收集three-advisory-statistics)

Buffer Cache Advice, Segment Level Statistics, Timed Statistics

### [7、哪个 VIEW 用来检查数据文件的大小？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#7哪个view用来检查数据文件的大小)

DBA_DATA_FILES

### [8、回滚段的作用是什么](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#8回滚段的作用是什么)

事务回滚：当事务修改表中数据的时候，该数据修改前的值(即前影像)会存放在回滚段中，当用户回滚事务(ROLLBACK)时，ORACLE 将会利用回滚段中的数据前影像来将修改的数据恢复到原来的值。

事务恢复：当事务正在处理的时候，例程失败，回滚段的信息保存在 undo 表空间中，ORACLE 将在下次打开数据库时利用回滚来恢复未提交的数据。

**1、** 读一致性：当一个会话正在修改数据时，其他的会话将看不到该会话未提交的修改。

**2、** 当一个语句正在执行时，该语句将看不到从该语句开始执行后的未提交的修改(语句级读一致性)。

**3、** 当 ORACLE 执行 Select 语句时，ORACLE 依照当前的系统改变号(SYSTEM CHANGE NUMBER-SCN)。

**4、** 来保证任何前于当前 SCN 的未提交的改变不被该语句处理。可以想象：当一个长时间的查询正在执行时。

**5、** 若其他会话改变了该查询要查询的某个数据块，ORACLE 将利用回滚段的数据前影像来构造一个读一致性视图。

### [9、你必须利用备份恢复数据库，但是你没有控制文件，该如何解决问题呢？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#9你必须利用备份恢复数据库但是你没有控制文件该如何解决问题呢)

重建控制文件，用带 backup control file 子句的 recover 命令恢复数据库。

### [10、如何变动数据文件的大小？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题，高级面试题及附答案解析.md#10如何变动数据文件的大小)

ALTER DATABASE DATAFILE <datafile_name> RESIZE <new_size>;

### 11、解释 data block , extent 和 segment 的区别（这里建议用英文术语）

### 12、存储过程 、函数 、游标 在项目中怎么用的：

### 13、用于网络连接的 2 个文件？

### 14、如何转换 init.ora 到 spfile?

### 15、给出在 STAR SCHEMA 中的两种表及它们分别含有的数据

### 16、提示窗体中触发的顺序是什么?

### 17、如何在不影响子表的前提下，重建一个母表

### 18、解释什么是 Partitioning（分区）以及它的优点。

### 19、如何建立一个备份控制文件?

### 20、解释冷备份和热备份的不同点以及各自的优点

### 21、解释归档和非归档模式之间的不同和它们各自的优缺点

### 22、如何进行强制 LOG SWITCH?

### 23、如何生成 explain plan?

### 24、说明如何使用相同的 LOV 2 列?

### 25、Coalescing 做了什么？

### 26、ORA-01555 的应对方法？

### 27、解释什么是死锁，如何解决 Oracle 中的死锁？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
