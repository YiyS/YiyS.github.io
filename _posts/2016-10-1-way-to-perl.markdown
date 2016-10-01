---
layout: post
title:  "A way to perl"
date:   2016-10-1
desc: "Hello, perl!"
keywords: "perl"
categories: [Perl]
tags: [perl]
icon: icon-perl
---


Hello, perl! 

## 基础

- 版本查询

```
perl -v
````

- 帮助文档

`````
# ubuntu 下似乎需要另外安装
sudo apt-get install perl-doc
perldoc -q keywords
```````

## 标量

- 不需要预先声明，创建时标记$直接使用，默认为初始值，数字为0，字符串为“”即空字符串
- print 函数，“”的变量内插，使用的是变量的真实值，要使用变量名需要在变量前加\

`````
$name="John";
print "I went to store with \$name\n";
print "I went to store with $name\n";
```````

## 运算符

### 引号运算符

- q()为单引号
- qq()为双引号
- qx()为反引号
- 可当对应的引号使用
- 使用print时还是要用回""等等的

```
$a=10;
$b=q{a=$a};
$c=qq{a=$a};
$d=qx{date};
print "$a\n";
print "$b\n";
print "$c\n";
print "$d\n";
```````

### 算术运算符

- 即加减乘除等
- %为求余
- **为乘幂

```````
$a=10;
$b=20;
$c=$a+$b;
print '$a+$b='.$c."\n";
`````````

### 比较运算符（数值）

- 使用=，!=，>，>=等等
- 特殊的一个为 <=>，当左边数小于右边返回1，小于则返回-1，相等则返回0
- 其他运算符返回的是 trur，或者 false

`````
$c=$a<=>$b;
if($a==$b){
  print "true\n";
}else{
  print "false\n";
}
print "$c\n";
`````

### 比较运算符（字符串）

- lt 检查左边字符串是否**小于**右边
- gt 检查左边字符串是否**大于**右边
- le 检查左边字符串是否**小于等于**右边
- ge 检查左边字符串是否**大于等于**右边
- eq 检查左边字符串是否**等于**右边
- ne 检查左边字符串是否**不等于**右边
- cmp 左边字符串小于右边返回-1，大于返回1，等于返回0

### 逻辑运算符

- 主要有下面几个
- and 或 && 
- or 或 ||
- not

````
$a=true;
$b=false;
$c=($a and $b);
print "$c\n";
`````

### 赋值运算符

- 如=，+=，-=等等
- 由几个算术运算符加上=组成 
- 把右边数，加，减，乘除，乘幂左边数后，赋值给右边数

```````
$a=10;
$b+=$a;
print "$c\n";
`````````

### 位运算符

### 其他
- .如前面所示，用于连接两个字符串，如 print '$a+$b='.$c."\n";
- x重复，('-'x3)为重复三次
- ..范围运算，(2..5)为（2,3,4,5）
- ++为自增加1，--为自减1
- ->指定一个类

## 参考资料

[perl 运算符](http://www.runoob.com/perl/perl-operators.html)
