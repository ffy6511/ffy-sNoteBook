---
{"dg-publish":true,"permalink":"/obsidian////chapter-4/","created":"2024-04-03T15:31:01.962+08:00","updated":"2024-09-08T15:25:05.516+08:00"}
---

# 1.整除性和模算术
## <mark style="background: #BBFABBA6;">模幂运算</mark>
1. **情形**：计算一个数的幂次方后再对一个数取模的运算
2. <mark style="background: #ADCCFFA6;">步骤</mark>： 
	1. 化指数为<mark style="background: #FFF3A3A6;">二进制数</mark>
	2. 从二进制的第一位开始，初始化 result=1,base=基数
		1. 每次都将base平方并对m取模
		2. 如果二进制为0，result不变；
		3. 如果二进制为1，result = result x base mod m
			1. 注意，这里乘的是变化之前的base!
3. ![Pasted image 20240423093253.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240423093253.png)
# 2.整数的表示和算法
# 3.素数和最大公约数
## 3.1 定义
1. 素数
	- 1不是素数
2. <mark style="background: #ADCCFFA6;">埃拉托斯特尼筛法</mark>
	- 作用：寻找不超过给定整数的所有素数
	- 解释：
		- 不超过n的合数，其本身的素因子一定不超过$\sqrt{n}$；
		- 对于n,找出不超过$\sqrt{n}$的所有素数，然后在2~n的范围内排除这些素数除自身以外的倍数。最后剩下的数就2~n范围内的素数。
3. <mark style="background: #ADCCFFA6;">梅森素数</mark>
	- 目前已知最大的素数均为$2^p$-1的形式，其中p也为素数
	- 将这种形式的素数，称为梅森素数
	- 然而，这并**不意味**着所有满足p为素数的$2^p$-1**均为素数**！
4. <mark style="background: #ADCCFFA6;">卡宁汉数</mark>
	- 形如$k^n\pm1$ 且 k很小而n很大的数（均为正整数),被称为~
5. 最大公约数
	1. 含义：使得**d|a**且**d|b**的**最大**整数$d$被称为a与b的~
	2. 表示：**gcd( a , b )**
	3. <mark style="background: #ADCCFFA6;">互素</mark>：若gcd(a , b) = 1，我们称a与b是两两~的
	4. <mark style="background: #FFF3A3A6;">寻找方法</mark>
		1. 利用整数的**素因子分解式**
			a = $p_1^{a_1}$$p_2^{a_2}$$p_3^{a_3}$…$p_n^{a_n}$, b = $p_1^{b_1}$$p_2^{b_2}$$p_3^{b_3}$…$p_n^{b_n}$
			则：记$c_i$=min{$a_i$,$b_i$}有，**gcd(a,b)** = **$p_1^{c_1}$$p_2^{c_2}$$p_3^{c_3}$…$p_n^{c_n}$**
		2. 暴力枚举
6. <mark style="background: #ADCCFFA6;">最小公倍数</mark>
	1. 含义：a,b的~是能够被a,b分别整除的最小正整数
	2. 表示：**lcm(a,b)**
	3. 利用<mark style="background: #BBFABBA6;">素因子分解式寻找</mark>
		1. 方式：只需要将gcd寻找方法中的$c_i$改为**max**($a_i$,$b_i$)即可
## 3.2 定理
1. <mark style="background: #BBFABBA6;">算数基本定理</mark>
	**每个大于1的整数都可以被唯一地写成两个或多个素数的乘积**；
	其中，素数因子以非递减的顺序排列
2. <mark style="background: #BBFABBA6;">素因子定理</mark>
- 内容：**如果n是个合数，那么一定有一个素因子小于等于$\sqrt{n}$** 
- 证明：
	如果n为合数，由合数的定义我们知道：一定存在一个1<a<n的因子a. n =ab
	若a>$\sqrt{n}$ 且 b>$\sqrt{n}$ 则ab >n，矛盾。因此a,b中一定有一个小于等于$\sqrt{n}$,
	在这种情况下，这个数x可能存在两种情况：
	1. x为素数，证毕；
	2. x不为素数。进一步，根据<mark style="background: #BBFABBA6;">算数基本定理</mark>，存在比它小的质因子，证毕
- <mark style="background: #BBFABBA6;">推论</mark>：
	**如果一个整数不能被小于等于它的平方根的素数整除，则它本身为素数**
> 在推论的支撑下，诞生了被称为试除法的<mark style="background: #ADCCFFA6;">蛮力算法</mark>。
> 即把n除以所有不超过$\sqrt{n}$的<mark style="background: #FFF3A3A6;">素数</mark>，如果均无法被整除，则n为素数。
> 我们可以用这个方法来证明较小的数是一个素数

