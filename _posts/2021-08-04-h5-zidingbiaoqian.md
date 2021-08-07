---
layout: post
title: 添加自定义标签
date: 2021-08-04
Author: 南念
tags: [H5, JavaScript, html]
comments: true
toc: true
categories: H5
---



##### 添加自定义标签

<!-- more -->

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8"> 
<title>为 HTML 添加新元素</title>
<script>
document.createElement("myHero")  \\添加新标签
</script>
<style>
myHero {
    display: block;
    background-color: #ddd;
    padding: 50px;
    font-size: 30px;
}				\\定义新标签
</style> 
</head>
<body>
 
<h1>我的第一个标题</h1>
 
<p>我的第一个段落。</p>
 
<myHero>我的第一个新元素</myHero>
 
</body>
</html>


```
