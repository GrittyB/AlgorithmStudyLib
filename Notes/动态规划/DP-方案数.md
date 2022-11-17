## 概述
这里的最优方案是指物品总价值最大的方案。以01背包为例

g_i,v 体积恰好 = j 的方案

```cpp
// g0,0 = 1
for i=1..N
   for v=0..V
        f[v]=max{f[i-1][v],f[i-1][v-c[i]]+w[i]}
        g[i][v]=0
        if(f[i][v]==f[i-1][v])
            inc(g[i][v],g[i-1][v])
        if(f[i][v]==f[i-1][v-c[i]]+w[i])
            inc(g[i][v],g[i-1][v-c[i]])
```

