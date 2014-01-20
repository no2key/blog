---
title: py2exe打包BeautifulSoup遇到问题及解决
date: '2012-03-25 04:49:39'
description: 
categories: ['python py2exe BeautifulSoup easy_install pip', 'Uncategorized']
---

今天用py2exe打包一个小程序，但是怎么都不能够找到BeautifulSoup模块，经过Google得知，py2exe无法读取压缩的egg文件，解决方法重新用解压方法安装BeautifulSoup，同时发现pip比easy_install要更方便，于是安装了pip。OK，打包成功，大功告成。
