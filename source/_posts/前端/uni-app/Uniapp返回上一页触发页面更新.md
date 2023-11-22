---


title: Uniapp返回上一页触发页面更新
date: 2021-03-30 23:37:42
tags: [uni-app,watch]
type:

---


## 一、引言

## 二、解决方案


## 参考

1. 

---


# 前言

本来返回上一页可以使用[uni.navigateBack(OBJECT)](https://uniapp.dcloud.io/api/router?id=navigateback),但是这个无法触发页面更新,另外可以选用[uni.reLaunch(OBJECT)](https://uniapp.dcloud.io/api/router?id=relaunch),但是会丢失页面栈,无法继续返回上上页.因此利用[uni.navigateBack(OBJECT)](https://uniapp.dcloud.io/api/router?id=navigateback)+传参触发页面更新函数的方式来实现.


---

提示：以下是本篇文章正文内容，下面案例可供参考


# 一、难点有哪些？

1. 如何返回上一页
2. 如何触发上一页的更新


# 二、返回上一页

代码如下：

```javascript
//click事件函数
gotoPre:function(){
    uni.navigateBack()//返回上一页
}
```


# 三、触发上一页的更新

代码如下：

```javascript
//click事件函数
gotoPre:function(){
    let pages = getCurrentPages()//页面栈
    let prePage = pages[pages.length - 2]//上一页
    prePage.$vm.reFresh = Math.random()//触发上一页监听器
    
    uni.navigateBack()//返回上一页
}
```


# 四、监听reFresh

```javascript
data() {
	return {
        reFresh:""
	}
},
watch:{
    //监听reFresh,如果有修改就执行监听器
    reFresh:function(){
        //初始化参数
        this.num = 0
        //刷新页面(即onLoad里的某些操作
        this.num = "110"
        console.log("页面已重新加载");
    }
},
```

---


# 五、示例源码

Talk is cheap. Show me the code：

[点击下载示例源码](https://download.csdn.net/download/qq_31646657/13657180)


# 总结

其实实际用的比这个要稍微复杂点,是需要返回上一页并刷新上一页里某个组件内的数据.
不过思路是一致的,简单说来就是返回上一页之后触发"触发组件内监听器"的监听器.
