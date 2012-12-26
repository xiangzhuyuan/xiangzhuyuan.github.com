---
layout: post
title: 腾讯的网站如何检测到你的 QQ 已经登录？
date: 2012-07-02 12:06
comments: true
categories: []
---
thanks for his share:(<a title="塵埃落定" href="http://www.lovelucy.info/tencent-sso.html">http://www.lovelucy.info/tencent-sso.html</a>)

<del>异构系统单点登录 SSO（single-sign-on）技术</del>

&nbsp;

网上有很多猜测，比如——<!--more-->

QQ 登录时在本地某地方存登录 ID 信息（Cookie 或文件），用 js 读，然后去服务器认证。但是现在的浏览器一般有沙箱功能，js 无法读到登录 ID；而且在清空 Cookie 后依然起作用。
以 IP、CPU ID、硬盘 ID 等硬件设备 hash 做唯一标识，QQ 登录时在服务器记录此信息，js 验证。感觉这样依赖环境过多，QQ 不太可能采用此方法。
QQ 启动某端口监听，js 连接此端口。但是用 netstat 查看后，QQ 并没有监听端口。
有这么一个神奇的链接，http://xui.ptlogin2.qq.com/cgi-bin/qlogin 你一点开，它就检测到你登录了 QQ。通过查看页面源代码，我们可以发现一个关于 ptlogin 的 js 文件，这段代码中，描述了使用 ActivexObject 浏览器插件的过程，于是一切了然。

可是 ActiveX 是 IE 的插件呀，我们使用 Chrome 或者 FireFox 也是可以直接登录的，这是怎么回事呢？

原来，QQ 使用了历史很悠久的 NPAPI（Netscape Plugin Application Programming Interface）接口。NPAPI 几乎支持所有主流浏览器，包括 FireFox、Chrome、Opera（IE 从 5.5 后停止支持 NPAPI，转而使用 ActiveX）。

打开 chrome://plugins/ 我们可以发现自动登录的有关插件，而在路径 <del>C:\Program Files\Tencent\QQ\Bin\TXSSO\bin</del> 下就可以找到关于 SSO 的相关动态链接库。

<strong>npSSOAxCtrlForPTLogin.dll</strong>

reference link:
<ul>
	<li>http://en.wikipedia.org/wiki/NPAPI</li>
	<li>http://mozilla.com.cn/post/21666/</li>
	<li>http://geeklu.com/2010/10/getting-started-with-npapi-plugin/</li>
	<li>http://www.lovelucy.info/tencent-sso.html</li>
	<li>http://1.lanz.sinaapp.com/?p=152</li>
	<li>http://taurus-ly.com/articles/2012/02/153.html</li>
	<li>http://www.cnblogs.com/cxwx/archive/2010/07/01/1768957.html</li>
</ul>
