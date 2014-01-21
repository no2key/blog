---
title: 手写JS代码，十行搞定ajax异步请求！！！
date: '2011-04-26 05:54:57'
description: 
tags: ['ajax''Javascript''js''XMLHttpRequest''异步请求'']
categories: ['Javascript''技术'']
---

据说要创业的人都必须会讲故事，好吧，我开始忽悠了。
开始的开始，有一个需求，要用非常少的js代码从后台获得数据。然后，听说要用到ajax，听说jquery很小很好用，结果下载下来一看。。。xxKB。不是吧，比页面本身还大。杀鸡焉用牛刀，于是google，百度，复制，粘贴，就有了下面这段代码：

function handler() {
 if(this.readyState == 4 && this.status == 200 && this.responseText != null) {
        obj = eval('(' + this.responseText + ')')
        alert(obj)
 }
}
function getCnt() {
        var objXmlHttp = null
        if(window.XMLHttpRequest){
            objXmlHttp = new XMLHttpRequest()
        }else if(window.ActiveXObject){
            try{objXmlHttp = new ActiveXObject("Msxml2.XMLHTTP")}
            catch(failed){
                try{objXmlHttp = new ActiveXObject("Microsoft.XMLHTTP")}catch(failed){}
            }
        }
        if (objXmlHttp) {
            objXmlHttp.onreadystatechange = handler
            objXmlHttp.open("GET", "/url?v="+(new Date()).valueOf(), true)
            objXmlHttp.send()
        }
}

最后的最后，说十行夸张了点，不过基本上已经很小了，一般的使用应该没什么问题了。至于浏览器兼容性嘛，绝大部分应该支持。ie7及chrome dev至少是经过验证的。
参考请见：
[http://www.w3.org/TR/XMLHttpRequest/](http://www.w3.org/TR/XMLHttpRequest/)
