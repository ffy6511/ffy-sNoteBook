---
{"dg-publish":true,"permalink":"/obsidian////chapter-5-introduction-and-recursion/","created":"2024-04-07T08:01:25.104+08:00","updated":"2024-09-08T15:25:05.511+08:00"}
---

# 1. 数学归纳法
## 1.1 基本思路
![Pasted image 20240407080400.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407080400.png)
- 不一定要求基础步骤是$p$(1)
- 技巧描述（<mark style="background: #ADCCFFA6;">归纳假设</mark>）
- 同样可以用于证明不等式
- 同样同样可以用于证明整除性问题![Pasted image 20240407080653.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407080653.png)
## 1.2 应用举例
### ①求和
![Pasted image 20240407081339.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407081339.png)
	实际的解题过程中，需要先设出 $p$($n$) 的<mark style="background: #FFF3A3A6;">命题</mark>叙述；
	根据<mark style="background: #FFF3A3A6;">实际</mark>的 $x$ 的<mark style="background: #FFF3A3A6;">定义域</mark>选择基础步骤；
### ②<mark style="background: #FFB86CA6;">整除性</mark>
![Pasted image 20240407082155.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407082155.png)
### ③证明<mark style="background: #BBFABBA6;">幂集的个数</mark>为 $2^n$
![Pasted image 20240407082738.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407082738.png)
	先设出$S$具有n个元素，以此来构造$T$ =$S$+$a$
### ④证明<mark style="background: #BBFABBA6;">摩尔根定律</mark>的推广形式
![Pasted image 20240407083039.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407083039.png)
	将$p$(n+1)看成两项的交集，然后利用基本的摩尔根定律$p$($2$)






## 1.3 创新型用法
### ①用三联骨牌覆盖棋盘
![Pasted image 20240407083942.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407083942.png)
![Pasted image 20240407083954.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407083954.png)
	最精彩的一步就是划分成4份后，先假设3份没有空缺的在中心有空缺

# 2.强归纳法与良序性
## 2.1 原理说明
> ![Pasted image 20240407084856.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407084856.png)


## 2.2 选择方式
- 需要用到前$k$个条件才能证明时，用强归纳法
## 2.3 举例
### ①算数基本定理的证明
![Pasted image 20240407085710.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407085710.png)
>将k+1分素数与合数两种情况进行讨论；
>特别是**k+1为合数时**将其分解为a,b之积，于是得以运用假设归纳的条件！
## 2.4 计算几何学的相关
## 2.5 利用良序性证明
- <mark style="background: #ADCCFFA6;">良序性公理</mark>
	任意一个非空的**非负整数**集合都有最小元素
- 证明举例
	![Pasted image 20240407091347.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407091347.png)
		找到**非空集合** --> 指出**最小元**
# 3. 递归定义与结构归纳法
## 3.1 递归定义的步骤
### ①**结构定义**
![Pasted image 20240407091705.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407091705.png)
#### 举例：
>①![Pasted image 20240407091819.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407091819.png)
>②字符串![Pasted image 20240409102103.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409102103.png)
>	步骤：since a∈$\sum*$ and b∈$\sum$，ab∈$\sum*$
>③字符串的长度![Pasted image 20240409102453.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409102453.png)
>④复合命题的合式公式![Pasted image 20240409103422.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409103422.png)
>⑤有根树
>⑥full二叉树![Pasted image 20240409104104.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409104104.png)
### ②**结构归纳法**
- 解释![Pasted image 20240409105611.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409105611.png)
- 举例
	- 满二叉树的高度$h$![Pasted image 20240409105810.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409105810.png)
		>只有根节点的高度为$0$
	- 满二叉树的节点个数$n$![Pasted image 20240409110046.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409110046.png)
	- 二叉树的顶点个数$n$与高度$h$的<mark style="background: #ADCCFFA6;">关系</mark>![Pasted image 20240409105930.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409105930.png)
		- 证明：![Pasted image 20240409110129.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409110129.png)![Pasted image 20240409110140.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409110140.png)
			结构归纳的归纳步骤与之前的归纳方法的<mark style="background: #FFB86CA6;">不同之处</mark>在于——并非从P(k)$\rightarrow$P(k+1)，而是从T1与T2出发，根据T=T1·T2,检验T的性质 

### ③**广义归纳法**
>用来证明具有良序性的集合的结果
#### $a_{m,n}$的举例
- 题目![Pasted image 20240409111049.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409111049.png)
- 思路![Pasted image 20240409111106.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409111106.png)
- 过程![Pasted image 20240409111116.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409111116.png)
	结构归纳的路径有两条，<mark style="background: #BBFABBA6;">分类讨论</mark>进行说明
### 归纳法小结
基础步骤 Basic Step
归纳步骤 Instuctive Step
## 3.2 精彩例题
### ① 斐波那契数列的性质（$f$为斐波那契数列）![Pasted image 20240407092120.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407092120.png)
>最精彩的部分可以说是利用$a$是 $x^2$-$x$-$1$=0的解，来将$a^2$进行代换

## 3.3 美妙的定理
### ①拉梅定理
- 内容：
>$a,b$为正整数，$a≥b$，则用欧几里得算法求解gcd(a,b)时使用除法的次数小于或等于$b$的十进制位数的5倍
- 证明：
>![Pasted image 20240409101333.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409101333.png)![Pasted image 20240409101341.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409101341.png)
# 4.递归算法
- 介绍

##  4.2 举例
- gcd(a,b)算法
## 4.3证明正确性
- 求幂的递归算法的正确性 $a^n$
	- 过程![Pasted image 20240409112356.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409112356.png)
## 4.4 递归与迭代 
- 利用斐波那契数列的计算次数进行比较
	- 递归
		- 代码![Pasted image 20240409112814.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409112814.png)
		- 次数：需要$f_{n+1}$-1次来计算得出$f_n$
	- 迭代
		- 代码![Pasted image 20240409112917.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409112917.png)
		- 次数：$n-1$
- 递归实现<mark style="background: #ADCCFFA6;">归并排序</mark>
	- 伪代码
		- ![Pasted image 20240409113453.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409113453.png)
		- ![Pasted image 20240409113503.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409113503.png)
	- 结论：
		- 不超过m+n-1次比较可以合并
# 验证程序的正确性