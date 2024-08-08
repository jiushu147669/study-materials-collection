# Android 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、dagger2](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#1dagger2)

Dagger2 是一个主要用于依赖注入的框架，减少初始化对象操作，降低耦合度

### [2、Android 中 touch 事件的传递机制是怎样的?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#2android中touch事件的传递机制是怎样的)

**1、** Touch 事件传递的相关 API 有 dispatchTouchEvent、onTouchEvent、onInterceptTouchEvent

**2、** Touch 事件相关的类有 View、ViewGroup、Activity

**3、** Touch 事件会被封装成 MotionEvent 对象，该对象封装了手势按下、移动、松开等动作

**4、** Touch 事件通常从 Activity#dispatchTouchEvent 发出，只要没有被消费，会一直往下传递，到最底层的 View。

**5、** 如果 Touch 事件传递到的每个 View 都不消费事件，那么 Touch 事件会反向向上传递,最终交由 Activity#onTouchEvent 处理、

**6、** onInterceptTouchEvent 为 ViewGroup 特有，可以拦截事件、

**7、** Down 事件到来时，如果一个 View 没有消费该事件，那么后续的 MOVE/UP 事件都不会再给它

### [3、Android 中任务栈的分配](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#3android中任务栈的分配)

Task 实际上是一个 Activity 栈，通常用户感受的一个 Application 就是一个 Task。从这个定义来看，Task 跟 Service 或者其他 Components 是没有任何联系的，它只是针对 Activity 而言的。

Activity 有不同的启动模式, 可以影响到 task 的分配

### [4、说说 mvc 模式的原理，它在 android 中的运用,android 的官方建议应用程序的开发采用 mvc 模式。何谓 mvc？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#4说说mvc模式的原理它在android中的运用,android的官方建议应用程序的开发采用mvc模式。何谓mvc)

mvc 是 model,view,controller 的缩写，mvc 包含三个部分：

**1、** 模型（model）对象：是应用程序的主体部分，所有的业务逻辑都应该写在该层。

**2、** 视图（view）对象：是应用程序中负责生成用户界面的部分。也是在整个 mvc 架构中用户唯一可以看到的一层，接收用户的输入，显示处理结果。

**3、** 控制器（control）对象：是根据用户的输入，控制用户界面数据显示及更新 model 对象状态的部分，控制器更重要的一种导航功能，响应用户出发的相关事件，交给 m 层处理。

**android 鼓励弱耦合和组件的重用，在 android 中 mvc 的具体体现如下：**

**1、** 视图层（view）：一般采用 xml 文件进行界面的描述，使用的时候可以非常方便的引入，当然，如果你对 android 了解的比较的多了话，就一定可以想到在 android 中也可以使用 JavaScript+html 等的方式作为 view 层，当然这里需要进行 java 和 javascript 之间的通信，幸运的是，android 提供了它们之间非常方便的通信实现。

**2、** 控制层（controller）：android 的控制层的重任通常落在了众多的 acitvity 的肩上，这句话也就暗含了不要在 acitivity 中写代码，要通过 activity 交割 model 业务逻辑层处理，这样做的另外一个原因是 android 中的 acitivity 的响应时间是 5s，如果耗时的操作放在这里，程序就很容易被回收掉。

**3、** 模型层（model）：对数据库的操作、对网络等的操作都应该在 model 里面处理，当然对业务计算等操作也是必须放在的该层的。

### [5、内存泄露如何查看和解决](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#5内存泄露如何查看和解决)

概念：有些对象只有有限的生命周期，当他们的任务完成之后，它们将被垃圾回收，如果在对象的生命周期本该结束的时候，这个对象还被一系列的引用，着就会导致内存泄露。

解决方法：使用开源框架 LeakCanary 检测针对性解决

**常见的内存泄露有：**

**1、** 单例造成的内存泄露，例如单例中的 Context 生命周期大于本身 Context 生命周期

**2、** 线程使用 Hander 造成的内存卸扣，当 activity 已经结束，线程依然在运行更新 UI

**3、** 非静态类使用静态变量导致无法回收释放造成泄露

**4、** WebView 网页过多造成内存泄露

**5、** 资源未关闭造成泄露，例如数据库使用完之后关闭连接

### [6、推送到达率如何提高](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#6推送到达率如何提高)

判手机系统，小米使用小米推送，华为使用华为推送，其他手机使用友盟推送

### [7、简述 JNI](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#7简述jni)

是 java 和 c 语言之间的桥梁，由于 java 是一种半解释语言，可以被反编译出来，一种重要涉及安全的代码就使用了 C 编程，再者很多底层功能调用 C 语言都实现了 Java 没必要重复造轮子，所以定义了 JNI 接口的实现

### [8、Fragment 中 add 与 replace 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#8fragment中add与replace的区别)

add 不会重新初始化 fragment,replace 每次都会；

添加相同的 fragment 时，replace 不会有任何变化，add 会报 IllegalStateException 异常；

replace 先 remove 掉相同 id 的所有 fragment，然后在 add 当前的这个 fragment，而 add 是覆盖前一个 fragment。所以如果使用 add 一般会伴随 hide()和 show()，避免布局重叠；

使用 add，如果应用放在后台，或以其他方式被系统销毁，再打开时，hide()中引用的 fragment 会销毁，所以依然会出现布局重叠 bug，可以使用 replace 或使用 add 时，添加一个 tag 参数；

### [9、Android root 机制](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#9android-root机制)

root 指的是你有权限可以再系统上对所有档案有 "读" "写" "执行"的权力。root 机器不是真正能让你的应用程序具有 root 权限。它原理就跟 linux 下的像 sudo 这样的命令。在系统的 bin 目录下放个 su 程序并属主是 root 并有 suid 权限。则通过 su 执行的命令都具有 Android root 权限。当然使用临时用户权限想把 su 拷贝的/system/bin 目录并改属性并不是一件容易的事情。这里用到 2 个工具跟 2 个命令。把 busybox 拷贝到你有权限访问的目录然后给他赋予 4755 权限，你就可以用它做很多事了。

### [10、内存溢出和内存泄漏有什么区别？何时会产生内存泄漏？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题2021年，常见面试题及答案汇总.md#10内存溢出和内存泄漏有什么区别何时会产生内存泄漏)

内存溢出：当程序运行时所需的内存大于程序允许的最高内存，这时会出现内存溢出；

内存泄漏：在一些比较消耗资源的操作中，如果操作中内存一直未被释放，就会出现内存泄漏。比如未关闭 io,cursor。

### 11、如何切换 fragement,不重新实例化

### 12、Android 中的 ANR

### 13、谈谈 Android 的 IPC（进程间通信）机制

### 14、让 Activity 变成一个窗口

### 15、如果 Listview 中的数据源发生改变，如何更新 listview 中的数据

### 16、如何将 SQLite 数据库(dictionary.db 文件)与 apk 文件一起发布

### 17、广播接受者的生命周期？

### 18、Activity 启动模式

### 19、属性动画

### 20、android 中有哪几种解析 xml 的类？官方推荐哪种？以及它们的原理和区别。

### 21、Intent 传递数据时，可以传递哪些类型数据？

### 22、开发中都使用过哪些框架、平台

### 23、什么是 IntentService？有何优点？

### 24、如何启用 Service，如何停用 Service。

### 25、请介绍下 Android 的数据存储方式。

### 26、sim 卡的 EF 文件是什么？有何作用

### 27、activity 与 fragment 区别

### 28、wait 和 sleep 的区别

### 29、谈 MVC ，MVP，MVVM

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
