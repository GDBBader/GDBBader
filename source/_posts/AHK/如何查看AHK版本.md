---

title: 如何查看AHK版本
date: 2023-03-09 22:19
tags: [AHK]

---

问：AHK有多个版本，例如1.1与2.0，但是从哪里查看呢？
答：有专门的内建变量：a_ahkversion
```ahk
msgbox, % a_ahkversion
```

## 参考
1. [Variables and Expressions - Definition & Usage | AutoHotkey v2](https://www.autohotkey.com/docs/v2/Variables.htm#AhkVersion)