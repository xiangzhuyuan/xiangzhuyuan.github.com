---
title: Facebook使用BitTorrent来部署他们的代码
author: mathewxiang
layout: post
permalink: >
  /2012/03/facebook%e4%bd%bf%e7%94%a8bittorrent%e6%9d%a5%e9%83%a8%e7%bd%b2%e4%bb%96%e4%bb%ac%e7%9a%84%e4%bb%a3%e7%a0%81/
categories:
  - 默认
---
<http://torrentfreak.com/facebook-uses-bittorrent-and-they-love-it-100625/>

BitTorrent设计的目的就是能够在很短的时间内传送大文件到很多个目的地.他们不仅仅只是让一般用户能够用来下载电影或者音乐,而是同样能够让企业从中获益.Facebook就在使用Bittorrent来很快的部署自己的代码到全球的服务器上.大访问量的服务提供商例如Facebook他们需要上千台的服务器来提供服务给用户.这样他们就必须在很短的时间内让用户不管是什么地方的都能够访问到最新的服务,就需要每一台服务器上面的代码都是最新的.

<!--more-->

通过访问来自Facebook的系统工程师部门的Tom Cook,了解到他们刚开始每天的代码更新都会遇到很多的问题,知道他们发现了Bittorrent,他在一次大会的发言中提到后来他们是如何使用Bittorrent来高效的部署自己的服务的.

他说,Bittorrent真的很赞,太棒了,它能够让我们省去很多过去需要担忧的问题.通过使用他们的Bittorrent驱动的分布式发布系统,能够在一分钟内搞定上百兆的代码到上万台的服务器上.在facebook内部,每一台服务器都相当于一个Peer,这样就能够很容易的得到最新的代码.如果不是这样的话,那发布往往需要好几个小时.

Facebook并不是为一个使用Bittorrent技术来更新代码的大访问提供商,twitter同样也采用这样的方式来更新部署.名字叫做Murder.它是一个基于BitTornado bittorrent客户端来实现的.这个客户端是开源的.