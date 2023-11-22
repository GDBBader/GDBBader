---

title: Nginx 反向代理
date: 2022-11-16 10:24
tags: [Nginx,反向代理,正向代理,代理]

---

## 〇、问题
1. 什么是正向代理？
2. 什么是反向代理？
3. Nginx如何配置反向代理？

## 一、前言
今天有工作上一个任务，现在有一个Java写的接口，是发布在8081端口上的；但是本机只对外开放了80端口，因此需要将http://127.0.0.1/api指向http://127.0.0.1:8081。

<!-- more -->

## 二、正向代理&反向代理
### 2.1 正向代理
先来看百度的解释：
> 正向代理，意思是一个位于客户端和原始服务器(origin server)之间的服务器，为了从原始服务器取得内容，客户端向代理发送一个请求并指定目标(原始服务器)，然后代理向原始服务器转交请求并将获得的内容返回给客户端。客户端才能使用正向代理。

理解：
我平时在用一个浏览器插件，叫做[Proxy SwitchyOmega](https://microsoftedge.microsoft.com/addons/detail/proxy-switchyomega/fdbloeknjpnloaggplaobopplkdhnikc)，在内网访问外网的时候我会使用切换其配置来达到访问外网的目的，这就是正向代理。

### 2.2 反向代理
先来看百度的解释：
> 反向代理服务器位于用户与目标服务器之间，但是对于用户而言，反向代理服务器就相当于目标服务器，即用户直接访问反向代理服务器就可以获得目标服务器的资源。同时，用户不需要知道目标服务器的地址，也无须在用户端作任何设定。反向代理服务器通常可用来作为Web加速，即使用反向代理作为Web服务器的前置机来降低网络和服务器的负载，提高访问效率。

理解：
你访问的地址是http://127.0.0.1/api，但你不知道的是它把你的请求给了http://127.0.0.1:8081。


## 三、Nginx配置反向代理
```json
server {
	listen      80;
	server_name 127.0.0.1;
	location /api/ {
		proxy_pass    http://127.0.0.1:8081/;
	}
}
```
注意：
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202211161052920.png)

## 参考
1. [反向代理_百度百科](https://baike.baidu.com/item/%E5%8F%8D%E5%90%91%E4%BB%A3%E7%90%86/7793488)
2. [Proxy SwitchyOmega - Microsoft Edge Addons](https://microsoftedge.microsoft.com/addons/detail/proxy-switchyomega/fdbloeknjpnloaggplaobopplkdhnikc)
3. [正向代理_百度百科](https://baike.baidu.com/item/%E6%AD%A3%E5%90%91%E4%BB%A3%E7%90%86/9524799)
4. [ Nginx配置——反向代理_止步前行的博客-CSDN博客_nginx反向代理](https://blog.csdn.net/zxd1435513775/article/details/102508463)