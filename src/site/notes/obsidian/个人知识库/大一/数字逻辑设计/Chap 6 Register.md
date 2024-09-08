---
{"dg-publish":true,"permalink":"/obsidian////chap-6-register/","created":"2024-05-15T15:21:58.142+08:00","updated":"2024-09-08T15:25:05.422+08:00"}
---

# 1.寄存器设计
## 📝相关概念
1. 寄存器：具有一定<mark style="background: #ADCCFFA6;">操作</mark>功能的触发器
	1. Save :
	2. Load :为1时允许时钟信号对触发器起作用
## ✨设计范式
- 原因：
	当输入的规模增大时，状态图/表的绘制会变得十分复杂
- 方法
	1. 用事先设计好的组合逻辑
	2. 用小规模、同思路的寄存器设计进行替换
## 🌰设计思路
1. **with clock gating**:![Pasted image 20240515153831.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515153831.png)
# 2. 寄存器传输操作
- 含义：存储信息在寄存器之间转移时可以处理、变化
- 基本条件：
	- 寄存器
	- 操作内容
		- 基本~包含：load, count, shift, add, 按位或等 它们被称为<mark style="background: #ADCCFFA6;">微操作</mark>
	- 操作发生的控制条件
# 3.设计语言（表示）
## 🌰：
![Pasted image 20240515155010.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240515155010.png)
1. 用字母/数字表示寄存器
2. (digits) 来表示寄存器的比特
3. $\leftarrow$表示数据的传输方向
4. `,` 逗号来分隔平行操作（同时发生）
5. \[ ] 表示存储信息的位置
# 4. 条件传输
- 简单的条件传输：
🌰  K1:(R2$\leftarrow$R1) 表示当`Load`信号K1为1时，可以将R1的值传输给R2（等待时钟信号）
	![Pasted image 20240522120547.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522120547.png)
## 条件传输表达式
- 原理：与简单的控制一致，当整体为1时右侧的信息传输可以发生；可以比较复杂
- 🌰控制加减法：![Pasted image 20240522120800.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522120800.png)
# 5. 操作
- 📝操作符号：![Pasted image 20240522121020.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522121020.png)
	- 注意区分此处的加法是`+`,而非或
	- 同时区分信息传输的判断`+`与操作的`+`：
		🌰 $(K_1+K_2):R_1\leftarrow R_2+R_3$ ,第一个`+`是<mark style="background: #FFF3A3A6;">逻辑判断</mark>；第二个`+`是<mark style="background: #FFF3A3A6;">值的计算</mark>
## ✨操作补充
 ### **<mark style="background: #BBFABBA6;">shift</mark>** 
 🌰:![Pasted image 20240522121857.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522121857.png)
	 `sl` 表示左移，右侧缺口补`0`;
	 `sr` 表示右移，左侧缺口补`0`
## 📝操作的语法
![Pasted image 20240522122255.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522122255.png)
	主要掌握Verilog；
	verilog当中<mark style="background: #FFF3A3A6;">无法直接做除/乘法</mark>，需要自己设计
# 6.寄存器传输结构
## 三态门bus
- 要求：
	- 每次都只能有一个三态门打开
---
# 7. Colunter 计数器
- 分类：
	- Ripple Counters
## Ripple Counter 行波计数器
1. 基本原型：![Pasted image 20240522133824.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522133824.png)
	时钟信号使上方的FF不断翻转，并当A:1->0（发生进位）时，$FF_B$得到时钟上升沿信号，自身翻转一次。因此，A的变化频率是B的两倍。
2. 存在问题：具有延时![Pasted image 20240522134122.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522134122.png)
	逐级具有延时；n位时延时最久为n $t_{PH}$ 
## 同步计数器
>在行波计数器的`延时`问题的启发下，考虑用一个clock信号来控制所有的触发器
![Pasted image 20240522145812.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522145812.png)
## 同步载入
>目的：将计数器的当前值设置为希望的值
![Pasted image 20240522145915.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522145915.png)
❓如何实现设置（`load`与`count`的组合：）
	`10`--加载：此时每个或门的上方的与门接受到了来自$D_i$与`load`的信号，为`1`，因此可以根据设置的$D_i$的组合来改变当前的数值
	`01`--计数；
	`00`锁存
✨CO表示计数的**进位** 
## 类似的应用：串并移位器
- 📝![Pasted image 20240615192358.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240615192358.png)
- 当`Shift`为`0`时，每个组合的第二个与门接受到的信号是`Shift'`,`Load`,$D_i$ `Load`为`1`时，将并行载入数据；
- `Shift`的优先级较高，其为`1`时，第二个与门的结果一定是`0`，因此为串入，`Serial`的数据传入第一个寄存器，并且每个寄存器的输出传入下一个寄存器的第一个与门的输入；
- 对于第三个与门：`Shift'`,`Load'`,$D_i$表示当`shift``load`为00时，保持不变
- ![Pasted image 20240615192849.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240615192849.png)
	- 注意此处确实为左移，因为低位的输出传给了高位的输入
## 取模计数器
🌰Counting Modulo 7:
	同步载入的应用![Pasted image 20240522142005.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522142005.png)
	❓为什么可以实现
		✅当`Q2Q1`为`11`也就是数据为`6`时，与门输入`load`为1，这使得下一次时钟沿信号来临的时候，将D0~D3的输入（均为`0`）load(赋值)给Q3~Q0
		✨因此，我们可以发现
			1. $D_i$可以控制数值的下确界！
			2. 而$Q_i$的与门可以控制模的上确界！
			这也得出了下面的🌰——
🌰从9开始的modulo 15:
	![Pasted image 20240522144500.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240522144500.png)
	- 此处`reset`不再使得数据从0开始，而是初始值
# 8. Register Cell Design
>寄存器单元设计
## 基本步骤
1. 确定系统的行为(specification)；
2. 定义外部的输入、输出，以及控制单元(control unit)和数据通路(datapath)需要的寄存器；
3. 设计状态机；
4. 定义内部的控制信号、状态信号；
    - 用这些信号来分配输出条件(output condition)、输出行为(output actions)等，包括寄存器传输(register transfer)（个人理解是设计内部信号来进一步设计状态机，包括设计 TC、OC、OA 等）；
5. 绘制框图(block diagram)；
6. 设计控制单元和数据通路的寄存器传输逻辑(register transfer logic)；
7. 设计控制单元逻辑(control unit logic)；
8. 验证正确性；
