---

title: DevTools中copy() 的作用
date: 2022-06-22 14:17
tags: [JavaScript]

---
## 一、前言

现有一个edge浏览器，如何将某接口返回的data值保存到系统剪切板中？

## 二、获取接口返回的data

```js
await ( await fetch(
'https://api.github.com/repos/microsoft/vscode-edge-devtools/issues?state=all&per_page=50&page=1'
)).json();
```

## 三、将某一值通过命令行保存到剪切板

```js
copy((()=>{return 123})())

copy(await ( await fetch(
'https://api.github.com/repos/microsoft/vscode-edge-devtools/issues?state=all&per_page=50&page=1'
)).json())
```
  

## 参考

1.  [在控制台中运行 JavaScript - Microsoft Edge Development | Microsoft Docs](https://docs.microsoft.com/zh-cn/microsoft-edge/devtools-guide-chromium/console/console-javascript)