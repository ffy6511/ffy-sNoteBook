---
{"dg-publish":true,"permalink":"/obsidian///xlab//type-script/","created":"2024-07-01T20:02:47.139+08:00","updated":"2024-09-08T15:25:05.461+08:00"}
---

>key: sk-3d3aa8fdb3f4441eadb2027cc849aed5
## 1.安全性

js作为弱的动态语言，并不对接口作严格的限制（可能会出错）

```js
const arr = [1,2,3];
for(const  index in arr){
	console.log(index + 1);
}
```
>`index`实际上为`string`类型；

TS相比于JS,多了对变量的类型声明，因此可以直接显明地显示JS潜在的错误
```ts
const arr : number =[1,2,3];
```

用`ts-node`来运行，多了编译和类型检查的过程

### 注释+
>在js中用`/**`开头来为希望声明类型的变量进行声明；
>可以作为从js 到 ts的过渡
```js
/**
* @param {number} dx
* @param {string} ch
*/
```

---
## 2.便捷性
代码补全时更加精确（根据类型），在运行之前发现潜在的问题

`interface`可以用来自己定义一个类,告知类型检查以规范
```ts
interface Config{
	x : string;
}
```

问号表示可能存在
```ts
interface config{
	x?: string;
	y?:string;
}
```
	情境：
```ts
const x : string | number = Math.random()<0.5 ? "" : 0;
```

---
## 3.静态分析
对于不可能执行的代码，会用浅色暗示

类型的`&`是将二者相加

大写字母表示类
- `Function`表示函数的类型定义
```ts
func : Funciton;
```
- 但是无法较为精确地定义，因此可以用箭头函数进行签名：
```ts
func: (x:number ,y : number) => number
```

函数与变量没有本质区别，在所有的地方都可以互相转化（嵌套）

---
## 4.重载
用`declare`进行声明
>要求定义和实现分离
```ts
declare function add(x: string, y: string) : string ;
declare function add(x: number, y: number) : number ;

---
//T被称为类型参数
function add <T>(x: T,y : T):T{
...
}

const a : string = add<string>("a","b");
const b : number = add<number>(1,2);

```

# 语法常识
>近似于`JS`
## 基础类型

- 反引号\`来定义多行文本和内嵌表达式
```ts
let words : string = `现在是北京时间 ${ time } .`
```
- 布尔类型
>值为`true` or `false`
```ts
let flag :boolean = true ;
```

- 数组类型
>加上括号或者用数组范型 `Array<number>`

1. 不定长
```ts
let arr : number[ ] = [1,2];

let arr2: Array<number> = [1,2];
```
2. 定长（对数目十分严格）
```ts
let arr : [number,number,number] = [1,2,3];
```
>类型不同时被称为元组
## Record
`pick` 含有
`omit`  不含有
`Partial`  变为可选（均有可能）
`Required` 将原有的变为可选的，是`Partial`的逆运算
`extends`
`...`  提取参数类型

```ts
interface A<T>{
	a: T;
}

const  A<number>{
	a : 3.1415926;
}
```

>type与interface相似
```ts
type O = {
x: string;
y: string;
random: number;
}

type k = keyof O;

type Optional<T> = { [ P in keyof T ] ? : T[p] };//？在遍历时表示可选
```

`ReturnType` 

```ts
function sub( x: number, y:number){
	x-y: number;
}
type X = ReturnType<typeof sub>;//返回 number
```

- never表示不存在可能，undefined表示未定义类型
- `void`表示不关心返回值，`undefined`表示必须为~
```ts
type Callable = (...args: any) => void;
const x: Callable =(a: number) => a;

const r = x(); 
```

## interface
- 规定某一对象所具有的内部变量名及其类型
🌰：
```ts
interface person{
	firstName :  string;
	lastName :  string;
	age : number;
}

const my_classmate : person = {
	firstName : 'JIanMin';
	lastName : 'Luo';
	age : 19;
}
```

- 可以用[ ] 取出对应属性的类型
🌰：
```ts
type A = person[ 'firstName' ];
```

- 可以使用`extends`关键字，继承其他 interface
```ts
interface Shape {
  name: string;
}

interface Circle extends Shape {
  radius: number;
}
```
- 同名接口会**合并**成一个接口
	- 必须保证同名接口中的同 名属性的类型相同
	- 同名接口中的 同名方法可以不同，但是最后出现的优先级最高
		- 例外：同名方法中的参数指定为字符串的，优先级比其他的要更高

## 泛型
### **产生原因**

参数和返回值的类型有密切联系，但是简单的函数声明无法体现出这种关系，因此需要引入泛型；

泛型的特点是带有 **类型参数**

🌰：
```ts
function getFirst<T>(arr:T[]):T {
  return arr[0];
}
```
>getFirst\<number>( [1, 2, 3] )

- 可以省略调用时的类型参数，写作`getFirst ( [1,2,3] ) `
---
### 泛型的写法

- 函数
```ts
function <T> ()
```

## declare
- 作用
	- 描述外部变量的类型 `declare var document;`
	- 不能为其赋值
	- 描述外部函数的类型
