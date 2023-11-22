---

title: sessionStorage与localStorage
date: 2022-06-22 15:36
tags: [sessionStorage,localStorage,JavaScript]

---
## 一、前言

`**sessionStorage**`**用途：**

-   页面异步发起多个请求时，多个请求都返回登录过期，可在`sessionStorage`添加标志位来标识页面上是否已经存在登录过期的弹框
-   临时保存表单中某些数据防止页面崩溃或误刷新导致数据丢失

`**localStorage**`**用途：**

与`sessionStorage`类似，不过`localStorage`的数据不会随着页面的关闭而清除，在同源的多个标签页也是数据共享的，而`seesionStorage`只在当前标签页可用。

## 二、常用方法

```javascript
sessionStorage.getItem("key1");
sessionStorage.setItem("key1",true);

localStorage.getItem("key1");
localStorage.setItem("key1",true);
```

## 问题

1.  举两个常用的`sessionStorage`应用场景。
2.  请描述`sessionStorage`与`localStorage`的区别。

## 参考

1.  [LocalStorage，sessionStorage](https://zh.javascript.info/localstorage)
2.  [Window.localStorage - Web API 接口参考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/localStorage)
3.  [Window.sessionStorage - Web API 接口参考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/sessionStorage)