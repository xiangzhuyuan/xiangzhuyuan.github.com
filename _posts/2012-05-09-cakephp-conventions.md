---
layout: post
title: CakePHP Conventions
date: 2012-05-09 23:15
comments: true
categories: []
---
<strong>Cakephp约定</strong>
我们崇尚基于约定的配置,这样做可能在刚开始学习cakephp的时候要花点时间,但是这些时间会换来以后的更多时间,俗话说,磨刀不误砍柴工.只要遵循我们的约定,在以后的开发中会更加高效,维护起来也会更加便利.在以后的开发中,突然进来新的同事,也能够很快上手.
cakephp的约定建立是来源于多年的web开发中的最佳实践.我们建议在开发的过程中还是遵循这些约定.当然我们也会提醒大家这些原则都是能够很容易重写的---在你接受遗留项目的有些功能还是很便利的.<!--more-->

<strong>控制器的约定</strong>
控制器的类名是复制的大写驼峰形式命名的.以Controller结尾.<strong>PeopleController</strong>和<strong>LatestArticlesController</strong>都是合格的命名.
在一个控制器的类中,首先你应该写的就是index()方法.当一个请求访问一个指定的控制器,但是没有指定action的时候,cakephp会默认的执行index(),例如,一个请求:http://www.yyxzy.org/apples/他将会被分发到<strong>ApplesController</strong>这个类的index()方法,同理,http://www.yyxzy.org/apples/view将会被映射到ApplesController的view()方法.当然你也可以通过在方法前面加一个下划线的前缀来改变这个方法的可访问性.这样的方法只能是被内部调用.
<pre><span class="cp">&lt;?php</span>
<span class="k">class</span> <span class="nc">NewsController</span> <span class="k">extends</span> <span class="nx">AppController</span> <span class="p">{</span>
    <span class="k">public</span> <span class="k">function</span> <span class="nf">latest</span><span class="p">()</span> <span class="p">{</span>
        <span class="nv">$this</span><span class="o">-&gt;</span><span class="na">_findNewArticles</span><span class="p">();</span>
    <span class="p">}</span>
    <span class="k">protected</span> <span class="k">function</span> <span class="nf">_findNewArticles</span><span class="p">()</span> <span class="p">{</span>
        <span class="c1">// Logic to find latest news articles</span>
    <span class="p">}</span>
<span class="p">}</span></pre>
例子中,当试图访问 http://www.example.com/news/latest/的时候,同样还是能够正常访问,而如果访问http://www.example.com/news/_findNewArticles/的时候将会得到一个action没有找到的error.当然你可以通过访问修饰符来控制一个控制器的方法是否能够被访问到,非public的方法就是不能够访问.

