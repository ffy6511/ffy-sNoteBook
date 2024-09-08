---
{"dg-publish":true,"permalink":"/obsidian///xlab//react/","created":"2024-07-03T20:47:53.298+08:00","updated":"2024-09-08T15:25:05.462+08:00"}
---

>中文文档：[React 官方中文文档 (docschina.org)](https://react.docschina.org/)


```
npm config set registry https://registry.npmmirror.com/

npx create-react-app tour
```

通过 npm 下载vite
>[开始 | Vite 官方中文文档 (vitejs.cn)](https://vitejs.cn/vite3-cn/guide/)

chakra有UI库
	ant design

npm.js
>[npm | Home (npmjs.com)](https://www.npmjs.com/)

10.196.110.28

http-server -p 8081 --cors

---
# 基础语法

```ts
const TodoItem: React.FC<TodoItemProps> = ({ todo, toggleTodo, deleteTodo }) => { //这行中的React.FC什么意思
```
- **``React.FC``** 表示 “React 函数组件”。
- 在 TypeScript 中，**``React.FC``** 是一种定义 React 函数组件类型的简写方式。
- 这样做的好处是可以更清晰地定义组件的 props，并且能够获得更好的类型检查和自动补全。

```c
useState, useEffect分别有什么用？
```
**``useState``** 当状态发生变化时，组件会重新渲染
**``useEffect``** 执行副作用操作，比如数据获取、订阅或手动操作 DOM


# 基础介绍

**❓什么是react**

1. React 是一个用于构建用户界面的 JavaScript 库，主要用于开发单页应用程序（SPA）；
2. 通过组件化的方式提高开发效率和代码重用性；
3. 只负责视图层（View Layer）的开发，不包含完整的前后端合一的全栈功能

❓**与传统三件套的语法类似性**

- **HTML 类似性**：
	- React 组件使用 JSX (JavaScript XML) 语法，这种语法看起来很像 HTML。JSX 允许我们在 JavaScript 代码中直接编写类似 HTML 的结构。
- **CSS 类似性**：
	- React 组件中可以直接引用 CSS 文件，或者使用内联样式（inline styles）来定义组件的样式，这与传统的 CSS 使用方式类似。
- **JavaScript 类似性**：
	- React 本质上是 JavaScript 库，所以其核心语法和逻辑处理仍然依赖 JavaScript。比如事件处理、条件渲染、列表渲染等与 JavaScript 处理方式相似。

## 常见语法

### -  **JSX**
>直接编写 HTML 结构
```jsx
const element = <h1>Hello, world!</h1>;
```

### - <mark style="background: #FFF3A3A6;">组件</mark>
>核心概念，可以是函数组件或类组件

	函数组件：
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
	类组件：
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

### -  **Props 和 State**
>`props` 用于组件之间的**数据传递**，`state` 用于**管理组件内部状态**
```jsx
// 导入 React 库
import React from 'react';

// 定义一个名为 Clock 的类组件
class Clock extends React.Component {
  // 构造函数，初始化组件的状态
  constructor(props) {
  //调用父类的构造函数并传入相应的`props`参数
    super(props);
    // 定义组件的初始状态，包含一个 date 属性，初始值为当前日期和时间
    this.state = { date: new Date() };
  }

  // 组件挂载后（插入 DOM 树中）调用的方法
  componentDidMount() {
    // 设置一个定时器，每秒调用一次 tick 方法
    this.timerID = setInterval(
      () => this.tick(),
      1000
    );
  }

  // 组件卸载前（从 DOM 树中移除）调用的方法
  componentWillUnmount() {
    // 清除定时器
    clearInterval(this.timerID);
  }

  // 更新组件状态的方法，每次调用时更新 date 为当前日期和时间
  tick() {
    this.setState({
      date: new Date()
    });
  }

  // 渲染组件的方法，返回组件的 JSX 表达式
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        {/* 使用组件的状态（state）中的 date 属性 */}
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

// 导出 Clock 组件
export default Clock;

```

### - **事件处理**
>Toggle组件示例
```jsx
// 导入 React 库
import React from 'react';

// 定义一个名为 Toggle 的类组件
class Toggle extends React.Component {
  // 构造函数，初始化组件的状态
  constructor(props) {
    super(props);
    // 定义组件的初始状态，包含一个 isToggleOn 属性，初始值为 true
    this.state = { isToggleOn: true };

    // 绑定事件处理方法，使其能够访问组件实例（this）
    this.handleClick = this.handleClick.bind(this);
  }

  // 定义一个事件处理方法，用于切换 isToggleOn 状态
  handleClick() {
    // 使用 setState 方法更新组件的状态
    this.setState(prevState => ({
    //先前的状态被访问并根据其值更新``isToggleOn``属性 将其取反
    //用于在React组件中处理点击事件时切换某个状态的布尔值。
      isToggleOn: !prevState.isToggleOn
    }));
  }

  // 渲染组件的方法，返回组件的 JSX 表达式
  render() {
    return (
      // 为按钮元素添加一个点击事件处理器
      <button onClick={this.handleClick}>
        {/* 根据 isToggleOn 状态显示不同的文本 */}
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}

// 导出 Toggle 组件
export default Toggle;
```

### - 列表和Key
```jsx
// 导入 React 库
import React from 'react';

// 定义一个名为 NumberList 的函数组件
function NumberList(props) {
  // 从 props 中获取 numbers 属性
  const numbers = props.numbers;
  // 使用 map 方法遍历 numbers 数组，并为每个元素创建一个 <li> 元素
  const listItems = numbers.map((number) =>
    // 每个 <li> 元素必须有一个唯一的 key 属性
    //将``number``转换为字符串，以确保``key``属性接受的是一个字符串值
    <li key={number.toString()}>
      {number}
    </li>
  );
  // 渲染一个包含所有 <li> 元素的 <ul> 元素
  return (
    <ul>{listItems}</ul>
  );
}

// 导出 NumberList 组件
export default NumberList;
```

## 概念补充

### 展开运算符

 **``...``** 可以在对象或数组字面量中用来展开它们的内容。在对象中使用展开运算符时，它会创建对象的浅拷贝，也就是说，它会复制对象的属性和属性值，但是嵌套对象或数组的引用仍然会保持一致。例如，**``{ ...obj }``** 将创建 **``obj``** 的浅拷贝

### 浅拷贝

指创建一个新对象或数组，并将原始对象或数组的所有属性或元素复制到新对象或数组中；
这意味着新对象和原始对象会共享相同的属性值（对于对象）或元素（对于数组）；
如果属性值是对象或数组，则仍然会共享相同的引用。**这意味着对新对象的更改可能会影响原始对象。**

### filter
- 📝作用：用于判断数组中的元素是否应该被保留
- 🌰：敌机和子弹的碰撞逻辑检测：
```js
  checkCollisions() {
    const { bullets, enemies, score } = this.state;
    const newBullets = [];
    const newEnemies = enemies.filter(enemy => {//fiter将满足条件的向保留，因此如果箭头函数的返回值是false，表示去除
      let hit = false;//记录敌机是否被子弹击中
      const remainingBullets = bullets.filter(bullet =>{
        if(
          bullet.x > enemy.x &&
          bullet.x < enemy.x + 40 &&
          bullet.y >enemy.y &&
          bullet.y < enemy.y + 40
        ){
          this.setState({score: score + 1});
          hit = true;
          return false;//在子弹的循环filter内，表示将击中敌机的子弹去除
        }
        return true;//子弹未命中，保留在子弹数组当中
      });
      newBullets.push(...remainingBullets);//将剩余的子弹放入新的子弹数组中
      return !hit;//如果hit为真，表示碰撞，将敌机从敌机数组中取出；否则保留
    });
    this.setState({ bullets: newBullets, enemies: newEnemies });
  }
```

### ✨**钩子函数**
#### useState
- 作用：初始化变量`x`,并创建一个函数`setX`，当该函数被调用时，改变`x`的值
- 格式：`const [state, setState] = useState(initialState);`
- 🌰：
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

#### useEffect
❓什么是副操作：
1. 指的是那些组件渲染过程中除了返回React元素之外需要执行的任何其他逻辑操作。通常不属于纯粹的渲染过程，而是涉及到与外部世界的交互或影响。
2. 副作用操作是与纯函数（pure functions）相对的，纯函数只依赖输入参数并且不产生外部影响，而副作用操作则会影响外部环境或依赖外部数据。

- **作用**：根据状态和属性的变化来执行某些操作 ; 在组件挂载和卸载时执行一次性操作
- **格式**：
```jsx
useEffect(() => {
  // 副作用逻辑
  return () => {
    // 可选的清理逻辑
  };
}, [dependencies]);
```
>依赖数组\[dependencies]决定了副作用的执行时机; 当数组为空时，副作用只在组件挂载和卸载时执行；

- 🌰**数据获取：**
```jsx
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    // 使用fetch API从服务器获取数据
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []); // 依赖数组为空，表示这个副作用仅在组件挂载和卸载时执行

  return (
    <div>
      {data ? <pre>{JSON.stringify(data, null, 2)}</pre> : 'Loading...'}
    </div>
  );
}
```

#####  清理函数
- 执行时机：在组件卸载或副作用重新执行前
- 作用：处理副作用的重复执行和避免资源泄漏
- 🌰：
1. <mark style="background: #BBFABBA6;">清理定时器</mark>：
```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCount(prevCount => prevCount + 1);
    }, 1000);

    return () => {
      clearInterval(interval); // 清理定时器
    };
  }, []); // 依赖项为空，表示该副作用只在组件挂载和卸载时执行

  return <div>Count: {count}</div>;
}
```

2. <mark style="background: #BBFABBA6;">移除事件监听器</mark>：
```jsx
import React, { useState, useEffect } from 'react';

function WindowSize() {
  const [size, setSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight
  });

  useEffect(() => {
    const handleResize = () => {
      setSize({
        width: window.innerWidth,
        height: window.innerHeight
      });
    };

    window.addEventListener('resize', handleResize);

    return () => {
      window.removeEventListener('resize', handleResize); // 清理事件监听器
    };
  }, []); // 依赖项为空，表示该副作用只在组件挂载和卸载时执行

  return (
    <div>
      Width: {size.width}, Height: {size.height}
    </div>
  );
}
```

3. <mark style="background: #BBFABBA6;">清理网络请求</mark>
```jsx
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    const controller = new AbortController();
    const signal = controller.signal;

    fetch('https://api.example.com/data', { signal })
      .then(response => response.json())
      .then(data => setData(data))
      .catch(error => {
        if (error.name === 'AbortError') {
          console.log('Fetch aborted');
        } else {
          console.error('Fetch error:', error);
        }
      });

    return () => {
      controller.abort(); // 清理未完成的网络请求
    };
  }, []); // 依赖项为空，表示该副作用只在组件挂载和卸载时执行

  return (
    <div>
      {data ? <pre>{JSON.stringify(data, null, 2)}</pre> : 'Loading...'}
    </div>
  );
}
```


---
#### **二者的区别**
`useState`主要用于管理组件内部的状态，而`useEffect`则用于处理任何需要在组件生命周期内执行的副作用操作。

```jsx
//管理状态变量
const [state, setState] = useState(initialState);
```

```jsx
//处理副操作
useEffect(() => {
  // 副作用逻辑
  return () => {
    // 可选的清理逻辑
  };
}, [dependencies]);
```

#### useSWR
- 格式：
```ts
const {
	data:xxx,
	error:xxx,
	isLoading:xxx,
} = useSWR<RoomMessageListRes>(
()=>{
	if(roomId === null)return false;
	return "/api/room/message/list?roomId="+roomId;
},
getFetcher,{
refreshInterval: 1000,
}
);
```


# 笔记补充
## 报错处理
❌`Rendered more hooks than during the previous render.`
- 📝报错原因：
	- 被父组件调用的子组件内存在react hook，且子组件被当做普通函数
	- 有条件地调用一个钩子或在所有钩子运行之前提前返回时
🌰
```js
// App.js

import {useEffect, useState} from 'react';

export default function App() {
  const [counter, setCounter] = useState(0);

  // ⛔️ Error: Rendered more hooks than during the previous render.
  if (counter > 0) {
    // 👇️ calling React hook conditionally
    useEffect(() => {
      console.log('hello world');
    });
  }

  return (
    <div>
      <button onClick={() => setCounter(counter + 1)}>toggle loading</button>
      <h1>Hello world</h1>
    </div>
  );
}
```

- ✅解决方式：
	- 将子组件改写成为函数组件 React Function
	- 将所有的钩子函数移到函数组件的顶层，并不要在条件中使用钩子
🌰:
为了确保内层的异步函数获得返回值之后再在外层继续运行，可以将用状态更新来分离内外层钩子函数
```ts
  const [creatorName, setCreatorName] = useState<string | null>(null);

  const{data: creatorQuery, isLoading: creatorNameLoading}  = trpc.user.getRoomCreatorName.useQuery(
    { uid: selectedRoom?.creatorId }); 
 

  useEffect(() => {  
    if (selectedRoom?.creatorId  && creatorQuery ) {   
        setCreatorName(creatorQuery.creator)
      };  
  }, [selectedRoom, creatorQuery]); // 确保在 selectedRoom 与 creatorQuery 改变时触发 useEffect  

```

## 细节
- React组件必须以大写字母开头
- useEffect的组件只在两种情况下运行：
	1. 首次渲染
	2. props变化时
🌰：
```ts
    const storedRoomId = localStorage.getItem('lastSelectedRoomId');
    const storedRoomName = localStorage.getItem('lastSelectedRoomName');

    useEffect(() => {
        if (storedRoomId) {
          setSelectedRoomId(parseInt(storedRoomId, 10));
          setSelectedRoomName(storedRoomName);
        }
      },  [storedRoomId, storedRoomName]);
```
- 状态更新
```tsx

    const [noPower, setNoPower] = useState(false);

    const handleDeleteRoom = async () => {
        setNoPower(false);  // 重置状态
        const currentUserId = parseInt(localStorage.getItem('currentUserId') || '0', 10);
        if (currentUserId !== creatorId) {
            setNoPower(true);
            return;
        }

        await deleteRoom.mutateAsync({ id: roomId });
    };

///
          {noPower && (  // 如果有错误信息则显示警告框
                <Alert 
                message="您没有权限删除该房间" 
                type="warning" 
                showIcon 
                closable 
                style={{ marginLeft: '5px' }}
                onClose={() => setNoPower(false)} 
                 />
            )}
```


