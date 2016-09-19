---
layout: post
title:  "avoid trouble while installing cummeRbund"
date:   2016-08-26
desc: "一种可能是最可以避免 non zero exit 的 cummeRbund 包安装方法。"
keywords: "R,RNA-seq"
categories: [RNA-seq]
tags: [sequencing]
icon: icon-microscope
---

### 首先安装 XML 包

````````````````
	> biocLite('XML')
	> #若成功，进入下一步
	> #若显示 non zero exit
	> sudo apt-get install libxml2-dev
	> #再安装 XML
``````````````````

### 再安装 RCurl 包

````````````````
	> biocLite('RCurl')
	> #若成功，进入下一步
	> #若显示 non zero exit
	> sudo apt-get install libcurl4-gnutls-dev
	> #再安装 RCurl
``````````````````

### 安装 cummeRbund

````````````````
	> biocLite('cummeRbund')
``````````````````







