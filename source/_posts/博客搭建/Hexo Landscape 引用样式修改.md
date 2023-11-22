---

title: Hexo Landscape 引用样式修改
date: 2022-10-07 22:10
tags: [Hexo,Landscape,博客,CSS]

---
## 一、前言
不太适应Landscape的引用样式，在这里记录一下如何修改。
默认引用的样式如下：
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210072213678.png)
<!-- more -->

## 二、配置文件所在位置
`\themes\landscape\source\css\_partial\article.styl`
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210072216141.png)

## 三、修改
```styl
  blockquote
    background-color: #f5f5f5
    font-family: font-serif
    font-size: 1.2em
    margin: line-height 10px
    text-align: left
    footer
      font-size: font-size
      margin: line-height 0
      font-family: font-sans
      cite
        &:before
          content: "—"
          padding: 0 0.5em
```
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210072221918.png)
如果运行`hexo g`后没有效果，那是因为hexo的差分机制，运行`hexo g -f`强制重新生成文件即可。

## 参考
1. [指令 | Hexo](https://hexo.io/zh-cn/docs/commands.html#generate)