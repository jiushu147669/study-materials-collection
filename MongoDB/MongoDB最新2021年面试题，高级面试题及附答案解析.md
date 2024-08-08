# MongoDB 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、ObjectID"有哪些部分组成](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#1objectid"有哪些部分组成)

一共有四部分组成:时间戳、客户端 ID、客户进程 ID、三个字节的增量计数器

### [2、当我试图更新一个正在被迁移的块(chunk)上的文档时会发生什么?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#2当我试图更新一个正在被迁移的块chunk上的文档时会发生什么)

更新操作会立即发生在旧的分片(shard)上,然后更改才会在所有权转移(ownership transfers)前复制到新的分片上.

### [3、为什么要在 MongoDB 中使用分析器](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#3为什么要在mongodb中使用分析器)

mongodb 中包括了一个可以显示数据库中每个操作性能特点的数据库分析器.通过这个分析器你可以找到比预期慢

的查询(或写操作);利用这一信息,比如,可以确定是否需要添加索引.

### [4、解释一下 MongoDB 中的索引是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#4解释一下mongodb中的索引是什么)

索引是 MongoDB 中的特殊结构，它以易于遍历的形式存储一小部分数据集。索引按索引中指定的字段的值排序，存储特定字段或一组字段的值。

### [5、什么是集合(表)](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#5什么是集合表)

集合就是一组 MongoDB 文档。它相当于关系型数据库（RDBMS）中的表这种概念。集合位于单独的一个数据库中。

一个集合内的多个文档可以有多个不同的字段。一般来说，集合中的文档都有着相同或相关的目的。

### [6、提到如何检查函数的源代码？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#6提到如何检查函数的源代码)

要检查没有任何括号的函数源代码，必须调用该函数。

### [7、什么是 NoSQL 数据库？NoSQL 和 RDBMS 有什么区别？在哪些情况下使用和不使用 NoSQL 数据库？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#7什么是nosql数据库nosql和rdbms有什么区别在哪些情况下使用和不使用nosql数据库)

NoSQL 是非关系型数据库，NoSQL = Not Only SQL。

关系型数据库采用的结构化的数据，NoSQL 采用的是键值对的方式存储数据。 在处理非结构化/半结构化的大数据时；在水平方向上进行扩展时；随时应对动态增加的数据项时可以优先考虑

使用 NoSQL 数据库。 在考虑数据库的成熟度；支持；分析和商业智能；管理及专业性等问题时，应优先考虑关系型数据库。

### [8、提及插入文档的命令语法是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#8提及插入文档的命令语法是什么)

用于插入文档的命令语法是 database.collection.insert（文档）。

### [9、如果在一个分片(shard)停止或者很慢的时候,我发起一个查询会怎样?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#9如果在一个分片shard停止或者很慢的时候,我发起一个查询会怎样)

如果一个分片(shard)停止了,除非查询设置了“partial”选项,否则查询会返回一个错误.如果一个分片(shard)响应很慢,mongodb 则会等待它的响应.

### [10、如何执行事务/加锁？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/MongoDB/MongoDB最新2021年面试题，高级面试题及附答案解析.md#10如何执行事务/加锁)

因为 mongodb 设计就是轻量高性能，所以没有传统的锁和复杂的事务的回滚

### 11、更新数据

### 12、如何执行事务/加锁?

### 13、monogodb 中的分片什么意思

### 14、查看 Mongos 使用的连接？

### 15、nosql 数据库有哪些

### 16、分片（sharding）和复制（replication）是怎样工作的？

### 17、解释什么是 MongoDB 中的 GridFS？

### 18、mongodb 的结构介绍

### 19、什么是 MongoDB 中的“命名空间”？

### 20、我应该启动一个集群分片(sharded)还是一个非集群分片的 mongodb 环境?

### 21、什么是 master 或 primary？

### 22、什么是文档(记录)

### 23、说明 Profiler 在 MongoDB 中的作用是什么？

### 24、使用 mongodb 的优点

### 25、为什么 mongodb 的数据文件那么庞大

### 26、分析器在 MongoDB 中的作用是什么?

### 27、允许空值 null 吗?

### 28、为什么要在 MongoDB 中用"Code"数据类型

### 29、在 MongoDB 中什么是副本集（避免单点故障）

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
