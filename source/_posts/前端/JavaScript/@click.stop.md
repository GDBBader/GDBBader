---

title: @click.stop
date: 2021-08-11 11:39:17
tags: [uni-app, vue]

---


## 一、引言

两元素嵌套, 并且两元素都绑定了点击事件, 此时, 点击内部元素时会一并触发外部元素的点击事件. 可使用.stop事件修饰符来阻止事件的传播.

## 二、

```html
<div @click.stop="cFather">
    <div @click.stop="cChild">haha</div>
</div>
```

```javascript
methods: {
    cFather: function() {
        console.log('Father')
    },
    cChild: function() {
        console.log('Child')
    },
}
```


## 参考

1. [事件处理 — Vue.js](https://cn.vuejs.org/v2/guide/events.html#%E4%BA%8B%E4%BB%B6%E4%BF%AE%E9%A5%B0%E7%AC%A6)
