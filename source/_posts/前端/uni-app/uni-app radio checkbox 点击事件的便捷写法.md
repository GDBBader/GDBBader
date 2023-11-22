---


title: uni-app radio checkbox 点击事件的便捷写法
date: 2021-08-31 17:27:27
tags: [uni-app,事件]
type:

---


## 一、引言

遇到一个写radio点击事件的便捷写法，记录一下。

## 二、源码

```
<view class="remember-psw">
	<checkbox-group>
		<label><checkbox value="psw" :checked='rememberPsw' @tap="rememberPsw =! rememberPsw" color="#09CC86"/>记住账号密码</label>
	</checkbox-group>
</view>
```


## 参考

1. [利用uni-app实现记住账号密码的功能_CherryLee_1210的博客-CSDN博客](https://blog.csdn.net/CherryLee_1210/article/details/86716326)
