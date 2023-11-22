---


title: 记忆强化之shell按行输出文本
date: 2021-08-31 14:11:31
tags: [shell,脚本,记忆,]
type:

---


## 一、引言

放置在桌面上，轮播效果可以用来强化记忆。
高级操作：

1. 可输出中携带网络地址，从命令行跳转到博客（cmder可以，git-bash不行）

## 二、方案

```
cat "fileName"|while read line 
do
    echo "$line"
    sleep 1
done
```


## 三、待优化

1. 通过参数指定文件名(已优化)

```shell
cat $1|while read line 
do
    echo "$line"
    sleep $2
done
```

3. 支持指定文件夹
4. 支持轮播间隔


## 后记

感觉这个东西用处也不是那么大，就是一个让摸鱼变得有些许意义的小工具。但是完全就可能不摸鱼。“人如果没有理想，那跟咸鱼又有什么分别。”要有理想，不要闲着摸鱼。


## 参考

1. [shell wait 和sleep 对比_妙妙的博客-CSDN博客_shell 等待](https://blog.csdn.net/qq_31382921/article/details/79817072)
2. [Shell 流程控制 | 菜鸟教程](https://www.runoob.com/linux/linux-shell-process-control.html)
3. [shell:读取文件的每一行内容并输出 - cbwcwy - 博客园](https://www.cnblogs.com/iloveyoucc/archive/2012/07/10/2585529.html)
4. [Shell 传递参数 | 菜鸟教程](https://www.runoob.com/linux/linux-shell-passing-arguments.html)
