---
{"dg-publish":true,"permalink":"/obsidian////chapter-6-counting/","created":"2024-04-11T23:24:27.907+08:00","updated":"2024-09-08T15:25:05.510+08:00"}
---

# 1.计数的基础
### 求和法则
>完成两项任务分别需要$n_1$与$n_2$种方法；
>两项任务不能同时执行

### 乘法规则
>完成一个任务有$n_1$种方式，且在之后有$n_2$种方式完成第二个任务

### 减法法则
- 两个集合的容斥原理![Pasted image 20240412081535.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412081535.png)
- 一个任务可以通过$n_1$种方式进行，或者可以通过$n_2$种方式进行
#### 取反的应用举例
1. 题目![Pasted image 20240412081916.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412081916.png)
2. 解读：
	1. 题目要求的是交集，联想我们的<mark style="background: #ADCCFFA6;">容斥原理</mark>，我们需要的是并集；
	2. 因此，可以考虑先求并集，然后<mark style="background: #BBFABBA6;">取反</mark>（总的减去并集）
### <mark style="background: #FF5582A6;">除法法则</mark>
>定义：![Pasted image 20240412083548.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412083548.png)

#### 圆桌围坐的举例
1. 题目![Pasted image 20240412083617.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412083617.png)
### 树图
>每个分支表示不同可能的选择

# 2.鸽洞原理
定理：
1. ![Pasted image 20240412084254.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412084254.png)
2. ![Pasted image 20240412084321.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412084321.png)
<mark style="background: #BBFABBA6;">构造</mark>
1. 举例1![Pasted image 20240412090047.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412090047.png)
## 广义鸽洞原理
1. 内容![Pasted image 20240412084533.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412084533.png)
	证明：![Pasted image 20240412084545.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412084545.png)
2. 反向应用：![Pasted image 20240412084704.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412084704.png)
3. 更多应用：![Pasted image 20240412085402.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412085402.png)
## e.g. <mark style="background: #FF5582A6;">摔跤手的连续比赛</mark>
1. 题目：![Pasted image 20240412111314.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412111314.png)
2. 解答：![e2e979521f743342ae96b43173d4f24.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/e2e979521f743342ae96b43173d4f24.jpg)
# 3.<mark style="background: #FFB86CA6;">排列与组合</mark>
- 概念
	1. *permutation* 排列
	2. *r-permutation* <mark style="background: #ADCCFFA6;">r排列</mark>
	3. *combinations* 组合：无序选择的计数
- 定理
	1. $A_n^r$=$\frac{n!}{(n-r)!}$![Pasted image 20240412090842.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412090842.png)
	2. $C_n^r$= $\frac{n!}{r!(n-r)!}$=$C_n^{n-r}$
		![Pasted image 20240412091437.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412091437.png)
	3. 
## con. <mark style="background: #FFF3A3A6;">循环圆桌的r排列</mark>
- 描述：从$n$个人中选取$r$人围坐在圆桌上，求取排列个数
- 解答：$N$ = $\frac{A_n^r}{r}$ 
- <mark style="background: #BBFABBA6;">into</mark>:若左右邻居相同也被认为是相同的排列![Pasted image 20240412092520.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412092520.png)
## e.g.<mark style="background: #BBFABBA6;">委员会的人员选择</mark>
1. 题目![Pasted image 20240412114446.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412114446.png)
2. 在b)中，考虑用整体的减去局部的
	1. 设总体为N=$C_{16}^5$，且题目所求的情况为S1（同时存在男女性）
	2. U=S1+{都是男性}+{都是女性}
	3. 则S1 = N$-$$C_7^5$$-$$C_9^5$.

# 4.二项式系数和恒等式
## 二项式定理
1. 内容：$(x+y)^n$ = $\sum_{i=0}^{n}C_n^ix^{n-i}y^i$   
2. 推论：
	1. $\sum_{k=0}^{n}C_n^k$= $2^n$ =$(1+1)^n$
	2. $\sum_{k=0}^{n}(-1)^kC_n^k$ = 0 =$(1-1)^n$
