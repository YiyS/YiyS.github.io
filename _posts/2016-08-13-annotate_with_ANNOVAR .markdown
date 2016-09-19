---
layout: post
title:  "annotate with ANNOVAR"
date:   2016-08-12
desc: "变异位点注释"
keywords: "annovar,WGS,WES"
categories: [NGS]
tags: [sequencing]
icon: icon-microscope
---

ANNOVR下载即可，免安装，可对SNP和Indels进行注释。

### 格式转换

	> $annovar/convert2annovar.pl -format vcf4 samp.gatk.UG.filter.vcf >samp.annovar

### 注释

	> $annovar/annotate_variation.pl -buildver hg19 -geneanno -outfile samp.anno samp.annovar $annovar/humandb
	> #这一步会生成3个文件，anno.log, anno.variant_function, anno.exonic_variant_function
	> #存在一个Warning，A total of 356 sequences will be ignored due to lack of correct ORF annotation
	> #If a transcript maps to multiple locations as "coding transcripts", but some with complete ORF, some without complete ORF (that is, with premature stop codon), then the ones without complete ORF will be ignored
	> #anno.exonic_variant_function存在很多UNKNOWN，也是ORF问题
	> #If a transcript maps to multiple locations, all as "coding transcripts", but none has a complete ORF, then this transcript will not be used in exonic_variant_function annotation and the corresponding annotation will be marked as "UNKNOWN".







