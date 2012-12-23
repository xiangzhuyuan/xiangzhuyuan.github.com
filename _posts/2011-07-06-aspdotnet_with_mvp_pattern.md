---
title: 我理解的mvp模式
author: mathewxiang
layout: post
permalink: /2011/07/aspdotnet_with_mvp_pattern/
categories:
  - '.net C#开发'
tags:
  - asp.net
  - command
  - mediator
  - mvp
---
在开发网页程序的时候最头疼的就是测试.tdd.其实tdd我还不是很懂,在开发中也没有真正去做.不过现在很流行.至少国外的很多公司都是在做这样的事情.特别是小而且强悍的团队,我期望能够加入到这样的团队中去.我要为此奋斗!有强人说过,招人就要找聪明而且能够解决问题的人.我就是这样的或者即将成为这样的人.

其实网页开发有很多,开发网页时间久了就不会在去担心刚开始时遇到的很多担心的问题,比如说是要掌握很多的东西,从后台的代码到前段的代码.虽说现在又很多企业都是详细分工了,可是历史的车轮总是很缓慢的.或者就是祈求老板不要那么浮躁吝啬,多招点人,多在如果提高生产效率怎么赚取用户更多的钱上下功夫而不是把很多心思都放在很单纯的程序员身上.或者就是我们人太好太帅总招来不经意的目光.

对于一个长期发展的网站来说,架构总是很重要,当然我还没有到这个地步,但是人人都说,我也就相信了.所谓架构就是各种前人高深的思想的具体化,各种设计模式,各种分离…总得来说实践起来很繁琐,说繁琐其实是很合理的.为了以后不让自己看着自己的成果而哭泣,总是希望一开始就选对了路.谨慎.现在说说mvp模式.我最近在codeproject上所搜关于mvp模式的文章,最早好像是在06年?出现的版本.为什么到现在了还没有让很多的人广泛的使用呢.其实这个模式比较伟大.以至于很多人都用不到.作为一个简单的产品来说,真是没有必要,谁知道这个产品什么时候就夭折了呢.老板也是想在一定时间内拿到产品.而人家不会关心你用了什么架构,是不是足够牛逼能够抵抗万年一遇的扩展再重构呢?在这里最让人不熟悉的就是这个P.当然不是几p中的那个p了.p=Presenter.他好比就是一个足够牛逼的男人,啥样的女子(其实还是有类型可以总结的)来了都能够轻松应付.因为他能够实现你所想要的.给你提供你所必须或者不需的.

可是大家或许都错了.其实他的心就是一个.在他的内心深处只有一个她=**I\***|View**,只要你给出你想要的,我就给你实现.当我足够强大的时候你就可以幻化成若干仿佛有她的味道的任何人.呵呵.我轻松应对.多的不说了,我先上代码.

***<u></u>*** 

1,首先讲到的就是她.其实就是对于用户来说,他所想要看到的一些数据,就是生产一个页面所需要的数据.

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="IView" src="http://www.yyxzy.org/wp-content/uploads/2011/07/image_thumb.png" width="279" height="119" />][1]

2,就是主要的Presenter了.其实他就是Model和IView之间的一个传达,他不用和view打交道,而是完全操作IView

[<img style="display: inline" title="image" alt="Presenter" src="http://www.yyxzy.org/wp-content/uploads/2011/07/image_thumb1.png" width="461" height="399" />][2]

3,继承自IView的page.在这里,你须去继承Iview,这样才能够具有她的味道,然后就可以获得你想要的了.当你实现接口后就要实现那些属性和EventHandler.而这些具体的实现已经在Presenter里实现了,所以你只需要完成那些必须的穿衣打扮就ok’

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="page" src="http://www.yyxzy.org/wp-content/uploads/2011/07/image_thumb2.png" width="434" height="555" />][3]

 

总结:

这个实在是太简单的讲述了,对于一个只能手机网络push文章的我来说,Kb太重要了.对于这个模式还有很多东西需要学习,特别是其中使用的3个主要的设计模式(observer,mediator,command)其中的思想还是我一时半会不能够熟练掌握的,待我慢慢学习吧.

 [1]: http://www.yyxzy.org/wp-content/uploads/2011/07/image.png
 [2]: http://www.yyxzy.org/wp-content/uploads/2011/07/image1.png
 [3]: http://www.yyxzy.org/wp-content/uploads/2011/07/image2.png