---
layout: post
title:  "sort and remove duplicate"
date:   2016-08-07
desc: "排序并去除PCR重复"
keywords: "WGS,WES,Samtools.bam,Picard"
categories: [NGS]
tags: [sequeincing]
icon: icon-microscope
---

sam文件需要转换成二进制bam文件后才能进行后续分析。使用picard-tools

### sort

	> java -Xmx30g -jar $picard/AddOrReplaceReadGroups.jar I=samp.sam O=samp.sorted.bam SORT_ORDER=coordinate CREATE_INDEX=true RGID=samp RGLB="pe" RGPU="Hiseq" RGSM=samp RGCN="researchname" RGDS=hg19 RGPL=illumina VALIDATION_STRINGENCY=SILENT
	
	AddOrReplaceReadGroups是增加文件头的，但它提供的参数能做到sort to bam

### Remove duplicate

	> java -Xmx30g -jar $picard/MarkDuplicates.jar CREATE_INDEX=true REMOVE_DUPLICATES=true ASSUME_SORTED=true VALIDATION_STRINGENCY=LENIENT I=samp.sorted.bam OUTPUT=samp.dedupbam METRICS_FILE=samp.metrics







