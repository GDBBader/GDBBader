---

title: 一键将Web页面保存至Anki
date: 2022-12-02 21:38
tags: [Anki,Anki-Connect,油猴]

---

## 一、前言
发布完博客后会添加至Anki协助自己强化记忆，但是一次次的重复动作让我觉得厌烦，因此有了写这个脚本的想法：在Web页面添加一个按钮，用来触发向Anki添加卡片的动作。该脚本发布在[Anki-Connect-addNotes](https://greasyfork.org/zh-CN/scripts/455865-anki-connect-addnotes) 可通过油猴安装。

<!-- more -->

## 二、步骤
### 2.1 通过调用Anki-Connect插件来向Anki添加卡片
```js
function addNotes(){
	// mdUrl就是添加至Anki的文本
	var mdUrl = ['<a href="',document.URL,'">',document.title,'</a>'].join("");
	// 调用Anki-Connect的接口所需的参数
	var data = JSON.stringify({
		"action": "addNotes",
		"version": 6,
		"params": {
			"notes": [
				{
					"deckName": "Default",
					"modelName": "Basic",
					"fields": {
						"Front": mdUrl
					},
					"tags": []
				}
			]
		}
	});
	// 使用GM_xmlhttpRequest是为了解决跨域问题
	GM_xmlhttpRequest({
		method: "post",
		// 本机的8765接口是anki-connect的默认端口
		url: 'http://127.0.0.1:8765',
		data: data,
		headers: { "Content-Type":"application/json" },
		onload: function(r) {
			console.log("添加至Anki成功！",r);
		}
	});
}
```
### 2.2 向页面注入一个功能按钮，并绑定功能
```js
function addButton(){
	let Container = document.createElement('div');
	Container.id = "add-notes-container";
	Container.style.position="fixed"
	Container.style.left="0"
	Container.style.top="0"
	Container.style['z-index']="999999"
	Container.innerHTML =`<button id="addNotes" style="position:absolute; left:30px; top:20px">
Add2Anki
</button>
`

	document.body.appendChild(Container);

	let button = document.getElementById("addNotes");
	button.onclick=addNotes;
}
```


## 参考
1. [Anki-Connect-addNotes](https://greasyfork.org/zh-CN/scripts/455865-anki-connect-addnotes)
2. [GitHub - FooSoft/anki-connect: Anki plugin to expose a remote API for creating flash cards.](https://github.com/FooSoft/anki-connect)