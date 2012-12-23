---
title: 开始学习Spring Roo第一步(2)
author: mathewxiang
layout: post
permalink: >
  /2011/11/%e5%bc%80%e5%a7%8b%e5%ad%a6%e4%b9%a0spring-roo%e7%ac%ac%e4%b8%80%e6%ad%a52/
categories:
  - 默认
---
接上一篇: [开始学习Spring Roo第一步(1)][1]

——

到这里，我们已经安装了Hibernate来为我们的工程提供对象关系映射支持。  
Hibernate是Roo当前支持的ORM的三个中的其中一个。另外还有EclipseLink和OpenJPA。  
我们选了当前很流行的Hypersonic in-memory数据库作为我们的目标数据库。  
在Roo的开发过程中使用Hypersonic是很方便的。因为他不需要开发人员安装并配置产品数据库。

当你已经准备好测试并且安装你的应用时，可以重复jpa setup。这个时候你可以重新制定数据库甚至不同的ORM。  
Roo提供TAB完成功能当你在配置产品的数据库时，例如Postgres，MySQL，Mirosoft SQL Server，Oracle，DB2，Sybase，  
H2，Hypersonic还有更多。

<!--more-->

另外一个重要的步骤就是编辑SRC\_MAIN\_RESOURCES/META-INF/persistence.xml，修改你的JPA支持的DDL（shema 管理）配置  
这样他就会在重启应用之后提前连接到数据库。同时，Roo还在文件里以注释的方式提供了一个完整可用的JPA配置的列表。  
注意的是，默认的在每次重启它的时候JPA会情况所有的数据库表。这点需要你去修改设置。

注意：Oracle和DB2的JDBC驱动目前在公共的maven库里还没有。Roo会安装标准的依赖为这些驱动，这个时候你需要运行一下的maven命令  
来安装你本地的maven库：

<pre class="shell">mvn install:install-file -DgroupId=com.oracle -DartifactId=ojdbc14 -Dversion=10.2.0.2 -Dpackaging=jar -Dfile=/path/to/file</pre>

2. 插件实体和域（field）

现在就是我们需要来插件域对象和域（field）了。依据就是我们之前做的那个类图。首先，我们使用entity Jpa 命令来插件一个活动的域对象。  
这个entity jpa命令有很多的可选的参数。还有一个必须的参数 –class。  
除了这个必须的参数外，我们使用 –testAutomatically 属性来为了方便我们的测试，插件集成的测试。好了，现在让我们来创建这个Topping对象吧：

<pre class="shell">com.springsource.roo.pizzashop roo&gt; hint
You can create entities either via Roo or your IDE.
Using the Roo shell is fast and easy, especially thanks to the TAB completion.

Start by typing 'ent' and then hitting TAB twice.
Enter the --name in the form '~.domain.MyEntityClassName'
In Roo, '~' means the --topLevelPackage you specified via 'create project'.

After specify a --name argument, press SPACE then TAB. Note nothing appears.
Because nothing appears, it means you've entered all mandatory arguments.
However, optional arguments do exist for this command (and most others in Roo).
To see the optional arguments, type '--' and then hit TAB. Mostly you won't
need any optional arguments, but let's select the --testAutomatically option
and hit ENTER. You can always use this approach to view optional arguments.

After creating an entity, use 'hint' for the next suggestion.
com.springsource.roo.pizzashop roo&gt;
com.springsource.roo.pizzashop roo&gt; entity jpa --class ~.domain.Topping --testAutomatically
Created SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain
Created SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain/Topping.java
Created SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain
Created SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain/ToppingDataOnDemand.java
Created SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain/ToppingIntegrationTest.java
Created SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain/Topping_Roo_Entity.aj
Created SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain/Topping_Roo_ToString.aj
Created SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain/Topping_Roo_Configurable.aj
Created SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain/ToppingIntegrationTest_Roo_Configurable.aj
Created SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain/ToppingDataOnDemand_Roo_DataOnDemand.aj
Created SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain/ToppingIntegrationTest_Roo_IntegrationTest.aj
Created SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain/ToppingDataOnDemand_Roo_Configurable.aj</pre>

你会注意到除了生成JAVA和AspectJ代码。entity jpa命令还在你工程的顶层包下面生成了一些合适的目录结构。  
你同时会发现我们用‘~’来代替工程的顶层包名。他给冗长的包名提供了一个很方便的缩写。同样你还可以在命令行里敲tab来显示完全的包名。  
接下来我们要给Topping类添加域（field）name。可以通过field命令来实现：

<pre class="shell">~.domain.Topping roo&gt; hint
You can add fields to your entities using either Roo or your IDE.

To add a new field, type 'field' and then hit TAB. Be sure to select
your entity and provide a legal Java field name. Use TAB to find an entity
name, and '~' to refer to the top level package. Also remember to use TAB
to access each mandatory argument for the command.

