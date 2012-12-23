---
title: 'git&amp;github ABC'
author: mathewxiang
layout: post
permalink: /2012/02/gitgithub-abc/
categories:
  - 编程,代码
tags:
  - git
  - github
---
l 1,注册Git

如果你到了这个页面,我想你也就是一个完全的新手对于git和github.

这个手册将会告诉你一些基础知识和解释一些基本的工作原理;

首先,下载安装git<!--more-->

github的核心是一个开源的版本控制系统,叫做Git*,是Linux的作者开发的,git对于你本地出现的一些和github有关的问题负责.

*如果你已经知道什么是git了,那就去这个地方:http://progit.org/book/ch1-3.html

l 1,下载并安装最新的git for windows(http://code.google.com/p/msysgit/downloads/list)

每一步使用默认的设置.

[<img style="display: inline; border: 0px;" title="wps_clip_image-2871" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image2871_thumb.png" alt="wps_clip_image-2871" width="528" height="478" border="0" />][1] [<img style="display: inline; border: 0px;" title="wps_clip_image-32432" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image32432_thumb.png" alt="wps_clip_image-32432" width="372" height="585" border="0" />][2]

l 配置你的SSH

我们使用SSH keys来建立一个安全的连接在你的电脑和github之间.配置他们很容易,但是需要一些简单的步骤.

为了确保你生成一个新的key,你需要确定他到底存不存在,首先,你需要打开git bash.在开始菜单中的git文件夹下.

[<img style="display: inline; border: 0px;" title="wps_clip_image-9851" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image9851_thumb.png" alt="wps_clip_image-9851" width="244" height="140" border="0" />][3]

1.查看你的ssh key,如果存在直接跳到第四步

$ cd ~/.ssh

首先,我们需要查看你电脑上是否已经存在ssh key

#如果提示此目录不存在那就继续第二步或者到第三步

2.备份或者移除已经存在的ssh key

如果已经存在一个ssh的目录,那就要备份一个或者删除他,

[<img style="display: inline; border: 0px;" title="wps_clip_image-161" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image161_thumb.png" alt="wps_clip_image-161" width="244" height="45" border="0" />][4]

3.生成一个新的ssh key

通过输入下面的一段,命令来生成新的ssh key.我们希望得到一些默认的设置来保存ssh key

[<img style="display: inline; border: 0px;" title="wps_clip_image-13579" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image13579_thumb.png" alt="wps_clip_image-13579" width="244" height="41" border="0" />][5]

这个时候需要密码:

[<img style="display: inline; border: 0px;" title="wps_clip_image-26862" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image26862_thumb.png" alt="wps_clip_image-26862" width="244" height="27" border="0" />][6]之后你会看到下面的重要的输出:

[<img style="display: inline; border: 0px;" title="wps_clip_image-19667" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image19667_thumb.png" alt="wps_clip_image-19667" width="244" height="133" border="0" />][7]大概的意识就是说你的认识信息已经保存在了上的/user/your\_user\_directory/.ssh/id\_rsa中,你的公钥信息保存在了/user/your\_user\_directory/.ssh/id\_rsa.pub中.

4.添加你的ssh key到你的github帐户中.

点击账户设置,选中ssh公钥,然后把公钥信息贴进去.

[<img style="display: inline; border: 0px;" title="wps_clip_image-2468" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image2468_thumb.png" alt="wps_clip_image-2468" width="208" height="244" border="0" />][8]

点击 add key

5.测试是否成功

为了查看你是否能够通过ssh连接到github.我们需要运行下边的命令:

[<img style="display: inline; border: 0px;" title="wps_clip_image-9250" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image9250_thumb.png" alt="wps_clip_image-9250" width="244" height="19" border="0" />][9]

会告诉你:

[<img style="display: inline; border: 0px;" title="wps_clip_image-647" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image647_thumb.png" alt="wps_clip_image-647" width="244" height="41" border="0" />][10]

别担心,输入 yes

[<img style="display: inline; border: 0px;" title="wps_clip_image-15277" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image15277_thumb.png" alt="wps_clip_image-15277" width="244" height="28" border="0" />][11]

l 配置你的信息

现在我们已经安装好了git,还有配置好了github给公钥,是时候来配置自己的信息了.

1.设置自己的名称,和邮件地址

Git跟踪你的每一个提交通过用户的名称和email.另外,我们使用这个信息来匹配你的github账户.输入下面的命令来实现这个步骤:用你的自己的名字和email代替命令中的名称和email:

[<img style="display: inline; border: 0px;" title="wps_clip_image-14703" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image14703_thumb.png" alt="wps_clip_image-14703" width="244" height="26" border="0" />][12]

2.设置你的github token.

一些工具不会通过ssh来连接到github,为了能够正确的使用这些工具,你需要找到并配置你的API token.

在你的github账户设置中,有一个account admin.

[<img style="display: inline; border: 0px;" title="wps_clip_image-4603" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image4603_thumb.png" alt="wps_clip_image-4603" width="244" height="114" border="0" />][13]

运行下面的命令,用你的github用户名和token代替他们.

[<img style="display: inline; border: 0px;" title="wps_clip_image-27281" src="http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image27281_thumb.png" alt="wps_clip_image-27281" width="244" height="28" border="0" />][14]

注意:如果你修改了密码,token将会被更新.

最后,开始和大家协同工作吧!

恭喜, git和github已经安装配置好了.接下来你要做点什么呢?

l 2,创建一个仓库

l 3,关注一个项目

l 4,和他人交流

l

 [1]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image2871.png
 [2]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image32432.png
 [3]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image9851.png
 [4]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image161.png
 [5]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image13579.png
 [6]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image26862.png
 [7]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image19667.png
 [8]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image2468.png
 [9]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image9250.png
 [10]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image647.png
 [11]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image15277.png
 [12]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image14703.png
 [13]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image4603.png
 [14]: http://www.yyxzy.org/wp-content/uploads/2012/02/wps_clip_image27281.png