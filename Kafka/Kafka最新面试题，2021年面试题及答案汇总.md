# Kafka 最新面试题，2023 年面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、监控 Kafka 的框架都有哪些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#1监控kafka的框架都有哪些)

对于 SRE 来讲，依然是送分题。但基础的我们要知道，Kafka 本身是提供了 JMX（Java Management Extensions）的，我们可以通过它来获取到 Kafka 内部的一些基本数据。

**1、** Kafka Manager：更多是 Kafka 的管理，对于 SRE 非常友好，也提供了简单的瞬时指标监控。

**2、** Kafka Monitor：LinkedIn 开源的免费框架，支持对集群进行系统测试，并实时监控测试结果。

**3、** CruiseControl：也是 LinkedIn 公司开源的监控框架，用于实时监测资源使用率，以及提供常用运维操作等。无 UI 界面，只提供 REST API，可以进行多集群管理。

**4、** JMX 监控：由于 Kafka 提供的监控指标都是基于 JMX 的，因此，市面上任何能够集成 JMX 的框架都可以使用，比如 Zabbix 和 Prometheus。

**5、** 已有大数据平台自己的监控体系：像 Cloudera 提供的 CDH 这类大数据平台，天然就提供 Kafka 监控方案。

**6、** JMXTool：社区提供的命令行工具，能够实时监控 JMX 指标。可以使用 Kafka-run-class.sh Kafka.tools.JmxTool 来查看具体的用法。

### [2、Kafka 的主要 API 有哪些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#2kafka的主要api有哪些)

Apache Kafka 有 4 个主要 API：

生产者 API 消费者 API 流 API 连接器 API

### [3、解释领导者和追随者的概念。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#3解释领导者和追随者的概念。)

在 Kafka 的每个分区中，都有一个服务器充当领导者，0 到多个服务器充当追随者的角色。

### [4、Kafka 如何实现延迟队列?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#4kafka-如何实现延迟队列)

Kafka 并没有使用 JDK 自带的 Timer 或者 DelayQueue 来实现延迟的功能，而是**基于时间轮自定义了一个用于实现延迟功能的定时器（SystemTimer）**。JDK 的 Timer 和 DelayQueue 插入和删除操作的平均时间复杂度为 O(nlog(n))，并不能满足 Kafka 的高性能要求，而基于时间轮可以将插入和删除操作的时间复杂度都降为**O(1)**。时间轮的应用并非 Kafka 独有，其应用场景还有很多，在 Netty、Akka、Quartz、Zookeeper 等组件中都存在时间轮的踪影。

底层使用数组实现，数组中的每个元素可以存放一个 TimerTaskList 对象。TimerTaskList 是一个环形双向链表，在其中的链表项 TimerTaskEntry 中封装了真正的定时任务 TimerTask.

Kafka 中到底是怎么推进时间的呢？Kafka 中的定时器借助了 JDK 中的 DelayQueue 来协助推进时间轮。具体做法是对于每个使用到的 TimerTaskList 都会加入到 DelayQueue 中。**Kafka 中的 TimingWheel 专门用来执行插入和删除 TimerTaskEntry 的操作，而 DelayQueue 专门负责时间推进的任务**。再试想一下，DelayQueue 中的第一个超时任务列表的 expiration 为 200ms，第二个超时任务为 840ms，这里获取 DelayQueue 的队头只需要 O(1)的时间复杂度。如果采用每秒定时推进，那么获取到第一个超时的任务列表时执行的 200 次推进中有 199 次属于“空推进”，而获取到第二个超时任务时有需要执行 639 次“空推进”，这样会无故空耗机器的性能资源，这里采用 DelayQueue 来辅助以少量空间换时间，从而做到了“精准推进”。Kafka 中的定时器真可谓是“知人善用”，用 TimingWheel 做最擅长的任务添加和删除操作，而用 DelayQueue 做最擅长的时间推进工作，相辅相成。

### [5、为什么 Kafka 不支持读写分离？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#5为什么kafka不支持读写分离)

在 Kafka 中，生产者写入消息、消费者读取消息的操作都是与 leader 副本进行交互的，从 而实现的是一种**主写主读**的生产消费模型。

Kafka 并不支持主写从读，因为主写从读有 2 个很明 显的缺点:

**数据一致性问题**。数据从主节点转到从节点必然会有一个延时的时间窗口，这个时间 窗口会导致主从节点之间的数据不一致。某一时刻，在主节点和从节点中 A 数据的值都为 X， 之后将主节点中 A 的值修改为 Y，那么在这个变更通知到从节点之前，应用读取从节点中的 A 数据的值并不为最新的 Y，由此便产生了数据不一致的问题。

**延时问题**。类似 Redis 这种组件，数据从写入主节点到同步至从节点中的过程需要经 历网络 → 主节点内存 → 网络 → 从节点内存这几个阶段，整个过程会耗费一定的时间。而在 Kafka 中，主从同步会比 Redis 更加耗时，它需要经历网络 → 主节点内存 → 主节点磁盘 → 网络 → 从节 点内存 → 从节点磁盘这几个阶段。对延时敏感的应用而言，主写从读的功能并不太适用。

### [6、Kafka 消息是采用 Pull 模式，还是 Push 模式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#6kafka-消息是采用-pull-模式还是-push-模式)

Kafka 最初考虑的问题是，customer 应该从 brokes 拉取消息还是 brokers 将消息推送到

