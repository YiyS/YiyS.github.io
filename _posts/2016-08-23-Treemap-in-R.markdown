---
layout: post
title:  "Treemap in R"
date:   2016-08-23
desc: "用R语言绘制类似Excel中的矩形树状图"
keywords: "tree map,R"
categories: [R]
tags: [R]
icon: icon-microscope
---


`````````````
	> install.packages('treemap')
	> library(treemap)
	> test=data.frame(region=c("this region","this region",
	+ "other city in the province","other city in the province",
	+ "outside the province","outside the province"),
	+ sex=c("male","female",
	+ "male","female",
	+ "male","female"),
	+ population=c(20110,19685,46492,39592,119531,99370))
	> test
	> treemap(test,index=c("region","sex"),vSize="population",type="index",
	+ palette=brewer.pal(6,"Pastel2"),
	+ title="source of the polulation",
	+ border.col="white",border.lwd=4)
`````````````
![](http://github.com/YiyS/YiyS.github.io/raw/master/_images/POPUL1.JPG)
	






