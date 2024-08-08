# ZooKeeper 最新 2023 年面试题附答案解析，大汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、ZAB 和 Paxos 算法的联系与区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#1zab和paxos算法的联系与区别)

**相同点：**

**1、** 两者都存在一个类似于 Leader 进程的角色，由其负责协调多个 Follower 进程的运行

**2、** Leader 进程都会等待超过半数的 Follower 做出正确的反馈后，才会将一个提案进行提交

**3、** ZAB 协议中，每个 Proposal 中都包含一个 epoch 值来代表当前的 Leader 周期，Paxos 中名字为 Ballot

**不同点：**

ZAB 用来构建高可用的分布式数据主备系统（Zookeeper），Paxos 是用来构建分布式一致性状态机系统。

### [2、什么是 ZooKeeper?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#2什么是zookeeper)

ZooKeeper 是一个开源分布式协同服务系统，Zookeeper 的设计目标是将那些复杂容易出错的分布式一致性服务封装起来，构成一个高效可用的原语集，并提供一系列简单接口给用户使用。

### [3、ZooKeeper 的数据模型？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#3zookeeper的数据模型)

共享的、树形结构，由一系列的 ZNode 数据节点组成，类似文件系统(目录不能存数据）。ZNode 存有数据信息，如版本号等等。ZNode 之间的层级关系，像文件系统中的目录结构一样。并且它是将数据存在内存中，这样可以提高吞吐、减少延迟。

### [4、集群最少要几台机器，集群规则是怎样的？集群中有 3 台服务器，其中一个节点宕机，这个时候 Zookeeper 还可以使用吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#4集群最少要几台机器集群规则是怎样的集群中有-3-台服务器其中一个节点宕机这个时候-zookeeper-还可以使用吗)

集群规则为 2N+1 台，N>0，即 3 台。可以继续使用，单数服务器只要没超过一半的服务器宕机就可以继续使用。

### [5、数据发布/订阅？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#5数据发布/订阅)

发布者将数据发布到 ZooKeeper 上一个或多个节点上，订阅者从中订阅数据，从而动态获取数据的目的，实现配置信息的集中式管理和数据动态更新。

### [6、ACL 权限控制机制](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#6acl权限控制机制)

UGO（User/Group/Others）

目前在 Linux/Unix 文件系统中使用，也是使用最广泛的权限控制方式。是一种粗粒度的文件系统权限控制模式。

ACL（Access Control List）访问控制列表

**包括三个方面：**

**权限模式（Scheme）**

**1、** IP：从 IP 地址粒度进行权限控制

**2、** Digest：最常用，用类似于 username:password 的权限标识来进行权限配置，便于区分不同应用来进行权限控制

**3、** World：最开放的权限控制方式，是一种特殊的 digest 模式，只有一个权限标识“world:anyone”

**4、** Super：超级用户

**授权对象**

授权对象指的是权限赋予的用户或一个指定实体，例如 IP 地址或是机器灯。

**权限 Permission**

**1、** CREATE：数据节点创建权限，允许授权对象在该 Znode 下创建子节点

**2、** DELETE：子节点删除权限，允许授权对象删除该数据节点的子节点

**3、** READ：数据节点的读取权限，允许授权对象访问该数据节点并读取其数据内容或子节点列表等

**4、** WRITE：数据节点更新权限，允许授权对象对该数据节点进行更新操作

**5、** ADMIN：数据节点管理权限，允许授权对象对该数据节点进行 ACL 相关设置操作

### [7、说几个 zookeeper 常用的命令。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#7说几个zookeeper常用的命令。)

常用命令：ls get set create delete 等。

### [8、ZAB 和 Paxos 算法的联系与区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#8zab-和-paxos-算法的联系与区别)

**相同点：**

**1、** 两者都存在一个类似于 Leader 进程的角色，由其负责协调多个 Follower 进程的运行

**2、** Leader 进程都会等待超过半数的 Follower 做出正确的反馈后，才会将一个提案进行提交

**3、** ZAB 协议中，每个 Proposal 中都包含一个 epoch 值来代表当前的 Leader 周期，Paxos 中名字为 Ballot

**不同点：**

ZAB 用来构建高可用的分布式数据主备系统（Zookeeper），Paxos 是用来构建分布式一致性状态机系统。

### [9、ZooKeeper 是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#9zookeeper-是什么)

**1、** ZooKeeper 是一个开源的分布式协调服务。它是一个为分布式应用提供一致性服务的软件，分布式应用程序可以基于 Zookeeper 实现诸如数据发布/订阅、负载均衡、命名服务、分布式协调/通知、集群管理、Master 选举、分布式锁和分布式队列等功能。

**2、** ZooKeeper 的目标就是封装好复杂易出错的关键服务，将简单易用的接口和性能高效、功能稳定的系统提供给用户。

**Zookeeper 保证了如下分布式一致性特性：**

**1、** 顺序一致性

**2、** 原子性

**3、** 单一视图

**4、** 可靠性

**5、** 实时性（最终一致性）

客户端的读请求可以被集群中的任意一台机器处理，如果读请求在节点上注册了监听器，这个监听器也是由所连接的 zookeeper 机器来处理。对于写请求，这些请求会同时发给其他 zookeeper 机器并且达成一致后，请求才会返回成功。因此，随着 zookeeper 的集群机器增多，读请求的吞吐会提高但是写请求的吞吐会下降。

有序性是 zookeeper 中非常重要的一个特性，所有的更新都是全局有序的，每个更新都有一个唯一的时间戳，这个时间戳称为 zxid（Zookeeper Transaction Id）。而读请求只会相对于更新有序，也就是读请求的返回结果中会带有这个 zookeeper 最新的 zxid。

### [10、集群支持动态添加机器吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/ZooKeeper/ZooKeeper最新2021年面试题附答案解析，大汇总.md#10集群支持动态添加机器吗)

其实就是水平扩容了，Zookeeper 在这方面不太好。两种方式：

全部重启：关闭所有 Zookeeper 服务，修改配置之后启动。不影响之前客户端的会话。

逐个重启：在过半存活即可用的原则下，一台机器重启不影响整个集群对外提供服务。这是比较常用的方式。

3.5 版本开始支持动态扩容。

### 11、集群支持动态添加机器吗？

### 12、服务器角色

### 13、广播模式

### 14、分布式集群中为什么会有 Master 主节点？

### 15、哪些情况会导致 ZAB 进入恢复模式并选取新的 Leader?

### 16、服务器角色

### 17、什么是会话 Session?

### 18、负载均衡

### 19、ZooKeeper 可以保证哪些分布式一致性特性？

### 20、zookeeper 是如何选取主 leader 的？

### 21、zk 节点宕机如何处理？

### 22、Zookeeper 专门设计的一种支持崩溃恢复的原子广 播协议是?

### 23、数据同步

### 24、Zookeeper 文件系统

### 25、Watcher 事件监听器？

### 26、说几个 zookeeper 常用的命令。

### 27、ZooKeeper 提供了什么？

### 28、服务器的 3 中角色？

### 29、Zookeeper 的 java 客户端都有哪些？

### 30、ZAB 协议？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
