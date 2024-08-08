# Linux 最新 2023 年面试题及答案，汇总版

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、文件描述符?每个描述符的含义?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#1文件描述符每个描述符的含义)

```
[root@iz2ze76ybn73dvwmdij06zz xiaoka]# ls -l
总用量 0
-rw-r—r— 1 root root 0 4月  21 13:17 a
-rw-r—r— 1 root root 0 4月  21 13:17 b
-rw-r—r— 1 root root 0 4月  21 13:17 c
-rw-r—r— 1 root root 0 4月  21 13:17 d
-rw-r—r— 1 root root 0 4月  21 13:17 e
```

**文件类型:**

**1、** -代表文件

**2、** d 代表目录

**3、** l 代表链接

**4、** c 代表字符型设备

**5、** b 代表块设备

**6、** n 代表网络设备

**访问权限符号:**

**1、** r 代表对象是可读的

**2、** w 代表对象是可写的

**3、** x 代表对象是可执行的

若没有某种权限，在该权限位会出现单破折线。

**这 3 组权限分别对应对象的 3 个安全级别:**

**1、** 对象的属主

**2、** 对象的属组

**3、** 系统其他用户

### [2、什么是环境变量？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#2什么是环境变量)

bash shell 用一个叫作环境变量(environment variable)的特性来存储有关 shell 会话和工作环境的信息。这项特性允许你在内存中存储数据，以便程序或 shell 中运行的脚本能够轻松访问到它们。这也是存储持久数据的一种简便方法。

在 bash shell 中，环境变量分为两类:

全局变量：对于 shell 会话和所有生成的子 shell 都是可见的。 局部变量： 只对创建他们的 shell 可见。

### [3、账户默认信息？添加账户？删除用户？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#3账户默认信息添加账户删除用户)

```
[root@iz2ze76ybn73dvwmdij06zz ~]# useradd -D//查看系统默认创建用户信息
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=yes
[root@iz2ze76ybn73dvwmdij06zz ~]# useradd xiaoka//添加用户
 [root@iz2ze76ybn73dvwmdij06zz /]# userdel xiaoka//删除用户
```

### [4、lvs/nginx/haproxy 优缺点](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#4lvs/nginx/haproxy优缺点)

**Nginx 的优点是：**

**1、** 工作在网络的 7 层之上，可以针对 http 应用做一些分流的策略，比如针对域名、目录结构

它的正则规则比 HAProxy 更为强大和灵活，这也是它目前广泛流行的主要原因之一

Nginx 单凭这点可利用的场合就远多于 LVS 了。

**2、** Nginx 对网络稳定性的依赖非常小，理论上能 ping 通就就能进行负载功能，这个也是它的优势之一

相反 LVS 对网络稳定性依赖比较大，这点本人深有体会；

**3、** Nginx 安装和配置比较简单，测试起来比较方便，它基本能把错误用日志打印出来

LVS 的配置、测试就要花比较长的时间了，LVS 对网络依赖比较大。

**4、** 可以承担高负载压力且稳定，在硬件不差的情况下一般能支撑几万次的并发量，负载度比 LVS 相对小些。

**5、** Nginx 可以通过端口检测到服务器内部的故障，比如根据服务器处理网页返回的状态码、超时等等，并且会把返回错误的请求重新提交到另一个节点，不过其中缺点就是不支持 url 来检测。比如用户正在上传一个文件，而处理该上传的节点刚好在上传过程中出现故障，Nginx 会把上传切到另一台服务器重新处理，而 LVS 就直接断掉了

如果是上传一个很大的文件或者很重要的文件的话，用户可能会因此而不满。

**6、** Nginx 不仅仅是一款优秀的负载均衡器/反向代理软件，它同时也是功能强大的 Web 应用服务器

LNMP 也是近几年非常流行的 web 架构，在高流量的环境中稳定性也很好。

**7、** Nginx 现在作为 Web 反向加速缓存越来越成熟了，速度比传统的 Squid 服务器更快，可考虑用其作为反向代理加速器

