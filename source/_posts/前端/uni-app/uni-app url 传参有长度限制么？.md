---


title: uni-app url 传参有长度限制么？
date: 2021-04-10 22:54:16
tags: [uni-app,url,浏览器]
type:

---


# 答案是：有

> url有长度限制，太长的字符串会传递失败，可使用[窗体通信](https://uniapp.dcloud.io/collocation/frame/communication)、[全局变量](https://ask.dcloud.net.cn/article/35021)，或`encodeURIComponent`等多种方式解决，如下为`encodeURIComponent`示例。
...



# 限制有多长？

很长，几百K左右吧。


# 如何传递超过URL长度限制的参数


## 1.`encodeURIComponent`

```
<navigator :url="'/pages/test/test?item='+ encodeURIComponent(JSON.stringify(item))"></navigator>
```

```
// 在test.vue页面接受参数
onLoad: function (option) {
    const item = JSON.parse(decodeURIComponent(option.item));
}
```

_注意：用`encodeURIComponent`不能传输含有`%`的参数，[【报Bug】- DCloud问答](https://ask.dcloud.net.cn/question/109415)_


## 2.`eventChannel`


## 3.全局变量`globalData`

- 第一步：在App.vue中配置全局变量

```
<script>  
    export default {  
        globalData: {  
            text: 'text'  
        }
    }  
</script>
```

- 第二步：在页面中操作全局变量

   - js：`getApp().globalData.text = 'test'`
   - onLaunch时：getApp对象还未获取，暂时可以使用`this.$scope.globalData`获取globalData。


## 4.页面通信`uni.$emit(eventName,OBJECT)`


# 为啥`encodeURIComponent`过就能传输更长的参数了？

注意
不能传输含有`%`的参数[【报Bug】页面跳转uni.navigateTo 通过 encodeURIComponent(JSON.stringify()) 编码内容出现% 子页面解码时出错 - DCloud问答](https://ask.dcloud.net.cn/question/109415)

---


# 参考

1. [uni.navigateTo - uni-app官网](https://uniapp.dcloud.io/api/router?id=navigateto)
2. [App.vue - uni-app官网](https://uniapp.dcloud.io/collocation/App?id=globaldata)
3. [uni-app官网](https://uniapp.dcloud.io/use-weex?id=nvue-%e5%92%8c-vue-%e7%9b%b8%e4%ba%92%e9%80%9a%e8%ae%af)
4. [页面通讯 - uni-app官网](https://uniapp.dcloud.io/api/window/communication?id=emit)
5. [uni-app官网](https://uniapp.dcloud.io/api/router?id=event-channel)
