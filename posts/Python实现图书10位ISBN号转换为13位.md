---
title: Python实现图书10位ISBN号转换为13位
date: '2011-05-25 05:28:03'
description: 
tags: ['10''13''ISBN''python''图书''转换'']
categories: ['Python''技术'']
---

&nbsp; &nbsp; ISBN是图书的一个国际通用编号，详细信息可参考维基百科中的词条：[http://zh.wikipedia.org/wiki/ISBN](http://zh.wikipedia.org/wiki/ISBN)。

&nbsp; &nbsp; ISBN在07年前使用的是10位编号，07年后并入国际货品编号，升级为13位，以下为将10位编号转换为13位编号的Python代码：

def isbn10to13(isbn):
    if len(isbn) != 10:
        return None
    isbn = "978"+isbn[:-1]
    sum = 0
    for i, b in enumerate(isbn):
        sum += (1 if i % 2 == 0 else 3) * int(b)
    return "%s%d" % (isbn, (10 - sum % 10) % 10)

&nbsp; &nbsp; 输入内容为10位的ISBN号去除连接符“-”的字符串，输出内容为13位的ISBN号去除连接符“-”的字符串。主要的工作在于计算出最后一位的校验码。
