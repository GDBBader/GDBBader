---


title: uni-app 自定义返回逻辑
date: 2021-04-10 23:06:49
tags: [uni-app,生命周期]
type:

---


# 引子

有需求需要从一个页面A进入页面B，但是页面B“返回上一页”时需要直接返回首页。


# `onBackPress`监听页面返回

当用户进行以下操作时，会触发该函数：

- Android 实体返回键 (`from = backbutton`)
- 顶部导航栏左边的返回按钮 (`from = backbutton`)
- 返回 API，即 `uni.navigateBack()` (`from = navigateBack`)


# 参考

1. [uni-app自定义返回逻辑教程 - DCloud问答](https://ask.dcloud.net.cn/article/35120)
2. [生命周期 - uni-app官网](https://uniapp.dcloud.io/collocation/frame/lifecycle?id=%e9%a1%b5%e9%9d%a2%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f)
