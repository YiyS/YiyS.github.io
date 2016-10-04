---
layout: post
title:  "Files in perl"
date:   2016-10-04
desc: "second"
keywords: "perl"
categories: [Perl]
tags: [perl]
icon: icon-perl
---


perl 中对文件的操作 

## open 函数

- 需要三个参数
- 句柄，即 Handle，必须使用大写
- 尖括号运算符，<为读取，>为重写，>>为追加写

```
# 打开并在屏幕输出一个文件
# MYFILE为句柄
open(MYFILE,'<',"myfile") or die"Can't open myfile:$!\n";
$myfile=<MYFILE>;
close(MYFILE);
print $myfile;

## 写入一个文件
open(MYFILE,'>',"myfile") or die"Can't write myfile:$!\n";

````

