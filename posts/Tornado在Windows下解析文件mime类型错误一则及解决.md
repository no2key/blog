---
title: Tornado在Windows下解析文件mime类型错误一则及解决
date: '2011-02-15 08:13:06'
description: 
tags: ['mime''python''tornado''unicodedecoderror''windows'']
categories: ['Python''技术'']
---

今日遇到一则错误，tornado服务器在解析文件的mime类型时报错，无法获取，错误如下。

    codeUnicodeDecodeError: 'ascii' codec can't decode byte 0xe4 in position 0

出错误原因：
Windows注册表中保存的mime类型对应项中包含非ascii字符

解决方法：
执行regedit，找到
HKEY_LOCAL_MACHINE\SOFTWARE\Classes\MIME\Database\Content Type
在其中找到非英文字母的mime类型，例如我遇到的“视频/x-m4v”，删除即可。

如何避免：
有些程序在安装时会新增一些mime类型，如果胡乱加，那么肯定就会出问题。我遇到的这个问题，估计是哪个视频播放软件犯了一个低级错误，不该翻译的地方翻译了。这个错误一般情况下不会有什么危害，真正除了问题却有可能摸不着头脑。

附：
mime类型标准的网址：[http://www.iana.org/assignments/media-types/](http://www.iana.org/assignments/media-types/)。访问可以看到，顶级类型里不包含“视频”，只有“vedio"。
