# Oracle 最新 2023 年面试题附答案解析，大汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、给出在 STAR SCHEMA 中的两种表及它们分别含有的数据](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#1给出在star-schema中的两种表及它们分别含有的数据)

Fact tables 和 dimension tables. fact table 包含大量的主要的信息而 dimension tables 存放对 fact table 某些属性描述的信息

### [2、如何生成 explain plan?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#2如何生成explain-plan)

运行 utlxplan.sql. 建立 plan 表

针对特定 SQL 语句，使用 explain plan set statement_id = 'tst1' into plan_table 运行 utlxplp.sql 或 utlxpls.sql 察看 explain plan

### [3、Oracle 中 function 和 procedure 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#3oracle中function和procedure的区别)

**1、** 可以理解函数是存储过程的一种

**2、** 函数可以没有参数,但是一定需要一个返回值，存储过程可以没有参数,不需要返回值

**3、** 函数 return 返回值没有返回参数模式，存储过程通过 out 参数返回值, 如果需要返回多个参数则建议使用存储过程

**4、** 在 sql 数据操纵语句中只能调用函数而不能调用存储过程

### [4、如何使用 Oracle 的游标？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#4如何使用oracle的游标)

**1、** oracle 中的游标分为显示游标和隐式游标

**2、** 显示游标是用 cursor...is 命令定义的游标，它可以对查询语句(select)返回的多条记录进行处理；隐式游标是在执行插入 (insert)、删除(delete)、修改(update)和返回单条记录的查询(select)语句时由 PL/SQL 自动定义的。

**3、** 显式游标的操作：打开游标、操作游标、关闭游标；PL/SQL 隐式地打开 SQL 游标，并在它内部处理 SQL 语句，然后关闭它

### [5、解释什么是 Oracle Forms?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#5解释什么是oracle-forms)

Oracle Forms 是用于创建与 Oracle 数据库交互的软件产品。它有一个 IDE，包括一个属性表，对象导航器和使用 PL/SQL 的代码编辑器。

### [6、集合操作符](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#6集合操作符)

**1、** Union ： 不包含重复值，默认按第一个查询的第一列升序排列。

**2、** Union All : 完全并集包含重复值。不排序。

**3、** Minus 不包含重复值，不排序。

### [7、说下 oracle 的锁又几种,定义分别是什么;](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#7说下-oracle的锁又几种,定义分别是什么;)

**1、** 行共享锁 (ROW SHARE)

**2、** 行排他锁(ROW EXCLUSIVE)

**3、** 共享锁(SHARE)

**4、** 共享行排他锁(SHARE ROW EXCLUSIVE)

**5、** 排他锁(EXCLUSIVE)

### [8、提到一个项目的“验证 LOV”属性?提到 lov 和 list 项目有什么区别?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#8提到一个项目的“验证lov属性提到lov和list项目有什么区别)

当验证的 LOV 设置为 True 时，Oracle Forms 将文本项的当前值与 LOV 中显示的第一列中的值进行比较。LOV 是列表项的属性。列表项只能有一列，而 lov 可以有一个或多个列。

### [9、FACT Table 上需要建立何种索引？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#9fact-table上需要建立何种索引)

位图索引（bitmap index）

### [10、pctused and pctfree 表示什么含义有什么作用？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Oracle/Oracle最新2021年面试题附答案解析，大汇总.md#10pctused-and-pctfree-表示什么含义有什么作用)

pctused 与 pctfree 控制数据块是否出现在 freelist 中,pctfree 控制数据块中保留用于 update 的空间,当数据块中的 free space 小于 pctfree 设置的空间时，该数据块从 freelist 中去掉,当块由于 dml 操作 free space 大于 pct_used 设置的空间时,该数据库块将被添加在 freelist 链表中。

### 11、描述 tablespace 和 datafile 之间的关系

### 12、列出 Oracle Forms 配置文件?

### 13、如何建立一个备份控制文件？

### 14、oracle 的锁又几种,定义分别是什么;

### 15、Oracle 的游标在存储过程里是放在 begin 与 end 的里面还是外面？

### 16、数据库的三大范式是什么？

### 17、触发器的作用有哪些？

### 18、Oracle 的导入导出有几种方式，有何区别？

### 19、创建用户时，需要赋予新用户什么权限才能使它联上数据库。

### 20、SGA 主要有那些部分，主要作用是什么?

### 21、怎样创建一个一个索引,索引使用的原则,有什么优点和缺点

### 22、如何启动 SESSION 级别的 TRACE

### 23、解释 TABLE Function 的用途

### 24、说下 Oracle 中有哪几种文件？

### 25、解释$$ORACLE_HOME和$$ORACLE_BASE 的区别？

### 26、不借助第三方工具，怎样查看 sql 的执行计划

### 27、如何判断哪个 session 正在连结以及它们等待的资源？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
