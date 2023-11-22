---

title: Git 如何调整 commit 的顺序
date: 2022-12-02 23:11
tags: [git]

---
## 〇、问题
1. 使用哪条命令调整commit的顺序？
> git rebase -i


## 一、前言
今天测试了git hooks，产生了大量的commit，而后又进行了正常的commit，因此在这里是想要调整一个commit的顺序然后再删除掉测试commit。

在找解决方案的时候其时发现不用先调整顺序，直接通过交互式git rebase就可以直接删除某些commit。

<!-- more -->

## 二、步骤
### 2.1 进入交互式git rebase
```
# 操作18个commit
git rebase -i HEAD~18
```
### 2.2 直接删除不需要的commit即可
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202212022344223.png)
### 2.3 继续完成git rebase即可
执行完2.3步骤后并没有完成git rebase而是进入了一步步执行的操作，可通过以下命令继续rebase命令的后续步骤：
```
git rebase --continue
```

## 参考
1. [Git - git-rebase Documentation](https://git-scm.com/docs/git-rebase)