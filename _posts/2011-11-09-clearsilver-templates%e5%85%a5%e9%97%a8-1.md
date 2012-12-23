---
title: ClearSilver templates入门-1
author: mathewxiang
layout: post
permalink: /2011/11/clearsilver-templates%e5%85%a5%e9%97%a8-1/
categories:
  - Python
tags:
  - ClearSilver templates，python
---
**Clearsilver是what？**  
快速的和编程语言无关的html模板系统。不管是在静态的还是动态的web站点中，都能够提供视图和逻辑分离的功能实现。  
1999年开始开发的，在很多的项目中都有使用。  
**为什么用它:**  
<span style="text-decoration: underline;">高性能和语言无关性</span> 因为它是用c写的，然后在那些Python，Perl，Java，还有Ruby脚本语言中以模块的形式存在。所以非常之快！  
<span style="text-decoration: underline;">修改方便</span> 有一套很强大的模板，一次能够实现很多的效果。  
国际化支持  
<span style="text-decoration: underline;">高级特色</span> 内建很多高级特性，例如gzip压缩传输，在线调试，去空格，宏编程，URL和JavaScript字符串转义等.

<!--more-->

**怎么用：**

**基础:**  
要想从数据库里取出数据然后动态的显示在页面上，就需要2个对象。一个就是模板文件，另外一个就是hdf数据集。hdf数据集有点和json是差不多的。这2个东西作用在一起，就能够形成一个动态数据的展示了。

**分离应用逻辑和模板**：当在处理程序逻辑的时候，我们只需要关注怎么在最后生成一个正确的hdf数据库。然后在模板中，我们就是通过**点操作符**来取各自对应的值。如果在展示数据个数和类别不变的情况下，是不要再去改动模板文件的。而只是去处理生成的hdf数据集就行了。

**下面来说说hdf dataset是什么东西**:  
hdf文件很好解析的。它有2种格式的。一种就是像字典那样。

<pre class="shell">Page.Name = My Index
Page.URL = /myindex.html
Page.Menu.0 = Home
Page.Menu.1 = Preferences
Page.Menu.2 = Help
Page.Menu.3 = Support</pre>

另一种就是和xml差不多，以各种包含关系存在。

<pre class="shell">Page {
    Name = My Index
    URL = /myindex.html
        Menu {
        0 = Home
        1 = Preferences
        2 = Help
        3 = Support
       }
}</pre>

第二种格式的完全能够像xml那样，包含多种关系。

<pre class="shell">Page {
    Menu {
          0 {
          Name = Home
          URL = /
        }
         1 {
         Name = Preferences
         URL = /prefs
        }
        2 {
        Name = Help
        URL = /help.html
       }
       3 {
       Name = Support
       URL = /feedback/
       }
   }
}</pre>

因为HFD的api完全能够读写这种格式的文件。所以它完全可以成为一个强大的可配置和持久化的语言。但是，主要的目的还是能够把数据放到hdf文件中，然后  
在模板文件中使用。

在我们解析模板文件的时候，模板文件能够指向到hdf文件中的具体的变量，能够遍历特定节点的所有变量。例如，一个cs模板在解析上面的hdf文件中的Page。Menu的时候，  
它就能够去遍历所有的menu.返回所有的Menu。name和Url元素。

**这里要说2个比较重要的hdf写法的语法：**

1. Page.Name : Page.Menu.0.Name 通过冒号能够替代等号来拷贝某一个元素的值。不过在拷贝前被拷贝元素必须存在。  
2. 元素能够设置一个多行字符串值，这个语法和标准的unix脚本或者perl的语法类似。例如：

<pre class="shell">Page.Name &lt;&lt; EOM
This is my multi-line page name.
Isn't it spiffy?
EOM</pre>

**来说说模板文件：**  
模板文件的后缀可以是.cst或者.cs，由文本和嵌入的clearsilver命令构成。嵌入的语法就跟别的嵌入到html中的模板系统是差不多的。例如。  
clearsilver的嵌入方式是以<!--?cs开始，以? -->结束。

**有下面的一些命令：**  
替换: var, evar, lvar, include, linclude, set, name  
控制流: if, else, elif, alt  
遍历: each, loop, with  
宏: def, call

所有的控制流语句，遍历语句还有**def**语句都有结束语句，和html是一样的，比如**if**就对应着**/if**  
大多数的命令有一个或者多个参数表达式。  
另外cs语法也支持注释，就是在标签里 添加#作为注释开始。

<pre class="shell">&lt;?cs # this is a comment ?&gt;</pre>

**替换(应该不是替换,或者说是取值比较好)：** 简单的变量替换用

<pre class="shell"> &lt;? var:Page.Name ?&gt;</pre>

就能够实现。  
**evar**和**var**是一样的，除了对应的节点的值也是解析为cs命令。在加载和解析cs模板的时候会发生**evar**解析。结果就是，在展示之前语法将会报错，就是说**evar**不能够用在cs命令里面。比如说**each**循环中，就不能够  
使用evar来展现数据。  
**lvar**和**evar**有点像,不能够在响应的时候解析数据集的变量,而应该是在解析的时候,要不然会报语法错误,如果不是缓冲输出的话,将会得到一个不完整的页面,这个**CGI**工具总是以缓冲的形式将数据输出.

name将会返回当前节点的键名.比如<a name="name"></a><tt><?cs name:Page.Name ?></tt> 将会返回Name.这个在遍历和宏表达中比较有作用.别名的变量的真实名称能够拥有特殊的意义.(下面的例子中会讲到),这个和内置的另外一个表达式是同样的作用<a name="name"></a><tt><?cs var:name(Page.Name) ?>.</tt>