---
layout: post
title: 定义图像中可点击区域map
date: 2021-08-04
Author: 南念
tags: [H5, JavaScript, html]
comments: true
toc: true
categories: H5
---



##### 定义图像中可点击区域map

<!-- more -->

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>点击太阳或其他行星，注意变化：</p>			

<img src="planets.gif" width="145" height="126" alt="Planets" usemap="#planetmap">		#alt --图像加载失败 显示文字

<map name="planetmap">
  <area shape="rect" coords="0,0,82,126" alt="Sun" href="sun.htm">
  <area shape="circle" coords="90,58,3" alt="Mercury" href="mercur.htm">
  <area shape="circle" coords="124,58,8" alt="Venus" href="venus.htm">
</map>

</body>
</html>

<area shape="default|rect|circle|poly">


```

| default | 规定全部区域。   |
| ------- | ---------------- |
| rect    | 定义矩形区域。   |
| circ    | 定义圆形。       |
| poly    | 定义多边形区域。 |

| *x1,y1,x2,y2*          | 如果 shape 属性设置为 "rect"，则该值规定矩形左上角和右下角的坐标。 |
| ---------------------- | ------------------------------------------------------------ |
| *x,y,radius*           | 如果 shape 属性设置为 "circ"，则该值规定圆心的坐标和半径。   |
| *x1,y1,x2,y2,..,xn,yn* | 如果 shape 属性设置为 "poly"，则该值规定多边形各顶点的值。如果第一个坐标和最后一个坐标不一致，那么为了关闭多边形，浏览器必须添加最后一对坐标。 |
