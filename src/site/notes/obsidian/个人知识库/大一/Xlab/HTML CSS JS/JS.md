---
{"dg-publish":true,"permalink":"/obsidian///xlab/html-css-js/js/","created":"2024-05-17T17:22:37.187+08:00","updated":"2024-09-08T15:25:05.445+08:00"}
---

- 资源推荐
	- 在线代码与可视化
	>[codesandbox.io/code-in-sandboxes](https://codesandbox.io/code-in-sandboxes)
	- 菜鸟编程
	[JavaScript 用法 | 菜鸟教程 (runoob.com)](https://www.runoob.com/js/js-howto.html)
	- 错误参考
	>https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Errors#%E9%94%99%E8%AF%AF%E5%88%97%E8%A1%A8
	
# 核心知识点
## 整体总结
🌰answers from gpt4o:
1. **数据类型（String, Array, Map, Set, Object, JSON）的定义与方法**：
   
   - **String**：字符串，定义方式有**单引号**、**双引号**或**反引号**包裹。
     
     ```javascript
     let str = "Hello, World!";
     console.log(str.length); // 获取字符串长度
     console.log(str.toUpperCase()); // 转换为大写
     ```
   - **Array**：数组，使用**方括号**定义。
     
     ```javascript
     let arr = [1, 2, 3];
     arr.push(4); // 添加元素
     console.log(arr.length); // 获取数组长度
     ```
   - **Map**：键值对集合，使用`new Map()`定义。
     ```javascript
     let map = new Map();
     map.set('key', 'value'); // 设置键值对
     console.log(map.get('key')); // 获取值
     ```
   - **Set**：值的集合，使用`new Set()`定义。
     ```javascript
     let set = new Set();
     set.add(1); // 添加值
     console.log(set.has(1)); // 检查是否存在
     ```
   - **Object**：对象，使用花括号定义。
     ```javascript
     let obj = { name: 'Alice', age: 25 };
     console.log(obj.name); // 访问属性
     obj.name = 'Bob'; // 修改属性
     ```
   - **JSON**：JavaScript对象表示法，用于数据交换。
     ```javascript
     let jsonString = '{"name":"Alice","age":25}';
     let jsonObject = JSON.parse(jsonString); // 解析JSON字符串为对象
     console.log(JSON.stringify(jsonObject)); // 将对象转换为JSON字符串
     ```
   
2. **null 和 undefined**：
   - `null`：表示一个空值，主动赋予。
     ```javascript
     let a = null;
     console.log(a); // null
     ```
   - `undefined`：表示未定义的值，变量未赋值时默认是`undefined`。
     ```javascript
     let b;
     console.log(b); // undefined
     ```

3. **浅拷贝与深拷贝**：
   - **浅拷贝**：复制对象的引用，而非对象本身。
     ```javascript
     let obj1 = { name: 'Alice' };
     let obj2 = Object.assign({}, obj1); // 浅拷贝
     ```
   - **深拷贝**：完全复制对象，两个对象互不影响。
     ```javascript
     let obj3 = { name: 'Alice', details: { age: 25 } };
     let obj4 = JSON.parse(JSON.stringify(obj3)); // 深拷贝
     ```

4. **箭头函数**：
   - 简洁的函数定义方式，不绑定`this`。
     ```javascript
     const add = (a, b) => a + b;
     console.log(add(2, 3)); // 5
     ```

5. **函数闭包**：
   - 闭包是指有权访问另一个函数作用域中变量的函数。
     ```javascript
     function outer() {
       let count = 0;
       return function inner() {
         count++;
         console.log(count);
       };
     }
     const counter = outer();
     counter(); // 1
     counter(); // 2
     ```

6. **回调函数**：
   - 一个作为参数传递给另一个函数的函数，在某个时间点调用。
     ```javascript
     function greet(name, callback) {
       console.log('Hello ' + name);
       callback();
     }
     greet('Alice', function() {
       console.log('This is a callback function.');
     });
     ```

7. **const / let / var 的区别**：
   - `const`：定义常量，不能重新赋值。
     ```javascript
     const PI = 3.14;
     // PI = 3.15; // 错误
     ```
   - `let`：定义块作用域变量，可以重新赋值。
     ```javascript
     let x = 10;
     x = 20; // 正确
     ```
   - `var`：定义函数作用域变量，可以重新赋值，存在变量提升。
     
     ```javascript
     var y = 10;
     y = 20; // 正确
     ```
   
8. **promise**：
   - 处理异步操作的对象。
     ```javascript
     let promise = new Promise((resolve, reject) => {
       let success = true;
       if (success) {
         resolve('Success!');
       } else {
         reject('Error!');
       }
     });
     promise.then(message => {
       console.log(message);
     }).catch(error => {
       console.log(error);
     });
     ```

9. **async / await**：
   - 用于处理异步函数，使代码看起来像同步代码。
     ```javascript
     async function fetchData() {
       try {
         let response = await fetch('https://api.example.com/data');
         let data = await response.json();
         console.log(data);
       } catch (error) {
         console.log('Error:', error);
       }
     }
     fetchData();
     ```

10. **fetch**：
    - 用于发起HTTP请求。
      ```javascript
      fetch('https://api.example.com/data')
        .then(response => response.json())
        .then(data => console.log(data))
        .catch(error => console.log('Error:', error));
      ```

11. **EMCAScript, DOM, BOM**：
    - **EMCAScript**：JavaScript的标准化规范。
    - **DOM**：文档对象模型，表示HTML文档的结构。
      ```javascript
      document.getElementById('myId').innerText = 'Hello, World!';
      ```
    - **BOM**：浏览器对象模型，表示浏览器窗口和框架。
      ```javascript
      console.log(window.innerWidth);
      ```

12. **DOM 树与 DOM 操作（在这里与 HTML/CSS 结合）**：
    - **DOM 树**：表示HTML文档的树状结构。
    - **DOM 操作**：修改HTML文档结构和样式。
      ```javascript
      let element = document.createElement('div');
      element.textContent = 'Hello, World!';
      document.body.appendChild(element);
      ```

13. **如何在 HTML 中写入并执行 JS 代码？如何处理事件？如何用 JS 实现动画？**：
    - **在 HTML 中写入并执行 JS 代码**：
      ```html
      <script>
        console.log('Hello, World!');
      </script>
      ```
    - **处理事件**：
      ```html
      <button id="myButton">Click me</button>
      <script>
        document.getElementById('myButton').addEventListener('click', function() {
          alert('Button clicked!');
        });
      </script>
      ```
    - **实现动画**：
      ```html
      <div id="myDiv" style="width: 100px; height: 100px; background: red; position: absolute;"></div>
      <script>
        let div = document.getElementById('myDiv');
        let position = 0;
        function move() {
          if (position >= 350) {
            clearInterval(interval);
          } else {
            position++;
            div.style.left = position + 'px';
          }
        }
        let interval = setInterval(move, 10);
      </script>
      ```

# 基础补充
## 实现动画效果
<mark style="background: #BBFABBA6;">方法①</mark> setInterval({函数名}，{执行次数})
>利用不断循环的函数，多次产生对象的运动效果

✨<mark style="background: #BBFABBA6;">方法②</mark>`requestAnimationFrame`
- 优点：它与浏览器的刷新率同步，可以**提高动画性能和节能效果**。
- 功能：要求浏览器在下一次重绘之前调用指定的回调函数来更新动画

>更多方法可以参见codesandbox中的“动画”文件夹
## DOM树及其操作
- <mark style="background: #BBFABBA6;">什么是DOM树</mark>
其实就是将html文档整体看成一个树的结构，事实上我们也是如此操作编写代码的。
以下是一些名词：
	- **Document**：根节点，表示整个HTML文档。
	- **Element**：表示HTML元素，比如 `<div>`、`<p>`、`<a>` 等。
	- **Attribute**：表示元素的属性，比如 `class`、`id` 等（属性在DOM树中并不是单独的节点，而是附属于元素节点）。
	- **Text**：表示元素或属性中的文本内容。

<mark style="background: #BBFABBA6;">常见的DOM操作</mark>
>我们已经在其他地方见过许多

- 访问节点
	- `document.getElementById(id)`：根据元素的 `id` 获取元素。
	- `document.getElementsByClassName(className)`：根据元素的 `class` 获取元素集合。
	- `document.getElementsByTagName(tagName)`：根据元素的标签名获取元素集合。
	- `document.querySelector(selector)`：根据CSS选择器获取第一个匹配的元素。
	- `document.querySelectorAll(selector)`：根据CSS选择器获取所有匹配的元素。
- 创建和插入节点
	-  `document.createElement(tagName)`：创建一个新的元素节点。
	- `node.appendChild(newNode)`：将新的节点添加为某个节点的最后一个子节点。
	- `node.insertBefore(newNode, referenceNode)`：在某个节点之前插入新的节点。
🌰:
```js
let newDiv = document.createElement('div');
newDiv.textContent = 'New Div';
document.body.appendChild(newDiv);
```
- 删除节点：
	-  `node.removeChild(childNode)`：从父节点中移除子节点。
- 修改节点
	-  `node.textContent`：获取或设置元素的文本内容。
	- `node.innerHTML`：获取或设置元素的HTML内容。
	- `element.setAttribute(name, value)`：设置元素的属性。
	- `element.getAttribute(name)`：获取元素的属性。
	- `element.classList`：用于添加、移除和切换元素的CSS类
🌰:
```js
let paragraph = document.querySelector('p');
paragraph.textContent = 'Hello, DOM!';
paragraph.setAttribute('class', 'highlight');
paragraph.classList.add('new-class');
```
- 事件处理
	- `element.addEventListener(event, function)`：向元素添加事件监听器。

## BOM
- <mark style="background: #BBFABBA6;">概念</mark>：
1. 一种编程接口，用于<mark style="background: #FFF3A3A6;">与浏览器进行交互</mark>。
2. 提供了与浏览器窗口和导航相关的对象和方法，使得开发者可以**控制浏览器窗口**、**管理浏览历史**、**操作地址栏**等

- <mark style="background: #BBFABBA6;">主要特性
</mark>
1. **window 对象**：表示浏览器窗口，是全局对象，所有全局变量和函数都是 window 对象的属性和方法。
2. **导航对象**：通过 `navigator` 对象访问浏览器的信息（如用户代理、在线状态、平台等）。
3. **历史对象**：通过 `history` 对象管理浏览历史（如前进、后退、跳转等）。
4. **位置对象**：通过 `location` 对象访问和操作地址栏 URL（如重新加载页面、跳转到新页面等）。
5. **对话框方法**：如 `alert`、`confirm` 和 `prompt`。

🌰：
```js
// 获取浏览器信息
console.log(navigator.userAgent);

// 跳转到新页面
location.href = 'https://www.example.com';

// 显示提示框
alert('Hello, BOM!');

// 前进一页
history.forward();
```

## fetch
>https://developer.mozilla.org/zh-CN/docs/Web/API/fetch

1. 用于进行网络请求的现代方法
2. 基于 Promise，并通过更直观的语法来处理 HTTP 请求和响应

<mark style="background: #BBFABBA6;">基本语法</mark>
```js
fetch(url, options)
  .then(response => {
    // handle response
  })
  .catch(error => {
    // handle error
  });
```
- `url`：请求的 URL 地址。
- `options`（可选）：一个包含自定义配置的对象，如方法、头信息、请求体等。

🌰**示例**：
```js
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
      throw new Error('Network response was not ok ' + response.statusText);
    }
    const data = await response.json(); // 等待并解析响应体
    console.log(data); // 处理解析后的 JSON 数据
  } catch (error) {
    console.error('There was a problem with your fetch operation:', error); // 处理错误
  }
}

fetchData();
```
	- `async function fetchData()`：定义一个异步函数。
	- `await fetch('https://api.example.com/data')`：等待 `fetch` 请求完成。
	- `await response.json()`：等待并解析响应体为 JSON。
	- `try...catch`：捕获并处理任何错误。

### 可选的请求内容
>https://developer.mozilla.org/zh-CN/docs/Web/API/fetch#options

## 异步编程
- 📝概念:
	一个异步过程的执行将不再与原有的序列有顺序关系,不按照代码顺序执行，执行效率更高
- 什么时候用异步编程：
	用子线程来完成一些可能消耗时间足够长以至于被用户察觉的事情

>但是独立于主线程的子线程与主线程失去同步，我们无法确定它的结束，往往通过**回调函数**来实现异步任务的结果处理。

🌰：回调函数搭配setTimeout实现异步编程
```js
setTimeout(function () {
    document.getElementById("demo1").innerHTML="RUNOOB-1!";  // 三秒后子线程执行
}, 3000);

document.getElementById("demo2").innerHTML="RUNOOB-2!";      // 主线程先执行
```

## Promise
1. <mark style="background: #BBFABBA6;">概念</mark>：用于处理异步操作的一种对象。代表了一个在未来可能完成或失败的操作及其结果。
2. <mark style="background: #BBFABBA6;">产生原因</mark>：优雅地异步编程
>先观察传统的异步编程的“函数瀑布”问题
```js
setTimeout(function () {
    console.log("First");
    setTimeout(function () {
        console.log("Second");
        setTimeout(function () {
            console.log("Third");
        }, 3000);
    }, 4000);
}, 1000);
```
这个函数瀑布实在是不美观，且对后序的操作带来不便，为此：
```js
new Promise(function (resolve, reject) {
    setTimeout(function () {
        console.log("First");
        resolve();
    }, 1000);
}).then(function () {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            console.log("Second");
            resolve();
        }, 4000);
    });
}).then(function () {
    setTimeout(function () {
        console.log("Third");
    }, 3000);
});
```
上述代码可以直观地替代瀑布函数，显得更有层次感与可读性；
>接下来分析其语法的具体内容：

🌰:
```js
new Promise(function (resolve, reject) {  //前面是固定的创建方法，紧随后置的是起始函数
    var a = 0;
    var b = 1;
    if (b == 0) reject("Divide zero");    //如果失败，reason为“Divide zero"
    else resolve(a / b);  // 这里resolve的value为a/b=0
}).then(function (value) {      //起始函数执行成功，运行.then后的函数
    console.log("a / b = " + value);
}).catch(function (err) {
    console.log(err);
}).finally(function () {   //无论起始函数是否执行成功都会执行.finally内的函数
    console.log("End");
});
```
解释：
	- `resolve(value)`：表示异步操作成功，并将结果（`value`）传递给 `.then` 的处理函数。
	- `reject(reason)`：表示异步操作失败，并将错误原因（`reason`）传递给 `.catch` 的处理函数。

- <mark style="background: #BBFABBA6;">已解决的Promise</mark>
	- 表现：`Promise.resolve(value)` 
		- - 如果 `value` 本身是一个 Promise，那么返回这个 Promise。
		- 如果 `value` 是一个普通值（比如字符串、对象等），那么返回一个新的<mark style="background: #FFF3A3A6;">已解决</mark>的 Promise，这个 Promise 的值就是 `value`。
	- 举例🌰：
```js
function myFunction() {
    return Promise.resolve("Hello, world!");
}
//调用函数：（本身是一个值为解决的Promise,因此直接加上.then
myFunction().then(message => {
    console.log(message); // 输出: "Hello, world!"
});
```

---
## Promise的语法糖
### async 函数
- 用于声明一个异步函数，异步函数总是返回一个 Promise
🌰：
```js
async function myFunction() {
    return "Hello, world!";
}

// 等价于
function myFunction() {
    return Promise.resolve("Hello, world!");
}
```
### await
- <mark style="background: #BBFABBA6;">作用</mark>：后面加上异步操作函数名，<mark style="background: #FFF3A3A6;">返回的值</mark>是异步函数的resolve或rejected
	1. 等待一个 Promise 对象的解析（resolve）。
	2. 只能在 `async` 函数内部使用。`await` 会暂停 `async` 函数的执行，直到 Promise 解决（resolve）或拒绝（reject），然后继续执行函数并返回解决后的值。
- <mark style="background: #BBFABBA6;">举例说明其等待的功能</mark>🌰
```js
async function myFunction() {
    let promise = new Promise((resolve, reject) => {
        setTimeout(() => resolve("Done!"), 1000);
    });

    let result = await promise; // 等待，直到 Promise resolve
    console.log(result); // 输出: Done!
}
```
	此时，如果myFunction内后面部分还有内容要执行，也会在await的作用下中止，等待上述的延时结束

### <mark style="background: #BBFABBA6;">综合作用</mark>
```js
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Data received");
        }, 2000);
    });
}

async function processData() {
    console.log("Fetching data...");
    const data = await fetchData(); // 等待 fetchData() resolve
    console.log(data); // 输出: Data received
    console.log("Processing complete");
}

processData();
```

## 函数闭包
- 📝什么是函数闭包
在外层函数内部定义的内层函数，能够访问其外层函数里的参数，即使外层函数已经调用结束。
- 🌰一个简单的说明情景：
```js
function outerFunction() {
    let outerVariable = 'I am outside!';

    function innerFunction() {
        console.log(outerVariable);
    }

    return innerFunction;
}

const closureFunction = outerFunction();
closureFunction(); // 输出: I am outside!
```
	- const closureFunction = outerFunction(); 首先将外层函数的调用结果复制给了closureFunction
	- 观察外层函数的返回，我们不难发现这个返回结果就是其内部函数innerFunction;
	- 因此，closureFunction此时就等价于内部函数innerFunction，后接（）是因为内部函数是没有参数的
	- closureFunction(); // 输出: I am outside!   调用了外层函数内部的函数，通过结果我们发现内部函数可以访问外部函数的参数！✨
- 什么时候用到函数闭包
	1. 回调函数：异步编程中保存函数执行的上下文
		```js
		function sayHelloLater(name) {
		    setTimeout(function() {
		        console.log('Hello, ' + name);
			    }, 1000);
			}
		sayHelloLater('Alice'); // 一秒钟后输出: Hello, Alice
		```
	2. 
## DOM方法
>https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Building_blocks/Build_your_own_function#%E5%9F%BA%E6%9C%AC%E5%87%BD%E6%95%B0
- 创建元素与追加
```js
const panel = document.createElement("div");

const msg = document.createElement("p");
msg.textContent = "This is a message box";
panel.appendChild(msg);

const closeBtn = document.createElement("button");
closeBtn.textContent = "x";
panel.appendChild(closeBtn);

```
	创建了一个 <p> 元素和一个<button>元素——并且把它们追加到了 panel <div> 之下
## 绘图相关
✨一览表：
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Canvas Example</title>
  <style>
    canvas {
      border: 1px solid black; /* 为canvas添加边框，便于查看 */
    }
  </style>
</head>
<body>
  <!-- 定义一个canvas元素，指定其宽度和高度 -->
  <canvas id="myCanvas" width="500" height="400"></canvas>
  
  <script>
    // 获取canvas元素
    const canvas = document.getElementById('myCanvas');
    // 获取2D绘图上下文
    const ctx = canvas.getContext('2d');

    /* 
     * Canvas基本属性：
     * - width: 宽度，以像素为单位
     * - height: 高度，以像素为单位
     * 注意：这些属性也可以在JavaScript中设置，例如：canvas.width = 500;
     */

    // 设置绘图样式
    ctx.fillStyle = 'green'; // 填充颜色
    ctx.strokeStyle = 'blue'; // 边框颜色
    ctx.lineWidth = 5; // 线条宽度

    // 绘制一个矩形
    ctx.fillRect(50, 50, 150, 100); // 填充矩形：起点(50, 50)，宽150，高100
    ctx.strokeRect(50, 50, 150, 100); // 绘制矩形边框

    // 绘制一条直线
    ctx.beginPath(); // 开始一条新路径
    ctx.moveTo(50, 200); // 起点
    ctx.lineTo(200, 300); // 终点
    ctx.stroke(); // 绘制线条

    // 绘制一个圆形
    ctx.beginPath(); // 开始新路径
    ctx.arc(300, 150, 50, 0, Math.PI * 2); // 圆心(300, 150)，半径50，起始角0，终止角2π
    ctx.fill(); // 填充圆形
    ctx.stroke(); // 绘制圆形边框

    // 绘制文本
    ctx.fillStyle = 'red'; // 设置文本填充颜色
    ctx.font = '24px Arial'; // 设置字体大小和样式
    ctx.fillText('Hello Canvas', 250, 50); // 在指定位置绘制文本

    // 绘制图片
    const img = new Image();
    img.src = 'https://via.placeholder.com/100'; // 设置图片源
    img.onload = function() {
      ctx.drawImage(img, 350, 200, 100, 100); // 在指定位置绘制图片，宽高100x100
    };

    /*
     * 其他常用方法：
     * - clearRect(x, y, width, height): 清除指定矩形区域的内容
     * - beginPath(): 开始一条新路径
     * - closePath(): 关闭路径
     * - stroke(): 绘制路径
     * - fill(): 填充路径
     * - moveTo(x, y): 将绘图游标移动到指定位置
     * - lineTo(x, y): 绘制一条从当前位置到指定位置的直线
     * - arc(x, y, radius, startAngle, endAngle, anticlockwise): 绘制圆弧
     */
  </script>
</body>
</html>
```
补充：
- **获取 canvas 元素和 2D 绘图上下文**：通过 `getElementById` 获取 canvas 元素，并通过 `getContext('2d')` 获取 2D 绘图上下文。
- **设置绘图样式**：通过 `fillStyle`、`strokeStyle` 和 `lineWidth` 设置填充颜色、边框颜色和线条宽度。
- **绘制矩形**：使用 `fillRect` 和 `strokeRect` 绘制填充矩形和矩形边框。
- **绘制直线**：使用 `beginPath` 开始新路径，`moveTo` 移动到起点，`lineTo` 绘制直线，`stroke` 绘制路径。
- **绘制圆形**：使用 `beginPath` 开始新路径，`arc` 绘制圆弧，`fill` 填充圆形，`stroke` 绘制圆形边框。
- **绘制文本**：通过 `fillText` 在指定位置绘制文本。
- **绘制图片**：通过 `drawImage` 在指定位置绘制图片
## 概念类型
1. 条件判断的true

任何不是 `false`、`undefined`、`null`、`0`、`NaN`、或一个空字符串（`''`）在作为条件语句进行测试时实际返回 `true`，
## 事件介绍
>https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Building_blocks/Events#%E4%BB%80%E4%B9%88%E6%98%AF%E4%BA%8B%E4%BB%B6%EF%BC%9F
- 基本步骤：
	1. 注册一个事件处理器
	2. 处理不同的事件 `addEventListenser`
🌰改变颜色：
```js
const btn = document.querySelector("button");

function random(number) {
  return Math.floor(Math.random() * (number + 1));
}

btn.addEventListener("click", () => {
  const rndCol = `rgb(${random(255)}, ${random(255)}, ${random(255)})`;
  document.body.style.backgroundColor = rndCol;
});
```
- 事件对象
	- 被自动传递给事件处理函数，以提供额外的功能和信息
	- 🌰：
```js
function bgChange(e) {
  const rndCol = `rgb(${random(255)}, ${random(255)}, ${random(255)})`;
  e.target.style.backgroundColor = rndCol;
  console.log(e);
}

btn.addEventListener("click", bgChange);
```
	事件对象的额外属性 event
- 其他事件
	- mouseover
		功能实现上与hover基本相同，但是前者是JS,后者只能在CSS中实现
		- 如果只是需要在鼠标悬停时改变元素的样式，用 `hover` 伪类就足够了，它简单且高效。
		- 如果需要在鼠标悬停时执行一些复杂的操作，如动画、数据加载等，使用 `mouseover` 事件会更灵活。
### 视频事件
- 解决事件冒泡（同时触发多个事件监视器的现象）
✨利用stopPropagation( )
🌰:

```js
const btn = document.querySelector("button");
const box = document.querySelector("div");
const video = document.querySelector("video");

btn.addEventListener("click", () => box.classList.remove("hidden"));

video.addEventListener("click", (event) => {
  event.stopPropagation();
  video.play();
});

box.addEventListener("click", () => box.classList.add("hidden"));
```

### 键盘事件
- 分类：keydown, keypress, keyup
1. keydown: 当用户按下任意键时触发
	1. 常用属性：
		<mark style="background: #FFF3A3A6;">key: 表示按下的键的值</mark>，例如 'a'、'Enter'、'1' 等。
		code: 表示物理键盘上的键的位置，例如 'KeyA'、'Digit1'。
		ctrlKey: 布尔值，表示 Ctrl 键是否被按下。
		shiftKey: 布尔值，表示 Shift 键是否被按下。
		altKey: 布尔值，表示 Alt 键是否被按下。
		metaKey: 布尔值，表示 Meta 键（在 Mac 上通常是 Command 键）是否被按下
	2. 举例：
🌰检测用户按下的键：
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Keydown Event Example</title>
</head>
<body>
  <input type="text" id="textBox" placeholder="Type something...">
  <script>
    const textBox = document.getElementById('textBox');

    textBox.addEventListener('keydown', event => {
      console.log(`You pressed "${event.key}" (code: ${event.code}).`);
    });
  </script>
</body>
</html>
```

### 普通事件监测器

#### select
```js
<select id="weather">
  <option value="">--作出选择--</option>
  <option value="sunny">晴天</option>
  <option value="rainy">雨天</option>
  <option value="snowing">雪天</option>
  <option value="overcast">阴天</option>
</select>
```
并且用下述代码来读取选择的数据：
```js
  const choice = select.value;
```
#### button
```js
button.addEventListener("click",__);
```

## 经典操作
### 修改html中p的内容
- 步骤
1. 在html中设置选择器
```html
<p></p>
```
2. 在js中用函数引用得到对应的p
```js
const para = document.querySelector("p");
```
3. 利用事件监视器在交互之后改变对应的内容
🌰:事件监视器（简化的函数表示方式）
```js
 btn.addEventListener('click', () => {
 ___
 });
```
🌰:在原来的文本后面新增文本
```js
	para.textContent += `${i} `;// i 是变量的名称
```
	此处使用`$`可以实现在字符串中插入变量的值，如果para本身是一个数值，就可以直接相加
	效果与+= i+" ";相同，注意引号内为空格，且可以换成单引号；
	更常见的用法如下：
✨：
```js
 para.textContent = `外面现在是 ${temperature} 华氏度——风和日丽。`;
```
可以避免temperature在''内部成为字符串，注意要用{}包含
🌰：关键词替代
```js
    newStory = newStory.replace("35 摄氏度", temperature);
      story.textContent = newStory;
```
当然，也可以直接让para={对应的内容};
✨注意，此处<mark style="background: #FFF3A3A6;">textContent是必需</mark>的！
### 替换变量的内容
- 关键操作：<mark style="background: #BBFABBA6;">replace</mark> 
- 🌰：根据出现的内容替换另一个变量的内容
1. 全局范围内搜索替换：
```js
  newStory = newStory.replace(/:inserta:/g, xItem);
```
2. 替换第一次出现的:inserta:
```js
  newStory = newStory.replace(":inserta:", xItem);
```


### 生成随机数
🌰：
```js
let randomNumber = Math.floor(Math.random() * 100) + 1;
```
- 表示声明一个randomNumber的变量，并将右侧的值赋值给它；
- Math.randon()将产生一个0~1之间的小数；
- floor(x) 表示将x的小数部分去除，然后得到地对应的整数；
- 因此，上述操作可以得到0~100之间的随机数
### 调试相关
1. 打印值
```js
console.log(lowOrHi);
```
>将`lowOrHi`的值打印到控制台

### 调用策略
####  1. 内置代码的风险规避
>如果JS加载于想要操作的HTML元素之前，代码将会出错。因此，为了 避免这种风险，对于内置在HTML中的JS代码需要加上下述代码：

```js
document.addEventListener("DOMContentLoaded", () => {
  // …
});
```
也就是在\<script>的后面跟上这段代码，再内含JS代码

#### 2. 外部调用
需要在HTML的\<head>内加入下述代码：
```html
<script src="script.js" defer></script>
```
>应保证：`script.js`内具有JS代码，且与HTML代码文件处于同一目录下

- 📝<mark style="background: #ADCCFFA6;">参数之间的差异</mark>
	🌰：![Pasted image 20240523192316.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240523192316.png)
	1. `NULL`: 遇到脚本后停止对HTML内容的渲染，直至下载并运行完毕
	2. `defer`: 按照它们在页面上出现的顺序加载，并且只有当页面内容全部加载完毕之后脚本才会运行。
		✨如果脚本<mark style="background: #FFF3A3A6;">依赖于 DOM 的存在</mark>（例如，脚本修改了页面上的一个或多个元素），这一点非常有用。
	3. `async`:浏览器遇到 `async` 脚本时不会阻塞页面渲染，而是直接下载然后运行。一旦下载完成，脚本就会执行，从而阻止页面渲染。
		✨当页面的脚本之间<mark style="background: #FFF3A3A6;">彼此独立</mark>，且不依赖于本页面的其他任何脚本时，`async` 是最理想的选择
- 👍：总结
		1. 如果脚本无需等待页面解析，且无依赖独立运行，那么应使用 `async`。
		2. 如果脚本需要等待页面解析，且依赖于其他脚本，调用这些脚本时应使用 `defer`
### 遍历按钮分配处理器
```js
const buttons = document.querySelectorAll("button");

for (let i = 0; i < buttons.length; i++) {
  buttons[i].addEventListener("click", createParagraph);
}

```
# JS函数
函数的定义：function {函数名}（{参数名}）{\_\_}
	🌰:function displayMessage() {}
## 重要函数类型
### 回调函数
- **含义**：作为另一个函数的参数的函数
- **作用**：用于处理异步操作，例如读取文件、处理用户输入、或者从服务器获取数据
- **示例**：
🌰基本定义与调用：
```js
// 定义一个函数，接收另一个函数作为参数
function doSomething(callback) {
    console.log("Doing something...");
    callback(); // 调用回调函数
}
// 定义一个回调函数
function myCallback() {
    console.log("Callback function executed.");
}
// 调用 doSomething 函数并传递回调函数
doSomething(myCallback);
```
✨实际应用：<mark style="background: #FFF3A3A6;">异步操作</mark>
1. **setTimeout**
```js
function greet() {
    console.log("Hello, World!");
}
// 2秒后执行greet函数
setTimeout(greet, 2000);
```
>在指定的延迟时间后执行一次函数或代码片段

- 格式：setTimeout(function, delay, ...args);
	function：要执行的函数。
	delay：延迟的时间，以毫秒为单位。
	...args：可选参数，传递给函数的参数。


2. **作为事件处理的函数**
```js
// 为按钮添加点击事件处理程序
document.getElementById("myButton").addEventListener("click", function() {
    console.log("Button clicked!");
});
//这同时也是匿名函数的体现！✅
```
3. 处理异步网络请求
```js
// 模拟异步数据请求
function fetchData(callback) {
    setTimeout(() => {
        const data = { name: "John", age: 30 };
        callback(data); // 处理数据的回调函数
    }, 2000);
}

// 定义处理数据的回调函数
function handleData(data) {
    console.log("Data received:", data);
}

// 发起数据请求并处理数据
fetchData(handleData);

```
### 匿名函数
- **作用**：通常用于较短的生命周期，完成数量不多的任务，较少调用
- **功能**：
1. 事件处理:直接在事件绑定时定义回调函数。
```js
document.getElementById("myButton").addEventListener("click", function() {
    console.log("Button clicked!");
});
```
2. 数组方法：
>数组方法如 `map`、`filter` 和 `reduce` 都接受回调函数，匿名函数在这些情况下非常常见
```js
let numbers = [1, 2, 3, 4, 5];
let squaredNumbers = numbers.map(function(num) {
    return num * num;
});
console.log(squaredNumbers); // 输出: [1, 4, 9, 16, 25]
```
3. 定时器：setTimeOut 与 setInterval
```js
setTimeout(function() {
    console.log("This message is displayed after 2 seconds");
}, 2000);
```
	🌰`setInterval`是在一定时间周期后反复执行函数内容的函数：
```js
setInterval(function() {
    console.log("This message is displayed every 1 second");
}, 1000);
```
4. 结合Promises使用:处理异步操作
```js
fetch('https://api.example.com/data')
    .then(function(response) {
        return response.json();
    })
    .then(function(data) {
        console.log("Data received:", data);
    })
    .catch(function(error) {
        console.error("Error:", error);
    });
```
5. 动态创建函数
🌰倍增器：
```js
function createMultiplier(multiplier) {
    return function(num) {
        return num * multiplier;
    };
}

let double = createMultiplier(2);
console.log(double(5)); // 输出: 10

let triple = createMultiplier(3);
console.log(triple(5)); // 输出: 15
```
📝**分析**：
	1. 首先定义了一个叫做`creatMultiplier`的函数，需要一个参数multiplier
	2. 外层函数的<mark style="background: #FFF3A3A6;">返回值是一个函数</mark>，这个函数没有名字，因此是匿名函数
	3. 下方的第一次调用的结果：让`double`本身成为了一个匿名函数，接受传参`num`
	4. 可以看到在上方的函数定义中，匿名函数点的返回值是二者的乘积
	5. 因此，最后调用`double`函数的时候会显示对应的结果

6. 作为对象：{\_}内的一部分
🌰打印对象的名称：
```js
let person = {
    name: 'Alice',
    greet: function() {
        console.log('Hello, ' + this.name);
    }
};
person.greet(); // 输出: Hello, Alice
```
✨:`this`关键词
{ #f33955}

- 功能：方法调用上下文
	 当一个方法作为对象的方法调用时，`this` 绑定到该对象。
	 🌰因为 `greet` 方法是通过 `person.greet()` 这样的语法调用的，所以 `this` 绑定到 `person` 对象。
### 箭头函数
1. 事件处理中配合匿名函数的使用
```js
textBox.addEventListener("keydown", (event) => {
  console.log(`You pressed "${event.key}".`);
});
```
如果函数的接受参数只有1个（如上），可以将括号去掉：
```js
textBox.addEventListener("keydown", event => {
  console.log(`You pressed "${event.key}".`);
});
```

## 函数的默认参数
- 情形：在默认情况下有默认的输出；如果调用函数时有具体的传参，那么用该参数代替
- 手法：
🌰打招呼：
```js
function hello(name = "克里斯") {
  console.log(`你好，${name}！`);
}
hello("阿里"); // 你好，阿里！
hello(); // 你好，克里斯！
```
## document.querySelector
1. 点击网页的交互
```js
document.querySelector("html").addEventListener("click", function () {
  alert("别戳我，我怕疼。");
});
```
- `document.querySelector("html")` 
	选择整个 HTML 文档的根元素。选择器 `"html"` 直接指向文档的 `<html>` 元素。
- `.addEventListener("click", function () {` 
	在选中的 HTML 元素上添加一个事件监听器。第一个参数 `"click"` 指定监听点击事件。
- `function () { alert("别戳我，我怕疼。"); }`  
	当点击事件触发时将执行这个函数。函数体内的代码使用 `alert` 方法弹出一个提示框，显示信息 "别戳我，我怕疼。"。

## document.querySelectforAll
>[Document.querySelectorAll - Web API | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelectorAll)

```js
var container = document.querySelector("#test");
var matches = container.querySelectorAll("div.highlighted > p");
```
得到一个`<p>`元素的<mark style="background: #ADCCFFA6;">列表</mark>，其直接父元素是一个 class 为`"highlighted"`的`div`，并且位于 ID 为`"test"`的容器内。

2. 属性选择器
🌰:返回文档中属性名为`"data-src"`的`iframe`元素列表：
```js
var matches = document.querySelectorAll("iframe[data-src]");
```

🌰:返回 ID 为`"userlist"`的列表中包含值为`"1"`的`"data-active"`属性的元素
```js
var container = document.querySelector("#userlist");
var matches = container.querySelectorAll("li[data-active='1']");
```

# 数据类型
## 什么是JSON
- 概念：
	1. 基于 JavaScript 的对象字面量语法，但独立于编程语言，几乎所有现代编程语言都支持 JSON
	2. 易于人阅读和编写，同时也易于**机器解析和生成**
- JSON与JS的对象的转换
🌰JSON的内容：
```JSON
{
  "name": "Alice",
  "age": 25,
  "isStudent": true,
  "courses": [
    "Mathematics",
    "Computer Science"
  ],
  "address": {
    "street": "123 Main St",
    "city": "Somewhere",
    "zip": "12345"
  },
  "graduationYear": null
}
```
🌰转换：
```js
// JSON 字符串
const jsonString = '{"name": "Alice", "age": 25, "isStudent": true}';

// 解析 JSON 字符串为 JavaScript 对象
const jsonObj = JSON.parse(jsonString);
console.log(jsonObj.name); // 输出: Alice

// 将 JavaScript 对象转换为 JSON 字符串
const obj = { name: "Bob", age: 30, isStudent: false };
const jsonStringify = JSON.stringify(obj);
console.log(jsonStringify); // 输出: {"name":"Bob","age":30,"isStudent":false}
```

## 字符串相关
### <mark style="background: #BBFABBA6;">切片</mark>
🌰将字符串切片获得第一个到倒数第二个（不包含）的新字符串：
```js
refused.textContent = refused.textContent.slice(0, refused.textContent.length - 2) + '.';
```
就是作用于这样的情景：
	Admit: Chris, Anne, Colin, Terri, Sam, Kay, Bruce.
	在之前的循环当中，总是xx+", "
	因此，在结束之后希望末尾不具有空格且以.结尾，需要删除末尾的两个元素。
	由于这里的切片(m,n)是从m到n但不包含最后一位。因此希望删除x位，就令n=length-x.

## 数组相关

1. <mark style="background: #BBFABBA6;">得到数组长度</mark>
- 函数：`_.length;`
- 🌰：
```js
let sequence = [1, 1, 2, 3, 5, 8, 13];
for (let i = 0; i < sequence.length; i++) {
  console.log(sequence[i]);
}
```
2. <mark style="background: #BBFABBA6;">将字符串按照特定符号分隔为数组</mark>
🌰按照字符串中的“,"进行分隔:
```js
let myData = "Manchester,London,Liverpool,Birmingham,Leeds,Carlisle";

let myArray = myData.split(",");
myArray;

```
如此一来，myArray就是\[
    "Manchester",
    "London",
    "Liverpool",
    "Birmingham",
    "Leeds",
    "Carlisle"
	]
✨也可以用`join`将数组中的<mark style="background: #BBFABBA6;">元素串联成为字符串</mark>
	🌰将数组之间用`,`串联成为字符串
```js
let myNewString = myArray.join(",");
myNewString;
```
>Manchester,London,Liverpool,Birmingham,Leeds,Carlisle
### 增删数据
- <mark style="background: #BBFABBA6;">在末尾增加项目</mark>
```js
myArray.push("Cardiff");
```
<mark style="background: #ADCCFFA6;">返回值</mark>：新的数组的长度！✨
🌰因此，可以将这个表达式赋值给一个变量来存储数组的长度：
```js
var newLength = myArray.push("Bristol");
```
>此时，变量`newLength`存储了该数组的长度
- <mark style="background: #BBFABBA6;">在末尾删除项目</mark>
```js
myArray.pop();
```
<mark style="background: #ADCCFFA6;">返回值</mark>：已删除的项目！😆
🌰因此，可以将其赋值给变量储存：
```js
let removedItem = myArray.pop();
```
- 开头的增删操作
	将push与pop分别换为unshift与shift,分别对应在开头的增加与删除！
# 值得回顾
## 笑话机
>[笑话生成器 - 学习 Web 开发 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Silly_story_generator)

