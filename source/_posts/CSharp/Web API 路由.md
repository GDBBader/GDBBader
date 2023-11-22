---


title: Web API 路由
date: 2021-04-13 15:48:25
tags: [Web API,C#,路由]
type:

---


## 一、什么是路由？

在计算机网络里，路由就是

> 路由（routing）就是通过互联的网络把信息从源地址传输到目的地址的活动。


在Web API中意思也类似，就是将网络请求传输给控制器的活动。

> 路由是 Web API 将 URI 与操作匹配的方式。


## 二、什么是控制器？

> 在 ASP.NET Web API 中， 控制器 是处理 HTTP 请求的类。



## 三、Web API路由模板

在`APP_Start`文件夹下`WebApiConfig.cs`文件中。

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web.Http;

namespace ProductsAPP
{
    public static class WebApiConfig
    {
        public static void Register(HttpConfiguration config)
        {
            // Web API 配置和服务

            // Web API 路由
            config.MapHttpAttributeRoutes();

            config.Routes.MapHttpRoute(
                name: "DefaultApi",
                routeTemplate: "api/{controller}/{id}",
                defaults: new { id = RouteParameter.Optional }
            );
        }
    }
}
```


## 四、Web API路由选择操作的几种方式


### 1. 通过匹配操作的谓词前缀来选择操作

假设现已匹配到路由，有控制器代码如下(以下例子来自[ASP.NET Web API 中的路由 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api))：

```cs
public class ProductsController : ApiController
{
    public IEnumerable<Product> GetAllProducts() { }
    public Product GetProductById(int id) { }
    public HttpResponseMessage DeleteProduct(int id){ }
}
```

下面是一些可能的 HTTP 请求，以及为每个请求调用的操作：

| HTTP 谓词 | URI 路径 | 操作 | 参数 |
| --- | --- | --- | --- |
| GET | api/Products | GetAllProducts | _ 无 () _ |
| GET | api/Products/4 | GetProductById | 4 |
| DELETE | api/Products/4 | DeleteProduct | 4 |
| POST | api/Products | _ 不 (匹配) _ |  |


请注意，URI 的 {id} 段（如果存在）映射到操作的 id 参数。 在此示例中，控制器定义了两个 GET 方法，一个带有 id 参数，另一个不包含参数。
另请注意，POST 请求将失败，因为控制器不定义 " POST ... " 方法。


### 2. 通过显式的指定操作的谓词来选择操作

上面的前缀方式是Web API的基本路由机制，还可以通过特性显式地指定谓词。

```cs
public class ProductsController : ApiController
{
    [HttpGet]
    public Product FindProduct(id) {}
}
```


### 3. 通过操作名称来选择操作

当通过路由规则能找到多个操作时，以上两种方式不被允许，请求接口后会报如下错误

```xml
<Error>
<Message>出现错误。</Message>
<ExceptionMessage>找到了与该请求匹配的多个操作: 类型 ProductsAPP.Controllers.ProductsController 的 Get1 类型 ProductsAPP.Controllers.ProductsController 的 Get2</ExceptionMessage>
<ExceptionType>System.InvalidOperationException</ExceptionType>
<StackTrace> 在 System.Web.Http.Controllers.ApiControllerActionSelector.ActionSelectorCacheItem.SelectAction(HttpControllerContext controllerContext) 在 System.Web.Http.Controllers.ApiControllerActionSelector.SelectAction(HttpControllerContext controllerContext) 在 System.Web.Http.ApiController.ExecuteAsync(HttpControllerContext controllerContext, CancellationToken cancellationToken) 在 System.Web.Http.Dispatcher.HttpControllerDispatcher.<SendAsync>d__15.MoveNext()</StackTrace>
</Error>
```

此时可通过指定操作名称的方式来选择操作


#### a. 配置路由模板

```cs
routes.MapHttpRoute(
    name: "ActionApi",
    routeTemplate: "api/{controller}/{action}/{id}",
    defaults: new { id = RouteParameter.Optional }
);
```


#### b. 调用时指定操作名称即可


### 4. 特性路由（属性路由）


#### a.

> 将 RoutePrefix 属性添加到控制器。 此属性定义此控制器上所有方法的初始 URI 段。


```cs
[RoutePrefix("api/products")]
public class ProductsController : ApiController
{
    // ...
```


#### b.

> 然后将 [Route] 特性添加到控制器操作，如下所示：


```cs
[Route("Get1111/{id:int}")]
    public string Get1(int id)
    {
        // ...
```


#### c.

`http://localhost/api/products/Get1111/1`

理解:感觉就是将路由配置信息从`WebApiConfig.cs`中给拿了出来，使用更加灵活。


## 五、路由的主要阶段

- 匹配路由模板的 URI。
- 选择控制器。
- 选择操作。


## 参考

1. [ASP.NET Web API 中的路由 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api)
2. [路由 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E8%B7%AF%E7%94%B1)
3. [ASP.NET Web API 中的路由和操作选择 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
4. [C# 特性（Attribute） | 菜鸟教程](https://www.runoob.com/csharp/csharp-attribute.html)
5. [ASP.NET Web API 2 中的属性路由 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
6. [使用 ASP.NET Web API 2 中的属性路由创建 REST API | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-api/overview/web-api-routing-and-actions/create-a-rest-api-with-attribute-routing)
