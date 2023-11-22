---


title: 如何利用 Token 令牌使用户不能在多台设备登录
date: 2021-08-11 15:01:52
tags: [Token,令牌,HTTP]
type:

---


## 什么是Token？

就是一个服务器生成的字符串。当成两人交流的**暗号**即可。如何使用还是两人来约定。

> [四，接口认证方式：Bearer Token - 简书](https://www.jianshu.com/p/8f7009456abc)token放在Redis中。因为在申请jwt令牌时，spring security会响应用户身份令牌,把它作为key,jwt令牌作为value添加到Redis中。然后前端请求服务端都必须携带jwt令牌，可以把身份令牌保存到cookie。从Redis查询jwt令牌设置到header. 通过ZuulFilter拦截所有请求 ,校验请求头是否有jwt令牌，是否有cookie，从Redis查jwt令牌是否过期，全都通过则放行



## 个人理解

![[Token 服务器大致原理.png]]

---


## 参考

1. [Token（计算机术语）_百度百科](https://baike.baidu.com/item/Token/2615248)
