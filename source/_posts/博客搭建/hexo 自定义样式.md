---


title: hexo 自定义样式
date: 2021-08-07 21:15:32
tags: [hexo,博客]
type:

---


## 一、引言

hexo默认的主题的引用样式（如下图）不太舒服，想要修改。记录一下自定义样式的过程。

- 默认样式
![](https://gitee.com/qiebzps/pic/raw/master/img/20210807212128.png#alt=)

## 二、步骤

![](https://gitee.com/qiebzps/pic/raw/master/img/20210807212245.png#alt=)


### 2.1 找到需要修改的样式的CSS选择器

![](https://gitee.com/qiebzps/pic/raw/master/img/20210807212711.png#alt=)

```css
.article-entry blockquote {
    font-family: Georgia, "Times New Roman", serif;
    font-size: 1.4em;
    margin: 1.6em 20px;
    text-align: center;
}
```


### 2.2 根据需要调整为想要的样式

（看着Obsidian的引用样式比较顺眼，因此这里采用Obsidian的样式）

1. 查看Obsidian引用的样式  Ctrl+shift+i 调用调试窗口
2. 找到对应的引用样式如下

```css
.markdown-preview-view blockquote {
  border-radius: 0 4px 4px 0;
  border: 1px solid var(--background-modifier-border);
  border-left-width: 5px;
  padding: 10px 20px;
  margin-inline-start: 30px;
  margin-inline-end: 30px;
}
```


### 2.3 在hexo下引用自定义的css文件

1. 


## 参考

1. [hexo主题—自定义样式_欢迎来到Gavin zijef的博客，请多指教-CSDN博客_hexo自定义主题](https://blog.csdn.net/qq_42595443/article/details/82263318)
