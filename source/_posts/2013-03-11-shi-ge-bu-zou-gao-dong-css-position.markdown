---
layout: post
title: "十個步驟搞懂CSS Position"
date: 2013-03-11 01:03
comments: true
categories: CSS
---
十個步驟搞懂CSS Position  
範例1: 若要子元素參考父元素的中間, 則父元素要設position: relative, 子元素要設position: absolute並且left: 50% \(其餘子元素會往左上縮\)  
範例2: 若要子元素參考父元素的左邊, 則子元素要設float: left \(其餘子元素會往左上縮\)


不囉唆直接看圖:  
[http://www.barelyfitz.com/screencast/html-training/css/positioning/](http://www.barelyfitz.com/screencast/html-training/css/positioning/)  
\<div id="div-before"\>\<p\>紫色\</p\>\</div\>  
　\<div id="div-1"\>  
　　\<p\>黑色\</p\>  
　　\<div id="div-1a"\>\<p\>紅色\</p\>\</div\>  
　　\<div id="div-1b"\>\<p\>綠色\</p\>\</div\>  
　　\<div id="div-1c"\>\<p\>藍色\</p\>\</div\>  
　\</div\>  
\<div id="div-after"\>靛色\</p\>\</div\>  

