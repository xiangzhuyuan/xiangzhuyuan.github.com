---
title: two google related bookmarklets
author: mathewxiang
layout: post
permalink: /2012/04/two-google-related-bookmarklet/
categories:
  - web前端
tags:
  - bookmarklet
---
two useful bookmarklet:

1.  <a style="cursor: move;" title="google search" onclick="alert('把它拖拽到书签栏，以后直接选中文字然后点击');return false;" href="javascript:var q=((window.getSelection&&window.getSelection())||(document.getSelection&&document.getSelection())||(document.selection&&document.selection.createRange&&document.selection.createRange().text));if(q!=null){window.open('http://www.google.com/search?q=' +q);void(0);}">google search bookmarklet</a>
2.  <a style="cursor: move;" onclick="alert('把它拖拽到书签栏，以后直接选中文字然后点击');return false;" href="javascript:var t=((window.getSelection&&window.getSelection())||(document.getSelection&&document.getSelection())||(document.selection&&document.selection.createRange&&document.selection.createRange().text));var e=(document.charset||document.characterSet);if(t!=''){window.open('http://translate.google.com/?text='+t+'&hl=zh-CN&langpair=auto|zh-CN&tbb=1&ie='+e);}else{window.open('http://translate.google.com/translate?u='+encodeURIComponent(location.href)+'&hl=zh-CN&langpair=auto|zh-CN&tbb=1&ie='+e);};">Chinese (Simplified)</a>

what is Bookmarklet?

### <a href="http://en.wikipedia.org/wiki/Bookmarklet" target="_blank"><em>Bookmarklet</em> – Wikipedia, the free encyclopedia</a>

How about google translate?

### <a href="http://translate.google.com/" target="_blank"><em>Google Translate</em></a>