3. <mark style="background: #BBFABBA6;">素数的无限性</mark>
4. <mark style="background: #BBFABBA6;">素数定理</mark>
- 内容：
	- 记不超过x的素数个数为n，π(x)=$\frac n{\frac x {lnx}}$ ，当x无限增长时，π(x)趋近于1；
	- 也就是说，x足够大时，不超过x的素数个数接近于$\frac x{ln x}$ 
- 推论：
	- 由此，我们得到一个整数n是素数的概率大约是$\frac 1{ln n}$ 
5. <mark style="background: #BBFABBA6;"> gcd与lcm的启发</mark>
	ab为正整数则 **ab = gcd(a,b)·lcm(a,b)**
1. <mark style="background: #BBFABBA6;">贝祖定理</mark>
	1. 内容：如果a,b均为正整数，则存在整数s,t有 **gcd(a,b)=sa+tb** 成立
	2. 其他定义：
		1. <mark style="background: #ADCCFFA6;">贝祖系数</mark>：s t称为a,b的~
		2. 上式称为<mark style="background: #ADCCFFA6;">贝祖恒等式</mark>
2. <mark style="background: #FFF3A3A6;">与模数互素的除数可以作用于同余式的两端</mark>
	1. 内容：若ac$\equiv$bc(mod m )且**gcd(c,m) = 1**, 则 $a\equiv$ $b$ (mod m).
## 3.3 手法
1. **求n的素因子分解式**
- 过程
	1. 用递增的素数去除n
	2. 如果无法除尽就增大素数；如果能够除尽则记录素数a1，同时用商代替被除数继续这一步骤
	3. 直到步骤②中得到的商也为素数（或者说继续除，得到商为1，记录除数）
	4. 最后可以写成 n =a1 x a2 x a3$\dots$ 的形式
2. <mark style="background: #FFF3A3A6;">欧几里得算法</mark>求解gcd(a,b)
	内容：gcd(a,b) = gcd(b,r)，其中**r为a/b的余数**
3. <mark style="background: #FFF3A3A6;">寻找</mark>a,b的等于gcd的<mark style="background: #FFF3A3A6;">线性组合</mark>的方法
	1. **反向处理**欧式算法![Pasted image 20240403200757.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240403200757.png)
	2. **<mark style="background: #FF5582A6;">扩展欧几里得算法</mark>**
		1. 先设置$s_0$=$t_1$=1,$s_1$=$t_0$=0, $q$ 为欧式算法中产生的商 ($q_1$为第一个商)
		2. 通过$s_j$ =$s_{j-2}$ - $q_{j-1}$$s_{j-1}$ , $t_j$ =$t_{j-2}$ - $q_{j-1}$$t_{j-1}$（其中j=2,3,4…,n）
		3. 最后，**gcd(a,b)** = $s_n$$a$ + $t_n$$b$ 
## 3.4 举例
扩展欧几里得算法的运用![c7bc39d94161debca5b057fbe2bd33f.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/c7bc39d94161debca5b057fbe2bd33f.jpg)
# 4.求解同余方程
## 知识回顾
1. 形如$a$$x$ $\equiv$ $b$ (mod $m$) 的方程被称为<mark style="background: #ADCCFFA6;">同余方程</mark>
	1. 有解的充要条件为 gcd(a,b)|m
2. 为了求解同余方程，引入 <mark style="background: #ADCCFFA6;">数论倒数</mark>
	1. 定义$\bar{a}$为$a$的数论倒数，有$\bar{a}$$a$ $\equiv$ 1(mod $m$)
	2. 当$a$ 和 $m$ 互质且$m$>1时，$\bar{a}$存在且模数$m$唯一
3. <mark style="background: #BBFABBA6;">求解数论倒数的方法</mark>
	1. 引入：若gcd(a,m)=1,根据裴蜀定理有 sa+tm = 1,两边同时对m取模有           $s$$a$=1(mod $m$) ,因此$s$就是数论倒数
	2. 由1可知，求解数论倒数与裴蜀定理密切相关
		举例：![Pasted image 20240403204803.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240403204803.png)
	3. 注意，是将最后能够除尽时候的除数放在反向处理的左端，右边与101相乘的数就是101 modulo 4620的数论倒数
4. <mark style="background: #BBFABBA6;">进一步求解同余方程的方法</mark>
	1. 有$\bar{a}$$a$ $\equiv$ 1(mod $m$)① 与 $a$$x$ $\equiv$ $b$(mod $m$)②
	2. 对②两边同乘 $\bar{a}$ 得到 $x$ $\equiv$ $b$$\bar{a}$ (mod $m$) ③
	3. 然后检验③式的每一组解是否都是原同余方程的解
