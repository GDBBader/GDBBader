---


title: div宽度自适应（或指定），高度等于宽度
date: 2021-08-31 13:46:54
tags: [CSS]
type:

---

暂时还未搞懂原理，先记录一下。

```css
.haha {
  width: 30px;
  background-color: blue;
  display: flex;
}
.haha::after{
  padding-top: 100%;
  content: "";
}
```


## 参考

1. [CSS-使用Flex实现元素以宽高比缩放_Moon Star-CSDN博客](https://blog.csdn.net/qq_36157085/article/details/107921214)
