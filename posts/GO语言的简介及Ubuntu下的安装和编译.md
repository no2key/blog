---
title: GO语言的简介及Ubuntu下的安装和编译
date: '2010-01-12 05:40:00'
description: 
tags: 
categories: ['GO'']
---



**简介**



GO语言是Google基于BSD发布的开源系统级编程语言，目标是融合Python的开发效率和C的运行时效率于一体。该项目的网址是http://golang.org。目前只支持Linux，freebsd和Mac OS X平台的amd64和386架构。

# 安装

有一个快速的编译器安装说明，见[http://golang.org/doc/install.html](http://golang.org/doc/install.html)。我在虚拟机中的Ubuntu9.10下安装过程如下：

1.设置环境变量

一共需要设置4个变量

    
export GOROOT=$HOME/go

export GOARCH=386

export GOOS=linux

export GOBIN=$HOME/bin
 




如果你的平台是AMD64，请将GOARCH替换成amd64；另外GOBIN是可选的，可以




mkdir ~/bin
 



这里是存放GO语言编译器连接器的目录，需要加入到PATH：




PATH=${PATH}:$HOME/bin
 



将以上这行和上面4个export拷贝到你的.bashrc中。



重新打开终端窗口。





2.获取GO源码

GO使用C写的，需要获取源码后编译，在命令行执行以下命令：


apt-get install python-setuptools python-dev

sudo easy_install mercurial

hg clone -r release https://go.googlecode.com/hg/ $GOROOT

sudo apt-get install bison gcc libc6-dev ed make

cd $GOROOT/src

make all
&nbsp;


等到出现：



--- cd ../test

N known bugs; 0 unexpected bugs



（N为某个数字，我这里为4）后编译完成。


# 编写Hello GO!

针对不同的架构，编译器和链接器都是不一样的：

386对应的编译器是8g，链接器是8l；

amd64对应的编译器是6g，链接器是6l；

OK.我们来编写一个最简单的GO程序，代码如下：


package main

import "fmt"

func main() {

	fmt.Printf("hello, world\n")

}


&nbsp;

将上面的代码保存为hello.go并编译之：


8g hello.go
&nbsp;

编译后生成hello.8，再链接：


8l hello.8
&nbsp;

生成hello.out，执行：


./hello.out
&nbsp;

终端上将显示：

Hello, GO!

如果要编写大型程序，Make工具依然有效。

# 语法及类库文档

语法见这里：

[http://golang.org/doc/go_spec.html](http://golang.org/doc/go_spec.html)

类库见这里：

[http://golang.org/pkg/](http://golang.org/pkg/)

有用的文档：

[http://golang.org/doc/effective_go.html](http://golang.org/doc/effective_go.html)

[http://golang.org/doc/go_tutorial.html](http://golang.org/doc/go_tutorial.html)

如果以前学习的C++可以参考这里：

[http://golang.org/doc/go_for_cpp_programmers.html](http://golang.org/doc/go_for_cpp_programmers.html)

# 保持最新版本

目前GO语言还在不断完善中，还没有到可以进入生产环境的时候，如果想及时更新最新的版本，如下：



hg pull

hg update release

make all
 
