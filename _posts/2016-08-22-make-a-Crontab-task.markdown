---
layout: post
title:  "make a Cron task"
date:   2016-08-21
desc: "使用Cron定时服务"
keywords: "linux,automatic"
categories: [Linux]
tags: [ubuntu]
icon: icon-ubuntu
---

使用crontab 来设置定时任务，这里以监控硬盘使用情况为例

### 安装

*  cron, crontab在ubuntu下都是自带的

### 使用

`````````````
	> gedit storage.sh
	> #在storage.sh中输入如下命令
	> df -h | grep /dev/sdb1 | tee -a /home/usrname/storage.log
	> crontab -e
	> */10 * * * * sh /home/usrname/storage.sh
	> service cron restart
	> service cron status
`````````````
	






