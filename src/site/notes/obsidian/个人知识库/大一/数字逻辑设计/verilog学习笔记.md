---
{"dg-publish":true,"permalink":"/obsidian////verilog/","created":"2024-04-13T10:10:13.551+08:00","updated":"2024-09-08T15:25:05.435+08:00"}
---

> [Verilog 门级建模 | Verilog学习笔记 (cuijiacai.com)](https://verilog.cuijiacai.com/5-1-gate-level-modeling/)
# 激励文件编写规则
## 基本内容要求
1. 设置<mark style="background: #BBFABBA6;">仿真时间</mark>
```verilog
`timescale 1ns / 1ps

module MyMC14495_tb();
```
2. 定义<mark style="background: #BBFABBA6;">输入与输出</mark>信号
- 输入为reg，输出为wire
- 与设计源文件design source的内容相对应
```verilog
 reg a;
 reg b;
 wire c;
```
3. <mark style="background: #BBFABBA6;">实例化</mark>设计源文件
- 第一个名字为设计源文件名，第二个满足命名规则即可
```verilog
MyMC14495 MyMC14495(
	.a([a的实参]),
	.b(_),
	.c(_)
)；
```
这里.a的a是实例化中的形参，实参指的是在设计源文件中的实际名称
4. 添加激励（<mark style="background: #BBFABBA6;">测试条件</mark>）
```verilog
initial
begin
    a = 0;
    b = 0;
    #500;
    a = 0;
    b = 1;
    #500;
    a = 1;
    b = 0;
    #500;
    a = 1;
    b = 1;
    #500;
end
endmodule
```
## 时钟信号
### 定期翻转
```verilog
    initial begin
        clk = 0;
        forever #5 clk = ~clk;  // 每5单位时间翻转，产生10单位时间的周期
    end
```
### 上升沿的处理
```verilog
always @(posedge clk)
	begin
		if( )
			;
		else
			begin
				if()
				;
			end
		end
```
### 时钟分频
- 含义：将一个高频时钟（如50MHz）分频，生成一个周期为1秒的时钟信号。
- 与上述定期翻转的差异
	- - `initial ... forever`块的代码目的是在<mark style="background: #FFF3A3A6;">仿真</mark>环境中生成一个特定周期的时钟信号，用于驱动其他逻辑或测试目的。
	- - 自定义模块的代码目的是通过计数器和时钟分频生成一个低频时钟信号，这通常用于<mark style="background: #FFF3A3A6;">实际硬件设计</mark>中将高频时钟信号分频为更低频的时钟信号。
- 🌰：
```verilog
`timescale 1ns / 1ps

module clk_1s( 
	input clk, 
	output reg clk_1s
);
	 
	reg [31:0] cnt;

	initial begin
		cnt = 32'b0;
	end

	wire[31:0] cnt_next;
	assign cnt_next = cnt + 1'b1;

	always @(posedge clk) begin
		if(cnt<50_000_000)begin
			cnt <= cnt_next;
		end
		else begin
			cnt <= 0;
			clk_1s <= ~clk_1s;
		end
	end

endmodule

```
	注意，`always`块外部的assign语句表示：当右侧表达式的值发生变化时，立刻将其赋值给左侧
	因此，初始化`cnt`之后，`cn_next`立刻被赋值为1;接着，在时钟信号的上升沿到来时，先检查`cnt`的值，如果小于50M(假设时钟信号的频率是50MHz)，则更新`cnt`为`cnt_next`，此时连续赋值语句的assign的右式发生变化，因此`cnt_next`立刻被更新。
	上述过程持续50M次之后，输入的时钟信号clk_1s发生翻转
## 强制赋值
使用`force`与`release`可以实现<mark style="background: #ADCCFFA6;">强制赋值</mark>
## 常见问题
### ❓<mark style="background: #BBFABBA6;">仿真文件的命名</mark>
✅<mark style="background: #FFF3A3A6;">没有强制要求</mark>
1. 前缀tb_或者后缀_tb来区别，表明是测试文件
2. 复杂情况下应当描述具体的功能
3. 避免使用空格、特殊字符与非ASCII字符

# 语法知识
1. <mark style="background: #BBFABBA6;">reg</mark>
>表示寄存器，用来保存值，直到被显式地更新
2. <mark style="background: #BBFABBA6;">非阻塞赋值</mark>  `<=`
> 更新操作在当前的仿真周期结束时发生；其他涉及的运算采用旧值
- 优点：
	- 模拟真实硬件的行为，多个寄存器的更新基本上是在同一时间发生的，遵循**时钟信号**的触发
	- 避免了潜在的竞态条件和优先级问题
- 举例
```verilog
always @(posedge clk) begin
    a <= b;
    b <= c;
    c <= a;
end
```
确保了a,b,c在仿真时间周期结束了分别采用对应的旧值
## 仿真中访问设计文件的值
- 含义：即使在源文件`top`中没有定义对应的output，也可以在仿真文件中访问对应的值（在自定义模块中存在的值）
- 格式🌰(labC)：
```verilog
//用于显示
    initial begin
        $monitor("Time = %t, SW = %b, AN = %b, SEGMENT = %b, hour_tens = %b, hour_ones = %b, min_tens = %b, min_ones = %b", 
                 $time, SW, AN, SEGMENT, uut.hour_tens, uut.hour_ones, uut.min_tens, uut.min_ones);
    end
```
### Generate
- 作用：简化代码书写，用cell的小自定义模块书写大的模块
- 🌰1位全加器+`generate` = 8位全加器
```verilog
module FullAdder1b(
    input A,
    input B,
    input Cin,
    output Sum,
    output Cout
);

    assign Sum = A ^ B ^ Cin;
    assign Cout = (A&B) | (B&Cin) | (A&Cin);

endmodule

module FullAdder8b(
    input [7:0] A,
    input [7:0] B,
    input Cin,
    output [7:0] Sum,
    output Cout
);

    wire[8:0] carry; // [0] for Cin of this module; [1...8] for Cout ports of 8 1-bit-full-adder
    assign carry[0] = Cin;


    genvar i; // Used in generate block
    generate 
        for(i = 0; i < 8; i = i+1) begin
            // instance of 1-bit-full-adder
            FullAdder1b fa1b (.A(A[i]), .B(B[i]), .Cin(carry[i]), .Sum(Sum[i]), .Cout(carry[i+1]));
        end
    endgenerate

    assign Cout = carry[8];

endmodule

```
