---
title: 10个利用jQuery mobile插件开发移动网页的小贴士
author: mathewxiang
layout: post
permalink: /2011/09/gettingstarttedjquerymobile/
categories:
  - web开发
tags:
  - android
  - ipad
  - iphone
  - jQuery
  - jQuery mobile
  - smartphone
---
from:http://www.webdesignerdepot.com/2011/05/10-handy-jquery-mobile-tips-and-snippets-to-get-you-started  
万事开头难,技术也不例外.带着这样的想法,我们将一些和jQuery Mobile库相关的技巧还有代码段放在这里,为了让大家能够轻松的了解这些东西.在这里我们不是全面的讲解这个库,而是直接上来就讲那些对于刚开始接触的人来说很迷惑纠结的点.你可以在评论中让我们知道那段代码比较好用,同时你也可以告诉我们你自己的好用的代码哦.  
<!--more-->

  
1. 一个最基本的页面

我发现自己总是需要一个完整的最基本的页面.下面的这个就是一个最基本页面的代码:  
[<img class="alignnone size-medium wp-image-266" title="1" src="http://www.yyxzy.org/wp-content/uploads/2011/09/1-300x226.png" alt="" width="300" height="226" />][1]  
2. 在哪里添加传统的jQuery调用

在我开始使用jQuery的扩展的时候,我发现自己会立刻修改一些页面的东西在mobile创建被触发之前.而事实告诉我,推荐的解决方案是在加载mobile插件之前添加传统的jQuery的调用.这样的话,你的jQuery命令就有机会在库加载完成之前运行.下面是一种模式:  
[<img class="alignnone size-medium wp-image-267" title="2" src="http://www.yyxzy.org/wp-content/uploads/2011/09/2-300x221.png" alt="" width="300" height="221" />][2]  
3. 立刻禁用所有的链接Ajax导航

Ajax的导航是相当的绚烂的,但是很多时候我们想把它禁用了.可以添加下面的代码来告诉mobile库来禁用ajax导航.在添加mobile库之后添加一小段代码,也就是说要在库加载完成之后才能够引用.  
[<img class="alignnone size-medium wp-image-268" title="3" src="http://www.yyxzy.org/wp-content/uploads/2011/09/3-300x134.png" alt="" width="300" height="134" />][3]  
4. 禁止截取一些字符串

Mobile库的一个亮点是它能够很智能的截取一些比较长的项目来使用UI元素.我发现在2个地方这个功能还是比较烦人的,第一,就是在我的list条目中,我往往想看到全部的文字,第二个就是在页面的尾部.往往它会把你的长字符串给截断了,在后面添加上”…”来代替.可以使用这个简单的css来重写这些默认的设置.

针对于list:

    body .ui-li .ui-li-desc {

     white-space: normal;

     }

针对于尾部:

    body .ui-footer .ui-title {

     white-space: normal;

     }

     

5. 使用media属性来获取终端的类型

首先我的问题是怎么基于css(屏幕尺寸)来识别终端.举个例子,我想在iPad上显示2列而在智能手机上显示1列,很明显的办法就是通过media queries来完成.

在一些时候通过使用media queries,你可以很快的做出目标的屏幕大小,接着按着这个尺寸,我们能够很快得设置不同的布局在可用的屏幕空间上通过传统的css技术.

下面是两个比较牛逼的资源:

· “[**CSS Media Queries and Using Available Space**][4],” CSS-Tricks;

· [**Hardboiled CSS3 Media Queries**][5],” Stuff and Nonsense.

6. 通过jQuery来确定终端

就像我们想在某些终端上执行对于的css一样,我们希望能够在对于的平台上执行特定的jQuery.这里有一个适配器(<http://snipplr.com/view/31607/iphone-ipad-ipod-detect/>),它能够很轻松的在用户的终端上运行jQuery的片段.  
[<img class="alignnone size-medium wp-image-269" title="4" src="http://www.yyxzy.org/wp-content/uploads/2011/09/4-300x136.png" alt="" width="300" height="136" />][6]

7. 还有一个比较扭曲的问题就是这个库很难找到post过去一个form的目标页面.除非你使用从根目录开发的完全路径

举个例子,我发现这个form就永远也找不到它的接收者.

    <form action=" form-handler.php " method="get" >

而如果希望能够正常工作,你就需要一个完整的路径:

    <form action="/current-directory/form-handler.php" method="get" >

或者,就是让处理form的页面返回一个完整可以用的jQuery mobile页面,在tip1中提到的.

8. 做一个弹出框

一个比较有用的特色就是这个库内建的弹出框和对话框,设置这个玩意实在是简单到不行,你只需要给一个链接添加一个属性,data-rel=”dialog”.

需要注意2个事情:1. 这个页面必须是一个完整的jQuery mobile页面.在tip1中提到的.2. 这个页面必须是一个完全独立的外部页面.

    <a href="#pop.html" data-rel="dialog">Pop up!</a> 

[<img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="clip_image008" src="http://www.yyxzy.org/wp-content/uploads/2011/09/clip_image008_thumb.gif" alt="clip_image008" width="254" height="500" border="0" />][7]

9. 取消和确定的按钮组合

这段代码容纳了两个基本的需求,首先它拥有2个按钮,幸运的是,这个库有内建的列结构,能够轻松的使用fieldset标签和合适的类来让它工作,看下面,第二就是让2个按钮有不同的样式,这个代码是来源于文档的,我经常用到它.

    <fieldset>

     <div><button type="submit" data-theme="c">Cancel</button></div>

     <div><button type="submit" data-theme="b">Submit</button></div>

    </fieldset>

[<img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="clip_image010" src="http://www.yyxzy.org/wp-content/uploads/2011/09/clip_image010_thumb.gif" alt="clip_image010" width="254" height="500" border="0" />][8]

10. 创建一个你自己的列结构

我希望能够创建一个适应多个终端的页面,我发现我需要组合使用上面提到的media query技巧.幸运的是,web开发者很早之前就解决了这个问题,通过组合这些技术和media query.我们可以轻松创建对应于不同终端的不同结构的页面.

<http://www.positioniseverything.net/articles/onetruelayout/anyorder> 这篇文章设置出了最简单的系统之一.

总结

jQuery mobile库发展很迅猛,它可以让只要花很少功夫就能够做出绚烂的页面.虽然它现在还是beta2版本,但是它有一个好的开始,希望这些入门tips能够让你喜欢上这个库.

 [1]: http://www.yyxzy.org/wp-content/uploads/2011/09/1.png
 [2]: http://www.yyxzy.org/wp-content/uploads/2011/09/2.png
 [3]: http://www.yyxzy.org/wp-content/uploads/2011/09/3.png
 [4]: http://css-tricks.com/css-media-queries/
 [5]: http://stuffandnonsense.co.uk/blog/about/hardboiled_css3_media_queries
 [6]: http://www.yyxzy.org/wp-content/uploads/2011/09/4.png
 [7]: http://www.yyxzy.org/wp-content/uploads/2011/09/clip_image008.gif
 [8]: http://www.yyxzy.org/wp-content/uploads/2011/09/clip_image010.gif