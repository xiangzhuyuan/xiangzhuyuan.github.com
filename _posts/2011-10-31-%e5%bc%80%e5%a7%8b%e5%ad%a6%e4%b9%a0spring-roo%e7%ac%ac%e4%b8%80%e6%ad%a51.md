---
title: 开始学习Spring Roo第一步(1)
author: mathewxiang
layout: post
permalink: >
  /2011/10/%e5%bc%80%e5%a7%8b%e5%ad%a6%e4%b9%a0spring-roo%e7%ac%ac%e4%b8%80%e6%ad%a51/
categories:
  - 编程,代码
tags:
  - Maven
  - Spring Roo
---
[上次提到maven][1]还是刚接触到,就去apache那里看了看,了解的相当肤浅.好多东西都不知道了,忘记了毕竟离开java阵营也有很长时间了.最近有回来了,又让我回忆起来有关于xml的一些记忆.呵呵.

下面我要说的是一个基于Spring框架技术的另外一个的开发框架.也是采用了Maven的项目管理方式.

我们会很快得一步步建立一个过程,你会看见如何使用Roo在一个平常的工程中.  
详细的细节我们会在别的地方再讲.首先来我们看看怎么玩这个东东吧.

1先看看通过这个文章我们能够学到一些什么吧.  
我们会使用Roo的骨架来建立一个完整的web应用.这里会演示很多的Roo核心特色.而特别是下面这些,  
**你将会学到.**  
*建立工程  
*主域对象(JPA实体)的建立和开发.  
*给主域对象添加不同类型的域(field).  
*在主域对象间建立关系  
*集成测试的自动创建  
*建立IDE识别的工程  
*web层的自动架构  
*在web容器里运行程序  
*应用程序中访问不同试图的控制和安全性  
*自定义我们应用的外观  
*创建并运行Selenium测试.  
*开发备份你的应用

<!--more-->

替代的教程: the wedding rsvp application(结婚请柬?)

除了我们的这个教程,我们还在博客里写了一个单独的手把手教程,文章讲述了制作一个结婚请柬应用程序的所有步骤.  
它保持更新来对应Roo的主要版本,有很多的特性和有趣的技能.  
*通过JPA实体来创建一个标准的mvc web应用.  
*spring安全性的用法,包括登录页面的自定义.  
*通过smtp发送邮件  
*通过junit或者selenium测试.  
*Eclipse的用法  
*打包应用

<http://blog.springsource.com/2009/05/27/roo-part-2/>

下面就让我们来开始吧!

为了演示通过Roo来开发应用,我们要建立一个披萨店的网站,需求包括店员能够创建新的披萨种类,有披萨的排名功能.  
而且还能够让店主开设网上订单功能.通过简短的和店主的沟通,我们制作了一个简单的类图:

