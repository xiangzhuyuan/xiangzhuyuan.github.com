---
layout: post
title: CakePHP Structure
date: 2012-05-14 10:17
comments: true
categories: []
---
<h1><a href="http://www.yyxzy.org/wp-content/uploads/2012/05/cakephp.jpg"><img class="alignnone size-full wp-image-1324" title="cakephp" src="http://www.yyxzy.org/wp-content/uploads/2012/05/cakephp.jpg" alt="" width="653" height="206" /></a>基于cakephp的程序中的一些结构</h1>
Cakephp中不仅仅有Controller, Model和View这些类,而且还有其他的一些特色的附加类和对象.这些能够帮助你在MVC模式的开发中更加快速和享受他们.组件,行为,帮助类这些类都是提供一些容易扩展和重用的类,他们能够帮助开发者来快速添加一些功能性函数到基于MVC框架的应用中.现在我们就站在一个更高的角度,来看看这些特色到底是怎么来提供这些特性的.<!--more-->

<strong>应用程序扩展</strong>

控制器,帮助类,还有对象类,他们都拥有自的父类.这个父类能够作用于整个应用.AppController(在<tt>/app/Controller/AppController.php</tt>), AppHelper (在 <tt>/app/View/Helper/AppHelper.php</tt>) 还有 AppModel (在 <tt>/app/Model/AppModel.php</tt>),他们够能够让你添加一些函数,能够在控制器,帮助类,以及对象类之间共享这些函数.

虽然他们不是类或者文件,但是路由扮演了一个这样的角色,在一个cakephp的请求中,路由的配置定义可以告诉cakephp怎么来把url和控制器匹配起来.默认的行为或假定这个url:/controller/action/var1/var2 会被映射到Controller::action($var1, $var2),但是你也可以使用路由类来自定义url怎么来和控制器匹配在你的应用中.

一些特色的东西可以在cakephp中被打包作为一个插件来用.一个插件可以是对象,控制器,还有视图组成的来完成一个特定目的的在cakephp应用中.例如一个用户管理系统或者简单的博客系统.都能够作为插件在cakephp中使用.

<strong>控制器的扩展(创作组件Components)</strong>

一个组件就是一个类,他的作用就是协助控制器来完成一个逻辑任务,如果你希望一些逻辑可以在控制器之间共用,或者是在这个应用中,组件通常就能够派上用场.例如,核心的EmailComponent组件类就能够很容易的插件并且发送邮件,比起在控制器中自己写一个单独的action来完成这个任务,你就可以把它打包出来共享它.

控制器还经常被用来作为回调的对象,一些回调行为还是比较有用的.如果你需要在cakephp的核心操作中插入一些逻辑代码,可以这样实现回调:
<ol>
	<li>beforeFilter(),会在运行控制器的action逻辑前被触发.</li>
	<li>beforeRender().他会在跑完逻辑响应视图之前被触发.</li>
	<li>afterFiler(),他会在跑完这个逻辑及响应视图之后被触发.往往他和afterRender()之间没有太大的区别,但是如果你手动的调用render()方法,然后再运行一些逻辑就会不一样了.</li>
</ol>
<strong>对象的扩展(行为Behaviors)</strong>

同样的,行为的作用也是对于对象类来添加一些功能性的函数.例如,如果你存储用户的数据到一个树结构中,你可以声明你的用户对象像一个树结构,然后像操作树一样来移除添加替换节点的数据.对象类同样被叫做<strong>DataSources</strong>的类支持,<strong>DataSources</strong>是一个抽象的模块,他能够使操作对象的不同数据类型而保持一致.一般来说cakephp中的数据源一般都是数据库.你可能会添加一些附加的数据源,然后能够允许你把对象数据输出到Rss,CSV文件,或者LDAP等.甚至iCal事件,Datasources允许你统一来自不同的数据源数据,相比较有限的Sql join.Datasources允许你告诉自己的LDAP对象,使他们统一于一些iCal事件.

就像控制器一样,对象类也有很多的回调函数:
<ul>
	<li>beforeFind()</li>
	<li>afterFind()</li>
	<li>beforeValidate()</li>
	<li>beforeSave()</li>
	<li>afterSave()</li>
	<li>beforeDelete()</li>
	<li>afterDelete()</li>
</ul>
相比这些函数的名称以及足以让你明白到底他们能够干什么了.详细的会在以后的对象章节中提到.

<strong>视图的扩展(Helpers)</strong>

一个帮助类他的存在就是为了完成视图逻辑,好比组件至于控制器.帮助类能够让一个现实逻辑被访问,而且能够在多个视图间共享,一个核心的帮助类,<strong>AjaxHelper</strong>,他能够让Ajax的请求变得更加简单.

很多的应用中,在视图层那边有很多的代码块是重复的.cakephp能够通过布局(layouts)和元素(elements)来让这些代码能够重用.默认的,每一个视图在被控制器响应之后会被放置在一个layout中.元素会在多个视图中被当做代码段来重复使用.
