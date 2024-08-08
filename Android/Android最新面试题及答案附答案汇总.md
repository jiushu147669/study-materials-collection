# Android 最新面试题及答案附答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、Android 的四大组件是哪些，它们的作用？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#1android的四大组件是哪些它们的作用)

---

**1、** Activity：Activity 是 Android 程序与用户交互的窗口，是 Android 构造块中最基本的一种，它需要为保持各界面的状态，做很多持久化的事情，妥善管理生命周期以及一些跳转逻辑

**2、** service：后台服务于 Activity，封装有一个完整的功能逻辑实现，接受上层指令，完成相关的事物，定义好需要接受的 Intent 提供同步和异步的接口

**3、** Content Provider：是 Android 提供的第三方应用数据的访问方案，可以派生 Content Provider 类，对外提供数据，可以像数据库一样进行选择排序，屏蔽内部数据的存储细节，向外提供统一的借口模型，大大简化上层应用，对数据的整合提供了更方便的途径

**4、** BroadCast Receiver：接受一种或者多种 Intent 作触发事件，接受相关消息，做一些简单处理，转换成一条 Notification，统一了 Android 的事件广播模型

### [2、android:gravity 与 android:layout_gravity 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#2android:gravity与android:layout_gravity的区别)

gravity：表示组件内元素的对齐方式

layout_gravity：相对于父类容器，该视图组件的对齐方式

### [3、GLSurfaceView](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#3glsurfaceview)

基于 SurfaceView 视图再次进行拓展的视图类，专用于 3D 游戏开发的视图，是 surfaceView 的子类，openGL 专用

### [4、什么是 aar?aar 是 jar 有什么区别?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#4什么是aaraar是jar有什么区别)

“aar”包是 Android 的类库项目的二进制发行包。

文件扩展名是.aar，maven 项目类型应该也是 aar，但文件本身是带有以下各项的 zip 文件：

**1、** /AndroidManifest.xml (mandatory)

**2、** /classes.jar (mandatory)

**3、** /res/ (mandatory)

**4、** /R.txt (mandatory)

**5、** /assets/ (optional)

**6、** /libs/\*.jar (optional)

**7、** /jni//\*.so (optional)

**8、** /proguard.txt (optional)

**9、** /lint.jar (optional)

这些条目是直接位于 zip 文件根目录的。 其中 R.txt 文件是 aapt 带参数–output-text-symbols 的输出结果。

jar 打包不能包含资源文件，比如一些 drawable 文件、xml 资源文件之类的,aar 可以。

### [5、IntentService 有何优点?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#5intentservice有何优点)

Acitivity 的进程，当处理 Intent 的时候，会产生一个对应的 Service； Android 的进程处理器现在会尽可能的不 kill 掉你；非常容易使用

### [6、跟 activity 和 Task 有关的 Intent 启动方式有哪些？其含义？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#6跟activity和task-有关的-intent启动方式有哪些其含义)

核心的 Intent Flag 有

**1、** FLAG_ACTIVITY_NEW_TAS

**2、** FLAG_ACTIVITY_CLEAR_TOP

**3、** FLAG_ACTIVITY_RESET_TASK_IF_NEEDED

**4、** FLAG_ACTIVITY_SINGLE_TO

**5、** FLAG_ACTIVITY_NEW_TAS

如果设置，这个 Activity 会成为历史 stack 中一个新 Task 的开始。一个 Task（从启动它的 Activity 到下一个 Task 中的 Activity）定义了用户可以迁移的 Activity 原子组。Task 可以移动到前台和后台；在某个特定 Task 中的所有 Activity 总是保持相同的次序

这个标志一般用于呈现“启动”类型的行为：它们提供用户一系列可以单独完成的事情，与启动它们的 Activity 完全无关。

使用这个标志，如果正在启动的 Activity 的 Task 已经在运行的话，那么，新的 Activity 将不会启动；代替的，当前 Task 会简单的移入前台。参考 FLAG_ACTIVITY_MULTIPLE_TASK 标志，可以禁用这一行为。

