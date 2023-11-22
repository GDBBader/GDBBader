---


title: WebAPI 中控制器操作如何拿到URI中的参数？
date: 2021-08-18 09:35:38
tags: [WebAPI,控制器,URI,路由]
type:

---


## 一、路由配置与控制器代码如下

WebApiConfig.cs

```c
config.Routes.MapHttpRoute(//基于约定的路由
    name: "DefaultApi",
    routeTemplate: "api/{controller}/{id}",
    defaults: new { id = RouteParameter.Optional }
);
```
控制器

```c
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using ProductsAPP.Models;

namespace ProductsAPP.Controllers
{
    public class ProductsController : ApiController
    {
        //创建一个产品列表
        Product[] products = new Product[]
        {
            new Product{Id=1,Name="Tomato Soup",Category="Groceries",Price=1},
            new Product{Id=2,Name="Yo-yo",Category="Toys",Price=3.75M},
            new Product{Id=3,Name="Hammer",Category="Hardware",Price=16.99M},
        };

        public IEnumerable<Product> GetAllProducts()
        {
            return products;
        }
        public string GetId(int id)
        {
            return "a";
        }
        public string GetName(string name)
        {
            return "b";
        }
		public string GetIdName(int id,string name)
		{
		    return "ab";
		}
    }
}
```


## 二、情况1`https://localhost:44388/api/products/1`

URI中的1作为参数id，与操作GetId(int id)匹配


## 三、情况2`https://localhost:44388/api/products/?id=1`或`https://localhost:44388/api/products?id=1`

“?”号后的id=1，其中的1作为参数id，与操作GetId(int id)匹配


## 四、情况3`(https://localhost:44388/api/products/1?name=2)`

末尾“/”号后的1?name=2，其中的1作为参数id，2作为参数name，与操作GetIdName(int id,string name)匹配


## 五、情况4`https://localhost:44388/api/products/?id=1&name=2`或`https://localhost:44388/api/products?id=1&name=2`

“?”号后的id=1&name=2，其中的1作为参数id，2作为参数name，与操作GetIdName(int id,string name)匹配


## 参考

1. [C#进阶系列——WebApi 接口参数不再困惑：传参详解 - 懒得安分 - 博客园](https://www.cnblogs.com/landeanfen/p/5337072.html)
2. [ASP.NET Web API 中的路由 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api)
3. [ASP.NET Web API 中的路由和操作选择 | Microsoft Docs](https://docs.microsoft.com/zh-cn/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
