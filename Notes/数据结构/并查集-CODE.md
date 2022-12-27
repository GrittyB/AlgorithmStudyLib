```cpp
int get(int x) {
	return fa[x] == x ? x : fa[x] = get(fa[x]);
}
void merge(int x, int y) {
	fa[get(x)] = get(y);
}
```

维护到祖宗节点的距离
```cpp
int get(int x) {
	if(fa[x] == x) return x;
	int rt = get(fa[x]);
	d[x] += d[rt];
	fa[x] = rt;
}
void merge(int x, int y) {
	x = get(x), y = get(y);
	if(x == y) return ;
	d[x] = size[y];
	size[y] += size[x];
	fa[x] = y;
}
```