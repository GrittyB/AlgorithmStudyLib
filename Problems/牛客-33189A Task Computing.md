---
date: 2022-09-02
url: https://ac.nowcoder.com/acm/contest/33189/A
tags: 
- 来源/牛客多校
- 类型/贪心/邻项交换,推导贪心策略
---


## 题意

$$n \text { 个无序数对 }\{w_i, p_i\} \text {, 从中选 } m \text { 个, 使得 } \sum_{1}^{m} w_i \prod_{1}^{i-1} p_j \text { 最大 }$$


## 思路

对于已选的m个数 , 考虑第 i , i+1 个
假设交换前最优,
这两者的影响是 $s(w_{i}+ p_{i}w_{i+1})$
交换后的影响是$s(w_{i+1}+p_{i}w_{i})$
要交换前更优, 按照 $w_{i}+ p_{i}w_{i+1}>w_{i+1}+p_{i}w_{i}$排序即可
然后在顺序dp
## 代码


- [ ] 牛客33189 Task Computing #todo 
( 是个好题目的话, 记得提炼好放sm里哦 )