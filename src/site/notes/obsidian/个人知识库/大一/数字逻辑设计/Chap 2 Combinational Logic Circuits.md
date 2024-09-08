---
{"dg-publish":true,"permalink":"/obsidian////chap-2-combinational-logic-circuits/","created":"2024-04-09T18:13:19.521+08:00","updated":"2024-09-08T15:25:05.419+08:00"}
---

# 布尔代数运算
![Pasted image 20240409181549.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409181549.png)
	优先级：逆与或（双单）
	<mark style="background: #FFF3A3A6;">重要</mark>：15
- 更多的公式![Pasted image 20240409181747.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409181747.png)
# 对偶法则
- 含义
	将所有的 **与** 和 **或** 对调得到的式子
- 关键
	需要保证参与运算的结构不能变；
	e.g. 
		A⋅B 会被对偶为 (A+B) 以保证运算顺序
# 互补函数 *Complement of a Function*
- **含义**
	1. 将它的 <mark style="background: #ADCCFFA6;">对偶函数</mark> 中每一个 变量 都取反得到的函数
	2. 恰好等于**原函数的非**
- 举例
	-  ![Pasted image 20240409182400.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409182400.png)
# 替代法则 *Subtitution Rules*
- **含义**
	将一个等式中**所有的**某个变量都替换为同一个表达式，则等式依然成立
- **举例**![Pasted image 20240409182617.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409182617.png)
# ！标准形式与规范形式
概述：![Pasted image 20240409183357.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409183357.png)
1. 最小项之和 SOM：有1出1
2. 最大项之积 POM：有0出0
>建议参看修佬笔记与个人之前的题集：
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap02/#%E6%A0%87%E5%87%86%E5%BD%A2%E5%BC%8F%E4%B8%8E%E8%A7%84%E8%8C%83%E5%BD%A2%E5%BC%8F
>>练习也值得一看
## <mark style="background: #BBFABBA6;">两种化简方向</mark>
### <mark style="background: #FFF3A3A6;">给出POS</mark>
1. 要求化简成为SOP
	1. 将$F$取反
	2. 将取反之后的最小项用1填入卡诺图
	3. 在目前的卡诺图里对0进行处理（当做SOP）
	4. 最后得到的SOP就是所求
2. 要求化简成为POS
	1. 将$F$取反
	2. 将取反之后的最小项用1填入卡诺图
	3. 在目前的卡诺图里对1进行处理
	4. 将得到的SOP取反得到所求的POS
<mark style="background: #FFB86CA6;">总结</mark>：
>给出POS时，不管化简方向如何，都需要先取反并将取反的SOP填图；
>对0处理+取反恰好满足了$F$原来的性质；两次取反同理；
>如果要<mark style="background: #BBFABBA6;">从POS</mark>
>	得<mark style="background: #ADCCFFA6;">到SOP</mark>，取反后对0处理即可；
>	如果要<mark style="background: #ADCCFFA6;">得到POS</mark>，意味着用卡诺图化简之后的结果还需要取反，因此第一步对<mark style="background: #FFF3A3A6;">取反后的1</mark>处理，再将结果SOM形式取反

举例：![Pasted image 20240417082848.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240417082848.png)
### <mark style="background: #FFF3A3A6;">给出SOP</mark>
1. 要求化简成为POS
	1. 填图
	2. 对**0**处理
	3. 取**反**
2. 要求化简成为SOP
	1. 填图
	2. 对1处理
# 异或
![Pasted image 20240615165825.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240615165825.png)
# 电路实现与优化
## 按门输入计
1. $F$ = $\bar{A}B$+$\bar{A}C$
	特别注意这种情况，非门<mark style="background: #FF5582A6;">只需要记一个</mark>
	>因为我们实际上是把非了以后的东西当作了一个字面量在用
2. 复杂逻辑门的计算![Pasted image 20240409184534.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409184534.png)
	Ans:![Pasted image 20240409184547.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409184547.png)
## 卡诺图
>修佬的笔记:https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap02/#%E5%8D%A1%E8%AF%BA%E5%9B%BE
1. 由~的到SOM是我们熟悉的
2. 由卡诺图求解POM需要利用取反
	1. 将卡诺图中的0/1对调
	2. 着眼于SOM进行优化（或者舍去1.直接对0操作）
	3. 将最终的结果整体取反
	e.g.![Pasted image 20240409185156.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409185156.png)

## 蕴含项
1. ~是相对于某一处1来说的
2. 因此 对于不同的1，主蕴含项的规模可以不同
# 经典组合电路
## 三态门
1. 特征：除了输入和输出，还有使能端(enable)
2. 真值情况：![Pasted image 20240409185542.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409185542.png)
3. 图示：![Pasted image 20240409185555.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409185555.png)
4. 作用：避免了0/1状态电路形成电流的逆流
## 复杂门
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap02/#%E5%A4%8D%E6%9D%82%E9%97%A8