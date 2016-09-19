---
layout: post
title:  "adding disk space to linux in VM"
date:   2016-08-07
desc: "给linux虚拟机增加硬盘"
keywords: "VM,disk space"
categories: [Linux]
tags: [linux]
icon: icon-ubuntu
---

使用虚拟机安装linux后最大的一个问题就是磁盘空间不足，特别是由于分区原因，真正分配到/home目录下的空间实际上更少。在VMware中调整配置可以往/home中增加空间。

### 在VMare中给linux增加一个硬盘
* 虚拟机-设置-硬盘-添加
* 选择SCSI
* store virtual disk as a single file
	
### 在linux虚拟机中挂载硬盘

#### 新建分区

	> fdisk -l #查看分区
	> fdisk /dev/sdb
	> m
	> n
	> p
	> 1
	> w
	> fdisk -l #查看分区是否成功

#### 格式化

	> mkfs -t ext3 /dev/sdb1

#### 挂载

	> mkdir /home/usrname/sdb1
	> mount /dev/sdb1 /home/usrname/sdb1







