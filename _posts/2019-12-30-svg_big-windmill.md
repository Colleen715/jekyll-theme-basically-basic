---
title: 看！会变大的翻转风车！
layout: page
excerpt_separator: "<!--more-->"
categories: 
  - svg制作
tags:
  - svg
---  

	<style>
	svg {
	    width: 150px;
	    height: 150px;
	  
	    -webkit-transition: -webkit-transform 1s, width 1.5s, height 2s;
	    transition: width 3s, height 1.8s, transform 2.5s;
	}
	svg:hover {
	    width:250px;
	    height:250px;
	    -webkit-transform: rotateX(1600deg);
	    transform: rotateY(1600deg);
	    color:#D86C6C;
	}
		.box {
	  position: relative;
	  width: 500px;
	  height: 450px;
	  animation: jump 2s alternate infinite;
	  
	   &:before,
	  &:after {
	    position: absolute;
	    content: '';
	    left: 69px;
	    top: 0;
	    width: 70px;
	    height: 110px;
	    background: $strawberry;
	    border-radius: 60px 60px 0 0;
	    transform: rotate(-45deg);
	    transform-origin: 0 100%;
	  }
	  
	  &:after  {
	    left: 0;
	    transform: rotate(45deg);
	    transform-origin: 100% 100%;
	  }
	}
	@keyframes jump {
	  0% {
	    top: -40px;
	    transform: rotate(20deg);
	  }
	  
	  100% {
	    top: 0;
	    transform: rotate(-20deg);
	  }
	  
	}
	
	@keyframes blink {
	  0% {
	    width: 10px;
	    height: 10px;
	  }
	  
	  100% {
	    height: 1px;
	  }
	}
	</style>
	</head>
<body>
 <svg aria-hidden="true" focusable="false" data-prefix="fas" data-icon="fan" class="svg-inline--fa fa-fan fa-w-16" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
	 <path fill="#D86C6C" d="M352.57 128c-28.09 0-54.09 4.52-77.06 12.86l12.41-123.11C289 7.31 279.81-1.18 269.33.13 189.63 10.13 128 77.64 128 159.43c0 28.09 4.52 54.09 12.86 77.06L17.75 224.08C7.31 223-1.18 232.19.13 242.67c10 79.7 77.51 141.33 159.3 141.33 28.09 0 54.09-4.52 77.06-12.86l-12.41 123.11c-1.05 10.43 8.11 18.93 18.59 17.62 79.7-10 141.33-77.51 141.33-159.3 0-28.09-4.52-54.09-12.86-77.06l123.11 12.41c10.44 1.05 18.93-8.11 17.62-18.59-10-79.7-77.51-141.33-159.3-141.33zM256 288a32 32 0 1 1 32-32 32 32 0 0 1-32 32z">
		 
	 </path>
</svg>

