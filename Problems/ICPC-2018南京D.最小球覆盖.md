---
date: 2022-10-10
url: https://codeforces.com/gym/101981
tags: 
- 来源/ICPC
- 类型/杂项/三分
- 类型/计算几何/最小球覆盖
---

## 题意

给定n个点, 求最小球(半径)

## 思路

典型题,  每一个dis都是一个凸函数, n个dis和也是凸函数,
三分

## 代码

```cpp
double x[105], y[105], z[105],tp[3];
int n;
double pf(double x) {return	x * x;}
double dis(double a, double b, double c) {
	double r = 0;
	fp(i, 1, n) {
		r = max(r, pf(a - x[i]) + pf(b - y[i]) + pf(c - z[i]));
	}
	return r;
}
double cal(int ct) {
	if(ct == 3) return dis(tp[0], tp[1], tp[2]);
	double l = -1e5, r = 1e5;
	fp(i, 1, 80) {
		double dt = (r - l) / 3;
		double pl = l + dt, pr = r - dt, fl, fr;
		tp[ct] = pl, fl = cal(ct + 1);
		tp[ct] = pr, fr = cal(ct + 1);
		if(fl < fr) r = pr;
		else l = pl;
	}
	return cal(ct + 1);
}
```


- [x] ICPC-2018南京D #todo ✅ 2022-10-11
( 是个好题目的话, 记得提炼好放sm里哦 )