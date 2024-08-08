# Android 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、andorid 应用第二次登录实现自动登录](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#1andorid-应用第二次登录实现自动登录)

前置条件是所有用户相关接口都走 https，非用户相关列表类数据走 http。

**步骤**

**1、** 第一次登陆 getUserInfo 里带有一个长效 token，该长效 token 用来判断用户是否登陆和换取短 token

**2、** 把长效 token 保存到 SharedPreferences

**3、** 接口请求用长效 token 换取短 token，短 token 服务端可以根据你的接口最后一次请求作为标示，超时时间为一天。

**4、** 所有接口都用短效 token

**5、** 如果返回短效 token 失效，执行第 3 步，再直接当前接口

**6、** 如果长效 token 失效（用户换设备或超过一月），提示用户登录。

### [2、ContentProvider 与 sqlite 有什么不一样的？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#2contentprovider与sqlite有什么不一样的)

```
ContentProvider会对外隐藏内部实现，只需要关注访问contentProvider的uri即可，contentProvider应用在应用间共享。
Sqlite操作本应用程序的数据库。
ContentProiver可以对本地文件进行增删改查操作
```

### [3、AIDL 的全称是什么？如何工作？能处理哪些类型的数据？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#3aidl的全称是什么如何工作能处理哪些类型的数据)

全称是：Android Interface Define Language

在 Android 中, 每个应用程序都可以有自己的进程、在写 UI 应用的时候, 经常要用到 Service、在不同的进程中, 怎样传递对象呢?显然, Java 中不允许跨进程内存共享、因此传递对象, 只能把对象拆分成操作系统能理解的简单形式, 以达到跨界对象访问的目的、在 J2EE 中,采用 RMI 的方式, 可以通过序列化传递对象、在 Android 中, 则采用 AIDL 的方式、理论上 AIDL 可以传递 Bundle,实际上做起来却比较麻烦。

AIDL(AndRoid 接口描述语言)是一种借口描述语言; 编译器可以通过 aidl 文件生成一段代码，通过预先定义的接口达到两个进程内部通信进程的目的、如果需要在一个 Activity 中, 访问另一个 Service 中的某个对象, 需要先将对象转化成 AIDL 可识别的参数(可能是多个参数), 然后使用 AIDL 来传递这些参数, 在消息的接收端, 使用这些参数组装成自己需要的对象.

AIDL 的 IPC 的机制和 COM 或 CORBA 类似, 是基于接口的，但它是轻量级的。它使用代理类在客户端和实现层间传递值、如果要使用 AIDL, 需要完成 2 件事情:

**1、** 引入 AIDL 的相关类.;

**2、** 调用 aidl 产生的 class.

**AIDL 的创建方法:**

AIDL 语法很简单,可以用来声明一个带一个或多个方法的接口，也可以传递参数和返回值。 由于远程调用的需要, 这些参数和返回值并不是任何类型.下面是些 AIDL 支持的数据类型:

**1、** 不需要 import 声明的简单 Java 编程语言类型(int,boolean 等)

**2、** String, CharSequence 不需要特殊声明

**3、** List, Map 和 Parcelables 类型, 这些类型内所包含的数据成员也只能是简单数据类型, String 等其他比支持的类型.

(另外: 我没尝试 Parcelables, 在 Eclipse+ADT 下编译不过, 或许以后会有所支持)

### [4、activity，fragment 传值问题](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#4activityfragment传值问题)

通过 Bundle 传值，在 activty 定义变量传值，扩展 fragment 创建传值

### [5、Manifest.xml 文件中主要包括哪些信息？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#5manifestxml文件中主要包括哪些信息)

**1、** manifest：根节点，描述了 package 中所有的内容。

**2、** uses-permission：请求你的 package 正常运作所需赋予的安全许可。

**3、** permission： 声明了安全许可来限制哪些程序能你 package 中的组件和功能。

**4、** instrumentation：声明了用来测试此 package 或其他 package 指令组件的代码。

**5、** application：包含 package 中 application 级别组件声明的根节点。

**6、** activity：Activity 是用来与用户交互的主要工具。

**7、** receiver：IntentReceiver 能使的 application 获得数据的改变或者发生的操作，即使它当前不在运行。

**8、** service：Service 是能在后台运行任意时间的组件。

**9、** provider：ContentProvider 是用来管理持久化数据并发布给其他应用程序使用的组件。

### [6、简要解释一下 activity、 intent 、intent filter、service、Broadcase、BroadcaseReceiver](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#6简要解释一下activity-intent-intent-filterservicebroadcasebroadcasereceiver)

