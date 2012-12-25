---
layout: post
title: Using reCAPTCHA with ASP.NET
date: 2010-08-26 11:31
comments: true
categories: []
---
<h3>from <a href="http://code.google.com/apis/recaptcha/docs/aspnet.html">http://code.google.com/apis/recaptcha/docs/aspnet.html</a></h3>  <p>The reCAPTCHA ASP.NET Library provides a simple way to place a <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> on your ASP.NET website, helping you stop bots from abusing it. The library wraps the <a href="http://code.google.com/apis/recaptcha/intro.html">reCAPTCHA API</a>. You can use the library from any .NET language including C# and Visual Basic .NET.</p>  <p>To use reCAPTCHA with ASP.NET, you can download the <a href="http://code.google.com/p/recaptcha/downloads/list?q=label:aspnetlib-Latest">reCAPTCHA ASP.NET library</a>.</p>  <h4>Quick Start</h4>  <p>After you've signed up for your API keys, below are basic instructions for installing reCAPTCHA on your site with ASP.NET:</p>  <ol>   <li>Add a reference on your website to library/bin/Release/Recaptcha.dll: On the Visual Studio Website menu, choose Add Reference and then click the .NET tab in the dialog box. Select the Recaptcha.dll component from the list of .NET components and then click OK. If you don't see the component, click the Browse tab and look for the assembly file on your hard drive. </li>    <li>Insert the reCAPTCHA control into the form you wish to protect by adding the following code snippets:      <p>At the top of the aspx page, insert this:</p>      <pre>
