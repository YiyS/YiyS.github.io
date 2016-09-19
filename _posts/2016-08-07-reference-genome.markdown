---
layout: post
title:  "reference genome"
date:   2016-08-07
desc: "有关参考基因组的一些事"
keywords: "reference genome"
categories: [NGS]
tags: [NGS,reference]
icon: icon-microscope
---

人类参考基因组可以从NCBI和UCSC下载,以UCSC为例

### 方法一

- for i  in $(seq 1 22) X Y M
- do wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/chromosomes/chr${I}.fa.gz
- done 


### 方法二(ftp)

- ftp hgdownload.cse.ucsc.edu
- username: anonymous
- password: your email address,
- cd goldenPath/hg19/chromosomes
- mget chr*.fa.gz

### 生成hg19.fasta
- gunzip -k chr*.fa.gz
- for i in $(seq 1 22) X Y M
- do cat chr${i}.fa>>hg19.fasta
- done


--------------------------------------------------------------------------------

#### 参考资料
[基因各种版本对应关系]<http://www.bio-info-trainee.com/1469.html>""