## 帕斯卡恒等式
><mark style="background: #BBFABBA6;">Pascal's Identify</mark>
1. 内容：$C_{n+1}^k=C_n^k+C_n^{k-1}$ 
2. 证明：![Pasted image 20240416100214.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416100214.png)
3. <mark style="background: #BBFABBA6;">帕斯卡三角形</mark>
	1. 图例：![Pasted image 20240416100319.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416100319.png)

## 范德蒙德恒等式及其推论
><mark style="background: #BBFABBA6;">Vandermonde's Identify</mark>
1. <mark style="background: #FFF3A3A6;">内容</mark>：$C_{m+n}^r=\sum_{k=0}^rC_m^{r-k}C_n^k$
2. 证明：
	1. 左式为从$m+n$中选取$r$个元素的组合方法
	2. 这个选取的过程可以细化为，从$m$个元素中取$k$个
	3. 然后从$n$个元素中选取剩下的$r-k$个
	4. 令$k$从0遍历到$n$，并将结果累加即可
3. <mark style="background: #FFB86CA6;">推论</mark>：$C_{2n}^n=\sum_{k=0}^n{(C_n^k)}^2$ 
	令m=n=r即可
4. <mark style="background: #FFB86CA6;">定理</mark>：$C_{n+1}^{k+1}=\sum_{k=r}^nC_k^r$ 
	<mark style="background: #ADCCFFA6;">组合证明</mark>：![Pasted image 20240422190814.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422190814.png)
# 5.排列与组合的推广
## <mark style="background: #BBFABBA6;">可重复的排列</mark>
1. 从$n$个可选取的元素中选取$r$个元素，允许重复
2. $n^r$ 
## <mark style="background: #BBFABBA6;">可重复的组合</mark>
1. 形式：$n$个元素的集合中允许重复的$r$组合（不关注同一类的差异）
2. <mark style="background: #FFF3A3A6;">组合数</mark>：$C_{n+r-1}^r$
3. 解释：看做$n-1$个挡板将$r$个元素分隔
4. 举例：
	1. ❓&✅![Pasted image 20240416103157.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416103157.png)
	2. 求解给定<mark style="background: #FFB86CA6;">线性方程组解的个数</mark>![Pasted image 20240416103341.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416103341.png)
		1. 可以看作3种类型的甜点一共买了11份
		2. 如果要求$x_i$不小于某个数，考虑已经取了一定份之后再求解
## <mark style="background: #BBFABBA6;">具有不可区别的物体的集合的排列</mark>
1. 方法：将$n$个元素先进行全排列，然后除以重复个数的全排列
2. 定理：![Pasted image 20240416104102.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416104102.png)
## <mark style="background: #BBFABBA6;">球盒模型</mark>

### <mark style="background: #FFB86CA6;">组合数总览</mark>
![Pasted image 20240416110800.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416110800.png)
<mark style="background: #FFB86CA6;">当盒子不可分辨时，就考虑枚举</mark>
### 球可分辨，盒子不可分辨时的枚举
1. 关键：注意除以重复的盒子数的阶乘（盒子均相同）
2. 举例：![Pasted image 20240416200030.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416200030.png)
	1. ✅![84da79bb2362f0c6b227b69071192cf.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/84da79bb2362f0c6b227b69071192cf.jpg)

## 简单回顾
允许重复与否的排列与组合：![Pasted image 20240416103602.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416103602.png)

### 第二类斯特林数(补充)
>n个不同的数划分为m个集合的方案数，要求**不能为空集**
>写作S (n, m) 
1. 递推式的推导:![Pasted image 20240416110050.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416110050.png)
2. xx
3. 由第二类斯特林数的<mark style="background: #BBFABBA6;">应用推广</mark>
	1. <mark style="background: #FFF3A3A6;">允许盒子为空</mark>![Pasted image 20240416110348.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416110348.png)
	2. 球可区分且<mark style="background: #FFF3A3A6;">盒子可区分</mark>![Pasted image 20240416110414.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416110414.png)
	3. ![Pasted image 20240416110612.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240416110612.png)
# 6.生成排列和组合
