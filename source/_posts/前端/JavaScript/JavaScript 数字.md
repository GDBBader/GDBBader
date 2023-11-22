---

title: JavaScript 数字
date: 2022-07-16 11:32
tags: [JavaScript]

---
根据语言规范，JavaScript 采用 “遵循 IEEE 754 标准的双精度 64 位格式”（"double-precision 64-bit format IEEE 754 values"）表示数字。——在 JavaScript（除了`[BigInt](/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/BigInt)`）当中，**并不存在整数 / 整型 (Integer)。** 因此在处理如下的场景时候，您一定要小心：

一个看上去是整数的东西，其实都是浮点数。

```js
0.1 + 0.2 = 0.30000000000000004
```

  

## 参考
1. [https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/A_re-introduction_to_JavaScript](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/A_re-introduction_to_JavaScript)