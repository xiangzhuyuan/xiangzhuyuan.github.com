---
layout: post
title: jQuery获取Select选择的Text和 Value(转)
date: 2010-10-14 19:09
comments: true
categories: []
---
jQuery获取Select选择的Text和Value:<br/>
语法解释：<br/>
1. $("#select_id").change(function(){//code...});   <font color="#008000"><span class="green">//为Select添加事件，当选择其中一项时触发</span><br/></font>2. var checkText=$("#select_id").find("option:selected").text();  <font color="#008000"><span class="green">//获取Select选择的Text</span><br/></font>3. var checkValue=$("#select_id").val();  <font color="#008000"><span class="green">//获取Select选择的Value</span><br/></font>4. var checkIndex=$("#select_id ").get(0).selectedIndex;  <font color="#008000"><span class="green">//获取Select选择的索引值</span><br/></font>5. var maxIndex=$("#select_id option:last").attr("index");  <span class="green"><font color="#008000">//获取Select最大的索引值</font></span> <br/>
jQuery设置Select选择的 Text和Value:<br/>
语法解释：<br/>
1. $("#select_id ").get(0).selectedIndex=1;  <font color="#008000"><span class="green">//设置Select索引值为1的项选中</span><br/></font>2. $("#select_id ").val(4);   <font color="#008000"><span class="green">// 设置Select的Value值为4的项选中</span><br/></font>3. $("#select_id option[text='jQuery']").attr("selected", true);   <font color="#008000"><span class="green">//设置Select的Text值为jQuery的项选中</span><br/></font>
<div class="div">jQuery添加/删除Select的Option项：<br/>
语法解释：<br/>
1. $("#select_id").append("<option value='Value'>Text</option>");  <font color="#008000"><span class="green">//为Select追加一个Option(下拉项)</span><br/></font>2. $("#select_id").prepend("<option value='0'>请选择</option>");  <font color="#008000"><span class="green">//为Select插入一个Option(第一个位置)</span><br/></font>3. $("#select_id option:last").remove();  <font color="#008000"><span class="green">//删除Select中索引值最大Option(最后一个)</span><br/></font>4. $("#select_id option[index='0']").remove();  <font color="#008000"><span class="green">//删除Select中索引值为0的Option(第一个)</span><br/></font>5. $("#select_id option[value='3']").remove();  <font color="#008000"><span class="green">//删除Select中Value='3'的Option</span><br/></font>5. $("#select_id option[text='4']").remove();  <span class="green"><font color="#008000">//删除Select中Text='4'的Option</font></span></div>
<div class="div"> </div>
<div class="div"> </div>
<div class="div"><span class="green">
<p>http://www.cnblogs.com/SAL2928/archive/2008/10/28/1321285.html</p>
<p>jquery radio取值，checkbox取值，select取值，radio选中，checkbox选中，select选中，及其相关 <br/>
获 取一组radio被选中项的值 <br/>
var item = $('input[@name=items][@checked]').val(); <br/>
获 取select被选中项的文本 <br/>
var item = $("select[@name=items] option[@selected]").text(); <br/>
select下拉框的第二个元素为当前选中值 <br/>
$('#select_id')[0].selectedIndex = 1; <br/>
radio单选组的第二个元素为当前选中值 <br/>
$('input[@name=items]').get(1).checked = true; <br/><br/>
获取值： <br/><br/>
文本框，文本区域：$("#txt").attr("value")； <br/>
多选框 checkbox：$("#checkbox_id").attr("value")； <br/>
单选组radio：     $("input[@type=radio][@checked]").val(); <br/>
下拉框select： $('#sel').val(); <br/><br/>
控制表单元素： <br/>
文本框，文本区域：$("#txt").attr("value",'');//清空内容 <br/>
$("#txt").attr("value",'11');//填充内容 <br/><br/>
多选框checkbox： $("#chk1").attr("checked",'');//不打勾 <br/>
$("#chk2").attr("checked",true);//打勾 <br/>
if($("#chk1").attr('checked')==undefined) //判断是否已经打勾 <br/><br/>
单选组 radio：      $("input[@type=radio]").attr("checked",'2');//设置value=2的项目为当前选中项 <br/>
下拉框 select：     $("#sel").attr("value",'-sel3');//设置value=-sel3的项目为当前选中项 <br/>
$("<option value='1'>1111</option><option value='2'>2222</option>").appendTo("#sel")//添加下拉框的option <br/>
$("#sel").empty()；//清空下拉框</p>
<p>----------------------------------------------------------------------------------------------------</p>
<p> </p>
<p>//遍历option和添加、移除option<br/>
function changeShipMethod(shipping){<br/><wbr/>var len = $("select[@name=ISHIPTYPE] option").length<br/><wbr/>if(shipping.value != "CA"){<br/><wbr/><wbr/>$("select[@name=ISHIPTYPE] option").each(function(){<br/><wbr/><wbr/><wbr/>if($(this).val() == 111){<br/><wbr/><wbr/><wbr/><wbr/>$(this).remove();<br/><wbr/><wbr/><wbr/>}<br/><wbr/><wbr/>});<br/><wbr/>}else{<br/><wbr/><wbr/>$("<option value='111'>UPS Ground</option>").appendTo($("select[@name=ISHIPTYPE]"));<br/><wbr/>}<br/>
}</p>
<p><br/>
//取得下拉選單的選取值</p>
<p>$(#testSelect option:selected').text();<br/>
或$("#testSelect").find('option:selected').text();<br/>
或$("#testSelect").val();<br/>
//////////////////////////////////////////////////////////////////<br/>
记 性不好的可以收藏下：<br/>
1,下拉框:</p>
<p>var cc1 <wbr/><wbr/>= $(".formc select[@name='country'] option[@selected]").text(); //得到下拉菜单的选中项的文本(注意中间有空格)<br/>
var cc2 = $('.formc select[@name="country"]').val(); <wbr/><wbr/>//得到下拉菜单的选中项的值<br/>
var cc3 = $('.formc select[@name="country"]').attr("id"); //得到下拉菜单的选中项的ID属性值<br/>
$("#select").empty();//清空下拉框 //$("#select").html('');<br/>
$("<option value='1'>1111</option>").appendTo("#select")//添加下拉框的option</p>
<p>稍微解释一下:<br/>
1.select[@name='country'] option[@selected] 表示具有name 属性，<br/>
并 且该属性值为'country' 的select元素 里面的具有selected 属性的option 元素；<br/>
可以看出有@开头的就表示后面跟 的是属性。</p>
<p>2,单选框:<br/>
$("input[@type=radio][@checked]").val(); <wbr/><wbr/>//得到单选框的 选中项的值(注意中间没有空格)<br/>
$("input[@type=radio][@value=2]").attr("checked",'checked'); //设置单选框value=2的为选中状态.(注意中间没有空格)</p>
<p>3,复选框:<br/>
$("input[@type=checkbox][@checked]").val(); //得到复选框的选中的第一项的值<br/>
$("input[@type=checkbox][@checked]").each(function() { //由于复选框一般选中的是多个,所以可以循环输出<br/><wbr/><wbr/>alert($(this).val());<br/><wbr/><wbr/>});</p>
<p>$("#chk1").attr("checked",'');//不打勾<br/>
$("#chk2").attr("checked",true);// 打勾<br/>
if($("#chk1").attr('checked')==undefined){} //判断是否已经打勾</p>
<p><br/>
当然jquery的选择器是强大的. 还有很多方法.</p>
<p><script src="jquery-1.2.1.js" type="text/javascript"></script><br/>
<script language="javascript" type="text/javascript"><br/>
$(document).ready(function(){<br/>
$("#selectTest").change(function()<br/>
{<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>//alert("Hello");<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>//alert($("#selectTest").attr("name"));<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>//$("a").attr("href","xx.html");<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>//window.location.href="xx.html";<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>//alert($("#selectTest").val());<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>alert($("#selectTest option[@selected]").text());<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>$("#selectTest").attr("value", "2");</p>
<p>});<br/>
});<br/>
</script></p>
<p><br/>
<a href="#">aaass</a></p>
<p><!--下拉框--><br/>
<select id="selectTest" name="selectTest"><br/>
<option value="1">11</option><br/>
<option value="2">22</option><br/>
<option value="3">33</option><br/>
<option value="4">44</option><br/>
<option value="5">55</option><br/>
<option value="6">66</option><br/>
</select><br/>
jquery radio取值，checkbox取值，select取值，radio选中，checkbox选中，select选中，及其相关获取一组radio被选中 项的值<br/>
var item = $('input[@name=items][@checked]').val();<br/>
获取select被选 中项的文本<br/>
var item = $("select[@name=items] option[@selected]").text();<br/>
select 下拉框的第二个元素为当前选中值<br/>
$('#select_id')[0].selectedIndex = 1;<br/>
radio单选组的第二个 元素为当前选中值<br/>
$('input[@name=items]').get(1).checked = true;<br/>
获取值：<br/>
文本 框，文本区域：$("#txt").attr("value")；<br/>
多选框 checkbox：$("#checkbox_id").attr("value")；<br/>
单选组radio： $("input[@type=radio][@checked]").val();<br/>
下拉框select： $('#sel').val();<br/>
控 制表单元素：<br/>
文本框，文本区域：$("#txt").attr("value",'');//清空内容<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>$("#txt").attr("value",'11');// 填充内容<br/>
多选框checkbox： $("#chk1").attr("checked",'');//不打勾<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>$("#chk2").attr("checked",true);// 打勾<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>if($("#chk1").attr('checked')==undefined) //判断是否已经打勾<br/>
单选组radio： $("input[@type=radio]").attr("checked",'2');//设置value=2的项目为当前选中项<br/>
下拉框 select： $("#sel").attr("value",'-sel3');//设置value=-sel3的项目为当前选中项<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>$("<optionvalue='1'& gt;1111</option><optionvalue='2'>2222</option& gt;").appendTo("#sel")//添加下拉框的option<br/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/><wbr/>$("#sel").empty()；// 清空下拉框</p>
<p>获取一组radio被选中项的值<br/>
var item = $('input[@name=items][@checked]').val();<br/>
获取select被选中项的文本<br/>
var item = $("select[@name=items] option[@selected]").text();<br/>
select下拉框的第二个元素为当 前选中值<br/>
$('#select_id')[0].selectedIndex = 1;<br/>
radio单选组的第二个元素为当前选中值<br/>
$('input[@name=items]').get(1).checked = true;<br/>
获取值：<br/>
文本框，文本区域：$("#txt").attr("value")；<br/>
多选框 checkbox：$("#checkbox_id").attr("value")；<br/>
单选组radio： $("input[@type=radio][@checked]").val();<br/>
下拉框select： $('#sel').val();<br/>
控 制表单元素：<br/>
文本框，文本区域：$("#txt").attr("value",'');//清空内容<br/>
$("#txt").attr("value",'11');// 填充内容<br/>
多选框checkbox： $("#chk1").attr("checked",'');//不打勾<br/>
$("#chk2").attr("checked",true);// 打勾<br/>
if($("#chk1").attr('checked')==undefined) //判断是否已经打勾<br/>
单选组radio： $("input[@type=radio]").attr("checked",'2');//设置value=2的项目为当前选中项<br/>
下拉框 select： $("#sel").attr("value",'-sel3');//设置value=-sel3的项目为当前选中项<br/>
$("<option value='1'>1111</option><option value='2'>2222</option>").appendTo("#sel")//添加下拉框的option<br/>
$("#sel").empty()；// 清空下拉框</p>
</span></div>
