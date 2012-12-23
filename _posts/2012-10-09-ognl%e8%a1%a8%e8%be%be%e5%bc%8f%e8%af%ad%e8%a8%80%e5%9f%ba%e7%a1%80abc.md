---
title: OGNL表达式语言基础ABC
author: mathewxiang
layout: post
permalink: /2012/10/ognl%e8%a1%a8%e8%be%be%e5%bc%8f%e8%af%ad%e8%a8%80%e5%9f%ba%e7%a1%80abc/
categories:
  - Java
tags:
  - OGNL
  - Struts2
---
**OGNL表达式语言能够帮助我们访问存在于ValueStack和ActionContext中的值.**

首先让我们来看看通过OGNL来访问一个String数组的变量.在action类中我们创建一个string数组,代码如下:<!--more-->

<pre>package vaannila;

public class SampleAction {

    private  String[] sampleArray;
    {
    	sampleArray =  new String[]{"item1","item2","item3"};
    }
    public String execute()
    {
    	return "success";
    }
    public String[] getSampleArray() {
    	return sampleArray;
    }
    public void setSampleArray(String[] sampleArray) {
    	this.sampleArray = sampleArray;
    }
}</pre>

这样,在success中就能够通过下面的方式读取这个数组的值:

<pre>&lt;b&gt;Array Usage Examples&lt;/b&gt;

&lt;hr&gt;
&lt;b&gt;sampleArray :&lt;/b&gt; &lt;s:property value="sampleArray"/&gt; 

&lt;b&gt;sampleArray.length :&lt;/b&gt; &lt;s:property value="sampleArray.length"/&gt; 

&lt;b&gt;sampleArray[0] :&lt;/b&gt; &lt;s:property value="sampleArray[0]"/&gt; 

&lt;b&gt;[0].sampleArray :&lt;/b&gt; &lt;s:property value="[0].sampleArray"/&gt; 

&lt;b&gt;top.sampleArray :&lt;/b&gt; &lt;s:property value="top.sampleArray"/&gt;</pre>

下图就是页面的输出效果:

<img src="http://www.yyxzy.org/wp-content/uploads/2012/10/OgnlPic1.gif" alt="" width="612" height="172" />

上面有三种方式能够获取到sampleArray.由于这个sampleArray是在这个stack的top.所以可以通过[0]或者top这个关键字来

直接取到.

下面看看怎么获取到一个ArrayList,在action类中创建一个ArrayList:

<pre>package vaannila;

import java.util.ArrayList;
import java.util.List;

public class SampleAction {

    private  List&lt;String&gt; sampleList = new ArrayList&lt;String&gt;();
    {
        sampleList.add("listItem1");
        sampleList.add("listItem2");
        sampleList.add("listItem3");
    }
    public String execute()
    {
    	return "success";
    }
    public List&lt;String&gt; getSampleList() {
    	return sampleList;
    }
    public void setSampleList(List&lt;String&gt; sampleList) {
    	this.sampleList = sampleList;
    }
}</pre>

同样可以通过下面的方式显示这个list:

<pre>&lt;b&gt;List Usage Examples&lt;/b&gt;

&lt;hr&gt;
&lt;b&gt;sampleList :&lt;/b&gt; &lt;s:property value="sampleList"/&gt; 

&lt;b&gt;sampleList.size :&lt;/b&gt; &lt;s:property value="sampleList.size"/&gt; 

&lt;b&gt;sampleList[0] :&lt;/b&gt; &lt;s:property value="sampleList[0]"/&gt;</pre>

<img src="http://www.yyxzy.org/wp-content/uploads/2012/10/OgnlPic2.gif" alt="" width="615" height="141" />

下面再来看看怎么读取一个map类型的数据.通过在action类中创建一个map:

<pre>package vaannila;

import java.util.HashMap;
import java.util.Map;

public class SampleAction {

	private  Map&lt;Integer,String&gt; sampleMap = new HashMap&lt;Integer,String&gt;();
	private  String carMake;
	{
		sampleMap.put(new Integer(1), "one");
		sampleMap.put(new Integer(2), "two");
		sampleMap.put(new Integer(3), "three");
	}
	public String execute()
	{
		return "success";
	}
	public Map&lt;Integer, String&gt; getSampleMap() {
		return sampleMap;
	}
	public void setSampleMap(Map&lt;Integer, String&gt; sampleMap) {
		this.sampleMap = sampleMap;
	}
	public String getCarMake() {
		return carMake;
	}
	public void setCarMake(String carMake) {
		this.carMake = carMake;
	}

}</pre>

可以通过下面的方式来访问这个map:

<pre>&lt;b&gt;Map Usage Examples&lt;/b&gt;

&lt;hr&gt;
&lt;b&gt;sampleMap[1] :&lt;/b&gt; &lt;s:property value="sampleMap[1]"/&gt; 

&lt;b&gt;sampleMap.size :&lt;/b&gt; &lt;s:property value="sampleMap.size"/&gt;</pre>

当然你可以直接在jsp中声明一个map:

<pre>&lt;s:select list="#{'make1':'Ford', 'make2':'Honda', 'make3':'Toyota'}" name="carMake" label="Select "&gt;&lt;/s:select&gt;</pre>

<img src="http://www.yyxzy.org/wp-content/uploads/2012/10/OgnlPic3.gif" alt="" width="615" height="190" />

下面来看看怎么访问在action中model对象的属性name.代码如下:

<pre>package vaannila;

public class SampleAction {

    private  User user = new User();
    {
        user.setName("Eswar");
    }
    public String execute()
    {
        return "success";
    }

    public String getQuote()
    {
        return "Don't think, just do";
    }
    public User getUser() {
        return user;
    }
    public void setUser(User user) {
        this.user = user;
    }

}</pre>

可以通过下面的方式来访问:

<pre>&lt;b&gt;user.name :&lt;/b&gt; &lt;s:property value="user.name"/&gt;</pre>

同样可以在jsp中直接调用action中的一个方法:

<pre>&lt;b&gt;quote() :&lt;/b&gt; &lt;s:property value="quote()"/&gt;</pre>

<img src="http://www.yyxzy.org/wp-content/uploads/2012/10/OgnlPic4.gif" alt="" width="613" height="170" />

 

related link:<http://www.dzone.com/tutorials/java/struts-2/struts-2-example/struts-2-ognl-expression-language-example-1.html>