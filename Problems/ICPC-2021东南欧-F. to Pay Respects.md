---
date: 2022-09-13
url: https://codeforces.com/gym/103438/problem/F
tags: 
- 来源/ICPC
- 类型/trick
---


## 题意

打BOSS, BOSS可以使用回血效果, 你可以用毒药效果
效果可以叠加

每轮操作顺序:
1. Boss 选择是否使用回血效果
2. 你选择是使用毒药效果
3. 你进行一次普通攻击, 造成X点伤害
4. 所有效果应用

使用毒药后, 可以产生两种效果, 1. Boss 中毒效果 +1 2. Boss回血效果-1 (如果有)

效果每轮后, 产生Boss血量的变化:  X +P * p - R * r 
P是毒药效果, p是毒药叠加数, R是回血效果, r是回血效果叠加数

给定Boss每轮的回血效果使用情况, 你可以用K次毒药

问如何使得, 你给Boss造成的伤害最大

## 思路

每个位置 i 造成的 两种效果, 是固定的 
而 P效果 R效果 两者可以一起看
那我们就对每个pos应用P效果后产生的效果,排序, 选最大的k个即可


## 代码

```cpp
int main(int argc, char const *argv[])
{	
	init_code();
	ll n, x, r, p, k;
	cin >> n >> x >> r >> p >> k;
	string s;
	cin >> s;
	vector<ll> v;
	ll ans = n * x; 
	fp(i, 0, n - 1) {
		if(s[i] == '1') {
			ans -= (n - i) * r;
			v.pb( (n - i) * ( r + p ) );
		} else {
			v.pb( (n - i) * p );
		}
	}
	sort(v.begin(), v.end(), greater<ll>());
	fp(i, 0, k - 1) {
		ans += v[i];
	}
	cout << ans;
	return 0;
}
```
- [x] ICPC-2021东南欧-F. to Pay Respects #todo ✅ 2022-09-13
( 是个好题目的话, 记得提炼好放sm里哦 )