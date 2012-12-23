---
title: Mono学习-1
author: mathewxiang
layout: post
permalink: /2011/09/getting-started-in-mono/
categories:
  - Mono
tags:
  - Gtksharp
  - Mono
---
**什么是Mono**  
Mono的设计初衷是成为一个能够让开发人员轻松地开发出跨平台的应用程序的软件平台.  
它是基于ECMA标准的C#和CLI开发的微软.net框架的开源版本,我们可以感觉到,拥有这样  
一个成功的标准化的软件平台,我们能够轻松地创建很棒的能够在Linux上跑的应用程序.

**组件**

使用到了很多组件来实现Mono:  
C#编译器-Mono的C#编译器完全实现了C# 1.0,2.0,3.0和4.0的功能,关于这个功能  
更好的描述可以去看这个http://en.wikipedia.org/wiki/C\_Sharp\_%28programming_language%29#Versions  
<!--more-->

**Mono的运行时环境**  
实现了ECMA CLI(ECMA Common Language Infrastructure),运行时环境提供了即时编译以及预编译,类库加载器,垃圾回收,  
线程系统,还有互操作功能.

**基类库**  
平台提供一个可读性强的一组类,这些类能够提供稳固的功能来创建应用程序,这些类可以和微软的.net框架下的类相媲美.

**Mono类库**

当然Mono也提供了很多类,这些类凌驾于微软提供的那些基础类之上.这些类是非常实用的.特别是再构建linux程序时,有很多例子,这些类是开发这些Gtk+, Zip files, LDAP, OpenGL, Cairo, POSIX等程序时用到的.

**好处**  
选择实用Mono开发应用程序有很多的好处:

**流行**-基于成功的.net框架,有很多的拥有丰富的C#开发经验的开发人员,而且还有数不尽的书籍,网站,教程以及样例代码来解决可想象的问题.  
**高级编程语言**-Mono借鉴了很多的实用特性,例如自动内存管理,反射,集合,还有线程,这些能够使你集中精力于你的应用程序而非系统基础功能代码.  
**基类库**-拥有可读性很强的类库,这些内建的类能够大大地提高生产效率,你需要Socket还是HashTable?不用费心了,这些平台都给你提供了.  
**跨平台**-Mono的设计初衷就是能够跨平台,Mono可以在 Linux, Microsoft Windows, Mac OS X, BSD, and Sun Solaris, Nintendo Wii, Sony PlayStation 3, Apple iPhone这些终端上跑,而且还能够在 x86, x86-64, IA64, PowerPC, SPARC (32), ARM, Alpha, s390, s390x (32 and 64 bits) 这些上面跑,还不止这些,使用Mono开发的应用程序可以让它在你身边任何一台计算机上运行.更多请阅读http://www.mono-project.com/What\_is\_Mono?title=Platforms&action=edit&redlink=1

**CLR(Common Language Runtime)**,公共语言运行时能够让你选择你最熟悉的语言,而且可以和CLR下的其他语言进行互操作,例如,你用C#写个类,你可以在VB.net继承  
它,而在Eiffel中使用它.详细阅读http://www.mono-project.com/Languages

**什么是Gtk#(GtkSharp)**  
它是专门为mono和.net开发的工具包.它集成了gtk+工具箱,  
以及GNOME类库,通过使用Mono和.net开发框架,能够完全支持原生的图形Gnome应用的开发.

**亮点:**  
1. 多平台(Unix,Windows,MacOS)  
2. 丰富的小工具和控件  
3. 可以通过ATK访问工具包来访问  
4. 国际化  
5. 支持C#,java,Python,VB.Net以及很多语言  
6. 用户界面设计器  
7. 开源,免费