## 概述

Binary Jumping, 即国内的树上倍增
描述 :  x 节点 高k级 的节点是?
k 按照 二进制分解后的数 去跳
```c++
int jump(int x,int d) {
	for(int i = 0; i <= 20; i++) 
		if(d >> i & 1) x = up[x][i];
	return x; // x 是 0 的话, 就说明多跳了, 没有找到
}
```

## 子问题
[[Binary Jumping - LCA]]



## CODE
[[Binary Jumping - LCA - CODE]]