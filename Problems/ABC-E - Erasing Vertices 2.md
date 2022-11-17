---
date: 2022-09-04
url: https://atcoder.jp/contests/abc267/tasks/abc267_e
tags: 
- 来源/ABC
- 类型/贪心
---


## 题意

给定一个无向图带有n个点m条边，每个点都有权值。每次要删除一条边，一次删除的代价是从这个点直接相邻的点的权值和，使n次删除操作后的最大值最小，求其最小值。

## 思路

发现删除一个点之后不会让其他节点删除变大。因此我们每次都删除代价最小的点即可。

用set去维护{ sum_id ,id } 每次删完后(用vis表示删过), 将周围的点更新

注意set重载问题, 要用const method , 且 两个参数都要写上排序, 不然会去重掉 

## 代码

```cpp
ll wt[N], a[N];
int n, m;
vector<int> e[N];
struct node {
	ll w, id;
	bool operator <(const node a) const {
		if(w == a.w) return id < a.id;
		return w < a.w;
	}
};
set<node>st;
bool vis[N];
int main(int argc, char const *argv[])
{	
	init_code();
	cin >> n >> m;
	fp(i, 1, n) {
		cin >> a[i];
	}
	fp(i, 1, m) {
		int u, v;
		cin >> u >> v;
		e[u].pb(v);
		e[v].pb(u);
	}
	fp(i, 1, n) {
		for(auto v: e[i]) {
			wt[i] += a[v];
		} st.insert({wt[i], i});
	}

	ll ans = 0;
	while(st.size()) {
		node now = *st.begin(); st.erase(st.begin());
		vis[now.id] = 1;
		ans = max(ans, (ll)now.w);
		for(auto v:e[now.id]) {
			if(vis[v]) continue;
			ll nwt = wt[v] - a[now.id];
			st.erase({wt[v],v});
			wt[v] = nwt; 
			st.insert({wt[v],v});
		}
	}
	cout << ans ;
	return 0;
}
```
- [x] E - Erasing Vertices 2 #todo ✅ 2022-09-04
( 是个好题目的话, 记得提炼好放sm里哦 )