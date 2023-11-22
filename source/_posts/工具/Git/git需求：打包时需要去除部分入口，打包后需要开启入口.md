---

title: git需求：打包时需要去除部分入口，打包后需要开启入口
date: 2021-08-12 23:57:56
tags: [git,shell]
type:

---


## 一、引言

现状：同一套代码，需要打包ios端、安卓端，两端的部分功能与入口有所不同，主要是入口的显隐。因此在打包时需要改动部分代码。
需求：在将来会有回溯到某个版本查找bug的需要，因此需要在commit中留下痕迹

## 二、解决

1. 将需要隐去的功能隐去
2. commit
3. revert
4. 及时上传即可

实现为shell脚本gr.sh如下：

```
git commit -m $1

git revert HEAD --no-edit
```


## 三、运行

- 方法1. 在git bash中直接运行即可。
- 方法2. 将gr.sh所在的文件夹添加到环境变量PATH中然后在git bash中就可以随时此`gr.sh some_words`的方式运行此脚本。


## 参考

1. [Reset、Revert 跟 Rebase 指令有什麼差別？ - 為你自己學 Git | 高見龍](https://gitbook.tw/chapters/rewrite-history/reset-revert-and-rebase.html)
2. [Shell 传递参数 | 菜鸟教程](https://www.runoob.com/linux/linux-shell-passing-arguments.html)