**8、** Nginx 可作为中层反向代理使用，这一层面 Nginx 基本上无对手，唯一可以对比 Nginx 的就只有 lighttpd 了

不过 lighttpd 目前还没有做到 Nginx 完全的功能，配置也不那么清晰易读，社区资料也远远没 Nginx 活跃

**9、** Nginx 也可作为静态网页和图片服务器，这方面的性能也无对手。还有 Nginx 社区非常活跃，第三方模块也很多

**Nginx 的缺点是：**

**1、** Nginx 仅能支持 http、https 和 Email 协议，这样就在适用范围上面小些，这个是它的缺点

**2、** 对后端服务器的健康检查，只支持通过端口来检测，不支持通过 url 来检测

不支持 Session 的直接保持，但能通过 ip_hash 来解决

LVS：使用 Linux 内核集群实现一个高性能、高可用的负载均衡服务器

它具有很好的可伸缩性（Scalability)、可靠性（Reliability)和可管理性（Manageability)

LVS 的优点是：

**1、** 抗负载能力强、是工作在网络 4 层之上仅作分发之用，没有流量的产生

这个特点也决定了它在负载均衡软件里的性能最强的，对内存和 cpu 资源消耗比较低

**2、** 配置性比较低，这是一个缺点也是一个优点，因为没有可太多配置的东西

所以并不需要太多接触，大大减少了人为出错的几率

**3、** 工作稳定，因为其本身抗负载能力很强，自身有完整的双机热备方案

如 LVS+Keepalived，不过我们在项目实施中用得最多的还是 LVS/DR+Keepalived

**4、** 无流量，LVS 只分发请求，而流量并不从它本身出去，这点保证了均衡器 IO 的性能不会收到大流量的影响。

**5、** 应用范围较广，因为 LVS 工作在 4 层，所以它几乎可对所有应用做负载均衡，包括 http、数据库、在线聊天室等

LVS 的缺点是：

**1、** 软件本身不支持正则表达式处理，不能做动静分离

而现在许多网站在这方面都有较强的需求，这个是 Nginx/HAProxy+Keepalived 的优势所在

**2、** 如果是网站应用比较庞大的话，LVS/DR+Keepalived 实施起来就比较复杂了

特别后面有 Windows Server 的机器的话，如果实施及配置还有维护过程就比较复杂了相对而言，Nginx/HAProxy+Keepalived 就简单多了。

**HAProxy 的特点是：**

**1、** HAProxy 也是支持虚拟主机的。

**2、** HAProxy 的优点能够补充 Nginx 的一些缺点，比如支持 Session 的保持，Cookie 的引导同时支持通过获取指定的 url 来检测后端服务器的状态

**3、** HAProxy 跟 LVS 类似，本身就只是一款负载均衡软件单纯从效率上来讲 HAProxy 会比 Nginx 有更出色的负载均衡速度，在并发处理上也是优于 Nginx 的

**4、** HAProxy 支持 TCP 协议的负载均衡转发，可以对 MySQL 读进行负载均衡对后端的 MySQL 节点进行检测和负载均衡，大家可以用 LVS+Keepalived 对 MySQL 主从做负载均衡

**5、** HAProxy 负载均衡策略非常多，HAProxy 的负载均衡算法现在具体有如下 8 种：

**1、** roundrobin，表示简单的轮询，这个不多说，这个是负载均衡基本都具备的；

**2、** ?static-rr，表示根据权重，建议关注；

**3、** leastconn，表示最少连接者先处理，建议关注；

**4、** source，表示根据请求源 IP，这个跟 Nginx 的 IP_hash 机制类似

**5、** 们用其作为解决 session 问题的一种方法，建议关注；

**6、** ri，表示根据请求的 URI；

**7、** rl_param，表示根据请求的 URl 参数’balance url_param’ requires an URL parameter name；

**8、** hdr(name)，表示根据 HTTP 请求头来锁定每一次 HTTP 请求；

