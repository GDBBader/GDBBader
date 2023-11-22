---


title: IIS 网站部署问题汇总
date: 2021-08-24 09:22
tags: [IIS,Windows,.NET]
type:

---


## 确定程序运行CLR

.NET Framework 与CLR时两码事，但CLR的版本可以根据.NET Framework的版本来确定。

> .NET Framework 是管理面向 .NET Framework 的应用的运行时执行环境。 它包括公共语言运行时（提供内存管理和其他系统服务）和一个全面的类库（使程序员能利用强大可靠的代码实现所有主要领域的应用开发）。


> .NET 框架是由微软开发的软件开发平台，其最主要的两个组成部分是公共语言运行时 (CLR) 和框架类库 (FCL)，基础类库 (BCL)是框架类库的一个子集。


.NET Framework

- CLR
- 类库

![[Pasted image 20210824094716.png]]


## 确定管道托管模式

- 问题：axd资源报404
- 解决：iis-> 应用程序池-> 基本设置-> 托管管道模式-> 经典
- 集成
- 经典


## 启动32位应用程序

- 
问题：未能加载文件或程序集*或它的某一个依赖项。试图加载格式不正确的程序。
![[Pasted image 20210824135452.png]]

- 
原因：64位系统，可能引用了32位的dll

- 
解决：iis-> 应用程序池-> 高级设置-> 启动32位应用程序
![[Pasted image 20210824140104.png]]



## HTTP 错误 401.3 - Unauthorized

- 问题：由于 Web 服务器上此资源的访问控制列表(ACL)配置或加密设置，您无权查看此目录或页面。
- 方法1：

![[Pasted image 20210824140639.png]]

- 方法2:

![[Pasted image 20210824141104.png]]


## HTTP 錯誤 500.19 - Internal Server Error

-问题：無法存取要求的網頁，因為與該網頁相關的設定資料不正確。
![[Pasted image 20210824143303.png]]

- 原因：![[Pasted image 20210824143611.png]]
- 解决：参考“HTTP 错误 401.3 - Unauthorized”


## 参考

1. [.NET Framework 入门 | Microsoft Docs](https://docs.microsoft.com/zh-cn/dotnet/framework/get-started/)
2. [.NET框架简介](http://c.biancheng.net/view/3047.html)
3. [ .net framework、C#、CLR、Visual Studio的对应关系。_高级项目经理、专注于技术架构、分享项目管理及职场心得-CSDN博客](https://blog.csdn.net/u011872945/article/details/72897183)
4. [IIS 之 托管管道模式 - Now,DayBreak - 博客园](https://www.cnblogs.com/xinaixia/p/4462385.html)
5. [一点点对WebResource.axd的配置及使用[转] - liuyz2006 - BlogJava](http://www.blogjava.net/liuyz2006/articles/383263.html)
6. [互联网信息服务 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E7%B6%B2%E9%9A%9B%E7%B6%B2%E8%B7%AF%E8%B3%87%E8%A8%8A%E6%9C%8D%E5%8B%99)
7. [未能加载文件或程序集“XXXXXX”或它的某一个依赖项。试图加载格式不正确的程序。 - 寒枫 - 博客园](https://www.cnblogs.com/autumn/p/3575008.html)
