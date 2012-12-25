---
layout: post
title: LINQ和Entity Framework之间的比较
date: 2010-08-12 22:49
comments: true
categories: []
---
LINQ to SQL advantages over the Entity Framework:
➤➤ Easy to get started and query 
Entity Framework advantages over LINQ to SQL:
➤➤ Enables you to build a conceptual model of the database rather than purely working with a 1:1 domain model of the database as objects (such as having one object mapped to multiple database tables, inheritance support, and defining complex properties).
➤➤ Able to generate a database from your entity model.
➤➤ Support for databases other than just SQL Server.
➤➤ Support for many-to-many relationships.
➤➤ Lazy loading and eager loading support.
➤➤ Synchronization to get database updates will not lose your customizations to your model.
➤➤ Will continue to evolve, whereas LINQ to SQL development will from now on be minimal.

LINQ和Entity Framework之间的比较

相对于Entity Framework，LINQ比较容易学习。
相对于LINQ，Entity Framework具有以下的优点：
1）可以建立一个概念意义上的数据库对象，而不是一个简单的1对1数据库模型作为对象（比如说一个对象可以映射到数据库中的多个表，继承性，还有定义复杂的属性。）
2）可以通过实体模型生成对于的数据库
3）可以支持多类型的数据库
4）可以支持多多的关系
5）延迟和及时加载
6）
7）Entity Framework技术会继续发展，而LINQ的开发也就那样了！

