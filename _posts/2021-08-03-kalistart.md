---
layout: post
title: kali初始化
date: 2021-08-03
Author: 南念
tags: [hack, kali, linux]
comments: true
toc: true
categories: 渗透
---



###### vim编辑配置文件显示行号 

set nu

###### 修改root登录ssh

修改配置文件

vim /etc/ssh/sshd_config

<!-- more -->

32行 PermitRootLogin  yes

37    PubKeyAuthentication yes

重启ssh服务 /etc/init.d/ssh restart

允许ssh开机自启

update -rc.d ssh enable



------



###### 系统更新

apt update  获取更新列表

apt upgrade   更新

apt-get在ubuntu系统中用于安装和更新软件的命令，和yum相比，它不需要安装yum源，

可以直接使用，命令简单又好用。

apt-get install package 安装package

apt-get install package --reinstall 重新安装包package

apt-get -f install 修复安装

apt-get update 更新源

apt-get upgrade 更新已安装的包

apt-get dist-upgrade 升级系统

apt-get remove package 删除包

apt-get remove package --purge 删除包，包括配置文件等

apt-get clean && sudo apt-get autoclean 清理无用的包
