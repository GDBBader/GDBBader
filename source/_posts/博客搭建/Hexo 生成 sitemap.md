---

title: Hexo 生成 sitemap
date: 2022-12-04 19:27
tags: [Hexo,博客,sitemap]

---

## 〇、问题
1. 请用一名话描述什么是sitemap.

## 一、什么是sitemap
* 网站地图
* 是用来通知探索引擎哪些页面可供抓取的一个文件，XML格式、txt格式、sitemap索引等

<!-- more -->

## 二、Hexo如何生成sitemap### 2.1 安装插件
### 2.1 安装插件
插件地址：[GitHub - ludoviclefevre/hexo-generator-seo-friendly-sitemap](https://github.com/ludoviclefevre/hexo-generator-seo-friendly-sitemap)
安装：`npm install hexo-generator-seo-friendly-sitemap --save`
配置：
```json
sitemap:
    path: sitemap.xml
    tag: true
    category: false
```
例外：如果哪个页面不需要添加到网站地图中可以在`front-matter`添加`sitemap: false`

### 2.2 生成sitemap
`hexo generate`即可在public文件夹中生成：
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202212041954431.png)


## 参考
1. [sitemap_百度百科](https://baike.baidu.com/item/sitemap/6241567)
2. [GitHub - ludoviclefevre/hexo-generator-seo-friendly-sitemap](https://github.com/ludoviclefevre/hexo-generator-seo-friendly-sitemap)