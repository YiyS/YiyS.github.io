---
layout: post
title:  "make best use of CPU"
date:   2016-08-07
desc: "CPU的高效利用"
keywords: "CPU,ubuntu"
categories: [Linux]
tags: [ubuntu]
icon: icon-ubuntu
layout: post
---

对于CPU的利用，应该保持在一个合适的范围，利用率过低，工作效率不能达到最大，而利用率过高，发热问题也会给CPU带来很大的损耗。本文介绍一下linux系统下如何控制CPU占用。

### 提高CPU利用率
- 使用nohup投递多个命令

> nohup command 1> outputfile 2> output.log &

- 使用Ctrl+alt+T，开启多个终端分别输入多个命令：) 

### 降低CPU占用
- nice
nice通过降低进程优先级发挥作用，因此，当一个进程占用了100%的CPU时，nice不起作用。使用方式与sudo类似，加在命令前面

- cpulimit
cpulimit可以直接限制进程的CPU占用率不超过一定的数值，事实上会超过一点点，需要根据实际适当调整参数。cpulimit在于它是以PID识别进程的，因此在运行过程中，可以不断修改参数。下面的代码通过PID限制进程的CPU占用率不超过50%。

> sudo apt install cpulimit 
>
> cpulimit -50 number -p PID

- cgroups
设定控制组，控制CPU的使用率和分配。默认cpu.shares=1024，改为512后将在cpulimited和cpulesslimit间按2:1分配CPU。仅在同时运行两组进程时生效。

> sudo cgcreate -g cpu:/cpulimited
>
> sudo cgcreate -g cpu:/lesscpulimited
>
> sudo cgset -r cpu.shares=512 cpulimited
>
> sudo cgexec -g cpu:cpulimited command

----------------------
CPU分配的控制，能够在最合适的时间里完成任务，同时保护了电脑，好好睡一觉，等着明天醒来收数据吧。