<strong>控制器的类名对应的URL的一些注意事项</strong>
正如上面演示的一样,单个的单词命名的控制器很容易通过一个简单的小写单词url映射到.例如,<strong>ApplesController</strong>(包含他的文件的文件名是(ApplesController.php)将会通过http://example.com/apples访问到.
哪一些不规范的写法的控制器类名怎么被处理呢?我们看看:
<ul>
	<li>/redApples</li>
	<li>/RedApples</li>
	<li>/Red_apples</li>
	<li>/red_apples</li>
</ul>
上面的这些访问都会被解析到RedApples控制器上,但是,我们约定的url可以是小写加下划线的,所以这个访问 /red_apples/go_pick是正确的写法,他会被解析到RedApplesController::go_pick这个action.cakephp的url和参数处理我会在以后讲到,他归属在路由配置那块.

<strong>文件名和类名的约定</strong>
一般来说,文件名和类名是配对的,也就是说是相同的,他们都是大写驼峰命名的.所有如果你有一个MyNiftyClass,那么这个包含他的文件的文件名就是MyNiftyClass.php.下面的例子将会说明在cakephp中怎么来给文件和文件包含的类命名.
<ul>
	<li>控制器类KissesAndHugsController将会保存这样一个名字的文件中:KissesAndHugsController.php</li>
	<li>组件类MyHandyComponent将会保存这样一个名字的文件中:MyHandyComponent.php</li>
	<li>对象类OptionValue将会保存这样一个名字的文件中:OptionValue.php</li>
	<li>行为类EspeciallyFunkableBehavior将会保存这样一个名字的文件中:EspeciallyFunkableBehavior.php</li>
	<li>视图类SuperSimpleView将会保存这样一个名字的文件中:SuperSimpleView.php</li>
	<li>帮助类BestEverHelper将会保存这样一个名字的文件中:BestEverHelper.php</li>
</ul>
上面的文件将会被放置在合适的app文件夹下的某个文件夹中.

&nbsp;

<strong>对象和数据库的命名约定</strong>

对象类的名字是一个单个单词(没用下划线)组成,或者就是一个定语来修饰的.总之应该不是动宾结构的,你懂得.例如:Person,BigPerson或者ReallyBigPerson.
数据库表对应的cakephp中的对象类,他的命名就是把对象类的定语和主语给下划线分开.上面三个对象类对应的就应该是: people, big_people和really_big_people.

你可以使用工具类Inflector来检查单个/多个单词组成形式.详情:http://book.cakephp.org/2.0/en/core-utility-libraries/inflector.html

表字段的名字同样是多个单词用下划线连接起来的.例如:first_name.

在表之间存在1对多或者多对1的情况下,我们建议使用单个单词(关系表)加_id.所以,如果是Baker有很多Cake的时候,在cakes的表中,将会有一个baker_id的这样一个字段来表示外键.如果那个关系表本身名字就有多个单词下划线组成的category_types,同理直接后面加_id.例如:category_type_id.

一个组合表,就是在很多model之间有包含被包含的关系时候,它的命名一般都是abc名称排序的. (apples_zebras rather than zebras_apples).

所有和cakephp中对象类有交互的表,都需要有一个主键.如果你在表里没有唯一主键,cakephp的约定,你要使用它必须表中自己加一个唯一主键.

cakephp不支持组合主键,如果想要操作你的组合表的数据,直接使用query(http://book.cakephp.org/2.0/en/models/retrieving-your-data.html#model-query)来调用,或者添加一个主键到他里面.例如:
<pre><span class="x">CREATE TABLE posts_tags (</span>
<span class="x">id INT(10) NOT NULL AUTO_INCREMENT,</span>
<span class="x">post_id INT(10) NOT NULL,</span>
<span class="x">tag_id INT(10) NOT NULL,</span>
<span class="x">PRIMARY KEY(id));</span></pre>
相比较使用一个自动增长的int类型的键作为主键,你可以使用一个char(36)类型的主键,cakephp会使用一个一个36位的字符uuid(String::uuid)在你通过使用Model:save添加一条新纪录的时候.
<strong>视图约定</strong>

视图模板文件的命名对应于控制器的action的名字,如果action的名字是getReady(),那么cakephp会去找get_ready.ctp.
基本的模式就是: /app/View/Controller/underscored_function_name.ctp.
通过cakephp的点滴命名规则,你在获得丰富功能的时候免除了很多的麻烦.下面是一个完成的命名约定的体现:
<ul>
	<li>Database table: “people”</li>
	<li>Model class: “People”, found at /app/Model/People.php</li>
	<li>Controller class: “PeopleController”, found at /app/Controller/PeopleController.php</li>
	<li>View template, found at /app/View/People/index.ctp</li>
</ul>
使用这些约定,cakephp会知道http://example.com/people/请求会映射到<strong>PeopleController</strong>的index() action.在调用的时候自动的将会把Person对象和people表对应起来.

&nbsp;

related post:
<h2><a title="Link to CakePHP Folder Structure" href="http://www.yyxzy.org/2012/04/cakephp-folder-structure/" rel="bookmark">CakePHP Folder Structure</a></h2>
