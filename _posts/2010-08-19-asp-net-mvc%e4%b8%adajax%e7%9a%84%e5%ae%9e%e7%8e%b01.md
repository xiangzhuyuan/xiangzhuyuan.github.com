---
title: asp.net mvc中Ajax的实现1
author: mathewxiang
layout: post
permalink: /2010/08/asp-net-mvc%e4%b8%adajax%e7%9a%84%e5%ae%9e%e7%8e%b01/
categories:
  - 默认
---
<pre><strong>利用Jquery：</strong></pre>

<pre><pre>这里实现一个最简单的留言板，数据存储在一个List&lt;string>中。</pre>


<pre>在View中引用Jquery：</pre>


<pre><pre>    </pre>


<pre>添加下面脚本：</pre>


<pre><p>
  <p>
    <img src="http://www.xueit.com/upload/downloadpic/201007/245994332201071823463978.gif" /> Code <p>
      
    </p>    
    
  </p></pre>
  
  
  <pre>创建控制器：</pre>
  
  
  <pre><p>
  <p>
    <img src="http://www.xueit.com/upload/downloadpic/201007/245994332201071823463978.gif" /> Code [http://www.xueit.com]
  </p>
  
  <p>
    <pre><p>
  public class CommentController : Controller
  {
      private IList&lt;string> _comments = new List&lt;string>();
  
      public ActionResult Index()
      {
          return View(_comments);
      }
  
      public ActionResult IndexAjaxHelp()
      {
          return View(_comments);
      }
  
      public ActionResult AddComment(string comment)
      {
          _comments.Add("<li>
    "   comment   "
  </li>");
          return Content(string.Join("\n", _comments.ToArray()));
      }
  
  }
</p></pre>
    
    
    <pre>创建View表单：</pre>
    
    
    <pre><p>
  <p>
    <img src="http://www.xueit.com/upload/downloadpic/201007/245994332201071823463978.gif" /> Code [http://www.xueit.com]
  </p>
  
  <p>
    <pre><p>
  <h4>
    Comments
  </h4>    
      
  
  <ul id="comments">
    
  </ul>
      
      &lt;% using (Html.BeginForm("AddComment","Comment",FormMethod.Post,new {@class="hijax"})) { %>    
          &lt;%= Html.TextArea("Comment", new{rows=5, cols=50}) %>
          
  
  <button type="submit">Add Comment</button>
               <span id="indicator" style="display:none"><img src="http://www.cnblogs.com/content/load.gif" alt="loading..." /></span>                                 
      &lt;% } %>
</p></pre>
    
    
    <pre>效果：</pre>
    
    
    <pre><a href="http://images.cnblogs.com/cnblogs_com/zhuqil/WindowsLiveWriter/Asp.netmvc2Ajax_EBA5/3_2.png"><img title="3" border="0" alt="3" src="http://www.xueit.com/upload/downloadpic/201007/5902752902010718234639375.png" width="784" height="321" /></a> </pre>
    
    
    <h4>
      Ajax Helper。
    </h4>
    
    
    <pre><strong></strong></pre>
    
    
    <pre>将最简单的留言板修改成Ajax Helper的方式。</pre>
    
    
    <p>
      <a href="http://11011.net/software/vspaste"></a>
    </p>
    
    
    <p>
      1、首先了解一下Ajax Helper下面四种方法。
    </p>
    
    
    <p>