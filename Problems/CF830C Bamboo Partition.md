---
date: 2022-09-02
url: https://www.luogu.com.cn/problem/CF830C
tags: 
- 来源/CF
- 类型/数论/数论分块
---


## 题意

$$\text { 给定 } n \text { 个数 } a_{1} \sim a_{n} \text { ，求最大的 } d \text { ，满足 } \sum_{i=1}^{n} d-\left(\left(a_{i}-1\right) \% d+1\right) \leq k \text {. } $$

$$ 1<=n<=100 , 1<=k<=10^{11} , 1<=a_i<=109$$

## 思路

取模转换成整除形式 ==> 得到整除求和, 可以分块枚举

化简$$\begin{eqnarray}
\sum_{i  =  1}^{n} d-\left(\left(a_{i}-1\right) \% d+1\right) &\leq &k \\
得 \sum_{i  =  1}^{n} d- ( (a_{i}-1)- \lfloor \frac{(a_{i}-1)}{d} \rfloor d    +1) &\leq& k ①\\ 
得  \sum_{i  =  1}^{n} d ( 1 +  \lfloor\frac{(a_{i}-1)}{d}\rfloor ) &\leq k &+  \sum_{i  =  1}^{n} a_{i}②
\\得 d\sum_{i  =  1}^{n}  ( 1 +  \lfloor\frac{(a_{i}-1)}{d}\rfloor )& \leq k &+  \sum_{i  =  1}^{n} a_i③
\end{eqnarray}$$
*tip : 在②->③把d 提出来, 是当我在分块枚举 整除部分的时候, 整除部分是相同的, 但是d是不同的 ,  所以外面的d提出来, 然后, 通过不等式, 确定d的令一个范围*

然后, 枚举每块整除相同部分的 d的范围\[l , r] , 再通过不等式, 确定第二个范围, 取交集

*tip : 分块时候枚举的d 不会超过 max_element of ai , 所以, 最后要判断 d 能否取更大, 也就是分块值 为0 的情况*

## 代码
![[Pasted image 20220902120450.png]]

- [x] CF830C Bamboo Partition #todo ✅ 2022-09-02
( 是个好题目的话, 记得提炼好放sm里哦 )