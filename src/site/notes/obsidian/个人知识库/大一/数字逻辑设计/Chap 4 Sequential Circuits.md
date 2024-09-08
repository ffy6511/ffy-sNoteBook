---
{"dg-publish":true,"permalink":"/obsidian////chap-4-sequential-circuits/","created":"2024-04-24T13:26:26.640+08:00","updated":"2024-09-08T15:25:05.424+08:00"}
---

- 之前讲的是组合电路，本章介绍的是时序电路
	- 组合电路的局限性：
		1. 无法实现信息的存储，所有的功能模块对于特定的输入给出相同的输出
		2. 复杂的逻辑，抽象层级多
	- 时序电路的优点：
		1. 拥有**存储信息**的能力（计算机）
		2. 输出除了与输入有关（也可以没有输入），也与自身的状态State有关
	- 关系：
		时序电路在组合电路的基础上得到![Pasted image 20240424134625.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424134625.png)
- **时序电路的分类**
	><mark style="background: #ADCCFFA6;">依据</mark> 输入信号的时间和内部状态改变的时间
	>1. **同步时序电路** **synchronous sequential circuit**
	>	1. 经过一定的时钟间隔，在离散的时间内采集信息
	>	2. 将时钟脉冲作为输入信号的~称为钟控时序电路 (clocked sequential circuit)
	>2. **异步时序电路 asynchronous sequential circuit**
	>	1. 看似不经过一定的时钟间隔（间隔取很小）
- 时序电路的目标
	- 使得整体的效率（流量）最高
## 1. <mark style="background: #BBFABBA6;">延时</mark>
- 什么是延时![Pasted image 20240424140821.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424140821.png)
- 如何利用延时（延时的好处）![Pasted image 20240424140856.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424140856.png)
	- 将输出的Y作为输入信息的一部分，使得输出由B与Y(state)共同决定
	- S为0时，Y等同于Y(t-0.9) ; S为1时，Y就是B
	- 因此，S为0时Y存储了信息
## 2.改进为<mark style="background: #ADCCFFA6;">振荡器</mark>（时钟）
- ![Pasted image 20240424142525.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424142525.png)
- 时序电路的信息存储元件
	- 主要有 锁存器(latch) 与 触发器(flip-flop) 两种
	- 锁存器是触发器的基础，构成触发器
	- 多数情况下使用触发器
