---
layout: post
title: 学点东西
date: 2011-11-15 20:55
comments: true
categories: []
---
对于网站的性能,对于网页的精致一定要有偏执的要求!不管现在是否和你有关,还是以后属于自己的网站一定要有这个精神才行.

<img style="display: block; margin-right: auto; margin-left: auto;" src="http://www.yyxzy.org/wp-content/uploads/2011/11/wpid-1321361570381.jpg" alt="高性能网站建设指南" />

今天我主要是把css的background-position给学习了下.其实在上面的<a href="http://book.douban.com/subject/3132277/">《高性能网站建设指南》</a>指南中就说了对于一个网页的渲染并不是常常所说的完全大部分的时间都花在了很数据库交互取得数据,而是由于一个浏览器载入一个页面需要下载很多的资源文件阻塞造成的,我没有做过测试.你管你信不信,我信.因为<a href="http://stevesouders.com/">他</a>是大家.没有理由不信.当然并不是说写代码就不要太注意性能了,我们同样需要努力.所以我们的解决方案就是尽可能的减少浏览器请求的资源文件数量减少同时下载造成的阻塞.而对于图片的处理就是<a href="http://stevesouders.com/hpws/sprites.php">CSS Sprites</a> .也就是把同一个页面的图片放在一张图片上,然后利用css来显示具体的图片在具体的位置;而这个时候就要用到background-position,而更多的在就要用到它的负值了.到底是什么作用呢?下面来看看:

<a href="http://www.yyxzy.org/wp-content/uploads/2011/11/background-position.jpg"><img class="alignnone size-full wp-image-754" title="background-position" src="http://www.yyxzy.org/wp-content/uploads/2011/11/background-position.jpg" alt="background-position" width="607" height="506" /></a>

&nbsp;

在上面的图片中显示的是在一个div上设置背景图,而一般位置的计算就是从div的左上角(0,0)开始往右往下开始像素数递增.如果我们这个时候想要把图上的红点作为div左上角的开始,我们应该怎么办?很简答就是我们要把图片往左上移动.这个移动也就是要改变css中的background-position 的值,刚才我说了在往右下移动的时候像素数是递增的,所以往左上移动就得减了啊.这个时候就出现所谓的负值了.
<pre class="shell">.n_header_inner a.logo {
	background:url(/res/v3/img/logo.gif) 0 0 no-repeat;
	display:block;
	overflow:hidden;
	width:180px;
	height:80px; 
	text-indent:-999em;
	float:left;
}
.n_header_inner a.logo:hover {
	background-position:-50px -50px;
}</pre>
这样就能够把那个红点作为div的左上角起点了.原来一切都是这么有规则的.其实一切很简单,但是就看你到底想不想做到最好.
