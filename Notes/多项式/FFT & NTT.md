## 概述


## 算法流程
(迭代过程)
1. 先蝴蝶变换, 每个数的二进制翻转求出
2. 从len = 2 的区间开始合并, 直到合并n个
	每一块, \[0,mid) 的部分 +  , \[mid,len) -
$$ \begin{aligned}
①A\left(\omega_{n}^{k}\right) &=B\left(\omega_{n / 2}^{k}\right)+\omega_{n}^{k} C\left(\omega_{n / 2}^{k}\right) \\
②A\left(\omega_{n}^{k+n / 2}\right) &=B\left(\omega_{n / 2}^{k}\right)-\omega_{n}^{k} C\left(\omega_{n / 2}^{k}\right) \\
蝴蝶变换后,B(x)&是A(x)的左部, C(x)是A(x)的右部 
\end{aligned}

$$

## 子问题
