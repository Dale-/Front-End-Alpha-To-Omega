<h1 align="center">
<br>
  <img src="/source/images/fe-title.png" alt="Front-End-Alpha-To-Omega" width="400">
  <br>
    <br>
  Front-End-Alpha-To-Omega
  <br>
</h1>

<h4 align="center">Front-End-Alpha-To-Omega 是一个帮助初学者从零开始学习前端的项目。整个项目包含14个模块，从前端的知识技能图谱，到有趣的技术文档学习资源以及在前端前行路上长期关注的前端开发相关的网站、博客和活跃开发者。</h4>

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

* 如果你正在学习如何成为一名前端工程师，可点击右上角`Star`此项目, 我会持续更新资源和链接。

## Table of Contents

1. **[Start here](#here)**
2. **[HTML](#html)**
3. **[CSS](#css)**
4. **[JavaScript](#javascript)**
5. **[Security](#security)**
6. **[Performance](#performance-1)**
7. **[SEO](#seo)**
8. **[Tools](#tools)**
9. **[工程化](#tools)**
10. **[测试](#tools)**
11. **[小程序](#tools)**

---



### 由此开始
* [📖 互联网是如何工作的?](https://developer.mozilla.org/zh-CN/docs/learn/How_the_Internet_works) **|** [📹 视频](https://www.youtube.com/watch?v=7_LPdttKXPc)
* Front End & Back End
* [HTTP协议](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Overview)
* [从输入URL到页面加载完成，发生了什么](https://segmentfault.com/a/1190000006879700)

### HTML
* DOM
* Element
* Attribute

### CSS
* Selector
* Priority
* Specificity
* Box Model

> CSS Architecture
* BEM
* OOCS
* SMACSS

> CSS Preprocessore
* Sass
* PostCSS
* Less

### JavaScript
> Framework
* [React](https://zh-hans.reactjs.org/)
  * [Redux](https://cn.redux.js.org/)
  * [Mobx](https://mobx.js.org/README.html)
* [Vue](https://cn.vuejs.org/index.html)
  * [VueX](https://vuex.vuejs.org/zh/)
* [AngularJS](https://angularjs.org/)
  * RxJS
  * NgR


### 安全
* **HTTPS**
  每个页面和所有外部内容(插件、图像...)都使用HTTPS。
* **HTTP严格传输安全性(HSTS)**
  HTTP头设置'Strict-Transport-Security'
* **跨站点请求伪造攻击(CSRF)**
  确保向服务器端发送的请求是合法的，并来自您的网站/应用程序，以防止发生CSRF攻击。
* **跨站点脚本攻击(XSS)**
  确保页面或网站没有XSS攻击的可能性
* **Content Type Options**
  防止Google Chrome 和 Internet Explorer 尝试将响应的内容类型从服务器声明的内容类型中嗅探出来
* **X-Frame-Options (XFO)（外部框架连接设定）**
  保护网站的访问者免受劫持攻击。
* **Content Security Policy（内容安全策略）** 
  定义内容如何加载到您的网站上的方式以及允许加载的位置。也可以用来防止劫持攻击。


### [性能优化](https://segmentfault.com/a/1190000019185648)
> 网络层面

##### 减少请求次数

* 图片（雪碧图，图标字体）: 多张小图片合并为一张图，利用CSS-background-position调整图片显示位置
* 资源合并压缩: CSS、 Javascript、Image 都可以用相应的工具(Webpack)进行压缩，压缩后往往能省下不少空间。
* 浏览器缓存: 如果图片或者脚本，样式文件内容比较固定，不经常被修改，那么，尽可能利用缓存技术（application cache、http缓存、CDN、localstorage、sessionstorage，备忘录模式），减少HTTP请求次数或文件下载次数。

##### 减少单次请求所花费的时间
* 减少请求中数据的大小，从而达到减少单次请求所花费的时间

##### 图片优化
不同业务场景下的图片方案选型
* JPEG/JPG
  * 关键字: 有损压缩、体积小、加载快、不支持透明
  * 使用场景：JPG 适用于呈现色彩丰富的图片，在我们日常开发中，JPG 图片经常作为**大的背景图、轮播图或 Banner 图**出现。
  * 缺陷: 有损压缩在轮播图上确实很难露出马脚，但当它处理矢量图形和 Logo 等线条感较强、颜色对比强烈的图像时，人为压缩导致的图片模糊会相当明显。此外，JPEG 图像不支持透明度处理，透明图片需要召唤 PNG 来呈现。
* PNG
  * 关键字: 无损压缩、质量高、体积大、支持透明
  * 优点: PNG 图片具有比 JPG 更强的色彩表现力，对线条的处理更加细腻，对透明度有良好的支持。它弥补了上文我们提到的 JPG 的局限性，唯一的 BUG 就是体积太大。 
  * 应用场景: 考虑到 PNG 在处理线条和颜色对比度方面的优势，我们主要用它来呈现**小的 Logo、颜色简单且对比强烈的图片**或背景等。
* SVG
  * 关键字: 文本文件、体积小、不失真、兼容性好
  * 应用场景: 将 SVG 写入独立文件后引入 HTML
* Base64
  * 关键字: 文本文件、依赖代码、小图标解决方案
  * 应用场景：图片的实际尺寸很小 \ 图片无法以雪碧图的形式与其它小图结合 \ 图片的更新频率非常低
* WebP
  * 关键字: 年轻的全能型选手（是 Google 专为 Web 开发的一种旨在加快图片加载速度的图片格式，它支持有损压缩和无损压缩。）
  * 优点: WebP 像 JPEG 一样对细节丰富的图片信手拈来，像 PNG 一样支持透明，像 GIF 一样可以显示动态图片——它集多种图片文件格式的优点于一身
  * 局限性: 兼容性


> 存储层面

##### 浏览器缓存

##### 本地缓存

> 渲染层面

##### 服务端渲染
##### 浏览器渲染
##### DOM优化
  * 时间循环与异步更新
  * 回流与重绘


##### 首屏渲染提速
  * 懒加载


### SEO
* Google Analytics
* Headings logic
* sitemap.xml
* robots.txt
* Structured Data
* Sitemap HTML
* Pagination link tags

### Tools
> Package Managers
* npm
* yarn

> Version Control
* Git

> IDE

* Visual Studio Code
* Atom
* Sublime Text
* WebStorm
* Vim
* Emacs
* Brackets

> 调试工具
* Firebug/Firebug-lite/Web Inspector
* YSlow/Smushit
* IEDeveloperToolBar/IETester
* SuperPreview/JsBeautifier
* Fiddler/WireShark/tcpdump


### 工程化

> Code Quality
* JSCS
* ESLint
* stylelint
* htmlhint

> 构建系统
* webpack
* gulp
* grunt

> 代码分析
* Code climate

### 测试
> 单元测试
 * Jasmine
* Mocha
* Protractor
* Karma
* Jest
> UI测试
> 集成测试
> 测试覆盖率

### 小程序
* Taro
* WePY
* mpvue