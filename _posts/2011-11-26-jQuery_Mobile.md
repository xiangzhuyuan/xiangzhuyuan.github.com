---
layout: post
title: jQuery Mobile使用简单例子
date: 2011-11-26 15:07
comments: true
categories: []
---
<strong>介绍</strong>
欢迎使用jQuery Mobile，如果你之前还没有用过jQuery，不需要担心。
尽管对于jQuery的理解还有对javascript的理解在这里来说是好事情，但是你还是可以不需要掌握太多html标记意外的技能。
在接下来的一小会时间我将会引导你来创建一个简单基于jQuery Mobile的网站，还会告诉你在哪里你能够学到更多。

我们这里将会用到的时<strong> jQuery Mobile 1.0 Alpha 4.1</strong>.

<strong>开始：</strong>
开始前你可以去下载jQuery Mobile的包，最新最稳定的在这里<a href="http://jquerymobile.com/download/">http://jquerymobile.com/download/</a>.当然我们的代码也会使用CDN（content delivery network）来发布。
<!--more-->
每一个jQuery Mobile的工程都是开始于至少一个html文件。在你最喜欢的编辑器中新建一个命名为inex1。html的文件。我们的页面的基于html5的doctype。
&lt;!DOCTYPE html&gt;
注意所有的使用到jQuery Mobile扩张库的页面都是要使用html5标记的。html的头部有3部分构成：
*css文件
*jQuery核心库
*jQuery Mobile库

例子：
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Page Title&lt;/title&gt;
&lt;link rel="stylesheet" href="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css"</a> /&gt;
&lt;script src="<a href="http://code.jquery.com/jquery-1.5.2.min.js&quot;">http://code.jquery.com/jquery-1.5.2.min.js"</a>&gt;&lt;/script&gt;
&lt;script src="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js"</a>&gt;&lt;/script&gt;
&lt;/head&gt;
接下来我们看看页面的body部分。jQuery Mobile使用的通常的html标记，而是在移动设备上来增强他们的表现形式。而这个增强就是通过html标签的data属性来起作用的。
像下面这样：
&lt;div id="someId" data-something="foobar"&gt;

看见这个data-something标记了吗？我们能够把这个标记添加到任何的html标记，浏览器会无视它。当浏览器无视它的时候，jquery mobile就
能够使用这些属性来帮助页面生成一个适合移动设备浏览器的页面。jquery mobile会寻找一个包含特殊data-role的值为page的div标签。例子：
&lt;div data-role="page"&gt;
This is my page.
&lt;/div&gt;

这个data-role属性会告诉jQuery Mobile我的内容就是这个页面的内容在工程中。好了，让我们来看看一个简单的完整的jQuery Mobile页面吧：
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Page Title&lt;/title&gt;
&lt;meta name="viewport" content="width=device-width, minimum-scale=1, maximum-scale=1"&gt;
&lt;link rel="stylesheet" href="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css"</a> /&gt;
&lt;script src="<a href="http://code.jquery.com/jquery-1.5.2.min.js&quot;">http://code.jquery.com/jquery-1.5.2.min.js"</a>&gt;&lt;/script&gt;
&lt;script src="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js"</a>&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div data-role="page"&gt;

&lt;p&gt;Oh snap, I'm a mobile developer.&lt;/p&gt;

&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;
你会注意到我们没有写任何的js脚步，我只是用了一些jQuery Mobile 的资源，下面就是生成的页面：
好吧，并不是让人印象深刻，但是让我们看看当我们在页面中添加更多的元素之后会发生什么吧，在我们的页面的内容中我们可以
添加3个可选的节（section）。一个header，一个body，一个footer。和之前一样，我们要添加一些data属性，下面是我们页面的第二版：
<strong>index2.html</strong>

&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Page Title&lt;/title&gt;
&lt;link rel="stylesheet" href="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css"</a> /&gt;
&lt;script src="<a href="http://code.jquery.com/jquery-1.5.2.min.js&quot;">http://code.jquery.com/jquery-1.5.2.min.js"</a>&gt;&lt;/script&gt;
&lt;script src="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js"</a>&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div data-role="page"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;My Header&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;Oh snap, I'm a mobile developer.&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;

我用3个新的div块替换了之前的一段文字。我的第一个div有一个data-role属性的值是header，第二的值是content，第三个是footer，
再来一次，我们没有写任何的js脚本，但是我们现在看这个页面就是下面的样子了：
和你看到的一样，有一个很大的不错的变化。我们的头和尾自动的变得跟头和尾一样的。哈哈

<strong>添加页面:</strong>
当我们的站点有很多的页面的时候，怎么办呢，jQuery Mobile给我们提供了2个比较有意思的方式来添加很多的页面到你的站点。
首先让我们看看怎么怎么在同一个页面中添加其他的pages。

<strong>index3.html</strong>
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Page Title&lt;/title&gt;
&lt;link rel="stylesheet" href="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css"</a> /&gt;
&lt;script src="<a href="http://code.jquery.com/jquery-1.5.2.min.js&quot;">http://code.jquery.com/jquery-1.5.2.min.js"</a>&gt;&lt;/script&gt;
&lt;script src="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js"</a>&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div data-role="page" id="main"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;My Header&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;Oh snap, I'm a mobile developer.&lt;/p&gt;
&lt;p&gt;
Here is a &lt;a href="#page2"&gt;link&lt;/a&gt; to another page.
&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;div data-role="page" id="page2"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;Page Two&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;
Welcome to page 2. Enjoy your stay.
&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;
让我们看看到底发生什么变化了在代码中，你会注意到我们有2个div块是用role为page的。第一个和我们之前的一样。我们加了一个”main“的id。
为了能够让jQuery Mobile验证唯一的page。在我们的页面中，我们用一个链接添加了第二段文章，我用#page2作为链接。这个会告诉jQuery Mobile
在同一个文档里还有第二page。正如你看见的，我给了一个id为page2的div。有头，内容，尾。我们在浏览器中看的时候，第二个会被隐藏。

