---

title: Windows 如何查看端口是否开启
date: 2022-11-22 16:45
tags: [netstat,findstr]

---
## 〇、问题
1. 使用哪条命令？
netstat -aon | findstr 8080

## 一、前言
今天在启动应用的时候显示端口占用，但是不知道被哪个应用占用了，在此记录一下如何查看端口的占用情况。

<!-- more -->

二、命令
`netstat -aon | findstr 8080`
### 2.1 netstat
netstat用于显示TCP连接、端口等网络信息。

-a 显示所有活动的TCP连接，以及正在监听的[[TCP]]和[[UDP]]端口
-o 显示对应的[[进程]]ID。
-n 以数字的显示活动的地址和端口。
### 2.2 findstr
findstr用于在文件中搜索文本模式。

## 参考
1. [netstat | Microsoft Learn](https://learn.microsoft.com/zh-cn/windows-server/administration/windows-commands/netstat)
2. [findstr | Microsoft Learn](https://learn.microsoft.com/zh-cn/windows-server/administration/windows-commands/findstr)