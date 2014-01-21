---
title: 一个Python函数：执行MySQL的SQL文件
date: '2011-04-29 07:30:26'
description: 
tags: ['mysql''python''sql文件'']
categories: ['Python''技术'']
---

有些时候，我们需要通过python来执行SQL文件，那么这个函数就有用武之地了。调用之前确保安装了mysql。Linux和Windows应该是都可以用的，Linux下没有测试过。

from subprocess import Popen, PIPE

def excSQLFile(host, db, user, passwd, charset, filename):
    process = Popen('mysql -h%s -D%s -u%s -p%s --default-character-set=%s' \
        % (host, db, user, passwd, charset),
        stdout=PIPE, stdin=PIPE, shell=True)
    output = process.communicate('source ' + filename)[0]
    return output
