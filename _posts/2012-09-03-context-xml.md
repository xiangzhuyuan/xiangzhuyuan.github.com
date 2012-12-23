---
title: context.xml
author: mathewxiang
layout: post
permalink: /2012/09/context-xml/
categories:
  - Java
  - Web
tags:
  - java
  - tomcat
---
**context.xml**这个文件对于一个web工程来说是可选的.他包含一个**<Context>**标签.  
他可以用来定义一个工程的自己行为.例如JNDI等.<!--more-->

这个文件是在tomcat5中产生的.是从**server.xml**中移出来的.当然这个**context**内容也可以放在tomcat的根目录下的conf文件夹中.或者可以放在你的工程的**META-INF**文件下面.把它命名为context.xml.  
上面的第二种方法意思就是不用重启tomcat.你可以在修改了web.xml之后直接刷新页面看到效果.或者通过**Tomcat管理器**(http://wiki.metawerx.net/wiki/TomcatManager)来手动重载.  
你的程序中是context.xml必须放在根目录META-INF下.就是/META-INF/context.xml.  
META-INF和WEB-INF应该是同一个级别的文件夹.非包含关系.

<pre>index.jsp
/WEB-INF
    web.xml
    /lib
        myjar.jar
    /classes
        myclass.class
/META-INF
    context.xml</pre>

可是,意外的是目前很多的程序并没有使用这个特性,尽管比较有用.把server.xml下所有的依赖提出来放到各自应用的context.xml中,让程序更加容易扩展和部署.

**context.xml文件的配置例子:**  
下面的例子是配置了一个mysql的数据库连接池,还有安全域.

<pre>&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;Context&gt;
    &lt;!-- Specify a JDBC datasource --&gt;
    &lt;Resource name="jdbc/mydatabase" 
              auth="Container"
              type="javax.sql.DataSource" 
              username="YOUR_USERNAME" 
              password="YOUR_PASSWORD"
              driverClassName="com.mysql.jdbc.Driver"
              url="jdbc:mysql://mysql.metawerx.net:3306/YOUR_DATABASE_NAME?autoReconnect=true"
              validationQuery="select 1"
              maxActive="10" 
              maxIdle="4"/&gt;

    &lt;!-- Specify the security realm and location of the users file
    &lt;Realm className="org.apache.catalina.realm.MemoryRealm" 
           pathname="/tomcat/webapps/ROOT/WEB-INF/users.xml" /&gt;
    --&gt;
&lt;/Context&gt;</pre>

**访问在上面配置的数据源:**

<pre>// Get DataSource
Context ctx = new InitialContext();
DataSource ds = (DataSource)ctx.lookup("java:comp/env/jdbc/mydatabase");
// Get Connection and Statement
Connection c = ds.getConnection();
Statement s = c.createStatement();</pre>

附件的数据库就可以在context.xml文件中继续追加元素.使用不同的名称(ex:jdbc/customerDatabase).  
**访问上面配置的安全域:**  
上面的安全的配置需要更进一步的在web.xml文件中的配置,详细的情况可以去看看这个文章: [Securing your site with Container Managed Security][1]

**注意:**  
在很多的例子中,标签是需要很多的属性的,例如path,docBase.这种情况其实主要是这个标签配置在server.xml中.但是如果要是在context.xml中就是可选的属性了.全局的一些配置就需要配置在server.xml中的节点了.在<CATALINA>/conf下.

**陷阱/排错/调试JNDI数据源**  
一般来说JNDI是很难调试的,因为没有debug输出,如果遇到问题从以下几个方面来查看:

1.  配置JNDI数据源,确保在数据库连接驱动在**<CATALINA>/common/lib**存在.
2.  如果JNDI数据源不起作用,无法连接,确保数据库的连接字符串是正确的,可以通过telnet或者mysql的客户端连接来验证.
3.  确保在**server.xml**中节点的**deployXML**是被设置为false.不然context.xml会被忽略的.
4.  在**tomcat5.5和6**中会把**context.xml**拷贝到**<CATALINA>/conf/Standalone**这个目录,当第一次部署成功之后,之后就不会被移除或者更新,除非程序没有被部署,如果说当你修改了在**context.xml**中的配置,而没有起作用,就需要去删除**<CATALINA>/conf/Standalone**目录下的所有文件,在tomcat7中不会出现这个问题,除非copyXML被设置为false.

 

reference link:<http://wiki.metawerx.net/wiki/Context.xml>

 [1]: http://wiki.metawerx.net/wiki/SecuringYourSiteWithContainerManagedSecurity