---
{"dg-publish":true,"permalink":"/obsidian////chapter-10-graph/","created":"2024-05-30T23:17:10.134+08:00","updated":"2024-09-08T15:25:05.502+08:00"}
---

# 1.基本图概念
## ✨类型：
![Pasted image 20240531082755.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240531082755.png)
	特别注意，有向复杂图允许自环；
	`multigraph` 的意思应当具有重边（有向与无向需区分）
	`simple` ：没有两条边关联同一个顶点
🌰`directed multigraph`与`directed (simple) graph`的区分：
![Pasted image 20240531125016.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240531125016.png)
	7.为directed graph; 8.为directed multigraph
## 📝补充概念
- <mark style="background: #BBFABBA6;">pendant</mark> :deg(v) = 1, 则v is pendant
- <mark style="background: #BBFABBA6;">N(v)</mark> :the neighborhood of v（与v相邻/有边的的集合）
- <mark style="background: #FFF3A3A6;">自环</mark>（loop）的顶点计算deg时，该环的贡献为<mark style="background: #FFF3A3A6;">2</mark>
- `degree sequence`指的是在这个图中的顶点的度数的序列，要求按照<mark style="background: #FFF3A3A6;">非升序</mark>！（因此唯一）
## 👏简单定理
1. 无向图中，所有顶点的度数之和 = 2e（一定为偶数）
2. 无向图中，度数为奇数的顶点个数一定为偶数
3. 👍<mark style="background: #FFF3A3A6;">若</mark>G是至少有2个顶点的简单图，那么一定存在至少2个顶点具有相同的`degree`
	证明：假设有n个顶点，从三个角度进行讨论——
	1. 至少有2个顶点的度数为0；
	2. 恰好有1个顶点的度数为0，那么剩下n-1个顶点的度数分布在1,2...n-2，由<mark style="background: #BBFABBA6;">鸽洞原理</mark>~
	3. 若没有顶点的度数为0，则n个顶点的度数分布在1,2....n-1,同理 由鸽洞原理~
4. 有向图中，入度和出度之和均与边数相等
5. 求解图的子集的个数：
	1. $C_n^i$选取顶点个数i，（从1到n）
	2. 对于选定的顶点组合中存在的边数e,考虑是否引入边，所以乘上$2^e$ 
	3. 累加
## 实例化应用
- ***Precedence Graphs***
	- 有向图，v->w表示w表示的事件不能在v表示的事件之前发生![Pasted image 20240531125637.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240531125637.png)
	- 
# 2.特殊的图
## 简单补充：
![Pasted image 20240531091207.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240531091207.png)
- $Q_{n-1}$得到$Q_n$：拷贝前者，在两份的顶点标记前方分别添加`0`,`1`，然后分别对应连接
- $Q_n$中的n从0开始；$w_n$中的n是除了中心以外的顶点的个数，$w_3$是三角形（由环图得到）
## Bipartile Graphs
><mark style="background: #BBFABBA6;">二部图</mark>
- 含义：顶点可以分为两个不相交的子集，使得每条边都的顶点来自两个子集。同一个子集的顶点之间不存在边；
- 🌰：![Pasted image 20240531081724.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240531081724.png)
- <mark style="background: #FFF3A3A6;">判断定理</mark>：
	一个简单图是二部图 $\Leftrightarrow$  能够用**两种**颜色对每个顶点选择一种上色，且**没有**两个**相邻**的顶点被赋予**相同的颜色**；
		初始化：取任意一个顶点赋予任意一种颜色，由此扩展，直至能在满足条件的情况下完成所有的上色/矛盾

- <mark style="background: #BBFABBA6;">完全二部图</mark> $k_{m,n}$ 
	- 含义：两个子集分别有m,n个顶点，且每个顶点到对方子集的顶点均有边(有mxn条边)
	- 🌰:![Pasted image 20240531082449.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240531082449.png)
## Regular graph
>正则图
- 含义：简单图的所有顶点的**度数均相同**时，称为~
- 举例：
	- 完全图 $k_n$是(n-1)-regular
	- 圈图 $c_n$ 是2-regular
	- 对于完全二部图$k_{m,n}$，当m=n时为n-regular
## match
- 含义：
	- 匹配M是边集E的子集，且这些匹配关联的顶点均不相同；
	- 🌰如果{s,t},{u,v}是M中的不同边，那么一定有s,t,u,v均是不同的顶点
- 顶点的匹配：
	- 如果顶点v在M中，则称其 **被匹配**；否则称为未被匹配
- <mark style="background: #BBFABBA6;">最大匹配</mark>：包含最多边数的一个匹配
- <mark style="background: #BBFABBA6;">完全匹配</mark>： 若二部图中的一个匹配M，使得其中的一个顶点子集的顶点都在M中被匹配，则称其为~
	- ✨判断完全匹配是否存在的定理——***Hall's Marriage Theorem***
		- 📝内容：
## 从旧图构造新图
- $G-e$ ：从G中删除边e, 子图具有与G相同的顶点集，边集是$E-\{e\}$ 
- $G+e$ : 在G中增加边e
- 边的收缩：删除边后将其2个顶点合并成一个新的顶点
- $G-v$： 删除顶点v与所有与其关联的边
- 并集
🌰在G上的4种操作：![Pasted image 20240531090918.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240531090918.png)
# 3.图的表达
