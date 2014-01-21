---
title: 加密软件TrueCrypt安装及使用简介（二）
date: '2010-12-21 08:12:02'
description: 
tags: ['TrueCrypt' 'U盘' '加密' '安装' '开源' '磁盘']
categories: ['信息安全' '软件']
---

# 3       TrueCrypt使用

## 3.1   基本原理

TrueCrypt在使用时类似于虚拟光驱之类的软件。首先将加密的卷文件、或者加密的U盘，加密的分区等等都加载为某个Windows盘符，然后就跟使用本地分区一样进行使用就可以了。使用完成之后再卸载掉。

这里需要注意，TrueCrypt的加密方式是先创建加密容器（加密卷或者分区、设备），然后将需要加密的内容存放到这个加密容器中。

## 3.2   创建文件加密卷

TrueCrypt启动后默认在Windows通知区有一个小图标，点击该图标，将显示TrueCrypt的主界面，如图3-1所示。

[![3-1](http://www.lunny.info/wp-content/uploads/2010/12/3-1.jpg "3-1")](http://www.lunny.info/wp-content/uploads/2010/12/3-1.jpg)

图3-1


点击【创建加密卷】，将显示加密卷创建向导，如图3-2所示：

[![3-2](http://www.lunny.info/wp-content/uploads/2010/12/3-2.jpg "3-2")](http://www.lunny.info/wp-content/uploads/2010/12/3-2.jpg)

图3-2

加密卷有三种，分别为：

1）  文件型：即在磁盘中创建一个加密文件；

2）  加密非系统分区/设备：即将某个非系统分区或者加密U盘等移动设备变成加密卷；

3）  加密系统分区或整个硬盘：即将硬盘某个系统分区或者整个硬盘加密。

这里我们选择【创建文件型加密卷】，点击之后会出现图3-3的界面。

[![3-3](http://www.lunny.info/wp-content/uploads/2010/12/3-3.jpg "3-3")](http://www.lunny.info/wp-content/uploads/2010/12/3-3.jpg)

图3-3

点击【下一步】后，如图3-4所示：

[![3-4](http://www.lunny.info/wp-content/uploads/2010/12/3-4.jpg "3-4")](http://www.lunny.info/wp-content/uploads/2010/12/3-4.jpg)

图3-4

将要求选择一个文件来作为加密卷文件，这个文件的扩展名可随意，最好是用一个不容易被认出是加密文件的名称。这里要特别注意：

1）  不要选择一个已经存在的文件，否则该文件将会被覆盖。

2）  不要自己误删除这个文件，否则加密内容将丢失，无法恢复。

[![3-5](http://www.lunny.info/wp-content/uploads/2010/12/3-5.jpg "3-5")](http://www.lunny.info/wp-content/uploads/2010/12/3-5.jpg)

图3-5

文件选择好之后，会出现【加密选项】界面，如图3-6所示，在这里可以选择加密的算法，一般选择默认即可。

[![3-6](http://www.lunny.info/wp-content/uploads/2010/12/3-6.jpg "3-6")](http://www.lunny.info/wp-content/uploads/2010/12/3-6.jpg)

图3-6

点击【下一步】会出现输入文件加密卷大小的界面，这里我们可以根据自己的需求输入一个值。除非有大文件需要存，一般都不要设置太大，方便保存到U盘中或文件服务器中。如果一个文件满了，那么可以再建一个，也可根据规则，比如一个月一个文件或者一年。

[![3-7](http://www.lunny.info/wp-content/uploads/2010/12/3-7.jpg "3-7")](http://www.lunny.info/wp-content/uploads/2010/12/3-7.jpg)

图3-7

点击【下一步】要求输入加密卷的密码（图3-8），这里密码一定要记牢。如果忘记了密码，加密卷中的文件基本没有找回来的可能。同时这里也可以采用密钥文件的形式，如果使用了文件密钥，注意文件密钥一定要保存好，如果丢失，加密卷也无法打开。

[![3-8](http://www.lunny.info/wp-content/uploads/2010/12/3-8.jpg "3-8")](http://www.lunny.info/wp-content/uploads/2010/12/3-8.jpg)

图3-8

密码输入完毕后将会到最后一步，进行加密卷的格式化。这里可以选择FAT格式和NTFS格式。如果小于4G，建议用FAT，这个文件格式可以在Linux和MacOS中读写。如果选择NTFS，则大小可以超出4G，但是只能在Windows系列操作系统之间读写，Linux中默认可以读取，需要修改配置允许写入才可以写；MacOS中默认无法读取和写入。

[![3-9](http://www.lunny.info/wp-content/uploads/2010/12/3-9.jpg "3-9")](http://www.lunny.info/wp-content/uploads/2010/12/3-9.jpg)

图3-9

[![3-10](http://www.lunny.info/wp-content/uploads/2010/12/3-10.jpg "3-10")](http://www.lunny.info/wp-content/uploads/2010/12/3-10.jpg)

图3-10

至此，文件型加密卷创建完成，我们可以来使用了。

## 3.3   使用文件加密卷

文件加密卷创建完成后，就跟普通文件类似，可以像普通文件那样复制粘贴。在需要使用时必须通过TrueCrypt进行挂载。挂载的方式如图3-11所示：

[![3-11](http://www.lunny.info/wp-content/uploads/2010/12/3-11.jpg "3-11")](http://www.lunny.info/wp-content/uploads/2010/12/3-11.jpg)

图3-11

在盘符列表框中选择某个盘符，例如选择M：，然后在【加密卷】下的输入框中输入或点击【选择文件】选中刚才创建的加密卷文件，点击【载入】，将会弹出密码输入框，如图3-12所示。

[![3-12](http://www.lunny.info/wp-content/uploads/2010/12/3-12.jpg "3-12")](http://www.lunny.info/wp-content/uploads/2010/12/3-12.jpg)

图3-12

输入此加密卷文件的密码，如果生成了密钥文件，选择密钥文件的路径。点击确定，如果密码正确，系统将会将加密卷中的内容载入到M：盘中。如图3-13所示，在M：盘上点击右键，选择打开，或者通过windows资源管理器选择M盘（如图3-14所示）均可打开。此时可以对M盘进行读写操作，和使用普通的分区没有任何区别。

[![3-13](http://www.lunny.info/wp-content/uploads/2010/12/3-13.jpg "3-13")](http://www.lunny.info/wp-content/uploads/2010/12/3-13.jpg)

图3-13

[![3-14](http://www.lunny.info/wp-content/uploads/2010/12/3-14.jpg "3-14")](http://www.lunny.info/wp-content/uploads/2010/12/3-14.jpg)

图3-14
