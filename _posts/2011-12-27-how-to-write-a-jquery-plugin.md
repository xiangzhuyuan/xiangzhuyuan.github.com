---
layout: post
title: 怎么写jQuery插件
date: 2011-12-27 09:53
comments: true
categories: []
---
<a title="http://docs.jquery.com/Plugins/Authoring" href="http://docs.jquery.com/Plugins/Authoring">http://docs.jquery.com/Plugins/Authoring</a>

当你感觉jQuery还不错,想开发属于自己的插件的时候,来到这个地方算是找对地方了.
通过插件或者方法来扩张jQuery是一种很强大的方法,能够节省你很多的时间,通过把
一些你很经典的想法来抽象到你的方法中.本文列出了一些基本东西,还有一些最佳实践,
还有些你刚开始入门的一些例子:

目录
<ul>
	<li class="toclevel-1"><a href="#Getting_Started"><span class="tocnumber">1</span> <span class="toctext">Getting Started</span></a></li>
	<li class="toclevel-1"><a href="#Context"><span class="tocnumber">2</span> <span class="toctext">Context</span></a></li>
	<li class="toclevel-1"><a href="#The_Basics"><span class="tocnumber">3</span> <span class="toctext">The Basics</span></a></li>
	<li class="toclevel-1"><a href="#Maintaining_Chainability"><span class="tocnumber">4</span> <span class="toctext">Maintaining Chainability</span></a></li>
	<li class="toclevel-1"><a href="#Defaults_and_Options"><span class="tocnumber">5</span> <span class="toctext">Defaults and Options</span></a></li>
	<li class="toclevel-1"><a href="#Namespacing"><span class="tocnumber">6</span> <span class="toctext">Namespacing</span></a>
<ul>
	<li class="toclevel-2"><a href="#Plugin_Methods"><span class="tocnumber">6.1</span> <span class="toctext">Plugin Methods</span></a></li>
	<li class="toclevel-2"><a href="#Events"><span class="tocnumber">6.2</span> <span class="toctext">Events</span></a></li>
	<li class="toclevel-2"><a href="#Data"><span class="tocnumber">6.3</span> <span class="toctext">Data</span></a></li>
</ul>
</li>
	<li class="toclevel-1"><a href="#Summary_and_Best_Practices"><span class="tocnumber">7</span> <span class="toctext">Summary and Best Practice</span></a></li>
</ul>
<!--more-->
<strong><a name="Getting_Started"></a>入门:</strong>
开发一个jQuery的插件,通过添加一个新的函数属性到<strong>jQuery.fn.</strong><em>对象</em>,而这个<em>对象名称</em>就是你创建的名字了:
<pre>jQuery.fn.myPlugin = function() {

  // Do your awesome plugin stuff here

};</pre>
但是等等,那个我喜欢的<strong>$</strong>符号呢? 别担心还在那里,只要确保你的插件不和别的库有冲突,那些库也有可能使用<strong>$</strong>付作为一种记号,<span style="text-decoration: underline;">给一个自运行的函数(闭包)传递jQuery对象的最好方式就是用$符号来代替他,这样在这个闭包中就不会被其他的库覆盖.</span>
<pre>(function( $ ) {
  $.fn.myPlugin = function() {

    // Do your awesome plugin stuff here

  };
})( jQuery );</pre>
这样就好多了,现在在这个闭包中,我们就能够尽情的<strong>使用$符号来替代jQuery对象了</strong>.

<a name="Context"></a><strong>上下文</strong>:
现在我们就能够在这个脚本中写属于自己的插件代码了.在开始之前,我要提到一个东西就是<strong>context</strong>.在一个临时的插件函数范围中<span style="text-decoration: underline;">,<strong>this</strong>关键字就指向到了jquery 插件触发的那个jquery对象.</span>在这里是一个插件替换,因为在很多其他的实例中当jQuery接受一个回调的时候,这个this关键字指向的是一个原生的DOM元素.这个经常会让程序员不必要的封装一下在jQuery的函数中.
<pre>(function( $ ){

  $.fn.myPlugin = function() {

    // there's no need to do $(this) because
    // "this" is already a jquery object

    // $(this) would be the same as $($('#element'));

    this.fadeIn('normal', function(){

      // the this keyword is a DOM element

    });

  };
})( jQuery );</pre>
$('#element').myPlugin();

<a name="The_Basics"></a><strong>基础概念:</strong>
我们理解了jQuery插件中的上下文,就让我们来写一个实际做了事情的插件吧.
<pre>(function( $ ){

  $.fn.maxHeight = function() {

    var max = 0;

    this.each(function() {
      max = Math.max( max, $(this).height() );
    });

    return max;
  };
})( jQuery );</pre>
<pre>var tallest = $('div').maxHeight();
// Returns the height of the tallest div</pre>
这个是一个简单的插件,使用.height()来返回page中最高的div 的高度.
<a name="Maintaining_Chainability"></a><strong>Maintaining Chainability</strong>

之前的代码返回一个数值,代表最高的div的高度,但是很多时候我们使用同样的方法来处理
一系列的元素集合,把他们传递给链条中的下一个方法,这个写法是jQuery很帅的设计,也是流行的一个原因,所以为了维护插件中代码的可连接性,<span style="text-decoration: underline;">我们需要确保插件返回的继续是一个jQuery的对象,也就是在插件函数内部的this关键字.</span>
<pre>(function( $ ){

  $.fn.lockDimensions = function( type ) {  

    return this.each(function() {

      var $this = $(this);

      if ( !type || type == 'width' ) {
        $this.width( $this.width() );
      }

      if ( !type || type == 'height' ) {
        $this.height( $this.height() );
      }

    });

  };
})( jQuery );</pre>
<pre>$('div').lockDimensions('width').css('color', 'red');</pre>
因为插件返回的是<strong>this关键字</strong>在他的范围中,它维护了可连接性,能够让jQuery集合继续
传递到jQuery的其他方法中,例如.css().这样如果你的插件不返回一个本身固有的值,你应该返回一个this关键字在你的插件临时的函数中.同样,你能够把参数那些你传递到插件函数的再传递到其他的函数中.这样在前面的代码中,width就能够变成一个type参数传递给函数.
<a name="Defaults_and_Options"></a><strong>Defaults and Options</strong>

<strong></strong>很多复杂的自定义的插件提供很多的选项,它的最佳实践就是定义一些默认的设置,能够被扩展的,(使用$.extend)当插件被调用的时候,这样就在在调用插件的时候省去一长串的参数了.你能够在调用函数的时候只传递一个对象,而这个对象就是被你重写的默认设置.看下面:
<pre>(function( $ ){

  $.fn.tooltip = function( options ) {  

    // Create some defaults,
    // extending them with any options that were provided
    var settings = $.extend( {
      'location'         : 'top',
      'background-color' : 'blue'
    }, options);

    return this.each(function() {        

      // Tooltip plugin code here

    });

  };
})( jQuery );</pre>
&nbsp;
<pre>$('div').tooltip({
  'location' : 'left'
});</pre>
在这个例子中,在调用了tooltip插件给了一些选项,默认的location设置会被重写为left.而默认的background-color还是blue.所以最后的设置对象是:
<pre>{
    'location'         : 'left',
    'background-color' : 'blue'
}</pre>
这个是一个很不错的方式来提供一个可高配置的插件,而不需要开发人员定义所有可用选项.

<a name="Namespacing"></a><strong>命名空间</strong>
合适的命名空间在开发插件的时候是一个重要的部分,正确的命名能够降低你的代码被其他插件或者现写的代码覆盖重写的几率,命名空间同样能够使你的生活简单作为一个插件开发人员.能够帮助你继续扩展你的方法,事件,数据等.

<a name="Plugin_Methods"></a><strong>插件方法</strong>:
一般情况下,一个插件也就是一个命名空间.在jQuery.fn对象中:
<pre>(function( $ ){

  $.fn.tooltip = function( options ) {
    // THIS
  };
  $.fn.tooltipShow = function( ) {
    // IS
  };
  $.fn.tooltipHide = function( ) {
    // BAD
  };
  $.fn.tooltipUpdate = function( content ) {
    // !!!
  };

})( jQuery );</pre>
这样的做法是不提倡的,纠正的方法是,你应该整理你的插件方法到一个对象中,然后通过方法名称给插件来调用他们:
<pre>(function( $ ){

  var methods = {
    init : function( options ) {
      // THIS
    },
    show : function( ) {
      // IS
    },
    hide : function( ) {
      // GOOD
    },
    update : function( content ) {
      // !!!
    }
  };

  $.fn.tooltip = function( method ) {

    // Method calling logic
    if ( methods[method] ) {
      return methods[ method ].apply( this, Array.prototype.slice.call( arguments, 1 ));
    } else if ( typeof method === 'object' || ! method ) {
      return methods.init.apply( this, arguments );
    } else {
      $.error( 'Method ' +  method + ' does not exist on jQuery.tooltip' );
    }    

  };

})( jQuery );

// calls the init method
$('div').tooltip(); 

// calls the init method
$('div').tooltip({
  foo : 'bar'
});
// calls the hide method
$('div').tooltip('hide');
// calls the update method
$('div').tooltip('update', 'This is the new tooltip content!');</pre>
这种类型的插件架构能够让你把方法封装在插件父闭包中,然后通过传递方法名作为第一个参数来调用,接着传递其他的一些参数你可能需要用到的.这种方式的方法封装和插件架构是在jQuery插件组织中比较统一的标准
方法.

<a name="Events"></a><strong>events</strong>

