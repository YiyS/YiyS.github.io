---
layout: post
title:  "Tophat trouble shooting"
date:   2016-08-18
desc: "Tophat使用过程中出现的问题和结局办法"
keywords: "tophat,RNA-seq"
categories: [NGS]
tags: [sequencing]
icon: icon-microscope
---

一些在使用tophat进行比对中可能出现的问题.

### err=127

* 如图

![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/TOPHAT1.JPG)
	
* 可能原因

a. boost未正确编译

b. 环境变量

* 解决方法

a. 去掉参数 -p ，使用单线程，这个不太现实。

b. 先确认是否安装了boost，若没，去安装一个

c. 若安装了boost依然出现这个问题，输入

````````
	> whereis libboost_thread.so.1.61.0
	> #若返回地址如下
	> libboost_system.so.1.61:/usr/local/lib/libboost_system.so.1.61.0
	> #则是环境变量问题，继续
	> export LD_LIBRARY_PATH=/usr/local/lib/: $LD_LIBRARY_PATH
	> echo LD_LIBRARY_PATH
````````````

d. 以上步骤设置好了环境变量，剩下还需检测问题是否解决

``````````
	> ldd /usr/local/bin/segment_juncs
```````````

* 问题解决

![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/TOPHAT2.JPG)


### err=2

* 如图

![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/TOPHAT3.JPG)

* 解决方法

加上参数--keep-tmp

* 若还没解决

降低线程数-p不超过核心数，或者清理一下硬盘空间，我也不知道是哪个起作用了(@_@;)

### Errno 28

* 这个问题是硬盘空间不足导致的，增大硬盘可用空间也没其他办法

![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/TOPHAT4.JPG)

* 所以应该给tophat预留多少硬盘空间，以下图表提供参考，所用的为共5.7G的pairend数据

![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/TOPHAT5.JPG)

----------

TOPHAT运行时间很长！这些问题是比对快结束才出现的，建议一开始就使用ldd检查！


#### 参考资料

[Question: Error: segment-based junction search failed with err =127](https://www.biostars.org/p/163067/)

[Question: Libboost error while running Tophat alignment job](https://www.biostars.org/p/185969/)

[LD_LIBRARY_PATH环境变量的设置](http://james23dier.iteye.com/blog/763274)

[Question: Tophat Error : Oserror: Errno 2 No Such File Or Directory](https://www.biostars.org/p/42792/)



