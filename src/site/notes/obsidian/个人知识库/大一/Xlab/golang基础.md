---
{"dg-publish":true,"permalink":"/obsidian///xlab/golang/","created":"2024-05-24T16:01:11.385+08:00","updated":"2024-09-08T15:25:05.473+08:00"}
---

>https://tour.go-zh.org/list

# 基本语法
1. 函数可以返回任意数量的返回值
2. 声明变量时，类型在名称的后面；多个类型相同时，除了最后一个外均可省略，之间用`,`相隔
3. 函数的返回值是写在<mark style="background: #FFF3A3A6;">传参的后面</mark>的：
```go
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```
	此处表示返回x,y
与下文等价：
```go
var x,y int //先声明变量，注意类型与名称之间不存在逗号

func split(sum int) (int,int) {
	x = sum * 4 / 9
	y = sum - x
	return x,y
}

func main() {
	fmt.Println(split(10))
}
```
4. 变量初始化时如果给出了值，可以忽略类型的说明 (自动识别)
5. 只能在函数内部用`:=`对变量进行赋值
6. 没有明确初始化的变量声明会被赋予对应类型的 **零值**。
	- 数值类型为 `0`，
	- 布尔类型为 `false`，
	- 字符串为 `""`（空字符串）
7. 表达式 `T(v)` 将值 `v` 转换为类型 `T`。
8. 声明变量却不指定类型也是被允许的，此时系统会根据右值为左值赋予类型
🌰:
```go
i := 42           // int
```
9. 常量的声明与变量类似，只不过使用 `const` 关键字。
	常量可以是字符、字符串、布尔值或数值。
	常量不能用 `:=` 语法声明。
## 流程控制
1. Go 的 `for` 语句后面的三个构成部分外没有小括号， 大括号 `{ }` 则是必须的。
	1. `for`也是一样，没有`()`
	2. 二者均可以在条件表达式前执行一个简短语句。其作用域在自身以内
	🌰`	switch os := runtime.GOOS; os {`  **用分号分隔**
2.  for 是 Go 中的「while」，可以去掉分号
```go
for sum < 1000 {
		sum += sum
	}
```
3. 在函数中常用的赋值方式是 `z := 1.0` 
4. 为每个 `case` 后面自动添加了所需的 `break` 语句。
	1. 除非以 `fallthrough` 语句结束，否则分支会自动终止。
	2. `case` <mark style="background: #FFF3A3A6;">无需为常量</mark>，且取值<mark style="background: #FFF3A3A6;">不限于整数</mark>
5. 无条件的 `switch` 同 `switch true` 一样。将一长串 `if-then-else` 写得更加清晰。
```go
t := time.Now()
	switch {
	case t.Hour() < 12:
		fmt.Println("早上好！")
	case t.Hour() < 17:
		fmt.Println("下午好！")
	default:
		fmt.Println("晚上好！")
	}
```
6. <mark style="background: #ADCCFFA6;">defer</mark> 语句会将函数推迟到外层函数返回之后执行
```go
package main

import "fmt"

func main() {
	defer fmt.Println("world")

	fmt.Println("hello")
}
```
	hello
	world
7. 进一步说，defer推迟执行的函数是被放入了一个栈，也就是最开始defer的函数最后执行
8. Go 没有指针运算。
9. 结构体的成员访问
	1. 也可以用`.`来访问
```go
type Vertex struct {   //此处的顺序也有所不同
	X int
	Y int
}
func main() {
	v := Vertex{1, 2}
	v.X = 4
	fmt.Println(v.X)
}
```
     2. 使用隐式解引用，直接写 `p.X` 就可以用指向结构体的指针p对其成员X进行访问

- <mark style="background: #BBFABBA6;">切片</mark>
1. `[]T` 表示一个元素类型为 `T` 的切片
2. 选出一个半闭半开区间，包括第一个元素，但排除最后一个元素。
🌰从数组中获得切片：
```go
package main

import "fmt"

func main() {
	primes := [6]int{2, 3, 5, 7, 11, 13}

	var s []int = primes[1:4]
	fmt.Println(s)
}
```
	[3 5 7]