After completing the mandatory arguments, press SPACE, type '--' and then TAB.
The optional arguments shown reflect official JSR 303 Validation constraints.
Feel free to use an optional argument, or delete '--' and hit ENTER.

If creating multiple fields, use the UP arrow to access command history.

After adding your fields, type 'hint' for the next suggestion.
To learn about setting up many-to-one fields, type 'hint relationships'.
~.domain.Topping roo&gt;
~.domain.Topping roo&gt; field string --fieldName name --notNull --sizeMin 2
Managed SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain/Topping.java
Created SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain/Topping_Roo_JavaBean.aj
Managed SRC_TEST_JAVA/com/springsource/roo/pizzashop/domain/ToppingDataOnDemand_Roo_DataOnDemand.aj
Managed SRC_MAIN_JAVA/com/springsource/roo/pizzashop/domain/Topping_Roo_ToString.aj</pre>

正如hint命令给你的提示，你能够轻松地给域添加约束，通过可选的属性例如 –notNULL 和 –sizeMin 2。  
这些约束都是Roo参考http://jcp.org/en/jsr/detail?id=303 规范以注解的形式添加到java源代码里的。  
而且你应该注意到Roo shell知道当前的上下文中你要使用field命令。他知道你刚才创建了一个Topping类。  
接下来添加的域会追加到Topping这个类上。当前的这个上下文你会在命令行里发现：

如果你想在当前的上下文里给别的类添加域，你需要使用 –class属性来完成。  
下面我们要添加Base和Pizza的对象。通过下面的命令：

<pre class="shell">entity jpa --class ~.domain.Base --testAutomatically
field string --fieldName name --notNull --sizeMin 2
entity jpa --class ~.domain.Pizza --testAutomatically
field string --fieldName name --notNull --sizeMin 2
field number --fieldName price --type java.lang.Float</pre>

在给Pizza添加了name和price域之后，接着要给他和Base于Topping之间添加关系约束了。一个Pizza可以有很多的Topping与其对应，  
一个Topping可以对于很多的Pizza。所以Pizza和Toppings之间他们是多对多的关系。可以通过filed set命令来添加多对多的关系。

<pre class="shell">~.domain.Pizza roo&gt; field set --fieldName toppings --type ~.domain.Topping</pre>

你可以发现定义他们之间的关系很简单，而你甚至不需要知道具体的Jpa注解是怎么创建我们之间的映射关系。  
同样你可以定义多对一的关系给Pizza和Toppings。 可以通过下面的field reference命令：

<pre class="shell">~.domain.Pizza roo&gt; field reference --fieldName base --type ~.domain.Base</pre>

下面我们可以使用同样的方式来继续添加PizzaOrder对象，并且借助field date和field number命令来添加一些特殊的域。

<pre class="shell">entity jpa --class ~.domain.PizzaOrder --testAutomatically
field string --fieldName name --notNull --sizeMin 2
field string --fieldName address --sizeMax 30
field number --fieldName total --type java.lang.Float
field date --fieldName deliveryDate --type java.util.Date
field set --fieldName pizzas --type ~.domain.Pizza</pre>

到这里对象基本搞定！

3.集成测试

当你完成了创建你的对象之后，你要看一看到底是否能够工作，幸运的是，Roo已经在我们创建域对象的时候创建了集成的测试。  
提示：如果你没有在创建对象的时候创建集成测试。你依然能够很轻松地创建他们，通过test integration命令。当你创建集成测试完成后，你就  
能够使用perform tests命令来运行他们了：

<pre class="shell">~.domain.PizzaOrder roo&gt; perform tests
...
-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running com.springsource.roo.pizzashop.domain.PizzaOrderIntegrationTest
Tests run: 9, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 5.413 sec
Running com.springsource.roo.pizzashop.domain.ToppingIntegrationTest
Tests run: 9, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.148 sec
Running com.springsource.roo.pizzashop.domain.PizzaIntegrationTest
Tests run: 9, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.14 sec
Running com.springsource.roo.pizzashop.domain.BaseIntegrationTest
Tests run: 9, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.097 sec

Results :

Tests run: 36, Failures: 0, Errors: 0, Skipped: 0

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESSFUL
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 17 seconds
[INFO] Finished at: Tue Dec 29 15:58:04 EST 2009
[INFO] Final Memory: 25M/79M
[INFO] ------------------------------------------------------------------------</pre>

正如你看到的。Roo已经运行了一个等同于maven 的test命令。（相当于‘mvn test’）来运行测试。  
所有的测试已经通过。Roo生成了9个集成测试针对每一个域对象，这样4个对象就有36个集成测试。

4，使用你的IDE

