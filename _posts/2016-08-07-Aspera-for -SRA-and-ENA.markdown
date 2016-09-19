---
layout: post
title:  "Aspera for SRA and ENA"
date:   2016-08-07
desc: "从ENA和SRA下载测序数据"
keywords: "Aspera,data"
categories: [NGS]
tags: [Aspera]
icon: microscope
---

ENA和SRA都是测序数据库，使用Aspera可以达到很高的下载速度。目前提供Aspera下载的NCBI和EBI数据库不多。

### 安装

- 从官网下载aspera-connect.tar.gz
- tar -zxvf aspera-connect.tar.gz
- sh aspera-connect-3.6.2.117442-linux-64.sh

### 复制许可证到根目录
- sudo cp ~/.aspera/connect/etc/aspera-license /usr/local/bin/
- cp ~/.aspera/connect/etc/asperaweb_id_dsa.putty ~/
- cp ~/.aspera/connect/etc/asperaweb_id_dsa.openssh ~/

### 设置环境变量
- export PATH=/home/usrname/.aspera/connect/bin

### 下载数据（以ENA为例）
- ascp -i ~/asperaweb_id_dsa.openssh -Tr -Q -l 100M -L- era-fasp@fasp.sra.ebi.ac.uk:*/vol1/ERA669/ERA669354/fastq/Illumina_Ampli1_EDTA.L1_P1.fq.gz .*


