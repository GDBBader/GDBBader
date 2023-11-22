---

title: uni-app picker 组件的 range-key属性
date: 2021-03-13 11:52:19
tags: [uni-app,picker,vue,组件]

---

## 一、前言

饶了远路了。
我竟然将对象数组给转换成字符串数组之后才进行使用。根本没有用到range-key。


## 二、学习

> 当 range 是一个 Array＜Object＞ 时，通过 range-key 来指定 Object 中 key 的值作为选择器显示内容



## 三、使用

```html
...
<picker @change="changeFunc" :value="aIndex" mode="selector" :range="aList" range-key="name">
    <view class="uni-input" style="background-color: #eee; border-radius: 5px;">{{aList[aIndex].name}}</view>
</picker>
...
aList:[
    {
    	name:'鸽子',
    	id:'a1'
    },
    {
    	name:'乌龟',
    	id:'a2'
    },
],
wjTypeIndex:0,
...
```


## 四、注意事项

`range-key`里面写对象的项的名字


## 参考

1. [picker - uni-app官网](https://uniapp.dcloud.io/component/picker)
