---
title: 做例子还是要检查完了再发布的啊!
author: mathewxiang
layout: post
permalink: /2011/10/com-ibatis-common-jdbc-exception-nestedsqlexception/
categories:
  - 编程,代码
tags:
  - ibatis
---
今天在apache的目录上down了一个ibatis-2.3.4.726.zip ,里面有sample,那就跑跑看吧,可是在运行的时候还是报错了.  
我想很多人曾经要到了这个问题,或者很多想要用ibatis的人从开始的时候遇到这个问题就放弃了,这个错误真是犯的很低级啊!  
心想为什么呢?就一个劲儿找啊!而报的错就是sql语句有问题,而往往总是不去关注最有可能发生问题的地方,而是一个劲儿在别处找,或者就是不仔细看报错的内容,最终就是浪费时间!  
我估计他2.*的包里都会有这个问题.问题出在哪里呢?就是这个地方: