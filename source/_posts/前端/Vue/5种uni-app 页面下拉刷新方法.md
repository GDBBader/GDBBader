---


title: 5种uni-app 页面下拉刷新方法
date: 2021-03-30 23:41:45
tags: [uni-app,vue.js]
type:

---


---



# 一、前言

最近需要在uni-app里使用下拉刷新,研究一下


# 二、vue页面下拉刷新

![](https://img-blog.csdnimg.cn/20210131231444665.gif#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

1. 步骤一:监听页面下拉刷新动作onPullDownRefresh

```javascript
//onLoad等生命周期函数同级
<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
        onPullDownRefresh() {
            console.log("我要刷新了");
            //此处写开始刷新的代码
        },
		onLoad() {

		},
		methods: {

		}
	}
</script>
```

2. 步骤二:开启页面下拉刷新功能enablePullDownRefresh  pages.json

```javascript
{
	"pages": [
		{
			"path": "pages/index/pull-down-refresh",
			"style": {
				"navigationBarTitleText": "pull-down-refresh",
                "enablePullDownRefresh":true
			}
		}
	],
	"globalStyle": {
	
	}
}
```

4. 步骤三:停止刷新动作

```javascript
//onLoad等生命周期函数同级
<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
        onPullDownRefresh() {
            console.log("我要刷新了");
            //此处写开始刷新的代码
            setTimeout(e=>{
                //此处写结束刷新的代码,写在setTimeout里是为了模拟刷新动作执行的时间
                console.log("刷新结束,我要停止刷新动作了");
                uni.stopPullDownRefresh()
                },2000)
            
        },
		onLoad() {

		},
		methods: {

		}
	}
</script>
```


# 三、 nvue页面下拉刷新


## 方法1：同vue页面同样配置,同样效果

![](https://img-blog.csdnimg.cn/20210131231501108.gif#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)


## 方法2：waterfall

使用`<refresh>`子组件：用于给列表添加下拉刷新的功能。

```javascript
<template>
    <waterfall column-count="2" column-width="auto">
        <refresh @refresh="onrefresh" @pullingdown="onpullingdown" :display="refreshing ? 'show' : 'hide'">
            <text>Refreshing ...</text>
            <!-- <loading-indicator></loading-indicator> -->
        </refresh>
        <cell v-for="num in lists">
            <text>{{num}}</text>
        </cell>
    </waterfall>
</template>
<script>
    export default {
        data() {
            return {
                refreshing:null,
                lists: ['A', 'B', 'C', 'D', 'E']
            }
        },
        methods:{
            onpullingdown:function(){
                console.log("下拉的动作");
                this.refreshing = true;//展示refresh元素
            },
            onrefresh:function(){
                console.log("松手触发刷新");
                setTimeout(e=>{
                    this.refreshing = false;//隐藏refresh元素
                },200)
            }
        }
    }
</script>

<style></style>
```


## 方法3：list

使用`<refresh>`子组件：用于给列表添加下拉刷新的功能。

```javascript
<template>
    <list>
        <refresh @refresh="onrefresh" @pullingdown="onpullingdown" :display="refreshing ? 'show' : 'hide'">
            <text>Refreshing ...</text>
            <!-- <loading-indicator></loading-indicator> -->
        </refresh>
        <cell>a</cell>
        <cell>b</cell>
        <cell>c</cell>
    </list>
</template>

<script>
	export default {
		data() {
			return {
				refreshing:null,
			}
		},
		methods: {
			onpullingdown:function(){
			    console.log("下拉的动作");
			    this.refreshing = true;//展示refresh元素
			},
			onrefresh:function(){
			    console.log("松手触发刷新");
			    setTimeout(e=>{
			        this.refreshing = false;//隐藏refresh元素
			    },200)
			}
		}
	}
</script>

<style>

</style>
```


# 四、还有一种方式,看文档不推荐使用,如有需要可前往下方链接查看

[scroll-view - uni-app官网](https://uniapp.dcloud.io/component/scroll-view?id=scroll-view)


# 五、示例源码

Talk is cheap. Show me the code：
[5种uni-app 页面下拉刷新方法-源码示例.zip](https://download.csdn.net/download/qq_31646657/14978638)


# 六、参考文章

1. [下拉刷新](https://uniapp.dcloud.io/api/ui/pulldown)
2. [waterfall子组件refresh](https://uniapp.dcloud.io/component/waterfall?id=%e5%ad%90%e7%bb%84%e4%bb%b6)
3. [refresh - uni-app官网](https://uniapp.dcloud.io/component/refresh?id=refresh)
4. [list子组件refresh](https://uniapp.dcloud.io/component/list?id=list)
5. [scroll-view - uni-app官网](https://uniapp.dcloud.io/component/scroll-view?id=scroll-view)
