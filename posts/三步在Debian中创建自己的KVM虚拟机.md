---
title: 三步在Debian中创建自己的KVM虚拟机
date: '2012-08-15 08:06:04'
description: 
tags: 
categories: ['Linux' '软件']
---

1 电脑一台，必须的，并且注意必须要支持VT-x，同时在BIOS中Enable。然后就安装Debian吧，推荐64位的6.0版本，安装过程基本都是下一步，就不用详细介绍了。
  捎带一笔，国内比较快的Debian的源mirrors.163.com，速度还可以。

2 下一步就是要安装虚拟机软件了。 

    apt-get install qemu-kvm bridge-utils uml-utilities


  安装完毕就需要配置网络了，修改/etc/network/interfaces，将eth0的配置注释掉，加入br0的配置：

auto br0  
iface br0 inet static #dhcp  
bridge_ports eth0  
address 192.168.1.39  
netmask 255.255.255.0  
gateway 192.168.1.6
name-servers 8.8.8.8


修改完毕记得重启网络，实在不行就重启吧。

3 第三步自然就是创建虚拟机，安装运行了。
#先创建磁盘啊

kvm-img create disk.img 20G

#然后安装系统了

kvm -boot d -cdrom xp.iso -m 1024 -hda ./disk.img -net nic -net tap -vnc :1

#最后运行啊，tap网卡会自动创建的，不用担心

kvm -boot c -m 1024 -hda ./disk.img -net nic -net tap -vnc :1


当然如果需要后台运行的话，建议安装screen

apt-get install screen