一个很经典的特性bind方法就是能够通过命名空间来绑定事件.如果你把插件绑定到一个事件上,那么这样做就是一个比较好的实践.通过这种方式,你可以稍后unbind它.这样做就不会干扰到其他绑定到这个事件上的事件.你可以给你的事件添加命名空间,通过附加".&lt;namespace&gt;"来区分这个事件的类别.
<pre>(function( $ ){

  var methods = {
     init : function( options ) {

       return this.each(function(){
         $(window).bind('resize.tooltip', methods.reposition);
       });

     },
     destroy : function( ) {

       return this.each(function(){
         $(window).unbind('.tooltip');
       })

     },
     reposition : function( ) {
       // ...
     },
     show : function( ) {
       // ...
     },
     hide : function( ) {
       // ...
     },
     update : function( content ) {
       // ...
     }
  };

  $.fn.tooltip = function( method ) {

    if ( methods[method] ) {
      return methods[method].apply( this, Array.prototype.slice.call( arguments, 1 ));
    } else if ( typeof method === 'object' || ! method ) {
      return methods.init.apply( this, arguments );
    } else {
      $.error( 'Method ' +  method + ' does not exist on jQuery.tooltip' );
    }    

  };

})( jQuery );</pre>
<pre>$('#fun').tooltip();
// Some time later...
$('#fun').tooltip('destroy');</pre>
在这个例子中,当tooltip通过init方法实例化后,他就会绑定reposition方法到window对象的resize事件,而这些都是在tooltip的命名空间下进行的.之后,如果开发人员需要销毁tooltip,我们就能够通过调用插件,传递给一个命名空间,来解除绑定.在这个例子中,对于unbind方法来说,他能够让我们安全的解除绑定插件事件,而不会影响到插件之外绑定到这个事件上的事件.

<strong><a name="Data"></a>数据 Data</strong>
经常在插件的开发中.你可能需要去维护状态,检查插件是否已经在一个已知的元素上被实例化,通过使用jQuery的data方法就能够在每个元素上跟踪变量的值,可是,和通过很多不同的名称来跟踪一大堆单个的数据相比,最好还是使用一个单个的对象来包含所有的变量,然后通过名称来访问这些变量比较好
<pre>(function( $ ){

  var methods = {
     init : function( options ) {

       return this.each(function(){

         var $this = $(this),
             data = $this.data('tooltip'),
             tooltip = $('&lt;div /&gt;', {
               text : $this.attr('title')
             });

         // If the plugin hasn't been initialized yet
         if ( ! data ) {

           /*
             Do more setup stuff here
           */

           $(this).data('tooltip', {
               target : $this,
               tooltip : tooltip
           });

         }
       });
     },
     destroy : function( ) {

       return this.each(function(){

         var $this = $(this),
             data = $this.data('tooltip');

         // Namespacing FTW
         $(window).unbind('.tooltip');
         data.tooltip.remove();
         $this.removeData('tooltip');

       })

     },
     reposition : function( ) { // ... },
     show : function( ) { // ... },
     hide : function( ) { // ... },
     update : function( content ) { // ...}
  };

  $.fn.tooltip = function( method ) {

    if ( methods[method] ) {
      return methods[method].apply( this, Array.prototype.slice.call( arguments, 1 ));
    } else if ( typeof method === 'object' || ! method ) {
      return methods.init.apply( this, arguments );
    } else {
      $.error( 'Method ' +  method + ' does not exist on jQuery.tooltip' );
    }    

  };

})( jQuery );</pre>
通过使用data能够帮助你跟踪变量值和状态,通过方法调用.把你的数据命名空间规约到一个大对象中能够把访问你插件属性的过程变得简单.同样可以轻松地移除不需要的数据.
<a name="#Summary_and_Best_Practices"></a><strong>总结和最佳实践:</strong>
通过使用jQuery插件能够让你把那些不包括在库中的.那些很经典很实用的方法函数抽象到一个方法中,能够让你重用他们.让你在以后的开发中节省时间开发更有效率.这里只是一个简单的文章,告诉你应该在之后的开发中尽量遵循的一些最佳实践规范:
<ul>
	<li>尽量把插件封装在一个闭包中:</li>
</ul>
<p style="padding-left: 90px;">(function( $ ){ /* plugin goes here */ })( jQuery)</p>

<ul>
	<li>在你的插件临时函数中不要重复封装this关键字.</li>
	<li>一般不要在你的插件中直接返回一个固定的值,而是返回一个this关键字.这样能够维护可链接性.</li>
	<li>不要搞一长串的参数,通过给插件传递一个供设置的对象,这样就能够在插件内部扩展.</li>
	<li>不要在一个插件中把jQuery.fn对象分割成很多.</li>
	<li>总是给自己的方法,事件,数据(data)添加命名空间.</li>
	<li>jQuery.fn的发音应该是jQuery effin'</li>
</ul>
