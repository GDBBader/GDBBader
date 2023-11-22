---


title: vue自定义事件
date: 2021-07-19 17:16:39
tags: [vue,JavaScript,]
type:

---


## 一、自定义事件

通过`$emit`生成

```javascript
this.$emit('my-event',666)
```

## 二、事件监听

通过`v-on`监听，是在HTML中监听。

```html
<my-component v-on:my-event="doSomething($event)"></my-component>
```

`$event`代表666


## 参考

1. [事件处理 — Vue.js](https://cn.vuejs.org/v2/guide/events.html)
2. [自定义事件 — Vue.js](https://cn.vuejs.org/v2/guide/components-custom-events.html)
