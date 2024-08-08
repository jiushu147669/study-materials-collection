# Linux 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、vi （VIsual：视觉）文本编辑器 类似 win 的记事本 （操作类似于地下的 vim 命令，看底下 vim 的操作）](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#1vi-visual：视觉文本编辑器-类似win的记事本-操作类似于地下的vim命令看底下vim-的操作)

### [2、什么是中间件？什么是 jdk？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#2什么是中间件什么是jdk)

中间件介绍：

中间件是一种独立的系统软件或服务程序，分布式应用软件借助这种软件在不同的技术之间共享资源

中间件位于客户机/ 服务器的操作系统之上，管理计算机资源和网络通讯

是连接两个独立应用程序或独立系统的软件。相连接的系统，即使它们具有不同的接口

但通过中间件相互之间仍能交换信息。执行中间件的一个关键途径是信息传递

通过中间件，应用程序可以工作于多平台或 OS 环境。

jdk：jdk 是 Java 的开发工具包

它是一种用于构建在 Java 平台上发布的应用程序、applet 和组件的开发环境

### [3、Linux 使用的进程间通信方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#3linux-使用的进程间通信方式)

> 了解即可，不需要太深入。

**1、** 管道(pipe)、流管道(s_pipe)、有名管道(FIFO)。

**2、** 信号(signal) 。

**3、** 消息队列。

**4、** 共享内存。

**5、** 信号量。

**6、** 套接字(socket) 。

### [4、使用什么命令查看 ip 地址及接口信息？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#4使用什么命令查看-ip-地址及接口信息)

**答案：**

ifconfig

### [5、你常用的 Nginx 模块，用来做什么](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#5你常用的nginx模块用来做什么)

**1、** rewrite 模块，实现重写功能

**2、** access 模块：来源控制

**3、** ssl 模块：安全加密

**4、** ngx_http_gzip_module：网络传输压缩模块

**5、** ngx_http_proxy_module 模块实现代理

**6、** ngx_http_upstream_module 模块实现定义后端服务器列表

**7、** ngx_cache_purge 实现缓存清除功能

### [6、free 命令 （显示系统内存）](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#6free-命令-显示系统内存)

```
#显示系统内存使用情况，包括物理内存、交互区内存(swap)和内核缓冲区内存。
-b 以Byte显示内存使用情况
-k 以kb为单位显示内存使用情况
-m 以mb为单位显示内存使用情况
-g 以gb为单位显示内存使用情况
-s<间隔秒数> 持续显示内存
-t 显示内存使用总合
```

### [7、用什么命令对一个文件的内容进行统计？(行号、单词数、字节数)](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#7用什么命令对一个文件的内容进行统计行号单词数字节数)

**答案：**

wc 命令 - c 统计字节数 - l 统计行数 - w 统计字数。

### [8、打印文件第一行到第三行?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#8打印文件第一行到第三行)

文件 tomcat 中内容:

```
?  apache cat tomcat
text21
text22
text23
start
stop
restart
end
```

```
? apache head -3 tomcat
text21
text22
text23
? apache sed -n '1,3p' tomcat
text21
text22
text23
? apache awk 'NR>=1&&NR<=3' tomcat
text21
text22
text23
```

### [9、BASH 和 DOS 之间的基本区别是什么？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#9bash和dos之间的基本区别是什么)

**BASH 和 DOS 控制台之间的主要区别在于 3 个方面：**

**1、** BASH 命令区分大小写，而 DOS 命令则不区分;

**2、** 在 BASH 下，/ character 是目录分隔符，\作为转义字符。在 DOS 下，/用作命令参数分隔符，\是目录分隔符

**3、** DOS 遵循命名文件中的约定，即 8 个字符的文件名后跟一个点，扩展名为 3 个字符。BASH 没有遵循这样的惯例。

### [10、如果你的助手想要打印出当前的目录栈，你会建议他怎么做？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新面试题2021年，常见面试题及答案汇总.md#10如果你的助手想要打印出当前的目录栈你会建议他怎么做)

**答案：**

使用 Linux 命令 dirs 可以将当前的目录栈打印出来。

```
[root@localhost ~]# dirs
/usr/share/X11
```

【附】：目录栈通过 pushd popd 来操作。

### 11、使用什么命令查看用过的命令列表?

### 12、使用什么命令查看网络是否连通?

### 13、快速判断某个特定目录是否有超大文件？

### 14、| 管道命令（把多个命令组合起来使用）

### 15、数据字典属于哪一个用户的？

### 16、如何写一条规则，拒绝某个 ip 访问本机 8080 端口?

### 17、keepalive 的工作原理和如何做到健康检查

### 18、什么是运维？什么是游戏运维？

### 19、删除文件用哪个命令？如果需要连目录及目录下文件一块删除呢？删除空文件夹用什么命令？

### 20、同步时间命令

### 21、如何执行可以执行文件?

### 22、bash 手册

### 23、什么叫 CC 攻击？什么叫 DDOS 攻击？

### 24、源码安装通常的路子?

### 25、查看当前谁在使用该主机用什么命令? 查找自己所在的终端信息用什么命令?

### 26、删除文件?强制删除？递归删除?

### 27、如何查看目录中的文件？区分哪些是文件哪些是目录?递归查?

### 28、查看文件内容有哪些命令可以使用？

### 29、cd （change directory：英文释义是改变目录）切换目录

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
