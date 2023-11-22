---


title: Content-Type 是什么
date: 2021-07-27 18:45:30
tags: [http,MIME]
type:

---


## 一、引言

在调试Web Service时，SOAP指定请求头包含以下栏位：

```
Content-Type: text/xml; charset=utf-8
```

## 二、含义

> 用于指示资源的MIME类型 [media type](https://developer.mozilla.org/zh-CN/docs/Glossary/MIME_type) 。
在请求中 (如[`POST`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/POST) 或 [`PUT`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/PUT))，客户端告诉服务器实际发送的数据类型。



## 参考

1. [Content-Type - HTTP | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Type)