**9、** rdp-cookie(name)，表示根据据 cookie(name)来锁定并哈希每一次 TCP 请求。

### [5、Windows 和 Linux 的区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#5windows和linux的区别)

**1、** Windows 是微软开发的操作系统，民用操作系统，可用于娱乐、影音、上网。 Windows 操作系统具有强大的日志记录系统和强大的桌面应用。好处是它可以帮我们实现非常多绚丽多彩的效果，可以非常方便去进行娱乐、影音、上网。

**2、** Linux 的应用相对单纯很多，没有什么绚丽多彩的效果，因此 Linux 的性能是非常出色的，可以完全针对机器的配置有针对性的优化，

**3、** 简单来说 Windows 适合普通用户进行娱乐办公使用，Linux 适合软件开发部署

### [6、启动 shell](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#6启动shell)

GNU bash shell 能提供对 linux 系统的交互式访问。作为普通程序运行，通常在用户登陆终端时启动。登录时系统启动的 shell 依赖与用户账户的配置。

### [7、netstat 命令](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#7netstat-命令)

```
#Linux netstat命令用于显示网络状态。
#利用netstat指令可让你得知整个Linux系统的网络情况。
#语法：
netstat [-acCeFghilMnNoprstuvVwx][-A<网络类型>][--ip]
```

### [8、修改权限?](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#8修改权限)

chmod options mode file

比如给文件附加可以执行权限:

```
[root@xiaoka ~]# chmod +x filename
```

### [9、LVS、Nginx、HAproxy 有什么区别？工作中你怎么选择？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#9lvsnginxhaproxy有什么区别工作中你怎么选择)

LVS：是基于四层的转发

HAproxy：是基于四层和七层的转发，是专业的代理服务器

Nginx：是 WEB 服务器，缓存服务器，又是反向代理服务器，可以做七层的转发

区别：LVS 由于是基于四层的转发所以只能做端口的转发

而基于 URL 的、基于目录的这种转发 LVS 就做不了

工作选择：

HAproxy 和 Nginx 由于可以做七层的转发，所以 URL 和目录的转发都可以做

在很大并发量的时候我们就要选择 LVS，像中小型公司的话并发量没那么大

选择 HAproxy 或者 Nginx 足已，由于 HAproxy 由是专业的代理服务器

配置简单，所以中小型企业推荐使用 HAproxy

### [10、如何切换目录？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Linux/Linux最新2021年面试题及答案，汇总版.md#10如何切换目录)

语法: cd destination

destination : 相对文件路径或绝对文件路径

可以跳到存在的任意目录。

### 11、每天晚上 12 点，打包站点目录/var/www/html 备份到/data 目录下（最好每次备份按时间生成不同的备份包）

### 12、如何将本地 80 端口的请求转发到 8080 端口，当前主机 IP 为 192.168.2.1

### 13、说说 TCP/IP 的七层模型

### 14、如何查看命令历史记录?

### 15、请执行命令取出 linux 中 eth0 的 IP 地址(请用 cut，有能力者也可分别用 awk,sed 命令答)

### 16、如何查找匹配的文件？基于文件属性？

### 17、Ls 命令执行什么功能？ 可以带哪些参数，有什么区别？

### 18、如何中断一个进程?

### 19、怎么查看系统支持的所有信号？

### 20、如何用 sed 只打印第 5 行?删除第一行？替换字符串?

### 21、Linux 的目录结构是怎样的？

### 22、请列出你了解的 web 服务器负载架构

### 23、建立软链接(快捷方式)，以及硬链接的命令。

### 24、交互方式

### 25、讲述一下 Tomcat8005、8009、8080 三个端口的含义？

### 26、Tomcat 和 Resin 有什么区别，工作中你怎么选择？

### 27、find （find：找到的意思）查找指定文件或目录

### 28、怎样一页一页地查看一个大文件的内容呢？

### 29、mkdir （mkdir：创建目录） 创建目录

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
