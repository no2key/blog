---
title: 佳能A710 IS数码相机 在 Ubuntu Linux 6.10下 设备访问问题的解决
date: '2007-04-21 14:45:58'
description: 
categories: ['Linux&amp;Ubuntu']
---

&nbsp; &nbsp; &nbsp; &nbsp; 虽然7.04已经发布了，不过我还没来得及更新。买了相机拍照后要将图片导入到电脑中，将相机连接到usb口，此时会弹出框显示检测到了数码相机，在导入照片时却出现如下错误：

&nbsp; &nbsp; &nbsp; &nbsp; io-库 (“无法请求 USB 设备”) 中出现错误：Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

&nbsp; &nbsp; &nbsp; &nbsp; Google了一下，发现了一个人的博客，是一个在日本的中国程序员的，他的富士通的相机，解决问题的文章地址如下：
[http://my.donews.com/booker/2007/02/10/finepix_f30_camera_on_edgy_ubuntu/](http://my.donews.com/booker/2007/02/10/finepix_f30_camera_on_edgy_ubuntu/)

&nbsp; &nbsp; &nbsp; &nbsp; 于是参考了一下：步骤如下：
&nbsp; &nbsp; &nbsp; &nbsp; 1 连上数码相机，打开终端，在终端输入lsusb，可以查看到所有连接的usb设备：

[!['lsusb' /]('http://www.lunny.info/wp-content/uploads/2007/04/lsusb.jpg' alt='lsusb' /)]('http://www.lunny.info/wp-content/uploads/2007/04/lsusb.jpg' title='lsusb')


&nbsp; &nbsp; &nbsp; &nbsp; 2 可以看到 Bus 001 Device 008: ID **04a9**:**3138** Canon, Inc
04a9,3138这两个数字是我们需要的，这两个数字根据不同的数码相机会有所不同。

&nbsp; &nbsp; &nbsp; &nbsp; 3 在终端中输入sudo gedit /etc/udev/rules.d/45-libgphoto2.rules，
在其中加入如下行：

&nbsp; &nbsp; &nbsp; &nbsp; SYSFS{idVendor}==”04a9”, SYSFS{idProduct}==”3138”, MODE=”0660″, GROUP=”plugdev”

&nbsp; &nbsp; &nbsp; &nbsp; 保存并关闭。

&nbsp; &nbsp; &nbsp; &nbsp; 4 然后重启udev：

sudo /etc/init.d/udev restart

&nbsp; &nbsp; &nbsp; &nbsp; 5 拔插一下usb线，晕还是不行。又搜索了一下，找到另一篇文章
[http://forum.ubuntu.pl/viewtopic.php?t=23060](http://forum.ubuntu.pl/viewtopic.php?t=23060)

&nbsp; &nbsp; &nbsp; &nbsp; 居然是pl结尾的文章，XX文，不认识，不过命令应该都是英文的吧。在终端中输入sudo gedit /etc/udev/rules.d/40-permissions.rules
修改这一行
SUBSYSTEM=="usb_device", MODE="0644"
为
SUBSYSTEM=="usb_device", MODE="0666"

&nbsp; &nbsp; &nbsp; &nbsp; OK!这下终于可以了。
