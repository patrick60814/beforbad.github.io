---
layout: post
title: 页面上中下跳转方法
date: 2021-08-04
Author: 南念
tags: [H5, JavaScript, html]
comments: true
toc: true
categories: H5
---

##### 页面上中下跳转方法

<!-- more -->

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	<style>
		div{
			width: 300px;height: 800px;border-style: solid; border-width: 5px 5px;border-color: red;	}
	</style>
	</head>
	<body>
		<div><a id="t">1</a>	\\定义top位置
		<a href="#t">top</a>	\\跳转至t 位置
		<a href="#c">center</a> 	\\跳转至 c 位置
		<a href="#b">button</a>		\\ 跳转至 b 位置
		</div>
		<div><a id="c">center</a></div>		\\ 定义 c 位置
		<div><a id="b"></a>  		\\定义b位置
		<a href="#t">top</a>
		<a href="#c">center</a>
		<a href="#b">button</a>
		</div>
	</body>
</html>

```

