---

title: JavaScript new
date: 2022-07-26 18:06
tags: [JavaScript]

---
> [new](/zh-CN/docs/Web/JavaScript/Reference/Operators/new)，它和 `this` 密切相关。它的作用是创建一个崭新的空对象，然后使用指向那个对象的 `this` 调用特定的函数。注意，含有 `this` 的特定函数不会返回任何值，只会修改 `this` 对象本身。`new` 关键字将生成的 `this` 对象返回给调用方，而被 `new` 调用的函数称为构造函数。习惯的做法是将这些函数的首字母大写，这样用 `new` 调用他们的时候就容易识别了。

## 参考
1. [https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/A_re-introduction_to_JavaScript](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/A_re-introduction_to_JavaScript)