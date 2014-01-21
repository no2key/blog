---
title: 加密软件TrueCrypt安装及使用简介（一）
date: '2010-12-21 08:16:40'
description: 
tags: ['TrueCrypt''U盘''加密''安装''开源''磁盘'']
categories: ['信息安全''软件'']
---

# **1       简介**

TrueCrypt是一款开源免费的数据加密软件，它支持如下特性：

1）  支持Windows 7/Vista/XP, Mac OS X, Linux等操作系统，加密文件或者设备可在不同操作系统间使用；

2）  可以选择AES、Serpent和Twofish等算法，也可以组合他们使用，暴力破解的难度非常高；

3）  支持加密文件，加密硬盘分区，加密整个硬盘，加密U盘等移动设备等；

4）  支持密码认证和私钥文件认证；

5）  支持双加密卷，即普通卷和隐藏卷。

# 2       安装及配置

## 2.1   安装TrueCrypt

TrueCrypt在Windows上的安装很简单，一直下一步即可。双击安装程序，如图1-1将显示TrueCrypt的使用许可，此时选择接受。

[![2-1](http://www.lunny.info/wp-content/uploads/2010/12/2-1.jpg "2-1")](http://www.lunny.info/wp-content/uploads/2010/12/2-1.jpg)

图2-1




接下来询问你是用安装版本还是解压版本，如果我们是安装在台式电脑上，那么我们选择安装，见图2-2；如果是选择将软件放到U盘中，方便在别的地方试用，则选择解压。

[![2-2](http://www.lunny.info/wp-content/uploads/2010/12/2-2.jpg "2-2")](http://www.lunny.info/wp-content/uploads/2010/12/2-2.jpg)

图2-2

点击下一步，会出现安装选项（图2-3），这一步可以选择给所有用户安装或者只安装个当前用户，另外创建系统还原点可以不选。

[![2-3](http://www.lunny.info/wp-content/uploads/2010/12/2-3.jpg "2-3")](http://www.lunny.info/wp-content/uploads/2010/12/2-3.jpg)

图2-3

点击安装，系统将显示安装日志，过一会儿安装完成，如图2-4所示：

[![2-4](http://www.lunny.info/wp-content/uploads/2010/12/2-4.jpg "2-4")](http://www.lunny.info/wp-content/uploads/2010/12/2-4.jpg)

图2-4

此时安装已经完成，会有一个快捷方式在桌面上显示。

## 2.2   配置简体中文界面

TrueCrypt支持多语言，它是通过不同的语言文件来达成多语言的。已经下载了语言文件可以直接跳到2.2.2。

### 2.2.1 下载简体中文语言包

通过TrueCrypt界面可以直接链接到语言包下载网址，步骤如图2-5所示，点击菜单栏上的【Settings】，选择【Language】，将显示语言切换界面，如图2-6所示。点击界面上的【download language pack】，将会打开语言包下载网址。

[![2-5](http://www.lunny.info/wp-content/uploads/2010/12/2-5.jpg "2-5")](http://www.lunny.info/wp-content/uploads/2010/12/2-5.jpg)

图2-5

[![2-6](http://www.lunny.info/wp-content/uploads/2010/12/2-6.jpg "2-6")](http://www.lunny.info/wp-content/uploads/2010/12/2-6.jpg)

图2-6

将下载到的语言包文件解压，将Language.zh-cn.xml文件拷贝到c:\program files\TrueCrypt文件夹下。关闭并重新打开TrueCrypt。

[![2-7](http://www.lunny.info/wp-content/uploads/2010/12/2-7.jpg "2-7")](http://www.lunny.info/wp-content/uploads/2010/12/2-7.jpg)

图2-7

### 2.2.1将界面语言修改为简体中文

点击菜单栏上的【Settings】，选择【Language】，将显示语言切换界面，此时选择【简体中文】，点击【OK】即可。

[![2-8](http://www.lunny.info/wp-content/uploads/2010/12/2-8.jpg "2-8")](http://www.lunny.info/wp-content/uploads/2010/12/2-8.jpg)

图2-8
