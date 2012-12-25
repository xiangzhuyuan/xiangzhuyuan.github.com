---
layout: post
title: 在 C# 中实现 Singleton 具有下列优缺点：
date: 2010-02-25 03:21
comments: true
categories: []
---
<p>在 <b>C#</b> 中实现 <b>Singleton</b> 具有下列优缺点：</p>
<p><b>优点</b></p>
<ul><li>
<p>由于 <b>.NET Framework</b> 显式地指定静态变量初始化如何以及何时发生，因此静态初始化方法是可能的。</p>
</li>
<li>
<p>列的前面的"多线程 <b>Singleton"</b>中所描述的 <i>Double-Check Locking</i>
技术已在公共语言运行库中正确实现。</p>
</li>
</ul><p><b>缺点</b></p>
<p>如果您的多线程应用程序需要进行显式初始化，那么必须采取措施以避免线程问题。</p>
