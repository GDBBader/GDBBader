---

title: JavaScript 内存管理
date: 2022-07-12 09:05
tags: [JavaScript]

---
## 一、内存生命周期

1.  分配你所需要的内存
2.  使用分配到的内存（读、写）
3.  不需要时将其释放、归还

## 二、内存管理

内存管理管理的是什么？管理的就是内存的生命周期。

## 三、JavaScript内存分配与使用

变量定义时就完成了内存分配。

对变量的读写操作就是使用。

## 四、垃圾回收

垃圾回收的关键在于判断其“不再需要”--无法判断，只能近似。

-   引用计数
-   标记-清除

## 问题

1.  内存管理管理的是什么？
2.  简述两种垃圾回收算法的原理。

## 参考

1.  [内存管理 - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Memory_Management)