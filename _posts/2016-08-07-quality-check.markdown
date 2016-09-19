---
layout: post
title:  "quality check装"
date:   2016-08-07
desc: "测序数据的质量检测"
keywords: "sequencing,quality check"
categories: [NGS]
tags: [NGS,QC]
icon: icon-microscope
---

FastQC和NGSQCToolkit都可以对测序数据进行质量控制

### FastQC

#### 安装
- 官网下载
- unzip -o FastQC*.zip
- sudo ln -s ~/FastQC/fastqc /user/local/bin/fastqc 

#### 使用
- 终端输入fastqc启动GUI
- fastqc -f fastq -o resultdir file*.fastq.gz

### NGSQCToolkit

#### 安装
- unzip -o NGSQCToolkit_v2.3.3.zip
- sudo apt-get install libgd2-xpm-dev
- sudo apt-get install libgd-graph-perl

#### 使用MCPAN安装perl模块
- sudo perl -MCPAN -e shell
- install String::Approx
- q

#### 使用（pair-end数据）
- perl $NGSQCHome/path/to/NGSQCToolkit/QC/IlluQC_PRLL.pl -pe Read1.fq Read2.fq 2 A -z g
- 2代表Illumina平台，A为auto-detect，-z g为以gz格式输出


--------------------------------------------------------------------------------

比较两者，FastQC,速度比NGSToolkit快很多，结果以html形式生成测序数据QC报告。NGSQCToolkit会对测序数据进行过滤，它给出的html形式的QC报告包括了原始数据和过滤后的数据质量，耗时极多。因此比较适合的做法是使用FastQC先进行质量评估，再利用NGSQCToolkit的QC工具和trim工具，对测距数据进行过滤。
