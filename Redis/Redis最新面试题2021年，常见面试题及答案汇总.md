# Redis 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、Redis 如何做内存优化？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#1redis如何做内存优化)

尽可能使用散列表（hashes），散列表（是说散列表里面存储的数少）使用的内存非常小，所以你应该尽可能的将你的数据模型抽象到一个散列表里面。比如你的 web 系统中有一个用户对象，不要为这个用户的名称，姓氏，邮箱，密码设置单独的 key,而是应该把这个用户的所有信息存储到一张散列表里面.

### [2、Pipeline 有什么好处，为什么要用 pipeline？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#2pipeline有什么好处为什么要用pipeline)

可以将多次 IO 往返的时间缩减为一次，前提是 pipeline 执行的指令之间没有因果相关性。使用 Redis-benchmark 进行压测的时候可以发现影响 Redis 的 QPS 峰值的一个重要因素是 pipeline 批次指令的数目。

### [3、Redis 常用管理命令](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#3redis常用管理命令)

```
# dbsize 返回当前数据库 key 的数量。
# info 返回当前 Redis 服务器状态和一些统计信息。
# monitor 实时监听并返回Redis服务器接收到的所有请求信息。
# shutdown 把数据同步保存到磁盘上，并关闭Redis服务。
# config get parameter 获取一个 Redis 配置参数信息。（个别参数可能无法获取）
# config set parameter value 设置一个 Redis 配置参数信息。（个别参数可能无法获取）
# config resetstat 重置 info 命令的统计信息。（重置包括：keyspace 命中数、
# keyspace 错误数、 处理命令数，接收连接数、过期 key 数）
# debug object key 获取一个 key 的调试信息。
# debug segfault 制造一次服务器当机。
# flushdb 删除当前数据库中所有 key,此方法不会失败。小心慎用
# flushall 删除全部数据库中所有 key，此方法不会失败。小心慎用
```

### [4、Redis 持久化数据和缓存怎么做扩容？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#4redis持久化数据和缓存怎么做扩容)

1. 如果 Redis 被当做缓存使用，使用一致性哈希实现动态扩容缩容。
2. 如果 Redis 被当做一个持久化存储使用，必须使用固定的 keys-to-nodes 映射关系，节点的数量一旦确定不能变化。否则的话(即 Redis 节点需要动态变化的情况），必须使用可以在运行时进行数据再平衡的一套系统，而当前只有 Redis 集群可以做到这样。

### [5、Twemproxy 是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#5twemproxy是什么)

Twemproxy 是 Twitter 维护的（缓存）代理系统，代理 Memcached 的 ASCII 协议和 Redis 协议。它是单线程程序，使用 c 语言编写，运行起来非常快。它是采用 Apache 2.0 license 的开源软件。 Twemproxy 支持自动分区，如果其代理的其中一个 Redis 节点不可用时，会自动将该节点排除（这将改变原来的 keys-instances 的映射关系，所以你应该仅在把 Redis 当缓存时使用 Twemproxy)。 Twemproxy 本身不存在单点问题，因为你可以启动多个 Twemproxy 实例，然后让你的客户端去连接任意一个 Twemproxy 实例。 Twemproxy 是 Redis 客户端和服务器端的一个中间层，由它来处理分区功能应该不算复杂，并且应该算比较可靠的。

### [6、Redis 没有直接使用 C 字符串](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#6redis没有直接使用c字符串)

(即以空字符’\0’结尾的字符数组)作为默认的字符串表示，而是使用了 SDS。SDS 是简单动态字符串(Simple Dynamic String)的缩写。

### [7、使用过 Redis 分布式锁么，它是什么回事？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#7使用过-redis-分布式锁么它是什么回事)

先拿 setnx 来争抢锁， 抢到之后， 再用 expire 给锁加一个过期时间防止锁忘记了释放。

这时候对方会告诉你说你回答得不错， 然后接着问如果在 setnx 之后执行 expire 之前进程意外 crash 或者要重启维护了， 那会怎么样？

这时候你要给予惊讶的反馈： 唉， 是喔， 这个锁就永远得不到释放了。紧接着你需要抓一抓自己得脑袋， 故作思考片刻， 好像接下来的结果是你主动思考出来的， 然后回我记得 set 指令有非常复杂的参数， 这个应该是可以同时把 setnx 和 expire 合成一条指令来用的！ 对方这时会显露笑容， 心里开始默念： 摁， 这小子还不错。

### [8、Redis 如何设置密码及验证密码？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#8redis如何设置密码及验证密码)

