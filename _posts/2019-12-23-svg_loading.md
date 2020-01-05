---
title: 看到加载中动画是不是有点害怕？？？
layout: page
excerpt_separator: "<!--more-->"
categories: 
  - svg制作
tags:
  - svg
---    

<!--more-->

<html> 
<head> 
<meta charset="utf-8" /> 
<title></title> 
<style> 
body{ text-align:center} 
.div{ margin:0 auto; width:400px; height:100px; border:1px solid #F00} 
</style> 
</head> 
<body> 
第一种
<div>
<style>        .spinner {            margin-top: 100px;            margin-right: auto;            margin-bottom: 100px;            margin-left: auto;            width: 50px;            height: 50px;            position: relative;        }         h3{            text-align: center;        }        .container1 > div, .container2 > div, .container3 > div {            width: 12px;            height: 12px;            background-color: #c6ffdd;             border-radius: 100%;            position: absolute;            -webkit-animation: bouncedelay 1.2s infinite ease-in-out;            animation: bouncedelay 1.2s infinite ease-in-out;            -webkit-animation-fill-mode: both;            animation-fill-mode: both;        }         .spinner .spinner-container {            position: absolute;            width: 100%;            height: 100%;        }         .container2 {            -webkit-transform: rotateZ(45deg);            transform: rotateZ(45deg);        }         .container3 {            -webkit-transform: rotateZ(90deg);            transform: rotateZ(90deg);        }         .circle1 { top: 0; left: 0; }        .circle2 { top: 0; right: 0; }        .circle3 { right: 0; bottom: 0; }        .circle4 { left: 0; bottom: 0; }         .container2 .circle1 {            -webkit-animation-delay: -1.1s;            animation-delay: -1.1s;        }         .container3 .circle1 {            -webkit-animation-delay: -1.0s;            animation-delay: -1.0s;        }         .container1 .circle2 {            -webkit-animation-delay: -0.9s;            animation-delay: -0.9s;        }         .container2 .circle2 {            -webkit-animation-delay: -0.8s;            animation-delay: -0.8s;        }         .container3 .circle2 {            -webkit-animation-delay: -0.7s;            animation-delay: -0.7s;        }         .container1 .circle3 {            -webkit-animation-delay: -0.6s;            animation-delay: -0.6s;        }         .container2 .circle3 {            -webkit-animation-delay: -0.5s;            animation-delay: -0.5s;        }         .container3 .circle3 {            -webkit-animation-delay: -0.4s;            animation-delay: -0.4s;        }         .container1 .circle4 {            -webkit-animation-delay: -0.3s;            animation-delay: -0.3s;        }         .container2 .circle4 {            -webkit-animation-delay: -0.2s;            animation-delay: -0.2s;        }         .container3 .circle4 {            -webkit-animation-delay: -0.1s;            animation-delay: -0.1s;        }         @-webkit-keyframes bouncedelay {            0%, 80%, 100% { -webkit-transform: scale(0.0) }            40% { -webkit-transform: scale(1.0) }        }         @keyframes bouncedelay {            0%, 80%, 100% {                transform: scale(0.0);                -webkit-transform: scale(0.0);            } 40% {                  transform: scale(1.0);                  -webkit-transform: scale(1.0);              }        }</style>
 <body><div class="um-win" id="index">    <div class="um-header">           </div>     <div class="um-content">        <div class="spinner">            <div class="spinner-container container1">                <div class="circle1"></div>                <div class="circle2"></div>                <div class="circle3"></div>                <div class="circle4"></div>            </div>            <div class="spinner-container container2">                <div class="circle1"></div>                <div class="circle2"></div>                <div class="circle3"></div>                <div class="circle4"></div>            </div>            <div class="spinner-container container3">                <div class="circle1"></div>                <div class="circle2"></div>                <div class="circle3"></div>                <div class="circle4"></div>            </div>        </div>    </div>     <div class="um-footer">     </div></div> <script> </script> </body>
</div>

第二种
<div>
<html lang="zh-cn">
<head>
    <meta charset="utf-8">
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
</div>

第三种
<div>
<svg version="1.1" id="loader-1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="40px" height="40px" viewBox="0 0 40 40" enable-background="new 0 0 40 40" xml:space="preserve">
<path opacity="0.2" fill="#000" d="M20.201,5.169c-8.254,0-14.946,6.692-14.946,14.946c0,8.255,6.692,14.946,14.946,14.946
    s14.946-6.691,14.946-14.946C35.146,11.861,28.455,5.169,20.201,5.169z M20.201,31.749c-6.425,0-11.634-5.208-11.634-11.634
    c0-6.425,5.209-11.634,11.634-11.634c6.425,0,11.633,5.209,11.633,11.634C31.834,26.541,26.626,31.749,20.201,31.749z"></path>
<path fill="#000" d="M26.013,10.047l1.654-2.866c-2.198-1.272-4.743-2.012-7.466-2.012h0v3.312h0
    C22.32,8.481,24.301,9.057,26.013,10.047z" transform="rotate(8.64432 20 20)">
<animateTransform attributeType="xml" attributeName="transform" type="rotate" from="0 20 20" to="360 20 20" dur="0.5s" repeatCount="indefinite"></animateTransform>
</path>
</svg>
</div>
<div>
<svg version="1.1" id="loader-1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="40px" height="40px" viewBox="0 0 50 50" style="enable-background:new 0 0 50 50;" xml:space="preserve">
<path fill="#000" d="M25.251,6.461c-10.318,0-18.683,8.365-18.683,18.683h4.068c0-8.071,6.543-14.615,14.615-14.615V6.461z" transform="rotate(257.602 25 25)">
<animateTransform attributeType="xml" attributeName="transform" type="rotate" from="0 25 25" to="360 25 25" dur="0.6s" repeatCount="indefinite"></animateTransform>
</path>
</svg>
</div>
<div>
<svg version="1.1" id="loader-1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="40px" height="40px" viewBox="0 0 50 50" style="enable-background:new 0 0 50 50;" xml:space="preserve">
<path fill="#000" d="M43.935,25.145c0-10.318-8.364-18.683-18.683-18.683c-10.318,0-18.683,8.365-18.683,18.683h4.068c0-8.071,6.543-14.615,14.615-14.615c8.072,0,14.615,6.543,14.615,14.615H43.935z" transform="rotate(227.66 25 25)">
<animateTransform attributeType="xml" attributeName="transform" type="rotate" from="0 25 25" to="360 25 25" dur="0.6s" repeatCount="indefinite"></animateTransform>
</path>
</svg>
</div>
</body> 
</html>  
第三种的实现代码  

```
<svg version="1.1" id="loader-1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="40px" height="40px" viewBox="0 0 40 40" enable-background="new 0 0 40 40" xml:space="preserve">
<path opacity="0.2" fill="#000" d="M20.201,5.169c-8.254,0-14.946,6.692-14.946,14.946c0,8.255,6.692,14.946,14.946,14.946
    s14.946-6.691,14.946-14.946C35.146,11.861,28.455,5.169,20.201,5.169z M20.201,31.749c-6.425,0-11.634-5.208-11.634-11.634
    c0-6.425,5.209-11.634,11.634-11.634c6.425,0,11.633,5.209,11.633,11.634C31.834,26.541,26.626,31.749,20.201,31.749z"></path>
<path fill="#000" d="M26.013,10.047l1.654-2.866c-2.198-1.272-4.743-2.012-7.466-2.012h0v3.312h0
    C22.32,8.481,24.301,9.057,26.013,10.047z" transform="rotate(8.64432 20 20)">
<animateTransform attributeType="xml" attributeName="transform" type="rotate" from="0 20 20" to="360 20 20" dur="0.5s" repeatCount="indefinite"></animateTransform>
</path>
</svg>
```