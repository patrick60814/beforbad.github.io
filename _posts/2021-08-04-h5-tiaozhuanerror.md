---
layout: post
title: 不跳转页面在iframe中展示超链接页面
date: 2021-08-04
Author: 南念
tags: [H5, JavaScript, html]
comments: true
toc: true
categories: H5
---



##### 不跳转页面在iframe中展示超链接页面

<!-- more -->

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head> 
<body>

<iframe src="demo_iframe.htm"  name="iframe_a"  width="400"  height="400"  frameborder="0">您的浏览器不支持iframe标签</iframe>   	#frameborder  设置边框
<p><a href="//www.runoob.com"  target="iframe_a">RUNOOB.COM</a></p>		#

<p><b>注意：</b> 因为 a 标签的 target 属性是名为 iframe_a 的 iframe 框架，所以在点击链接时页面会显示在 iframe框架中。</p>

</body>
</html>

页面初始 iframe中展示的是  demo_iframe.html 页面  点击下方链接后 iframe中展示的是  链接的页面
```

