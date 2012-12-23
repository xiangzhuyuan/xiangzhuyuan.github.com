---
title: 我认识的wcf和web service之间的区别
author: mathewxiang
layout: post
permalink: /2011/08/different_between_wcf_and_webservice/
categories:
  - '.net C#开发'
  - 编程,代码
tags:
  - .net
  - asp.net web service
  - wcf
---
<p align="left">
  <strong>介绍</strong>
</p>

<p align="left">
  解释WCF和 asp.net web service之间的区别和联系.在使用开发实现asp.net web service的时候我们主要依靠的是XmlSerializer来把数据对象转化为xml的.
</p>

<p align="left">
  在使用XmlSerializer来序列化.net类型为xml的时候需注意一下几点:
</p>

<p align="left">
  a)      只有public的字段或者属性才能够被解析为xml.
</p>

<p align="left">
  b)      类必须实现IEnumerable的接口.
</p>

<p align="left">
  c)      那些实现了IDictionary接口的类型不能够解析为xml,例如Hash table.
</p>

<pre name="code" class="csharp">[DataContract]
public class Item
{
[DataMember]
public string ItemID;
[DataMember]
public decimal ItemQuantity;
[DataMember]
public decimal ItemPrice;

}</pre>

<p align="left">
  <em> </em>
</p>

<p align="left">
  而WCF是使用DataContractAttribute和DataMemberAttribute这两个属性类来把.net下的类型解释为xml的.
</p>

<p align="left">
  DataContractAttribute属性类能够运用在类和结构上.DataMemberAttribute运用在字段和property上.而这些Field和property能够是public或者private的.
</p>

<p align="left">
  <strong>DataContractAttribute</strong><strong>和</strong><strong>XmlSerializer</strong><strong>之间的只要区别</strong><strong></strong>
</p>

<p align="left">
  a)      DataContractAttribute在设计上要比XmlSerializer有更好的性能.
</p>

<p align="left">
  b)      在序列化数据对象类的时候,XmlSerializer不能够对具体的字段区别对待.而DataContractAttribute能够显式表示那些字段和属性需要内序列化.
</p>

<p align="left">
  c)      DataContractAttribute能够解析Hashtable为xml.
</p>

<p align="left">
  <strong>开发Service</strong>
</p>

<p align="left">
  在开发asp.net web service 的时候我们必须在类上添加WebService属性和在方法上添加WebMethod属性.
</p>

<p align="left">
  <strong>Example</strong>
</p>

<pre name="code" class="csharp">[WebService]
public class Service : System.Web.Services.WebService
{
[WebMethod]
public string Test(string strMsg)
{
return strMsg;
}
}</pre>

<p align="left">
  在开发WCF的时候我们需要这样:
</p>

<pre name="code" class="csharp">[ServiceContract]
public interface ITest
{
[OperationContract]
string ShowMessage(string strMsg);
}
public class Service : ITest
{
public string ShowMessage(string strMsg)
{
return strMsg;
}
}</pre>

<p align="left">
  首先我们需要写一个接口,这个接口被ServiceContractAttribute修饰.它说明了这个接口定义了一个WCf 服务的契约.接口的方法都被OperationContractAttribute所修饰,它说明了这些方法都是服务契约的操作.
</p>

<p align="left">
  实现了这个接口的类就看做是WCF里的服务类.
</p>

<p align="left">
  <strong>服务宿主</strong>
</p>

<p align="left">
  Asp.net web service被编译成了一个dll和一个.asmx文件,这个服务文件在应用程序的根目录下.dll在bin文件夹里,我们通过url来访问服务.
</p>

<p align="left">
  WCF服务可以寄宿在IIS或者WindowsActionService.
</p>

<p align="left">
  a)      编译服务类为一个类库.
</p>

<p align="left">
  b)      .SVC服务类文件复制到虚拟目录根目录,程序集复制到bin子目录.
</p>

<p align="left">
  c)      复制web.config文件到虚拟目录的根目录.
</p>

<p align="left">
  <strong>客户端开发</strong><strong></strong>
</p>

<p align="left">
  ASP.NET Web services通过命令行工具wsdl.exe来生成客户端代码.WCF使用ServiceMetadata tool(svcutil.exe)来生成客户端代码.
</p>

<p align="left">
  <strong>消息表述</strong><strong></strong>
</p>

<p align="left">
  在ASP.NET Web services中,SOAP消息的头可以自定义,在WCF服务中提供了MessageContractAttribute , MessageHeaderAttribute 和 MessageBodyMemberAttribute来描述soap消息的结构.
</p>

<p align="left">
  <strong>服务描述</strong><strong></strong>
</p>

<p align="left">
  asp.net接收到一个wsdl描述的get请求时,同样会返回一个wsdl描述的响应.可以通过继承自ServiceDescriptionFormatExtension类来自定义wsdl.
</p>

<p align="left">
  当wcf接收到一个wsdl的请求时,wcf可以使用继承自ServiceMetadataBehavior这个类来自定义返回的wsdl响应.
</p>

<p align="left">
  <strong>异常处理</strong><strong></strong>
</p>

<p align="left">
  在ASP.NET Web services中,不被处理的异常将会给客户端返回一个soap错误.在wcf 服务中,在遇到不被处理的异常时不会返回soap错误,可以通过配置文件来处理这些异常,能够给客户端发送一些有助于调试的响应.
</p>

基本上可以说有下面几点关于在使用这两个服务时的选择:

1.  Wcf更加标准一点比起asp.net web service.
2.  Wcf可以支持HTTP,TCP,MSMQ,WS-HTTP 等的这些协议.而asp.net web service只支持http.
3.  Wcf能够像com+那样处理事务
4.  Wcf已经集成了Json
5.  Wcf可以寄宿在IIS或者WAS.
6.  Asp.net web service没有实例管理功能.例如你不能够有单例的service或者事务管理.