# 3.信息存储元件
## 缓冲器 buffer
>是构成锁存器的基础
- 一般通过两个非门串联，从给定输入到更新输出存在延时![Pasted image 20240424134019.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424134019.png)
---
## 锁存器 latch
1. 将buffer的非门换成**或非门**/**与非门**，分别得到SR锁存器与S'R'锁存器
2. 输入均为S(Set) 和 R(Reset) 两部分
3. 输出均为Q和Q'两部分
---
### <mark style="background: #ADCCFFA6;">SR锁存器</mark>
![Pasted image 20240424140224.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424140224.png)
1. 解释
	1. 均为0时意味着锁存数据
	2. `11`时没有定义，因为或非门用1（高电平）设置，无法同时设置
	3. set为1表示设置为1,reset为1表示复位为0
2. 注意
	1. 1有效
	2. 画图时S对应Q', R对应Q
### <mark style="background: #ADCCFFA6;">S'R'锁存器</mark>
![Pasted image 20240424140233.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424140233.png)
1. 解释：S' R'![Pasted image 20240424143816.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424143816.png)
	1. 逻辑高低对调
	2. 此时set为1表示设置Q为0/或者说reset为0（低电平有效）设置Q为0
	3. reset为1表示设置Q为1
2. 注意：
	1. S'对应Q , R'对应Q'
	2. 0有效，因此无法同时设置SR为`00`
### <mark style="background: #ADCCFFA6;">门控SR 锁存器</mark>
1. 图示![Pasted image 20240424143927.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424143927.png)
2. 解释：
	1. C是时钟输入
	2. C为0时<mark style="background: #FFF3A3A6;">锁存数据</mark>； C为1且SR为00时<mark style="background: #FFF3A3A6;">锁存数据</mark>
	3. 1有效，且SR不为`00`时，功能与SR相同（S设置Q为1）
---
### <mark style="background: #ADCCFFA6;">D锁存器</mark>
1. 图示![Pasted image 20240424144119.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424144119.png)
2. 解释
	1. C为0时锁存数据
	2. C为1时Q由D得到
3. 表示方式：![Pasted image 20240424144412.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424144412.png)
---
### <mark style="background: #ADCCFFA6;">传输门实现的D锁存器</mark>
1. 图示![Pasted image 20240424144321.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424144321.png)
# 触发器👍
## 📝不同的触发器
### <mark style="background: #BBFABBA6;">SR主从触发器</mark>
1. 图示：![Pasted image 20240424145150.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424145150.png)
2. 解释：
	1. 由于C为0时数据锁存，锁存器1,2不能同时改变输出数据
3. 局限性：
	SR 触发器之所以是所谓的 pulse-triggered 的，是因为在 C 置 `1`，S 和 R 置 `0` 时，如果出现噪音（S 或 R 输入短暂地跳变到 `1`），就会导致 Slave 写入异常数据（这个行为被称为 1s-catching）。
	>图示：![Pasted image 20240424151310.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424151310.png)
	>	此处的Y指的是第一个锁存器的Q；
	>	部分4和5对应噪音的影响；
4. 要求S,R的变化持续至少一个脉冲，才能避免`噪声`($1s\ catching$)
---
### J-K触发器
- 与SR主从触发器相似，J-S, K-R,
- 不同之处在于J-K触发器允许`11`同时存在，且此时将`state`反置
- 图示：![Pasted image 20240508141021.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240508141021.png)
	- 用D边缘触发器来作为触发器的核心

### T触发器
- 特征：
	1. 仅有`T`一个输入信号
	2. `0`保持不变；`1`**翻转** state
- 根据第二点特征，我们可以看到，将J-K触发器中的J=K=T即可
	- 正因为需要翻转，所以需要一个初始状态
- 由于是同样为主从触发器，存在`1s catching`问题需要改进
- 图示：![Pasted image 20240508141511.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240508141511.png)

### <mark style="background: #BBFABBA6;">D触发器</mark>
1. **边沿**触发式**触发器**主要对脉冲的 上升沿 或 下降沿 敏感![Pasted image 20240424152111.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424152111.png)
	1. 上图为<mark style="background: #BBFABBA6;">下降沿</mark>敏感
	2. 可以避免`噪声`
	3. 与上述的脉冲触发器相对
	4. D为0时Q为0，反之为1
	5. D触发器（J-K触发器）可以作为脉冲触发器，因为它们本身是**边缘触发器**
2. 下图介绍<mark style="background: #BBFABBA6;">上升沿</mark>触发(positive-edge-triggered)的 D 触发器
3. 图示：![Pasted image 20240424151937.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424151937.png)
	认为上述的第`5`部分是正确的(`4`不存在)
	1. 从锁存器储存的是上升沿前一刻写入主锁存器的结果
	2. 只存在一个输入
	3. 将 C 前的非门去掉则可得到下降沿触发(negative-edge-triggered)的 D 触发器
## 📝触发器描述
### <mark style="background: #ADCCFFA6;">特征表</mark>
>Characteristic table
![Pasted image 20240515145134.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515145134.png)
由当前状态和输出决定下一状态
### <mark style="background: #ADCCFFA6;">特征公式</mark>
>![Pasted image 20240515145202.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515145202.png)
用布尔代数表示下一状态
### <mark style="background: #ADCCFFA6;">激励表</mark>
对换特征表的次序即可
![Pasted image 20240515145258.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515145258.png)
### 🌰不同触发器的描述
①D触发器：![Pasted image 20240515145514.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515145514.png)
②T触发器：
![Pasted image 20240515145527.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515145527.png)
③SR触发器：
![Pasted image 20240515145541.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515145541.png)
④J-K触发器：
![Pasted image 20240515145556.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515145556.png)
## 🧩标准图形符号
![Pasted image 20240424153047.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424153047.png)
	上图锁存器的C的不必为时钟； 触发器的C为时钟信号
## 直接输入
异步触发信号
- 介绍：<mark style="background: #BBFABBA6;">Direct inputs</mark> 独立于脉冲 与 上升沿/下降沿，只要按下按钮就可以即时生效
- 图示：![Pasted image 20240508134111.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240508134111.png)
	- 
# 延时分析
时序电路的延时分析的主要构成
1. 组合电路导致的延时；
2. 触发器导致的延时；
3. 电路的松弛时间
## 组合电路延时

# 时序电路分析

## 输入方程
🌰![Pasted image 20240512125144.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512125144.png)
> DA​ 得到转移方程：𝐴(𝑡+1)=𝐷𝐴=𝐴(𝑡)𝑋+𝐵(𝑡)𝑋
> 可以简写为 𝐴(𝑡+1)=𝐷𝐴=𝐴𝑋+𝐵𝑋
## 状态表
🌰:![Pasted image 20240512125315.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512125315.png)

## 状态图
>**State Diagram**
### 状态图的分类
1. <mark style="background: #ADCCFFA6;">米勒型</mark> Mealy
- 特点
	- 输出与当前状态和输入<mark style="background: #FFF3A3A6;">均有关</mark>
	- 输出位于`edge`
	- edge上分别为input和output `x`/`y`
	- node保存了在特定输入下的`state`
	- 输入的变化引起输出立即变化
- 举例：![Pasted image 20240512123046.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512123046.png) 
2. <mark style="background: #ADCCFFA6;">摩尔型 </mark>Moore
- 特点
	- 输出<mark style="background: #FFF3A3A6;">仅与当前状态有关</mark>
	- `node`上的`x/y`分别表示当前state与output
	- edge的组合表示使得node状态发生改变的`input`（输入改变state而非output，前者改变后者）
	- 由于输出只与状态有关，且状态是通过时钟信号的xx沿变化的，所以具有滞后、稳定性
- 举例：![Pasted image 20240512123800.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512123800.png)
3. 混合型
	🌰![Pasted image 20240512133631.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512133631.png)
	- 将希望稳定输出的设计为摩尔型，比如状态`00`
---
### 状态图的优化
> 等价状态 Equivalent State
- 原则：
	- 观察状态改变情况，如果对于相同的输入`inputs`，具有完全相同的`output`与下一状态
	- 那么就能将两个状态合并为一个状态，表现为将多个`node`合并为一个`node`
- 举例：
	- 待简化状态图：![Pasted image 20240512124716.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512124716.png)
	- 简化的状态图：![Pasted image 20240512124725.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512124725.png)

# 时序电路设计
## 整体思路
- $n$个触发器最多能够表达$2^n$个二进制状态
- 对于不存在的状态：
	- 画在状态图中用x补充，且卡诺图时当做`d`! 
- ![Pasted image 20240512125600.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512125600.png)
## ①为状态赋值
>![Pasted image 20240512141804.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512141804.png)
>注意此时存在`3`个输入与`3`个输出
### <mark style="background: #FFB86CA6;">最佳原则</mark>：（相邻格雷码）
1. <mark style="background: #FFF3A3A6;">相同输入条件下具有相同次态的现态</mark>
2. 相邻输入条件下同一次态的现态
3. 输出完全相同的现态
4. 最小化状态表中出现次数最多的状态或初始状态
- 第一条最重要
### 🌰
- e.g①![Pasted image 20240512153737.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512153737.png)![Pasted image 20240512153900.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512153900.png)
## ②（利用卡诺图）得到方程
🌰![Pasted image 20240512142930.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512142930.png)![Pasted image 20240512143013.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512143013.png)
	或许可以直接观察状态表得到结果
## ③画出设计图
🌰：![Pasted image 20240512150230.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512150230.png)
	经过格雷码的编码方式优化的结果
## ④Map Technology
>有时，根据题目的要求，只能使用特定的部件。基本等价于工艺映射
>[[obsidian/个人知识库/大一/数字逻辑设计/Chap 3 Combinational Logic Design#工艺映射\|Chap 3 Combinational Logic Design#工艺映射]]
## 等价状态
### 📝情形
对于所有的输入，如果<mark style="background: #FFF3A3A6;">输出均相同</mark>，那么下面的三种情况均为~
1. 下一状态<mark style="background: #ADCCFFA6;">相同</mark>
	 ![Pasted image 20240515142743.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515142743.png)
2. 下一状态<mark style="background: #ADCCFFA6;">交错</mark>
	 ![Pasted image 20240515142835.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515142835.png)
3. 下一状态<mark style="background: #ADCCFFA6;">循环</mark>
	![Pasted image 20240515143243.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515143243.png)
		$S_i$等4个状态相互依赖，构成循环
### ✨**Hidden Table**
>是上述等价状态三种情形的具象化；
- 根据**输出不同**可以直接画X；
- 如果**输出完全相同**
	- 状态也相同，打√
	- 状态依赖于其他状态，填入对应的状态组合
- **可以**对一次优化的结果**继续优化**（可能存在多步）
🌰：![Pasted image 20240515143657.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515143657.png)
## 编码方式
1. 格雷码
2. 独热码 one-hot
	1. 用m位表示m个状态
	2. 组合逻辑电路简单，但是触发器需要更多
	3. 🌰![Pasted image 20240512150750.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512150750.png)
		1. 设计图![Pasted image 20240512152913.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512152913.png)

# 👍状态机 FSM
>**State-Machine Diagram**
- 在状态图的基础上得到
## ❓<mark style="background: #BBFABBA6;">改进的原因</mark>
	状态图需要输入全部的输入和对应的输出，变量较大时，工作量较大
## 📝<mark style="background: #ADCCFFA6;">相关概念</mark>
1. IC :input condition
2. TC:transition condition
	1. 无条件转移 unconditional transition
		> transition的发生无需条件（TC=1恒成立）
	2. 有条件转移 conditional transition
		> 在边上存在1或多个TC；
		> 任意一个TC为`1`时，转移发生
3. OC:output condition
## ✨<mark style="background: #FFB86CA6;">output的四种类型</mark>
1. **Moore Outputs** : 与所有条件均无关，同一state下的输出一致
2. **TCI Outputs** : 
	1. 只跟当前的状态有关；
	2. 在🌰中的`S0`状态下A为`1`则`Y`为`1`(无论A，B的组合使其转向`S1`/`S2`)
3. **TCD Outputs** : 状态的转移需要条件，且满足转移条件时产生对应的输出
4. **TCOD Outputs**: 输出与转换条件和输出条件均有关（斜线将二者连接），二者均为`1`时输出的结果为`1`
### 🌰
![Pasted image 20240514194909.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514194909.png)
### 📝<mark style="background: #FFF3A3A6;">小结</mark>
对于一个**给定的状态**来说：
1. 输出产生的条件应满足下列之一
	1. unconditional(Moore型)
	2. TCI 且 输出条件为真
	3. TCD 且 转移条件transitive condition为真
	4. TOCD 且 TC与OC（转移与输出条件）均为真
## 💥<mark style="background: #BBFABBA6;">正确性检查</mark>
### ①TC
1. 从1个状态向其他任意不同状态的TC的交集为空集（状态转移不能冲突）
2. 从1个状态向其他所有可转移状态的TC的`或`$\cup$为`1` 
### ②OC
1. 同理，某一状态下不同输出的OC交集为空
2. 某一状态下OC的`或`为1（必须存在输出）
### 🌰🌰
![Pasted image 20240514202042.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514202042.png)
## 📝<mark style="background: #ADCCFFA6;">状态表</mark>
- 格式：![Pasted image 20240514202439.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514202439.png)
### 🌰🌰
	![Pasted image 20240514202811.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514202811.png)![Pasted image 20240514203043.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514203043.png)
## 设计FSM
### 📝步骤
1. 确定输入与输出
2. 从系统流程中得到状态图
3. 从状态图中得到状态表
4. 进一步得到`next state`的等式与`output`的等式
# 👍延时
Fan-out会影响延时
Buffer的使用可以减少延时
## 基本概念
>>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap04/#%E8%A7%A6%E5%8F%91%E5%99%A8%E5%BB%B6%E6%97%B6
- 📝<mark style="background: #ADCCFFA6;">相关概念</mark>
	- $t_s$ 采集信号（脉冲或上升沿）前需要稳定的时间
		- 对于Pulse-triggered触发器，为一个脉冲
		- 对于Edge-triggered触发器，由触发器本身决定
	- $t_h$ 在采集完成之后依旧需要输入信号维持不变的一段时间（近乎为0）
	- $t_w$ 时钟脉冲信号的宽度
	- $t_{px}$ 信号采集完成后Q端输出发生改变所需的时间
- 💥<mark style="background: #ADCCFFA6;">额外的时间成分</mark>
	- ![Pasted image 20240514212731.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514212731.png)
		1. 在两个上升沿/下降沿之间的时间
		2. 两个触发器之间所有的组合逻辑的延时
		3. 所有的额外的时间
## 设计要求
>总和小于一个时钟信号的周期
- 🌰图示
	![Pasted image 20240514213128.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514213128.png)
		1. $t_{pd,FF}$表示从上一级触发器的D->Q的转化时间
		2. $t_{pd,COMB}$表示组合逻辑的总延时
		3. $t_s$表示set up建立时间（要求输入保持不变的时间）
- 📝公式：![Pasted image 20240514213355.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240514213355.png)
#### 📝进制转换
1. 1MHz = $10^6$Hz
2. 1s = $10^9$ns
	🌰:
	当Clock frequency = <mark style="background: #FFF3A3A6;">250 MHz</mark>时，$t_p$=$\frac 1 {250M}$s = 4x$10^{-9}$s = <mark style="background: #FFF3A3A6;">4ns</mark>
异步电路 Asynchronization
当异步信号传入电路的时候，前后触发器对于某个信号的解读可能不同，因而产生错误
✅
	1. 将异步信号也接入一个触发器，接受时钟信号的控制；
	2. 对于<mark style="background: #ADCCFFA6;">亚稳态</mark>（D的不稳定变化造成Q的不稳定变化）的现象，可以通过多级采样解决
# 时序电路的verilog
简介：![Pasted image 20240512161129.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512161129.png)
	- 阻塞赋值：立即生效（依次）
	- 非阻塞赋值：右侧是时钟沿信号瞬间的值（同时）
	- 二者不能同时出现在一个`always`中
	- always中的变量只能为`reg`类型
- 🌰：D触发器
	![Pasted image 20240512161637.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512161637.png)
## 🌰
### ①Sequecne Recognizer
![Pasted image 20240512162646.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240512162646.png)
1. 第一个`always`块表示一个D触发器的工作原理
	- 在时钟的上升沿信号到来时更新状态为下一个状态
	- 或者在复位信号`RESET`的作用下将state初始化（此处为`00`也就是A）
2. 第二个`always`块是组合电路的逻辑，是输入改变state的样例，根据状态图得到
	`@(x or state` 表示当`x`或`state`发生改变时执行
3. 第三个`always`块也是组合电路的逻辑，表示根据当前的state得到输出的值
	给出一个x,该状态机将在时钟沿信号的作用下周期更新state
## 补充
### `parametar`
用在参数的定义当中，在module中若 parametar A= 2'b00,则下面的模块中可以用A表示2'b00,当需要改变A的值时，只需要在module中改变即可
>类似于C语言的宏定义
