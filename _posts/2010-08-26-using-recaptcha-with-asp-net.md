---
title: Using reCAPTCHA with ASP.NET
author: mathewxiang
layout: post
permalink: /2010/08/using-recaptcha-with-asp-net/
categories:
  - 默认
---
### from <http://code.google.com/apis/recaptcha/docs/aspnet.html>

The reCAPTCHA ASP.NET Library provides a simple way to place a [CAPTCHA][1] on your ASP.NET website, helping you stop bots from abusing it. The library wraps the [reCAPTCHA API][2]. You can use the library from any .NET language including C# and Visual Basic .NET.

To use reCAPTCHA with ASP.NET, you can download the [reCAPTCHA ASP.NET library][3].

#### Quick Start

After you’ve signed up for your API keys, below are basic instructions for installing reCAPTCHA on your site with ASP.NET:

1.  Add a reference on your website to library/bin/Release/Recaptcha.dll: On the Visual Studio Website menu, choose Add Reference and then click the .NET tab in the dialog box. Select the Recaptcha.dll component from the list of .NET components and then click OK. If you don’t see the component, click the Browse tab and look for the assembly file on your hard drive. 
2.  Insert the reCAPTCHA control into the form you wish to protect by adding the following code snippets: 
    At the top of the aspx page, insert this:
    
    <pre>

 [1]: http://www.google.com/recaptcha/captcha
 [2]: http://code.google.com/apis/recaptcha/intro.html
 [3]: http://code.google.com/p/recaptcha/downloads/list?q=label:aspnetlib-Latest