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



## 由此开始
* [📖 互联网是如何工作的?](https://developer.mozilla.org/zh-CN/docs/learn/How_the_Internet_works) **|** [📹 视频](https://www.youtube.com/watch?v=7_LPdttKXPc)
* Front End & Back End
* [HTTP协议](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Overview)
* [从输入URL到页面加载完成，发生了什么](https://segmentfault.com/a/1190000006879700)

## HTML
* DOM
* Element
* Attribute

## CSS
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

## JavaScript
> Framework
* [React](https://zh-hans.reactjs.org/)
  * [Redux](https://cn.redux.js.org/)
  * [Mobx](https://mobx.js.org/README.html)
* [Vue](https://cn.vuejs.org/index.html)
  * [VueX](https://vuex.vuejs.org/zh/)
* [AngularJS](https://angularjs.org/)
  * RxJS
  * NgR


## Security
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


## Performance
> 网络层面
* 减少请求次数
* 减少单次请求所花费的时间
* 图片优化 (JPG / PNG / SVG / Base64 / WebP )

> 存储层面
* 浏览器缓存
  * 强缓存
  * 协商缓存
*  本地缓存
   * Cookie
   * localStorage & sessionStorage
   * IndexedDB
  
> CDN
* 缓存
* 回源

> 渲染层面
* 服务器端渲染
* 浏览器端渲染
* DOM优化
* Evvent Loop 与异步更新策略
* 回流与重绘

> 事件的节流与防抖
* 节流
* 防抖


## SEO
* Google Analytics
* Headings logic
* sitemap.xml
* robots.txt
* Structured Data
* Sitemap HTML
* Pagination link tags

## Tools
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


## 工程化

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

## 测试
> 单元测试
 * Jasmine
* Mocha
* Protractor
* Karma
* Jest
> UI测试

> 集成测试

> 测试覆盖率

## 小程序
* Taro
* WePY
* mpvue