这个标志不能用于调用方对已经启动的 Activity 请求结果。

**FLAG_ACTIVITY_CLEAR_TOP**

如果设置，并且这个 Activity 已经在当前的 Task 中运行，因此，不再是重新启动一个这个 Activity 的实例，而是在这个 Activity 上方的所有 Activity 都将关闭，然后这个 Intent 会作为一个新的 Intent 投递到老的 Activity（现在位于顶端）中。

例如，假设一个 Task 中包含这些 Activity：A，B，C，D。如果 D 调用了 startActivity()，并且包含一个指向 Activity B 的 Intent，那么，C 和 D 都将结束，然后 B 接收到这个 Intent，因此，目前 stack 的状况是：A，B。

上例中正在运行的 Activity B 既可以在 onNewIntent()中接收到这个新的 Intent，也可以把自己关闭然后重新启动来接收这个 Intent。如果它的启动模式声明为 “multiple”(默认值)，并且你没有在这个 Intent 中设置 FLAG_ACTIVITY_SINGLE_TOP 标志，那么它将关闭然后重新创建；对于其它的启动模式，或者在这个 Intent 中设置 FLAG_ACTIVITY_SINGLE_TOP 标志，都将把这个 Intent 投递到当前这个实例的 onNewIntent()中。

这个启动模式还可以与 FLAG_ACTIVITY_NEW_TASK 结合起来使用：用于启动一个 Task 中的根 Activity，它会把那个 Task 中任何运行的实例带入前台，然后清除它直到根 Activity。这非常有用，例如，当从 Notification Manager 处启动一个 Activity。

**FLAG_ACTIVITY_RESET_TASK_IF_NEEDED**

如果设置这个标志，这个 activity 不管是从一个新的栈启动还是从已有栈推到栈顶，它都将以 the front door of the task 的方式启动。这就讲导致任何与应用相关的栈都讲重置到正常状态（不管是正在讲 activity 移入还是移除），如果需要，或者直接重置该栈为初始状态。

**FLAG_ACTIVITY_SINGLE_TOP**

如果设置，当这个 Activity 位于历史 stack 的顶端运行时，不再启动一个新的

**FLAG_ACTIVITY_BROUGHT_TO_FRONT**

这个标志一般不是由程序代码设置的，如在 launchMode 中设置 singleTask 模式时系统帮你设定。

**FLAG_ACTIVITY_CLEAR_WHEN_TASK_RESET**

如果设置，这将在 Task 的 Activity stack 中设置一个还原点，当 Task 恢复时，需要清理 Activity。也就是说，下一次 Task 带着 FLAG_ACTIVITY_RESET_TASK_IF_NEEDED 标记进入前台时（典型的操作是用户在主画面重启它），这个 Activity 和它之上的都将关闭，以至于用户不能再返回到它们，但是可以回到之前的 Activity。

这在你的程序有分割点的时候很有用。例如，一个 e-mail 应用程序可能有一个操作是查看一个附件，需要启动图片浏览 Activity 来显示。这个 Activity 应该作为 e-mail 应用程序 Task 的一部分，因为这是用户在这个 Task 中触发的操作。然而，当用户离开这个 Task，然后从主画面选择 e-mail app，我们可能希望回到查看的会话中，但不是查看图片附件，因为这让人困惑。通过在启动图片浏览时设定这个标志，浏览及其它启动的 Activity 在下次用户返回到 mail 程序时都将全部清除。

**FLAG_ACTIVITY_EXCLUDE_FROM_RECENTS**

如果设置，新的 Activity 不会在最近启动的 Activity 的列表中保存。

**FLAG_ACTIVITY_FORWARD_RESULT**

如果设置，并且这个 Intent 用于从一个存在的 Activity 启动一个新的 Activity，那么，这个作为答复目标的 Activity 将会传到这个新的 Activity 中。这种方式下，新的 Activity 可以调用 setResult(int)，并且这个结果值将发送给那个作为答复目标的 Activity。

**FLAG_ACTIVITY_LAUNCHED_FROM_HISTORY**

