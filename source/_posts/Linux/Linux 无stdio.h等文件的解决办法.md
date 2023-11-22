---

title: Linux 无stdio.h等文件的解决办法
date: 2021-03-21 21:22:29
tags: [Linux,编译]
type:
---

## 一、引言

安装好Mint Linux后，使用gcc来编译.c文件，却发现各自.h文件缺失，在此记一下解决办法。

## 二、解决方案

安装`build-essential`包即可。


## 参考

1. [【linux】error: stdio.h: No such file or directory_郭老二-CSDN博客](https://blog.csdn.net/u010168781/article/details/78589242)
2. [build-essential软件包简介 | darkmi's blog](http://blog.darkmi.com/2015/04/06/2738.html)
