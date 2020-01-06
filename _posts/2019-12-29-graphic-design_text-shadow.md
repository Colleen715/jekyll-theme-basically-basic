---
title: "学会制作文字阴影，让你的标题更吸引用户！"
layout: page
excerpt_separator: "<!--more-->"
categories:
  - 平面设计
---    
 
## 文字阴影让你的文章更吸引人！

<!--more-->
### 基本概念
text-shadow: X轴  Y轴  Rpx  color;
属性说明（顺序依次对应）： 阴影的X轴(可以使用负值) 阴影的Y轴(可以使用负值) 阴影模糊值（大小） 阴影的颜色
PS：此属性使用于文字阴影，而不是对盒模型进行操作。

### 文字阴影
- CSS3 text-shadow 属性  
实例：  
1. ![文字阴影模糊效果](\assets\images\text-shadow_jb.jpg)  
 
```  
h1
{
text-shadow: 2px 2px #ff0000;
}  
```   

2. ![文字阴影模糊效果](\assets\images\text-shadow_mf.jpg)  

```
<!DOCTYPE html>
<html>
<head>
<style>
h1 {text-shadow:2px 2px 8px #FF0000;}
</style>
</head>
<body>
<h1>Text-shadow with blur effect</h1>
</body>
</html>
```

3. ![白色文字上文字阴影](\assets\images\text-shadow_bzmf.jpg)  

```
<!DOCTYPE html>
<html>
<html>
<head>
<style>
h1
{
color:white;
text-shadow:2px 2px 4px #000000;
}
</style>
</head>
<body>
<h1>Text-shadow on white text</h1>
</body>
</html>
```  

4. ![氖辉光文字阴影](\assets\images\text-shadow_nhg.jpg)  

```
<!DOCTYPE html>
<html>
<head>
<style>
h1
{
text-shadow:0 0 3px #FF0000;
}
</style>
</head>
<body>
<h1>Text-shadow with neon glow</h1>
</body>
</html>
```

### 心得： text-shadow为字体添加阴影, 可以通过对text-shadow属性设置相关的属性值，来实现一些需要的字体阴影效果,减少了图片的使用。
