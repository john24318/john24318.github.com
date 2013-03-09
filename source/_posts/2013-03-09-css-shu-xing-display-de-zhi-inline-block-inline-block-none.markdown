---
layout: post
title: "CSS 屬性 display 的值 inline block inline-block none"
date: 2013-03-09 18:24
comments: true
categories: CSS
---
常用的4種display:  
**1. display: none**   
**2. display: inline**  (ex:  \<a\>、\<span\>、\<b\>、\<i\>、\<img\>、\<iframe\>...)  
**3.display: block**  (ex:  \<div\>、\<p\>、\<h1\>、\<h2\>...)  
**4.display: inline-block**  
<!-- more -->


**1. display: none**  

把 HTML 元件的 display 設為 none 就是不顯示這個東西。display: none 和 visibility: hidden 的差別是 display: none 這個東西就不見了，不佔空間，visibility: hidden 只是隱形看不見，還是有佔空間。


**2. display: inline**  

\<a\>、\<span\>、\<b\>、\<i\>、\<img\>、\<iframe\>...  這幾個 HTML 元素預設的 display 屬性是 inline，用最簡單的講法解釋 display: inline 就是兩個 display: inline 的元素連在一起會在同一行，不會換行。  

display: inline 的 HTML 元素可以有 margin-left、margin-right、padding-left、padding-right，但不能有 margin-top、margin-bottom、padding-top、padding-bottom、width、heightbackground-image 。  

要讓 display: inline 元素水平置中的方式是在此元素的父元素加上 text-align: center。  
※當然你也可以用 CSS 把預設是 display: inline 的 HTML 元素設成 display: block 。  

附帶一提，display: inline 元素不該包住 display: block 元素。


**3.display: block**  

\<div\>、\<p\>、\<h1\>、\<h2\>...  這幾種 HTML 元素預設的 display 屬性是 block ，簡單講就是不管 display: block 元素的前面後面是什麼，碰到 display: block 元素就是會換行，而 display: block 元素的寬度預設會撐到最大。  

display: block 元素不管是 margin、padding、width、height、background-image 通通都可以。  

要將 display: block 元素水平置中，方法是在此元素加上 margin: 0 auto， 0 可以取代為任何數字。  

※當然也可以用 CSS 把預設是 display: block 的 HTML 元素設成 display: inline 。


**4.display: inline-block**  

顧名思義，就是外面是 inline，裡面是 block 。  

所以碰到 display: inline-block 元素不會換行，但是又可以設定 padding-top、padding-bottom、width、height、background-image。  

用 CSS 讓連結用圖片顯示就是 inline-block 常見的應用。


參考資料：[http://blog.xuite.net/vexed/tech/29221717-CSS+%E5%B1%AC%E6%80%A7+display+%E7%9A%84%E5%80%BC+inline+block+inline-block+none](http://blog.xuite.net/vexed/tech/29221717-CSS+%E5%B1%AC%E6%80%A7+display+%E7%9A%84%E5%80%BC+inline+block+inline-block+none)
