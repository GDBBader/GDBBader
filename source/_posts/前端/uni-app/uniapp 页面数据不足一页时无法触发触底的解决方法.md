---


title: uniapp 页面数据不足一页时无法触发触底的解决方法
date: 2021-07-15 11:49:56
tags: [uniapp,生命周期]
type:

---


## 一、引言

当使用`onReachBottom`生命周期时，假如初始化加载的数据不足一页，将无法触发`onReachBottom`。

## 二、解决

```css
page{
    height: 100%;
}
```


## 参考

1. [uni-app官网](https://uniapp.dcloud.io/collocation/frame/lifetime?id=%e9%a1%b5%e9%9d%a2%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f)
