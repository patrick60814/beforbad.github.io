---
layout: post
title: Docker常用命令
date: 2021-08-01
Author: 南念
tags: [docker, Command]
comments: true
pinned: true
categories: 技术
---



记录学习docker时一些常用的命令
<!-- more -->
## 基础命令

```
docker pull    			--拉取镜像
docker images  			--查看本地镜像
docker run -d -p 80:80  --运行容器
docker ps	   		    --查看当前运行容器
docker stop <Id>		--停止容器
docker restart <Id>     --重启容器
docker rm <Id>		    --删除容器
docker rmi <name>       --删除镜像
```

## 示例

```
docker pull influxdb	

docker run -d -p 8083:8083 -p8086:8086 --expose 8090 --expose 8099 --name influxdb-test influxdb
admin  1234554321


docker exec -it 243c32535da7 /bin/bash		进入容器

docker run -it ubuntu /bin/bash		交互式启动容器

docker ps					查看运行中的容器

docker images				查看本地有的镜像



docker ps -a 		查看已停止的容器

docker start <容器 ID>	启动已停止的容器



docker stop <容器 ID>	停止容器

	

docker exec -it 243c32535da7 /bin/bash		进入容器




cyrilix/rabbitmq-mqtt:latest

docker run --name nginx-test -p 8081:80  -v $PWD/html:/usr/share/nginx/html -d nginx

			--name nginx-test：容器名称。

			-p 8080:80： 端口进行映射，将本地 8080 端口映射到容器内部的 80 端口。

			-d nginx： 设置容器在在后台一直运行。



docker run --name tomcat -p 8080:8080 -v $PWD/test:/usr/local/tomcat/webapps/test -d tomcat 

			-p 8080:8080：将主机的 8080 端口映射到容器的 8080 端口。

			-v $PWD/test:/usr/local/tomcat/webapps/test：将主机中当前目录下的 test 挂载到容器的 /test



docker run -itd --name mysql-test -p 3306:3306

docker run -itd --name redis-test -p 6379:6379 redis



docker run -itd --name mongo -p 27017:27017 mongo --auth

$ docker exec -it mongo mongo admin									# 创建一个名为 admin，密码为 123456 的用户。

>  db.createUser({ user:'admin',pwd:'123456',roles:[ { role:'userAdminAnyDatabase', db: 'admin'},"readWriteAnyDatabase"]});	# 尝试使用上面创建的用户信息进行连接。

> db.auth('admin', '123456')

								--auth：需要密码才能访问容器服务。

								 admin，密码为 123456

docker run -dit --name avatar_rabbitmq-mqtt -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=admin -p 15672:15672 -p 5672:5672 -p 1883:1883 cyrilix/rabbitmq-mqtt:latest



docker内部文件路径映射

docker run --name tomcat -p 8080:8080 -v $PWD/test:/usr/local/tomcat/webapps/test -d tomcat 

 docker run --name nginx2 -p 80:80 -v /usr/htm:/usr/share/nginx/html -d nginx
```