3. 切片类似于指针，自身的改变会影响对应的数组
4. 切片的上下界：默认为原来的数组关系。注意多次切片之间的操作<mark style="background: #FFF3A3A6;">继承</mark>
```go
package main

import "fmt"

func main() {
	s := []int{2, 3, 5, 7, 11, 13}

	s = s[1:4]
	fmt.Println(s)

	s = s[:2]
	fmt.Println(s)

	s = s[1:]
	fmt.Println(s)
}
```
	[3 5 7]
	[3 5]
	[5]
特别是最后的`[5]` ! 可见是在原来的s的基础上不断改变得到
5. 切片具有长度和容量属性，分别可以用len() 与 cap()得到
```go
package main

import "fmt"

func main() {
	s := []int{2, 3, 5, 7, 11, 13}
	printSlice(s)

	// 截取切片使其长度为 0
	s = s[:0]
	printSlice(s)

	// 扩展其长度
	s = s[:4]
	printSlice(s)

	// 舍弃前两个值
	s = s[2:]
	printSlice(s)
}

func printSlice(s []int) {
	fmt.Printf("len=%d cap=%d %v\n", len(s), cap(s), s)
}
```
	❓重新切片

<mark style="background: #BBFABBA6;">make 创建切片</mark>
- `make` 函数会分配一个元素为零值的数组并返回一个引用了它的切片：
```go
a := make([]int, 5)  // len(a)=5
```

- 🌰指定容量
```go
b := make([]int, 0, 5) // len(b)=0, cap(b)=5
```

- 切片可以包含任何类型，也包括其他切片。
- 切片的**追加**：`s = append(s, 0)` 表示向s(int类型)的(空)切片追加一个`0`到末尾

<mark style="background: #BBFABBA6;">range遍历切片</mark>
- 返回值：有两个，分别是对应的元素下标以及对应元素(的副本)
```go
package main

import "fmt"

var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}

func main() {
	for i, v := range pow {  //用两个变量来获取range pow的返回值
		fmt.Printf("2**%d = %d\n", i, v)
	}
}
```
	2**0 = 1
	2**1 = 2
	2**2 = 4
	2**3 = 8

- ❓如何忽视下标或值的返回值
	- 赋予 `_`
🌰：只需要索引
```go
for i := range pow
```
或者
```go
for i, _ := range pow
```
---
1. 映射中插入或修改元素
	1. delete(m, key)
2. 检验映射中的某个键是否存在：
	1. elem, ok = m\[key] 
		若 `key` 在 `m` 中，`ok` 为 `true` ；否则，`ok` 为 `false`。
		若 `key` 不在映射中，则 `elem` 是该映射元素类型的<mark style="background: #FFF3A3A6;">零值</mark>。
3. 函数作为函数的参数：
	1. 外层函数对传参函数的声明涉及内层函数的输入与输出类型的声明，以及自身的输出
🌰直角三角形的斜边：
```go
package main

import (
	"fmt"
	"math"
)

func compute(fn func(float64, float64) float64) float64 {
	return fn(3, 4)
}

func main() {
	hypot := func(x, y float64) float64 {
		return math.Sqrt(x*x + y*y)
	}
	fmt.Println(hypot(5, 12))

	fmt.Println(compute(hypot))
	fmt.Println(compute(math.Pow))
}
```
4.  选择值或指针作为接收者
	1. 原因：能够修改其接收者指向的值；更加高效。
5. 类型断言：判断一个接口值是否定义了特定的类型
	🌰`t,ok :=i.(T)`：`T`用一个具体的类型名称代替
		如果`i`保存了`T`类型的值，`t`将得到`i`本身，`ok`为`true` ；
		否则，`ok`为`false`，且`t`将是`T`类型对应的零值
🌰：
```go
	var i interface{} = "hello"

	s := i.(string)
	fmt.Println(s) //hello
```
---
1. 类型选择：与`switch`相似
```go
func do(i interface{}) {
	switch v := i.(type) {//将类型断言的T改为关键字type
	case int:
		fmt.Printf("二倍的 %v 是 %v\n", v, v*2)
	case string:
		fmt.Printf("%q 长度为 %v 字节\n", v, len(v))
	default:
		fmt.Printf("我不知道类型 %T!\n", v)
	}
}
```
1. 空接口可以保存任意类型的值
	1. 🌰：`var i interface{} = "hello"` 
2. Readers
	1. 方法：`func (T) Read(b []byte) (n int, err error)`
		🌰:`n, err := r.Read(b)`
		📝 用数据填充给定的字节切片并返回填充的字节数和错误值。
3. 图像
	1. 