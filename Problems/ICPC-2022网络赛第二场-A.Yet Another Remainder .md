---
date: 2022-12-20
url: 
tags: 
- 来源/ICPC
- 类型/Trick/数论
---


## 题意
( 简化

给定一个大数 

? 大数%p ( p not 2 or 5 , p < 100


## 思路

%p的数的 和式形式(类似):
$\sum\limits a_{i}10^{i} \quad \% p$
由于 p!= 2, 5, $10^{p-1}≡1 \quad (mod p)$
所以 $10^i$ 每隔 p - 1 一次循环, 按照 i 的 % p 余数 \[0, 1, .. p - 2 ] 分组,
知道每组的和, 就知道最后的数

## 代码


- [x] ICPC-2022网络赛第二场-A.Yet Another Remainder #todo ✅ 2022-12-20
( 是个好题目的话, 记得提炼好放sm里哦 )