这个标志一般不由应用程序代码设置，如果这个 Activity 是从历史记录里启动的（常按 HOME 键），那么，系统会帮你设定。

**FLAG_ACTIVITY_MULTIPLE_TASK**

不要使用这个标志，除非你自己实现了应用程序启动器。与 FLAG_ACTIVITY_NEW_TASK 结合起来使用，可以禁用把已存的 Task 送入前台的行为。当设置时，新的 Task 总是会启动来处理 Intent，而不管这是是否已经有一个 Task 可以处理相同的事情。

由于默认的系统不包含图形 Task 管理功能，因此，你不应该使用这个标志，除非你提供给用户一种方式可以返回到已经启动的 Task。

如果 FLAG_ACTIVITY_NEW_TASK 标志没有设置，这个标志被忽略。

**FLAG_ACTIVITY_NO_ANIMATION**

如果在 Intent 中设置，并传递给 Context.startActivity()的话，这个标志将阻止系统进入下一个 Activity 时应用 Acitivity 迁移动画。这并不意味着动画将永不运行——如果另一个 Activity 在启动显示之前，没有指定这个标志，那么，动画将被应用。这个标志可以很好的用于执行一连串的操作，而动画被看作是更高一级的事件的驱动。

**FLAG_ACTIVITY_NO_HISTORY**

如果设置，新的 Activity 将不再历史 stack 中保留。用户一离开它，这个 Activity 就关闭了。这也可以通过设置 noHistory 特性。

**FLAG_ACTIVITY_NO_USER_ACTION**

如果设置，作为新启动的 Activity 进入前台时，这个标志将在 Activity 暂停之前阻止从最前方的 Activity 回调的 onUserLeaveHint()。

典型的，一个 Activity 可以依赖这个回调指明显式的用户动作引起的 Activity 移出后台。这个回调在 Activity 的生命周期中标记一个合适的点，并关闭一些 Notification。

如果一个 Activity 通过非用户驱动的事件，如来电或闹钟，启动的，这个标志也应该传递给 Context.startActivity，保证暂停的 Activity 不认为用户已经知晓其 Notification。

**FLAG_ACTIVITY_PREVIOUS_IS_TOP**

If set and this intent is being used to launch a new activity from an existing one, the current activity will not be counted as the top activity for deciding whether the new intent should be delivered to the top instead of starting a new one、The previous activity will be used as the top, with the assumption being that the current activity will finish itself immediately.

**FLAG_ACTIVITY_REORDER_TO_FRONT**

如果在 Intent 中设置，并传递给 Context.startActivity()，这个标志将引发已经运行的 Activity 移动到历史 stack 的顶端。

例如，假设一个 Task 由四个 Activity 组成：A,B,C,D。如果 D 调用 startActivity()来启动 Activity B，那么，B 会移动到历史 stack 的顶端，现在的次序变成 A,C,D,B。如果 FLAG_ACTIVITY_CLEAR_TOP 标志也设置的话，那么这个标志将被忽略。

### [7、Fragment 在你们项目中的使用](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#7fragment-在你们项目中的使用)

Fragment 是 android3.0 以后引入的的概念，做局部内容更新更方便，原来为了到达这一点要把多个布局放到一个 activity 里面，现在可以用多 Fragment 来代替，只有在需要的时候才加载 Fragment，提高性能。

**Fragment 的好处：**

**1、** Fragment 可以使你能够将 activity 分离成多个可重用的组件，每个都有它自己的生命周期和 UI。

**2、** Fragment 可以轻松得创建动态灵活的 UI 设计，可以适应于不同的屏幕尺寸。从手机到平板电脑。

**3、** Fragment 是一个独立的模块,紧紧地与 activity 绑定在一起。可以运行中动态地移除、加入、交换等。

**4、** Fragment 提供一个新的方式让你在不同的安卓设备上统一你的 UI。

**5、** Fragment 解决 Activity 间的切换不流畅，轻量切换。

**6、** Fragment 替代 TabActivity 做导航，性能更好。

