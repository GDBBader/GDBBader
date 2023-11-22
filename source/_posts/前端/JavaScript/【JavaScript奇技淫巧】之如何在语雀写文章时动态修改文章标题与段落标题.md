---

title: 【JavaScript奇技淫巧】之如何在语雀写文章时动态修改文章标题与段落标题
date: 2022-07-26 18:06
tags: [JavaScript]

---
## 一、前言

有这么个需求：语雀的标题太招摇了，写文章时身边路过的人又有好奇宝宝，因此记录一下写文章时将标题字体大小调整为14px的方案。

## 二、知识点

1.  如何通过地址栏执行JavaScript代码
2.  如何向DOM绑定点击事件
3.  JavaScript如何修改元素样式

## 三、思路

1.  第一阶段

1.  找到对应元素
2.  修改元素的fontSize即可

2.  第二阶段

第一阶段可以在控制台手动实现，但每增加一次段落标题就要重新运行一次。可函数封装后通过body元素的点击事件调用。即每增加一次段落后点击页面及可调整字体大小。

1.  将第一阶段内容写成函数
2.  将函数绑定至body元素的click事件

## 四、实现

```js
/* 監聽body click事件 */
document.body.addEventListener('click', function (evt) {
    console.log("修改頁面字體大小");

    /* 定義字體大小 */
    FONTSIZE = "14px";

    /* 修改文章標題 */
    articleTitle = document.getElementById("article-title");
    if (articleTitle) {
        articleTitle.style.fontSize = FONTSIZE;
    }

    lakeTitle = document.getElementsByClassName("lake-title")[0];
    if (lakeTitle) {
        lakeTitle.style.fontSize = FONTSIZE;
    }

    /* 修改段落標題 */
    neTextList = document.getElementsByTagName("ne-text");
    for (i in neTextList) {
        try {
            item = neTextList[i];
            item.style.fontSize = FONTSIZE;
        } catch (error) {
            
        }
        
    }
    
}, false);
```

将以上代码压缩为一行后放置在地址栏，在代码前增加`javascript:`，收藏至收藏夹即可。

## 参考

1.  [理解Javascript中的事件绑定与事件委托 - SegmentFault 思否](https://segmentfault.com/a/1190000006667581)