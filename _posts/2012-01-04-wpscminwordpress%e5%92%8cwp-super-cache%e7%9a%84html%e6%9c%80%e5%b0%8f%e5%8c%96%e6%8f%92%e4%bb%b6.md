---
layout: post
title: WPSCMin:WordPress和WP Super Cache的html最小化插件
date: 2012-01-04 21:12
comments: true
categories: []
---
<a href="http://lyncd.com/wpscmin/">http://lyncd.com/wpscmin/</a>

感谢他!
WPSCMin是一个插件的插件,也就是wordpress的静态缓存插件wp super cache的插件.它使用Minify(<a href="http://code.google.com/p/minify/">http://code.google.com/p/minify/</a>)引擎来去除你返回的html内容中多余的空格以及注释.最终你的页面将会减少5-20%的大小.

<!--more-->
<strong>它干什么:</strong>
1.能够把wp super cache缓存起来的文件最大化的最小化.
2.在wp super cache配置栏中添加了一个'on/off'开关,这样就能够在调试的时候关闭它,或者查看更加美观的源代码了.

<strong>它不干什么:
</strong>1.不会去最小化那些单独的js和css文件.
2.最小化动态页面.因为最小化动态页面的cpu消耗要大于因此而节约的带宽,-最小化html只是一种静态缓存的
概念就像super cache.所以它只是最小化那些要被super cache缓存起来的文件.

<strong>安装和更新:</strong>
要求:php5,wp super cache0.9.9.6+
1,下载http://lyncd.com/files/WPSCMin-0.5.zip解压,然后把 WPSCMin.php复制到wp super cache目录下的插件文件夹.
没有意外的话,就是这里:<strong>wp-content/plugins/wp-super-cache/plugins/</strong>.
2,登录到wp管理面板,然后到wp super cache的plugins节点下,启用它.

&nbsp;

&nbsp;

下面的是Yahoo的一些研究文章:
<ul>
	<li><a href="http://yuiblog.com/blog/2006/11/28/performance-research-part-1/">Performance Research, Part 1: What the 80/20 Rule Tells Us about Reducing HTTP Requests</a></li>
	<li><a href="http://yuiblog.com/blog/2007/01/04/performance-research-part-2/">Performance Research, Part 2: Browser Cache Usage - Exposed!</a></li>
	<li><a href="http://yuiblog.com/blog/2007/03/01/performance-research-part-3/">Performance Research, Part 3: When the Cookie Crumbles</a></li>
	<li><a href="http://yuiblog.com/blog/2007/04/11/performance-research-part-4/">Performance Research, Part 4: Maximizing Parallel Downloads in the Carpool Lane</a></li>
	<li><a href="http://yuiblog.com/blog/2008/02/06/iphone-cacheability/">Performance Research, Part 5: iPhone Cacheability - Making It Stick</a></li>
</ul>
