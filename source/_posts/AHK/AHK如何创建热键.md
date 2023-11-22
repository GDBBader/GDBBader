---


title: AHK如何创建热键
date: 2021-06-06 21:09:05
tags: [AHK,效率]
type:

---


# 一、如何创建热键

热键是通过一对 :: 创建的. 按键名或组合按键名必须在 :: 左边. 代码则跟在下面, 然后以 Return 结束.

```ahk
^j::
   Send, My First Script
Return
```
