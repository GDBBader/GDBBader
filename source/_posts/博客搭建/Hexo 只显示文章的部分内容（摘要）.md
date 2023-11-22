---

title: Hexo 只显示文章的部分内容（摘要）
date: 2022-09-19 20:13
tags: [博客,Hexo]

---
## 一、前言
Hexo的landscape主题默认在主页显示文章的全部内容，不适合主页的快速浏览，因此在此记录一下如何配置只显示文章的部分内容。
<!-- more -->

## 二、方案
```html
<!-- more -->
```
其他的主题也有支持在文章的metadata中单独写摘要的方式，但是官方的这种方式不需要更换主题，也比较简单，因此在这里还用官方提供的方式。

## 参考
1. [标签插件（Tag Plugins） | Hexo](https://hexo.io/zh-cn/docs/tag-plugins#%E6%96%87%E7%AB%A0%E6%91%98%E8%A6%81%E5%92%8C%E6%88%AA%E6%96%AD)