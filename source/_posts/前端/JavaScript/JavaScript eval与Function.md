---

title: JavaScript eval与Function
date: 2022-07-22 17:33
tags: [JavaScript]

---
两个函数都可以将字符串转换成js代码。

## 一、eval

```js
let print4 = eval(`
(()=>{
let func = ()=>{return 4;}
return func;
})()
`);

print4();
```

  

## 二、Function

```js
let print5 = new Function(`
return 5;
`);

print5();
```

## 问题

1.  请叙述`eval`与`Function`的功能。

## 参考

1.  [Function - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function)
2.  [Function() constructor - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/Function)
3.  [eval() - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/eval)
