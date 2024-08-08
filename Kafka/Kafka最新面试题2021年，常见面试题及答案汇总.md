# Kafka 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、3.它还可以在记录进入时对其进行处理。Apache Kafka 对于新手的面试](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#13它还可以在记录进入时对其进行处理。apache-kafka对于新手的面试)

### [2、Broker 的 Heap Size 如何设置？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#2broker的heap-size如何设置)

**1、** 其实对于 SRE 还是送分题，因为目前来讲大部分公司的业务系统都是使用 Java 开发，因此 SRE 对于基本的 JVM 相关的参数应该至少都是非常了解的，核心就在于 JVM 的配置以及 GC 相关的知识。

**2、** 标准答案：任何 Java 进程 JVM 堆大小的设置都需要仔细地进行考量和测试。一个常见的做法是，以默认的初始 JVM 堆大小运行程序，当系统达到稳定状态后，手动触发一次 Full GC，然后通过 JVM 工具查看 GC 后的存活对象大小。之后，将堆大小设置成存活对象总大小的 1.5~2 倍。对于 Kafka 而言，这个方法也是适用的。不过，业界有个最佳实践，那就是将 Broker 的 Heap Size 固定为 6GB。经过很多公司的验证，这个大小是足够且良好的。

### [3、Rebalance 有什么影响](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#3rebalance有什么影响)

Rebalance 本身是 Kafka 集群的一个保护设定，用于剔除掉无法消费或者过慢的消费者，然后由于我们的数据量较大，同时后续消费后的数据写入需要走网络 IO，很有可能存在依赖的第三方服务存在慢的情况而导致我们超时。Rebalance 对我们数据的影响主要有以下几点：

数据重复消费: 消费过的数据由于提交 offset 任务也会失败，在 partition 被分配给其他消费者的时候，会造成重复消费，数据重复且增加集群压力

Rebalance 扩散到整个 ConsumerGroup 的所有消费者，因为一个消费者的退出，导致整个 Group 进行了 Rebalance，并在一个比较慢的时间内达到稳定状态，影响面较大

频繁的 Rebalance 反而降低了消息的消费速度，大部分时间都在重复消费和 Rebalance

数据不能及时消费，会累积 lag，在 Kafka 的 TTL 之后会丢弃数据 上面的影响对于我们系统来说，都是致命的。

### [4、Kafka 的高可用机制是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#4kafka的高可用机制是什么)

这个问题比较系统，回答出 Kafka 的系统特点，leader 和 follower 的关系，消息读写的顺序即可。

[https://www.cnblogs.com/qingyunzong/p/9004703.html](https://www.cnblogs.com/qingyunzong/p/9004703.html)

[https://www.tuicool.com/articles/BNRza2E](https://www.tuicool.com/articles/BNRza2E)

[https://yq.aliyun.com/articles/64703](https://yq.aliyun.com/articles/64703)

### [5、解释 Kafka 可以接收的消息最大为多少？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#5解释kafka可以接收的消息最大为多少)

Kafka 可以接收的最大消息大小约为 1000000 字节。

### [6、Kafka 流的特点。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#6kafka流的特点。)

Kafka 流的一些最佳功能是 Kafka Streams 具有高度可扩展性和容错性。Kafka 部署到容器，VM，裸机，云。我们可以说，Kafka 流对于小型，中型和大型用例同样可行。此外，它完全与 Kafka 安全集成。编写标准 Java 应用程序。完全一次处理语义。而且，不需要单独的处理集群。

### [7、Kafka Follower 如何与 Leader 同步数据?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#7kafka-follower如何与leader同步数据)

Kafka 的复制机制既不是完全的同步复制，也不是单纯的异步复制。完全同步复制要求 All Alive Follower 都复制完，这条消息才会被认为 commit，这种复制方式极大的影响了吞吐率。而异步复制方式下，Follower 异步的从 Leader 复制数据，数据只要被 Leader 写入 log 就被认为已经 commit，这种情况下，如果 leader 挂掉，会丢失数据，Kafka 使用 ISR 的方式很好的均衡了确保数据不丢失以及吞吐率。Follower 可以批量的从 Leader 复制数据，而且 Leader 充分利用磁盘顺序读以及 send file(zero copy) 机制，这样极大的提高复制性能，内部批量写磁盘，大幅减少了 Follower 与 Leader 的消息量差。

### [8、Kafka 的哪些场景中使用了零拷贝（Zero Copy）？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#8kafka的哪些场景中使用了零拷贝zero-copy)

**1、** 其实这道题对于 SRE 来讲，有点超纲了，不过既然 Zero Copy 是 Kafka 高性能的保证，我们需要了解它。

**2、** Zero Copy 是特别容易被问到的高阶题目。在 Kafka 中，体现 Zero Copy 使用场景的地方有两处：基于 mmap 的索引和日志文件读写所用的 TransportLayer。

**3、** 先说第一个。索引都是基于 MappedByteBuffer 的，也就是让用户态和内核态共享内核态的数据缓冲区，此时，数据不需要复制到用户态空间。不过，mmap 虽然避免了不必要的拷贝，但不一定就能保证很高的性能。在不同的操作系统下，mmap 的创建和销毁成本可能是不一样的。很高的创建和销毁开销会抵消 Zero Copy 带来的性能优势。由于这种不确定性，在 Kafka 中，只有索引应用了 mmap，最核心的日志并未使用 mmap 机制。

**4、** 再说第二个。TransportLayer 是 Kafka 传输层的接口。它的某个实现类使用了 FileChannel 的 transferTo 方法。该方法底层使用 sendfile 实现了 Zero Copy。对 Kafka 而言，如果 I/O 通道使用普通的 PLAINTEXT，那么，Kafka 就可以利用 Zero Copy 特性，直接将页缓存中的数据发送到网卡的 Buffer 中，避免中间的多次拷贝。相反，如果 I/O 通道启用了 SSL，那么，Kafka 便无法利用 Zero Copy 特性了。

### [9、副本长时间不在 ISR 中，这意味着什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#9副本长时间不在isr中这意味着什么)

意味着 follower 不能像 leader 收集数据那样快速地获取数据。

### [10、：46, 48](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Kafka/Kafka最新面试题2021年，常见面试题及答案汇总.md#10：46,-48)

### 11、Kafka 中的数据日志是什么？

### 12、Kafka 为何这么快

### 13、Kafka 创建 Topic 时如何将分区放置到不同的 Broker 中

### 14、消费者故障，出现活锁问题如何解决？

### 15、什么是 Apache Kafka?

### 16、传统的消息传递方法有哪些类型？

### 17、consumer_offsets 是做什么用的？

### 18、解释 Kafka Producer API 的作用。

### 19、阐述下 Kafka 中的领导者副本（Leader Replica）和追随者副本（Follower Replica）的区别

### 20、讲讲 Kafka 维护消费状态跟踪的方法

### 21、Kafka 的消费者如何消费数据

### 22、为什么 Kafka 的复制至关重要？

### 23、如何保证 Kafka 顺序消费

### 24、Apache Kafka 是分布式流处理平台吗？如果是，你能用它做什么？

### 25、为什么 Kafka 的复制至关重要？

### 26、消费者如何不自动提交偏移量，由应用提交？

### 27、Kafka 新建的分区会在哪个目录下创建

### 28、Kafka 中的 zookeeper 起到什么作用？可以不用 zookeeper 吗？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
