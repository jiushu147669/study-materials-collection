# Android 最新面试题，2023 年面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、在 service 的生命周期方法 onstartConmand()可不可以执行网络操作？如何在 service 中执行网络操作？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#1在-service-的生命周期方法-onstartconmand可不可以执行网络操作如何在-service-中执行网络操作)

可以的，就在 onstartConmand 方法内执行。

### [2、简述 TCP，UDP，Socket](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#2简述tcpudpsocket)

TCP 是经过 3 次握手，4 次挥手完成一串数据的传送

UDP 是无连接的，知道 IP 地址和端口号，向其发送数据即可，不管数据是否发送成功

Socket 是一种不同计算机，实时连接，比如说传送文件，即时通讯

### [3、Android 中如何捕获未捕获的异常](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#3android-中如何捕获未捕获的异常)

**UncaughtExceptionHandler**

**1、** 自 定 义 一 个 Application ， 比 如 叫 MyApplication 继 承 Application 实 现 UncaughtExceptionHandler。

**2、** 覆写 UncaughtExceptionHandler 的 onCreate 和 uncaughtException 方法。 注意：上面的代码只是简单的将异常打印出来。在 onCreate 方法中我们给 Thread 类设置默认异常处理 handler，如果这句代码不执行则一切都是白搭。在 uncaughtException 方法中我们必须新开辟个线程进行我们异常的收集工作，然后将系统给杀死。

**3、** 在 AndroidManifest 中配置该 Application：<application android:name="com.example.uncatchexception.MyApplication"

Bug 收集工具 Crashlytics

Crashlytics 是专门为移动应用开发者提供的保存和分析应用崩溃的工具。国内主要使用的是友盟做数据统计。

**Crashlytics 的好处：**

**1、** Crashlytics 不会漏掉任何应用崩溃信息。

**2、** Crashlytics 可以象 Bug 管理工具那样，管理这些崩溃日志。

**3、** Crashlytics 可以每天和每周将崩溃信息汇总发到你的邮箱，所有信息一目了然。

### [4、android 中的动画有哪几类，它们的特点和区别是什么](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#4android中的动画有哪几类它们的特点和区别是什么)

两种，一种是 Tween 动画、还有一种是 Frame 动画。Tween 动画，这种实现方式可以使视图组件移动、放大、缩小以及产生透明度的变化;另一种 Frame 动画，传统的动画方法，通过顺序的播放排列好的图片来实现，类似电影。

### [5、Android 中的动画有哪几类，它们的特点和区别是什么](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#5android-中的动画有哪几类它们的特点和区别是什么)

Frame Animation(帧动画)主要用于播放一帧帧准备好的图片，类似 GIF 图片，优点是使用简单方便、缺点是需要事先准备好每一帧图片；

Tween Animation(补间动画)仅需定义开始与结束的关键帧，而变化的中间帧由系统补上，优点是不用准备每一帧，缺点是只改变了对象绘制，而没有改变 View 本身属性。因此如果改变了按钮的位置，还是需要点击原来按钮所在位置才有效。

Property Animation(属性动画)是 3.0 后推出的动画，优点是使用简单、降低实现的复杂度、直接更改对象的属性、几乎可适用于任何对象而仅非 View 类，主要包括 ValueAnimator 和 ObjectAnimator

### [6、java 中如何引用本地语言](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#6java中如何引用本地语言)

可以用 JNI（java native interface  java 本地接口）接口 。

### [7、请解释下在单线程模型中 Message、Handler、Message Queue、Looper 之间的关系。](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#7请解释下在单线程模型中messagehandlermessage-queuelooper之间的关系。)

简单的说，Handler 获取当前线程中的 looper 对象，looper 用来从存放 Message 的 MessageQueue 中取出 Message，再有 Handler 进行 Message 的分发和处理.

Message Queue(消息队列)：用来存放通过 Handler 发布的消息，通常附属于某一个创建它的线程，可以通过 Looper.myQueue()得到当前线程的消息队列

