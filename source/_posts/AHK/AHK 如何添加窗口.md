---


title: AHK 如何添加窗口
date: 2021-03-30 23:43:11
tags: [AHK,GUI]
type:

---


# 一、引子

写了两个热键脚本后觉得，如果脚本比较多，在将来定是难以管理，就想着如何把平时常用的脚本合并到一起，增加一个窗口，通过按键调用窗口，继而通过鼠标或键盘选择
相应的功能。


# 二、增加窗口（菜单）

```ahk
; 添加一些菜单项来创建弹出菜单.
Menu, MyMenu, Add, 欢迎使用psTools, fWelcome
Menu, MyMenu, Add  ; 添加分隔线.

Menu, MyMenu, Add, 1 ps-todo, fPSTodo
Menu, MyMenu, Add, 3 Now, fNow
Menu, MyMenu, Add  ; 添加分隔线.
```


# 三、添加相应子程序

```ahk
 fWelcome:
 	MsgBox,"Welcome"
 return
 
 fNow:
 	clipboard=%A_YYYY%-%A_MM%-%A_DD% %A_Hour%:%A_Min%:%A_Sec%
 	Send,^{v}
 	clipboard=
 return
 
 fPSTodo:
 	clipboard=
 		(
 		ps-todo %A_YYYY%-%A_MM%-%A_DD%
 		)
 	Send,^{v}
 	clipboard=
 return
```


# 四、Alt-`调用菜单

```ahk
!`::Menu, MyMenu, Show  ; 即按下 Alt-` 热键来显示菜单.
```

---


# 参考

1. [Menu | AutoHotkey](https://wyagd001.github.io/zh-cn/docs/commands/Menu.htm#ExPopup)
