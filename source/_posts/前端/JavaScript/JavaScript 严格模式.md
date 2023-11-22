---

title: JavaScript 严格模式
date: 2022-07-16 11:32
tags: [JavaScript]

---
## 一、什么是严格模式

对JavaScript作出部分限制或改变的模式。

比如：

1.  将过失错误转成异常，原来不报错的现在报错了；
2.  某些情况下运行得更快了；
3.  防止意外创建全局变量，使用前要先定义，不至于拼写错误导致创建全局变量

## 二、如何开启

-   脚本

```js
// 整个脚本都开启严格模式的语法
"use strict";
var v = "Hi!  I'm a strict mode script!";
```

-   函数

```js
function strict() {
  // 函数级别严格模式语法
  'use strict';
  function nested() {
    return "And so am I!";
  }
  return "Hi!  I'm a strict mode function!  " + nested();
}

function notStrict() {
  return "I'm not strict.";
}
```

## 问题

1.  请用一句话简述严格模式。

## 参考

1.  [严格模式 - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode)