---
title: Stack Exchang网站架构
author: mathewxiang
layout: post
permalink: /2012/03/stack-exchang%e7%bd%91%e7%ab%99%e6%9e%b6%e6%9e%84/
categories:
  - 编程,代码
tags:
  - stack exchang
---
##### 由Kyle Brandt发布在<http://blog.serverfault.com/2011/02/11/stack-exchanges-architecture-in-bullet-points/>

 

I thought as a break form the normal prose some of our readers might enjoy a short overview of the Stack Exchange Network (including Stack Overflow, Server Fault, and Super User) from a technical view:  
#### Traffic:

*   95 Million Page Views a Month 
    *   800 HTTP requests a second 
        *   180 DNS requests a second 
            *   55 Megabits per second</ul> 
            #### Data Centers:
            
            *   1 Rack with [Peak Internet][1] in OR (Hosts our [chat][2] and [Data Explorer][3]) 
                *   2 Racks with [Peer 1][4] in NY (Hosts the rest of the Stack Exchange Network)</ul> 
                #### Production Servers*:
                
                *   12 Web Servers (Windows Server 2008 R2) 
                    *   2 Database Servers (Windows Server 2008 R2 and SQL Server 2008 R2) 
                        *   2 Load Balancers (Ubuntu Server and HAProxy) 
                            *   2 Caching Servers (Redis on CentOS) 
                                *   1 Router / Firewall (Ubuntu Server) 
                                    *   3 DNS Servers (Bind on CentOS)</ul> 
                                    #### Software and Technologies Used:
                                    
                                    *   [C# / .NET][5] 
                                        *   [Windows Server 2008 R2][6] 
                                            *   [SQL Server 2008 R2][7] 
                                                *   [Ubuntu Server][8] 
                                                    *   [CentOS][9] 
                                                        *   [HAProxy][10] for load balancing 
                                                            *   [Redis][11] for caching 
                                                                *   [CruiseControl.NET][12] for builds 
                                                                    *   [Lucene.NET][13] for search 
                                                                        *   [Bacula][14] for backups 
                                                                            *   [Nagios][15] (with n2rrd and drraw plugins) for monitoring 
                                                                                *   [Splunk][16] for logs 
                                                                                    *   [SQL Monitor from Red Gate][17] for SQL Server monitoring 
                                                                                        *   [Mercurial][18] / [Kiln][19] for source control 
                                                                                            *   [Bind][20] for DNS</ul> 
                                                                                            #### Developers and System Administrators:
                                                                                            
                                                                                            *   14 Developers 
                                                                                                *   2 System Administrators</ul> 
                                                                                                *(excludes fail over and management servers) 
                                                                                                Posted by **Kyle Brandt (@kylembrandt)** on February 11th, 2011  
                                                                                                Filed under [Hardware][21], [Software][22]

 [1]: http://www.peakinternet.com/
 [2]: http://chat.stackexchange.com/
 [3]: http://data.stackexchange.com/
 [4]: http://www.peer1.com/
 [5]: http://www.microsoft.com/net/
 [6]: http://www.microsoft.com/windowsserver2008/en/us/default.aspx
 [7]: http://www.microsoft.com/sqlserver/en/us/default.aspx
 [8]: http://www.ubuntu.com/server
 [9]: http://www.centos.org/
 [10]: http://haproxy.1wt.eu/
 [11]: http://redis.io/
 [12]: http://sourceforge.net/projects/ccnet/
 [13]: http://lucene.apache.org/lucene.net/
 [14]: http://www.bacula.org/en/
 [15]: http://www.nagios.org/
 [16]: http://www.splunk.com/
 [17]: http://www.red-gate.com/products/dba/sql-monitor/
 [18]: http://mercurial.selenic.com/
 [19]: http://www.fogcreek.com/kiln/
 [20]: http://www.isc.org/software/bind
 [21]: http://blog.serverfault.com/category/hardware/
 [22]: http://blog.serverfault.com/category/software/