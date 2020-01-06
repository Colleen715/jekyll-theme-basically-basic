---
title: "看！是一个旋转的风车！"
layout: page
excerpt_separator: "<!--more-->"
categories: 
  - SVG笔记
---  

Look！This is windmill!  
Don't you know what this is? Click on it!

<!--more-->

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>无标题文档</title>
<style type="text/css">
#all{
	width: 800px;
	height: 450px;
	border: 1px solid green;
	position:absolute;
    top:50%;
    left:50%;
    margin:-225px 0 0 -400px;
}

div{
	display:inline-block;
	
}


#windmill{
	width:160px;
	height:160px;	
	position:relative;
	-moz-transition:-moz-transform 2s ease-in-out;
	-webkit-transition:-webkit-transform 2s ease-in-out;
	-moz-transform:rotate(0deg);
	-webkit-transform:rotate(0deg);
}
#windmill:hover{
	-moz-transform:rotate(960deg);	
	-webkit-transform:rotate(960deg);	
}
#windmill div.top{
	width:40px;
	height:80px;
	left:40px;
	top:0px;
	border-top-left-radius:40px;		
}
#windmill div.right{
	width:80px;
	height:40px;
	left:80px;
	top:40px;
	border-top-right-radius:40px;	
}
#windmill div.bottom{
	width:40px;
	height:80px;
	left:80px;
	top:80px;
	border-bottom-right-radius:40px;	
}
#windmill div.left{	
	width:80px;
	height:40px;
	left:0px;
	top:80px;
	border-bottom-left-radius:40px;	
}
#windmill div.ala{
	position:absolute;
	-moz-box-sizing:border-box;
	-webkit-box-sizing:border-box;
	background:rgba(0,0,255,0.4);	
	border:1px solid rgba(0,0,255,0.5);
	-moz-transition:background-color 1s linear;
	-webkit-transition:background-color 1s linear;
}
#windmill div.ala:hover{
	background-color:#00F;
}
.alaIn{
	position:absolute;
	background:rgba(255,255,255,0.7);	
	-moz-box-sizing:border-box;
	-webkit-box-sizing:border-box;
	-moz-transition:background-color 1s linear;
	-webkit-transition:background-color 1s linear;
	left:0;
	top:0;
}
.alaIn:hover{
	background-color:rgba(255,255,255,0.9);
}
.topIn{
	border-bottom-left-radius:40px;	
}
.rightIn{
	border-top-left-radius:40px;	
}
.bottomIn{
	border-top-right-radius:40px;	
}
.leftIn{
	border-bottom-right-radius:40px;	
}
</style>
</head>

<body>
<div id="windmill">
	<div class="top ala"></div><div class="top topIn alaIn"></div>
	<div class="right ala"></div><div class="right rightIn alaIn"></div>
	<div class="bottom ala"></div><div class="bottom bottomIn alaIn"></div>
	<div class="left ala"></div><div class="left leftIn alaIn"></div>
</div>
<div id="windmill">
	<div class="top ala"></div><div class="top topIn alaIn"></div>
	<div class="right ala"></div><div class="right rightIn alaIn"></div>
	<div class="bottom ala"></div><div class="bottom bottomIn alaIn"></div>
	<div class="left ala"></div><div class="left leftIn alaIn"></div>
</div>
<div id="windmill">
	<div class="top ala"></div><div class="top topIn alaIn"></div>
	<div class="right ala"></div><div class="right rightIn alaIn"></div>
	<div class="bottom ala"></div><div class="bottom bottomIn alaIn"></div>
	<div class="left ala"></div><div class="left leftIn alaIn"></div>
</div>
<div id="windmill">
	<div class="top ala"></div><div class="top topIn alaIn"></div>
	<div class="right ala"></div><div class="right rightIn alaIn"></div>
	<div class="bottom ala"></div><div class="bottom bottomIn alaIn"></div>
	<div class="left ala"></div><div class="left leftIn alaIn"></div>
</div>
<div id="windmill">
	<div class="top ala"></div><div class="top topIn alaIn"></div>
	<div class="right ala"></div><div class="right rightIn alaIn"></div>
	<div class="bottom ala"></div><div class="bottom bottomIn alaIn"></div>
	<div class="left ala"></div><div class="left leftIn alaIn"></div>
</div>

</body>

</html>


