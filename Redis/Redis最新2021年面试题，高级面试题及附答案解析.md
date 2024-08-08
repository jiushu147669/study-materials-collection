# Redis 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、Redis 集群方案应该怎么做？都有哪些方案？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#1redis集群方案应该怎么做都有哪些方案)

**1、** codis。

目前用的最多的集群方案，基本和 twemproxy 一致的效果，但它支持在 节点数量改变情况下，旧节点数据可恢复到新 hash 节点。

**2、** Redis cluster3.0 自带的集群，特点在于他的分布式算法不是一致性 hash，而是 hash 槽的概念，以及自身支持节点设置从节点。具体看官方文档介绍。

**3、** 在业务代码层实现，起几个毫无关联的 Redis 实例，在代码层，对 key 进行 hash 计算，然后去对应的 Redis 实例操作数据。 这种方式对 hash 层代码要求比较高，考虑部分包

### [2、Reids 支持的语言：](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#2reids支持的语言：)

java、C、C#、C++、php、Node.js、Go 等。

### [3、怎么测试 Redis 的连通性？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#3怎么测试redis的连通性)

ping

### [4、Redis 集群会有写操作丢失吗？为什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#4redis-集群会有写操作丢失吗为什么)

Redis 并不能保证数据的强一致性，这意味这在实际中集群在特定的条件下可能会丢失写操作。

### [5、Redis 回收使用的是什么算法？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#5redis回收使用的是什么算法)

LRU 算法

### [6、Redis 的并发竞争问题如何解决?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#6redis的并发竞争问题如何解决)

单进程单线程模式，采用队列模式将并发访问变为串行访问。Redis 本身没有锁的概念，Redis 对于多个客户端连接并不存在竞争，利用 setnx 实现锁。

### [7、AOF 常用配置总结](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#7aof常用配置总结)

下面是 AOF 常用的配置项，以及默认值；前面介绍过的这里不再详细介绍。

**1、** appendonly no：是否开启 AOF

**2、** appendfilename "appendonly.aof"：AOF 文件名

**3、** dir ./：RDB 文件和 AOF 文件所在目录

**4、** appendfsync everysec：fsync 持久化策略

**5、** no-appendfsync-on-rewrite no：AOF 重写期间是否禁止 fsync；如果开启该选项，可以减轻文件重写时 CPU 和硬盘的负载（尤其是硬盘），但是可能会丢失 AOF 重写期间的数据；需要在负载和安全性之间进行平衡

**6、** auto-aof-rewrite-percentage 100：文件重写触发条件之一

**7、** auto-aof-rewrite-min-size 64mb：文件重写触发提交之一

**8、** aof-load-truncated yes：如果 AOF 文件结尾损坏，Redis 启动时是否仍载入 AOF 文件

### [8、Redis 管道 Pipeline](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#8redis-管道-pipeline)

在某些场景下我们在**一次操作中可能需要执行多个命令**，而如果我们只是一个命令一个命令去执行则会浪费很多网络消耗时间，如果将命令一次性传输到 `Redis`中去再执行，则会减少很多开销时间。但是需要注意的是 `pipeline`中的命令并不是原子性执行的，也就是说管道中的命令到达 `Redis`服务器的时候可能会被其他的命令穿插

### [9、微信公众号：Java 资讯库，回复“架构”](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#9微信公众号：java资讯库回复“架构)

### [10、Redis 集群方案什么情况下会导致整个集群不可用？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新2021年面试题，高级面试题及附答案解析.md#10redis集群方案什么情况下会导致整个集群不可用)

有 A，B，C 三个节点的集群,在没有复制模型的情况下,如果节点 B 失败了，那么整个集群就会以为缺少 5501-11000 这个范围的槽而不可用。

### 11、Reids 三种不同删除策略

### 12、Redis 集群的主从复制模型是怎样的？

### 13、Redis 如何做大量数据插入？

### 14、都有哪些办法可以降低 Redis 的内存使用情况呢?

### 15、Redis 常见性能问题和解决方案：

### 16、为什么 Redis 需要把所有数据放到内存中？

### 17、分布式 Redis 是前期做还是后期规模上来了再做好？为什么？

### 18、Redis 的持久化机制是什么？各自的优缺点？

### 19、如果有大量的 key 需要设置同一时间过期，一般需要注意什么？

### 20、缓冲内存

### 21、说说 Redis 哈希槽的概念？

### 22、Redis 有哪几种数据淘汰策略？

### 23、Redis 支持哪几种数据类型？

### 24、为什么 Redis 是单线程的？

### 25、Redis 相比 Memcached 有哪些优势：

### 26、Redis 如何设置密码及验证密码？

### 27、，免费领取架构资料。

### 28、Redis 提供 6 种数据淘汰策略：

### 29、Redis Module 实现布隆过滤器

### 30、Redis 集群会有写操作丢失吗？为什么？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
