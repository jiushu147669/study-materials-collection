# Java 高级面试题整理及答案

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、并行和并发有什么区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#1并行和并发有什么区别)

**1、** 并发：多个任务在同一个 CPU 核上，按细分的时间片轮流(交替)执行，从逻辑上来看那些任务是同时执行。

**2、** 并行：单位时间内，多个处理器或多核处理器同时处理多个任务，是真正意义上的“同时进行”。

**3、** 串行：有 n 个任务，由一个线程按顺序执行。由于任务、方法都在一个线程执行所以不存在线程不安全情况，也就不存在临界区的问题。

**做一个形象的比喻：**

**1、** 并发 = 俩个人用一台电脑。

**2、** 并行 = 俩个人分配了俩台电脑。

**3、** 串行 = 俩个人排队使用一台电脑。

### [2、Hibernate 中 SessionFactory 是线程安全的吗？Session 是线程安全的吗（两个线程能够共享同一个 Session 吗）？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#2hibernate中sessionfactory是线程安全的吗session是线程安全的吗两个线程能够共享同一个session吗)

SessionFactory 对应 Hibernate 的一个数据存储的概念，它是线程安全的，可以被多个线程并发访问。SessionFactory 一般只会在启动的时候构建。对于应用程序，最好将 SessionFactory 通过单例模式进行封装以便于访问。Session 是一个轻量级非线程安全的对象（线程间不能共享 session），它表示与数据库进行交互的一个工作单元。Session 是由 SessionFactory 创建的，在任务完成之后它会被关闭。Session 是持久层服务对外提供的主要接口。Session 会延迟获取数据库连接（也就是在需要的时候才会获取）。为了避免创建太多的 session，可以使用 ThreadLocal 将 session 和当前线程绑定在一起，这样可以让同一个线程获得的总是同一个 session。Hibernate 3 中 SessionFactory 的 getCurrentSession()方法就可以做到。

### [3、Java 会存在内存泄漏吗？请简单描述。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#3java会存在内存泄漏吗请简单描述。)

内存泄漏是指不再被使用的对象或者变量一直被占据在内存中。理论上来说，Java 是有 GC 垃圾回收机制的，也就是说，不再被使用的对象，会被 GC 自动回收掉，自动从内存中清除

但是，即使这样，Java 也还是存在着内存泄漏的情况，java 导致内存泄露的原因很明确：长生命周期的对象持有短生命周期对象的引用就很可能发生内存泄露，尽管短生命周期对象已经不再需要，但是因为长生命周期对象持有它的引用而导致不能被回收，这就是 java 中内存泄露的发生场景。

### [4、生产环境服务器变慢，如何诊断处理？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#4生产环境服务器变慢如何诊断处理)

**1、** 使用 top 指令，服务器中 CPU 和 内存的使用情况，-H 可以按 CPU 使用率降序，-M 内存使用率降序。排除其他进程占用过高的硬件资源，对 Java 服务造成影响。

**2、** 如果发现 CPU 使用过高，可以使用 top 指令查出 JVM 中占用 CPU 过高的线程，通过 jstack 找到对应的线程代码调用，排查出问题代码。

**3、** 如果发现内存使用率比较高，可以 dump 出 JVM 堆内存，然后借助 MAT 进行分析，查出大对象或者占用最多的对象来自哪里，为什么会长时间占用这么多；如果 dump 出的堆内存文件正常，此时可以考虑堆外内存被大量使用导致出现问题，需要借助操作系统指令 pmap 查出进程的内存分配情况、gdb dump 出具体内存信息、perf 查看本地函数调用等。

**4、** 如果 CPU 和 内存使用率都很正常，那就需要进一步开启 GC 日志，分析用户线程暂停的时间、各部分内存区域 GC 次数和时间等指标，可以借助 jstat 或可视化工具 GCeasy 等，如果问题出在 GC 上面的话，考虑是否是内存不够、根据垃圾对象的特点进行参数调优、使用更适合的垃圾收集器；分析 jstack 出来的各个线程状态。如果问题实在比较隐蔽，考虑是否可以开启 jmx，使用 visualmv 等可视化工具远程监控与分析。

### [5、你是如何理解 fiber 的?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#5你是如何理解fiber的)

React Fiber 是一种基于浏览器的**单线程调度算法**.

React 16 之前 ，`reconcilation` 算法实际上是递归，想要中断递归是很困难的，React 16 开始使用了循环来代替之前的递归.

`Fiber`：**一种将 `recocilation` （递归 diff），拆分成无数个小任务的算法；它随时能够停止，恢复。停止恢复的时机取决于当前的一帧（16ms）内，还有没有足够的时间允许计算。**

