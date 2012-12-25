---
layout: post
title: 让ruby 在 notepad++ 上飞一会儿
date: 2011-05-11 10:39
comments: true
categories: []
---
<h2><span class="Apple-style-span" style="font-size:13px;"><strong>1.notepad++ 简单介绍</strong></span></h2>
<h4>notepad++可能大家都不陌生吧，它是一个很强大的编辑器，它的特性是，开放源代码， 支持多语言的，但是它目前只能运行在Windows平台下（缺点，都4.6的版本，还没看到能在其他os上的版本）。大家用过ruby下自带的SciTE吧，它使用的是 Scintilla edit component ，其实官方网站上说 SciTE本来只是作为Scintilla edit component 推广用的一个Demo。呵呵，notepad++也使用Scintilla edit component,所以感觉像是2兄弟。</h4>
notepad++的具体特征我就不详细说了，大家可以去网站看看：
<a href="http://notepad-plus.sourceforge.net/uk/site.htm">http://notepad-plus.sourceforge.net/uk/site.htm</a>
<h4><strong>2.ruby 在 notepad++ 上飞翔</strong>
在这之前，我建议大家下载 最新版本4.6, 压缩的包只有1M多。我是下载zip，解压就可以用的（够绿色）。</h4>
启动notepad++:

<img src="http://lh6.google.com/lemonzc777/R3Hh6dGXqKI/AAAAAAAAABU/zfxzXhP-8ho/p1.JPG?imgmax=512" alt="" />

创建一个新rb文件

<img src="http://lh6.google.com/lemonzc777/R3Hh6dGXqLI/AAAAAAAAABc/qdmWfMU5nGc/p2.JPG?imgmax=512" alt="" />

点击菜单上的Run?

no, no, no 在这里是不行的，不像SciTE, 我们得需要来配置下一个非常棒的插件。

去这个地方:  <a href="http://sourceforge.net/projects/npp-plugins/files/">http://sourceforge.net/projects/npp-plugins/files/</a>
<h4><strong>3.军刀 NppExec 插件</strong>
瑞士的军刀大家都晓得，比着是方便，好用的工具吧。 我们notepad++下面的NppExec也算是一把军刀呢。它的功能就是执行代码，不过如何执行，请听我下面慢慢讲解.</h4>
小心按坏F6, :), 按下快键 F6 ，将出现下面窗口（NppExec),在窗口中输入:
ruby $(FULL_CURRENT_PATH)  (<strong><span style="text-decoration:underline;">一定要到当前的目录</span></strong>)

<img src="http://lh6.google.com/lemonzc777/R3Hh6dGXqMI/AAAAAAAAABk/qbEQZL1yeAk/p3.JPG?imgmax=512" alt="" />

点击ok,  啊哦，ruby: No such file or directory -- new (LoadError)

<span style="text-decoration:underline;"><strong>(在运行之前一定要保存,才可以看见当前的代码的效果哦,人家是读文件来解释的</strong></span>)
呵呵 老兄你忘了保存(注：不要保存在有空格的目录下），save and ok again, 结果出来了。

<img src="http://lh6.google.com/lemonzc777/R3Hh6dGXqNI/AAAAAAAAABs/b4lue1IcjHo/p4.JPG?imgmax=512" alt="" />

<strong>随后，我们可以保存这个Command 为Ruby Run, 这样以后就直接按F6点ok（如果一建就能执行默认的command就好了）。</strong>
<h4><strong>4. Rails 在 notepad++ 上奔跑</strong>
除了NppExec插件，我们还有Light Explorer 插件（这些插件都是默认安装在npp 4.6上的）. ok, 找到你的project directory path, 按F6, 我们创建一个GO TO PROJECT(我暂时只想到这个name， Save Command的时候输入这个name), 创建一个Command, 脚本为：CD X:xxxxxxxxx (你的rails的project根目录)。  ok 执行一下。</h4>
<img src="http://lh3.google.com/lemonzc777/R3Hh6tGXqOI/AAAAAAAAAB0/qfzecFGAlKQ/p5.JPG?imgmax=576" alt="" />

<img src="http://lh3.google.com/lemonzc777/R3HiKtGXqPI/AAAAAAAAACA/wXv3FVcviKc/p6.JPG" alt="" />

下面，我们创建一个Run Server 的Command,  按F6, 脚本: ruby script/server

<img src="http://lh4.google.com/lemonzc777/R3HiK9GXqQI/AAAAAAAAACI/g4WuEWA9ObM/p7.JPG" alt="" />
<img src="http://lh5.google.com/lemonzc777/R3HoENGXqSI/AAAAAAAAACY/y3S9uNqZFok/p9.JPG" alt="" />
<img src="http://lh5.google.com/lemonzc777/R3HoENGXqSI/AAAAAAAAACY/y3S9uNqZFok/p9.JPG" alt="" />

如何快捷，批量的创建和删除Command(界面上没有delete按钮)：
你也可以在npp的 pluginsConfig 目录下找到 npes_saved.txt 和npes_temp.txt 文件，打开它们，自己看了哈。下面是我的 npes_save.txt：

::Ruby Run
ruby $(FULL_CURRENT_PATH)

::GO to Project Directory
CD D:tempMy DocumentsNetBeansProjectsRailsDemo

::Run Server
ruby script/server

::Rails Destroy Template
ruby script/destroy --help

::Rails Generate Template
ruby script/generate --help

补充： pluginsdocNppExec.txt 有详细的关于NppExec的说明。
<h4><strong>5. *.erb  在notepad++ 漫步</strong></h4>
<h4>当用npp打开erb的时候，npp把它当作一般的normal text格式文件，所以没有语法高亮，不过你可以点击menu－&gt;language-&gt;html，马上*.erb就可以漫步了。</h4>
<img src="http://lh4.google.com/lemonzc777/R3HiK9GXqRI/AAAAAAAAACQ/zgX_318JSA4/p8.JPG?imgmax=400" alt="" />

<strong>总结，notepad++上还有好一些插件，感觉还不错， 如果不喜欢java ide的同学，喜欢速度快的ide的同学们，不妨考虑使用一下这种方式来develop （应该不光是ruby,其他语言也一样可以配置）</strong>

<del>共同学习：Functions List这个插件应该是类是自动完成，不过我在pluginsAPIs目录下 创建了一个erb.api,添加了一些常用的字串， 但打开erb文件还是无法在Functions list中看到。我已经给这个插件作者发送了一份email，等待他的答复</del>

<del>lemonzc</del>
<del> Symbio Chengdu</del>
<h1>本文转自javaeye,经过一些修改</h1>
