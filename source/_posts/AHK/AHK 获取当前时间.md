---


title: AHK 获取当前时间
date: 2021-03-30 23:42:36
tags: [AHK,脚本]
type:

---


# 一、引子

在使用Excel的时候需要用到一定的格式当前时间，比如
`2021-01-01 00:00:00`
，但是并没有找到好的方法，且用`AHK`


# 二、代码

```ahk
^3::
clipboard=%A_YYYY%-%A_MM%-%A_DD% %A_Hour%:%A_Min%:%A_Sec%
Send,^{v}
clipboard=
```


# 三、解析

- `^3::`代表注册`Ctrl-3`快捷键
- `clipboard=%A_YYYY%-%A_MM%-%A_DD% %A_Hour%:%A_Min%:%A_Sec%`将一定格式的时间保存至剪切板
- `Send,^{v}` 粘贴，输出
- `clipboard=`清空剪切板


# 四、后记

本来是参考[quantLearner](https://blog.csdn.net/The_Time_Runner)的文章[AutoHotKey||AHK||获取当前日期时间_漫步量化-CSDN博客](https://blog.csdn.net/The_Time_Runner/article/details/84317066)，但是使用过程中发现在输出时前几位还能正常输出，后面时分秒就有点输出错乱，因此作出如上改进。

---


# 五、参考

1. [AutoHotKey||AHK||获取当前日期时间_漫步量化-CSDN博客](https://blog.csdn.net/The_Time_Runner/article/details/84317066)
2. [如何用AutoHotkey自定义复制粘贴键-百度经验](https://jingyan.baidu.com/article/8275fc866c241946a03cf6d2.html)
