---


title: CS 硬编码是什么意思？
date: 2021-08-11 14:15:33
tags: [C#,视图,硬编码]
type:

---


## 问题

```cs
public string Index() 
{ 
    return "Hello World!"; 
}
```
当前，`Index` 方法返回带有在控制器类中硬编码的消息的字符串。 更改 `Index` 方法以调用控制器 [视图](https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.aspnetcore.mvc.controller.view#Microsoft_AspNetCore_Mvc_Controller_View) 方法，如以下代码所示：

```cs
public ActionResult Index() 
{ 
    return View(); 
}
```


## 理解

硬编码就是会被编码出来，如果需要更改就需要重新编译。

---


## 参考

1. [将视图添加到 MVC 应用 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/mvc/overview/getting-started/introduction/adding-a-view)
2. [c# - 硬编码是什么意思？ - IT工具网](https://www.coder.work/article/3058663)
