---
layout: post
title:  "using SOAPfuse"
date:   2016-08-23
desc: "SOAPfuse使用记录"
keywords: "SOAPfuse,RNA-seq"
categories: [NGS]
tags: [sequencing]
icon: icon-microscope
---

SOAPfuse, SOAPfusion，不是同一个东西。

### 安装

*  免安装，解压即用，

*  官网上未更新，到sourceforge下载

*  修改环境变量

````````````````
	> export PERL5LIB=$SOAPfuse/source/bin/perl_module:$PERL5LIB
``````````````````


### 使用

* 建立database，下载4个文件，自己创建一个文件relationship.list如下

> 1	chr1
> 2	chr2
> .....
> X	chrX
> Y	chrY
> M	chrM

* 中间以制表符分隔

* 傻瓜式，看manuel填写config

* 不行可以试试其他软件，比如tophat2 --fusion-search







