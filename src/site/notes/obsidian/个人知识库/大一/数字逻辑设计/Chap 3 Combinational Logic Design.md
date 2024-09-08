---
{"dg-publish":true,"permalink":"/obsidian////chap-3-combinational-logic-design/","created":"2024-04-03T14:44:58.896+08:00","updated":"2024-09-08T15:25:05.416+08:00"}
---

# 延迟相关
## 转换时间
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap03/#%E8%BD%AC%E6%8D%A2%E6%97%B6%E9%97%B4
1. 区别转换时间与延迟时间
	1. 转换时间--一处变化![Pasted image 20240409190536.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409190536.png)
	2. 传播延迟--输入与输出变化的中点![Pasted image 20240409190834.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409190834.png)
		1. 注意：$t_{PHL}$ 指的是<mark style="background: #FFF3A3A6;">输出</mark>（响应）的<mark style="background: #FFF3A3A6;">高到低</mark>
		2. 同理：转换时间$t_r$表示<mark style="background: #FFF3A3A6;">输出</mark>的rise(升高)
2. 与负载的关系
	1. 负载增加，转换时间增加
	2. <mark style="background: #ADCCFFA6;">最大负载</mark>：转换时间不超过**预定的最大值**时的最大负载
## 延迟模型
### 分类
1. 传输延迟(transport delay)：延迟为定值
2. 惯性延迟(inertial delay):引入拒绝时间(rejection time)的延迟
	1. 举例：![Pasted image 20240409191310.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409191310.png)
综合查看
	![Pasted image 20240409191340.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409191340.png)

## 延迟计算
1. 计算电路自身的**固有延迟** 以及 不同负载导致的**额外延迟**
## 延迟带来的问题
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap03/#%E5%BB%B6%E8%BF%9F%E5%B8%A6%E6%9D%A5%E7%9A%84%E9%97%AE%E9%A2%98
# 正逻辑和负逻辑
1. 介绍：
	1. 正逻辑：1为有效信号
	2. 负逻辑：0为有效信号
2. 图示：![Pasted image 20240409193014.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409193014.png)
	1. 右侧带倒三角的是负逻辑门--<mark style="background: #ADCCFFA6;">极性指示器</mark>**(polarity indicator)**
# 工艺映射
## 与非门+非门的实现
1. 步骤
	1. 将**与门**用<mark style="background: #ADCCFFA6;">与非门</mark>替代，并在电路**前进**方向上加上非门
	2. 将**或门**用<mark style="background: #ADCCFFA6;">与非门</mark>替代，并在电路前进的<mark style="background: #FFF3A3A6;">负方向</mark>加上非门
	3. 将相连的两个非门释放
	4. 得到最终的电路
2. 示例：![Pasted image 20240409193425.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409193425.png)

## 或非门+非门的实现
1. 步骤：与门与或门的对换后非门放置方向相反，其他相同
2. 示例：![Pasted image 20240409193529.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409193529.png)
## 正确性的验证
1. 人工逻辑分析(Manual Logic Analysis)
	1.  找到最终电路的真值表或布尔代数式，判断其是否和预期行为一致；
2. 仿真(Simulation)
	1. 在仿真环境中，使用合适的测试输入（激励信号）来测试最终电路（或其网表，可能编写为 HDL），通过观察其响应结果来判断是否实现预期行为；

# 组合逻辑
## 基本逻辑函数
1. 图例：![Pasted image 20240409194312.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409194312.png)
2. 使能函数与三态门的区别
## 基本功能块
1. 分类
	1. 译码器 Decoder
	2. 编码器 Encoder
	3. 多路复用器 Multiplexer (MUX)
	4. 信号分配器 Demultiplexer (DEMUX)
修佬的笔记
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap03/#%E5%9F%BA%E6%9C%AC%E5%8A%9F%E8%83%BD%E5%9D%97
### <mark style="background: #BBFABBA6;">Decoder</mark> 译码器
- 位数由少->多，保证输入能够唯一映射到输出
- $n-m$译码器的目的是从n个变量中产生不超过$2^m$个最小项
	- m<=$2^n$
- <mark style="background: #FF5582A6;">译码器与使能结合</mark>![Pasted image 20240409200108.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409200108.png)
	1. m位输出每个都接入一个EN
	2. 因此n-m译码器对应着加入m个使能函数
	3. 这些使能函数的输入相同
		1. 输入为0时，译码器输出为0；
		2. 输入为1时，译码器<mark style="background: #FFF3A3A6;">有且仅有一个</mark>门输出为1
- 使用译码器实现**二进制加法器**
	1. 真值表：![Pasted image 20240409200741.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409200741.png)
	2. 实现的电路 (3-8译码器):![Pasted image 20240409200809.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409200809.png)
### <mark style="background: #BBFABBA6;">Encoder</mark> 编码器
- 位数由多->少
- 8-2进制编码器的真值表：![Pasted image 20240409201135.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409201135.png)
	1. 输出方程：![Pasted image 20240409201156.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409201156.png)
	2. 限制条件：
			1. 若多个$A_i$同时为真，会存在误解，需要消除不确定性
			2. 增加一个输入优先级-><mark style="background: #ADCCFFA6;"> 优先编码器</mark>
- <mark style="background: #ADCCFFA6;">优先编码器</mark>
	- 真值表：![Pasted image 20240409201704.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240409201704.png)
		1. $D_3$的优先级最高
		2. X对应的变量不在最小值中出现
			1. 可以理解为X为随意，0/1均成立
			2. X不代表任意或者未知
		3.
### <mark style="background: #FFF3A3A6;">多路复用器</mark>
#### 特点
1. 是一个用$n$条<mark style="background: #ADCCFFA6;">选择输入</mark>从$2^n$条输入中**选择一条**的组合电路
#### 举例
<mark style="background: #BBFABBA6;">2-1多路复用器</mark> MUX
1. 真值表![Pasted image 20240410123927.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410123927.png)
2. 可见S为0时选择$I_0$作为输入
3. 图例与常用符号![Pasted image 20240410124013.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410124013.png)
	1. 梯形中较长的边表示输入
	2. 较短的边表示输出
	3. 用到的装置
		1. 1-2译码器
		2. 两个使能电路
		3. 一个二输入或门
<mark style="background: #BBFABBA6;">4-1多路复用器</mark>
1. <mark style="background: #ADCCFFA6;"> 紧凑真值表</mark>![Pasted image 20240410124703.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410124703.png)
	1. $00I_0$ 表示当$S_1$与$S_0$分别取0时，输入的结果Y就是$I_0$
	2. 这也恰好是因为n条选择输入的二进制的值有$2^n$个，可对应$2^n$个输入变量
2. 装置图![Pasted image 20240410125248.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410125248.png)
	1. <mark style="background: #FFF3A3A6;"> 4-2的解读</mark>
		4表示与门的数量
		2表示**从与门输入**的变量数
	2. 所需：
		1. 2-4译码器
		2. 四个用作使能电路的与门
		3. 一个四输入的或门
	3. 用<mark style="background: #FFB86CA6;">三态门</mark>可以减少门输入成本![Pasted image 20240412144906.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412144906.png)
#### 设计
>1. 译码器产生选择输入的最小项
>2. 与或门提供选择电路
>3. $I_1$作为使能信息：若~为1则最小项$m_1$连向或门；否则为0
<mark style="background: #BBFABBA6;">四重4-1多路复用器</mark>
1. 每个输入信息都是一个四位的向量->输出也是一个四位的向量
2. 图例：![Pasted image 20240410130322.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410130322.png)
<mark style="background: #BBFABBA6;">一位加法器</mark>
![Pasted image 20240410144125.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410144125.png)
如果让X Y作为选择信号，Z作为输入信号
1. 当XY为00时，C为0，因为Z无论为0/1，C均为0
2. 当XY为10时，C为Z


## 加法器
### <mark style="background: #BBFABBA6;">半加器</mark>
- 含义:产生两位二进制数的和的电路
- 输入：加数 和 被加数
- 输出：S（和）与 C（进位）
- 真值表：![Pasted image 20240412151444.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412151444.png)![Pasted image 20240412151454.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412151454.png)
- 真值表->布尔表达式->逻辑电路图![Pasted image 20240412151531.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412151531.png)
### <mark style="background: #BBFABBA6;">全加器</mark>
- 含义：实现三个一位的二进制数相加的组合逻辑电路
- 输入：相加的有效位X，Y 以及 来自前一个低位产生的进位
- 输出：S（和）与 C（进位）
- 真值表：![Pasted image 20240412151845.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412151845.png)
- 布偶表达式：![Pasted image 20240412151902.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412151902.png)
	- 用<mark style="background: #FFF3A3A6;">异或</mark>形式转换![Pasted image 20240412152049.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412152049.png)
- 异或形式下的电路逻辑图![Pasted image 20240412152108.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412152108.png)
### <mark style="background: #BBFABBA6;">二进制行波进位加法器</mark>
- 别称：并行加法器 
- 特点：由并联的全加器构成，最低有效位的进位输入置为0
- 举例：<mark style="background: #ADCCFFA6;">4位行波进位加法器</mark>![Pasted image 20240412152505.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412152505.png)
## 二进制减法
对于<mark style="background: #BBFABBA6;">负数</mark>而言（正数的反码和补码就是本身）
1. **反码**：将0/1对换得到
2. **补码**：将反码+1
3. 其他进制的反码计算
	1. ？？？![Pasted image 20240412153107.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412153107.png)
### 传统的二进制减法
1. 所需硬件：
	1. 加法器
	2. 减法器：对初始结果进行校正
	3. 二进制补码器：对结果校正
2. 多路复用器的S端
	1. 置为0：选择加法器的输出作为结果--加法
	2. 置为1：选择补码器的输出作为结果--减法
3. 复杂的加减法器的电路图![Pasted image 20240412154126.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412154126.png)
	正因为其复杂性，我们考虑引入补码来简化硬件
### 采用补码的二进制减法
>共享加法和减法的逻辑来简化硬件
1. 原理：![Pasted image 20240412153803.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412153803.png)
2. 举例：![Pasted image 20240412153817.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412153817.png)
## 二进制加减法器
### 装置构成
1. 加法器
2. 补码器
### 不同的设计
1. 利用<mark style="background: #BBFABBA6;">全加器与非门实现</mark>A$-$B![Pasted image 20240412152505.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412152505.png)
	修改：
	1. 将$B_i$输入之前取反（加入反相器）
	2. 将$C_0$从全加器的0置为1
	3. 从此得到A加上B的补码的结果
	结果：
	1. A>=B：实现了A$-$B
	2. A<B:结果为B$-$A的补码
2. 利用<mark style="background: #BBFABBA6;">异或门与S选择端</mark>得到加减法器
	1. 电路图![Pasted image 20240412154946.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412154946.png)
	2. <mark style="background: #FFF3A3A6;">S端的选择功能</mark>
		1. 由于异或的特性：与0异或的值为本身；与1异或的值等于取反
		2. S为1$->$ B取反, $C_0$（S）为1 $->$实现减法器
		3. S为0，B为本身，$C_0$为0，因此为加法器
## 有符号的二进制数
### 对负数的两种表示方法
1. 符号-数值表示法
	将对应的正数的符号位置为1，其余不变
2. **符号-二进制补码表示法**（更加常用）
	将对应的正数取其反码+1（补码）得到，这里的<mark style="background: #FFF3A3A6;">取反包括符号位</mark>
- 举例：![Pasted image 20240412155924.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240412155924.png)
### **利用补码表示法实现简化的加减运算**
由于n位二进制数的加减法结果还是n位，因此这个n位数加减$2^n$+$x$（x较小）等价于加减了$x$本身。上述特点等价于 (x+y) mod $2^n$ = x+y
1. **加法**：
	1. <mark style="background: #ADCCFFA6;">步骤</mark>
		1. 执行包括符号位在内的加法；
		2. <mark style="background: #BBFABBA6;">丢弃</mark>符号位产生的<mark style="background: #BBFABBA6;">进位</mark>；
		3. 如果结果是负数，将自动呈补码形式
	2. <mark style="background: #ADCCFFA6;">解释</mark>
		1.  可能发生符号位进位的情形
			1. 1xxx + 1xxx 负数相加
				1. 形式上：由于补码形式表示的负数一定是11xxx的形式（10xxx的1将不再是符号位），因此11xx+11xx的结果是1xxxx。因此，舍弃符号位进位的操作在形式上是合理的
				2. 值：我们需要确保`丢弃进位`的操作不会影响我们所求的值的结果。
			2. 1xxx + 0xxx 正负相加
	3. <mark style="background: #ADCCFFA6;">举例</mark>![Pasted image 20240424172147.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424172147.png)
2. **减法**：
	1. <mark style="background: #ADCCFFA6;">步骤</mark>
		1. 对减数取补再与被减数相加（均包括符号位），后续与加法相同!
	2. <mark style="background: #ADCCFFA6;">举例</mark>![Pasted image 20240424172010.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240424172010.png)
	解释图：![f134c08dc5a71639324b7294a60318f.jpg](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/f134c08dc5a71639324b7294a60318f.jpg)
# 可编程技术
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap05/#%E5%8F%AF%E7%BC%96%E7%A8%8B%E6%8A%80%E6%9C%AF
## 分类
### 永久编程技术
>出厂后经过一次编程，便永久成型(不可修改)
1.  Mask programming 掩模编程
2. Fuse 保险丝
3. Anti-fuse   反保险丝
### 可重编程技术
>允许重复进行编程
1. Volatile 内存
	断电后编程信息会丢失
2. Non-Volatile 
## 常见的可编程技术
### <mark style="background: #BBFABBA6;">ROM</mark>
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap05/#rom
- Read Only Memory 只读内存
- 组合电路
	1. AND门个数固定
	2. OR门的个数可以改变
- 功能
	将固定的地址输出其中memory的信息
	具有“只读”的特征
- <mark style="background: #BBFABBA6;">举例</mark>![Pasted image 20240410141518.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410141518.png)
	1. N个输入经过译码器得到$2^N$个最小项
	2. 通过或门得到M个输出
	3. 这个ROM为32x8,其中32表示存储地址（行数）；8表示位宽（输出个数）
- <mark style="background: #FFF3A3A6;">ROM结合使能信号的扩展</mark>
{ #7d8ddf}

	- 用使能信号选择并行的输出芯片对以及需要的芯片行
	- 每次选择其中一行，看似输出一行，实际上地址是所有行的行数（<mark style="background: #FFF3A3A6;">选择</mark>）
	- <mark style="background: #BBFABBA6;">举例</mark>：![60f2e2c8b64782774c69f1538b3a0a6.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/60f2e2c8b64782774c69f1538b3a0a6.png)![1ad0567b071f46f9660d35bff471338.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/1ad0567b071f46f9660d35bff471338.png)
- <mark style="background: #ADCCFFA6;">设计</mark>
>3位二进制的平方![Pasted image 20240410144624.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410144624.png)
1. 由图，$B_0$=$A_0$，$B_1$=0
2. 因此，可以设计8X4bit的ROM![Pasted image 20240410144735.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410144735.png)
### <mark style="background: #BBFABBA6;">PALⓇ</mark>
>https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap05/#pal
- Programmable Array Logic 可编程阵列逻辑
- 组合电路
	与ROM相反，AND可变
- 不需要像 ROM 那样列出所有最小项
	- 可以优化
- <mark style="background: #BBFABBA6;">举例</mark>![Pasted image 20240410141854.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410141854.png)
	1. OR门是固定的
	2. AND门可以通过在线路中增添<mark style="background: #ADCCFFA6;"> X </mark> 改变
	3. 注意OR门<mark style="background: #FFF3A3A6;">输出的结果可以返回作为输入</mark> 如$W$！
		1. 因此可以补充一些逻辑

### <mark style="background: #BBFABBA6;">PLA</mark>
https://note.isshikih.top/cour_note/D2QD_DigitalDesign/Chap05/#pla
Programmable Logic Array 可编程逻辑阵列
- 组合电路
	AND与OR门<mark style="background: #FFF3A3A6;">都可以改变</mark>
	P用<mark style="background: #ADCCFFA6;">可编程的AND阵列</mark>来代替ROM的译码器
	输出的时候再做一次异或来补充逻辑
- <mark style="background: #BBFABBA6;">举例</mark>![Pasted image 20240410142536.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410142536.png)
	1. F1与F2<mark style="background: #FFF3A3A6;">可</mark>后期<mark style="background: #FFF3A3A6;">编程</mark>决定是否<mark style="background: #ADCCFFA6;">取反</mark>->丰富了表达的逻辑
		1. 比如F1一个输入为0，根据**异或的原理**，F1等于另一个输入的逻辑
		2. 再如F2一个输入为1，根据**异或原理**，F2为另一个输入的取反
#### 根据门数进行设计
1. 步骤：
	1. 卡诺图简化最小项
	2. （如果变量数依旧多于门）<mark style="background: #FFF3A3A6;">取反</mark>观察
		1. 指的是将卡诺图中的0看做1，其他步骤不变得到的SOP
2. 举例：
	1. F1(A,B,C) =Σm(0,1,2,4)     F2(A,B,C)=Σm(0,5,6,7)
	2. 画出卡诺图得到最小项![Pasted image 20240410150023.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410150023.png)
	3. 观察得到，$\bar{F_1}$ 与 $F_2$ 恰好 满足4个变量
	4. 由此得到![Pasted image 20240410150231.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240410150231.png)
### <mark style="background: #BBFABBA6;">FPGA</mark>
- Field-Programmable Gate Array