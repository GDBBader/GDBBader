---

title: Vue.component
date: 2022-09-13 21:32:08
tags: [Vue]

---
## 哪个版本的写法？
Vue2
<!-- more -->
## Vue.component的作用？
1. 注册全局组件
2. 获取全局组件
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202209152131981.png)

## Vue2中如何局部注册？
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202209152131672.png)

## 为什么平时看到的项目中的局部写法并不是以上列示的写法？
平时使用的是cue-cli构建的项目，vue-cli使用的是webpack、Babel来使用ES2015模块的，那么：
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202209152132580.png)

## 问题
1. `Vue.component`的作用与用法？
> `Vue.component`的作用是注册组件；全局注册。
2. 与`new Vue({components:{}})`中的`components`的区别是什么？
> `components`的作用是注册组件，局部注册。

## 参考
1. [API — Vue.js](https://v2.cn.vuejs.org/v2/api/index.html#Vue-component)
2. [组件注册 — Vue.js](https://v2.cn.vuejs.org/v2/guide/components-registration.html#%E5%B1%80%E9%83%A8%E6%B3%A8%E5%86%8C)