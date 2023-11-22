---

title: Fetch 学习
date: 2022-06-22 14:10
tags: [JavaScript]

---
## 一、什么是`Fetch`

-   是一个`API`
-   用来获取网络资源的，以前是使用`XMLHttpRequest`实现的
-   基于`Promise`

## 二、如何发起get、post

```js
async function getDoc(){
    return await fetch('https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch')
}
```

```js
getDoc().then(res=>{
    console.log(res);
}).catch();
```

```js
async function getDoc(){
    return await fetch('https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch',{
        method:'POST',
        body:JSON.stringify({a:3})
    })
}
```

```js
getDoc().then(res=>{
    console.log(res);
}).catch();
```
`post`只需要在`fetch`的第二个参数中指定`method`即可。

## 二、.json的作用
```js
fetch('http://example.com/movies.json')
  .then(response => response.json())
  .then(data => console.log(data));
```
返回一个将响应 body 解析成 JSON 的 promise

也就是`.json`过的内容只等下了`response`中的`data`。

## 问题

1.  什么是`fetch`？
2.  如何发起`get`、`post`？

## 参考

1.  [Fetch API - Web API 接口参考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API#%E6%B5%8F%E8%A7%88%E5%99%A8%E5%85%BC%E5%AE%B9)
2.  [使用 Fetch - Web API 接口参考 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch)