---
layout: post
title:  "the structure of genome"
date:   2016-10-4
desc: "a deep search"
keywords: "perl"
categories: [Perl]
tags: [perl]
icon: icon-perl
---


基因组结构，关于 primary assembly, analysis set, decoy, alt, HLA

## 基本概念

### contigs

- 没有 gaps 的连续序列

### 

### alt

- 同一位置的不同序列，等位
- 在参考基因组中表示为，chr6_GL000250v2_alt

### unlocalized sequence

- map 到一个染色体上，未知顺序，位置
- 在参考基因组中表示为，chr17_GL000205v2_random

### unplaced sequence

- 未知染色体
- 在参考基因组上表示为，chrUn_GL000220v1

### PAR 区域

- 伪染色体序列，存在于X和Y染色体上
- 性染色体上唯一可参加互换的位置

### decoy genome

- bwa 开发者 Heng Li 创造
- 人类疱疹病毒 human herpesvirus 4, type 1, 也叫 Epstein-Barr virus (EBV) 
- 从 HuRef， NA12878，construct的其他序列
- chxxx_decoy

### Patche

- 是基因小版本，如 GRCh38.7 和 GRCh38.6 之间的不同的序列
- fix patches should take precedence over the chromosomes
- treat novel patches as population sequence variants

## 各种基因组

### primary assembly

- 包含组装好的染色体，chr1-chr22, chrX, chrY, chrM
- unlocalized sequence, chrxxx_random
- unplaced sequence, chUn_xxxx

### UCSC 的 analysis set

- 这里是下载地址：http://hgdownload.cse.ucsc.edu/goldenPath/hg38/bigZips/analysisSet/
- 来源于：ftp://ftp.ncbi.nlm.nih.gov/genbank/genomes/Eukaryotes/vertebrates_mammals/Homo_sapiens/GRCh38/seqs_for_alignment_pipelines/GCA_000001405.15_GRCh38_full_plus_hs38d1_analysis_set.fna
- 含有：
- Primary Assembly
- 屏蔽的PAR 序列，中心粒序列
- decoy
- alt


### BroadInstitute 的 reference genome

- 也用于 1000Genomes 的 pipelines
- 下载地址：ftp://ftp.broadinstitute.org/bundle/hg38/hg38bundle/
- 原始来源：http://sourceforge.net/projects/bio-bwa/files/bwakit/bwakit-0.7.12_x64-linux.tar.bz2/download
- primary assembly
- alt
- decoy genome
- HLA（和上面一个比唯一不同）


## 用哪个

- 可以就用新的
- GRCh38+ALT 可能导致很多质量值为0的mapping，bwa-mem可以解决这个问题
- HLA typing
- decoy可以使比对速度更快
- 可以进行 re-align

## 查看参考基因组有的成分

````
cat GRCh38.fasta | grep chrUn* > chrUn.txt
cat GRCh38.fasta | grep chr*random > random.txt
cat GRCh38.fasta | grep *decoy > decoy.txt
cat GRCh38.fasta | grep hla* > hla.txt
``````
## 参考资料

[The decoy genome](http://www.cureffi.org/2013/02/01/the-decoy-genome/)
[Reference Genome Components](http://gatkforums.broadinstitute.org/gatk/discussion/7857/components-of-reference-genomes)
