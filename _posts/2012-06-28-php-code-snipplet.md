---
layout: post
title: php code snipplet
date: 2012-06-28 00:12
comments: true
categories: []
---
一段php代码.仅供参考!<!--more-->
<div style="background: #fdfdfd; color: black;"><span style="text-decoration: underline;">PHP语言</span>: <a href="http://fayaa.com/code/">高亮代码由发芽网提供</a></div>
<div class="source" style="font-family: '[object HTMLOptionElement]', Consolas, 'Lucida Console', 'Courier New'; color: #000000; background-color: #f9f7ed;"><span style="color: #507090;">&lt;?php</span>
<span style="color: #d04020;">/**</span>
<span style="color: #d04020;"> * Created by JetBrains PhpStorm.</span>
<span style="color: #d04020;"> * User: Administrator</span>
<span style="color: #d04020;"> * Date: 12-6-27</span>
<span style="color: #d04020;"> * Time: 下午10:55</span>
<span style="color: #d04020;"> * To change this template use File | Settings | File Templates.</span>
<span style="color: #d04020;"> */</span><span style="color: #906030;">$a</span> <span style="color: #303030;">=</span> <span style="color: #008000; font-weight: bold;">array</span>(<span style="color: #0000d0; font-weight: bold;">1</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">3</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">4</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">5</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">6</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">8</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">3</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">2</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">22</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">55</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">554</span><span style="color: #000000;">,</span> <span style="color: #0000d0; font-weight: bold;">12</span>);
<span style="color: #808080;">//var_dump($a);</span>
<span style="color: #007020;">rsort</span>(<span style="color: #906030;">$a</span>);
<span style="color: #808080;">//var_dump($a);</span>
<span style="color: #808080;">//print($a[0]) . "\n";</span></div>
<span style="color: #906030;">$b</span> <span style="color: #303030;">=</span> <span style="color: #906030;">$a</span><span style="color: #000000;">[</span><span style="color: #0000d0; font-weight: bold;">0</span><span style="color: #000000;">];</span>

<span style="color: #808080;">//print ceil($b / 25) . "\n";</span>
<span style="color: #906030;">$filenames</span> <span style="color: #303030;">=</span> <span style="color: #008000; font-weight: bold;">array</span>();
<span style="color: #008000; font-weight: bold;">for</span> (<span style="color: #906030;">$i</span> <span style="color: #303030;">=</span> <span style="color: #0000d0; font-weight: bold;">0</span>; <span style="color: #906030;">$i</span> <span style="color: #303030;">&lt;</span> <span style="color: #007020;">ceil</span>(<span style="color: #906030;">$b</span> <span style="color: #303030;">/</span> <span style="color: #0000d0; font-weight: bold;">25</span>); <span style="color: #906030;">$i</span><span style="color: #303030;">++</span>)
<span style="color: #000000;">{</span>

<span style="color: #906030;">$filenames</span><span style="color: #000000;">[]</span> <span style="color: #303030;">=</span> <span style="background-color: #fff0f0;">"requesr_"</span> <span style="color: #303030;">.</span>(<span style="color: #906030;">$i</span><span style="color: #303030;">==</span><span style="color: #0000d0; font-weight: bold;">0</span><span style="color: #303030;">?</span> (<span style="color: #906030;">$i</span> <span style="color: #303030;">*</span> <span style="color: #0000d0; font-weight: bold;">25</span>)<span style="color: #303030;">:</span>((<span style="color: #906030;">$i</span> <span style="color: #303030;">*</span> <span style="color: #0000d0; font-weight: bold;">25</span>)<span style="color: #303030;">+</span><span style="color: #0000d0; font-weight: bold;">1</span>)) <span style="color: #303030;">.</span> <span style="background-color: #fff0f0;">"_"</span> <span style="color: #303030;">.</span> ((<span style="color: #906030;">$i</span> <span style="color: #303030;">+</span> <span style="color: #0000d0; font-weight: bold;">1</span>) <span style="color: #303030;">*</span> <span style="color: #0000d0; font-weight: bold;">25</span>) <span style="color: #303030;">.</span> <span style="background-color: #fff0f0;">"xml.gz"</span>;
<span style="color: #000000;">}</span>

<span style="color: #007020;">var_dump</span>(<span style="color: #906030;">$filenames</span>);
