---


title: 在windows上使用nginx部署vue-cli项目
date: 2021-07-22 13:55:36
tags: [nginx,vue-cli,vue,windows,]
type:

---


## 一、引言

vue-cli项目，想不想部署至iis上，但一直报权限问题，现通过nginx部署。

## 二、步骤

1. 通过vue-cli build项目
2. 将dist下的文件复制到nginx安装目录下的html文件夹
3. 启动nginx
4. 访问
默认是http://localhost:80,可通过nginx安装目录下的conf/nginx.conf配置端口等信息。


## 参考

1. [windows下nginx的安装和vue项目的部署_风如也的博客-CSDN博客](https://blog.csdn.net/qq_38157825/article/details/108662073)