> [Fiber 详解](https://github.com/xiaomuzhu/front-end-interview/blob/master/docs/guide/fiber.md)

### [6、HashMap 的扩容操作是怎么实现的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#6hashmap的扩容操作是怎么实现的)

**1、** 在 jdk1.8 中，resize 方法是在 hashmap 中的键值对大于阀值时或者初始化时，就调用 resize 方法进行扩容；

**2、** 每次扩展的时候，都是扩展 2 倍；

**3、** 扩展后 Node 对象的位置要么在原位置，要么移动到原偏移量两倍的位置。

在 putVal()中，我们看到在这个函数里面使用到了 2 次 resize()方法，resize()方法表示的在进行第一次初始化时会对其进行扩容，或者当该数组的实际大小大于其临界值值(第一次为 12),这个时候在扩容的同时也会伴随的桶上面的元素进行重新分发，这也是 JDK1.8 版本的一个优化的地方，在 1.7 中，扩容之后需要重新去计算其 Hash 值，根据 Hash 值对其进行分发，但在 1.8 版本中，则是根据在同一个桶的位置中进行判断(e.hash & oldCap)是否为 0，重新进行 hash 分配后，该元素的位置要么停留在原始位置，要么移动到原始位置+增加的数组大小这个位置上

```
final Node < K, V > [] resize() {
    Node < K, V > [] oldTab = table; //oldTab指向hash桶数组
    int oldCap = (oldTab == null) ? 0 : oldTab.length;
    int oldThr = threshold;
    int newCap, newThr = 0;
    if (oldCap > 0) { //如果oldCap不为空的话，就是hash桶数组不为空
        if (oldCap >= MAXIMUM_CAPACITY) { //如果大于最大容量了，就赋值为整数最大的阀值
            threshold = Integer.MAX_VALUE;
            return oldTab; //返回
        } //如果当前hash桶数组的长度在扩容后仍然小于最大容量 并且oldCap大于默认值16
        else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY && oldCap >= DEFAULT_INITIAL_CAPACITY) newThr = oldThr << 1; // double threshold 双倍扩容阀值threshold
    }
    // 旧的容量为0，但threshold大于零，代表有参构造有cap传入，threshold已经被初始化成最小2的n次幂
    // 直接将该值赋给新的容量
    else if (oldThr > 0) // initial capacity was placed in threshold
        newCap = oldThr;
    // 无参构造创建的map，给出默认容量和threshold 16, 16*0.75
    else { // zero initial threshold signifies using defaults
        newCap = DEFAULT_INITIAL_CAPACITY;
        newThr = (int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);
    }
    // 新的threshold = 新的cap * 0.75
    if (newThr == 0) {
        float ft = (float) newCap * loadFactor;
        newThr = (newCap < MAXIMUM_CAPACITY && ft < (float) MAXIMUM_CAPACITY ? (int) ft : Integer.MAX_VALUE);
    }
    threshold = newThr;
    // 计算出新的数组长度后赋给当前成员变量table
    @
    SuppressWarnings({
        "rawtypes", "unchecked"
    })
    Node < K, V > [] newTab = (Node < K, V > []) new Node[newCap]; //新建hash桶数组
    table = newTab; //将新数组的值复制给旧的hash桶数组
    // 如果原先的数组没有初始化，那么resize的初始化工作到此结束，否则进入扩容元素重排逻辑，使其均匀的分散
    if (oldTab != null) {
        // 遍历新数组的所有桶下标
        for (int j = 0; j < oldCap; ++j) {
            Node < K, V > e;
            if ((e = oldTab[j]) != null) {
                // 旧数组的桶下标赋给临时变量e，并且解除旧数组中的引用，否则就数组无法被GC回收
                oldTab[j] = null;
                // 如果e.next==null，代表桶中就一个元素，不存在链表或者红黑树
                if (e.next == null)
                // 用同样的hash映射算法把该元素加入新的数组
                    newTab[e.hash & (newCap - 1)] = e;
                // 如果e是TreeNode并且e.next!=null，那么处理树中元素的重排
                else if (e instanceof TreeNode)
                ((TreeNode < K, V > ) e).split(this, newTab, j, oldCap);
                // e是链表的头并且e.next!=null，那么处理链表中元素重排
                else { // preserve order
                    // loHead,loTail 代表扩容后不用变换下标，见注1
                    Node < K, V > loHead = null, loTail = null;
                    // hiHead,hiTail 代表扩容后变换下标，见注1
                    Node < K, V > hiHead = null, hiTail = null;
                    Node < K, V > next;
                    // 遍历链表
                    do {
                        next = e.next;
                        if ((e.hash & oldCap) == 0) {
                            if (loTail == null)
                            // 初始化head指向链表当前元素e，e不一定是链表的第一个元素，初始化后loHead
                            // 代表下标保持不变的链表的头元素
                                loHead = e;
                            else
                            // loTail.next指向当前e
                                loTail.next = e;
                            // loTail指向当前的元素e
                            // 初始化后，loTail和loHead指向相同的内存，所以当loTail.next指向下一个元素时，
                            // 底层数组中的元素的next引用也相应发生变化，造成lowHead.next.next.....
                            // 跟随loTail同步，使得lowHead可以链接到所有属于该链表的元素。
                            loTail = e;
                        } else {
                            if (hiTail == null)
                            // 初始化head指向链表当前元素e, 初始化后hiHead代表下标更改的链表头元素
                                hiHead = e;
                            else hiTail.next = e;
                            hiTail = e;
                        }
                    } while ((e = next) != null);
                    // 遍历结束, 将tail指向null，并把链表头放入新数组的相应下标，形成新的映射。
                    if (loTail != null) {
                        loTail.next = null;
                        newTab[j] = loHead;
                    }
                    if (hiTail != null) {
                        hiTail.next = null;
                        newTab[j + oldCap] = hiHead;
                    }
                }
            }
        }
    }
    return newTab;
}
```

### [7、解释如何使用 WAR 文件部署 web 应用程序?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#7解释如何使用war文件部署web应用程序)

在 Tomcat 的 web 应用程序目录下，jsp、servlet 和它们的支持文件被放置在适当的子目录中。你可以将 web 应用程序目录下的所有文件压缩到一个压缩文件中，以.war 文件扩展名结束。你可以通过在 webapps 目录中放置 WAR 文件来执行 web 应用程序。当一个 web 服务器开始执行时，它会将 WAR 文件的内容提取到适当的 webapps 子目录中。

### [8、常用的并发工具类有哪些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#8常用的并发工具类有哪些)

**1、** CountDownLatch

**2、** CyclicBarrier

**3、** Semaphore

**4、** Exchanger

### [9、你能保证 GC 执行吗？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#9你能保证-gc-执行吗)

不能，虽然你可以调用 System.gc() 或者 Runtime.gc()，但是没有办法保证 GC 的执行。

### [10、哪些集合类是线程安全的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Java/Java高级面试题整理及答案.md#10哪些集合类是线程安全的)

**1、** Vector：就比 Arraylist 多了个 synchronized （线程安全），因为效率较低，现在已经不太建议使用。

**2、** hashTable：就比 hashMap 多了个 synchronized (线程安全)，不建议使用。

**3、** ConcurrentHashMap：是 Java5 中支持高并发、高吞吐量的线程安全 HashMap 实现。它由 Segment 数组结构和 HashEntry 数组结构组成。Segment 数组在 ConcurrentHashMap 里扮演锁的角色，HashEntry 则用于存储键-值对数据。一个 ConcurrentHashMap 里包含一个 Segment 数组，Segment 的结构和 HashMap 类似，是一种数组和链表结构；一个 Segment 里包含一个 HashEntry 数组，每个 HashEntry 是一个链表结构的元素；每个 Segment 守护着一个 HashEntry 数组里的元素，当对 HashEntry 数组的数据进行修改时，必须首先获得它对应的 Segment 锁。（推荐使用）

### 11、事务的 ACID 是指什么？

### 12、对象分配规则

### 13、两个对象值相同(x.equals(y) == true)，但却可有不同的 hash code，这句话对不对？

### 14、创建对象的过程是什么？

### 15、&和&&的区别

### 16、为什么 wait(), notify()和 notifyAll ()必须在同步方法或者同步块中被调用？

### 17、Java 中的继承是单继承还是多继承

### 18、Java 中，如何将字符串 YYYYMMDD 转换为日期？

### 19、请你谈谈对 OOM 的认识

### 20、CopyOnWriteArrayList 可以用于什么应用场景？

### 21、什么时候使用享元模式？

### 22、什么是 Executors？

### 23、死锁与活锁的区别，死锁与饥饿的区别？

### 24、堆的作用是什么？

### 25、垃圾回收的优点和原理。说说 2 种回收机制

### 26、React 如何进行组件/逻辑复用?

### 27、请解释一下 MAC 代表什么?

### 28、ThreadLocal 是什么？有什么用？

### 29、线程的生命周期？

### 30、说几个常见的编译时异常类？

### 31、Java 如何实现多线程之间的通讯和协作？

### 32、什么是 Java Timer 类？如何创建一个有特定时间间隔的任务？

### 33、使用 js 获取一个表单元素

### 34、多线程同步和互斥有几种实现方法，都是什么？

### 35、什么是重排序

### 36、Java 中 java.util.Date 与 java.sql.Date 有什么区别？

### 37、说说类加载的过程

### 38、React 最新的生命周期是怎样的?

### 39、复制算法（copying）

### 40、用 Java 的套接字编程实现一个多线程的回显（echo）服务器。

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
