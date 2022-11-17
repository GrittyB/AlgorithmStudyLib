## 概念
子集dp的状态转移, 是由子集转移到当前集合
枚举子集的方法

	for (int i = s; i; i = (i - 1) &ｓ)


转移方程
```cpp
for(int i=0;i< 1<<n;i++)
{
	// S = i;
	for(int j=S&(S-1);j;S&(j-1)) 
	{
		dp[S]=max(dp[S],dp[S^j]+dp[j]);
	}
}
```

从小到大枚举集合S, 再枚举每个集合S的子集

枚举所有子集的子集
复杂度 $$\sum_{\mathrm{i}=0}^{\mathrm{n}}\left(\begin{array}{c}
\mathrm{n} \\
\mathrm{i}
\end{array}\right) 2^{\mathrm{i}}=3^{\mathrm{n}}$$
