# Python 最新 2023 年面试题，高级面试题及附答案解析

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是 Twemproxy](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#1什么是twemproxy)

Twemproxy 是一种代理分片机制，由 Twitter 开源。Twemproxy 作为代理，可接受来自多个程序的访问，按照路由规则，转发给后台的各个 Redis 服务器，再原路返回。该方案很好的解决了单个 Redis 实例承载能力的问题。当然，Twemproxy 本身也是单点，需要用 Keepalived 做高可用方案。通过 Twemproxy 可以使用多台服务器来水平扩张 Redis 服务，可以有效的避免单点故障问题。虽然使用 Twemproxy 需要更多的硬件资源和在 Redis 性能有一定的损失（twitter 测试约 20%），但是能够提高整个系统的 HA 也是相当划算的。不熟悉 twemproxy 的同学，如果玩过 nginx 反向代理或者 MySQL proxy，那么你肯定也懂 twemproxy 了。其实 twemproxy 不光实现了 Redis 协议

### [2、写出如下代码的输出结果](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#2写出如下代码的输出结果)

```python
def decorator_a(func):
print('Get in decorator_a')
def inner_a(*args, **kwargs):
print('Get in inner_a')
return func(*args, **kwargs)
return inner_a

def decorator_b(func):
print('Get in decorator_b')
def inner_b(*args, **kwargs):
print('Get in inner_b')
return func(*args, **kwargs)
return inner_b

@decorator_b #f=decorator_b(f)
@decorator_a #f=decorator_a(f)
def f(x):
print('Get in f')
return x 2
f(1)
```

答案

> Get in decorator_a

Get in decorator_b

Get in inner_b

Get in inner_a

Get in f

解释

> 当我们对 f 传入参数 1 进行调用时，inner_b 被调用了，他会先打印 Get in inner_b,然后在 inner_b 内部调用了 inner_a,所以会再打印 Get in inner_a,然后再 inner_a 内部调用原来的 f,并且将结果作为最终的返回总结：装饰器函数在被装饰函数定义好后立即执行从下往上执行函数调用时从上到下执行

### [3、如何使用 python 删除一个文件或者文件夹？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#3如何使用python删除一个文件或者文件夹)

```python
import os
import shutil
os.remove(path) # 删除文件
os.removedirs(path) # 删除空文件夹
shutil.rmtree(path) # 删除文件夹，可以为空也可以不为空
```

### [4、为什么学 python](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#4为什么学python)

答题路线：a、python 的优点，b、python 的应用领域广

**具体：**

优点

**1、** python 语法非常优雅，简单易学

**2、** 免费开源

**3、** 跨平台，可以自由移植

**4、** 可扩展，可嵌入性强

**5、** 第三方库丰富

**应用领域**

**1、** 在系统编程中应用广泛，比如说 shell 工具。

**2、** 在网络爬虫方面功能非常强大，常用的库如 scrapy，request 等

**3、** 在 web 开发中使用也很广泛，如很多大型网站都用 python 开发的，如 ins，youtube 等，常用的框架如 django，flask 等

**4、** python 在系统运维中应用广泛，尤其在 linux 运维方面，基本上都是自动化运维。

**5、** 在人工智能，云计算，金融等方面也应用非常广泛。

### [5、如何修改本地 hosts 文件](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#5如何修改本地hosts文件)

进入 c:\windows\system32\drivers\etc 进行修改

### [6、编写程序，查找文本文件中最长的单词](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#6编写程序查找文本文件中最长的单词)

```
def longest_word(filename):
    with open(filename, 'r') as infile:
              words = infile.read().split()
    max_len = len(max(words, key=len))
    return [word for word in words if len(word) == max_len]

print(longest_word('test.txt'))
----------------------------------------------------
['comprehensions']
```

### [7、用一行代码实现数值交换](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#7用一行代码实现数值交换)

**1、** a=1

**2、** b=2

**3、** 答案：a,b=b,a

### [8、数据库的导入与导出命令](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#8数据库的导入与导出命令)

**1、** 导出(MySQLdump)

**2、** 导出数据和表结构

**3、** MySQLdump -uroot -p dbname > dbname .sql

**4、** 只导出表结构

**5、** MySQLdump -uroot -p -d dbname > dbname .sql

6、导入

**7、** MySQL -u 用户名 -p 密码 数据库名 < 数据库名.sql

### [9、Redis 中 watch 的作用](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#9redis中watch的作用)

**1、** watch 用于在进行事务操作的最后一步也就是在执行 exec 之前对某个 key 进行监视

**2、** 如果这个被监视的 key 被改动，那么事务就被取消，否则事务正常执行.

**3、** 一般在 MULTI 命令前就用 watch 命令对某个 key 进行监控.如果想让 key 取消被监控，可以用 unwatch 命令

### [10、MySQL 常见数据库引擎及区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新2021年面试题，高级面试题及附答案解析.md#10mysql常见数据库引擎及区别)

**1、** InnoDB：用于事务处理应用程序，具有众多特性，包括 ACID 事务支持。(提供行级锁)

**2、** MyISAM：默认的 MySQL 插件式存储引擎，它是在 Web、数据仓储和其他应用环境下最常使用的存储引擎之一。注意，通过更改 STORAGE_ENGINE 配置变量，能够方便地更改 MySQL 服务器的默认存储引擎。

**3、** Memory：将所有数据保存再 RAM 中

### 11、求以下代码结果：

### 12、有两个字符串列表 a 和 b，每个字符串是由逗号隔开的一些字符

### 13、怎样获取字典中所有键的列表？

### 14、解释 Python 的内置数据结构？

### 15、三元运算编写格式

### 16、列表推导式[i for i in range(10)]和生成式表达式(i for i in range(10))的区别

### 17、什么是局域网和广域网

### 18、描述以下 dict 的 items 和 iteritems 的区别

### 19、为何不建议以下划线作为标识符的开头

### 20、如何打乱一个排好序的列表

### 21、什么是多态？

### 22、threading.local 的作用

### 23、vuex 的作用

### 24、or 和 and

### 25、解释 Python 中 map()函数？

### 26、通过什么途径学习 python

### 27、对字典 d={'a':30,'g':17,'b':25,'c':18,'d':50,'e':36,'f':57,'h':25}按照 value 字段进行排序

### 28、lambda 表达式格式以及应用场景？

### 29、为什么数据很大的时候使用 limit offset 分页时，越往后翻速度越慢，如何优化？

### 30、IO 多路复用的作用？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
