---

title: git branch
date: 2021-06-06 20:38:12
tags: [git,branch]
type:

---


## 一、`git branch` 列出本地分支

```
$ git branch
* master
```

<--more-->


## 二、`git branch -a` 查看全部分支


## 三、`git branch -r` 查看远端分支


## 四、如何查看当前分支对应的远端分支是啥?

使用`git status`时即会提示当前本地所在分支所对应的远端分支是哪个

```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
```


## 五、把远端的分支拉到本地（并切换过去）

```
$ git checkout -b 本地分支名 origin/分支名
```
