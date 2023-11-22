---

title: 博客迁移至 Obsidian
date: 2023-04-11 22:10
tags: [博客,JavaScript]

---
## 一、前言
以前写在语雀中的文档有不少，一篇一篇复制粘贴过于麻烦，到今天也迟迟没有都迁移至Obsidian。今天想起来可以用TinyTask来进行重复性的复制粘贴，但是每往篇文章的标题有的长，有的短，导致无法保证定位准确，在此记录一下解决方案：通过删除标题元素解决。

<!-- more -->

## 二、整体思路
第一步：提取语雀文章标题并粘贴至Obsidian
第二步：删除语雀网页上的标题
第三步：通过TinyTask复制文章内容至Obsidian

## 三、实现
### 3.1 提取语雀文章标题并粘贴至Obsidian
1. 找到标题元素![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2023/20230411221924.png)
标题元素的`id="article-title"`
2. 代码
```js
(()=>{
	titleElement = document.getElementById("article-title");
	title = titleElement.getInnerHTML();
	// 复制到剪切板
	navigator.copliboard.writeText(title);
})()
```
上述功能可以通过向页面注入按钮的方式（博客中有关于如何向页面注入按钮的文章）添加到页面上。

### 3.2 删除语雀网页上的标题
```js
titleElement.remove()
```

```js
(()=>{
	let titleElement = document.getElementById("article-title");
	let title = titleElement.getInnerHTML();
	navigator.clipboard.writeText(title);
	titleElement.remove();
})()
```

### 3.3 通过TinyTask复制文章内容至Obsidian