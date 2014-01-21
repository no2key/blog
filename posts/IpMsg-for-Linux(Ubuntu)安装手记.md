---
title: IpMsg for Linux(Ubuntu)安装手记
date: '2007-12-09 11:55:29'
description: 
tags: ['IPMsg''Linux''Ubuntu'']
categories: ['Linux''Linux&amp;Ubuntu''软件'']
---

ipmsg是一个开源的局域网消息和文件传送工具，其最大的优点是可以直接传送文件夹，并且传送速度非常快。ipmsg目前已有了windows, mac, linux版本。为了从我的Linux（Ubuntu 7.04）传送文件到局域网内一台windows机器，我试着安装了一下。

1 先下载源码
我下载的是for gnome2版本的源码
[http://www.ipmsg.org/archive/g2ipmsg-0.9.1.tar.gz](http://www.ipmsg.org/archive/g2ipmsg-0.9.1.tar.gz)
目前最新的版本是0.9.3，不过这个版本在编译是会出现问题，所以我选择了0.9.1版本，差别不大。

2 解压
在ubuntu中用命令行
`tar xzvf g2ipmsg-0.9.1.tar.gz`
，或者菜单右键用归档管理器解压即可。

3 修改语言
用文本编辑工具，比如gedit，打开src/codeset.c文件，将其中的CP932更改为CP936（英文）或者GBK（中文）并保存。

4 安装编译依赖项
`sudo apt-get install libxml-parser-perl libgnomeui-dev libpanel-applet2-dev
sudo apt-get install gettext intltool
`
5 编译
`./configure –enable-systray
make
sudo make install`

这下可用了，重启后在主菜单的附件中将会有Gnome2 IP Messenger的快捷方式。
OK，完成，可以在windows和linux之间传送文件或者文件夹了。
