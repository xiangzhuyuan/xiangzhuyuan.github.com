---
layout: post
title: 使用Mustache模板系统
date: 2012-03-05 21:08
comments: true
categories: []
---
<ul> <li><a href="https://github.com/janl/mustache.js">https://github.com/janl/mustache.js</a>  <li><a href="http://mustache.github.com/mustache.5.html">http://mustache.github.com/mustache.5.html</a>  <li><a href="http://mustache.github.com/">http://mustache.github.com/</a></li></ul> <p>前段时间接触了Mustache这个十分简单的模板系统,感觉挺不错的.正好我的那个记账的小站上还缺点功能,一直没有兴趣来实现,正好,练练手.</p> <ul> <li>一个htm页面.发送ajax请求.  <li>一个php文件,用来返回json数据.  <li>一个模板文件.用来和json生成页面到上面提到的主页面中.</li></ul> <p>其实之前也用到过ajax请求得到json数据.然后在js中一个个填充到页面中,只不过这样的页面代码看起来有点丑,而这个mustache正好能够帮助我们完成这个任务.</p> <p>先看看这个第一个htm页面:</p> <p><a href="http://www.yyxzy.org/wp-content/uploads/2012/03/image.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.yyxzy.org/wp-content/uploads/2012/03/image_thumb.png" width="963" height="474"></a></p> <p>然后看看那个php代码:</p> <p><a href="http://www.yyxzy.org/wp-content/uploads/2012/03/image1.png"><img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.yyxzy.org/wp-content/uploads/2012/03/image_thumb1.png" width="892" height="296"></a></p> <p>然后这样就能够实现我对于往月花销分类的一个简单分类统计.</p> <p>没有状态就靠兴趣好玩支撑了!</p>
