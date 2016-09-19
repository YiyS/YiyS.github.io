---
layout: post
title:  "variant calling with GATK"
date:   2016-08-07
desc: "GATK使用"
keywords: "GATK,WGS,WES"
categories: [NGS]
tags: [sequencing]
icon: icon-microscope
---

GATK的使用主要分几个步骤，Local realignment, Base quality score recalibration, Variant calling, Variant quality score recalibration, Filtering

### Local realignment

#### Create realign target

	> java -Xmx30g -jar $gatk -R hg19.fasta -T RealignerTargetCreator -I samp.dedup.bam -o samp.intervals -known 1000G_phase1.indels.hg19.sites.vcf
	> #这一步需要fai,和dict文件，可分别通过samtools和picard tools获得
	> samtools faidx hg19.fasta
	> jar -Xmx2g -jar $picard/CreateSequenceDictionary.jar R=hg19.fasta O=hg19.dict

#### Indel Realigner

	> java -Xmx30g -jar $gatk -R hg19.fasta -T IndelRealigner -I samp.dedup.bam -targetIntervals samp.intervals -o samp.realign.bam
	
### Base quality score recalibration
	> java -Xmx30g -jar $gatk -R hg19.fasta --disable_indel_quals -T BaseRecalibrator -rf BadCigar -knownSites dbsnp_138.hg19.vcf -knownSites Mills_and_1000G_gold_standard.indels.hg19.sites.vcf -knownSites 1000G_phase1.indels.hg19.sites.vcf -I sampe.realigned.bam -o samp.recal_data.grp 
	> java -Xmx30g -jar $gatk -R hg19.fasta -T PrintReads -rf BadCigar -BQSR samp.recal_data.grp -I samp.realigned.bam -o samp.recal.bam --allow_potentially_misencoded_quality_scores 
	> #这里的参考文件Mills，可能出出现错误提示Input files knownSites2 and reference have incompatible contigs.对此应该是要在GATK resource bundle 里下载hg19.fasta, hg19.dict, hg19.fai等文件。

### Variant calling

#### 使用UnifiedGenotyper

	> java -Xmx30g -jar $gatk -T UnifiedGenotyper -R hg19.fasta -I samp.realign.bam -o samp.gatk.UG.vcf -stand_call_conf 30.0 -stand_emit_conf 0 -glm BOTH -rf BadCigar


### Variant recalibration

-----------------------------------
在使用GATK过程中，可能出现错误提示，Quality Scores encoded出错，使用--fixMisencodedQuals即可





