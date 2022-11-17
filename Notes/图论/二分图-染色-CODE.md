dfs:
```cpp
int n,m;
vector<int>e[N];//存图
int col[N];//染色
int ok=1;//判断是否合法

void dfs(int u) {
	for(auto v:e[u]) {
		if(col[v] == -1) {
			col[v] = col[u]^1;
			dfs(v);
		} else if(col[v] == col[u]) {
			ok = 0;
			return ;
		}
	}
}

void sov(){
	cin>>n>>m;
	FOR(i,1,n)e[i].clear(),col[i]=-1; ok=1;  // 初始化
	FOR(i,1,m){
		int u,v;cin>>u>>v;
		e[u].pb(v);e[v].pb(u);
	}
	FOR(i,1,n){
		if(col[i]==-1) col[i]=1,dfs(i);
	}
	if(ok)puts("Yes");
	else puts("No");
}
```

bfs:
```cpp
void bfs(int u){
	queue<int>q; 
	q.push(u);
	while(!q.empty()){
		auto t=q.front(); 
		q.pop();
		for(auto v:e[t]){
			if(col[v]==-1){
				col[v]=col[t]^1; 
				q.push(v);
			}else if(col[v]==col[t]){ ok=0; return; }
		}
	}
}
