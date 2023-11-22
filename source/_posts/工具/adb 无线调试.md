---
title: adb 无线调试
date: 2022-09-18 22:02:24
tags: [adb,wifi]
---

## 一、前言
经常需要在手机上看书，但是觉得体验不如电脑上来得舒服，而网易蜗牛读书又还没有电脑版或网页版，因此使用adb来在电脑上显示手机屏幕内容。
但是电脑的有线，用来给手机充电太慢，因此使用adb wifi调用功能。
<!-- more -->
## 二、步骤
### 2.1 从手机上找到无线调试的IP地址与端口
一般在开发者选项中
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202209182326996.png)
### 2.2 adb连接
``` cmd
adb.exe connect 192.168.0.101:42303
```
### 2.3 启动scrcpy即可

## 参考
1. [通过wifi连接adb的三种方法_Saddyの云的博客-CSDN博客_wifiadb](https://blog.csdn.net/saddyyun/article/details/89029013)