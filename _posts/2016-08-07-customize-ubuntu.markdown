---
layout: post
title:  "customize ubuntu"
date:   2016-08-07
desc: "安装Ubuntu 16.04 后需要做的几件事"
keywords: "linux"
categories: [Linux]
tags: [ubuntu]
icon: icon-ubuntu
---

### 改变软件源

- 设置-软件-安装源
- Enable Canonical 合作伙伴

### 安装解码器

- sudo apt-get install ubuntu-restricted extras

### 电源管理(TPL)
- sudo add-apt-repository ppa:linrunner/tlp
- sudo apt-get update
- sudo apt-get install tlp tlp-rdw
- sudo tlp start

--------------------------------------------------------------------------------

解码器的安装主要是可以在ubuntu系统下观看视频，而电源部分，曾有人提出，由于驱动所致独显不能关闭，笔记本安装Ubuntu后发热量会增加，在16.04 版本中，这个问题应该已经解决，可以输入
- cat /sys/kernel/debug/vgaswitcheroo/switch
查看显卡状态，以决定是否需要手动关闭独立显卡。
