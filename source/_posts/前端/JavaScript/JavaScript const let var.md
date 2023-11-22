---

title: JavaScript const let var  
date: 2021-09-26 23:09
tags: [JavaScript,变量]  
type:

---

## 一、JavaScript 创建变量的几种方式
```js
// 全局变量
a = 1;
// 局部变量
let b = 2;
// 常亮
const c = 3;
```
`const` 定义成对象或数组时，不能重写，但对象的属性并不在保护范围。即：
```js
const str = 'aaa';// 不能重新赋值
const obj = {
	age:12// 可以重新赋值
};
```
  

## 参考
1.  [const - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/const)