当然Roo的工程能够在你喜欢的IDE里打开并编辑。我们建议你使用SpringSource Tool Suite。你能够在SpringSource  
免费下载到、如果你不使用STS，你就去IDE用法http://static.springsource.org/spring-roo/reference/html/usage.html#usage-ide哪里去查看详细的内容吧。

默认的Roo工程不会包含任何IDE制定的工程配置文件，所以IDE就不能够正常的导入工程。Roo shell能够帮助你创建一个IDE认识的工程。可以使用  
perform eclipse命令。当然你如果安装了eclipse的m2eclipse插件就不需要这个命令了。如果你既没有m2eclipse插件又不使用STS。那就只能运行下面的命令了：

<pre class="shell">~.domain.PizzaOrder roo&gt; perform eclipse
...
[INFO] Preparing eclipse:eclipse
[INFO] [aspectj:compile {execution: default}]
[INFO] [eclipse:eclipse {execution: default-cli}]
[INFO] Adding support for WTP version 2.0.
[INFO] Using Eclipse Workspace: null
[INFO] Adding default classpath container: org.eclipse.jdt.launching.JRE_CONTAINER
[INFO] Wrote settings to /Users/sschmidt/pizza/.settings/org.eclipse.jdt.core.prefs
[INFO] Wrote Eclipse project for "pizzashop" to /Users/sschmidt/pizza.
...

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESSFUL
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 3 seconds
[INFO] Finished at: Tue Dec 29 16:11:38 EST 2009
[INFO] Final Memory: 24M/79M
[INFO] ------------------------------------------------------------------------</pre>

注意，第一次运行这个命令可能要等一会，因为maven要下载依赖和他们的源代码到你本地的库里。  
一旦这个命令成功执行完，你就能够通过STS导入工程了。导入之后，看一看java源码。例如你可以  
跑个JUnit测试看看。

如果你使用的是STS或者装有m2eclipse插件的eclipse，你可以完全跳过这一步。直接在IDE下的maven里选择导入maven工程即可。  
正如在本文的工程结构中描述那样，Roo的工程广泛的采用了AspectJ Intertype declarations。但是这个并不影响代码提示功能在STS里。  
你可以在集成测试的代码里使用testMarkerMethod() 方法来测试它。例如你可以打开BaseIntegrationTest.java源文件试试：

注意：所有的方法可以在STS代码助手里看见。

5. 插件一个web层

接下来我们要给Pizza shop创建web层。通过web mvn命令来完成。最方便的方法来创建控制器和所有相关的web产品的是web mvc setup命令：

<pre class="shell">~.domain.PizzaOrder roo&gt; web mvc setup

~.domain.PizzaOrder roo&gt; web mvc all --package ~.web</pre>

这个命令会扫描工程里所有的实体对象，然后会为每一个域对象插件一个spring mvc 的控制器。–package 属性会制定控制器要放在什么地方。  
可以通过传统的命令行或者STS的Roo shell来运行它。在STS里你可以右键项目然后在 ‘Spring Tools > Open Roo Shell’.

注意：在sts里面运行了web mvc setup命令后工程会从本来一个普通的的java工程转换为一个web工程。同时还会添加例如Spring mvc 的依赖进去。  
为了能够在STS里更新工程的classpath，你可以再次运行‘perform eclipse’命令。然后刷新工程在sts里、

所有这些新添加的 web部件的需要的视图架构可以在 src/main/webapp文件夹里找到。这个文件夹里包括图片，样式表，jsp页面等。这个地方的说  
明会在http://static.springsource.org/spring-roo/reference/html/beginning.html#customizing-ui讲到。

Roo生成的Spring mvc控制器遵循的是REST模式，这样能够尽可能多的利用spring3中的很多新特性。下面是URI – Resource 映射的关系图：

[<img class="alignnone size-full wp-image-721" title="restmappings" src="http://www.yyxzy.org/wp-content/uploads/2011/11/restmappings.png" alt="" width="450" height="230" />][2]

6：添加web server  
在web容器里部署产品时有很多可供选择的。  
*从shell部署：  
*运行‘mvn tomcat：run’在工程的根目录。部署到tomcat容器里。  
*运行‘mvn jetty：run’在工程的根目录。部署到jetty容器里。  
*部署到STS里web容器  
*直接把工程拽到想要部署的web容器视图中  
*右键工程，选择 ‘Run As > Run on Server’ 来部署到想要的容器中。

接下来就看看到底我们的工程怎么着了吧!启动server–>http://localhost:8080/pizzashop

接下来是安全性等  
敬请期待~

 [1]: http://www.yyxzy.org/2011/10/%E5%BC%80%E5%A7%8B%E5%AD%A6%E4%B9%A0spring-roo%E7%AC%AC%E4%B8%80%E6%AD%A51/
 [2]: http://www.yyxzy.org/wp-content/uploads/2011/11/restmappings.png