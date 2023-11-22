---


title: uni-app navigator 无法跳转
date: 2021-04-10 22:57:15
tags: [uni-app,bug,跳转]
type:

---


# 现象

`<navigator url="../add/add" class="fab-circle">记</navigator>`这么一句,就是跳转不过去.


# 原因

只新建了`add.vue`页面，但是在`page.json`中没有增加相关的配置。

配置如下：

```
//page.json
{
	"pages": [
	***其他配置
	{
		"path": "pages/add/add",
		"style": {
			"navigationBarTitleText": "记一笔"
		}
	}
	***其他配置
	]
}
```
