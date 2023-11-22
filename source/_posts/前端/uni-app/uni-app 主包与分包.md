---


title: uni-app 主包与分包
date: 2021-04-10 23:07:56
tags: [uni-app,分包]
type:

---


# 理解

启动加载主包，按需要加载分包。


# 作用

- 小程序：提高进入页面时的加载速度，不至于说我进入小程序必须等所有页
- APP：提升首页是vue时的启动速度

> App默认为整包。从uni-app 2.7.12+ 开始，也兼容了小程序的分包配置。其目的不用于下载提速，而用于首页是vue时的启动提速。


---


# 参考

1. [pages.json - uni-app官网](https://uniapp.dcloud.io/collocation/pages?id=subpackages)
