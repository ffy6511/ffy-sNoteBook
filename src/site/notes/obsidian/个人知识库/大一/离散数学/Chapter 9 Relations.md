---
{"dg-publish":true,"permalink":"/obsidian////chapter-9-relations/","created":"2024-05-07T11:17:57.032+08:00","updated":"2024-09-08T15:25:05.518+08:00"}
---

# 1. 关系
## 二元关系
- 定义：从A到B的~是A X B的笛卡尔积的<mark style="background: #FFF3A3A6;">子集</mark>
- 表达：
	1. 有向图 graph
		起始顶点与终止顶点分别表示A与B的元素
	2. 2D-Table表示法
	3. 谓词 predicate
		1. x | y 即x可以整除y
	4. 枚举 list
	5. Connection Matrices
		使用一个`m x n`的矩阵，如果对应的$a_i与b_j$有关系，则$ij$位置为1
- <mark style="background: #FFF3A3A6;">个数</mark>
	- 考虑A,B之间的`relation`个数
	- 设各自有m,n个元素，则共有mxn个有序对
	- 对于关系，是笛卡尔积的子集
	- 因此，有$2^{m\  x\  n}$个关系
## 集合的关系
- <mark style="background: #ADCCFFA6;">集合A上的关系</mark> A binary relation R on A 
	- 定义：从A到A自身的关系
## 关系的性质
###  <mark style="background: #ADCCFFA6;">自反性</mark> *reflextive*
(a,a)$\in$R for every element a $\in$ A
如果A为空集，那么关系也是空集，也满足自反性
1. 有向图中每个顶点都有自环
2. 矩阵中主对角线均为1
- <mark style="background: #ADCCFFA6;">反自反性</mark> *antirelextive*
	1. 注意，自反性和反自反性并不“非此即彼”
	2. 空集，<mark style="background: #FFB86CA6;">既是自反的也是反自反的</mark>
	3. 有向图中不存在环
###  <mark style="background: #ADCCFFA6;">对称性</mark> *symmetric*
1. ( b,a) $\in$ R whenever (a,b) $\in$ R
2. 矩阵关于主对角线**对称**（方阵）
3. 有向图存在的边都是**双向**的
- <mark style="background: #ADCCFFA6;">反对称性</mark> *antisymmetric*
	1. if (a,b) $\in$ R and (b,a) $\in$ R, then a=b.
	2. 可以 假设(a,b) $\in$ R 且a,b,不相同，则 (b,a) $\notin$ R 满足~
	3. 在矩阵中，<mark style="background: #FFF3A3A6;">关于主对角线的</mark>(0,0)也满足反对称性，因为此时前提不满足，谓词公式一定是`True`；也就是说，只要不存在(1,1)就满足~
		1. 指的是关于主对角线对称的两个矩阵元素的1/0关系。
	4. 在有向图中，两个顶点之间**或不存在边**，或**只存在一条边**（可以存在自环）
- <mark style="background: #ADCCFFA6;">非对称性</mark> *asymmetric*
	$\forall x\forall y((x,y) \in R \rightarrow (y,x)\notin R$)   
<mark style="background: #BBFABBA6;">conclusion</mark>
1. 存在同时满足两种性质的关系
	1. 关于主对角线均为(0,0)即可
2. 也存在同时不满足两种性质的关系
###  <mark style="background: #ADCCFFA6;">传递性</mark> *transitive*
1. (a,b) $\in$ R and (b,c) $\in$ R, then (a,c) $\in$ R
2. 满足传递性，则![Pasted image 20240510092945.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240510092945.png)
## 由图表判断关系
### 有向图
1. 是否自环--自反
2. 是否双向边--对称
3. 若(a,b)且(b,c) 则观察是否存在a->c的边
	若前提不成立，则一定满足
### 矩阵

## 各种关系的数目(n元)
- 计算方法
	利用矩阵
- 图表：
![Pasted image 20240510091837.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240510091837.png)![Pasted image 20240510091913.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240510091913.png)
## 集合的结合运算
>省略 并交差的基本运算
### Compositiom 复合
- 计算：
	1. 关系矩阵作乘法:(<mark style="background: #FFB86CA6;">乘为与 加为或</mark>)
		e.g.![de338cbf6f4d2efc0ad9eba559615ef.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/de338cbf6f4d2efc0ad9eba559615ef.jpg)
			![Pasted image 20240514092822.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514092822.png)
	2. 利用定义
