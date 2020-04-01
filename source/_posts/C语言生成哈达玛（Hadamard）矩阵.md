---
title: C语言生成哈达玛（Hadamard）矩阵
date: 2020-03-19 11:12:30
categories: 
- 随笔
tags: 
- Hadamard
- C语言
---

# C语言生成哈达玛（Hadamard）矩阵
**Hadamard矩阵定义：**
&ensp;&ensp;&ensp;&ensp;哈达玛（Hadamard)矩阵是由+1和-1元素构成的且满足Hn * Hn’=nI（这里Hn’为Hn的转置，I为单位方阵）n阶方阵。

**生成：**
调用matlab函数hadamard(2)生成2阶哈达玛矩阵：
```
 hadamard(2)
	ans =
     	1     1
     	1    -1
```
在hadamard源码中可以看到
```
for i = 1:e
    H = [H  H
         H -H]; 
end
```
知道任意2^n^阶hadamard矩阵都是2^n-1^阶hadamard矩阵通过如上结构的叠加

所以生成2^n^阶hadamard矩阵的C语言实现如下：
```bash
int* GenerateHDM(int n)
{
	int i, j, k, N;
	int L = 1 << n;//边长
	int* Hadamard = (int*)malloc(L * L * sizeof(int));

	Hadamard[0] = 1;
	Hadamard[1] = 1;
	Hadamard[L] = 1;
	Hadamard[L + 1] = -1;

	for (k = 1; k <= n - 1; k++)
	{
		N = 1 << k;
		for (i = 0; i < N; i++)
		{
			for (j = 0; j < N; j++)
			{
				Hadamard[(N + i) * L + j] = Hadamard[i * L + j];
				Hadamard[i * L + N + j] = Hadamard[i * L + j];
				Hadamard[(N + i) * L + N + j] = -Hadamard[i * L + j];
			}
		}
	}

	return Hadamard;
}
```

调用GenerateHDM生成边长为8的hadamard矩阵结果如下
```bash
1     1     1     1     1     1     1     1
1    -1     1    -1     1    -1     1    -1
1     1    -1    -1     1     1    -1    -1
1    -1    -1     1     1    -1    -1     1
1     1     1     1    -1    -1    -1    -1
1    -1     1    -1    -1     1    -1     1
1     1    -1    -1    -1    -1     1     1
1    -1    -1     1    -1     1     1    -1
```
matlab调用结果：

```bash
1     1     1     1     1     1     1     1
1    -1     1    -1     1    -1     1    -1
1     1    -1    -1     1     1    -1    -1
1    -1    -1     1     1    -1    -1     1
1     1     1     1    -1    -1    -1    -1
1    -1     1    -1    -1     1    -1     1
1     1    -1    -1    -1    -1     1     1
1    -1    -1     1    -1     1     1    -1
```
**perfect !**


