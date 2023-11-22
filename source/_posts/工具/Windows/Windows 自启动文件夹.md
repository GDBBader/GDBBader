---


title: Windows 自启动文件夹
date: 2021-04-09 17:27:00
tags: [Windows,自启动]
type:

---


## 一、引言

如何在Windows系统启动的时候自启动某些软件?

## 二、解决

需要自启动的软件(或者快捷方式)可以放到如下文件夹中,Windows将会自动启动.

1. 当前用户的自启动

```
C:\Users\zps\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
```

2. 所有用户的自启动

```
C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp
```

可以在`运行`中使用`shell:startup``shell:commond startup`来快速打开两个文件夹.

> If you want to autostart a program for currently logged-on user please open the shell:startup
and if you want to start a program at Windows 10 startup please use (open) the all users startup folder shell:Common Startup



## 参考

1. [Auto Run a program when Windows-10 starts, how to?](https://www.softwareok.com/?seite=faq-Windows-10&faq=151)
