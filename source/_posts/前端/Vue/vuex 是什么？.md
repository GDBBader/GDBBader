---


title: vuex 是什么？
date: 2021-08-31 17:39:51
tags: [vuex,vue.js,uni-app,JavaScript,全局变量]
type:

---


## 一、vuex 是什么?

理解:是一种保存全局变量的方式。

> 当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。


## 二、与全局变量的不同

1. 
Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。

2. 
你不能直接改变 store 中的状态。改变 store 中的状态的唯一途径就是显式地**提交 (commit) mutation**。这样使得我们可以方便地跟踪每一个状态的变化，从而让我们能够实现一些工具帮助我们更好地了解我们的应用。



## 参考

1. [开始 | Vuex](https://vuex.vuejs.org/zh/guide/)
