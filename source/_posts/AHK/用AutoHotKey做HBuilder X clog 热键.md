---

title: 用AutoHotKey做HBuilder X clog 热键
date: 2021-03-17 10:11:33
tags: [AutoHotKey,HBuilder X]
---

## 一、上代码

```ahk
:*:clog::console.log("");
return
```


## 二、解释

- `::clog::console.log("");`代表当输入`clog`后再按空格或者确认时就自动输出`console.log("");`
- `:*:clog::console.log("");`代表当输入`clog`时就直接输出`console.log("");`


## 三、 待改进

1. 输出后能直接地位到引号内部
2. 仅在HX中才触发


## 参考

1. [热字串 - 定义与使用 | AutoHotkey](https://wyagd001.github.io/zh-cn/docs/Hotstrings.htm)
