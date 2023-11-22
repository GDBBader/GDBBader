---

title: Shell 批量创建文件夹
date: 2022-10-22 09:29
tags: [shell]

---
## 〇、问题
1. 使用哪条命创建文件夹
2. 如何读取文件
3. shell循环的语法是什么

## 一、前言
写这么一个脚本放到闲鱼上去，有人会用得到的。

<!-- more -->

## 二、步骤
### 2.1 创建一个保存着文件夹名称的txt文件
```txt
//Folders.txt
文件夹1
文件夹2
文件夹3
```

### 2.2 读取文件for循环输出
```bash
//Run.sh
folders=`cat ./Folders.txt`
for folder in $folders
do
    name=`echo ${folder} | tr -d '\r'| tr -d '\n'`
    echo ../${name}
done
read end
```
其中，`| tr -d '\r'| tr -d '\n'`是为了去除换行。

### 2.3 创建文件夹
```bash
//Run.sh
folders=`cat ./Folders.txt`
for folder in $folders
do
    name=`echo ${folder} | tr -d '\r'| tr -d '\n'`
    mkdir ../${name}
done
read end
```
## 参考
1. [Shell for循环和for int循环详解](http://c.biancheng.net/view/2804.html)