点击链接，会自动的转换到第二页。

注意返回前一页的的按钮是自动创建的，（当然你可以配置她的。）不写一行js，就能够得到一个移动设备很友好的网站。可以让页和页之间无缝的
切换。而且自动提供导航帮助栏。这样很炫，但是你还是希望把所有的页面都写在一个文档里面。这样的话很快就变得不可管理。
在这里jquery mobile也提供了另外一种方式就是使用ajax来请求另外一个页面，同样会有很炫的页面切换方式。让我们来看看怎么做：

<strong>index4.html</strong>

&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Page Title&lt;/title&gt;
&lt;link rel="stylesheet" href="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css"</a> /&gt;
&lt;script src="<a href="http://code.jquery.com/jquery-1.5.2.min.js&quot;">http://code.jquery.com/jquery-1.5.2.min.js"</a>&gt;&lt;/script&gt;
&lt;script src="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js"</a>&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div data-role="page" id="main"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;My Header&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;Oh snap, I'm a mobile developer.&lt;/p&gt;
&lt;p&gt;
Here is a &lt;a href="#page2"&gt;link&lt;/a&gt; to another page.
&lt;/p&gt;
&lt;p&gt;
Here is a &lt;a href="newpage.html"&gt;link&lt;/a&gt; to a new page.
&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;div data-role="page" id="page2"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;Page Two&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;
Welcome to page 2. Enjoy your stay.
&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;

在我们的模板里有2个链接现在。我们继续让第一个链接到page2.而添加另外一个链接到一个新的页面。mewpage.html。
同样它也是一个简单的链接，但是jquery mobile会自动处理它，现在让我们看看这个<strong>newpage.html</strong>

newpage.html

&lt;div data-role="page"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;The new Page&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;This is my new page!&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;Page Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

正如你看到的，用一个标准的方式来创建一个page。一个data-role为content的div就搞定。再给它添点内容。唯一和之前的页面不同的就是这个页面是在一个新的文件中，
你现在可以在浏览器中试试到底行不行。注意点是如果链接指向到别的域时是不会用ajax请求的。你可以禁用ajax来请求一个页面通过link basis。

<strong>UI小工具</strong>

到现在我们一个专注于页面和基本的导航了。jquery mobile拥有一套的UI小工具，他们能够以同样的方式来工作。
你只需要给普通的html标签添加上data-role属性，jquery mobile就能够自动增强它来适应移动设备的环境让它看上去更加好看，性能更好。
本文不会提到全部，将会演示一下lists。lists能够轻松提供一个菜单类型的导航功能给用户。

index5.html

&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Page Title&lt;/title&gt;
&lt;link rel="stylesheet" href="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css"</a> /&gt;
&lt;script src="<a href="http://code.jquery.com/jquery-1.5.2.min.js&quot;">http://code.jquery.com/jquery-1.5.2.min.js"</a>&gt;&lt;/script&gt;
&lt;script src="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js"</a>&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div data-role="page" id="main"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;My Header&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;

&lt;ul data-role="listview"&gt;
&lt;li&gt;&lt;a href="#page2#"&gt;Page Two&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="newpage.html"&gt;New Page&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;div data-role="page" id="page2"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;Page Two&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;
Welcome to page 2. Enjoy your stay.
&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;

我们页面的内容已经换成了UL标记，注意给它添加一个data-role为listviews的属性。这样就会告诉jquery mobile这个你要解释成一个lsit
view。然后它的外观让人感觉到很帅气：

注意list的item都是宽度都是100%的，注意默认的箭头都在右边的。所有的这些都是data-role给你完成的，让我们在把它给修改下：
<strong>index6.html</strong>

&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;Page Title&lt;/title&gt;
&lt;link rel="stylesheet" href="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.css"</a> /&gt;
&lt;script src="<a href="http://code.jquery.com/jquery-1.5.2.min.js&quot;">http://code.jquery.com/jquery-1.5.2.min.js"</a>&gt;&lt;/script&gt;
&lt;script src="<a href="http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js&quot;">http://code.jquery.com/mobile/1.0a4/jquery.mobile-1.0a4.min.js"</a>&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;div data-role="page" id="main"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;My Header&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;

&lt;ul data-role="listview" data-inset="true"&gt;
&lt;li&gt;&lt;a href="#page2#"&gt;Page Two&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;&lt;a href="newpage.html"&gt;New Page&lt;/a&gt;&lt;/li&gt;
&lt;/ul&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;div data-role="page" id="page2"&gt;

&lt;div data-role="header"&gt;
&lt;h1&gt;Page Two&lt;/h1&gt;
&lt;/div&gt;

&lt;div data-role="content"&gt;
&lt;p&gt;
Welcome to page 2. Enjoy your stay.
&lt;/p&gt;
&lt;/div&gt;

&lt;div data-role="footer"&gt;
&lt;h4&gt;My Footer&lt;/h4&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;/body&gt;
&lt;/html&gt;

我们改了哪里呢？只是添加了一个data-inset=‘true’的属性，让我们再来看看变成什么样子了：
看见好看的圆角和内间距了吗？这个只是jquery mobile包中的众多的listview中的一个。

接下来干什么？
这个文章只是简单的讲了讲jquery mobile开发基础，更多的还是去这里学习吧：(<a href="http://jquerymobile.com/demos/1.0a4.1/)">http://jquerymobile.com/demos/1.0a4.1/)</a>
