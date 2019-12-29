---
title: "什么是网页安全字体？"
layout: page
excerpt_separator: "<!--more-->"
categories:
  - 平面设计
---   

## 网页安全字体（web safe fonts）

<!--more-->    

### 网页安全字体（web safe fonts）
它是基本上能保证所有用户看见的是类似的字体，也就是说他们的操作系统里以很大概率自带了这些字体。传统的安全字体大概多数人都已经看厌了，比如 Times New Roman、Arial之类的。现在时兴使用网络字体，比如Google的那些字体。

### 为什么我们仍然需要网页安全字体集？  
1. 不完善的字体(Incomplete Fonts)    
如果某种字体中的某个字符不可用, 浏览器会尝试去以你字体集里的下一种字体去显示那些字符,如果你没有字体集，那么浏览器则会用它默认的字体 。
2. 网络问题(Netword Issues)   
通过@font-face加载远程字体需要网络连接, 如果负责字体服务的网络不可用或者暂时的维护浏览器会使用他的默认字体，除非你在你的CSS字体集里添加了网页安全字体。例如： 这个网页设计用的是 PT Sans 字体
  
![图示](\assets\images\Web-safe Fonts（1）.jpg)  
  
如果你没有字体集的同时网络中断 然后网页就会变成这个(Chrome)
![图示](\assets\images\Web-safe Fonts（2）.jpg)  
网页看起来完全不一样是因为Time New Roman大大影响了这个设计的信息

但是，如果我们用了包括网页安全字体的字体集，我们可以减缓这个网络带来的问题。
  
![图示](\assets\images\Web-safe Fonts（3）.jpg)  
@font-face可以在客户关闭(@font-face Can Be Turned Off Client-Side)

一些浏览器可以提供选项禁止下载字体文件，大多数情况下，禁止浏览器使用远程字体会导致混乱。有研究证明，字体集中使用网页安全字体能有效减少字体对网页的影响。  
3. 网页安全字体 = 便宜的, 简单地实现优雅的性能下降 (Web-safe Fonts = Cheap and Easy Graceful Degradation)  

### [资料共享](https://www.webfx.com/blog/web-design/why-we-still-need-web-safe-fonts/)