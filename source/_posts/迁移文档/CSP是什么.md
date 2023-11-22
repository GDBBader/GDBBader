---

title: CSP是什么
date: 2022-06-20 11:19
tags: [HTML,JavaScript,CSP]

---
## 一、前言

在从收藏夹的标签向页面注入调用外部接口的操作时浏览器调用外部接口失败并返回如下提示：

```
Refused to connect to 'http://127.0.0.1:8085/getPageJson' because it violates the following Content Security Policy directive: "connect-src 'self' updates.developer.allizom.org updates.developer.mozilla.org www.google-analytics.com stats.g.doubleclick.net".
```

相关`js`代码如下：

```js
(()=>{
  httpRequest = new XMLHttpRequest();
  
    httpRequest.onreadystatechange = alertContents;
    httpRequest.open('GET', 'http://127.0.0.1:8085/getPageJson');
    httpRequest.send();
  
    function alertContents() {
    if (httpRequest.readyState === XMLHttpRequest.DONE) {
      if (httpRequest.status === 200) {
        alert(httpRequest.responseText);
      } else {
        alert('There was a problem with the request.');
      }
    }
  }
})()
```

经过查找原因后大致可知是`CSP`把所调用的地址给禁止了。

## 二、什么是CSP？

```
`Content-Security-Policy`
```

控制用户代理能够为指定的页面加载哪些资源

如何使用`CSP`：
```html
<meta http-equiv="Content-Security-Policy" content="default-src https:">

<meta http-equiv="Content-Security-Policy" content="default-src 'self' *">
```

## 三、解决方案

通过向页面增加`Content-Security-Policy`的配置信息来去除对调用外部链接的限制：

```js
appendMeta();

function appendMeta() {
  var meta = document.createElement('meta');
  httpEquiv = "Content-Security-Policy";
  content = "default-src 'self' *";
  meta.httpEquiv = httpEquiv;
  meta.content = content;

  document.head.appendChild(meta);
}
```

  

## 问题

1.  `CSP`全称是什么？

```
Content-Security-Policy
```

2.  一句话说明其作用。

控制能够加载的资源，防止跨站脚本攻击

## 参考

1.  [Content-Security-Policy - HTTP | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Security-Policy)