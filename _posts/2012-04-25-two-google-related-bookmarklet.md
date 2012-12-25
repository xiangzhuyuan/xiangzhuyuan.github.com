---
layout: post
title: two google related bookmarklets
date: 2012-04-25 14:18
comments: true
categories: []
---
two useful bookmarklet:
<ol>
	<li><a style="cursor: move;" title="google search" onclick="alert('把它拖拽到书签栏，以后直接选中文字然后点击');return false;" href="javascript:var q=((window.getSelection&amp;&amp;window.getSelection())||(document.getSelection&amp;&amp;document.getSelection())||(document.selection&amp;&amp;document.selection.createRange&amp;&amp;document.selection.createRange().text));if(q!=null){window.open('http://www.google.com/search?q=' +q);void(0);}">google search bookmarklet</a></li>
	<li><a style="cursor: move;" onclick="alert('把它拖拽到书签栏，以后直接选中文字然后点击');return false;" href="javascript:var t=((window.getSelection&amp;&amp;window.getSelection())||(document.getSelection&amp;&amp;document.getSelection())||(document.selection&amp;&amp;document.selection.createRange&amp;&amp;document.selection.createRange().text));var e=(document.charset||document.characterSet);if(t!=''){window.open('http://translate.google.com/?text='+t+'&amp;hl=zh-CN&amp;langpair=auto|zh-CN&amp;tbb=1&amp;ie='+e);}else{window.open('http://translate.google.com/translate?u='+encodeURIComponent(location.href)+'&amp;hl=zh-CN&amp;langpair=auto|zh-CN&amp;tbb=1&amp;ie='+e);};">Chinese (Simplified)</a></li>
</ol>
what is Bookmarklet?
<h3><a href="http://en.wikipedia.org/wiki/Bookmarklet" target="_blank"><em>Bookmarklet</em> - Wikipedia, the free encyclopedia</a></h3>
How about google translate?
<h3><a href="http://translate.google.com/" target="_blank"><em>Google Translate</em></a></h3>
