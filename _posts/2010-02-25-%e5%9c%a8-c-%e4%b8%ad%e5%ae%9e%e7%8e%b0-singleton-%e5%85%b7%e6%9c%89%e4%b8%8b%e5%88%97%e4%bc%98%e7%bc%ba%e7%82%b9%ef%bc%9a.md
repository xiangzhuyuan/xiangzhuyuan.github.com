---
title: '在 C# 中实现 Singleton 具有下列优缺点：'
author: mathewxiang
layout: post
permalink: >
  /2010/02/%e5%9c%a8-c-%e4%b8%ad%e5%ae%9e%e7%8e%b0-singleton-%e5%85%b7%e6%9c%89%e4%b8%8b%e5%88%97%e4%bc%98%e7%bc%ba%e7%82%b9%ef%bc%9a/
categories:
  - 默认
---
在 **C#** 中实现 **Singleton** 具有下列优缺点：

**优点**

*   由于 **.NET Framework** 显式地指定静态变量初始化如何以及何时发生，因此静态初始化方法是可能的。

*   列的前面的”多线程 **Singleton”**中所描述的 *Double-Check Locking*  
    技术已在公共语言运行库中正确实现。

**缺点**

如果您的多线程应用程序需要进行显式初始化，那么必须采取措施以避免线程问题。