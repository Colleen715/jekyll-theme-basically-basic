---
title: 看到加载中动画是不是有点害怕？？？
layout: page
excerpt_separator: "<!--more-->"
categories: 
  - svg制作
tags:
  - svg
---   

Don't you know what this is? Click on it!

<!--more-->     

- 第一种
<!--more-->
<section>
 <style>        .spinner {            margin-top: 100px;            margin-right: auto;            margin-bottom: 100px;            margin-left: auto;            width: 50px;            height: 50px;            position: relative;        }         h3{            text-align: center;        }        .container1 > div, .container2 > div, .container3 > div {            width: 12px;            height: 12px;            background-color: #9966FF;             border-radius: 100%;            position: absolute;            -webkit-animation: bouncedelay 1.2s infinite ease-in-out;            animation: bouncedelay 1.2s infinite ease-in-out;            -webkit-animation-fill-mode: both;            animation-fill-mode: both;        }         .spinner .spinner-container {            position: absolute;            width: 100%;            height: 100%;        }         .container2 {            -webkit-transform: rotateZ(45deg);            transform: rotateZ(45deg);        }         .container3 {            -webkit-transform: rotateZ(90deg);            transform: rotateZ(90deg);        }         .circle1 { top: 0; left: 0; }        .circle2 { top: 0; right: 0; }        .circle3 { right: 0; bottom: 0; }        .circle4 { left: 0; bottom: 0; }         .container2 .circle1 {            -webkit-animation-delay: -1.1s;            animation-delay: -1.1s;        }         .container3 .circle1 {            -webkit-animation-delay: -1.0s;            animation-delay: -1.0s;        }         .container1 .circle2 {            -webkit-animation-delay: -0.9s;            animation-delay: -0.9s;        }         .container2 .circle2 {            -webkit-animation-delay: -0.8s;            animation-delay: -0.8s;        }         .container3 .circle2 {            -webkit-animation-delay: -0.7s;            animation-delay: -0.7s;        }         .container1 .circle3 {            -webkit-animation-delay: -0.6s;            animation-delay: -0.6s;        }         .container2 .circle3 {            -webkit-animation-delay: -0.5s;            animation-delay: -0.5s;        }         .container3 .circle3 {            -webkit-animation-delay: -0.4s;            animation-delay: -0.4s;        }         .container1 .circle4 {            -webkit-animation-delay: -0.3s;            animation-delay: -0.3s;        }         .container2 .circle4 {            -webkit-animation-delay: -0.2s;            animation-delay: -0.2s;        }         .container3 .circle4 {            -webkit-animation-delay: -0.1s;            animation-delay: -0.1s;        }         @-webkit-keyframes bouncedelay {            0%, 80%, 100% { -webkit-transform: scale(0.0) }            40% { -webkit-transform: scale(1.0) }        }         @keyframes bouncedelay {            0%, 80%, 100% {                transform: scale(0.0);                -webkit-transform: scale(0.0);            } 40% {                  transform: scale(1.0);                  -webkit-transform: scale(1.0);              }        }</style>
 <body><div class="um-win" id="index">    <div class="um-header">           </div>     <div class="um-content">        <div class="spinner">            <div class="spinner-container container1">                <div class="circle1"></div>                <div class="circle2"></div>                <div class="circle3"></div>                <div class="circle4"></div>            </div>            <div class="spinner-container container2">                <div class="circle1"></div>                <div class="circle2"></div>                <div class="circle3"></div>                <div class="circle4"></div>            </div>            <div class="spinner-container container3">                <div class="circle1"></div>                <div class="circle2"></div>                <div class="circle3"></div>                <div class="circle4"></div>            </div>        </div>    </div>     <div class="um-footer">     </div></div> <script> </script> </body>
 </section>
  
- 第二种  

<html lang="zh-cn">
<head>
    <meta charset="utf-8">
    <title>加载中动画</title>
    <style type="text/css">
        .typing_loader{
            width: 20px;
            height: 20px;
            border-radius: 50%;
            -webkit-animation: typing 1s linear infinite alternate;
               -moz-animation: Typing 1s linear infinite alternate;
                    animation: typing 1s linear infinite alternate;
            margin: 46px auto; /* Not necessary- its only for layouting*/  
            position: relative;
            left: -40px;
        }
        @-webkit-keyframes typing{
            0%{
                background-color: rgba(247,111,73, 1);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,0.2), 
                            80px 0px 0px 0px rgba(247,111,73,0.2);
              }
            25%{ 
                background-color: rgba(247,111,73, 0.4);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,2), 
                            80px 0px 0px 0px rgba(247,111,73,0.2);
            }
            75%{ background-color: rgba(247,111,73, 0.4);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,0.2), 
                            80px 0px 0px 0px rgba(247,111,73,1);
              }
        }

        @-moz-keyframes typing{
           0%{
                background-color: rgba(247,111,73, 1);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,0.2), 
                            80px 0px 0px 0px rgba(247,111,73,0.2);
              }
            25%{ 
                background-color: rgba(247,111,73, 0.4);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,2), 
                            80px 0px 0px 0px rgba(247,111,73,0.2);
            }
            75%{ background-color: rgba(247,111,73, 0.4);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,0.2), 
                            80px 0px 0px 0px rgba(247,111,73,1);
              }
        }

        @keyframes typing{
           0%{
                background-color: rgba(247,111,73, 1);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,0.2), 
                            80px 0px 0px 0px rgba(247,111,73,0.2);
              }
            25%{ 
                background-color: rgba(247,111,73, 0.4);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,2), 
                            80px 0px 0px 0px rgba(247,111,73,0.2);
            }
            75%{ background-color: rgba(247,111,73, 0.4);
                box-shadow: 40px 0px 0px 0px rgba(247,111,73,0.2), 
                            80px 0px 0px 0px rgba(247,111,73,1);
              }
        }
    </style>
</head>
<body>
<div id="loadingMask">
    <div class="typing_loader"></div>
</div>
</body>
</html>
