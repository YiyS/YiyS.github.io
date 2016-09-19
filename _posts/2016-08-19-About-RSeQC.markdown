---
layout: post
title:  "About RSeQC"
date:   2016-08-21
desc: "RNA-seq质控软件RSeQC使用记录"
keywords: "RSeQC,RNA-seq"
categories: [NGS]
tags: [sequencing]
icon: icon-microscope
---

这里只使用了两个，geneBody_coverage.py和junction_saturation.py

### 安装

* 建议用pip install

* 记得添加环境变量

`````````````
	> export PATH=~/.local/bin:$PATH
`````````````
	
### geneBody_coverage.py

	> geneBody_coverage.py -r hg19.bed -i SRR4010869_tophat/accepted_hits.bam -o RSEQC-OUT
	> #主要是看5'-3'bias

![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/RSEQC1.JPG)

### junction_saturation.py

	> junction_saturation.py -r hg19.bed -i SRR4010869_tophat/accepted_hits.bam -o RSEQC-Junct-OUT
	> #看是否能进行alternative splice analyse

![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/RSEQC2.JPG)





