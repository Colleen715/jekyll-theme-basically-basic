---
title: "如何制作canvas实现动画?"
layout: page
excerpt_separator: "<!--more-->"
categories:
  - 学习笔记
  tags:
  - 学习笔记
---

Canvas API（画布）是在HTML5中新增的标签用于在网页实时生成图像，并且可以操作图像内容，基本上它是一个可以用JavaScript操作的位图（bitmap）。 
Canvas 对象表示一个HTML画布元素。它没有自己的行为，但是定义了一个 API 支持脚本化客户端绘图操作。
Don't you know what this is? Click on it!
<!--more-->
## Canvas动画原理是什么？
快速切换的静态画面，其实就是不同的图片循环替换，造成视觉上图片在动，其中要运用控制函数使素材运动，最终生成网页图像。 

## 实践出真知，直接运用知识点来操作吧！  
- ### 用canvas实现行人走路的动画  
1. 制作这个动画的素材如下：  
![jpg](\assets\images\person_walk.jpg)  
从右至左，就是一个人的行走的所有动作，抬腿，迈步,脚落下，另一只脚迈步，然后循环如此。
2. 动画是5个动作的合成，原本应有5张图片，现在我们将5张图片放在一张图片里，需要时截取图片的部分，可以降低时间成本。因为在实际的web应用中，页面上可能有上百张甚至好几百张图片，如果每张图片都是单独的，就需要建立几百个http连接，耗费的时间成本很大，所以我们可以把多张图片合成到一张大的图片中，然后通过CSS中的背景定位等技术，把背景定位到实际的图片位置，就可以得到所需图片了（canvas也可以利用这种思想）。这样可以节省大量的连接建立时间，它是前端优化的一部分。  
3. 实现源码如下:
```

<pre>
<xmp>
<pre class="prettyprint"><code class="prism language-html has-numbering" onclick="mdcp.signin(event)" style="position: unset;"><span class="token doctype">&lt;!DOCTYPE html&gt;</span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>html</span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>head</span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>meta</span> <span class="token attr-name">charset</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>utf-8<span class="token punctuation">"</span></span> <span class="token punctuation">/&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>meta</span> <span class="token attr-name">http-equiv</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>X-UA-Compatible<span class="token punctuation">"</span></span> <span class="token attr-name">content</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>IE=edge<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>title</span><span class="token punctuation">&gt;</span></span>walk<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>title</span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>meta</span> <span class="token attr-name">name</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>viewport<span class="token punctuation">"</span></span> <span class="token attr-name">content</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>width=device-width, initial-scale=1<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>head</span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>body</span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>canvas</span> <span class="token attr-name">width</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>500<span class="token punctuation">"</span></span> <span class="token attr-name">height</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>400<span class="token punctuation">"</span></span> <span class="token attr-name">id</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>canvas<span class="token punctuation">"</span></span><span class="token style-attr language-css"><span class="token attr-name"> <span class="token attr-name">style</span></span><span class="token punctuation">="</span><span class="token attr-value"><span class="token property">margin-top</span><span class="token punctuation">:</span> 200px<span class="token punctuation">;</span></span><span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>canvas</span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>img</span> <span class="token attr-name">src</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>../asserts/walk.jpg<span class="token punctuation">"</span></span><span class="token style-attr language-css"><span class="token attr-name"> <span class="token attr-name">style</span></span><span class="token punctuation">="</span><span class="token attr-value"><span class="token property">display</span><span class="token punctuation">:</span> none<span class="token punctuation">;</span></span><span class="token punctuation">"</span></span> <span class="token attr-name">id</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>walk<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>script</span><span class="token punctuation">&gt;</span></span><span class="token script language-javascript">
    <span class="token comment">//获取图片</span>
    <span class="token keyword">let</span> walkImg <span class="token operator">=</span> document<span class="token punctuation">.</span><span class="token function">getElementById</span><span class="token punctuation">(</span><span class="token string">'walk'</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
    <span class="token comment">//获取绘图上下文</span>
    <span class="token keyword">let</span> ctx <span class="token operator">=</span> document<span class="token punctuation">.</span><span class="token function">getElementById</span><span class="token punctuation">(</span><span class="token string">'canvas'</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">getContext</span><span class="token punctuation">(</span><span class="token string">'2d'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    
    <span class="token comment">//这个参数是用来标识，现在改用哪个用作，初始值是4，图片最有边的动作，开始行走的动作。取值是4~0，循环</span>
    <span class="token keyword">let</span> index <span class="token operator">=</span> <span class="token number">4</span><span class="token punctuation">;</span>

    <span class="token comment">//行走位置</span>
    <span class="token keyword">let</span> position <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span>
    
    <span class="token comment">//行走的方向，true代表从左至右， false代表从右至左</span>
    <span class="token keyword">let</span> direct <span class="token operator">=</span> <span class="token boolean">true</span><span class="token punctuation">;</span>

    <span class="token comment">//定时器，确保图片加载完成再绘制动画</span>
    <span class="token keyword">let</span> timer <span class="token operator">=</span> <span class="token keyword">null</span><span class="token punctuation">;</span>
    <span class="token comment">//确保图片加载完成再绘制到</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token operator">!</span>walkImg<span class="token punctuation">.</span>complete<span class="token punctuation">)</span> <span class="token punctuation">{</span>
      timer <span class="token operator">=</span> <span class="token function">setInterval</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token punctuation">{</span>
        <span class="token comment">//两张图片加载完成</span>
        <span class="token keyword">if</span> <span class="token punctuation">(</span>walkImg<span class="token punctuation">.</span>complete<span class="token punctuation">)</span> <span class="token punctuation">{</span>
          <span class="token comment">//清除定时器</span>
          <span class="token function">clearInterval</span><span class="token punctuation">(</span>timer<span class="token punctuation">)</span><span class="token punctuation">;</span>
          timer <span class="token operator">=</span> <span class="token keyword">null</span><span class="token punctuation">;</span>
          <span class="token comment">//绘制</span>
          <span class="token function">drawAll</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token punctuation">}</span>
      <span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token number">200</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
      <span class="token function">drawAll</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>

    <span class="token keyword">function</span> <span class="token function">drawAll</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
      <span class="token comment">//清除原来的图层</span>
      ctx<span class="token punctuation">.</span><span class="token function">clearRect</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">500</span><span class="token punctuation">,</span> <span class="token number">400</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      <span class="token comment">//画脚下的线，当做地面</span>
      <span class="token function">addLawn</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      <span class="token comment">//添加初始动作</span>
      <span class="token function">addWalk</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      <span class="token comment">//使用定时器，不断重绘画面，形成动画</span>
      <span class="token function">setInterval</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token punctuation">{</span>
        ctx<span class="token punctuation">.</span><span class="token function">clearRect</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">500</span><span class="token punctuation">,</span> <span class="token number">400</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">addLawn</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token function">addWalk</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token number">150</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>

    <span class="token comment">//绘制线段，当做地面</span>
     <span class="token keyword">function</span> <span class="token function">addLawn</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
      ctx<span class="token punctuation">.</span><span class="token function">save</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span><span class="token function">beginPath</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span>strokeStyle <span class="token operator">=</span> <span class="token string">'green'</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span>lineWidth <span class="token operator">=</span> <span class="token number">3</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span><span class="token function">moveTo</span><span class="token punctuation">(</span><span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">112</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span><span class="token function">lineTo</span><span class="token punctuation">(</span><span class="token number">500</span><span class="token punctuation">,</span> <span class="token number">112</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span><span class="token function">stroke</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span><span class="token function">closePath</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span><span class="token function">restore</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
     <span class="token punctuation">}</span>

     <span class="token comment">//添加不同位置图片</span>
     <span class="token keyword">function</span> <span class="token function">addWalk</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
      ctx<span class="token punctuation">.</span><span class="token function">save</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      <span class="token comment">/**
       * 行走分为两个方向，从左至右和从右至左，我们分别说明
       * 1、从右至左：图片资源的5个动作就是从右至左方向走的，所以从右至左行走时，无需
       * 额外处理图片，只需将对应动作放在规定位置即可。
       * 
       * 2、从左至右：这与图片资源的工作方向相反，所以，提取动作后，需要翻转（利用scale进行翻转）。
       * */</span>

      <span class="token keyword">if</span> <span class="token punctuation">(</span>direct<span class="token punctuation">)</span> <span class="token punctuation">{</span>
        <span class="token comment">//从左至右方向，scale(-1, 1)先翻转画布，然后利用translate修改坐标系原点</span>
        ctx<span class="token punctuation">.</span><span class="token function">scale</span><span class="token punctuation">(</span><span class="token operator">-</span><span class="token number">1</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        ctx<span class="token punctuation">.</span><span class="token function">translate</span><span class="token punctuation">(</span><span class="token operator">-</span>position<span class="token operator">-</span><span class="token number">55</span><span class="token punctuation">,</span><span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        position <span class="token operator">+=</span> <span class="token number">6</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
        <span class="token comment">//从右至左方向，无需翻转，只需修改坐标系原点，然后将图片直接从原点处放置即可</span>
        ctx<span class="token punctuation">.</span><span class="token function">translate</span><span class="token punctuation">(</span>position<span class="token punctuation">,</span><span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
        position <span class="token operator">-=</span> <span class="token number">6</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span>
      <span class="token comment">//根据index不同，从图片资源中提取不同的行走动作</span>
      <span class="token keyword">switch</span><span class="token punctuation">(</span>index<span class="token punctuation">)</span> <span class="token punctuation">{</span>
        <span class="token keyword">case</span> <span class="token number">0</span><span class="token punctuation">:</span>
          ctx<span class="token punctuation">.</span><span class="token function">drawImage</span><span class="token punctuation">(</span>walkImg<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
          <span class="token keyword">break</span><span class="token punctuation">;</span>
        <span class="token keyword">case</span> <span class="token number">1</span><span class="token punctuation">:</span>
          ctx<span class="token punctuation">.</span><span class="token function">drawImage</span><span class="token punctuation">(</span>walkImg<span class="token punctuation">,</span> <span class="token number">75</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
          <span class="token keyword">break</span><span class="token punctuation">;</span>
        <span class="token keyword">case</span> <span class="token number">2</span><span class="token punctuation">:</span>
          ctx<span class="token punctuation">.</span><span class="token function">drawImage</span><span class="token punctuation">(</span>walkImg<span class="token punctuation">,</span> <span class="token number">145</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
          <span class="token keyword">break</span><span class="token punctuation">;</span>
        <span class="token keyword">case</span> <span class="token number">3</span><span class="token punctuation">:</span>
          ctx<span class="token punctuation">.</span><span class="token function">drawImage</span><span class="token punctuation">(</span>walkImg<span class="token punctuation">,</span> <span class="token number">220</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
          <span class="token keyword">break</span><span class="token punctuation">;</span>
        <span class="token keyword">case</span> <span class="token number">4</span><span class="token punctuation">:</span>
          ctx<span class="token punctuation">.</span><span class="token function">drawImage</span><span class="token punctuation">(</span>walkImg<span class="token punctuation">,</span> <span class="token number">270</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">55</span><span class="token punctuation">,</span> <span class="token number">110</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
          <span class="token keyword">break</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span>
      
      <span class="token comment">//图片位置，走到这返回</span>
      <span class="token keyword">if</span> <span class="token punctuation">(</span>position <span class="token operator">&gt;</span> <span class="token number">440</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
        direct <span class="token operator">=</span> <span class="token boolean">false</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span> 
      <span class="token keyword">if</span> <span class="token punctuation">(</span>position <span class="token operator">&lt;</span> <span class="token number">10</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
        direct <span class="token operator">=</span> <span class="token boolean">true</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span>

      index <span class="token operator">-=</span><span class="token number">1</span> <span class="token punctuation">;</span>
      <span class="token keyword">if</span> <span class="token punctuation">(</span>index <span class="token operator">&lt;</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
        index <span class="token operator">=</span> <span class="token number">4</span><span class="token punctuation">;</span>
      <span class="token punctuation">}</span>
      ctx<span class="token punctuation">.</span><span class="token function">restore</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
  </span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>script</span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>body</span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>html</span><span class="token punctuation">&gt;</span></span>
<div class="hljs-button signin" data-title="登录后复制"></div></code>
</xmp>
</pre>
```