---


title: uni-app 页面高度小于100%时无法触发 onReachBottom 的解决办法
date: 2021-06-10 11:54:26
tags: [uni-app,onReachBottom]
type:

---


## 一、什么是onReachBottom？

- 页面生命周期
- 代表**页面滚动到底部的事件**
- 常用于加载下一页数据
- 可在pages.json里定义具体页面底部的触发距离onReachBottomDistance

<--more-->


## 二、常见问题

1. 当页面加载了较少数据无法充满一屏时，无法触发onReachBottom生命周期。此时可给page设置高度来解决

```css
page{
    heigit: 100%;
}
```
