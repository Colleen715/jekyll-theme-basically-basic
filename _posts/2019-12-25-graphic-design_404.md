---
title: "原来404错误页面可以这样设计"
layout: page
excerpt_separator: "<!--more-->"
categories:
  - 平面设计
---

起因：常见404页面大致相同，想寻找不一样的404页面。于是，我上网查找了资料。

<!--more-->
### 经常见到404，那到底什么是404页面呢？
404页面是网站优化中必不可少的基础优化之一，随着网站运营时间的不断延长，网站上原来的网页内容可能会被删除，但是该网页的链接地址往往会以各种内链、外链形式存在，如果使用的是一些锚文本链接，这些文字内容可能会吸引到用户点击，而对应的页面却已经删除，此时如果没有设置404页面，那么用户获得的页面就是一个错误的页面，而搜索引擎 获得的路径则变成了死路。正因如此又将这类链接称之为死链。
　　在网站优化的过程中，404页面是影响网站排名与避免流量流失的一项重要因素，那么，我们应该如何设置404页面呢？
　　一般情况下，当用户输错了网站某个页面URL，一般会以下图的空间默认的形式显示你所访问的页面错误：

![平常所见到的404页面]（\assets\images\404_normal.jpg）
   
   而经过自定义的是这样的：  

![自定义的404页面可以是这样的]（\assets\images\404_unique.jpg）
 那么我们如何pick到它呢？？？  
 实现代码如下：  

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head> 
<meta charset="UTF-8" http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
<title>404-对不起！您访问的页面不存在</title> 
<style type="text/css"> 
.head404{ width:580px; height:234px; margin:50px auto 0 auto; background:url(https://www.daixiaorui.com/Public/images/head404.png) no-repeat; }
.txtbg404{ width:499px; height:169px; margin:10px auto 0 auto; background:url(https://www.daixiaorui.com/Public/images/txtbg404.png) no-repeat;}
.txtbg404 .txtbox{ width:390px; position:relative; top:30px; left:60px;color:#eee; font-size:13px;}
.txtbg404 .txtbox p {margin:5px 0; line-height:18px;} 
.txtbg404 .txtbox .paddingbox { padding-top:15px;} 
.txtbg404 .txtbox p a { color:#eee; text-decoration:none;} 
.txtbg404 .txtbox p a:hover { color:#FC9D1D; text-decoration:underline;}
</style> 
</head> 
<body bgcolor="#494949">
<div class="head404"></div>
<div class="txtbg404">
<div class="txtbox">
<p>对不起，您请求的页面不存在、或已被删除、或暂时不可用</p>
<p class="paddingbox">请点击以下链接继续浏览网页</p>
<p>》<a style="cursor:pointer" οnclick="history.back()">返回上一页面</a></p>
<p>》<a href="https://www.daixiaorui.com">返回网站首页</a></p>
</div>
</div>
</body>
</html>
```

###  设置方法 
1. 虚拟空间设置方法    
现在的idc提供商基本都提供404设置的功能，直接上传文件设置即可。

2. IIS下设置404页面  
在IIS管理器中右键单击要管理的网站，打开“属性”中的“自定义错误信息”页，为“404”设定相应的错误信息页即可。不过，此处在“消息类型”中一定要选择“文件”或“默认值”，而不要选择“URL”，不然，将导致返回“200”状态码。
3. Apache下设置404错误页面  
在.htaccess文件中加入如下内容即可：ErrorDocument 404 /notfound.php。切记不要使用绝对URL，如果使用绝对URL返回的状态码是“302”+“200”。
　　在设置好以后最好再检查一遍网页的http状态，可以用ranknow这个工具：检测你的站点404设置的是否正确。

###  安利动态404页面  
[是会动的猴子噢！](https://codepen.io/thejohnyagiz/pen/npDyq?__cf_chl_jschl_tk__=8b3a22438ac505bd5b6cb493b6a55ad792a93088-1577259573-0-AYhZJWr54GbS63sVkQG_NCE-f4NwvTNOM_YTmKWCfpsUZOJQ-PNCzbKi9yp1GMzghVxxe3dqEwmpfzDcelOZ1qEaA2njNqVrFtbmu-poqZDXwX_1EHy-UvBBj9n97Tnl2nydYClIGb5aYOXW8nvqbW6TF0jftoJxnVAUwzeRys2_MLYa-Etn7qD-D1BTIbTTSHijeS4bD9Cb0SpYRzaAJ0ZqJFBHtXpmcmC3XMStS4ttUQMxuZz3Ge3Gdbklr-BnJgp1KtfVxnXKocE6Zm8PXQL-fVrSl7GYGorNUGVh8DkoDaVAuMCjbKq4lu4YNCSDTBtbfFoKz_HAVYWhLPqelU_6uVOcFpuzGp0bHa3sC0ti)
   