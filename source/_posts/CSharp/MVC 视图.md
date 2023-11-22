---


title: MVC 视图
date: 2021-05-20 00:14:02
tags: [C#,MVC,Razor]
type:

---


# 视图是个啥？

- 视图就是表现数据的地方
- 就是展示出来的网页


# 使用 [Razor 视图引擎](https://docs.microsoft.com/zh-cn/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)

> 使用 [Razor 视图引擎](https://docs.microsoft.com/zh-cn/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)可以创建视图模板文件。 基于 Razor 的视图模板的文件扩展名为 _cshtml_。



# [[MVC 控制器|控制器]]与视图的交互

- 
通过`ViewBag`对象来传递数据。
```
//GET: /HelloWorld/Welcome/
public ActionResult Welcome(string name,int numTimes = 1)
{
    ViewBag.Message = "Hello " + name;
    ViewBag.NumTimes = numTimes;

    return View();

}
```

> 控制器负责提供所需的任何数据或对象，以便视图模板呈现对浏览器的响应。 最佳做法： **视图模板不应执行业务逻辑或直接与数据库交互**。 相反，视图模板应仅适用于控制器为其提供的数据。



- 
使用视图模型将数据从控制器传递给视图。


---


# 参考

1. [使用 Razor 语法的 ASP.NET Web 编程简介（C#） | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)
2. [将视图添加到 MVC 应用 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/mvc/overview/getting-started/introduction/adding-a-view)
