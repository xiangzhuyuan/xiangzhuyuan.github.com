---
layout: post
title: ASP.NET MVC 路由
date: 2010-11-02 18:30
comments: true
categories: []
---
           routes.MapRoute(
                "Default", // Route name
                "{controller}/{action}/{id}", // URL with parameters
                new { controller = "Home", action = "Index", id = UrlParameter.Optional }, // Parameter defaults
                new[] { "PaymentCenter.Controllers" }
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
            return RedirectToRoute("Portal_default");
        }
    }
