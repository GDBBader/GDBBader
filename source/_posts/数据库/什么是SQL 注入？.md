---

title: 什么是SQL 注入？
date: 2021-08-09 18:38:10
tags: [SQL,安全,数据库]
type:

---

# 一、什么是SQL 注入？


## （一）、理解

程序根据用户输入的某些内容来与数据库交互，数据库把用户输入当成了SQL语句。

> 简而言之，是在输入的字符串之中注入SQL指令，在设计不良的程序当中忽略了字符检查，那么这些注入进去的恶意指令就会被数据库服务器误认为是正常的SQL指令而运行，因此遭到破坏或是入侵。


---


# 二、参考

1. [SQLite 注入 | 菜鸟教程](https://www.runoob.com/sqlite/sqlite-injection.html)
2. [SQL注入 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/SQL%E6%B3%A8%E5%85%A5)