**7、** Fragment 在 4.2.版本中新增嵌套 fragment 使用方法，能够生成更好的界面效果。

### [8、你一般在开发项目中都使用什么设计模式？如何来重构，优化你的代码？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#8你一般在开发项目中都使用什么设计模式如何来重构优化你的代码)

较为常用的就是单例设计模式，工厂设计模式以及观察者设计模式,

一般需要保证对象在内存中的唯一性时就是用单例模式,例如对数据库操作的 SqliteOpenHelper 的对象。

工厂模式主要是为创建对象提供过渡接口，以便将创建对象的具体过程屏蔽隔离起来，达到提高灵活性的目的。

观察者模式定义对象间的一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新

### [9、描述一下 android 的系统架构](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#9描述一下android的系统架构)

android 系统架构分从下往上为 linux 内核层、运行库、应用程序框架层、和应用程序层。

linuxkernel：负责硬件的驱动程序、网络、电源、系统安全以及内存管理等功能。

libraries 和 android runtime：libraries：即 c/c++函数库部分，大多数都是开放源代码的函数库，例如 webkit（引擎），该函数库负责 android 网页浏览器的运行，例如标准的 c 函数库 libc、openssl、sqlite 等，当然也包括支持游戏开发 2dsgl 和 3dopengles，在多媒体方面有 mediaframework 框架来支持各种影音和图形文件的播放与显示，例如 mpeg4、h.264、mp3、 aac、amr、jpg 和 png 等众多的多媒体文件格式。android 的 runtime 负责解释和执行生成的 dalvik 格式的字节码。

applicationframework（应用软件架构），java 应用程序开发人员主要是使用该层封装好的 api 进行快速开发。

applications:该层是 java 的应用程序层，android 内置的 googlemaps、e-mail、即时通信工具、浏览器、mp3 播放器等处于该层，java 开发人员开发的程序也处于该层，而且和内置的应用程序具有平等的位置，可以调用内置的应用程序，也可以替换内置的应用程序。

上面的四个层次，下层为上层服务，上层需要下层的支持，调用下层的服务，这种严格分层的方式带来的极大的稳定性、灵活性和可扩展性，使得不同层的开发人员可以按照规范专心特定层的开发。

android 应用程序使用框架的 api 并在框架下运行，这就带来了程序开发的高度一致性，另一方面也告诉我们，要想写出优质高效的程序就必须对整个 applicationframework 进行非常深入的理解。精通 applicationframework，你就可以真正的理解 android 的设计和运行机制，也就更能够驾驭整个应用层的开发。

### [10、如何将 SQLite 数据库(dictionary.db 文件)与 apk 文件一起发布](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Android/Android最新面试题及答案附答案汇总.md#10如何将sqlite数据库dictionarydb文件与apk文件一起发布)

把这个文件放在/res/raw 目录下即可。res\raw 目录中的文件不会被压缩，这样可以直接提取该目录中的文件，会生成资源 id。

### 11、Hander 原理

### 12、activity 之间传递参数，除了 intent，广播接收器，contentProvider 之外，还有那些方法？

### 13、ListView 的优化方案

### 14、Android 系统的架构

### 15、String,StringBuffer,StringBuilder 的区别

### 16、音视频相关类

### 17、ListView 如何实现分页加载

### 18、SQLite 支持事务吗?添加删除如何提高性能?

### 19、如何修改 Activity 进入和退出动画

### 20、FragmentPagerAdapter 与 与 FragmentStatePagerAdapter 的区别与使用场景？

### 21、什么是 ANR 如何避免它？

### 22、View 的分发机制，滑动冲突

### 23、如果后台的 Activity 由于某原因被系统回收了，如何在被系统回收之前保存当前状态？

### 24、16Android 性能优化

### 25、SQLite 支持事务吗? 添加删除如何提高性能?

### 26、Fragment 的生命周期

### 27、属性动画，例如一个 button 从 A 移动到 B 点，B 点还是可以响应点击事件，这个原理是什么？

### 28、android 系统的优势和不足

### 29、RecyclerView 和 ListView 的区别

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
