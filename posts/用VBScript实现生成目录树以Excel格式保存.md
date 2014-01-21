---
title: 用VBScript实现生成目录树以Excel格式保存
date: '2011-07-04 01:03:32'
description: 
tags: ['excel' 'vbscript' '目录树']
categories: ['VBScript' '技术']
---

帮朋友实现这个功能，本想采用Python，熟门熟路的，但是朋友机器可能没有安装。对于小白，担心他会有更多的麻烦，只好试试好久没用的VBScript了。保存为Excel格式其实偷了懒，保存的是HTML格式，不过可以很容易的转到Excel中。实现代码如下：

''''''''''''''''''''''''''''''''''''
' Copyright (C) 2011
' Author: Lunny Xiao
' Email: xiaolunwen@gmail.com
' Date: 2011-7-1
' Description: traversing directory and building directory tree as html file format. If you want excel format,
'    you can open the html, select all content and paste to a new excel file. That's all.
''''''''''''''''''''''''''''''''''''

'Option Explicit

set fso = createobject("scripting.filesystemobject")

Sub TraverFolder(fd, folder, level)
	Set f = fso.GetFolder(folder)
	Set files = f.Files
	Set sfs = f.SubFolders
	dim i
	dim j
	i = 0
	For Each a in sfs
		fd.write("
")
		For j = 1 To level
			fd.write("

")
		Next
		fd.write("
" & a.name & "

")
		TraverFolder fd, a.Path, (level+1)
	Next

	i = 0
	For Each b In files
		fd.write("
")
		For j = 1 To level
			fd.write("

")
		Next
		fd.write("
" & b.name & "

")
	Next
	If i = 0 Then
		fd.write(vbcrlf)
	End If
End Sub

msg="请输入根目录:" 
dir=Inputbox(msg, "根目录")  

set ts = fso.opentextfile("d:\\res.html", 2, true)
ts.write("
")
TraverFolder ts, dir, 0
ts.write("
")
ts.close()

使用方法：
将上述代码保存为一个.vbs文件，直接双击该文件，会弹出框询问根目录（可从资源管理器复制粘贴）。点击确定，会在D盘根目录生成一个res.html文件。打开该文件，全选，复制，粘贴到一个新的Excel文件即可。
