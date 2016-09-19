---
layout: post
title:  "install ubuntu"
date:   2016-08-07
desc: "ubuntu, win10 双系统安装"
keywords: "ubuntu,linux"
categories: [Linux]
tags: [ubuntul]
icon: icon-ubuntu
---

采用Win10+Ubuntu 16.04 双系统方案。 建议用USB制作启动盘安装，硬盘安装是个坑。

### 工具

- Ubuntu 16.04 iso
- UltralSO
- EasyBCD(用于开机引导，作用不大)

### 步骤

- 压缩磁盘，得到100G可用空间
- 使用UltraISO制作启动盘
- 进入BOIS，关闭安全启动，设置USB优先启动
- 重启，开始安装
- 若提示BOIS模式和UEFI模式的错误，停止安装并回到BOIS修改设置，否则可能丢失原系统。
- 使用自动分区

--------------------------------------------------------------------------------

Ubuntu的安装比较简单，成功启动系统盘后，5到10分钟即可完成，自带grub引导可以启动Windows系统，系统大小约3.8G，系统内部通过加载硬盘可以快速读取并修改Windows上的文件。