5. <mark style="background: #BBFABBA6;">如何求解线性同余方程组？</mark>
	1. <mark style="background: #ADCCFFA6;">中国剩余定理</mark>
		1. 内容：
			对于 $x$ $\equiv$ $a_i$(mod $m_i$)的方程组，当$m_i$为大于1且两两互素的正整数时，（$a_i$可为任意整数），则方程组的
		2. 应用：![Pasted image 20240403214735.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240403214735.png)
	2. <mark style="background: #ADCCFFA6;">反向替换</mark>的方法
		1. 含义：将同余方程重写，然后代入别的同余方程，化简并迭代过程
		2. 举例：![Pasted image 20240403212712.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240403212712.png)
			1. <mark style="background: #FFB86CA6;">化简</mark>![bd6d5db841e0c1a8f9acf86a34416e6.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/bd6d5db841e0c1a8f9acf86a34416e6.jpg)
				1. 关键在于化$nx$为$(km+1)x$然后利用~同余$x$进行求解![4a13371d729187e436192c62d54d9a1.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/4a13371d729187e436192c62d54d9a1.jpg)
1. <mark style="background: #BBFABBA6;">费马小定理 </mark>
	1. 内容
		若 $p$ 为素数，且$a$是一个不能被 $p$ 整除的整数，则：$a^{(p-1)}$$\equiv 1$ (mod $p$)
		再者，$a^p$ $\equiv$  $a$(mod $p$)
	2. 应用
7. <mark style="background: #BBFABBA6;">伪素数</mark>
	1. 定义：![Pasted image 20240419081117.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419081117.png)
	2. 其他：![Pasted image 20240419081218.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419081218.png)
8. <mark style="background: #BBFABBA6;">如何判断r是否为p的原根？</mark>
	1. 步骤
		1. 列出$r^i$ mod $p$的结果（可在前者的基础计算)
		2. 遍历$i$从1~$p-1$
		3. 观察结果，如果均无重复（p-1个结果)，则称r是p的原根
	2. 相关原理--为什么$i$是<mark style="background: #FFF3A3A6;">1~p-1</mark>
		1. 根据**费马小定理**，$r^p$ mod $p$同余$r$,因此进入循环
9. <mark style="background: #BBFABBA6;">求解离散对数</mark>
	1. 定义：![Pasted image 20240419084455.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419084455.png)
	2. 注意：
		1. 每个素数$p$都存在一个模$p$的原根
		2. 讨论离散对数的前提，必须是原根
## 练习巩固
1. <mark style="background: #BBFABBA6;">求逆</mark>（求$a$ 模 $m$ 的逆）![Pasted image 20240403210129.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240403210129.png)
	1. 根据 检验gcd( $a$ ,$m$) =1 来说明该逆确实存在
	2. 对$a$与$m$使用欧几里得算法
	3. 化简到最终结果（余数为0）后从倒数第二行开始代回
	4. 写作 1 = $s$$a$+$t$$m$的形式，此时$s$就是所求的逆
2. 由逆进一步求<mark style="background: #BBFABBA6;">解线性同余方程</mark> $a$$x$ $\equiv$ $b$ (mod $m$)
	1. 用上一步求得的$\bar{a}$同乘方程得：$x$ $\equiv$ $\bar{a}$$b$ (mod $m$)
	2. 直接对右式进行简单计算并化简
	3. 得到最终结果
	![Pasted image 20240404105130.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240404105130.png)
3. <mark style="background: #BBFABBA6;">求解方程组</mark>
	1. 反向替代
	2. 利用中国同余方程
4. <mark style="background: #BBFABBA6;">由费马小定理求解高阶的模数</mark>
	✅![Pasted image 20240419084923.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419084923.png)
		注意取模后进一步运算（模数相同）可在先前的基础上继续计算结果！
1. <mark style="background: #BBFABBA6;">求解a的以p为底模m的离散对数</mark>
	1. ❓![Pasted image 20240419083106.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419083106.png)
		1. ✅（<mark style="background: #FFF3A3A6;">列表</mark>，得答案）
	2. ❓&✅![Pasted image 20240419084728.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240419084728.png)
# 5.同余的运用
## 5.1 散列函数
- 将k的键值经过取模运算分配内存空间
- $h$($k$) = $k$ mod $m$
- 应该是满射的
<mark style="background: #BBFABBA6;">遇到冲突情况如何解决</mark>？
>使用散列函数分配过的内存的、下一个未被分配的内控空间
## 5.2 伪随机数
### ①最常用的**产生方法**——**<mark style="background: #ADCCFFA6;">线性同余法</mark>**
![Pasted image 20240407075824.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240407075824.png)
②<mark style="background: #ADCCFFA6;">纯倍式生成器</mark>
取 $c$=0 的线性同余生成器
## 5.3 校验码
