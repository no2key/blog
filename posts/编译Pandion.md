---
title: 编译Pandion
date: '2011-03-11 04:35:56'
description: 
tags: ['pandion' 'VC++ Express 2010' 'Wix' 'XMPP' '下载' '潘迪安' '编译']
categories: ['IM' '技术']
---

Pandion（潘迪安）是一款Windows平台下的XMPP客户端，因其界面比较简洁，所以引起了我的兴趣。详细信息可访问http://pandion.im/

编译之前，需要先安装些软件：
1. VC++ Express 2010
http://download.microsoft.com/download/5/c/1/5c156922-ca10-49d8-b7e7-9bf092c3b6eb/VS2010ExpressCHS.iso
2. Wix 3.5
http://wix.sf.net
3.RoboCopy，如果是Vista之前的Windows版本，默认没有robocopy这个命令，可下载Windows Server 2003 Resource Kit Tools，安装好后就有了。
http://www.microsoft.com/downloads/en/confirmation.aspx?familyid=9d467a69-57ff-4ae7-96ee-b18c4790cffd&displaylang=en
4.Git，因为pandion的源码是存放在github的，所以需要用git来获取

下面是编译过程：
1.安装以上软件，基本上都是“下一步”；
2.设置环境变量%VS100COMNTOOLS%到"c:\program files\microsoft visual studio 10.0\common7\tools\"
3.打开git bash，输入命令：

git clone https://github.com/pandion/pandion.git

4.找到源码，执行build_all.bat即可，编译成功后在Installer\Wix下会生成一个安装包文件Pandion_2.6.0.msi
5.编译过程出现一个警告和2个错误，未详究，暂未发现影响。
