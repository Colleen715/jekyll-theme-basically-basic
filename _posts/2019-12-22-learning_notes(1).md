---
title: "如何制作canvas实现动画?"
layout: page
excerpt_separator: "<!--more-->"
categories:
  - 学习笔记
---


Canvas API（画布）是在HTML5中新增的标签用于在网页实时生成图像，并且可以操作图像内容，基本上它是一个可以用JavaScript操作的位图（bitmap）。 
- Canvas 对象表示一个HTML画布元素。它没有自己的行为，但是定义了一个 API 支持脚本化客户端绘图操作。
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
 <section>
    <head>
    <meta charset="utf-8" />  
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>walk</title>
    <meta name="viewport" content="width=device-width,   initial-scale=1">
    </head>
    <body>
    <canvas width="500" height="400" id="canvas" style="margin-top: 200px;"></canvas>
    <img src="C:\Users\19654\Desktop\学习笔记1\person.jpg" style="display: none;" id="walk">
    <script>
    //获取图片
    let walkImg = document.getElementById('walk'); 
    //获取绘图上下文
    let ctx = document.getElementById('canvas').getContext('2d');
    
    //这个参数是用来标识，现在改用哪个用作，初始值是4，图片最有边的动作，开始行走的动作。取值是4~0，循环
    let index = 4;

    //行走位置
    let position = 0;
    
    //行走的方向，true代表从左至右， false代表从右至左
    let direct = true;

    //定时器，确保图片加载完成再绘制动画
    let timer = null;
    //确保图片加载完成再绘制到
    if (!walkImg.complete) {
      timer = setInterval(() => {
        //两张图片加载完成
        if (walkImg.complete) {
          //清除定时器
          clearInterval(timer);
          timer = null;
          //绘制
          drawAll();
        }
      }, 200);
    } else {
      drawAll();
    }

    function drawAll() {
      //清除原来的图层
      ctx.clearRect(0, 0, 500, 400);
      //画脚下的线，当做地面
      addLawn();
      //添加初始动作
      addWalk();
      //使用定时器，不断重绘画面，形成动画
      setInterval(() => {
        ctx.clearRect(0, 0, 500, 400);
        addLawn();
        addWalk();
      }, 150);
    }

    //绘制线段，当做地面
     function addLawn() {
      ctx.save();
      ctx.beginPath();
      ctx.strokeStyle = 'green';
      ctx.lineWidth = 3;
      ctx.moveTo(0, 112);
      ctx.lineTo(500, 112);
      ctx.stroke();
      ctx.closePath();
      ctx.restore();
     }

     //添加不同位置图片
     function addWalk() {
      ctx.save();
      /**
       * 行走分为两个方向，从左至右和从右至左，我们分别说明
       * 1、从右至左：图片资源的5个动作就是从右至左方向走的，所以从右至左行走时，无需
       * 额外处理图片，只需将对应动作放在规定位置即可。
       * 
       * 2、从左至右：这与图片资源的工作方向相反，所以，提取动作后，需要翻转（利用scale进行翻转）。
       * */

      if (direct) {
        //从左至右方向，scale(-1, 1)先翻转画布，然后利用translate修改坐标系原点
        ctx.scale(-1, 1);
        ctx.translate(-position-55,0);
        position += 6;
      } else {
        //从右至左方向，无需翻转，只需修改坐标系原点，然后将图片直接从原点处放置即可
        ctx.translate(position,0);
        position -= 6;
      }
      //根据index不同，从图片资源中提取不同的行走动作
      switch(index) {
        case 0:
          ctx.drawImage(walkImg, 0, 0, 55, 110, 0, 0, 55, 110);
          break;
        case 1:
          ctx.drawImage(walkImg, 75, 0, 55, 110, 0, 0, 55, 110);
          break;
        case 2:
          ctx.drawImage(walkImg, 145, 0, 55, 110, 0, 0, 55, 110);
          break;
        case 3:
          ctx.drawImage(walkImg, 220, 0, 55, 110, 0, 0, 55, 110);
          break;
        case 4:
          ctx.drawImage(walkImg, 270, 0, 55, 110, 0, 0, 55, 110);
          break;
      }
      
      //图片位置，走到这返回
      if (position > 440) {
        direct = false;
      } 
      if (position < 10) {
        direct = true;
      }

      index -=1 ;
      if (index < 0) {
        index = 4;
      }
      ctx.restore();
    }
    </script>
    </body>
   </html>  

