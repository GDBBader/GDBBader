---

title: JavaScript 并发模型与事件循环
date: 2022-07-26 17:32
tags: [JavaScript]

---
## 一、问题

-   常听“`JavaScript`是单线程”那怎么还能并发执行？
-   什么是消息？
-   什么是事件循环？

## 二、单线程

所谓单线程，是指在JS引擎中负责解释和执行`JavaScript`代码的线程只有一个。

还有其他线程。

-   解释执行JavaScript代码的线程：**主线程**
-   定时器线程、AJAX线程...：**工作线程**

## 三、运行时

工作线程在运行时将消息放到消息队列中，主线程去一个个执行消息队列中消息。

![](https://cdn.nlark.com/yuque/0/2022/svg/1318699/1658827410749-4c1a6f81-77d8-4056-9f73-4564494f9e07.svg)

### 栈

函数调用形成的

### 堆

对象被分配在堆中

### 队列

包含待处理消息的消息队列

### 事件循环

主线程去一个个执行消息队列中的消息的过程就是事件循环

只有当一个消息执行完之后才会去执行其他消息，即不会被打断。

## 参考

1.  [JavaScript原理：一、消息队列与事件循环 - SegmentFault 思否](https://segmentfault.com/a/1190000023367138)
2.  [并发模型与事件循环 - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/EventLoop)