---

title: AHK 如何向剪切板中保存多行文本
date: 2023-03-09 22:09
tags: [AHK]

---


## 一、如何访问剪切板
使用内建变量：clipboard
```ahk
; 赋值
clipboard := "abc"
```

## 二、多行文本的语法
```ahk
clipboard := "
(abc
def
)"
```

## 参考
1. [Clipboard / ClipboardAll - Definition & Usage | AutoHotkey](https://www.autohotkey.com/docs/v1/misc/Clipboard.htm)
2. [多行文本（延续片段）（continuation section） · AHK常用代码片段集锦 · 看云 (kancloud.cn)](https://www.kancloud.cn/qq313899179/ahk_code/713501)
3. [脚本 - 定义 & 使用 | AutoHotkey v2 (wyagd001.github.io)](https://wyagd001.github.io/v2/docs/Scripts.htm#continuation-section)