- ### 让Canvas给你们放个烟花吧！  
这个在 Canvas烟花动画中使用了DOMContentLoaded 触发事件函数。  
实现源码如下:  
<section>  
    <head>
    <meta charset="UTF-8">
    <title>烟花</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        canvas{
            position: absolute;
        }
     </style>
     </head>  
     <body>
     <canvas id="canvas"></canvas>
     <script>
        //可视化窗口 Size 改变时触发 resizeCanvas 函数
        window.addEventListener("resize", resizeCanvas, false);
        //当 DOM 解析完成后触发 onLoad 函数
        window.addEventListener("DOMContentLoaded", onLoad, false);
        //requestAnimationFrame 兼容
        window.requestAnimationFrame = 
            window.requestAnimationFrame       || 
            window.webkitRequestAnimationFrame || 
            window.mozRequestAnimationFrame    || 
            window.oRequestAnimationFrame      || 
            window.msRequestAnimationFrame     || 
            function (callback) {
                window.setTimeout(callback, 1000/60);
            };
        
        //初始化变量
        var canvas, ctx, w, h, particles = [], probability = 0.04,  //0.04 烟花出现概率
            xPoint, yPoint;
        
        //初始化 Canvas
        function onLoad() {
            canvas = document.getElementById("canvas");
            ctx = canvas.getContext("2d");
            resizeCanvas();
            //渲染动画
            window.requestAnimationFrame(updateWorld);
        } 
        
        //改变 Canvas 可视窗口 Size 函数
        function resizeCanvas() {
            if (!!canvas) {
                w = canvas.width = window.innerWidth;
                h = canvas.height = window.innerHeight;
            }
        }
        
        //更新函数
        function updateWorld() {
            update();
            paint();
            window.requestAnimationFrame(updateWorld);
        } 
        
        //更新函数
        function update() {
            if (particles.length < 500 && Math.random() < probability) {
                createFirework();
            }
            var alive = [];
            for (var i = 0; i < particles.length; i++) {
                if (particles[i].move()) {
                    alive.push(particles[i]);
                }
            }
            particles = alive;
        } 
        
        //绘制函数
        function paint() {
            ctx.globalCompositeOperation = 'source-over';
            ctx.fillStyle = "rgba(0,0,0,0.2)";
            ctx.fillRect(0, 0, w, h);
            ctx.globalCompositeOperation = 'lighter';
            for (var i = 0; i < particles.length; i++) {
                particles[i].draw(ctx);
            }
        } 
        
        //创建烟花颗粒
        function createFirework() {
            xPoint = Math.random() * (w - 200) + 100;
            yPoint = Math.random() * (h - 200) + 100;
            var nFire = Math.random() * 50 + 100;
            var c = "rgb("+(~~(Math.random() * 200 + 55))+","+(~~(Math.random() * 200 + 55))+","+(~~(Math.random() * 200 + 55))+")";
            for (var i = 0; i < nFire; i++) {
                var particle = new Particle();
                particle.color = c;
                var vy = Math.sqrt(25 - particle.vx * particle.vx);
                if (Math.abs(particle.vy) > vy) {
                    particle.vy = particle.vy > 0 ? vy : -vy;
                }
                particles.push(particle);
            }
        } 
        
        //颗粒函数
        function Particle() {
            this.w = this.h = Math.random() * 4 + 1;
            
            this.x = xPoint - this.w / 2;
            this.y = yPoint - this.h / 2;
            
            this.vx = (Math.random() - 0.5) * 10;
            this.vy = (Math.random() - 0.5) * 10;
            
            this.alpha = Math.random() * .5 + .5;
            
            this.color;
        } 
        
        Particle.prototype = {
            gravity: 0.05,          //烟花颗粒坠落速度
            move: function () {     //改变烟花颗粒位置
                this.x += this.vx;
                this.vy += this.gravity;
                this.y += this.vy;
                this.alpha -= 0.01;
                if (this.x <= -this.w || this.x >= screen.width || this.y >= screen.height || this.alpha <= 0) {
                    return false;
                }
                return true;
            },
            draw: function (c) {    //渲染烟花颗粒
                c.save();
                c.beginPath();
                
                c.translate(this.x+this.w / 2, this.y+this.h / 2);  //改变位置
                c.arc(0, 0, this.w, 0, Math.PI * 2);                //圆形颗粒
                c.fillStyle = this.color;                           //填充颜色
                c.globalAlpha = this.alpha;                         //透明度
                
                c.closePath();
                c.fill();
                c.restore();
            }
        }
       </script>
       </body>
     </section>





