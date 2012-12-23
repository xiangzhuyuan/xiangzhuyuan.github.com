---
title: HTML5的Nav标签
author: mathewxiang
layout: post
permalink: /2011/07/html5_nav_tag/
categories:
  - 软件开发
tags:
  - html5
  - nav标签
---
在换了wordpress team的theme 之后看了看源码。发现已经把html5的很多标签都加了进去。或者早就发生的事情我才发现。愧啊！看来作为一个自称对web前段感兴趣的我来说真是落伍了啊！下面是本站的navigator。

<pre name="code" class="html">&lt;nav id="access" role="navigation">
				<h3 class="assistive-text">
  <?php _e( 'Main menu', 'twentyeleven' ); ?>
</h3>
				

<?php /*  Allow screen readers / text browsers to skip the navigation menu and get right to the good stuff. */ ?>
				

<div class="skip-link">
  <a class="assistive-text" href="#content" title="<?php esc_attr_e( 'Skip to primary content', 'twentyeleven' ); ?>"><?php _e( 'Skip to primary content', 'twentyeleven' ); ?></a>
</div>
				

<div class="skip-link">
  <a class="assistive-text" href="#secondary" title="<?php esc_attr_e( 'Skip to secondary content', 'twentyeleven' ); ?>"><?php _e( 'Skip to secondary content', 'twentyeleven' ); ?></a>
</div>
				

<?php /* Our navigation menu.  If one isn't filled out, wp_nav_menu falls back to wp_page_menu. The menu assiged to the primary position is the one used. If none is assigned, the menu with the lowest ID is used. */ ?>
			

<div id="navigation">
  <!-- menus START -->
  
  	
  
  <ul id="menus">
    <li class="current_page_item">
      <a class="home" title="Go to 52smap BBS" href="http://bbs.52smap.com/">BBS</a>
    </li>
    
  </ul>
</div>	

<?php wp_nav_menu( array( 'theme_location' => 'primary' ) ); ?>
			&lt;/nav>
</pre>

—–

在http://www.w3school.com.cn上看了一个demo。  
真的很简单啊。

<pre name="code" class="html">



&lt;nav>
<a href="/html5/index.asp">Home</a>
<a href="/html5/html5_meter.asp">Previous</a>
<a href="/html5/html5_noscript.asp">Next</a>
&lt;/nav>





</pre>

然后显示就是按照我们以前或者现在的形式,用到了ul,然后再控制样式.  
我要学习了啊!