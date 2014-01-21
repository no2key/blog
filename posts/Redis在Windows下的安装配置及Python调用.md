---
title: Redis在Windows下的安装配置及Python调用
date: '2011-05-17 07:42:30'
description: 
tags: ['python''redis''redis-py''windows''安装'']
categories: ['NoSQL''技术'']
---

Redis是一个Key-Value数据库，优点是简单，高效，稳定；缺点是所有数据存放于内存（会定期dump到磁盘），当然内存小时可以配置虚拟内存，不过性能会有所下降。
官方只提供源代码下载，并且不支持Windows，可从第三方下载Windows下的预编译文件，下载地址：

[https://github.com/dmajkic/redis/downloads](https://github.com/dmajkic/redis/downloads)

解压后，所有命令均在一个目录下，服务器端直接运行redis-server.exe即可，如果需要特殊配置，可以指定配置文件或者使用redis-client进行配置。配置文件其实就是配置命令的一个集合。redis的配置命令（2.2之后）可以做到在不重启服务的情况下生效，包括redis版本更新，slave转为master等等。

Redis的Python接口目前比较成熟的是redis-py，项目地址为https://github.com/andymccurdy/redis-py，通过git可将源码下载到本地，git的安装和使用请参考[《Git使用123》](http://www.lunny.info/html/2011/01/24/625330.html)。

git clone https://github.com/andymccurdy/redis-py.git
cd redis-py
python setup install

redis-py的使用请参考[https://github.com/andymccurdy/redis-py](https://github.com/andymccurdy/redis-py)。
