# Vue 最新面试题及答案附答案汇总

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、vue 常用的修饰符？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#1vue常用的修饰符)

**1、** .stop：等同于 JavaScript 中的 event.stopPropagation()，防止事件冒泡；

**2、** .prevent：等同于 JavaScript 中的 event.preventDefault()，防止执行预设的行为（如果事件可取消，则取消该事件，而不停止事件的进一步传播）；

**3、** .capture：与事件冒泡的方向相反，事件捕获由外到内；

**4、** .self：只会触发自己范围内的事件，不包含子元素；

**5、** .once：只会触发一次。

### [2、vue 常用的修饰符](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#2vue常用的修饰符)

**1、** .stop：等同于 JavaScript 中的 event.stopPropagation()，防止事件冒泡；

**2、** .prevent：等同于 JavaScript 中的 event.preventDefault()，防止执行预设的行为（如果事件可取消，则取消该事件，而不停止事件的进一步传播）；

**3、** .capture：与事件冒泡的方向相反，事件捕获由外到内；

**4、** .self：只会触发自己范围内的事件，不包含子元素；

**5、** .once：只会触发一次。

### [3、Vue-router 跳转和 location.href 有什么区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#3vue-router跳转和locationhref有什么区别)

**1、** 使用 location.href='/url'来跳转，简单方便，但是刷新了页面；

**2、** 使用 history.pushState('/url')，无刷新页面，静态跳转；

**3、** 引进 router，然后使用 router.push('/url')来跳转，使用了 diff 算法，实现了按需加载，减少了 dom 的消耗。

**4、** 其实使用 router 跳转和使用 history.pushState()没什么差别的，因为 vue-router 就是用了 history.pushState()，尤其是在 history 模式下。

### [4、简单说一下 Vue2.x 响应式数据原理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#4简单说一下vue2x响应式数据原理)

Vue 在初始化数据时，会使用`Object.defineProperty`重新定义 data 中的所有属性，当页面使用对应属性时，首先会进行依赖收集(收集当前组件的`watcher`)如果属性发生变化会通知相关依赖进行更新操作(`发布订阅`)。

### [5、vuex 有哪几种属性？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#5vuex有哪几种属性)

有五种，分别是 State、 Getter、Mutation 、Action、 Module

**1、** state => 基本数据(数据源存放地)

**2、** getters => 从基本数据派生出来的数据

**3、** mutations => 提交更改数据的方法，同步！

**4、** actions => 像一个装饰器，包裹 mutations，使之可以异步。

**5、** modules => 模块化 Vuex

### [6、路由跳转和 location.href 的区别？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#6路由跳转和locationhref的区别)

使用 location.href='/url'来跳转，简单方便，但是刷新了页面；

使用路由方式跳转，无刷新页面，静态跳转；

### [7、销毁过程](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#7销毁过程)

`父beforeDestroy->子beforeDestroy->子destroyed->父destroyed`

### [8、什么是 vue 生命周期？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#8什么是vue生命周期)

Vue 实例从创建到销毁的过程，就是生命周期。也就是从开始创建、初始化数据、编译模板、挂载 Dom→ 渲染、更新 → 渲染、卸载等一系列过程，我们称这是 Vue 的生命周期。

### [9、用纯 JS 编写一个程序来反转字符串](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#9用纯js编写一个程序来反转字符串)

使用内置函数：内置函数 reverse()直接反转字符串。

```
str="jQuery";
str = str.split("")
str = str.reverse()
str = str.join("")
alert(str);
```

首先将字符串拆分为数组，然后反转数组，最近将字符连接起来形成字符串。 使用循环:首先，计算字符串中的字符数，然后对原始字符串应用递减循环，该循环从最后一个字符开始，打印每个字符，直到 count 变为零。

### [10、分别简述 computed 和 watch 的使用场景](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/Vue/Vue最新面试题及答案附答案汇总.md#10分别简述computed和watch的使用场景)

**computed:**

当一个属性受多个属性影响的时候就需要用到 computed

最典型的栗子： 购物车商品结算的时候

**watch:**

当一条数据影响多条数据的时候就需要用 watch

栗子：搜索数据

### 11、数组去重复的方法有哪些

### 12、cancas 和 SVG 的是什么以及区别

### 13、解释一下 "use strict" ? “

### 14、vue 更新数组时触发视图更新的方法

### 15、JS 中的 Array.splice()和 Array.slice()方法有什么区别

### 16、再说一下 Computed 和 Watch

### 17、什么是观察者？

### 18、Vue 中双向数据绑定是如何实现的？

### 19、nextTick 知道吗，实现原理是什么？

### 20、如何在 JavaScript 中每 x 秒调用一个函数

### 21、Vue 里面 router-link 在电脑上有用，在安卓上没反应怎么解决？

### 22、vue 的实现原理？

### 23、什么是生命周期 hook？列出一些生命周期 hook。

### 24、JS 中的主要有哪几类错误

### 25、v-show 和 v-if 指令的共同点和不同点？

### 26、vuex 是什么？怎么使用？哪种功能场景使用它？

### 27、如何将 JS 日期转换为 ISO 标准

### 28、什么是动态 prop？

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
