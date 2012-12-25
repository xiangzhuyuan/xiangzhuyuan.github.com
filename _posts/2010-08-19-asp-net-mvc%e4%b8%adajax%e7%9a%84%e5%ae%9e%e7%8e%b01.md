---
layout: post
title: asp.net mvc中Ajax的实现1
date: 2010-08-19 15:55
comments: true
categories: []
---
<pre><strong>利用Jquery：</strong></pre>

<pre><pre>这里实现一个最简单的留言板，数据存储在一个List<string>中。</pre><pre>在View中引用Jquery：</pre><pre><pre>    <script src="http://www.cnblogs.com/Scripts/jquery-1.4.1.min.js" type="text/javascript"></script></pre><pre>添加下面脚本：</pre><pre><p><p><img src="http://www.xueit.com/upload/downloadpic/201007/245994332201071823463978.gif" /> Code <p></p>    <script type="text/javascript">
        //execute when the DOM has been loaded
        $(document).ready(function () {
            //wire up to the form submit event
            $("form.hijax").submit(function (event) {
                event.preventDefault();  //prevent the actual form post
                hijack(this, update_sessions, "html");
            });
        });

        function hijack(form, callback, format) {
            $("#indicator").show();
            $.ajax({
                url: form.action,
                type: form.method,
                dataType: format,
                data: $(form).serialize(),
                completed: $("#indicator").hide(),
                success: callback
            });
        }

        function update_sessions(result) {
            //clear the form
            $("form.hijax")[0].reset();
            $("#comments").append(result);
        }
    
    </script>
</p></pre><pre>创建控制器：</pre><pre><p><p><img src="http://www.xueit.com/upload/downloadpic/201007/245994332201071823463978.gif" /> Code [http://www.xueit.com]</p><p><pre><p>public class CommentController : Controller
{
    private IList<string> _comments = new List<string>();

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
        _comments.Add("<li>"   comment   "</li>");
        return Content(string.Join("\n", _comments.ToArray()));
    }

}</p></pre></pre><pre>创建View表单：</pre><pre><p><p><img src="http://www.xueit.com/upload/downloadpic/201007/245994332201071823463978.gif" /> Code [http://www.xueit.com]</p><p><pre><p><h4>Comments</h4>    
    <ul id="comments">        
    </ul>
    
    <% using (Html.BeginForm("AddComment","Comment",FormMethod.Post,new {@class="hijax"})) { %>    
        <%= Html.TextArea("Comment", new{rows=5, cols=50}) %>
        <button type="submit">Add Comment</button>
             <span id="indicator" style="display:none"><img src="http://www.cnblogs.com/content/load.gif" alt="loading..." /></span>                                 
    <% } %></p></pre><pre>效果：</pre><pre><a href="http://images.cnblogs.com/cnblogs_com/zhuqil/WindowsLiveWriter/Asp.netmvc2Ajax_EBA5/3_2.png"><img title="3" border="0" alt="3" src="http://www.xueit.com/upload/downloadpic/201007/5902752902010718234639375.png" width="784" height="321" /></a> </pre></pre></pre></pre>

<h4>Ajax Helper。</h4>

<pre><strong></strong></pre>

<pre>将最简单的留言板修改成Ajax Helper的方式。</pre>
<a href="http://11011.net/software/vspaste"></a>

<p>1、首先了解一下Ajax Helper下面四种方法。</p>

<p>
