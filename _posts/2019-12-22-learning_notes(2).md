---
title: "如何用CSS，JavaScript实现手风琴导航菜单？"
layout: page
excerpt_separator: "<!--more-->"
categories:
  - 学习笔记
---  

## ==手风琴导航栏菜单==
<section>
<!DOCTYPE html>
<html>
<head>
    <title>Side Navigator Demo</title>
    <script src="https://cdn.staticfile.org/jquery/1.10.2/jquery.min.js">
    </script>
    <link rel="stylesheet" href="https://cdn.staticfile.org/font-awesome/4.7.0/css/font-awesome.css">
    <style>
        body {
            padding: 0px;
            margin: 0px;
            /* background-color: cadetblue; */
        }
        
        .side-nav {
            width: 300px;
            position: fixed;
            height: 100%;
            z-index: 1;
            top: 0;
        }
        
        ul {
            list-style-type: none;
            padding: 0px;
            margin: 0px;
            font-size: 20px;
            color: #ffffff;
        }
        
        .first-menu-item {
            padding: 10px;
            border-bottom: 1px solid #d3d3d3;
            background-color: #2e8b57;
        }
        
        .second-menu-item {
            padding: 10px 10px 10px 20px;
            border-bottom: 1px solid #d3d3d3;
            background-color: #32cd32;
        }
        
        .third-menu-item {
            padding: 10px 10px 10px 30px;
            border-bottom: 1px solid #d3d3d3;
            background-color: #3cb371;
        }
        
        .menu-group {
            display: none;
        }
        
        .drop-down-item {
            position: relative;
        }
        
        .drop-down-item i {
            position: absolute;
            right: 14px;
            top: 14px;
        }
        
        .arrow-rotate {
            -webkit-transform: rotate(90deg);
            -ms-transform: rotate(90deg);
            -o-transform: rotate(90deg);
            transform: rotate(90deg);
        }
        
        .second-menu-item-selected {
            background-color: #32aa32;
        }
        
        .third-menu-item-selected {
            background-color: #3c8871;
        }
    </style>
</head>
 
<body>
    <script>
        $(document).ready(function() {
            $(".drop-down-item").click(function() {
                $(this).next(".menu-group").slideToggle();
                $(this).parent().siblings().find(".menu-group").slideUp();
                var arrow = $(this).children(".fa-angle-right");
                if (arrow.hasClass("arrow-rotate")) {
                    arrow.removeClass("arrow-rotate");
                } else {
                    arrow.addClass("arrow-rotate");
                }
                var arrow_brothers = $(this).parent().siblings().find(".fa-angle-right");
                if (arrow_brothers.hasClass("arrow-rotate")) {
                    arrow_brothers.removeClass("arrow-rotate");
                }
            });
 
            $(".second-menu-item.menu-link").click(function() {
                $(".second-menu-item.menu-link").removeClass("second-menu-item-selected");
                $(".third-menu-item.menu-link").removeClass("third-menu-item-selected");
                $(this).addClass("second-menu-item-selected");
            });
 
            $(".third-menu-item.menu-link").click(function() {
                $(".second-menu-item.menu-link").removeClass("second-menu-item-selected");
                $(".third-menu-item.menu-link").removeClass("third-menu-item-selected");
                $(this).addClass("third-menu-item-selected");
            });
        });
    </script>
    <div class="side-nav">
        <ul>
            <li>
                <div class="first-menu-item drop-down-item">Frontend <i class="fa fa-angle-right"></i></div>
                <ul class="menu-group">
                    <li>
                        <div class="second-menu-item menu-link">HTML</div>
                    </li>
                    <li>
                        <div class="second-menu-item drop-down-item">CSS <i class="fa fa-angle-right"></i></div>
                        <ul class="menu-group">
                            <li>
                                <div class="third-menu-item menu-link">Bootstrap</div>
                            </li>
                            <li>
                                <div class="third-menu-item menu-link">Font Awesome</div>
                            </li>
                            <li>
                                <div class="third-menu-item menu-link">Foundation</div>
                            </li>
                        </ul>
 
                    </li>
                    <li>
                        <div class="second-menu-item drop-down-item">JavaScript <i class="fa fa-angle-right"></i></div>
                        <ul class="menu-group">
                            <li>
                                <div class="third-menu-item menu-link">JQuery</div>
                            </li>
                            <li>
                                <div class="third-menu-item menu-link">Angular</div>
                            </li>
                            <li>
                                <div class="third-menu-item menu-link">VueJS</div>
                            </li>
                        </ul>
 
                    </li>
                </ul>
            </li>
            <li>
                <div class="first-menu-item drop-down-item">Backend <i class="fa fa-angle-right"></i></div>
                <ul class="menu-group">
                    <li>
                        <div class="second-menu-item menu-link">Java</div>
                    </li>
                    <li>
                        <div class="second-menu-item menu-link">C</div>
                    </li>
                    <li>
                        <div class="second-menu-item menu-link">C++</div>
                    </li>
                    <li>
                        <div class="second-menu-item menu-link">Python</div>
                    </li>
                    <li>
                        <div class="second-menu-item menu-link">PHP</div>
                    </li>
                </ul>
            </li>
            <li>
                <div class="first-menu-item drop-down-item">Mobile <i class="fa fa-angle-right"></i></div>
                <ul class="menu-group">
                    <li>
                        <div class="second-menu-item menu-link">Android</div>
                    </li>
                    <li>
                        <div class="second-menu-item menu-link">Swift</div>
                    </li>
                    <li>
                        <div class="second-menu-item menu-link">Ionic</div>
                    </li>
                </ul>
 
            </li>
        </ul>
    </div>
</body>
</html>
</section>


## 参考资料
[CSS，JavaScript实现手风琴导航菜单](https://blog.csdn.net/weixin_33913377/article/details/91925689)