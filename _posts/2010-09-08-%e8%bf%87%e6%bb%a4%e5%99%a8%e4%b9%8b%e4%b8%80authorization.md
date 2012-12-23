---
title: 过滤器之一authorization
author: mathewxiang
layout: post
permalink: /2010/09/%e8%bf%87%e6%bb%a4%e5%99%a8%e4%b9%8b%e4%b8%80authorization/
categories:
  - 默认
---
<div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px" id="scid:0767317B-992E-4b12-91E0-4F059A8CECA8:9e7bad4f-2a8e-4098-843a-5a4d322ce23b" class="wlWriterEditableSmartContent">
  Technorati 标签: <a href="http://technorati.com/tags/asp.net+mvc2" rel="tag">asp.net mvc2</a>
</div>

public class ControllerContext 

System.Web.Mvc 的成员 

摘要: Encapsulates information about an HTTP request that matches specified System.Web.Routing.RouteBase and System.Web.Mvc.ControllerBase instances.

封装对应于指定sysytem,web.routing.routebase和system.web.mvc.controllerbase实例的http请求的信息,

<pre>public class <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext">ControllerContext</a></b>
{
    // Fields
    private <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Abstractions:3.5.0.0:31bf3856ad364e35/System.Web.HttpContextBase">HttpContextBase</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_httpContext:System.Web.HttpContextBase">_httpContext</a></b>;
    private <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RequestContext">RequestContext</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_requestContext:System.Web.Routing.RequestContext">_requestContext</a></b>;
    private <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RouteData">RouteData</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_routeData:System.Web.Routing.RouteData">_routeData</a></b>;
    [<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://mscorlib:2.0.0.0:b77a5c561934e089/System.Runtime.CompilerServices.CompilerGeneratedAttribute/.ctor()">CompilerGenerated</a>]
    private <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerBase">ControllerBase</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/<controller>k__BackingField:System.Web.Mvc.ControllerBase">&lt;controller>k__BackingField</a></b>;
    internal const <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://mscorlib:2.0.0.0:b77a5c561934e089/System.String">string</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/PARENT_ACTION_VIEWCONTEXT:String">PARENT_ACTION_VIEWCONTEXT</a></b> = "ParentActionViewContext";

    // Methods
    public <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/.ctor()">ControllerContext</a></b>();
    protected <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/.ctor(System.Web.Mvc.ControllerContext)">ControllerContext</a></b>(<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext">ControllerContext</a> controllerContext);
    public <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/.ctor(System.Web.Routing.RequestContext,System.Web.Mvc.ControllerBase)">ControllerContext</a></b>(<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RequestContext">RequestContext</a> requestContext, <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerBase">ControllerBase</a> controller);
    public <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/.ctor(System.Web.HttpContextBase,System.Web.Routing.RouteData,System.Web.Mvc.ControllerBase)">ControllerContext</a></b>(<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Abstractions:3.5.0.0:31bf3856ad364e35/System.Web.HttpContextBase">HttpContextBase</a> httpContext, <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RouteData">RouteData</a> routeData, <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerBase">ControllerBase</a> controller);

    // Properties
    public virtual <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerBase">ControllerBase</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/property:Controller:System.Web.Mvc.ControllerBase">Controller</a></b> { [<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://mscorlib:2.0.0.0:b77a5c561934e089/System.Runtime.CompilerServices.CompilerGeneratedAttribute/.ctor()">CompilerGenerated</a>] get; [<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://mscorlib:2.0.0.0:b77a5c561934e089/System.Runtime.CompilerServices.CompilerGeneratedAttribute/.ctor()">CompilerGenerated</a>] set; }
    public virtual <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Abstractions:3.5.0.0:31bf3856ad364e35/System.Web.HttpContextBase">HttpContextBase</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/property:HttpContext:System.Web.HttpContextBase">HttpContext</a></b> { get; set; }
    public virtual <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://mscorlib:2.0.0.0:b77a5c561934e089/System.Boolean">bool</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/property:IsChildAction:Boolean">IsChildAction</a></b> { get; }
    public <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ViewContext">ViewContext</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/property:ParentActionViewContext:System.Web.Mvc.ViewContext">ParentActionViewContext</a></b> { get; }
    public <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RequestContext">RequestContext</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/property:RequestContext:System.Web.Routing.RequestContext">RequestContext</a></b> { get; set; }
    public virtual <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RouteData">RouteData</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/property:RouteData:System.Web.Routing.RouteData">RouteData</a></b> { get; set; }
---------------------------------------------------------------------------</pre>

Gets or sets the URL route data. 

###### Return Value

The URL route data. 
<pre>===========================================================================</pre>

<pre>public virtual <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RouteData">RouteData</a> <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/property:RouteData:System.Web.Routing.RouteData">RouteData</a></b>
{
    get
    {
        if (this.<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_routeData:System.Web.Routing.RouteData">_routeData</a> == null)
        {
            this.<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_routeData:System.Web.Routing.RouteData">_routeData</a> = (this.<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_requestContext:System.Web.Routing.RequestContext">_requestContext</a> != null) ? this.<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_requestContext:System.Web.Routing.RequestContext">_requestContext</a>.<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RequestContext/property:RouteData:System.Web.Routing.RouteData">RouteData</a> : new <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Routing:3.5.0.0:31bf3856ad364e35/System.Web.Routing.RouteData/.ctor()">RouteData</a>();
        }
        return this.<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_routeData:System.Web.Routing.RouteData">_routeData</a>;
    }
    set
    {
        this.<a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext/_routeData:System.Web.Routing.RouteData">_routeData</a> = value;
    }
}</pre>

<pre></pre>

<font face="Courier New"></font> 
<pre>===========================================================================
    // Nested Types
    private sealed class <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext.EmptyHttpContext">EmptyHttpContext</a></b> : <a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Abstractions:3.5.0.0:31bf3856ad364e35/System.Web.HttpContextBase">HttpContextBase</a>
    {
        // Methods
        public <b><a href="http://www.aisto.com/roeder/dotnet/Default.aspx?Target=code://System.Web.Mvc:2.0.0.0:31bf3856ad364e35/System.Web.Mvc.ControllerContext.EmptyHttpContext/.ctor()">EmptyHttpContext</a></b>();
    }
}</pre>

========================

AuthorizeAttribute 继承与ControllerContext

Encapsulates the information that is required for using an [AuthorizeAttribute][1] attribute.

封装信息,使用AuthorizeAttribute 属性的请求信息.

 [1]: urn:member:T:System.Web.Mvc.AuthorizeAttribute