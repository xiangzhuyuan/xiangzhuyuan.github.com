---
layout: post
title: CakePHP Folder Structure
date: 2012-04-23 23:07
comments: true
categories: []
---
当你下载了<strong>CakePHP</strong>的程序包,解压之后你会发现它的目录结构是这样的:
<ul>
	<li>app</li>
	<li>lib</li>
	<li>vendors</li>
	<li>plugins</li>
	<li>.htaccess</li>
	<li>index.php</li>
	<li>README</li>
</ul>
<!--more-->

在这里,你需要注意3个比较重要的文件夹:
<ul>
	<li><strong>app</strong>文件夹,这个地方放置你的程序主要实现.</li>
	<li><strong>lib</strong>文件夹,这个地方主要放置cakephp框架的核心逻辑代码.</li>
	<li>还有一个就是<strong>vendors</strong>文件夹,这个地方主要放置一些其他的第三方的php库.</li>
</ul>
下面就让我们来详细的看看<strong>app</strong>文件夹下面各个文件夹的作用吧.

<strong>Config</strong>

放置所有的配置文件,包括连接数据库的配置,启动配置文件,还有核心的一些配置文件

<strong>Controller</strong>

包含程序中所有的控制器,还有它的组件

<strong>Lib</strong>

这个地方只存放你组件的类库,没有第三方的其他类库,这样就能够很多的将自己的内部库和其他库分离开来.

<strong>Local</strong>

这个地方保存国际化的字符串文件

<strong>Model</strong>

存放应用程序的对象定义代码,还有数据源.

<strong>Plugin</strong>

存放插件包

<strong>tmp</strong>

这个目录是CakePHP用来存放临时数据的,它存储的实际数据取决于你的配置,不过,习惯上,这个目录主要存放一些对象的描述信息,日志,还有session信息.你要确保这个目录是可写的.否则会影响你程序的性能,特别是在debug的时候程序会提醒你如果它不存在或这不可能读.

<strong>Vendor</strong>

任何第三方的类库都应该放在这里,你可以很容易的通过App::import(‘vendor’,’name’)函数来访问他们.可能很多人都会说这个是不是有点重复,因为在程序的根目录已经有vendor目录.我们将会在管理多个应用程序和复杂系统设置的时候分析为什么这样做.

<strong>View</strong>

所有的展示层的文件都放在这个地方,例如元素,错误页面,帮助文档,布局文件,还有视图文件.

<strong>webroot</strong>

在管理配置应用产品阶段,这个地方应该是应用的文件根目录.这个文档同时存放CSS样式文件,图片,还有javascript文件.
