---
title: MySQL中的insert ignore into, replace into, insert select, on duplicate key update的用法小结
date: '2011-05-23 04:29:27'
description: 
tags: ['insert''select''on''duplicate''key''ignore''mysql''update''replace''into'']
categories: ['MySQL''技术'']
---

在MySQL中进行条件插入数据时，可能会用到以下语句，现小结一下。我们先建一个简单的表来作为测试：

CREATE TABLE `books` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(200) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `NewIndex1` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;



1.insert ignore into
当插入数据时，如出现错误时，如重复数据，将不返回错误，只以警告形式返回。所以使用ignore请确保语句本身没有问题，否则也会被忽略掉。例如：


insert ignore into books (name) values ('MySQL Manual')



2.on duplicate key update
当primary或者unique重复时，则执行update语句，如update后为无用语句，如id=id，则同1功能相同，但错误不会被忽略掉。例如，为了实现name重复的数据插入不报错，可使用一下语句：


insert into books (name) values ('MySQL Manual') on duplicate key update id = id



3.insert ... select ... where not exist
根据select的条件判断是否插入，可以不光通过primary 和 unique来判断，也可通过其它条件。例如：


insert into books (name) select 'MySQL Manual' from dual where not exists (select id from books where id = 1)



4.replace into
如果存在primary or unique相同的记录，则先删除掉。再插入新记录。


replace into books SELECT 1, 'MySQL Manual' FROM books
