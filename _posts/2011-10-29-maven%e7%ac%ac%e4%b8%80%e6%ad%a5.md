---
title: maven第一步
author: mathewxiang
layout: post
permalink: /2011/10/maven%e7%ac%ac%e4%b8%80%e6%ad%a5/
categories:
  - 编程,代码
tags:
  - apache
  - java
  - Maven
---
最近一直在纠结于maven的一些使用.很多时候都忘记了对于目前的我来说写代码写好代码才是关键的而不是纠结于这个pom tool才是,不过我这个人对于任何接触的事物还是喜欢搞清楚来由的习惯,所以我还是希望能够花点时间多了解一下的,毕竟我离开java有段时间了,而对于java来说在开发中的各种XML文件的配置总是让人头大,其实造成这个的终究原因还是java那个时候的热得发烫,而现在很多时候我已经不想再投身于java或者.net阵营了.因为对于那些经常被提到的大项目什么企业级的,动不动就提到大数据量并发什么的说辞我依然没有什么丝毫挑战的兴趣,或者我压根就没有能力碰到或者去解决这些issues.我希望我能够拿一个开源的脚本程序语言来解决生活中一些实际的问题,这些才是我的价值所在,而不是整天在那里思考如何才能够解决大并发量的数据问题.

不过既然混口饭吃还是要有java或者.net防身的好.就我目前的看法java在今后的若干年是会一直存在下去的.因为从热的发烫的时候起很多的领域已经被它占领,而不再开发新的光维护就会需要很多的技术人员的.这个时代我相信会很持久的.就好比那个[COBOL][1]语言,现在还有很多日企在维护,在内地很多程序员还需要学习他来维护他,给日本人干活.没有办法,得吃饭.

所以还是多会点东西比较靠谱,不说能够在某个领域多大牛,其实也就那回事.get things done! 才是解!

<!--more-->

下面来看看maven是怎么跑的吧…

1,首先去apache下载个zip的包[Maven 3.0.3 (Binary zip)][2].

