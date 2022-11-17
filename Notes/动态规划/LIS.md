原$O(n^2)$:
	$d p_{i}=\max _{j<i, a_{j}<a_{i}} d p_{j}+1$  
$O(nlogn)$: 
	维护 当前的最长len , 以及$dp_i$ , 长度为i 的序列的 **最后一个**元素的 **最小值** :
	1. if 新元素 a > dp数组的最后一个元素, dp\[++len] = a
	2. else 找到第一个大于等于 a 的运算dpj, 令dpj = a
