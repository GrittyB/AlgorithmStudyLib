
一.
算法流程 :
AB两点的LCA
- AB先jump到同样深度
	- if(a == b) return a ; else 执行下面
- 跳的高度从大到小 , 跳后两者不等, 则跳


对于步骤2解释:
- 跳的高度从大到小: 比如要跳 (1010)2  , 先跳1000, 再跳10
- 两者相等, 即多跳了,  iff.  跳的二进制的1不在 需要的二进制中 ,  反之, 不等则可跳