2, 解压它,位置随意.下面假设你用的win7,接着就是添加环境变量了.有2种方式:这里需要提醒的就是系统必须有java的环境变量,因为maven就是用java写的.先看看系统有没有java环境变量,不过我想都有.

      (1)去[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.yyxzy.org/wp-content/uploads/2011/10/image_thumb.png" width="244" height="237" />][3]添加

      (2)就是命令行方式:这样不方便的就是每次都要添加的.

<pre class="shell">C:\Users\tobrien &gt; set M2_HOME=c:\Program Files\apache-maven-3.0.3<br />C:\Users\tobrien &gt; set PATH=%PATH%;%M2_HOME%\bin</pre>

3, 看看成功了没有. <pre style="width: 550px; height: 143px" class="shell">d:\workspace\starter\target&gt;mvn -v
Apache Maven 3.0.3 (r1075438; 2011-03-01 01:31:09+0800)
Maven home: C:\maven\apache-maven-3.0.3\bin\..
Java version: 1.7.0, vendor: Oracle Corporation
Java home: C:\Program Files\Java\jdk1.7.0\jre
Default locale: zh_CN, platform encoding: GBK
OS name: "windows 7", version: "6.1", arch: "x86", family: "windows"</pre>

4, 配置Maven.在maven的目录下有个settings.xml 这个地方有几个作用,1就是指定你将来下载的jar包放哪里.2就是如果上网需要代理还需要在这里填写.3还有就是还可以指定自己的jar 的库的地址,这样就是不光可以去下载一些开源的包还可以添加自己其他工程的jar包.还有就是这个配置文件一般都有好几个,因为一般maven都是部署到服务器上的,很多用户共享,你可以有你自己的配置,所以一般都要复制一份到自己的目录下,就是 <pre class="shell">C:\Users\Administrator\.m2</pre>

5, 差不多让我们来看看用maven建一个小demo吧.这是最简单的目录了,就是创建一个工程,我们这里没有指定到底是哪个类型的工程,在apache哪里的库有很多的pom类型的,随着时间的推移会越来越多,你可以去那里得到一个列表的.我们只是看看到底是怎么回事,其他的以后再说.键入以下命令: <pre class="shell">d:\workspace&gt;mvn archetype:generate</pre>

6,当你的回车跑起来时会显示正在从远程回去一个pom库的列表,完成之后会等待让你输入你想要的库类型.这个时候我们不输入任何东西,直接回车. <pre style="width: 547px; height: 559px" class="shell">451: remote -&gt; org.scala-tools.archetypes:scala-archetype-simple (The maven-scala-plugin is used for
 compiling/testing/running/documenting scala code in maven.)
452: remote -&gt; org.slf4j:slf4j-archetype (The slf4j Archetype)
453: remote -&gt; org.sonatype.flexmojos:flexmojos-archetypes-application (-)
454: remote -&gt; org.sonatype.flexmojos:flexmojos-archetypes-library (-)
455: remote -&gt; org.sonatype.flexmojos:flexmojos-archetypes-modular-webapp (-)
456: remote -&gt; org.sonatype.nexus.archetypes:nexus-plugin-archetype (-)
457: remote -&gt; org.springframework.osgi:spring-osgi-bundle-archetype (Spring OSGi Maven2 Archetype)
458: remote -&gt; org.springframework.ws:spring-ws-archetype (Spring Web Services Maven2 Archetype.)
459: remote -&gt; org.syncope:syncope-archetype (-)
460: remote -&gt; org.trailsframework:trails-archetype (-)
461: remote -&gt; org.trailsframework:trails-secure-archetype (-)
462: remote -&gt; org.tynamo:tynamo-archetype (-)
463: remote -&gt; org.wicketstuff.scala:wicket-scala-archetype (-)
464: remote -&gt; org.wicketstuff.scala:wicketstuff-scala-archetype (Basic setup for a project that com
bines Scala and Wicket,
                depending on the Wicket-Scala project. Includes an example Specs
                test.)
465: remote -&gt; org.wikbook:wikbook.archetype (-)
466: remote -&gt; org.xwiki.rendering:xwiki-rendering-archetype-macro (Make it easy to create a maven p
roject for creating XWiki Rendering Macros.)
467: remote -&gt; org.zkoss:zk-archetype-component (The ZK Component archetype)
468: remote -&gt; org.zkoss:zk-archetype-webapp (The ZK wepapp archetype)
469: remote -&gt; ru.circumflex:circumflex-archetype (-)
470: remote -&gt; se.vgregion.javg.maven.archetypes:javg-minimal-archetype (-)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 143:</pre>

<pre style="width: 548px; height: 233px" class="shell">Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 143:
Choose version:
1: 1.0-alpha-1
2: 1.0-alpha-2
3: 1.0-alpha-3
4: 1.0-alpha-4
5: 1.0
6: 1.1
Choose a number: 6:</pre>

7, 之后会出现让你选择版本的提示,其实吧,我们没有输入类型的序号,默认的就是一个maven的starter例子.已经有好几个版本了.我们选择6. 接着还会出现让你的输入groupId,其实就是所谓的公司的名字.然后就是artifactId,其实就是产品的名字.接着是版本号,直接回车就是了.然后是包名. 回车会出现刚才你输入的信息的确认.直接Y就ok. <pre class="shell">Choose a number: 6: 6
Define value for property 'groupId': : xiang
Define value for property 'artifactId': : firstmavendemo
Define value for property 'version':  1.0-SNAPSHOT: :
Define value for property 'package':  xiang: : com.demo
Confirm properties configuration:
groupId: xiang
artifactId: firstmavendemo
version: 1.0-SNAPSHOT
package: com.demo
 Y: : Y</pre>

8,就是根据你刚才的输入信息来创建工程了.最后提示你成功了. <pre style="width: 548px; height: 400px" class="shell">[INFO] ----------------------------------------------------------------------------
[INFO] Using following parameters for creating project from Old (1.x) Archetype: maven-archetype-qui
ckstart:1.1
[INFO] ----------------------------------------------------------------------------
[INFO] Parameter: groupId, Value: xiang
[INFO] Parameter: packageName, Value: com.demo
[INFO] Parameter: package, Value: com.demo
[INFO] Parameter: artifactId, Value: firstmavendemo
[INFO] Parameter: basedir, Value: d:\workspace
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] project created from Old (1.x) Archetype in dir: d:\workspace\firstmavendemo
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 3:13.291s
[INFO] Finished at: Sat Oct 29 23:15:28 CST 2011
[INFO] Final Memory: 7M/22M
[INFO] ------------------------------------------------------------------------

</pre>

9, 编译工程. <pre style="width: 545px; height: 253px" class="shell">d:\workspace\firstmavendemo&gt;mvn install
[INFO] Scanning for projects...
...... 
[INFO] Installing d:\workspace\firstmavendemo\pom.xml to C:\Users\Administrator\.m2\repository\xiang \firstmavendemo\1.0-SNAPSHOT\firstmavendemo-1.0-SNAPSHOT.pom 
[INFO] ------------------------------------------------------------------------ 
[INFO] BUILD SUCCESS [INFO] ------------------------------------------------------------------------ 
[INFO] Total time: 10.080s 
[INFO] Finished at: Sat Oct 29 23:17:29 CST 2011 [INFO] Final Memory: 11M/27M 
[INFO] ------------------------------------------------------------------------ 

</pre>

10, 让我们看看到底是什么吧. <pre class="shell">d:\workspace\firstmavendemo&gt;cd target

d:\workspace\firstmavendemo\target&gt;java -cp firstmavendemo-1.0-SNAPSHOT.jar com.demo.App
Hello World!
</pre>

 [1]: http://zh.wikipedia.org/zh/COBOL
 [2]: http://maven.apache.org/download.html
 [3]: http://www.yyxzy.org/wp-content/uploads/2011/10/image.png