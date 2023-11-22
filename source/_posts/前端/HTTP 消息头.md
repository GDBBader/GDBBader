---

title: HTTP 消息头
date: 2022-11-16 14:36
tags: [HTTP,X-Real-IP,Host,X-Forwarded-For,Nginx]

---
## 〇、问题
1. 什么是HTTP Headers？
2. 作用是什么？

## 一、前言
在配置Nginx时遇到一些Host、X-Real-IP、X-Forwarded-For概念，这些都是HTTP的基本概念，在此学习记录一下。

<!-- more -->

## 二、什么是消息头？
> HTTP 消息头允许客户端和服务器通过 request和 response传递附加信息。

理解：
例如有一个根据书号查询图书作者的接口，客户端只需要调用接口时传一个书号即可。那HTTP Headers中的客户端IP、cookies等信息就是所谓的附加信息。

## 三、Host
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202211161450028.png)

一个用来保存域名的栏位。

## 四、X-Real-IP
你往里边存什么，它就是什么。就是一个普通的栏位而已。
如，在Nginx中可以使用如下配置：
```json
proxy_set_header X-Real-IP $remote_addr;
```
那么其中就会保存`$remote_addr`，ip_a->ip_b->ip_c，其中ip_b是一台代理，那么ip_c看到的X-Real-IP就是ip_b。

## 五、X-Forwarded-For
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202211161500645.png)
这是用来保存最初发起请示的客户端的IP地址。

## 参考
1. [HTTP Headers - HTTP | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers)
2. [X-Forwarded-For - HTTP | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/X-Forwarded-For)
3. [X-Forwarded-For 和 X-Real-IP 的区别？ - 猪啊美 - 博客园](https://www.cnblogs.com/mypath/articles/5239687.html)