- 表示：$R_2 \circ R_1$ <mark style="background: #FFF3A3A6;">从右到左</mark>，先计算$R_1$ 
>其他基本运算也可以由关系矩阵得到：
>	并：有1为1
>	交：全1为1
>	差：(1,0)为1

### 自身的复合
1. 在$R$中的(x,y)之间如果存在一条$n$条边的路径，那么在$R^n$中存在一条直接从x到y的边：![Pasted image 20240514101015.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514101015.png)
	$R_4=R_1$
#### <mark style="background: #ADCCFFA6;">相关性质</mark>
1. The relationshp R on a set A is <mark style="background: #FFF3A3A6;">transitive</mark> $\Leftrightarrow$ $R^n\subseteq R$ 
	- proof:![Pasted image 20240514102831.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514102831.png)
2. 对称关系的幂 依旧满足对称关系
	1. 证明：![Pasted image 20240514103510.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514103510.png)
3. 
### Inverse 取反
![Pasted image 20240510093031.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240510093031.png)
### 集合运算的性质
：🌰![Pasted image 20240514104011.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514104011.png)
# 4.闭包
闭包关系的证明
>围绕特性：①包含关系R; ②具有性质P; <mark style="background: #FFF3A3A6;">③</mark>是具有这种性质的关系的**最小关系**
## 自反闭包 r(R)
- 推论：R满足自反关系 $\Leftrightarrow$ R=R $\cup\  I_A$  
- 📝：![Pasted image 20240514111443.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514111443.png)
- 操作：
	- 矩阵：主对角线全为1
	- 有向图：全部顶点均有自环
## 对称闭包 s(R)
- 关系③的证明📝:![Pasted image 20240514111359.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514111359.png)
- 推论：R满足对称关系$\Leftrightarrow$ R=R $\cup$ $R^ {-1}$ 
	- 📝![Pasted image 20240514112353.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514112353.png)
- 操作
	- 矩阵：关于主对角线有1补1
	- 有向图：存在边则补为双向边
## 传递闭包 t(R)
### <mark style="background: #ADCCFFA6;">相关定理</mark>
①存在从a到b且长度为n的路径 iff (a,b)$\in R^n$
	📝:![Pasted image 20240514113011.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514113011.png)

 ②$R^*$表示连通关系，t(R) = $R^*$  
	 📝：![Pasted image 20240514113713.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514113713.png)![Pasted image 20240517080707.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517080707.png)
---
下面的定理保证了我们<mark style="background: #FFF3A3A6;">最多</mark>只需要算到$R^n$即可：
- 👏顶点个数为$n$的关系，大于n长度的路径一定包含了一个环
- 可能以少于n的k次的乘积就得出结果
可以利用矩阵计算
---
④$R$满足传递关系 $\Leftrightarrow$ R=$t(R)$
### ⌨️<mark style="background: #BBFABBA6;">沃舍尔算法</mark>
-  用上述矩阵的暴力求解方法需要$O(N^4)$的时间复杂度
- 因此，需要引出一种简便的方法——***Warshall's Algorithm*** 来求解$t(R)$ 
---
相关概念
- <mark style="background: #ADCCFFA6;">内部点</mark> interior vertices
	- 路径去掉起点和终点的剩余顶点
	- 在环中，去掉一个起点即可
计算逻辑：
![Pasted image 20240517083221.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517083221.png)
🌰举例说明：
	![Pasted image 20240517084138.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517084138.png)
	1. 计算$w^{(k)}$时，先从$w^{(k-1)}$中将1照抄
	2. 然后观察第$k$<mark style="background: #FFB86CA6;">列</mark>，如果存在(i,k)为1，也就是存在从i到k的路径，则观察第k行是否有1，也就是是否存在从k到j的路径。比较原图，最后得出(i,j)的关系
## ✨不同闭包关系的联结
🌰![Pasted image 20240517085211.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517085211.png)
	注意，<mark style="background: #FFF3A3A6;">自反性</mark>存在时<mark style="background: #FFF3A3A6;">最后</mark>计算；<mark style="background: #FFB86CA6;">对称性</mark>存在时<mark style="background: #FFB86CA6;">优先</mark>计算
# 5. 等价关系
## 📝相关概念
- <mark style="background: #BBFABBA6;">等价关系</mark> R
	1. R同时满足自反、对称、传递性
	2. 因此，证明R是否为等价关系，依次从以上三点验证即可，也就是aRa,bRa,以及aRb,bRc是否能推出aRc
- <mark style="background: #BBFABBA6;">等价</mark>
	a,b在等价关系R中联结，则称a~b
- $[x_R]$表示关系等价关系R的<mark style="background: #BBFABBA6;">等价类</mark>，$x$是对应集合的代表
	✨**形式化**：$[x_R]$={s|(s,x)$\in$R}
- <mark style="background: #FF5582A6;">Partition</mark> of a Set 集合的<mark style="background: #BBFABBA6;">划分</mark>
	- **要求**：
		1. $A_i$非空
		2. 任意两个子集不相交
		3. 任意a$\in$A，则a一定存在于某个$A_i$当中，或者说子集的并集恰好为A
	- **记号**：$pr(A)=\{A_1,A_2,\dots \}$ 
---
1. 常见的等价关系
	1. 模$m$同余
## ✨重要定理
### **等价类**
内容：当R为等价关系时，以下三条表述**等价**：
![Pasted image 20240517092641.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517092641.png)
证明：
	①$\Rightarrow$②：![Pasted image 20240517092723.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517092723.png)
	②$\Rightarrow$③：![Pasted image 20240517092840.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517092840.png)
	③$\Rightarrow$①： ![Pasted image 20240517092903.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517092903.png)
### **等价类与划分**
- 内容：若有集合A上的等价关系R，则那么关系R下的<mark style="background: #FFF3A3A6;">等价类</mark>和A的<mark style="background: #FFF3A3A6;">划分</mark>是一一对应的
- 证明：
	1. 给定等价关系的类可以得到**A的划分**
		从划分的三个性质分条证明：非空；不相交；并为整体![Pasted image 20240517093601.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517093601.png)
			此处需结合类的等价表述；
			对于任意
	1. 给定A的划分，可以确定R以及R的类
		![Pasted image 20240517093632.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517093632.png)
### <mark style="background: #FFF3A3A6;">等价R取交集性质不变</mark>
- 内容：![Pasted image 20240521092838.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521092838.png)
- 证明：![Pasted image 20240521092847.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521092847.png)
### <mark style="background: #FFF3A3A6;">等价R取并集</mark>
- 内容：满足自反与对称![Pasted image 20240521093210.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521093210.png)
- 证明：![Pasted image 20240521093217.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521093217.png)
### <mark style="background: #FFF3A3A6;">等价关系并集的连通关系</mark>
- 内容：$(R_1\cup R_2)^*$ 满足对A的等价关系
- 证明：
## 👏手法
### 从R得到A的划分
- 将所给的R画成有向图的形式，对于这样的连通分量是A的一个划分：
	1. 各个顶点存在自环；
	2. 每条边都是双边
	3. 满足传递性
	注：因为给出的R不一定是等价关系；而等价关系和划分是一一对应的。因此，要从有向图中根据等价关系寻找A的划分。
>举例：![Pasted image 20240521071901.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521071901.png)

### n元集合上的等价类的个数
- ✅原理：可以通过图示法，集合等价关系与A的划分的关系求解
- 🌰:![Pasted image 20240521092323.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521092323.png)
	- 进阶：❓<mark style="background: #BBFABBA6;">|A|=n时，等价关系个数p(n)=_</mark>
	- ✅![Pasted image 20240521092710.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521092710.png)
		- 推导原理：
			对于第n个元素，j表示前n-1个元素中与该元素处于同一个划分的元素个数。
			因此，首先从n-1个元素里选择j个元素，剩下的n-1-j个元素的划分方式就是p(n-j-1).
		- 手算方式：![Pasted image 20240521100317.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521100317.png)
# 6. 偏序
## 📝相关概念
- 偏序
	在S上满足自反的、<mark style="background: #FFF3A3A6;">反对称</mark>的、传递的关系R，称为偏序
		若(a,b)与(b,a)同时成立,则蕴含a=b
- $(S,R)$被称为偏序集 *poset* 
- <mark style="background: #BBFABBA6;">常见的偏序集</mark>
	- $(Z^+,|)$  正整数的整除关系
	- (Z,>=) 整数的大小比较关系
	- (P(S),$\subseteq$)  子集的包含关系
- 可比性 *Comparability*
	![Pasted image 20240521103849.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521103849.png)
- <mark style="background: #ADCCFFA6;">全序集</mark> totally ordered set /  **<mark style="background: #ADCCFFA6;">chain</mark>**
	（S,<=)是偏序，且任意两个集合中的元素均满足**可比**关系
	🌰:子集的属于关系是偏序集，**但是并非全序集**，这是因为：![Pasted image 20240521122819.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521122819.png)
- 良序集 well-ordered set
	**前提**：
		是全序集
		任意一个非空子集存在**最小**元素
