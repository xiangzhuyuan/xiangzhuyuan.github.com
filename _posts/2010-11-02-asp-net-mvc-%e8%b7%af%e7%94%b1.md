---
title: ASP.NET MVC 路由
author: mathewxiang
layout: post
permalink: /2010/11/asp-net-mvc-%e8%b7%af%e7%94%b1/
categories:
  - 默认
---
routes.MapRoute(  
“Default”, // Route name  
“{controller}/{action}/{id}”, // URL with parameters  
new { controller = “Home”, action = “Index”, id = UrlParameter.Optional }, // Parameter defaults  
new[] { “PaymentCenter.Controllers” }  
);

===========  
AreaRegistration.RegisterAllAreas();

RegisterRoutes(RouteTable.Routes);

==================

[HandleError]  
public class HomeController : Controller  
{  
public ActionResult Index()  
{  
//转入Portal主站  
return RedirectToRoute(“Portal_default”);  
}  
}