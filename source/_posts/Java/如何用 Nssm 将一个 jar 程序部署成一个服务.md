---

title: 如何用 Nssm 将一个 jar 程序部署成一个服务
date: 2022-10-19 22:30
tags: [Nssm,Java,Maven]

---

## 〇、问题
1. 如何运行一个jar程序
2. nssm如何部署服务

## 一、前言
在IDEA中用Java写了一个Rest Api项目（是用Maven）管理的，现在记录一个如何通过Nssm将其部署成一个服务。

<!-- more -->

## 二、步骤
### 2.1 在IDEA中通过Maven将程序打包成一个jar包
1. maven clean
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210192241322.png)
3. maven package
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210192242782.png)
执行完毕以后会在target文件夹下生成一些文件，其他包括一个jar文件：
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210192244103.png)
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210192245715.png)
### 2.2 通过java.exe将jar包运行起来
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210192246074.png)
### 2.3 通过nssm将其部署成一个服务
上一步只是为了验证程序是否可以正常启动，以下将通过nssm将其部署成一个服务
1. `nssm install`命令打开nssm服务安装界面
2. 安装服务
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210192309708.png)
3. 启动服务
`nssm.exe start 8080api`

## 参考
1. [NSSM - the Non-Sucking Service Manager](https://nssm.cc/usage)