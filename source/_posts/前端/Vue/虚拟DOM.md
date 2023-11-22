---

title: 虚拟DOM
date: 2021-12-27 17:04
tags: [HTML,JavaScript,Vue]

---
## 一、什么是DOM？
文档对象模型
指的是HTML元素以及在其上的操作方法。其中元素由tag、props、children组成：
```html
<div id="app">
  <p class="text">TXM to SFM</p>
</div>
```

## 二、什么是虚拟DOM？
虚拟DOM，那就不是真实的DOM。这里指的是用JavaScript的Object对象模描述出来的元素。而后会通过特定的渲染方法将其渲染成其实的DOM元素。下面一一种虚拟DOM的表示方法：
```js
{
  tag: 'div',
  props: {
    id: 'app'
  },
  chidren: [
    {
      tag: 'p',
      props: {
        className: 'text'
      },
      chidren: [
        'TXM to SFM'
      ]
    }
  ]
}
```

## 参考

1.  [对虚拟DOM和Dom-Diff的理解？ - SegmentFault 思否](https://segmentfault.com/a/1190000022277663)
2.  [HTML DOM 简介 | 菜鸟教程](https://www.runoob.com/htmldom/htmldom-intro.html)