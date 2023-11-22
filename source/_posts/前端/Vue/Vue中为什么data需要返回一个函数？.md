---

title: Vue中为什么data需要返回一个函数？
date: 2023-08-15 22:58
tags: [JavaScript,Vue]

---
## 一、前言
- 问：为什么vue中一个组件的data需要返回一个函数？
答：因为不返回一个函数而返回一个对象会造成数据共享。
- 问：那为什么返回一个对象会造成数据共享？
答：...

平时一直知道data需要返回一个函数，也知道直接返回一个对象会造成数据共享，因为以前也没有搞懂过这个问题就一直搁置了，今天把这个问题学习记录下。


## 二、什么是Vue组件？
官方文档总是让人难以理解，其中有下面一句话是关键：
> 一个 Vue 组件以一个包含 Vue 特定选项的 JavaScript 对象来定义

即，组件就是一个js对象。其实只要这点理解了，也就明白为什么data直接返回一个对象会出现数据共享的问题了。

## 三、理解

```js
// 一个普通的js对象（想象成这是一个组件）
Person = {
	data:{name:"zhangsan"}
}
// 在两个地方使用同一个Person对象的data
p1Data = Person.data;
p2Data = Person.data;
// 修改p1Data的name属性
p1Data.name = "lisi";
// 分别打印p1Data上的name属性
console.log(p1Data);//{name: "lisi"}
console.log(p2Data);//{name: "lisi"}
```
可以看到`p1Data`、`p2Data`的`name`都是`lisi`。为什么？因为在js中对象在赋值给一个变量时操作的是一个对象的引用，即，`p1Data`、`p2Data`指向的都是同一个对象，都是`Person.data`这个对象。可以理解为有一本书，它有一个名字叫红楼梦（`p1Data`），它还有另外一个名字叫石头记（`p2Data`），其实说的都是那本书。
另外一个问题是：为什么返回的是个函数就不会造成数据共享？
**因为函数是调用一次就执行一次。**
可以通过如下的代码进行验证：
```js
Person = {
	data(){return{name:"zhangsan"}}
}
p1Data = Person.data();
p2Data = Person.data();
p1Data.name = "lisi";
console.log(p1Data);//{name: "lisi"}
console.log(p2Data);//{name: "zhangsan"}
```

## 参考
1. [组件基础 | Vue.js](https://cn.vuejs.org/guide/essentials/component-basics.html#defining-a-component)
2. [你知道vue data为什么是一个函数\_vue.js\_脚本之家](https://www.jb51.net/article/228858.htm)