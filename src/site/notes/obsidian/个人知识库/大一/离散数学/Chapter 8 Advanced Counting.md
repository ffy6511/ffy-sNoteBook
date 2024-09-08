---
{"dg-publish":true,"permalink":"/obsidian////chapter-8-advanced-counting/","created":"2024-04-16T11:25:56.573+08:00","updated":"2024-09-08T15:25:05.520+08:00"}
---

# 1.递推关系的应用
- **递推关系的构造**：
	$a_n$用$a_i$表示，其中$i<n$的关系
- **验证递归关系是否正确**：
	1. 代入题目给出的$a_n$到递推关系式检验即可
	2. 可能存在多个解
- <mark style="background: #BBFABBA6;">给出多少个初始条件可以确定唯一解？</mark>
## 利用递推关系求解
1. 步骤：
	1. 找到$a_n$与$a_{n-1}$等的关系
	2. 列出递推公式
	3. 找到初始条件
	4. 求解通项公式
2. 关键：
	1. 将$a_n$的分解，通过下面的例题说明这点
3. e.g:<mark style="background: #BBFABBA6;">指定长度的比特串个数</mark>![Pasted image 20240419090407.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419090407.png)![Pasted image 20240419090422.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419090422.png)![Pasted image 20240419090450.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419090450.png)
4. e.g:<mark style="background: #BBFABBA6;">编码字的枚举</mark>![Pasted image 20240419090830.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419090830.png)
5. e.g:<mark style="background: #BBFABBA6;">多米诺骨牌的填充</mark>
	1. 技巧:考虑特殊位置的水平/垂直的填充方式
	2. 👍![Pasted image 20240419110016.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110016.png)![Pasted image 20240419110029.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110029.png)
6. e.g:<mark style="background: #BBFABBA6;">扩展要求的汉诺塔</mark>![Pasted image 20240419110114.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110114.png)![Pasted image 20240419110125.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110125.png)
## 从前向后考虑的比特串
1. 情形：包含xx的关系
2. 举例：
	1. 👍![Pasted image 20240419110316.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110316.png)![Pasted image 20240419110325.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110325.png)
	2. 👍![Pasted image 20240419110351.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110351.png)![Pasted image 20240419110337.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419110337.png)
# 2.求解线性递推关系
- <mark style="background: #ADCCFFA6;">k阶常系数线性齐次递推关系</mark>
	$a_n=c_1a_{n-1}+\dots+c_ka_{n-k}$ , 只要求$c_k$不为0，<mark style="background: #FF5582A6;">前面可以为0</mark>
		<mark style="background: #BBFABBA6;">e.g.</mark> $a_n=a_{n-5}$为5阶的~
- 求解~只需要<mark style="background: #FFF3A3A6;">k个初始条件</mark>，即可唯一确定
- 判断性质（多项）
	- 线性 linear
		- 所有的变量的次数只能为1
	- 齐次 homogeneous
		- $a_n=a_{n-1}a_{n-2}$同样是齐次的
		- 所有项中，各个变量的指数之<mark style="background: #FFF3A3A6;">和相同</mark>
		- 不含常数项
	- 常系数
	- 阶数 degree
## 求解常系数线性齐次递推关系
- 引理
	如果$s$与$t$是解，那么它们的线性组合也是解
### 定理①<mark style="background: #BBFABBA6;">没有重根</mark>的2阶:
	![Pasted image 20240419093450.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419093450.png)
	1. 举例应用：
	❓&✅![Pasted image 20240426075636.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426075636.png)
### 定理②存在重根时的2阶：
	![Pasted image 20240426075741.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426075741.png)
- 举例应用：![Pasted image 20240426075832.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426075832.png)
### 定理③不含重根的$k$阶方程：
	![Pasted image 20240426075919.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426075919.png)
### 定理④含有重根的$k$阶方程：
![Pasted image 20240426080129.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426080129.png)
>注意：每项是重数-1作为最高次
1. 应用举例：![Pasted image 20240426080753.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426080753.png)
## 求解常系数线性非齐次递推关系
1. <mark style="background: #FFB86CA6;">回顾定义</mark>：
	1. 线性：关注$a_i$的指数是否为1
	2. 齐次：项是否含有常数或函数项
	3. 常系数：系数不依赖于$n$
	4. $k$阶：$a_n$至少由$a_{n-k}$表示（$c_{n-k}$不等于0）
	- 区别![Pasted image 20240426180222.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426180222.png)
	- $a_n=a^2_{n-1}$属于 ：<mark style="background: #FFB86CA6;">非线性</mark>，可以看做$a_i$的系数不是常数
