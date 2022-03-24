---
layout: post
title: redhat
date: 2022-03-22
Author: 南念
tags: [hack, redhat，shell]
comments: true
toc: true
categories: redhat
---


#### 中科曙光服务器安装redhat7.9测试linux基础命令
```
##1.用户密码复杂度
Vim /etc/pam.d/system-auth
即在/etc/pam.d/system-auth中的“password requisite pam_pwquality.so”行尾添加具体参数，比如“minlen=8 ucredit=-1 lcredit=-1 ocredit=-1 dcredit=-1”
参数如下：
minlen=16		#最小密码长度16位
ucredit=-1		#最少一个大写字母
lcredit=-1			#最少一个小写字母
ocredit=-1		#最少一个特殊符合
dcredit=-1		#最少一个数字
ocredit = -3		#至少包含3个特殊字符
#注：只真对非root用户有效，root可更改其他用户密码随意。
<!-- more -->
```
```
##2.限制密码过期时间
Vim /etc/login.defs	中的 
PASS_MAXDAYS  90	#过期时间为90天，到期强制用户修改密码
```
```
##3.锁定用户
usermod -L test		#锁定
usermod -U test		#解锁
```
```
##4.查看用户权限
tail -5 /etc/passwd		#查看前5个
```
```
##5.修改文件可读写
Chmod u+w /filename		#修改filename文件可读性
```
```
##6.umask 控制默认权限，不要使默认的文件和目录具有全权而设的

文件全权为666 文件夹全权为777 ，umask默认为022，默认创建文件权限为（6-0，6-2，6-2）644，默认创建文件夹权限为（7-0，7-2，7-2）755 。
   所属者	     组用户	   其他用户		
d  rwx rwx rwx	 rwx	 rwx	 rwx	777	d表示文件夹、目录
	         111     111	 111		
- rw- r-- r--	 rw-	 r--	 r--	644	-表示文件
	         110	 100	 100		
修改umask值:  umask 011 
 ```
 ```
##7.ACL权限查看
getfacl 1.txt 		#查看1.txt权限
setfacl -m u:test:rw- 1.txt	#修改test用户对 1.txt 文件的权限
setfacl -m u:test:6 1.txt		#rwx也可用 7带替
```
```
##8.nfs协议共享文件夹
(1)A主机 192.168.1.3
yum install -y nfs-utils  		#安装nfs软件
mkdir /data				#创建用来共享的目录
vim /etc/exports			#修改nfs配置文件
/data 192.168.1.0/24(rw)	#共享目录路径 共享网段 共享权限
systemctl start nfs			#启动服务
exports -v				#查看状态
(2)B主机 192.168.1.4
mkdir /test			#创建挂载位置
mount -t nfs -o vers=3 192.168.1.3:/data /test	#挂载
df -hT  				#查看挂载信息
```
```
##9.磁盘分区
fdisk -L 			#查看磁盘分区
df -hT 			#查看挂载
分区：fdisk		#超过2T不能用		使用parted
fdisk /dev/sdb			#进入/dev/dsb硬盘分区交互界面
m 		#获得帮助
n      	#新建分区		d   	#删除分区
p  		#创建主分区		m    	#创建扩展分区
w     	#保存更改
```
```

##10.LVM 逻辑卷管理（无需停机的情况下可以方便地调整各个分区大小，可多块硬盘堆叠，大容量盘）
fdisk /dev/sdb		#磁盘分区
n 				#新建分区
P				#创建主分区
1				#分区编号
回车			#分区起始位
+5G				#加5G空间
T				#修改分区标签
8e				#修改标签为LVM
W				#保存并退出
Pvcreate /dev/sdb{1,2}			#创建pv  		sdb{1,2} 分区1、2  lsblk查看分区号
Pvdisplay						#查看pv
Vgcreate  vg0 /dev/sdb{1,2}   	#创建Vg卷组
Vgdisplay						#查看vg
Lvcreate -n lv0 -L 8G vg0 		#创建lv逻辑卷
Lvdisplay						#查看lv逻辑卷
#lV就相当与一个分区 可直接格式化然后挂在
格式化：
mkfs.xfs /dev/vg0/lv0 		#格式化为xfs
mkfs.ext4 /dev/vg0/lv0 		#格式化为ext4
#xfs
对于存储海量小文件或者超大规模文件，文件也很大，建议使用xfs。
它是一个64位文件系统，最大支持8EB减一的单个文件系统，实际部署取决于宿主操作系统的最大块限制。
##ext4
目前主流稳定的文件系统。容量达1EB，文件内容达16TB
然后挂在就可以使用了
LV扩容			
Lvextend -L 5G /dev/vg0/lv0		#扩容5G
Xfs-growfs /dev/vg0/lv0 			#扩容后检查
删除lvm
umount /dev/vg0/lv0		#解除挂载
Lvremove /dev/vg0/lv0 		#移除lv
Vgremove /dev/vg0			#移除vg
Pvremove /dev/sdb			#移除pv

```
**本地yum源配置步骤：**
**1、安装好RedHat后，使用root账户登陆系统,**
*#将安装rhel7所使用的iso光盘挂载到/mnt目录下*

```
[root@localhost ~]# mount -t iso9660 -o,loop /dev/sr0 /mnt
```
*或*
```
[root@localhost ~]# mount /dev/cdrom /mnt
```
*#注意此处二选一即可（均为单次有效，重启失效）*
**2、进入/etc/yum.repos.d/目录下，创建rhel7.repo配置文件，并编辑此文件**
```
[root@localhost ~]# cd /etc/yum.repos.d/``[root@localhost yum.repos.d]# touch rhel7.repo``[root@localhost yum.repos.d]# vim rhel7.repo
```
**3、rhel7.repo文件中的内容如下**

```
[rehl7]``name=rehl7   #自定义名称``baseurl=file:``///mnt   #本地光盘挂载路径``enabled=1   #启用yum源，0为不启用，1为启用``gpgcheck=0   #检查GPG-KEY，0为不检查，1为检查``：wq   #保存退出
```
**4、检查本地Yum源是否成功**
*#清除Yum源缓存*

```
[root@localhost yum.repos.d]# yum clean all
```

*#缓存本地Yum源*

```
[root@localhost yum.repos.d]# yum makecache
```

*#列出Yum软件列表*

```
[root@localhost yum.repos.d]# yum list
```

***本地配置成功！***

 

**附：常用Yum命令**
yum repolist all    *#列出所有仓库*
yum list all    *#列出仓库中所有软件包*
yum info <软件包名>    *#查看软件包信息*
yum install <软件包名>    *#安装软件包*
yum reinstall <软件包名>   *#重新安装软件包*
yum update <软件包名>    *#升级软件包*
yum remove <软件包名>    *#移除软件包*
yum clean all    *#清除所有仓库缓存*
yum check-update    *#检查可更新的软件包*

