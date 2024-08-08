# JavaScript 最新面试题及答案整理，汇总版

### 全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！

### 下载链接：[高清 172 份，累计 7701 页大厂面试题 PDF](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/index.md)

### [1、简述下你理解的面向对象？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#1简述下你理解的面向对象)

万物皆对象，把一个对象抽象成类,具体上就是把一个对象的静态特征和动态特征抽象成属性和方法,也就是把一类事物的算法和数据结构封装在一个类之中,程序就是多个对象和互相之间的通信组成的、

面向对象具有封装性,继承性,多态性。

封装:隐蔽了对象内部不需要暴露的细节,使得内部细节的变动跟外界脱离,只依靠接口进行通信.封装性降低了编程的复杂性、通过继承,使得新建一个类变得容易,一个类从派生类那里获得其非私有的方法和公用属性的繁琐工作交给了编译器、而继承和实现接口和运行时的类型绑定机制 所产生的多态,使得不同的类所产生的对象能够对相同的消息作出不同的反应,极大地提高了代码的通用性、

总之,面向对象的特性提高了大型程序的重用性和可维护性.

### [2、简述下 this 和定义属性和方法的时候有什么区别?Prototype？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#2简述下-this-和定义属性和方法的时候有什么区别prototype)

this 表示当前对象，如果在全局作用范围内使用 this，则指代当前页面对象 window； 如果在函数中使用 this，则 this 指代什么是根据运行时此函数在什么对象上被调用。 我们还可以使用 apply 和 call 两个全局方法来改变函数中 this 的具体指向。

prototype 本质上还是一个 JavaScript 对象。 并且每个函数都有一个默认的 prototype 属性。

在 prototype 上定义的属性方法为所有实例共享，所有实例皆引用到同一个对象，单一实例对原型上的属性进行修改，也会影响到所有其他实例。

### [3、javascript 创建对象的几种方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#3javascript创建对象的几种方式)

`javascript`创建对象简单的说,无非就是使用内置对象或各种自定义对象，当然还可以用`JSON`；但写法有很多种，也能混合使用

对象字面量的方式

```
person={firstname:"Mark",lastname:"Yun",age:25,eyecolor:"black"};
```

用`function`来模拟无参的构造函数

```
 function Person(){}
    var person=new Person();//定义一个function，如果使用new"实例化",该function可以看作是一个Class
        person.name="Mark";
        person.age="25";
        person.work=function(){
        alert(person.name+" hello...");
    }
person.work();
```

用`function`来模拟参构造函数来实现（用`this`关键字定义构造的上下文属性）

```
function Pet(name,age,hobby){
       this.name=name;//this作用域：当前对象
       this.age=age;
       this.hobby=hobby;
       this.eat=function(){
          alert("我叫"+this.name+",我喜欢"+this.hobby+",是个程序员");
       }
    }
    var maidou =new Pet("麦兜",25,"coding");//实例化、创建对象
    maidou.eat();//调用eat方法
```

用工厂方式来创建（内置对象）

```
var wcDog =new Object();
     wcDog.name="旺财";
     wcDog.age=3;
     wcDog.work=function(){
       alert("我是"+wcDog.name+",汪汪汪......");
     }
     wcDog.work();
```

用原型方式来创建

```
function Dog(){

     }
     Dog.prototype.name="旺财";
     Dog.prototype.eat=function(){
     alert(this.name+"是个吃货");
     }
     var wangcai =new Dog();
     wangcai.eat();
```

用混合方式来创建

```
 function Car(name,price){
      this.name=name;
      this.price=price;
    }
     Car.prototype.sell=function(){
       alert("我是"+this.name+"，我现在卖"+this.price+"万元");
      }
    var camry =new Car("凯美瑞",27);
    camry.sell();
```

### [4、异步加载的方式有哪些？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#4异步加载的方式有哪些)

(1) defer，只支持 IE

(2) async：true

(3) 创建 script，插入到 DOM 中，加载完毕后 callBack

### [5、你有哪些性能优化的方法？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#5你有哪些性能优化的方法)

**1、** 减少 http 请求次数：CSS Sprites, JS、CSS 源码压缩、图片大小控制合适；网页 Gzip， CDN 托管，data 缓存 ，图片服务器。

**2、** 前端模板 JS+数据，减少由于 HTML 标签导致的带宽浪费，前端用变量保存 AJAX 请求结果，每次操作本地变量，不用请求，减少请求次数

**3、** 用 innerHTML 代替 DOM 操作，减少 DOM 操作次数，优化 javascript 性能。

**4、** 当需要设置的样式很多时设置 className 而不是直接操作 style。

**5、** 少用全局变量、缓存 DOM 节点查找的结果。减少 IO 读取操作。

**6、** 避免使用 CSS Expression（css 表达式)又称 Dynamic properties(动态属性)。

**7、** 图片预加载，将样式表放在顶部，将脚本放在底部 加上时间戳。

**8、** 避免在页面的主体布局中使用 table，table 要等其中的内容完全下载之后才会显示出来，显示比 div+css 布局慢。

### [6、压缩合并目的？http 请求的优化方式？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#6压缩合并目的http请求的优化方式)

1）Web 性能优化最佳实践中最重要的一条是减少 HTTP 请求。而减少 HTTP 请求的最主要的方式就是，合并并压缩 JavaScript 和 CSS 文件。

CSS Sprites（CSS 精灵）：把全站的图标都放在一个图像文件中，然后用 CSS 的 background-image 和 background-position 属性定位来显示其中的一小部分。

合并脚本和样式表; 图片地图：利用 image map 标签定义一个客户端图像映射，（图像映射指带有可点击区域的一幅图像）具体看： [http://club.topsage.com/thread-2527479-1-1.html](http://link.zhihu.com/?target=http%3A//club.topsage.com/thread-2527479-1-1.html)

图片 js/css 等静态资源放在静态服务器或 CDN 服时，尽量采用不用的域名，这样能防止 cookie 不会互相污染，减少每次请求的往返数据。

css 替代图片, 缓存一些数据

少用 location.reload()：使用 location.reload() 会刷新页面，刷新页面时页面所有资源 (css，js，img 等) 会重新请求服务器。建议使用 location.href="当前页 url" 代替 location.reload() ，使用 location.href 浏览器会读取本地缓存资源。

### [7、你觉得 jQuery 源码有哪些写的好的地方](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#7你觉得jquery源码有哪些写的好的地方)

**1、** `jquery`源码封装在一个匿名函数的自执行环境中，有助于防止变量的全局污染，然后通过传入`window`对象参数，可以使`window`对象作为局部变量使用，好处是当`jquery`中访问`window`对象的时候，就不用将作用域链退回到顶层作用域了，从而可以更快的访问 window 对象。同样，传入`undefined`参数，可以缩短查找`undefined`时的作用域链

**2、** `jquery`将一些原型属性和方法封装在了`jquery.prototype`中，为了缩短名称，又赋值给了`jquery.fn`，这是很形象的写法

**3、** 有一些数组或对象的方法经常能使用到，`jQuery`将其保存为局部变量以提高访问速度

**4、** `jquery`实现的链式调用可以节约代码，所返回的都是同一个对象，可以提高代码效率

### [8、bootstrap 好处？](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#8bootstrap好处)

自适应和响应式布局，12 栅格系统，统一的界面风格和 css 样式有利于团队开发。编写灵活、稳定、高质量的 HTML 和 CSS 代码的规范。

### [9、声明函数作用提升?声明变量和声明函数的提升有什么区别](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#9声明函数作用提升声明变量和声明函数的提升有什么区别)

**变量声明提升：**

**1、** 变量申明在进入执行上下文就完成了。

**2、** 只要变量在代码中进行了声明，无论它在哪个位置上进行声明， js 引擎都会将它的声明放在范围作用域的顶部；

\*\*函数声明提升

### [10、$(function(){})和 window.onload 和 $(document).ready(function(){})](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/JavaScript/JavaScript最新面试题及答案整理，汇总版.md#10$function{}和windowonload-和-$documentreadyfunction{})

window.onload:用于当页面的所有元素，包括外部引用文件，图片等都加载完毕时运行函数内的函数。load 方法只能执行一次，如果在 js 文件里写了多个，只能执行最后一个。

$$(document).ready(function()\{\})和$$(function(){})都是用于当页面的标准 DOM 元素被解析成 DOM 树后就执行内部函数。这个函数是可以在 js 文件里多次编写的，对于多人共同编写的 js 就有很大的优势，因为所有行为函数都会执行到。而且$(document).ready()函数在 HMTL 结构加载完后就可以执行，不需要等大型文件加载或者不存在的连接等耗时工作完成才执行，效率高。

### 11、渐进增强和优雅降级

### 12、事件模型

### 13、说出几个 http 协议状态码?

### 14、web 开发中会话跟踪的方法有哪些

### 15、实现继承的方法有哪些？？？

### 16、js 延迟加载的方式有哪些？

### 17、ajax 请求方式有几种（8 种）？

### 18、谁是 c 的构造函数?

### 19、基本数据类型和引用数据类型有什么区别？

### 20、什么是对象解构？

### 21、对象的 prototype(原型) 是什么？

### 22、函数 fn1 函数 fn2 函数 fn3，如果想在三个函数都执行完成后执行某一个事件应该如何实现?

### 23、如何检查值是否虚值？

### 24、为什么函数被称为一等公民？

### 25、什么是 ES6 模块？

### 26、jquery 和 zepto 有什么区别?

### 27、说说你对 AMD 和 Commonjs 的理解

### 28、什么是事件冒泡？

### 29、闭包

## [全部答案，更新日期：2023 年 6 月 11 日，直接下载吧！](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)

## [新增：高清 PDF：172 份，7701 页，最新整理](https://gitlab.gaorta.com/devteam/learning-journey/study-materials-collection/-/tree/master/docs/daan.md)