- 字典顺序 lexicographic order
	![Pasted image 20240521105945.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521105945.png)
	- 对于两个偏序集，在第一个R下相同时再比较下一项
	- 满足这种性质的($A_1$x$A_2$,<=)也是一种偏序关系
### 哈斯图 Hasse Diagrams
- <mark style="background: #ADCCFFA6;">得到方式</mark>：在偏序关系的图的基础上，先去除自环，再去除满足传递性的路径，只留下必要的路径。最后，将较小的点（起点）置于下方，去除箭头（看上去像无向图）
- 🌰几种模型的哈斯图画法：![Pasted image 20240521124109.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521124109.png)
	1. 对于作为全序关系/链的`<=`关系，它的哈斯图就是一条<mark style="background: #FFF3A3A6;">链</mark>
	2. 对于整除关系: 可以存在多个极高元
	3. 对于子集的属于关系：存在一个最高元
#### 元的概念
- 极大元 maximal  不存在可以覆盖~的元素；在链的<mark style="background: #FF5582A6;">top</mark>;<mark style="background: #FFF3A3A6;"> 可以不唯一</mark>
- 极小元 minimal   不存在比当前元素还小的元素
- 最大元 greatest element 不一定存在，因为**不一定存在<mark style="background: #FFF3A3A6;">覆盖</mark>所有元素的元素**
- 最小元 least element   被所有其他元覆盖
- 🌰：最大值与最小值![Pasted image 20240521124438.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521124438.png)
#### 界的概念
>A是S的一个子集
- 上界：如果 u>=a 对于$\forall a\in A$均成立，那么u称为一个 <mark style="background: #ADCCFFA6;">upper bound</mark> of A
- 下界：如果 I <= a~，那么I称为一个 <mark style="background: #ADCCFFA6;">lower bound</mark> of A
	🌰![Pasted image 20240521132522.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521132522.png)
- 上确界：上界当中的最小值称为<mark style="background: #FFF3A3A6;"> least upper bound</mark>
- 下确界：下界当中的最大值称为<mark style="background: #FFF3A3A6;">greatest lower bound</mark>
	🌰：![Pasted image 20240521132836.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521132836.png)
### 格 lattice
- 定义：在<mark style="background: #ADCCFFA6;">偏序</mark>集的基础上，如果对于任何一对元素，都存在唯一的上确界与下确界，则称为~
- 🌰：![Pasted image 20240521133240.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521133240.png)
	- 在(b)哈斯图中，b,c之间虽然存在下确界a，但是**不存在唯一的上确界**(d/e都是上确界)
- 常见的格
	- (Z,<=)         上确界lub为较大数；下确界glb为较小数
	- ($Z^+,|$)          lub为最小公倍数； glb为最大公因数
		因此，判断给定的集合A与关系R（为整除|）时，如果在A中找不到某对元素的最大公因数或最小公倍数，那么就可以得出结论：这不构成一个格
### 字典序 
- 建立基础：拥有对两个集合的笛卡尔积 $A_1$ X $A_2$ 以及他们的关系R
- 🌰：字典序下的字符串比较
	- 原理：a~z的大小关系满足全序集
	- 比较方式：从前往后进行比较，直到某一位较小，或者某一串耗尽
### 拓扑排序
- 含义：对于给定的偏序对的哈斯图，构造一个序列满足：如果aRb(b在a后)，则序列中b在a后
- 算法伪代码：![Pasted image 20240521134351.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521134351.png)
- 评价：
	实际上答案不唯一，也就是类似于FDS里学的拓扑排序，每次打印入度为0的顶点并更新邻接顶点的入度。
## ✨重要定理
### 良序集的推广定理
- 内容：如果S是一个well-ordered set, 性质$P$(x)对于S上所有的X为$true$ 
- 证明：
	1. **基始步骤**：证明 𝑃(𝑥) 对 S 中的最小元素$x_0$​ 成立。
	2. **归纳步骤**：假设 𝑃(𝑦) 对于所有小于某个元素 x 的 𝑦 都成立（即 ∀𝑦<𝑥,  𝑃(𝑦) 为真∀y<x,P(y) 为真），然后证明 𝑃(𝑥)P(x) 也成立。
	![Pasted image 20240521123611.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521123611.png)
### 最大/小元
- 内容：当最大/小元存在时，它们一定唯一
### 任何一个全序集（链）都是一个格
### <mark style="background: #FFF3A3A6;">每一个非空的偏序集都存在至少一个最小元</mark>
📝证明：![Pasted image 20240521134118.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240521134118.png)