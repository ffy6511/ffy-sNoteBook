---
{"dg-publish":true,"permalink":"/obsidian/////ch8/","created":"2024-04-11T20:28:14.922+08:00","updated":"2024-09-08T15:25:05.372+08:00"}
---

1. 多元函数的极限与连续性
##  二重<mark style="background: #BBFABBA6;">极限存在性</mark>判断
- 原理
	当二元函数以任意方向趋于点$P_0(x_0,y_0)$时，$f(x,y)$都趋于点$A$,则称~
- 归结原理的推论
	由不同方向得到的极限存在但不同 or 某种方向的极限不存在，则二重极限不存在
- 举例![Pasted image 20240411203404.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240411203404.png)![Pasted image 20240411203415.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240411203415.png)
	先后求x,y的极限称为<mark style="background: #ADCCFFA6;">累次极限</mark>，要与我们此处同时求x,y的二重极限<mark style="background: #FFF3A3A6;">区分</mark>
## 两种<mark style="background: #BBFABBA6;">极限的关系</mark>
![Pasted image 20240411203707.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240411203707.png)
## 二元函数的<mark style="background: #BBFABBA6;">连续</mark>
1. 全增量![Pasted image 20240411203849.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240411203849.png)
2. 偏增量![Pasted image 20240411203934.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240411203934.png)
3. 连续曲面![Pasted image 20240411204003.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240411204003.png)
4. 介值定理![Pasted image 20240411204044.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240411204044.png)

## <mark style="background: #BBFABBA6;">一句话说理</mark>
1. 复合函数的偏导
	![Pasted image 20240415103512.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415103512.png)![Pasted image 20240415103531.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415103531.png)
	<mark style="background: #ADCCFFA6;">链导法则</mark>：如果复合函数中无x，对x的偏导可略去这一项![Pasted image 20240415103855.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415103855.png)![Pasted image 20240415104044.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415104044.png)
2. 混合偏导数与求偏导的顺序无关
3. <mark style="background: #ADCCFFA6;">全微分</mark>
	1. <mark style="background: #ADCCFFA6;">全增量</mark>![Pasted image 20240415110155.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415110155.png)
	2. 相关定理
		1. 在($x,y$)处<mark style="background: #FFF3A3A6;">可微</mark>，则<mark style="background: #FFF3A3A6;">必连续</mark>
		2. 可微则偏导数相等![Pasted image 20240415110445.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415110445.png)
		3. <mark style="background: #ADCCFFA6;">全微分</mark>![Pasted image 20240415110511.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415110511.png)
			1. 具体解题：求得各项的偏导并乘以$dx$后相加
				e.g.![Pasted image 20240415113246.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415113246.png)
4. 转换为极坐标形式
	1. 本质：将$(x,y)$分别用$(p$cos$\theta,p$sin$\theta)$代替，即$p$与$\theta$为$x与y$的复合函数
	2. 举例：![Pasted image 20240415111936.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415111936.png)
5. 偏导数的几何意义
	![Pasted image 20240415115129.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240415115129.png)
6. 隐函数的偏导数
	1. 由方程确定隐函数对象，视为复合函数
	2. 方法：
		1. 直接求偏导
		2. 同求微分，由微分的结果的偏导结果
		3. 对一个方程使用<mark style="background: #ADCCFFA6;">隐函数求导法</mark>
	3. 举例：
		1. e.g 偏导![Pasted image 20240421105703.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240421105703.png)
		2. e.g 微分—<mark style="background: #FFF3A3A6;">二阶微分</mark>![Pasted image 20240421105725.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240421105725.png)
			- z为被确定的隐函数，x\y为自变量，对这两种类型的微分有区别.对dz的再微分为$d^2z$，对dx,dy的~为0
			- 注意<mark style="background: #ADCCFFA6;">微分的复合公式</mark>：![Pasted image 20240421110317.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240421110317.png)
# 8.5 场的方向导数与梯度
## 定义
### 方向导数
![Pasted image 20240425113229.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425113229.png)
### 梯度
1. 梯度的定义![Pasted image 20240425114500.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425114500.png)![Pasted image 20240425114537.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425114537.png)
2. 用梯度表示方向导数![Pasted image 20240425114617.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425114617.png)![Pasted image 20240425114625.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425114625.png)
	1. 其中，在定点的梯度大小是一定的![Pasted image 20240425114724.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425114724.png)
	2. 当$l$与$grdu\ u(P_0)$的方向相同，即等于函数在$P_0$处的偏导结果的向量
