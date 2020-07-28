<h1 align="center">
<br>
  <img src="/source/images/fe-title.png" alt="Front-End-Interview-Questions" width="400">
  <br>
    <br>
  Front-End-Interview-Questions
  <br>
</h1>

<h4 align="center">Front-End-Interview-Questions 是一个前端常见面试题汇总的文件。</h4>

<p align="center">
  <a href="http://makeapullrequest.com">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome">
  </a>
  <a href="https://gitpod.io/#https://github.com/thedaviddias/Front-End-Checklist">
    <img src="https://img.shields.io/badge/Gitpod-Ready--to--Code-blue?logo=gitpod" alt="Gitpod Ready-to-Code">
  </a>
  <a href="https://creativecommons.org/publicdomain/zero/1.0/">
    <img src="https://img.shields.io/badge/license-CC0-green.svg?style=flat-square" alt="CC0">
  </a>
</p>

* 如果你正在寻找常见的前端面试题，可点击右上角`Star`此项目, 我会持续更新资源和链接。

## Table of Contents

1. **[React相关]()**
2. **[网络相关]()**
3. **[Webpack相关]()**
4. **[前端缓存]()**
5. **[JavaScript相关]()**
6. **[CSS相关]()**

---


### React相关

1. React hooks原理
2. 为什么 setState 是异步的
3. React性能优化 (https://dale-.github.io/2019/02/19/React-Render-Performance/)
4. Redux的原理、数据流和redux具体解决的问题 ✅ (https://dale-.github.io/2017/08/13/Getting-Started-with-Redux/)
5. redux和mobx的区别 (https://segmentfault.com/a/1190000017538995?utm_source=tag-newest)
6. useMemo和useCallback的区别
7. React高阶组件
8. 虚拟DOM、DOM Diff
9. 50个React questions (https://segmentfault.com/a/1190000018604138)

   
### 网络相关

1. HTTP请求格式、状态码
2. http body格式
3. http和https的区别  
4. HTTP强制缓存
5. Keep-alive vs http2
6. 如何减少DNS查询时间提高网站的打开速度
7. http2.0和http1.0区别
8. TCP为什么要四次挥手
9. 浏览器请求数据到请求数据结束与服务器进行了几次交互


### Webpack相关

1. Webpack热更新原理
2. Webpack常见的加载器
3. 多页打包
4. Webpack构建流程
5. webpack性能优化
6. loader和plugin的区别


### 前端缓存

1. HTTP缓存（强缓存和协商缓存）
2. 前端的缓存方式
3. localStorage如何设置过期时间
4. 本地缓存机制
5. localStorage、sessionStorage的区别


### JavaScript相关

1. 数组去重的方式
2. setTimeout、Promise、Async/Await的区别
3. 前端SSR
4. JS的内存原理
5. JS中的垃圾回收机制
6. JS中的Event Loop
7. New操作符的工作原理
8. JS的继承方式
9. Apply、call、bind方法的区别
10. 深拷贝的常见问题
11. 前后端交互的安全性
12. 跨域产生的问题和解决方案
13. 首页加载优化
14. 无限下拉列表优化
15. 浏览器页面渲染过程
16. 前端网络优化
17. for 和 foreach的区别
18. 前端文件上传机制
19. 前端监控
20. 浏览器从地址栏输入URL到显示页面的步骤
21. 回流和重绘的定义以及如何避免
22. Websocket和ajax的区别
23. fetch api与传统request的区别
24. 常用设计模式
25. 闭包
26. 树的遍历方式
27. commonjs和ES6 module的区别
28. 如何阻止冒泡
29. 排序算法


>  为什么setState是异步的

1. 保证内部数据统一
2. setState异步更新



>  for和 foreach的区别

* 写法不同

```javascript
var arr = [1, 5, 8, 9, 6];

// for循环
for(var i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}

// forEach循环
arr.forEach((value) => {
  console.log(value);
})
```

* 中断循环

  for循环可以中断循环（利用break语句或return语句），但forEach不可以中断循环。

* 关于扩展js原生的Array类

  使用for循环时，打印每个value值，并不会打印出来扩展js原生的Array类，但使用forEach循环，就可以打印出来。

  

> http2.0 和 http1.0区别

*  HTTP1.x的解析是基于文本存在缺陷，HTTP2.0的协议解析决定采用二进制格式。
* HTTP1.x的header带有大量信息，而且每次都要重复发送，HTTP2.0使用encoder来减少需要传输的header大小，通讯双方各自cache一份header fields表，既避免了重复header的传输，又减小了需要传输的大小。
* 多路复用，让所有数据流共用同一个连接，可以更有效地使用 TCP 连接。
* 服务推送，提前缓存可能需要的文件。



> 回流和重绘

* 回流

  当render tree中的一部分(或全部)因为元素的规模尺寸，布局，隐藏等改变而需要重新构建。这就称为回流(reflow)。每个页面至少需要一次回流，就是在页面第一次加载的时候，这时候是一定会发生回流的，因为要构建render tree。在回流的时候，浏览器会使渲染树中受到影响的部分失效，并重新构造这部分渲染树，完成回流后，浏览器会重新绘制受影响的部分到屏幕中，该过程成为重绘。

* 重绘

  当render tree中的一些元素需要更新属性，而这些属性只是影响元素的外观，风格，而不会影响布局的，比如background-color。则就叫称为重绘。



> JS中的垃圾回收机制

* 标记清除

  这是javascript中最常用的垃圾回收方式。当变量进入执行环境是，就标记这个变量为“进入环境”。从逻辑上讲，永远不能释放进入环境的变量所占用的内存，因为只要执行流进入相应的环境，就可能会用到他们。当变量离开环境时，则将其标记为“离开环境”。

* 引用计数

  另一种不太常见的垃圾回收策略是引用计数。引用计数的含义是跟踪记录每个值被引用的次数。当声明了一个变量并将一个引用类型赋值给该变量时，则这个值的引用次数就是1。相反，如果包含对这个值引用的变量又取得了另外一个值，则这个值的引用次数就减1。当这个引用次数变成0时，则说明没有办法再访问这个值了，因而就可以将其所占的内存空间给收回来。这样，垃圾收集器下次再运行时，它就会释放那些引用次数为0的值所占的内存。

> JS中的Evnet Loop

浏览器端事件循环中的异步队列有两种：macro（宏任务）队列和 micro（微任务）队列。宏任务队列可以有多个，微任务队列只有一个。

* 常见的 macro-task 比如：setTimeout、setInterval、script（整体代码）、 I/O 操作、UI 渲染等。
* 常见的 micro-task 比如: new Promise().then(回调)、MutationObserver(html5新特性) 等。

1. 一开始执行栈空,我们可以把执行栈认为是一个存储函数调用的栈结构，遵循先进后出的原则。micro 队列空，macro 队列里有且只有一个 script 脚本（整体代码）。
2. 全局上下文（script 标签）被推入执行栈，同步代码执行。在执行的过程中，会判断是同步任务还是异步任务，通过对一些接口的调用，可以产生新的 macro-task 与 micro-task，它们会分别被推入各自的任务队列里。同步代码执行完了，script 脚本会被移出 macro 队列，这个过程本质上是队列的 macro-task 的执行和出队的过程。
3. 上一步我们出队的是一个 macro-task，这一步我们处理的是 micro-task。但需要注意的是：当 macro-task 出队时，任务是一个一个执行的；而 micro-task 出队时，任务是一队一队执行的。因此，我们处理 micro 队列这一步，会逐个执行队列中的任务并把它出队，直到队列被清空。
4. 执行渲染操作，更新界面
5. 检查是否存在 Web worker 任务，如果有，则对其进行处理
6. 上述过程循环往复，直到两个队列都清空



> 无限下拉列表优化

* 监听一个固定长度列表的首尾元素是否进入视窗

* 更新当前页面内渲染的第一个元素对应的序号

* 根据上述序号，获取目标数据元素，列表内容重新渲染成对应内容

* 容器 padding 调整，模拟滚动实现

  核心：利用父元素的 padding 去填充随着无限下拉而本该有的、越来越多的 DOM 元素，仅仅保留视窗区域上下一定数量的 DOM 元素来进行数据渲染。



> 浏览器页面渲染流程

* 解析HTML，构建DOM Tree
* 解析CSS文本，构建CSSOM Tree (styleSheets)
*  结合DOM Tree 与 CSSOM Tree，构建Render Tree (渲染树)
*  Layout: 根据Render Tree进行节点计算
*  Paint: 遍历Render Tree信息绘制页面



> 本地缓存机制

本地缓存就简单多了，我们常用的有三个：cookie、localStorage、sessionStorage。

* Cookie：一般用来存储用户信息，每次请求的时候内容都会自动被传递给服务器。不同浏览器对于cookie的大小并不统一，一般都是4-10kb。Cookie可以设置时效。注意，cookie比较浪费带宽，不建议写入太多内容，这也是前端性能优化的一点。
* LocalStorage：localstorage会把内容一直存在浏览器，直到清除浏览器的缓存。注意，没有清除浏览器缓存，数据会永久存储在浏览器。Localstorage一般在5M左右。
* sessionStorage：跟localStorage一样，只不过sessionStorage的生命周期跟同源窗口有关，就是说当前同一个源下面的只要有一个窗口没关或者跳到另外的窗口，sessionStorage都会存在。sessionStorage大小也是5M左右。

上面三个是最常用的，还有一个session比较常用，这个是后台服务器设置的，我们只要了解session是后台注入后台使用，按理来说session没有大小限制。从安全性来说，session比cookie安全。



> Webpack热更新原理

* 启动webpack，生成compiler实例。compiler上有很多方法，比如可以启动 webpack 所有编译工作，以及监听本地文件的变化。
* 使用express框架启动本地server，让浏览器可以请求本地的静态资源。
* 本地server启动之后，再去启动websocket服务。通过websocket，可以建立本地服务和浏览器的双向通信。这样就可以实现当本地文件发生变化，立马告知浏览器可以热更新代码！



> Webpack 构建流程

* 根据配置，识别入口文件；
* 逐层识别模块依赖（包括 Commonjs、AMD、或 ES6 的 import 等，都会被识别和分析）；
* Webpack 主要工作内容就是分析代码，转换代码，编译代码，最后输出代码；
* 输出最后打包后的代码。



> Webpack loader 和 plugin的区别

* loader 用于加载某些资源文件。 因为webpack 本身只能打包commonjs规范的js文件，对于其他资源例如 css，图片，或者其他的语法集，比如 jsx， coffee，是没有办法加载的。 这就需要对应的loader将资源转化，加载进来。从字面意思也能看出，loader是用于加载的，它作用于一个个文件上。
* plugin 用于扩展webpack的功能。它直接作用于 webpack，扩展了它的功能。当然loader也时变相的扩展了 webpack ，但是它只专注于转化文件（transform）这一个领域。而plugin的功能更加的丰富，而不仅局限于资源的加载。



> http 和 https的区别

* https协议需要到ca申请证书，一般免费证书较少，因而需要一定费用。
* http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。
* http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。
* http的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。
* HTTP 页面响应速度比 HTTPS 快，主要是因为 HTTP 使用 TCP 三次握手建立连接，客户端和服务器需要交换 3 个包，而 HTTPS除了 TCP 的三个包，还要加上 ssl 握手需要的 9 个包，所以一共是 12 个包。



> React hooks原理

* 在Hoooks发布之前React定义组件有两种方法，一种是类组件，一种是函数式组件。因为我们组件中需要 状态 然后我们还需要生命周期来执行不同阶段的事物，我们还需要有一些副作用的操作，例如交互请求。所以我们一定要需要类组件，函数式组件中没有。
* 在我们在做分离业务逻辑，拆分组件，以达到更多业务逻辑复用时候，当我们遇到一个相对复杂的组件时候，因为此组件有很多状态，我们无法将其提取到函数式组件中，因为函数式组件，遵循签名是UI=f(state),函数式组件是无状态的，也无生命周期的，所以hook应运而生，一个既有状态又有生命周期的函数式组件，它让我们重新思考了函数式组件的发展形态。
* 上面说的是第一点，个人觉得第二点就是Hooks体现了React在组件内部进行逻辑隔离，之前只是在组件与组件之间拥有天然隔离，明确数据流以及可以进行Hoc层层嵌套，现在不用层层嵌套也可以把数据状态共享问题解决掉。Hoc层层嵌套就是很大缺点，它做的也是解决数据状态共享问题。在Hooks中实现的是 ‘状态细粒度划分’，‘状态以及变更逻辑隔离’，更加体现了web component 中的设计原则。
* hooks API背后的想法是你可以使用一个setter函数作为hook函数中的第二个数组项返回，而setter将控制由hook管理的状态。这意味着此处存储的数据位于正在渲染的组件之外。 此状态不与其他组件共享，但它保留在可以随后渲染特定组件的范围内。



> useMemo和useCallback的区别

useCallback和useMemo都可缓存函数的引用或值，但是从更细的使用角度来说useCallback缓存函数的引用，useMemo缓存计算数据的值。



> React高阶组件

高阶组件（HOC）是 React 中用于重用组件逻辑的高级技术。

具体来说，高阶组件是一个函数，能够接受一个组件并返回一个新的组件。在我们项目中使用react-redux框架的时候，有一个connect的概念，这里的connect其实就是一个高阶组件。

代码复用的方法、形式有很多种，你可以用类继承来做到代码复用，也可以分离模块的方式。但是高阶组件这种方式很有意思，也很灵活。学过设计模式的同学其实应该能反应过来，它其实就是设计模式里面的装饰者模式。它通过组合的方式达到很高的灵活程度。



实现高阶组件的方法有如下两种：

   * 属性代理。高阶组件通过呗包裹的React组件来操作props
* 反向继承。高阶组件继承于被包裹的React组件