Handler：可以发布或者处理一个消息或者操作一个 Runnable，通过 Handler 发布消息，消息将只会发送到与它关联的消息队列，然也只能处理该消息队列中的消息

Looper：是 Handler 和消息队列之间通讯桥梁，程序组件首先通过 Handler 把消息传递给 Looper，Looper 把消息放入队列。Looper 也把消息队列里的消息广播给所有的

Handler：Handler 接受到消息后调用 handleMessage 进行处理

Message：消息的类型，在 Handler 类中的 handleMessage 方法中得到单个的消息进行处理

在单线程模型下，为了线程通信问题，Android 设计了一个 Message Queue(消息队列)， 线程间可以通过该 Message Queue 并结合 Handler 和 Looper 组件进行信息交换。下面将对它们进行分别介绍：

**Message**

Message 消息，理解为线程间交流的信息，处理数据后台线程需要更新 UI，则发送 Message 内含一些数据给 UI 线程。

**Handler**

Handler 处理者，是 Message 的主要处理者，负责 Message 的发送，Message 内容的执行处理。后台线程就是通过传进来的 Handler 对象引用来 sendMessage(Message)。而使用 Handler，需要 implement 该类的 handleMessage(Message)方法，它是处理这些 Message 的操作内容，例如 Update UI。通常需要子类化 Handler 来实现 handleMessage 方法。

**Message Queue**

Message Queue 消息队列，用来存放通过 Handler 发布的消息，按照先进先出执行。

每个 message queue 都会有一个对应的 Handler。Handler 会向 message queue 通过两种方法发送消息：sendMessage 或 post。这两种消息都会插在 message queue 队尾并按先进先出执行。但通过这两种方法发送的消息执行的方式略有不同：通过 sendMessage 发送的是一个 message 对象,会被 Handler 的 handleMessage()函数处理；而通过 post 方法发送的是一个 runnable 对象，则会自己执行。

**Looper**

Looper 是每条线程里的 Message Queue 的管家。Android 没有 Global 的 Message Queue，而 Android 会自动替主线程(UI 线程)建立 Message Queue，但在子线程里并没有建立 Message Queue。所以调用 Looper.getMainLooper()得到的主线程的 Looper 不为 NULL，但调用 Looper.myLooper() 得到当前线程的 Looper 就有可能为 NULL。对于子线程使用 Looper，API Doc 提供了正确的使用方法：这个 Message 机制的大概流程：

**1、** 在 Looper.loop()方法运行开始后，循环地按照接收顺序取出 Message Queue 里面的非 NULL 的 Message。

**2、** 一开始 Message Queue 里面的 Message 都是 NULL 的。当 Handler.sendMessage(Message)到 Message Queue，该函数里面设置了那个 Message 对象的 target 属性是当前的 Handler 对象。随后 Looper 取出了那个 Message，则调用 该 Message 的 target 指向的 Hander 的 dispatchMessage 函数对 Message 进行处理。在 dispatchMessage 方法里，如何处理 Message 则由用户指定，三个判断，优先级从高到低：

**1、** Message 里面的 Callback，一个实现了 Runnable 接口的对象，其中 run 函数做处理工作；

**2、** Handler 里面的 mCallback 指向的一个实现了 Callback 接口的对象，由其 handleMessage 进行处理；

**3、** 处理消息 Handler 对象对应的类继承并实现了其中 handleMessage 函数，通过这个实现的 handleMessage 函数处理消息。

由此可见，我们实现的 handleMessage 方法是优先级最低的！

3\、Handler 处理完该 Message (update UI) 后，Looper 则设置该 Message 为 NULL，以便回收！

在网上有很多文章讲述主线程和其他子线程如何交互，传送信息，最终谁来执行处理信息之类的，个人理解是最简单的方法——判断 Handler 对象里面的 Looper 对象是属于哪条线程的，则由该线程来执行！

1\、当 Handler 对象的构造函数的参数为空，则为当前所在线程的 Looper；

