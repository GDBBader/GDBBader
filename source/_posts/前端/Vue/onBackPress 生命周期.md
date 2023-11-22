---


title: onBackPress 生命周期
date: 2021-05-20 00:09:06
tags: [生命周期,onBackPress,uni-app]
type:

---


# 一、引子

A->X:X页面返回，需要返回到A页面并触发A页面刷新
D->E->X:X页面返回，需要返回到D页面


# 二、思路


## 返回至哪个页面

1. X页面加一个标志位F，判断X页面的来源
2. 根据标志位F来决定需要返回至哪个页面（使用onBackPress页面生命周期可以做到）


## 触发A页面刷新

1. A页面加一个侦听器（功能是刷新页面）
2. X页面返回A页面时触发A页面侦听器（可通过在A页面设置变量，侦听器侦听变量R，如果变量R更改即触发刷新;从X页面返回时修改R即可。参看以前的文章[Uniapp返回上一页触发页面更新_qiebzps的博客-CSDN博客](https://blog.csdn.net/qq_31646657/article/details/111053707)

---


# 参考

1. [uni-app自定义返回逻辑教程 - DCloud问答](https://ask.dcloud.net.cn/article/35120)
2. [生命周期 - uni-app官网](https://uniapp.dcloud.io/collocation/frame/lifecycle?id=%e9%a1%b5%e9%9d%a2%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f)
3. [Uniapp返回上一页触发页面更新_qiebzps的博客-CSDN博客](https://blog.csdn.net/qq_31646657/article/details/111053707)
