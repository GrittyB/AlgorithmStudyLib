---
date: 2022-10-09
url: https://ac.nowcoder.com/acm/problem/216006
tags: 
- 来源/ICPC
- 类型/杂项/三分
---


## 题意 

你每做一个烟花要n分钟，释放已做好的所有烟花需要m分钟，每只烟花成功释放的概率为p。问你在采取**最优策略**的前提下，直到成功释放第一个烟花时最小的期望时间花费



## 思路

假设每k个烟花点燃一次，则每次成功的概率是$P = 1-(1-p)^k$

如果第一次未发现烟花, 则第二次点燃, 第二次未发现, 则第三次点燃..

这是个伯努利实验, 实验次数的概率分布服从几何分布

其实验次数的期望$E(X) = 1 /P$

其时间的期望$E(Y) = (nk+m) /P$

求导后, 发现是凸函数,
三分求最值

## 代码
```cpp
double n, m, p;
double cal(ll k) {
	return (m + n * k) / (1 - pow(1 - p, k));
}
void sov() {
	cin >> n >> m >> p;
	p /= 10000;
	ll l = 1, r = 1e9;
	double ans = 1e18;
	while(l + 1 < r) {
		ll mid = (l + r) / 2;
		double fl = cal(mid - 1), fr = cal(mid + 1);
		if(fl > fr)  l = mid, ans = min(ans, fl);
		else r = mid, ans = min(ans, fr); 
	}
	ans = min({ans, cal(l), cal(r)});
	printf("%.8lf\n", ans);
}

```

- [x] ICPC-2020南京Fireworks #todo ✅ 2022-10-10
( 是个好题目的话, 记得提炼好放sm里哦 )