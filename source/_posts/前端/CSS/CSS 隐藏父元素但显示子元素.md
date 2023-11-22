---


title: CSS 隐藏父元素但显示子元素
date: 2021-08-18 09:20:04
tags: [CSS]
type:

---


## 一、引言

某一组件元素嵌套，现需要仅显示子元素的样式。

## 二、解决

```css
.parent { visibility: hidden; }
.child { visibility: visible; }
```


## 参考

1. [visibility - CSS（层叠样式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/visibility)
