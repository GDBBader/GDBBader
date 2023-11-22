---


title: Vue.js 模板引用
date: 2021-09-01 15:15
tags: [vue,ref]
type:

---


## 一、什么是模板引用?

一种引用模板(元素)的方式。
可使用`ref`属性给组件或HTML元素指定ID。


## 二、如何使用(vue2)？

```html
<!-- 父组件 -->
<base-input ref="usernameInput"></base-input>
<!-- 子组件 -->
<input ref="input">
```

```javascript
//子组件方法
methods: { 
	// 用来从父级组件聚焦输入框 
	focus: function () { 
		this.$refs.input.focus() 
	} 
}
```

通过`this.$refs.usernameInput.focus()`调用子组件的`focus`方法


## 参考

1. [模板引用 | Vue.js](https://v3.cn.vuejs.org/guide/component-template-refs.html)
2. [处理边界情况 — Vue.js](https://cn.vuejs.org/v2/guide/components-edge-cases.html#%E8%AE%BF%E9%97%AE%E5%AD%90%E7%BB%84%E4%BB%B6%E5%AE%9E%E4%BE%8B%E6%88%96%E5%AD%90%E5%85%83%E7%B4%A0)