2\、Looper.getMainLooper()得到的是主线程的 Looper 对象，Looper.myLooper()得到的是当前线程的 Looper 对象。

### [8、广播注册](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#8广播注册)

首先写一个类要继承 BroadCastReceiver

第一种：在清单文件中声明，添加

```
<receive android:name=".BroadCastReceiverDemo">
<intent-filter>
<action android:name="android.provider.Telephony.SMS_RECEIVED">
</intent-filter>
</receiver>
```

第二种：使用代码进行注册如：

```
IntentFilter filter = new IntentFilter("android.provider.Telephony.SMS_RECEIVED");
BroadCastReceiverDemo receiver = new BroadCastReceiver();
registerReceiver(receiver, filter);
```

两种注册类型的区别是：

a.第一种是常驻型广播，也就是说当应用程序关闭后，如果有信息广播来，程序也会被系统调用自动运行。

b.第二种不是常驻广播，也就是说广播跟随程序的生命周期。

### [9、Service 生命周期](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#9service生命周期)

在 Service 的生命周期里，常用的有：

4 个手动调用的方法

```
startService()    启动服务
stopService()    关闭服务
bindService()    绑定服务
unbindService()    解绑服务
```

5 个内部自动调用的方法

```
onCreat()            创建服务
onStartCommand()    开始服务
onDestroy()            销毁服务
onBind()            绑定服务
onUnbind()            解绑服务
```

**1、** 手动调用 startService()启动服务，自动调用内部方法：onCreate()、onStartCommand()，如果一个 Service 被 startService()多次启动，那么 onCreate()也只会调用一次。

**2、** 手动调用 stopService()关闭服务，自动调用内部方法：onDestory()，如果一个 Service 被启动且被绑定，如果在没有解绑的前提下使用 stopService()关闭服务是无法停止服务的。

**3、** 手动调用 bindService()后，自动调用内部方法：onCreate()、onBind()。

**4、** 手动调用 unbindService()后，自动调用内部方法：onUnbind()、onDestory()。

**5、** startService()和 stopService()只能开启和关闭 Service，无法操作 Service，调用者退出后 Service 仍然存在；bindService()和 unbindService()可以操作 Service，调用者退出后，Service 随着调用者销毁。

### [10、请介绍下 AsyncTask 的内部实现和适用的场景](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题，2021年面试题及答案汇总.md#10请介绍下-asynctask-的内部实现和适用的场景)

AsyncTask 内部也是 Handler 机制来完成的，只不过 Android 提供了执行框架来提供线程池来执行相应地任务，因为线程池的大小问题，所以 AsyncTask 只应该用来执行耗时时间较短的任务，比如 HTTP 请求，大规模的下载和数据库的更改不适用于 AsyncTask，因为会导致线程池堵塞，没有线程来执行其他的任务，导致的情形是会发生 AsyncTask 根本执行不了的问题

### 11、说下 Activity 的四种启动模式、应用场景 ？

### 12、NDK 是什么

### 13、请介绍下 Android 中常用的五种布局。

### 14、activity 在屏幕旋转时的生命周期

### 15、Android 中 4 大组件

### 16、如何对 Android 应用进行性能分析

### 17、ListView 中图片错位的问题是如何产生的

### 18、Fragment 与 activity 如何传值和交互？

### 19、Android 本身的 api 并未声明会抛出异常，则其在运行时有无可能抛出 runtime 异常，你遇到过吗？诺有的话会导致什么问题？如何解决？

### 20、说说 LruCache 底层原理

### 21、Android 数字签名

### 22、Activity 的状态有几种？

### 23、android 的数据存储

### 24、一条最长的短信息约占多少 byte?

### 25、Fragment 的 replace 和 add 方法的区别

### 26、为什么 Android 引入广播机制?

### 27、如何退出 Activity？如何安全退出已调用多个 Activity 的 Application？

### 28、系统上安装了多种浏览器，能否指定某浏览器访问指定页面？请说明原由。

### 29、说说 ContentProvider、ContentResolver、ContentObserver 之间的关系

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
