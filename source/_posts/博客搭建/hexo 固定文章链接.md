---


title: hexo 固定文章链接
date: 2021-04-03 10:18:45
tags: [hexo,博客]
type:

---


## 一、引言

博客的文章需要在其他地方引用。但是文章多了之后，使用文件夹来管理文章，发现文章链接变了。记一下配置方法。

## 二、解决方案

找到配置文件`_config.yml`并修改如下即可

```
#原配置
#permalink: :year/:month/:day/:title/

#现配置
permalink: :year/:month/:day/:name/
```


## 参考

1. [使用子文件夹管理 Hexo 文章且不改变文章永久链接 - PRIN BLOG](https://printempw.github.io/hexo-posts-in-subfolder/)
