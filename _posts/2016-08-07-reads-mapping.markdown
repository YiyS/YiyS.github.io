---
layout: post
title:  "reads mapping"
date:   2016-08-07
desc: "序列比对"
keywords: "mapping,bwa"
categories: [NGS]
tags: [bwa,WGS,WES]
icon: icon-microscope
---

使用bwa,bwa提供三个算法，分别通过bwa aln, bwa sw, bwa mem使用

### 安装
- ubuntu 已提供bwa安装
- sudo apt install bwa

### 建立索引
- bwa index -a bwtsw hg19.fasta
- 全基因组使用的a参数为bwtsw

### Mapping(pairend)

#### 使用 bwa aln
- bwa aln hg19.fasta Read1.fastq.gz > read1.sai
- bwa aln hg19.fasta Read2.fastq.gz > read2.sai
- bwa sampe -f pair-end.sam hg19.fasta read1.sai read2.sai Read1.fastq.gz Read2.fastq.gz
	
#### 使用 bwa aln
- bwa mem -M hg19.fasta Read1.fastq.gz Read2.fastq.gz > pair-end.sam
