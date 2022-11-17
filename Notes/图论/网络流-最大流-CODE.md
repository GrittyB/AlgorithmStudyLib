Dinic
```cpp
int n, m;
ll adj[510][510], oadj[510][510];

ll flow[510];

bool V[510];
int pn[510];

bool reachable() {
    memset(V, false, sizeof (V));
    queue<int> Q; Q.push(1); V[1] = 1;
    while(!Q.empty()) {
        int u = Q.front(); Q.pop();
        fp(v, 1, n) if(adj[u][v] && !V[v]) { // 没走过, 还能走
            V[v] = 1, pn[v] = u, Q.push(v);
        }
    }
    return V[n];
}

int main(int argc, char const *argv[])
{
    init_code();
    cin >> n >> m;
    fp(i, 1, m) {
        int u, v, c;
        cin >> u >> v >> c;
        adj[u][v] += c;
    }
    int u, v;
    ll maxflow = 0;
    while(reachable()) { // bfs, 处理出来层次图, 与增广路
        ll flow = 1e18;
        for(v = n; v != 1; v = pn[v]) { // 随便一条增广路, 找bottleneck
            u = pn[v];
            flow = min(flow, adj[u][v]);
        }
        maxflow += flow;  // 进行增广, cap更新
        for(v = n; v != 1; v = pn[v]) {
            u = pn[v];
            adj[u][v] -= flow;
            adj[v][u] += flow;
        }
    }
    cout << maxflow;
    return 0;
}
```