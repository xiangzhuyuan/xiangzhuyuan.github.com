---
title: asp.net下的缓存的一个实现以及.net下的HttpRuntime对象的属性
author: mathewxiang
layout: post
permalink: >
  /2010/11/asp-net%e4%b8%8b%e7%9a%84%e7%bc%93%e5%ad%98%e7%9a%84%e4%b8%80%e4%b8%aa%e5%ae%9e%e7%8e%b0%e4%bb%a5%e5%8f%8a-net%e4%b8%8b%e7%9a%84httpruntime%e5%af%b9%e8%b1%a1%e7%9a%84%e5%b1%9e%e6%80%a7/
categories:
  - 默认
---
<pre><span style="color: #0000ff">using</span> System;
<span style="color: #0000ff">using</span> System.Collections.Generic;
<span style="color: #0000ff">using</span> System.Linq;
<span style="color: #0000ff">using</span> System.Text;
<span style="color: #0000ff">using</span> System.Web;
<span style="color: #0000ff">using</span> System.Collections;
<span style="color: #0000ff">using</span> System.Web.Caching;

<span style="color: #0000ff">namespace</span> CCAS.BLL
{
    <span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> CacheHelper
    {
        <span style="color: #808080">/// &lt;summary></span>
        <span style="color: #808080">/// 建立缓存</span>
        <span style="color: #808080">/// &lt;/summary></span>
        <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">object</span> TryAddCache(<span style="color: #0000ff">string</span> key, <span style="color: #0000ff">object</span> <span style="color: #0000ff">value</span>, CacheDependency dependencies, DateTime absoluteExpiration,
            TimeSpan slidingExpiration, CacheItemPriority priority, CacheItemRemovedCallback onRemovedCallback)
        {
            <span style="color: #0000ff">if</span> (HttpRuntime.Cache[key] == <span style="color: #0000ff">null</span> &#038;&#038; <span style="color: #0000ff">value</span> != <span style="color: #0000ff">null</span>)
                <span style="color: #0000ff">return</span> HttpRuntime.Cache.Add(key, <span style="color: #0000ff">value</span>, dependencies, absoluteExpiration, slidingExpiration, priority, onRemovedCallback);
            <span style="color: #0000ff">else</span>
                <span style="color: #0000ff">return</span> <span style="color: #0000ff">null</span>;
        }
        <span style="color: #808080">/// &lt;summary></span>
        <span style="color: #808080">/// 获取缓存</span>
        <span style="color: #808080">/// &lt;/summary></span>
        <span style="color: #808080">/// </span>
        <span style="color: #808080">/// &lt;returns>&lt;/returns></span>
        <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">object</span> GetCache(<span style="color: #0000ff">string</span> key)
        {
            <span style="color: #0000ff">return</span> HttpRuntime.Cache[key];
        }


        <span style="color: #808080">/// &lt;summary></span>
        <span style="color: #808080">/// 移除缓存</span>
        <span style="color: #808080">/// &lt;/summary></span>
        <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">object</span> TryRemoveCache(<span style="color: #0000ff">string</span> key)
        {
            <span style="color: #0000ff">if</span> (HttpRuntime.Cache[key] != <span style="color: #0000ff">null</span>)
                <span style="color: #0000ff">return</span> HttpRuntime.Cache.Remove(key);
            <span style="color: #0000ff">else</span>
                <span style="color: #0000ff">return</span> <span style="color: #0000ff">null</span>;
        }

        <span style="color: #808080">/// &lt;summary></span>
        <span style="color: #808080">/// 移除键中带某关键字的缓存</span>
        <span style="color: #808080">/// &lt;/summary></span>
        <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">void</span> RemoveMultiCache(<span style="color: #0000ff">string</span> keyInclude)
        {
            IDictionaryEnumerator CacheEnum = HttpRuntime.Cache.GetEnumerator();
            <span style="color: #0000ff">while</span> (CacheEnum.MoveNext())
            {
                <span style="color: #0000ff">if</span> (CacheEnum.Key.ToString().IndexOf(keyInclude.ToString()) >= 0)
                    HttpRuntime.Cache.Remove(CacheEnum.Key.ToString());
            }

        }

        <span style="color: #808080">/// &lt;summary></span>
        <span style="color: #808080">/// 移除所有缓存</span>
        <span style="color: #808080">/// &lt;/summary></span>
        <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">void</span> RemoveAllCache()
        {
            IDictionaryEnumerator CacheEnum = HttpRuntime.Cache.GetEnumerator();
            <span style="color: #0000ff">while</span> (CacheEnum.MoveNext())
            {
                HttpRuntime.Cache.Remove(CacheEnum.Key.ToString());
            }
        }
    }
}
</pre>

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="httpruntime_namespace" border="0" alt="httpruntime_namespace" src="http://images.cnblogs.com/cnblogs_com/mathewxiang/Windows-Live-Writer/eeaea08eb8af_8E50/httpruntime_namespace_thumb_1.png" width="347" height="406" />][1]

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="httpruntime" border="0" alt="httpruntime" src="http://images.cnblogs.com/cnblogs_com/mathewxiang/Windows-Live-Writer/eeaea08eb8af_8E50/httpruntime_thumb_1.png" width="547" height="173" />][2]

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="httpruntime_param" border="0" alt="httpruntime_param" src="http://images.cnblogs.com/cnblogs_com/mathewxiang/Windows-Live-Writer/eeaea08eb8af_8E50/httpruntime_param_thumb.png" width="1071" height="389" />][3]

 [1]: http://images.cnblogs.com/cnblogs_com/mathewxiang/Windows-Live-Writer/eeaea08eb8af_8E50/httpruntime_namespace_4.png
 [2]: http://images.cnblogs.com/cnblogs_com/mathewxiang/Windows-Live-Writer/eeaea08eb8af_8E50/httpruntime_4.png
 [3]: http://images.cnblogs.com/cnblogs_com/mathewxiang/Windows-Live-Writer/eeaea08eb8af_8E50/httpruntime_param_2.png