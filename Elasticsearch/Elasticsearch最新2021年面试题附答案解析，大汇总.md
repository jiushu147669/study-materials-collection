# Elasticsearch 最新 2023 年面试题附答案解析，大汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、详细描述一下 Elasticsearch 搜索的过程？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#1详细描述一下elasticsearch搜索的过程)

`面试官`：想了解 ES 搜索的底层原理，不再只关注业务层面了。

搜索拆解为“query then fetch” 两个阶段。

**query 阶段的目的**：定位到位置，但不取。

步骤拆解如下：

**1、** 假设一个索引数据有 5 主+1 副本 共 10 分片，一次请求会命中（主或者副本分片中）的一个。

**2、** 每个分片在本地进行查询，结果返回到本地有序的优先队列中。

**3、** 第 2）步骤的结果发送到协调节点，协调节点产生一个全局的排序列表。

**fetch 阶段的目的**：取数据。

路由节点获取所有文档，返回给客户端。

### [2、Beats 如何与 Elasticsearch 结合使用？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#2beats-如何与-elasticsearch-结合使用)

Beats 是一种开源工具，可以将数据直接传输到 Elasticsearch 或通过 logstash，在使用 Kibana 进行查看之前，可以对数据进行处理或过滤。

传输的数据类型包含：审核数据，日志文件，云数据，网络流量和窗口事件日志等。

### [3、解释一下 Elasticsearch 的 分片？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#3解释一下-elasticsearch-的-分片)

当文档数量增加，硬盘容量和处理能力不足时，对客户端请求的响应将延迟。

在这种情况下，将索引数据分成小块的过程称为分片，可改善数据搜索结果的获取。

### [4、精准匹配检索和全文检索匹配检索的不同？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#4精准匹配检索和全文检索匹配检索的不同)

**两者的本质区别：**

精确匹配用于：是否完全一致？

**举例：邮编、身份证号的匹配往往是精准匹配。**

全文检索用于：是否相关？

举例：类似 B 站搜索特定关键词如“马保国 视频”往往是模糊匹配，相关的都返回就可以。

### [5、您能否说明当前可下载的稳定 Elasticsearch 版本？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#5您能否说明当前可下载的稳定elasticsearch版本)

Elasticsearch 当前最新版本是 7.10（2020 年 11 月 21 日）。

为什么问这个问题？ES 更新太快了，应聘者如果了解并使用最新版本，基本能说明他关注 ES 更新。甚至从更广维度讲，他关注技术的迭代和更新。

但，不信你可以问问，很多求职者只知道用了 ES，什么版本一概不知。

### [6、您能解释一下 Elasticsearch 中的 Explore API 吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#6您能解释一下-elasticsearch-中的-explore-api-吗)

没有用过，这是 Graph （收费功能）相关的 API。

点到为止即可，类似问题实际开发现用现查，类似问题没有什么意义。

[https://www.elastic.co/guide/en/elasticsearch/reference/current/graph-explore-api.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/graph-explore-api.html)

### [7、elasticsearch 了解多少，说说你们公司 es 的集群架构，索引数据大小，分片有多少，以及一些调优手段 。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#7elasticsearch了解多少说说你们公司es的集群架构索引数据大小分片有多少以及一些调优手段-。)

`面试官`：想了解应聘者之前公司接触的 ES 使用场景、规模，有没有做过比较大规模的索引设计、规划、调优。

如实结合自己的实践场景回答即可。

比如：ES 集群架构 13 个节点，索引根据通道不同共 20+索引，根据日期，每日递增 20+，索引：10 分片，每日递增 1 亿+数据，

每个通道每天索引大小控制：150GB 之内。

仅索引层面调优手段：

**设计阶段调优**

**1、** 根据业务增量需求，采取基于日期模板创建索引，通过 roll over API 滚动索引；

**2、** 使用别名进行索引管理；

**3、** 每天凌晨定时对索引做 force_merge 操作，以释放空间；

**4、** 采取冷热分离机制，热数据存储到 SSD，提高检索效率；冷数据定期进行 shrink 操作，以缩减存储；

**5、** 采取 curator 进行索引的生命周期管理；

**6、** 仅针对需要分词的字段，合理的设置分词器；

**7、** Mapping 阶段充分结合各个字段的属性，是否需要检索、是否需要存储等。……..

**写入调优**

**1、** 写入前副本数设置为 0；

**2、** 写入前关闭 refresh_interval 设置为-1，禁用刷新机制；

**3、** 写入过程中：采取 bulk 批量写入；

**4、** 写入后恢复副本数和刷新间隔；

**5、** 尽量使用自动生成的 id。

**查询调优**

**1、** 禁用 wildcard；

**2、** 禁用批量 terms（成百上千的场景）；

**3、** 充分利用倒排索引机制，能 keyword 类型尽量 keyword；

**4、** 数据量大时候，可以先基于时间敲定索引再检索；

**5、** 设置合理的路由机制。

**1.4、其他调优**

部署调优，业务调优等。

上面的提及一部分，面试者就基本对你之前的实践或者运维经验有所评估了。

### [8、能列举过你使用的 X-Pack 命令吗?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#8能列举过你使用的-x-pack-命令吗)

7.1 安全功能免费后，使用了：setup-passwords 为账号设置密码，确保集群安全。

### [9、elasticsearch 全文检索](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#9elasticsearch-全文检索)

(1) 客户端使用 RestFul API 向对应的 node 发送查询请求

(2)协调节点将请求转发到所有节点（primary 或者 replica）所有节点将对应的数据查询之后返回对应的 doc id 返回给协调节点

(3)协调节点将 doc 进行排序聚合

(4) 协调节点再根据 doc id 把查询请求发送到对应 shard 的 node，返回 document

### [10、你之前公司的 ElasticSearch 集群，一个 Node 一般会分配几个分片？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Elasticsearch/Elasticsearch最新2021年面试题附答案解析，大汇总.md#10你之前公司的elasticsearch集群一个node一般会分配几个分片)

我们遵循官方建议，一个 Node 最好不要多于三个 shards.

### 11、什么是 ElasticSearch 脑裂？

### 12、你能否列出与 Elasticsearch 有关的主要可用字段数据类型？

### 13、详细描述一下 Elasticsearch 索引文档的过程。

### 14、elasticsearch 分布式架构原理

### 15、logstash 如何与 Elasticsearch 结合使用？

### 16、介绍一下你们的个性化搜索方案？

### 17、您能否列出 与 ELK 日志分析相关的应用场景？

### 18、简要介绍一下 Elasticsearch？

### 19、Elasticsearch 支持哪些类型的查询？

### 20、elasticsearch 实际设计

### 21、拼写纠错是如何实现的？

### 22、Elasticsearch 是如何实现 master 选举的？

### 23、lucence 内部结构是什么？

### 24、ElasticSearch 中的副本是什么？

### 25、Elasticsearch 是如何实现 Master 选举的？

### 26、解释一下 Elasticsearch 集群中的 Type 的概念 ？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
