---
title: Python的List Comprehensions
author: mathewxiang
layout: post
permalink: /2012/09/python%e7%9a%84list-comprehensions/
categories:
  - Python
tags:
  - List Comprehensions
  - python
---
### List Comprehensions 不知道具体的翻译表达,也懒得去弄清楚国内行业中是怎么表达的.暂且就叫它为’列表推导式’.<!--more-->

总之感觉这个语法糖还是很优雅的.列表推导式的作用就是创建一个List,方法比较简洁.在一般的程序中,会把满足一定条件的结果放到预先定义好的list对象中.

<pre>&gt;&gt;&gt; squares = []
&gt;&gt;&gt; for x in range(10):
...     squares.append(x**2)
...
&gt;&gt;&gt; squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]</pre>

针对上的运算,我们可以通过下面的方式得到相同的结果:

<pre>squares = [x**2 for x in range(10)]</pre>

当然上面的表达式同样可以通过lambda表达实现:

<tt>squares = map(lambda x: x**2, range(10)),</tt>

<tt>但是它相比较来说更加容易让人理解.</tt>

同样列表推导式还可以包含一些括号括起来的运算逻辑.而且还可以有很多的for或者if判断.

<pre>&gt;&gt;&gt; [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]</pre>

上面的表达式等同于:

<pre>&gt;&gt;&gt; combs = []
&gt;&gt;&gt; for x in [1,2,3]:
...     for y in [3,1,4]:
...         if x != y:
...             combs.append((x, y))
...
&gt;&gt;&gt; combs
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]</pre>

如果表达式是一个元组,就需要把它括起来:

<pre>vec = [-4, -2, 0, 2, 4]
# create a new list with the values doubled
[x*2 for x in vec]

# filter the list to exclude negative numbers
[x for x in vec if x &gt;= 0]

# apply a function to all the elements
[abs(x) for x in vec]

# call a method on each element
freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
[weapon.strip() for weapon in freshfruit]

# create a list of 2-tuples like (number, square)
[(x, x**2) for x in range(6)]

# the tuple must be parenthesized, otherwise an error is raised
[x, x**2 for x in range(6)]
  File "&lt;stdin&gt;", line 1
    [x, x**2 for x in range(6)]
               ^
SyntaxError: invalid syntax
# flatten a list using a listcomp with two 'for'
vec = [[1,2,3], [4,5,6], [7,8,9]]
[num for elem in vec for num in elem]</pre>

相关链接:

<http://docs.python.org/tutorial/datastructures.html#list-comprehensions>  
[Django官方文档TOC][1]

 [1]: http://www.yyxzy.org/2011/11/%E6%88%91%E5%87%86%E5%A4%87%E5%9C%A8%E6%8E%A5%E4%B8%8B%E6%9D%A5%E8%AF%BB%E4%B8%80%E8%AF%BBdjango%E7%9A%84%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3/ "Django文档"