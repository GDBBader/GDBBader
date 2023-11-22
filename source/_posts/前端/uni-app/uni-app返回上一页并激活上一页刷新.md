---


title: uni-app返回上一页并激活上一页刷新
date: 2021-04-10 22:48:24
tags: [uni-app,页面通信,触发器,组件]
type:

---


# 思路

当前页：C
上一页：P

返回上一页P，修改P页中的变量reFresh，监视器reFresh用来刷新页面。


# 更近一步：如何返回上一页并激活组件内的刷新

当前页：C
上一页：P 	组件:T

返回上一页P，修改P页中的变量reFresh，监视器reFresh用来修改组件T中的reFresh prop，T中的监视器reFresh用来更新页面。


# 返回并修改P页面的变量reFresh

```
let pages = getCurrentPages(); //页面栈

let prevPage = pages[pages.length - 2] //上一个页面 // （pages.length - 3 上上页 pages.length - 1当前页，以此类推）

prevPage.$vm.reFresh = Math.random() // 给上一页面的reFresh赋值，触发触发器

uni.navigateBack();
```


# P页面触发器

```
...在组件内新建reFresh prop
<swiper-page class="swiper-page" :reFresh="subReFresh" :pid="page.pageid" :parentId="pageId" ref="page"></swiper-page>
...


...
data() {
	return {
		...
		reFresh: "" ,//修改触发刷新
        subReFresh:"",//修改触发组件内刷新
		...
	}
},
...
watch:{
    reFresh:function(){
        this.subReFresh = Math.random();//修改组件内prop reFresh
        console.log("reFresh已修改");
    }
},
...
```


# T组件内触发器

```
...
props: {
	...
    reFresh:{
        type:Number,
        default:''
    }
	...
},
data() {
	return {
		...
	}
},
...
watch:{
    reFresh:function(){
        console.log("我是组件，我要重新加载");
    }
},
...
```

---


# 参考

1. [Uniapp返回上一页触发页面更新_qiebzps的博客-CSDN博客](https://blog.csdn.net/qq_31646657/article/details/111053707)
