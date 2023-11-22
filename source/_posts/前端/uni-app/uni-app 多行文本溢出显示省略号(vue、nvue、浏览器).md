---


title: uni-app 多行文本溢出显示省略号(vue、nvue、浏览器)
date: 2021-03-30 23:43:52
tags: [uni-app,vue,nvue]
type:

---


# 一、浏览器


# 二、vue

```javascript
<text class="text_vue">你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好</text>
<view class="text_vue">你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好</view>
.text_vue{
    /* 需要有宽度 */
    width: 200rpx;
    /* 超过了就隐藏 */
    overflow: hidden;
    /* 超过了就显示省略号 */
    text-overflow: ellipsis;
    
    /* webkit内核的浏览器 */
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
}
```

注意：

1. `text`与`view`标签都可以，在这里显示效果一样
2. `width: 200rpx;`需要给标签宽度
3. `overflow: hidden;`告诉渲染引擎如果溢出了就要隐藏
4. `text-overflow: ellipsis;`告诉渲染引擎溢出了显示省略号
5. `display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical;`告诉以webkit为内核的渲染引擎需要渲染3行，因为[[什么是webview？|WebView]]是一个基于webkit引擎所以它能听懂,而当在[[uni-app 是什么？|uni-app]]中使用vue页面时，使用的就是[[什么是webview？|WebView]]渲染。

> 在App端，如果使用vue页面，则使用[[什么是webview？|webview]]渲染；如果使用nvue页面(native vue的缩写)，则使用原生渲染。[综述 - uni-app官网](https://uniapp.dcloud.io/nvue-outline)



# 三、nvue

```javascript
<text class="text_nvue">你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好你好</text>
.text_nvue{
    lines:3;
    text-overflow: ellipsis;
}
```

注意：

1. 需要用`text`标签，否则样式不起作用
2. `lines`设置行数
3. `text-overflow`设置溢出显示什么，ellipsis代表省略号

---


# 四、参考

1. [css多行文字溢出隐藏为三个点(...)_seiEight的博客-CSDN博客](https://blog.csdn.net/seiEight/article/details/90902172?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)
2. [nvue如何设置文本溢出显示省略号 - DCloud问答](https://ask.dcloud.net.cn/question/82877)
3. [综述 - uni-app官网](https://uniapp.dcloud.io/nvue-outline)