1. 定义补充：
	1. <mark style="background: #ADCCFFA6;">相伴的齐次递推关系</mark>
		将非齐次递推关系中的$f(n)$给舍去，只保留齐次关系
3. 定理⑤:<mark style="background: #BBFABBA6;">非齐次 = 特解+相伴解</mark>![Pasted image 20240426081540.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426081540.png)
4. 思路：
	1. 先求出相伴的线性递推关系的解
	2. **观察**$F(n)$的特点，假设合理的解并带入求解
5. ❓什么时候可以确保由$F(n)$得出合理的特解
	$\rightarrow$ <mark style="background: #BBFABBA6;">定理⑥</mark>：多项式与常数的幂的积
6. 举例应用：
	- ❓&✅![Pasted image 20240426081942.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426081942.png)![Pasted image 20240426081948.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426081948.png)
### <mark style="background: #BBFABBA6;">定理⑥</mark>
1. 内容![Pasted image 20240426082807.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426082807.png)
	1. 注意：特解当中的$t$来自于$F(n)$当中的多项式的次数
	2. 如果$s$恰好是相伴递推关系的一个解，且重数为$m$
2. 举例：
	- 判断$s$是否为相伴递推关系的解，进一步判断<mark style="background: #FFF3A3A6;">特解形式</mark>![Pasted image 20240426083146.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426083146.png)
### ❓<mark style="background: #FFB86CA6;">如何求解</mark>特解当中的$P_i$？
✅将含$P_i$的特解作为$a_n$<mark style="background: #FFF3A3A6;">代回</mark>原来的式子，利用<mark style="background: #FFF3A3A6;">系数的相等</mark>求得对应的$P_i$ 
	e.g. ![Pasted image 20240426112017.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426112017.png)![586d977489dd6ba61ab6ae909c5063b.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/586d977489dd6ba61ab6ae909c5063b.jpg)
### 👍叠加原理
- 含义：当F(n)是多项的时候，可以<mark style="background: #FFF3A3A6;">分别设出对应的特解</mark>
- 举例：❓![Pasted image 20240426182642.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426182642.png)
- ✅![e95773faa3daef515668ba81c52124e.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/e95773faa3daef515668ba81c52124e.png)
# 3.分治算法和递推关系
>分治递推关系：$f(n)=af(\frac n b)+g(n)$ 
## 不同算法的分治实现
### 二分搜索
- $n$为偶数时，$f(n)=f(\frac n 2)+2$ 
	- **2次比较**：①确定所需表的左右；②检查该部分项的个数
### 求序列的最大和最小
- $n$为偶数时，$f(n)=2f(\frac n 2)+2$ 
	- **2次比较**：①比较最小；②比较最大
# 4.生成函数
1. 定义：由序列对应到函数的系数
- ![Pasted image 20240426090839.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426090839.png)
- 当$a_{k+p}$=0时，也认为这个<mark style="background: #ADCCFFA6;">有限序列</mark>具有生成函数（高阶为0）
## 由序列得到生成函数
步骤
	- 写出一一对应的级数
	- 观察是否有封闭解
- ![Pasted image 20240426091227.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426091227.png)
## 由生成函数求原序列
1. 步骤：
	1. 将所给的复杂生成函数分解为简单的生成函数之和/积
	2. 将分解之后的生成函数用幂级数表示，得到相应的序列
## 计数问题
- 情形：允许重复，并且存在某种约束
- 举例：
	- ❓8块相同的饼干分给3个不同的孩子，分别得到的饼干数要满足\[1,3],\[2,3],\[1,2],则：
	- ✅$(x^1+x^2+x^3)(x^2+x^3)(x^1+x^2)$，求乘积中的$x^8$的系数即可
- 进阶例题
	- 特征：结合广义的二项式表示
	- 举例：❓![Pasted image 20240430101444.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240430101444.png)
