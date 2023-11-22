---

title: 什么是 Obsidian Url？
date: 2023-02-15 21:30
tags: [Obsidian]

---
## 〇、问题
1. Url Scheme是什么？

## 一、前言
平时记的博客等文件为了加强记忆是将发布好的网页Url保存在Anki中。复习时就点击打开对应的网页来查看。就想着有没有能从Obsidian外部直接打开对应笔记的方式。果然，通过[[Url Scheme 1]]。

<!-- more -->

## 二、Obsidian的Url Scheme格式
1. 打开Obsidian `obsidian://`
2. 打开对应的笔记 `obsidian://open?vault=ob&file=fileId`
其中fileId是对应笔记标题的URI编码，例如：
```js
> encodeURI("什么是 Obsidian Url？");
< '%E4%BB%80%E4%B9%88%E6%98%AF%20Obsidian%20Url%EF%BC%9F'
```

## 三、打开本笔记的Url Scheme
`obsidian://open?vault=ob&file=%E4%BB%80%E4%B9%88%E6%98%AF%20Obsidian%20Url%EF%BC%9F`

## 参考
1. [encodeURI() - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/encodeURI)
2. [Intro to URL schemes in Shortcuts on iPhone or iPad – Apple Support (AU)](https://support.apple.com/en-au/guide/shortcuts/apd621a1ad7a/ios)