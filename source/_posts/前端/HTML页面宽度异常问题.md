---


title: HTML页面宽度异常问题
date: 2021-03-30 23:34:14
tags: [HTML,CSS]
type:

---

写了一个HTML,发现宽度在手机上显示的不同,有的手机上会是这样:
![](https://img-blog.csdnimg.cn/20201201224849334.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

有的会是这样:
![](https://img-blog.csdnimg.cn/20201201224730546.png#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

首先看到的是字体大小不一样,影响因素有二:

- -webkit-text-size-adjust: none;
- <meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no" />
看了一些文章,感觉这里边的水还深着呢,先了解到这种程度.


## window.devicePixelRatio

= 物理像素 / 独立像素 = 屏幕实际有多少个px / CSS width=100% 有多少个px
当window.devicePixelRatio=2时，代表一个CSS像素点等于两个物理像素点。


## viewport 视区

- layout viewport
- visual viewport
- ideal viewport


## text-size-adjust 文本溢出算法


## 分辨率（每一个方向上的像素数量）

两种表示方式

- 640*480
- 72ppi 8英寸*6英寸


### 分辨率与像素的关系

一张分辨率为640 x 480的图片，那它的分辨率就达到了307200像素。
一张分辨率为1600 x 1200的图片，它的像素就是200万。


## ppi、dpi的 区别？

- p 像素  屏幕、显示器
- d 点    打印机、印刷


## 参考

1. [viewport 深入理解 | 菜鸟教程](https://www.runoob.com/w3cnote/viewport-deep-understanding.html)
2. [text-size-adjust - CSS（层叠样式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-size-adjust)
3. [响应式 Web 设计 – Viewport | 菜鸟教程](https://www.runoob.com/css/css-rwd-viewport.html)
4. [属性选择器 - CSS（层叠样式表） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Attribute_selectors)
5. [分辨率（显示分辨率与图像分辨率）_百度百科](https://baike.baidu.com/item/%E5%88%86%E8%BE%A8%E7%8E%87/213523)
6. [像素_百度百科](https://baike.baidu.com/item/%E5%83%8F%E7%B4%A0/95084)
7. [visual viewport和layout viewport - SegmentFault 思否](https://segmentfault.com/a/1190000006068808)
