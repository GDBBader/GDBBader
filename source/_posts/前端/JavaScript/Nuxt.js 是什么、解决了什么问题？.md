---

title: Nuxt.js 是什么、解决了什么问题？
date: 2022-06-20 11:47
tags: [JavaScript]

---
## 一、Nuxt.js 是什么？

-   是一个`js`框架
-   是一个用来创建`Web`应用的框架

## 二、Vue.js 与 Nuxt.js 的异同

同：

`Vue.js`也是用来创建Web应用的

异：

`Vue.js`主要是用来创建单页应用程序（`SPA`），`SPA`对于`SEO`很不友好，因为它的`index.html`中并没有什么内容。

`Nuxt.js`是一个基于`vue.js`的`SSR`框架。它打包出来的前端项目`index.html`文件是有内容的，它直接将服务端渲染出来的`HTML`传递给浏览器，也加快了首屏的加载速度。

当一个项目需要搜索引擎提供流量时，使用`Nuxt.js`更合适。

## 问题

1.  `Nuxt.js`是什么？
2.  解决了`vue.js`的什么问题

## 参考

1.  [Nuxt.js是什么,为什么使用它、Nuxt.js环境搭建 - HelloWorld开发者社区](https://www.helloworld.net/p/2026572415)
2.  [你应该知道的Nuxt.js 基础知识 - 掘金](https://juejin.cn/post/6996563830583066631)