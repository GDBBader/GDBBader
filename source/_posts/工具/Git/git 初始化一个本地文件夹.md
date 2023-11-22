---
title: git 初始化一个本地文件夹
date: 2021-06-06 20:39:59
tags:
  - git
type: 
updated: 2023-11-22 22:22:45
---


## 一、本地文件夹初始化
`git init ./`

## 二、配置email、user
2.1 先查看是否已经配置了email、user
```
$ git config -l
//如果看到有下面两条说明之前已经配置过emial、user
user.name=GDBBader          
user.email=1033239636@qq.com
```
2.2 配置email、user

<!--more-->
## 二、与远端仓库(gitee/github)建立联系

1. `git remote add 远端仓库地址`
2. `git push -u origin master`

### 解读

1. 第一条是跟远端仓库建立联系
当执行过第一条之后直接`git push`会报如下错误[[git push]]```
```
$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

git push --set-upstream origin master
```

2. 第二条是远端有很多分支,我们需要push到哪一个分支

## 三、如何配置email、user

## 流程
```flow
s=>start: 文件夹初始化
f1=>operation: 配置email、user
e=>end: 添加远端仓库

s(right)->f1(right)->e

```

## 参考

1. [git remote 命令 | 菜鸟教程](https://www.runoob.com/git/git-remote.html)
