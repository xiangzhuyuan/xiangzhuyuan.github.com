---
title: 使用Mustache模板系统
author: mathewxiang
layout: post
permalink: /2012/03/%e4%bd%bf%e7%94%a8mustache%e6%a8%a1%e6%9d%bf%e7%b3%bb%e7%bb%9f/
categories:
  - 兴趣爱好
  - 编程,代码
tags:
  - JavaScript
  - Mustache
  - PHP
---
*   <https://github.com/janl/mustache.js> 
    *   <http://mustache.github.com/mustache.5.html> 
        *   <http://mustache.github.com/></ul> 
        前段时间接触了Mustache这个十分简单的模板系统,感觉挺不错的.正好我的那个记账的小站上还缺点功能,一直没有兴趣来实现,正好,练练手.
        
        *   一个htm页面.发送ajax请求. 
            *   一个php文件,用来返回json数据. 
                *   一个模板文件.用来和json生成页面到上面提到的主页面中.</ul> 
                其实之前也用到过ajax请求得到json数据.然后在js中一个个填充到页面中,只不过这样的页面代码看起来有点丑,而这个mustache正好能够帮助我们完成这个任务.
                
                先看看这个第一个htm页面:
                
                [<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.yyxzy.org/wp-content/uploads/2012/03/image_thumb.png" width="963" height="474" />][1]
                
                然后看看那个php代码:
                
                [<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.yyxzy.org/wp-content/uploads/2012/03/image_thumb1.png" width="892" height="296" />][2]
                
                然后这样就能够实现我对于往月花销分类的一个简单分类统计.
                
                没有状态就靠兴趣好玩支撑了!

 [1]: http://www.yyxzy.org/wp-content/uploads/2012/03/image.png
 [2]: http://www.yyxzy.org/wp-content/uploads/2012/03/image1.png