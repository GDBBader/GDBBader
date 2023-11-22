---

title: Hexo Landscape 主题搜索功能无法使用解决
date: 2022-10-06 20:51
tags: [hexo,landscape,博客]

---
## 一、前言
Landscape 这个默认的主题有自带的搜索，但是无法使用（点击之后没有反应），在此记录一下解决过程。

<!-- more -->

## 二、排查解决过程
### 2.1 修复自带的搜索
1. 发现问题
发现缺少jQuery
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210062142519.png)
3. 尝试更换jQuery地址
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210062144508.png)
至此，Hexo Landscape主题自带的搜索是可以用了。但是，这使用的Google，而对于一个新的博客网站来说可以Google还没有收录，另外在国内也无法使用Google。因此，需要替换成站内搜索。
### 2.2 实现站内搜索
TODO

## 参考
1. 