设置密码：config set requirepass 123456

授权密码：auth 123456

### [9、一个 Redis 实例最多能存放多少的 keys？List、Set、Sorted Set 他们最多能存放多少元素?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#9一个-redis-实例最多能存放多少的-keyslistsetsorted-set-他们最多能存放多少元素)

理论上 Redis 可以处理多达 232 的 keys，并且在实际中进行了测试，每个实例至少存放了 2 亿 5 千万的 keys。我们正在测试一些较大的值。任何 list、set、和 sorted set 都可以放 232 个元素。换句话说， Redis 的存储极限是系统中的可用内存值。

### [10、Redis 有哪些适合的场景？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Redis/Redis最新面试题2021年，常见面试题及答案汇总.md#10redis有哪些适合的场景)

**会话缓存（Session Cache）**

最常用的一种使用 Redis 的情景是会话缓存（sessioncache），用 Redis 缓存会话比其他存储（如 Memcached）的优势在于：Redis 提供持久化。当维护一个不是严格要求一致性的缓存时，如果用户的购物车信息全部丢失，大部分人都会不高兴的，现在，他们还会这样吗？

幸运的是，随着 Redis 这些年的改进，很容易找到怎么恰当的使用 Redis 来缓存会话的文档。甚至广为人知的商业平台 Magento 也提供 Redis 的插件。

**全页缓存（FPC）**

除基本的会话 token 之外，Redis 还提供很简便的 FPC 平台。回到一致性问题，即使重启了 Redis 实例，因为有磁盘的持久化，用户也不会看到页面加载速度的下降，这是一个极大改进，类似 PHP 本地 FPC。

再次以 Magento 为例，Magento 提供一个插件来使用 Redis 作为全页缓存后端。

此外，对 WordPress 的用户来说，Pantheon 有一个非常好的插件 wp-Redis，这个插件能帮助你以最快速度加载你曾浏览过的页面。

**队列**

Reids 在内存存储引擎领域的一大优点是提供 list 和 set 操作，这使得 Redis 能作为一个很好的消息队列平台来使用。Redis 作为队列使用的操作，就类似于本地程序语言（如 Python）对 list 的 push/pop 操作。

如果你快速的在 Google 中搜索“Redis queues”，你马上就能找到大量的开源项目，这些项目的目的就是利用 Redis 创建非常好的后端工具，以满足各种队列需求。例如，Celery 有一个后台就是使用 Redis 作为 broker，你可以从这里去查看。

**排行榜/计数器**

Redis 在内存中对数字进行递增或递减的操作实现的非常好。集合（Set）和有序集合（SortedSet）也使得我们在执行这些操作的时候变的非常简单，Redis 只是正好提供了这两种数据结构。

所以，我们要从排序集合中获取到排名最靠前的 10 个用户–我们称之为“user_scores”，我们只需要像下面一样执行即可：

当然，这是假定你是根据你用户的分数做递增的排序。如果你想返回用户及用户的分数，你需要这样执行：

ZRANGE user_scores 0 10 WITHSCORES

Agora Games 就是一个很好的例子，用 Ruby 实现的，它的排行榜就是使用 Redis 来存储数据的，你可以在这里看到。

**发布/订阅**

最后（但肯定不是最不重要的）是 Redis 的发布/订阅功能。发布/订阅的使用场景确实非常多。我已看见人们在社交网络连接中使用，还可作为基于发布/订阅的脚本触发器，甚至用 Redis 的发布/订阅功能来建立聊天系统！

### 11、说说 Redis 哈希槽的概念？

### 12、使用 Redis 有哪些好处？

### 13、Redis 支持的 Java 客户端都有哪些？官方推荐用哪个？

### 14、怎么测试 Redis 的连通性？

### 15、Redis 过期键的删除策略？

### 16、Redis 是单线程的，如何提高多核 CPU 的利用率？

### 17、Redis 的持久化机制是什么？各自的优缺点？

### 18、Redis key 的过期时间和永久有效分别怎么设置？

### 19、Redis 通讯协议

### 20、是否使用过 Redis 集群，集群的原理是什么？

### 21、Redis 相比 Memcached 有哪些优势？

### 22、惰性删除

### 23、怎么测试 Redis 的连通性？

### 24、Redis 有哪几种数据淘汰策略？

### 25、Redis 的数据类型？

### 26、Redis 集群方案应该怎么做？都有哪些方案？

### 27、怎么理解 Redis 事务？

### 28、Redis 和 Redisson 有什么关系？

### 29、Redis 是单线程

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