一个 activity 呈现了一个用户可以操作的可视化用户界面；一个 service 不包含可见的用户界面，而是在后台运行，可以与一个 activity 绑定，通过绑定暴露出来接口并与其进行通信；一个 broadcast receiver 是一个接收广播消息并做出回应的 component，broadcast receiver 没有界面；一个 intent 是一个 Intent 对象，它保存了消息的内容。对于 activity 和 service 来说，它指定了请求的操作名称和待操作数据的 URI，Intent 对象可以显式的指定一个目标 component。如果这样的话，android 会找到这个 component(基于 manifest 文件中的声明)并激活它。但如果一个目标不是显式指定的，android 必须找到响应 intent 的最佳 component。它是通过将 Intent 对象和目标的 intent filter 相比较来完成这一工作的；一个 component 的 intent filter 告诉 android 该 component 能处理的 intent。intent filter 也是在 manifest 文件中声明的。

### [7、Serializable 和 Parcelable 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#7serializable-和-parcelable-的区别)

如果存储在内存中，推荐使用 parcelable，使用 serialiable 在序列化的时候会产生大量的临时变量，会引起频繁的 GC

如果存储在硬盘上，推荐使用 Serializable，虽然 serializable 效率较低

Serializable 的实现：只需要实现 Serializable 接口，就会自动生成一个序列化 id

Parcelable 的实现：需要实现 Parcelable 接口，还需要 Parcelable.CREATER 变量

### [8、什么是 AIDL？如何使用？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#8什么是-aidl如何使用)

aidl 是 Android interface definition Language 的英文缩写，意思 Android 接口定义语言。

使用 aidl 可以帮助我们发布以及调用远程服务，实现跨进程通信。

**1、** 将服务的 aidl 放到对应的 src 目录，工程的 gen 目录会生成相应的接口类

**2、** 我们通过 bindService（Intent，ServiceConnect，int）方法绑定远程服务，在 bindService 中 有 一 个 ServiceConnec 接 口 ， 我 们 需 要 覆 写 该 类 的 onServiceConnected(ComponentName,IBinder)方法，这个方法的第二个参数 IBinder 对象其实就是已经在 aidl 中定义的接口，因此我们可以将 IBinder 对象强制转换为 aidl 中的接口类。我们通过 IBinder 获取到的对象（也就是 aidl 文件生成的接口）其实是系统产生的代理对象，该代理对象既可以跟我们的进程通信， 又可以跟远程进程通信， 作为一个中间的角色实现了进程间通信。

### [9、嵌入式操作系统内存管理有哪几种， 各有何特性](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#9嵌入式操作系统内存管理有哪几种-各有何特性)

页式，段式，段页，用到了 MMU,虚拟空间等技术

### [10、注册广播的几种方法?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新2021年面试题，高级面试题及附答案解析.md#10注册广播的几种方法)

**1、** 静态注册:在清单文件中注册， 常见的有监听设备启动，常驻注册不会随程序生命周期改变

**2、** 动态注册:在代码中注册，随着程序的结束，也就停止接受广播了补充一点：有些广播只能通过动态方式注册，比如时间变化事件、屏幕亮灭事件、电量变更事件，因为这些事件触发频率通常很高，如果允许后台监听，会导致进程频繁创建和销毁，从而影响系统整体性能

### 11、请介绍下 ContentProvider 是如何实现数据共享的

### 12、请描述一下 Intent 和 IntentFilter

### 13、描述下 Handler 机制

### 14、定位项目中，如何选取定位方案，如何平衡耗电与实时位置的精度？

### 15、如果后台的 Activity 由于某原因被系统回收了，如何在被系统回收之前保存当前状态？

### 16、Android 引入广播机制的用意

### 17、ListView 如何提高其效率？

### 18、请解释下 Android 程序运行时权限与文件系统权限的区别？

### 19、什么情况会导致 Force Close ？如何避免？能否捕获导致其的异常？

### 20、Android 中，帧动画

### 21、activity，service，intent 之间的关系

### 22、Service 是否在 main thread 中执行, service 里面是否能执行耗时的操作?

### 23、AsyncTask 使用在哪些场景？它的缺陷是什么？如何解决？

### 24、事件分发中的 onTouch 和 onTouchEvent 有什么区别，又该如何使用？

### 25、Android 线程间通信有哪几种方式（重要）

### 26、消息推送的方式

### 27、如何退出 Activity

### 28、如何将一个 Activity 设置成窗口的样式。

### 29、如果有个 100M 大的文件，需要上传至服务器中，而服务器 form 表单最大只能上传 2M，可以用什么方法。

### 30、如何保存 activity 的状态？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
