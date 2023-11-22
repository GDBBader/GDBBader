---


title: MVC 控制器
date: 2021-05-20 00:23:26
tags: [MVC,CS,控制器]
type:

---


# 什么是控制器

控制器是一个类。

- 类名就是路由。类中的方法名就是下一级路由。
![](https://gitee.com/qiebzps/pic/raw/master/img/20210520002141.png#alt=)
- 返回值即做为网页的内容。此一般返回一个[[MVC 视图]]，也可以指定返回类型。
![](https://gitee.com/qiebzps/pic/raw/master/img/20210520002152.png#alt=)


# 两种通过URL传递参数的方法

- `?`
[http://localhost](http://localhost):xxxx/HelloWorld/Welcome?name=Scott&numtimes=4

> [ASP.NET MVC 模型绑定系统](http://odetocode.com/Blogs/scott/archive/2009/04/27/6-tips-for-asp-net-mvc-model-binding.aspx)自动将命名参数从地址栏中的查询字符串映射到方法中的参数。


```c
// GET: /HelloWorld/Welcome/
public string Welcome(string name,int numTimes = 1)
{
    //return "This is my Welcome action method ...";
    return HttpUtility.HtmlEncode("Hello" + name + ", NumTimes is:" + numTimes);
}
```

- `/`
![](https://gitee.com/qiebzps/pic/raw/master/img/20210520002207.png#alt=)

---


# 参考

1. [添加控制器 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/mvc/overview/getting-started/introduction/adding-a-controller)