## 求解递推关系
- 步骤：
	- 思路①：乘积法
		1. 用$x^n$同乘递推关系的两端
		2. 设$G(x)=\sum _{n=0}^\infty a_nx^n$
		3. 将不同的求和化为$n=0$开始
		4. 将剩余的和函数写$G(x)$的形式表示
		5. 解出$G(x)$然后将<mark style="background: #FFF3A3A6;">和函数展成</mark>$x^n$的<mark style="background: #FFF3A3A6;">幂级数</mark>
	- 思路②：原地构造法
		1. 见例①
- 举例：
	- ①![Pasted image 20240430104610.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240430104610.png)![Pasted image 20240430104625.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240430104625.png)
## 证明恒等式
举例：
	①![Pasted image 20240430110009.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240430110009.png)![Pasted image 20240430110019.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240430110019.png)
## 定理
### 生成函数的相加与相乘
1. 内容：![Pasted image 20240426091455.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426091455.png)![Pasted image 20240426091647.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426091647.png)
2. 举例：![Pasted image 20240426091535.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426091535.png)
	>也可以通过微积分的求导得到结果
### 二项式表示:通常->广义
- 定义：
	- ①![Pasted image 20240426093055.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426093055.png)
	- ②广义的二项式公式![Pasted image 20240430101723.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240430101723.png)
		要求|x|<1
- 举例：![Pasted image 20240426093102.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426093102.png)
- 转换公式：![Pasted image 20240426093119.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426093119.png)
### 常见事实
![Pasted image 20240426103337.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426103337.png)![Pasted image 20240426103357.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426103357.png)![Pasted image 20240426103421.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426103421.png)
# 5. 容斥
## 容斥原理
1. 内容：![Pasted image 20240507091520.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507091520.png)
2. 另一种形式：![Pasted image 20240507091834.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507091834.png)
## 具有约束条件的方程的整数解个数
1. 形式：给出的$x_i$的限制是不超过某个数。我们知道，如果是不小于某个数时，可以利用<mark style="background: #FFF3A3A6;">隔板法</mark>进行快速求解。因此，可以转化为对应解的逆计算
	由于隔板法适用于$x_i$>=某个数的约束条件，因此当题目的条件给出的是$x_i$<=某个数时，可以令反面的性质为$P_i$
2. 举例：![Pasted image 20240507092233.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507092233.png)
## 埃拉托色尼筛
1. 作用：寻找不超过$N$的素数的个数
2. 原理：
	1. 根据<mark style="background: #ADCCFFA6;">算数的基本定理</mark>[[obsidian/个人知识库/大一/离散数学/Chapter 4 数论和密码学#3.2 定理\|Chapter 4 数论和密码学#3.2 定理]]，$N$一定有一个不超过$\sqrt N$ 的素因子，将这些素因子记为集合A
	2. 满足条件的素数一定是A以及范围内不能被A内任意元素整除的数字
	3. 因此，利用<mark style="background: #FFF3A3A6;">容斥原理</mark>计算后一部分即可
3. 举例：寻找不超过`100`的素数个数![Pasted image 20240507092959.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507092959.png)
##  ✨确定集合的满射函数个数
1. 形式：求解从$m$到$n$元素集合的满射函数个数
2. 原理：设$P_i$是陪域中$b_i$不在值域中的情况，那么符合条件的满射函数是所有$P$非同时成立的情况
3. 举例：![Pasted image 20240507095452.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507095452.png)
4. 定理：![Pasted image 20240507095544.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507095544.png)
## 错位排列
1. 形式：排列$n$个物体且没有一个物体在其初始位置
2. 定理：![Pasted image 20240507095926.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507095926.png)
	1. 证明：![Pasted image 20240507095945.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240507095945.png)
## 解题提醒：
1. <mark style="background: #BBFABBA6;">整除性问题</mark>时，交集的个数是N除以三者的<mark style="background: #FFF3A3A6;">最小公倍数</mark>
	1. 如果不是互质的三个数，那么就不是三者的简单乘积！
2. 由26个不重复字母组成且包含`fish`的字符串个数为：`23!`
	1. 将`fish`看做一个字符，一共有`23`种字符
	2. <mark style="background: #FF5582A6;">into</mark> 同时出现`fish`与`bird`的字符串个数为`0`，因为同时出现了`i`，但是字母仅能出现一次
3. 