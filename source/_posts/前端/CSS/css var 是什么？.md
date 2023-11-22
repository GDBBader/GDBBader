---


title: css var 是什么？
date: 2021-08-31 13:38:11
tags: [CSS,自定义属性]
type:

---


## 一、CSS自定义属性

分两部分,

margin-top: var(--status-bar-height);

## 二、声明与作用域

```css
.aa{
	--l1-color :red;
}
```


## 三、使用

```css
.aa{
	color: var(--l1-color,blue);
}
```

`blue`为备用值。


## 参考

1. [使用CSS自定义属性（变量） - CSS（层叠样式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Using_CSS_custom_properties)
2. [var() - CSS（层叠样式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/var%28%29)
