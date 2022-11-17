---
date: 2022-09-01
url: http://acm.hdu.edu.cn/showproblem.php?pid=7227
tags: 
- 来源/杭电多校
- 类型/DP/树形DP
---


## 题意

给定一颗树，给你选择一些点，使得这些点，最多只有两个点直接有边相连。
问最多可以选多少点 

## 思路
树形DP

将一棵树的**父节点的存在 and 存在的deg**情况抽象成状态

-----

状态表示:$f_{i, 0 / 1 / 2}$ 分别表示 {不选i, 选了且deg是0 , 选了且deg是1} 的 i 子树
状态转移:
$$
\begin{array}{l}
f_{u, 0} \leftarrow \sum_{v \in \mathrm{ch}_{u}} \max \left(f_{v, 0}, f_{v, 1}, f_{v, 2}\right) \\
f_{u, 1} \leftarrow 1+\sum_{v \in \operatorname{ch}_{u}} f_{v, 0} \\
f_{u, 2} \leftarrow 1+\max _{v^{\prime}}\left\{f_{v^{\prime}, 1}+\sum_{v \in \operatorname{ch}_{u, v \neq v^{\prime}}} f_{v, 0}\right\}
\end{array}$$
解释:
当前点不选, 子树可以随便选
当前选, 且deg是0, 子树只能不选
当前选, 且deg是1, 只能选一个子树相连, 其他都不能选
## 代码
```cpp
vector<int>e[N];//存图

int f[N][3];
void dfs(int u, int fa) {
	ll s0 = 0, s1 = 0, s2 = 0;
	for(auto v:e[u]) {
		if(v == fa) continue;
		dfs(v, u);
		s0 += max({f[v][0], f[v][1], f[v][2]});
		s1 += f[v][0];
	}
	f[u][0] = s0;
	f[u][1] = 1 + s1;
	for(auto v:e[u]) {
		if(v == fa) continue;
		s2 = max(s2, f[v][1] - f[v][0] + s1);
	}
	f[u][2] = 1 + s2;
}


int main(int argc, char const *argv[])
{	
	int size(512 << 20); // 512M
    __asm__ ( "movq %0, %%rsp\n"::"r"((char*)malloc(size)+size));
    int t, n;
    scanf("%d", &t);
    while(t--)
    {
        scanf("%d", &n);
        for (int i = 1, u, v; i < n;i++)
        {
            scanf("%d%d", &u, &v);
      		e[u].pb(v); e[v].pb(u);
        }
        dfs(1, 1);
        printf("%d\n", max({f[1][0], f[1][1], f[1][2]}));
        fp(i, 1, n) {
        	e[i].clear();
        }
    }
    exit(0);

	return 0;
}
```

- [x] HDU-H Orgrimmar #todo ✅ 2022-09-01
( 是个好题目的话, 记得提炼好放sm里哦 )