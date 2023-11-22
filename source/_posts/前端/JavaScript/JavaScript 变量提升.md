---

title: JavaScript 变量提升
date: 2022-04-18 14:51
tags: [JavaScript]

---
## 一、理解

变量提升：变量与函数的声明会在编译阶段被放入内存中。（这样的解释还没有理解，不过可以暂时理解为变量和函数的声明会在物理层面移动到代码的最前面。）

  

## 二、示例

```js
//请写一个变量提升的例子
num = 3;
console.log(num);
var num;

//请写一个函数提升的例子
abc();
function abc(params) {
    console.log(111);
}
//函数提升，提升的是声明而不是表达式
def();
let def = function ddd(params) {
    console.log(222);
}
```
  

## 问题

1.  如何用一句话解释变量提升？

可以先使用，再声明，JavaScript会把变量的声明提高。

2.  函数与变量谁的优先级更高？

函数和变量相比，会被优先提升。这意味着函数会被提升到更靠前的位置。

## 参考

1.  [Hoisting（变量提升） - 术语表 | MDN](https://developer.mozilla.org/zh-CN/docs/Glossary/Hoisting)