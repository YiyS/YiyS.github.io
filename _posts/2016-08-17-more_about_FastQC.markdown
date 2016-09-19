---
layout: post
title:  "more ablout FastQC"
date:   2016-08-17
desc: "FastQC结果解读"
keywords: "FastQC,WGS,WES,RNA-seq"
categories: [NGS]
tags: [sequencing]
icon: icon-microscope
---

为什么FastQC得到的图，WGS和WES那么好看，RNA-seq那么丑？

### per base sequece content

* 这里一般WGS和WES是可以达到平行的4条直线的，然而RNA-seq前约13个碱基波动会很大，原因，primer not random，个人认为，这段不需要trimming

### k-mer
	
* 同上，前几个碱基出现kmer数量很多，如下图，也可以忽略

#### 以下为filter前后的per base sequence content 和 kmer图

![plot all](http://github.com/YiyS/YiyS.github.io/raw/master/_images/FastQC1.JPG)
![plot chromosome](http://github.com/YiyS/YiyS.github.io/raw/master/_images/FastQC2.JPG)
![plot cnv](http://github.com/YiyS/YiyS.github.io/raw/master/_images/FastQC3.JPG)
![plot cnv](http://github.com/YiyS/YiyS.github.io/raw/master/_images/FastQC4.JPG)

* 可见并差别并不是很大

### duplicate level

* 这一项结果也不是很好，
![plot cnv](http://github.com/YiyS/YiyS.github.io/raw/master/_images/FastQC5.JPG)

* 这转录组中，这个问题不是问题,而在基因组中，还是要注意的。

----------

总而言之，别纠结，FastQC只是一个只是起到一个提示作用。


#### 参考资料

[FastQC: What tripped me up with my first RNA-Seq analysis](http://rustbeltscientist.tumblr.com/post/38282631404/fastqc-what-tripped-me-up-with-my-first-rna-seq)

[Question: Kmer Content in FastQC failed](https://www.biostars.org/p/172860/)

[Question: GC content and Kmer](https://www.biostars.org/p/160440/)




