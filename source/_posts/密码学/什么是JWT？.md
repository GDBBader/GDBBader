---


title: 什么是JWT？
date: 2021-08-31 15:06:42
tags: [JWT,密码,JSON,token]
type:

---


## 一、什么是JWT?

个人理解：是一种生成token的方法。

aaa.bbb.ccc就是一个JWT，简单来说就是一段字符串，由两个`.`间隔形成三部分，这三部分都是base后的JSON。

生成的token包含：

- Header（头部）
- Payload（负载）
- Signature（签名）(是对Header,Payload的加盐(私钥)hash)

## 二、作用-身份认证

JWT是一段字符串，由服务端生成的，发送给客户端保存的，客户端每次请求需要携带此字符串用来验证客户身份。


## 参考

1. [JSON Web Token 入门教程 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html)