consumer，也就是 pull 还 push。在这方面，Kafka 遵循了一种大部分消息系统共同的传统

的设计：

producer 将消息推送到 broker，consumer 从 broker 拉取消息

一些消息系统比如 Scribe 和 Apache Flume 采用了 push 模式，将消息推送到下游的

consumer。

这样做有好处也有坏处：由 broker 决定消息推送的速率，对于不同消费速率的

consumer 就不太好处理了。消息系统都致力于让 consumer 以最大的速率最快速的消费消

息，但不幸的是，push 模式下，当 broker 推送的速率远大于 consumer 消费的速率时，

consumer 恐怕就要崩溃了。最终 Kafka 还是选取了传统的 pull 模式

Pull 模式的另外一个好处是 consumer 可以自主决定是否批量的从 broker 拉取数据。Push

模式必须在不知道下游 consumer 消费能力和消费策略的情况下决定是立即推送每条消息还

是缓存之后批量推送。如果为了避免 consumer 崩溃而采用较低的推送速率，将可能导致一

次只推送较少的消息而造成浪费。Pull 模式下，consumer 就可以根据自己的消费能力去决

定这些策略

Pull 有个缺点是，如果 broker 没有可供消费的消息，将导致 consumer 不断在循环中轮询，

直到新消息到 t 达。为了避免这点，Kafka 有个参数可以让 consumer 阻塞知道新消息到达

(当然也可以阻塞知道消息的数量达到某个特定的量这样就可以批量发

### [7、为什么要使用 Apache Kafka 集群？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#7为什么要使用apache-kafka集群)

为了克服收集大量数据和分析收集数据的挑战，我们需要一个消息队列系统。因此 Apache Kafka 应运而生。其好处是：只需存储/发送事件以进行实时处理，就可以跟踪 Web 活动。通过这一点，我们可以发出警报并报告操作指标。此外，我们可以将数据转换为标准格式。此外，它允许对主题的流数据进行连续处理。由于它的广泛使用，它秒杀了竞品，如 ActiveMQ，RabbitMQ 等。

### [8、Kafka 中的 ISR、AR 又代表什么？ISR 的伸缩又指什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#8kafka中的-israr-又代表什么isr-的伸缩又指什么)

**ISR**：In-Sync Replicas 副本同步队列；ISR 是由 leader 维护，follower 从 leader 同步数据有一些延迟（包括延迟时间 replica.lag.time.max.ms 和延迟条数 replica.lag.max.messages 两个维度, 版本 0.10.x 中只支持 replica.lag.time.max.ms 这个维度），任意一个超过阈值都会把 follower 剔除出 ISR, 存入 OSR（Outof-Sync Replicas）列表，新加入的 follower 也会先存放在 OSR 中。AR=ISR+OSR。

**AR**：Assigned Replicas 所有副本；

### [9、Kafka Producer 写数据，ACK 为 0，1，-1 时分别代表什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#9kafka-producer-写数据ack-为-01-1-时分别代表什么)

1（默认） 数据发送到 Kafka 后，经过 leader 成功接收消息的的确认，就算是发送成功了。在这种情况下，如果 leader 宕机了，则会丢失数据。

0 生产者将数据发送出去就不管了，不去等待任何返回。这种情况下数据传输效率最高，但是数据可靠性确是最低的。

-1 producer 需要等待 ISR 中的所有 follower 都确认接收到数据后才算一次发送完成，可靠性最高。

### [10、Leader 总是-1，怎么破？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题，2021年面试题及答案汇总.md#10leader总是-1怎么破)

**1、** 对于有经验的 SRE 来讲，早期的 Kafka 版本应该多多少少都遇到过该种情况，通常情况下就是 Controller 不工作了，导致无法分配 leader，那既然知道问题后，解决方案也就很简单了。重启 Controller 节点上的 Kafka 进程，让其他节点重新注册 Controller 角色，但是如上面 ZooKeeper 的作用，你要知道为什么 Controller 可以自动注册。

**2、** 当然了，当你知道 controller 的注册机制后，你也可以说：删除 ZooKeeper 节点/controller，触发 Controller 重选举。Controller 重选举能够为所有主题分区重刷分区状态，可以有效解决因不一致导致的 Leader 不可用问题。但是，需要注意的是，直接操作 ZooKeeper 是一件风险很大的操作，就好比在 Linux 中执行了 rm -rf /xxx 一样，如果在/和 xxx 之间不小心多了几个空格，那”恭喜你”，今年白干了。

### 11、kafaka 生产数据时数据的分组策略

### 12、Kafka 和 Flume 之间的主要区别是什么？

### 13、Kafka 的设计时什么样的呢？

### 14、ZooKeeper 在 Kafka 中的作用是什么？

### 15、为什么 Kafka 技术很重要？

### 16、：21, 23, 25, 26, 27, 28, 29, 30Apache Kafka 对于有经验的人的面试

### 17、Kafka Producer API 的作用是什么？

### 18、Kafa consumer 是否可以消费指定分区消息？

### 19、如果 Leader Crash 时，ISR 为空怎么办

### 20、什么是消费者或用户？

### 21、解释如何调整 Kafka 以获得最佳性能。

### 22、你能用 Kafka 做什么？

### 23、Kafka 的优点有那些？

### 24、Kafka 的一些最显著的应用。

### 25、生产者和消费者的命令行是什么？

### 26、如何获取 topic 主题的列表

### 27、Kafka 什么情况下会 rebalance

### 28、什么是消费者组？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
