---
layout: post
title: YUI Compressor
date: 2012-02-13 23:19
comments: true
categories: []
---
之前说到了<a href="http://www.yyxzy.org/2012/01/jsmin/">JSLint</a>,不过在实际的工作中间到底是否能够完全遵循标准来实现就是另一说了.

According to <a href="http://developer.yahoo.com/performance/">Yahoo!'s Exceptional Performance Team</a>, 40% to 60% of Yahoo!'s users have an empty cache experience and about 20% of all page views are done with an empty cache (see <a href="http://yuiblog.com/blog/2007/01/04/performance-research-part-2/">this article by Tenni Theurer on the YUIBlog for more information on browser cache usage</a>). This fact outlines the importance of keeping web pages as lightweight as possible. Improving the engineering design of a page or a web application usually yields the biggest savings and that should always be a primary strategy. With the right design in place, there are many secondary strategies for improving performance such as minification of the code,<a href="http://en.wikipedia.org/wiki/Http_compression">HTTP compression</a>, using CSS sprites, etc.<!--more-->

根据yahoo性能小组的调查,yahoo的访问者中有40%到60%的用户在访问yahoo页面的时候是没有缓存的.而20%的页面是在没有缓存的情况下加载的.这个结果就说明了把一个页面尽可能做得轻量级是多么的重要.所以设计师提高一个页面的设计质量或者一个web工程,对于提高性能来说是一个很好的策略.有了适当的设计,然后还有很多的二级策略来提高性能.例如最小化代码,HTTP压缩,使用css sprites等.

In terms of code minification, the most widely used tools to minify JavaScript code are Douglas Crockford's <a href="http://crockford.com/javascript/jsmin">JSMIN</a>, <a href="http://dojotoolkit.org/docs/shrinksafe">the Dojo compressor</a> and Dean Edwards' <a href="http://dean.edwards.name/packer/">Packer</a>. Each of these tools, however, has drawbacks. JSMIN, for example, does not yield optimal savings (due to its simple algorithm, it must leave many line feed characters in the code in order not to introduce any new bugs).

对于最小化代码,常用到的工具就是来压缩Javascript代码,例如Douglas Crockford 的JSMIN,还有Dojo压缩,Dean Edward的Packer,不过这些工具都有一些硬伤,例如JSMIN,不能够做到完全的节约,由于他的简单的算法,为了不产生一些新的bug而不得不余留一些换行在代码中.

The goal of JavaScript and CSS minification is always to preserve the operational qualities of the code while reducing its overall byte footprint (both in raw terms and after gzipping, as most JavaScript and CSS served from production web servers is gzipped as part of the HTTP protocol). The YUI Compressor is JavaScript minifier designed to be 100% safe and yield a higher compression ratio than most other tools. Tests on the <a href="http://developer.yahoo.com/yui/">YUI Library</a> have shown savings of over 20% compared to JSMin (becoming 10% after HTTP compression). The YUI Compressor is also able to compress CSS files by using a port of <a href="http://foohack.com/">Isaac Schlueter</a>'s regular-expression-based CSS minifier.
<div> Javascript和Css 的最小化它的目的就是能够保持它的高可操作行的前提下减少代码的传输量,YUI压缩就是一个为javascript设计的100%安全的最小化精简工具,它能够比其他任何工具更加高效的压缩js,同样,它还能够压缩css,通过Isaac Schlueter 的一个基于正则的css最小化插件.</div>
<div>
<h2 id="work">How does the YUI Compressor work?</h2>
The YUI Compressor is written in <a href="http://java.sun.com/">Java</a> (requires Java &gt;= 1.4) and relies on <a href="http://www.mozilla.org/rhino/">Rhino</a> to tokenize the source JavaScript file. It starts by analyzing the source JavaScript file to understand how it is structured. It then prints out the token stream, omitting as many white space characters as possible, and replacing all local symbols by a 1 (or 2, or 3) letter symbol wherever such a substitution is appropriate (in the face of <a href="http://www.jslint.com/lint.html">evil features</a> such as <code>eval</code> or <code>with</code>, the YUI Compressor takes a defensive approach by not obfuscating any of the scopes containing the evil statement) The CSS compression algorithm uses a set of finely tuned regular expressions to compress the source CSS file. The YUI Compressor is open-source, so don't hesitate to look at the code to understand exactly how it works.

它到底是怎么工作的呢?

YUI压缩器是用Java写的.依赖于Rhino来标记化javascript的源代码.通过分析javascript的源代码文件来解析它的结构,然后打印出标记化的文件流,尽可能的忽略掉所有的空白字符.然后替换掉所有的本地变量通过使用单个的字母.只要这种做法是合适的.在遇到一些诡异的写法的时候,采取保守的策略以防混淆表达式,在css压缩算法中使用了一系列的正则表达来压缩文件.总之,yui是开源的,你可以查看代码来理解他的工作原理.

&nbsp;

</div>
