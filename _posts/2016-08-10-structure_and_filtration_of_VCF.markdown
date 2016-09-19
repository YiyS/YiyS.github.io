---
layout: post
title:  "structure and filtration of VCF"
date:   2016-08-12
desc: "VCF格式"
keywords: "vcf format,WES,WGS"
categories: [NGS]
tags: [sequencingl]
icon: icon-microscope
---

使用GATK UnifiedGenotyper，当glm BOTH时得到的VCF文件包含了SNP和Indel突变信息。可以通过perl命令筛选出这两种突变。

### VCF结构
- CHROM: 参考序列名，一般为chr1, chr2等等
- POS: variant的位置
- ID: 改SNP在dbSNP中的id，若没有，用'.'表示
- REF: 参考序列的碱基
- ALT: Variant的碱基
- QUAL: Phred格式的质量值,此数值越高，该位点存在variant的可能性越大Phred=-10log(1-p)，p为存在variant的概率
- FILTER: 除了QUAL， GATK使用了其他方法进行过滤，该项为'PASS'则通过了过滤

- INFO: 

AC: 该Allele数目

AF: Allele频率

AN: Allele总数目

DP: reads覆盖度

FS: 使用Fish's精确检验得到的Phred格式的p值，越小越好

HaplotypeScore: Consistency of the site with at most two segregating haplotypes

MLEAC: Maximum likelihood expectation (MLE) for the allele counts 

MLEAF: Maximum likelihood expectation (MLE) for the allele frequency
 
MQ: RMS Mapping Quality

MQ0: Total Mapping Quality Zero Reads

MQRankSum：Z-score From Wilcoxon rank sum test of Alt vs. Ref read mapping qualities

Dels: Dels=0.00则此Variant为SNP

- FORMAT: GT(Genotype):AD(Allele Depth):DP(Depth):GQ(GenotypeQuality):PL(三种基因型的质量值）
- samp: 与FORMAT构成基因型信息

### VCF过滤

#### 采用VQSR
- 当样品量足够大的外显子或，为全基因组测序时使用

#### 根据QUAL和测序深度筛选

	> #采用QUAL大于20，测序深度大于10的标准
	> perl -alne '{next if $F[5]<20;/DP=(\d+)/;next if $1<10;print}' 00.gatk.UG.vcf  >00.gatk.UG.vcf.filtered
	> #筛选出SNP
	> perl -wne '{if(/Dels/){print}}' 00.gatk.UG.vcf.filtered > 00.gatk.UG.snp.vcf
	> #筛选出indel
	> perl -wne '{unless(/Dels/){print}}' 00.gatk.UG.vcf.filtered > 00.gatk.UG.indel.vcf