## 定理
### <mark style="background: #BBFABBA6;">任意方向导数存在的充分条件</mark>
![Pasted image 20240425113320.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425113320.png)![Pasted image 20240425113326.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425113326.png)
>证明：![Pasted image 20240425113437.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425113437.png)
### <mark style="background: #BBFABBA6;">梯度运算法则</mark>
![Pasted image 20240425115552.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425115552.png)
## 手法
### <mark style="background: #BBFABBA6;">求解方向导数的最大值</mark>
1. 步骤：
	1. 求解$u$在$P_0$处的所有偏导结果$x'\ y'\ z'$ 
	2. 令$l$={$x',y',z'$}, 此时$\theta$等于0，有方向导数的最大值 
2. 举例：
	1. ❓![Pasted image 20240425115507.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425115507.png)
		1. ✅![Pasted image 20240425115521.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425115521.png)![Pasted image 20240425115526.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425115526.png)
### <mark style="background: #BBFABBA6;">梯度运算法则的运用</mark>
1. 举例
	1. ❓&✅![Pasted image 20240425115711.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425115711.png)
# 8.6 多元函数的极值及应用
>运用一元函数的泰勒公式，可以用多项式逼近一个多元函数，
## 定义
### 最值点
1. ~一定在边界、内部（稳定点/怀疑点）中取到
2. 如果实际问题已经排除了边界、不存在稳定点，且一定存在最值点，那么唯一的怀疑点一定就是最值点
## 定理
### <mark style="background: #BBFABBA6;">泰勒定理</mark>
1. 内容：![Pasted image 20240425121149.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425121149.png)
2. 相关概念：
	1. $R_n$ 拉格朗日余项![Pasted image 20240425121304.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425121304.png)
	2. $R_n$的误差![Pasted image 20240425121604.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425121604.png)
### 二元函数的<mark style="background: #BBFABBA6;">麦克劳林公式</mark>
>将泰勒定理的($x_0,y_0$)初始化为$(0,0)$时得到~
### 二元函数的<mark style="background: #BBFABBA6;">拉格朗日中值公式</mark>
1. 推演
	>在泰勒公式中令$n=0$,得到![Pasted image 20240425121935.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425121935.png)![Pasted image 20240425121948.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425121948.png)
2. 推论![Pasted image 20240425122050.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425122050.png)
	- 证明：![Pasted image 20240425122439.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425122439.png)
### <mark style="background: #BBFABBA6;">极值的必要条件</mark>
1. 内容：![Pasted image 20240425193224.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425193224.png)
2. 补充：
	1. $f(x,y)$在$P_0(x_0,y_0)$处取得极值时，其在该点的偏导数只有两种可能
		1. $f_x'(x_0,y_0)$与~均存在且同为0（$P_0$为稳定点/驻点）
		2. 两个偏导数中至少有一个不存在（$P_0$成为极值点的怀疑点）
	2. 极值点一定在稳定点与怀疑点当中取得
3. 启发：
	1. 对于怀疑点，用函数值不等式来检验
	2. 对于稳定点，利用定理：<mark style="background: #BBFABBA6;">极值的充分条件</mark>
### <mark style="background: #BBFABBA6;">极值的充分条件</mark>
1. 内容：![Pasted image 20240425194238.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425194238.png)![Pasted image 20240425194244.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425194244.png)
### <mark style="background: #BBFABBA6;">拉格朗日数乘法</mark>
>解决有条件极值问题
1. <mark style="background: #ADCCFFA6;">拉格朗日函数</mark>：![Pasted image 20240425210116.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425210116.png)
	$f$为**待求**的极值，$G$为变量满足的**约束条件**方程
2. **解方程组**：![Pasted image 20240425210316.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425210316.png)
## 手法
### 给出多元函数的展开式
1. ❓&✅![Pasted image 20240425193017.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425193017.png)
### 求极值
1. 步骤
	1. 计算一阶偏导函数
	2. 令一阶偏导为$0$，据此求得驻点
	3. 将驻点代入二阶偏导函数，分别求得A,B,C
	4. 计算$B^2-AC$的结果并判断
2. 举例：
	1. ❓![Pasted image 20240426143057.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426143057.png)
	2. ✅![Pasted image 20240426143050.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426143050.png)
		1. 注意公式判断法失效时，需要进一步讨论，确定极值是否存在
### 求最值
>最值需要先求极值，如果给出时区域范围，而不是条件约束，那么需要先在区域内遵循求极值的顺序（驻点与偏导数不存在的点），再在边界上转化成条件约束求极值的问题！
1. 步骤
	1. 区域内求极值
	2. 边界上求条件约束下的极值
2. 举例：
	1. ❓![Pasted image 20240426150231.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426150231.png)
	2. ✅![Pasted image 20240426150318.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426150318.png)
		1. 此处的条件限制可以直接带入简化方程
	3. ❓多层条件限制的逐层分析![Pasted image 20240426151859.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426151859.png)
	4. 👍![Pasted image 20240426151911.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426151911.png)![Pasted image 20240426151918.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240426151918.png)
### 拉格朗日数乘法的应用
1. 内接长方体的体积最值❓&✅
	![Pasted image 20240425210448.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425210448.png)![Pasted image 20240425210512.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425210512.png)![Pasted image 20240425210616.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240425210616.png)
2. 不等式形式的条件约束方程
# 8.7 偏导数在几何上的应用
