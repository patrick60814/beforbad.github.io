---
layout: post
title: 第一篇Blog
date: 2021-07-21
Author: Patrick
tags: [Blog, start, 闲记]
categories: 闲记
comments: true
toc: true
---

2021-07-30上班的时候摸鱼在网上瞎逛，在youtube上看到一个频道朱的简介里有个人blog，就点击去看了看，然后就就被他的[blog](https://siemenstutorials.pw/https://siemenstutorials.pw/)吸引住了，真不错然后就开始研究这个blog怎么搭建的，就发现了github pag了
然后就开始了我的blog。

<!-- more -->
### 相关链接

[github pag](https://pages.github.com/)

[hexo](https://hexo.io/zh-cn/ )

[jekyll](http://jekyllcn.com/ )

[留言功能](https://valine.js.org/)

[别人的blog示例](https://xpoet.cn/links/)

知道githubpag使用的是静态网页后，就纠结一个问题，怎么实现写的blog页面更新到网站？难道每次都去改index页面吗 ，后来发现原来可以使用Markdown来写，主页直接调用，然后就发现了 hexo和Jekyll两个工具了，真不错。

说下我对这两个工具的看法吧

​	刚开始是想着使用hexo的，因为hexo里的主题模板多，而且好看，但是后来发现，他没有_post文件夹，只能每次在本地写，然后在 hexo g 生成静态页面，在hexo d 到github上，这就很烦，还要生存静态页面才可以，果断放弃。jekyll虽然模板没有hexo多，但是方便啊，而且纯静态页面，有点html基础的还是可以自己diy一下的。

​	Jekyll是github官方提供的，blog可以直接写到_post目录下，就可以了，这就很方便。

​	然后就是找jekyll的主题了，你可以在这里找到[jekyll](http://jekyllthemes.org/) 使用的话每个主题的GitHub页面都有，原理很简单，纯静态页面，你只需要把喜欢的主题pull到你本地，然后上传到你的github上，主要修改_config.yml文件，把里面的内容修改成你自己的。

