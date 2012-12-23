---
title: WPSCMin:WordPress和WP Super Cache的html最小化插件
author: mathewxiang
layout: post
permalink: >
  /2012/01/wpscminwordpress%e5%92%8cwp-super-cache%e7%9a%84html%e6%9c%80%e5%b0%8f%e5%8c%96%e6%8f%92%e4%bb%b6/
categories:
  - 兴趣爱好
tags:
  - wordpress
  - WPSCMin
---
<http://lyncd.com/wpscmin/>

感谢他!  
WPSCMin是一个插件的插件,也就是wordpress的静态缓存插件wp super cache的插件.它使用Minify(<http://code.google.com/p/minify/>)引擎来去除你返回的html内容中多余的空格以及注释.最终你的页面将会减少5-20%的大小.

<!--more-->

  
**它干什么:**  
1.能够把wp super cache缓存起来的文件最大化的最小化.  
2.在wp super cache配置栏中添加了一个’on/off’开关,这样就能够在调试的时候关闭它,或者查看更加美观的源代码了.

**它不干什么:  
**1.不会去最小化那些单独的js和css文件.  
2.最小化动态页面.因为最小化动态页面的cpu消耗要大于因此而节约的带宽,-最小化html只是一种静态缓存的  
概念就像super cache.所以它只是最小化那些要被super cache缓存起来的文件.

**安装和更新:**  
要求:php5,wp super cache0.9.9.6+  
1,下载http://lyncd.com/files/WPSCMin-0.5.zip解压,然后把 WPSCMin.php复制到wp super cache目录下的插件文件夹.  
没有意外的话,就是这里:**wp-content/plugins/wp-super-cache/plugins/**.  
2,登录到wp管理面板,然后到wp super cache的plugins节点下,启用它.

 

 

下面的是Yahoo的一些研究文章:

*   [Performance Research, Part 1: What the 80/20 Rule Tells Us about Reducing HTTP Requests][1]
*   [Performance Research, Part 2: Browser Cache Usage – Exposed!][2]
*   [Performance Research, Part 3: When the Cookie Crumbles][3]
*   [Performance Research, Part 4: Maximizing Parallel Downloads in the Carpool Lane][4]
*   [Performance Research, Part 5: iPhone Cacheability – Making It Stick][5]

 [1]: http://yuiblog.com/blog/2006/11/28/performance-research-part-1/
 [2]: http://yuiblog.com/blog/2007/01/04/performance-research-part-2/
 [3]: http://yuiblog.com/blog/2007/03/01/performance-research-part-3/
 [4]: http://yuiblog.com/blog/2007/04/11/performance-research-part-4/
 [5]: http://yuiblog.com/blog/2008/02/06/iphone-cacheability/