[<img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border-width: 0px;" title="pizza" src="http://www.yyxzy.org/wp-content/uploads/2011/10/pizza_thumb.png" alt="pizza" width="452" height="125" border="0" />][2]

这个类图简单描述了当前的需求,不过它是一个好的开始,能够让店主很多的了解我们将会给他做一个什么样的网站.  
之后我们会不断的扩展它,来演示更多的高级特性通过Spring Roo.

第一步:建立一个传统的过程  
我们和店主沟通之后,收集了最初的意见和需求,我们将要开始我们的开发工作了.在安装了jdk,Spring Roo和maven之后,我们建立一个工程目录:

<pre class="shell">&gt; mkdir pizza
&gt; cd pizza
pizza&gt;</pre>

接下来,我们开始正式使用Spring Roo了.通过在Roo命令行键入hint来获取关于内容的指导:

<pre class="shell">pizza&gt; roo
    ____  ____  ____
   / __ \/ __ \/ __ \
  / /_/ / / / / / / /
 / _, _/ /_/ / /_/ /
/_/ |_|\____/\____/    1.0.0.RELEASE [rev XXX]

Welcome to Spring Roo. For assistance press TAB or type "hint" then hit ENTER.
roo&gt;
roo&gt; hint
Welcome to Roo! We hope you enjoy your stay!

Before you can use many features of Roo, you need to start a new project.

To do this, type 'project' (without the quotes) and then hit TAB.

Enter a --topLevelPackage like 'com.mycompany.projectname' (no quotes).
When you've finished completing your --topLevelPackage, press ENTER.
Your new project will then be created in the current working directory.

Note that Roo frequently allows the use of TAB, so press TAB regularly.
Once your project is created, type 'hint' and ENTER for the next suggestion.
You're also welcome to visit http://forum.springframework.org for Roo help.
roo&gt;</pre>

Roo命令有很多的使用的功能.在键入了hint后,你会发现他会指引你一步步的完成你的第一个Roo工程.  
或者你键入help你会看见一个能够在当前上下文中可以用的命令列表.目前我们还没有创建一个新的工程,  
我们只是得到当前能够用的高级的命令.创建一个可用的工程我们可用使用project命令.

<pre class="shell">roo&gt; project --topLevelPackage com.springsource.roo.pizzashop
Created /Users/sschmidt/Development/workspaces/test9/pom.xml
Created SRC_MAIN_JAVA
Created SRC_MAIN_RESOURCES
Created SRC_TEST_JAVA
Created SRC_TEST_RESOURCES
Created SRC_MAIN_WEBAPP
Created SRC_MAIN_RESOURCES/META-INF/spring
Created SRC_MAIN_RESOURCES/META-INF/spring/applicationContext.xml
Created SRC_MAIN_RESOURCES/META-INF/spring/log4j.properties
com.springsource.roo.pizzashop roo&gt;</pre>

当你键入project命令.回车,Roo会创建一个maven风格的目录结构和一个pom.xml文件.顶层的包名会被用做pom.xml里的groupId.  
在之后的使用中你可以用’~'来代替这个顶层的包名.下面就是这个工程的目录:

[<img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="projectfolders" src="http://www.yyxzy.org/wp-content/uploads/2011/10/projectfolders_thumb.png" alt="projectfolders" width="362" height="287" border="0" />][3]  
这个时候你会发现这个目录结构完全遵循maven的约定.把代码,测试和资源文件单独放置.  
Roo还给你默认的添加了application context和log4j.最后,pom.xml会包含所有需要的依赖和配置来让我们顺利开工!

一旦目录结构生成,你可以继续给工程添加持久化,Roo借助Java Persistence API(JPA)的牛逼的对象关系映射来为工程提供持久化.  
JPA负责你工程的实体和底层的数据库表之间的沟通.添加JPA支持.你可以键入persistence setup命令来完成.

<pre class="shell">com.springsource.roo.pizzashop roo&gt; hint
Roo requires the installation of a JPA provider and associated database.

Type 'jpa setup' and then hit TAB three times.
We suggest you type 'H' then TAB to complete "HIBERNATE".
After the --provider, press TAB twice for database choices.
For testing purposes, type (or TAB) HYPERSONIC_IN_MEMORY.
If you press TAB again, you'll see there are no more options.
As such, you're ready to press ENTER to execute the command.

Once JPA is installed, type 'hint' and ENTER for the next suggestion.
com.springsource.roo.pizzashop roo&gt;
com.springsource.roo.pizzashop roo&gt; jpa setup --provider HIBERNATE --database HYPERSONIC_IN_MEMORY
Created SRC_MAIN_RESOURCES/META-INF/persistence.xml
Created SRC_MAIN_RESOURCES/META-INF/spring/database.properties
Managed SRC_MAIN_RESOURCES/META-INF/spring/applicationContext.xml
Managed ROOT/pom.xml
com.springsource.roo.pizzashop roo&gt;</pre>

(记住随时能够tab给提示的哦)

未完待续~

 [1]: http://www.yyxzy.org/2011/09/%E4%BB%80%E4%B9%88%E6%98%AFmaven/
 [2]: http://www.yyxzy.org/wp-content/uploads/2011/10/pizza.png
 [3]: http://www.yyxzy.org/wp-content/uploads/2011/10/projectfolders.png