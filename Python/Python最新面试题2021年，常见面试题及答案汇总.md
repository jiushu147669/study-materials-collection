# Python 最新面试题 2023 年，常见面试题及答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、什么是 Python 中的猴子补丁？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#1什么是python中的猴子补丁)

猴子补丁(monkey patching)，是指在运行时动态修改类或模块。

```
from SomeOtherProduct.SomeModule import SomeClass

def speak(self):
    return "Hello!"

SomeClass.speak = speak
```

### [2、实现 99 乘法表（使用两种方法）](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#2实现99乘法表使用两种方法)

```python
print('\n'.join(['\t'.join(['{}*{}={}'.format(x,y,x*y) for x in range(1,y+1)]) for y in range(1,10)]))
```

```python
for i in range(1,10):
for j in range(1,i+1):
print('%s*%s=%s'%(i,j,i*j),end='\t')
else:
print()
```

### [3、什么是负索引？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#3什么是负索引)

我们先创建这样一个列表：

```
>>> mylist=[0,1,2,3,4,5,6,7,8]
```

负索引和正索引不同，它是从右边开始检索。

```
>>> mylist[-3]
```

运行结果：

```
6
```

它也能用于列表中的切片：

```
>>> mylist[-6:-1]
```

结果：

```
[3, 4, 5, 6, 7]
```

### [4、实现一个装饰器，通过一次调用，使函数重复执行 5 次](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#4实现一个装饰器通过一次调用使函数重复执行5次)

```python
from functools import wraps
def dec(func):
@wraps(func)
def inner(*args,**kwargs):
result=[func(*args,**kwargs) for i in range(5)]
return result
return inner

@dec
def add(x,y):
return x+y
print(add(1,2))
```

### [5、如何高效的找到 Redis 中所有以 felix 开头的 key](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#5如何高效的找到redis中所有以felix开头的key)

**1、** scan 0 match felixcount 5

**2、** 表示从游标 0 开始查询 felix 开头的 key，每次返回 5 条，但是这个 5 条不一定

### [6、列表中保留顺序和不保留顺序去重](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#6列表中保留顺序和不保留顺序去重)

**不保留顺序**

```python
lis=[3, 1, 4, 2, 3]
print(list(set(lis)))
```

**保留顺序**

```python
lis=[3, 1, 4, 2, 3]
T=[]
[T.append(i) for i in lis if i not in T])
print(T)

# 或者
T=sorted(set(lis), key=lis.index)
print(T)
```

### [7、python 的底层网络交互模块有哪些](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#7python的底层网络交互模块有哪些)

socket，urllib，requests，pycurl

### [8、一个大小为 100G 的文件 etl_log.txt，要读取文件的内容，写出具体过程代码](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#8一个大小为100g的文件etl_logtxt要读取文件的内容写出具体过程代码)

```python
with open("etl_log.txt",'r',encoding='utf8') as f:
for line in f:
print(line,end='')
```

### [9、axios 的作用](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#9axios的作用)

**axios 是基于 promise 的用于浏览器和 nodejs 的 HTTP 客户端，本身有以下特征：**

**1、** 从浏览器中创建 XMLHttpRequest；

**2、** 从 nodejs 发出 http 请求

**3、** 支持 promiseAPI

**4、** 拦截 请求和响应

**5、** 转换请求和响应数据

**6、** 取消请求

**7、** 自动转换 JSON 数据

**8、** 客户端支持防止 CSRF/XSRF 攻击

### [10、解释一下 Python 中的//，%和 \*\* 运算符](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Python/Python最新面试题2021年，常见面试题及答案汇总.md#10解释一下python中的//%和-**-运算符)

//运算符执行地板除法（向下取整除），它会返回整除结果的整数部分。

```
>>> 7//2
3
```

这里整除后会返回 3.5。

同样地，**执行取幂运算。a**b 会返回 a 的 b 次方。

```
>>> 2**10
1024
```

最后，%执行取模运算，返回除法的余数。

```
>>> 13%7
6
>>> 3.5%1.5
0.5
```

### 11、列举常见的关系型数据库和非关系型数据库。

### 12、css 如何隐藏一个元素

### 13、如何基于 Redis 实现发布和订阅

### 14、sys.path.append('xxx')的作用

### 15、怎样将字符串转换为小写？

### 16、解释一下 Python 中的赋值运算符

### 17、re 的 match 和 search 的区别

### 18、举例说明 Python 中的 range 函数?

### 19、输入一个字符串，输出该字符串的字符的所有组合。如输入'abc',输出 a,b,c,ab,ac,bc,abc.

### 20、解释\*args 和\*\*kwargs？

### 21、实现一个单例模式。(尽可能多的方法)

### 22、在 Python 中如何实现多线程？

### 23、简述 jsonp 及其原理

### 24、什么是 Flask？

### 25、解释 Python 中 reduce 函数的用法？

### 26、深拷贝和浅拷贝之间的区别是什么？

### 27、在什么情况下 y!=x-(x-y)会成立？

### 28、一个数如果恰好等于它的因子之和，这个数就称为‘完数’，比如 6=1+2+3，编程找出 1000 以内的所有的完数。

### 29、python 中如何使用进程池和线程池

### 30、编写程序，计算文件中单词的出现频率

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
