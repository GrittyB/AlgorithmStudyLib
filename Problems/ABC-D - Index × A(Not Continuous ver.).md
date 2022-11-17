---
date: 2022-09-06
url: 
tags: 
- 来源/ABC
- 类型/DP/背包DP
---


## 题意


给定一个长度为n的数组，求一个长度为m的不连续的数组b，使得 $\sum_{i=1}^{m}b[i]*i$最大。

$n <= 2000$
## 思路

$f_{i,j}$表示考虑第 i 个物品, 并且恰好选了 j个 物品的最大价值
对于每个物品, 考虑选和不选

$f_{i,j} = max(f_{i -1,j}, f{i -1,j - 1} + a[i] * j)$

初始化 $f_{i,0} = 0$ 其他 -INF


## 代码
```cpp
memset(f, -0x3f, sizeof f);
	f[0] = 0;	
	fp(i, 1, n) {
		fd(j, min(i,m), 1) {
			f[j] = max(f[j], f[j - 1] + j * a[i]);
		}
	}
	cout << f[m];
```

- [x] D - Index × A(Not Continuous ver.) #todo ✅ 2022-09-06
( 是个好题目的话, 记得提炼好放sm里哦 )