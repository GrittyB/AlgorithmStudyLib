```cpp
int len = 0;
void dfs(int u, int fa) {
	path[++len] = u; 
	pos[u][0] = len;
	for(auto v : e[u]) { 
		if(v != fa) {
			dfs(v, u);
		}
	}
	path[++len] = u;
	pos[u][1] = len;
} 
```