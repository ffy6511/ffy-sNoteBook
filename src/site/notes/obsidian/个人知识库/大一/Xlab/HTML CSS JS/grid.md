---
{"dg-publish":true,"permalink":"/obsidian///xlab/html-css-js/grid/","created":"2024-05-17T16:27:22.593+08:00","updated":"2024-09-08T15:25:05.440+08:00"}
---

# 📝基本概念
1. Grid容器和Grid项目
	- **Grid容器**：通过设置`display: grid`或`display: inline-grid`将一个元素定义为网格容器
	- **Grid项目**：网格容器的<mark style="background: #FFF3A3A6;">直接子元素</mark>自动成为网格项目
2. Grid轨道
    - **Grid行轨道**：水平的网格线。
    - **Grid列轨道**：垂直的网格线。
3. 网格单元格：由行和列的交叉形成的单个空间
4. 网格区域：由多个网格单元格组成的矩形区域
# 📖实现举例
🌰覆盖基本功能的内部样式表:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Grid Example</title>
  <style>
    /* 定义.grid-container为一个网格容器 */
    .grid-container {
      display: grid; /* 启用Grid布局 */
      
      /* 定义三列的网格，列宽分别为100px, 200px, 100px */
      grid-template-columns: 100px 200px 100px;
      
      /* 定义两行的网格，行高分别为50px, 100px */
      grid-template-rows: 50px 100px;
      
      /* 设置行和列之间的间距为10px */
      grid-gap: 10px;
    }
    
    /* 定义.grid-item的通用样式 */
    .grid-item {
      background-color: lightblue; /* 背景颜色 */
      border: 1px solid #333;      /* 边框 */
      padding: 20px;               /* 内边距 */
      text-align: center;          /* 文本居中 */
    }
    
    /* 定义.item1的网格位置 */
    .item1 {
      grid-column: 1 / 4; /* 横跨第1列到第4列 */
      grid-row: 1;        /* 占据第1行 */
    }
    
    /* 定义.item2的网格位置 */
    .item2 {
      grid-column: 1 / 2; /* 占据第1列 */
      grid-row: 2;        /* 占据第2行 */
    }
    
    /* 定义.item3的网格位置 */
    .item3 {
      grid-column: 2 / 4; /* 横跨第2列到第4列 */
      grid-row: 2;        /* 占据第2行 */
    }
  </style>
</head>
<body>
  <!-- 定义网格容器 -->
  <div class="grid-container">
    <!-- 定义网格项目 -->
    <div class="grid-item item1">Header</div>    <!-- 头部，横跨三列 -->
    <div class="grid-item item2">Sidebar</div>   <!-- 侧边栏，占据第二行的第一列 -->
    <div class="grid-item item3">Main Content</div> <!-- 主内容区，占据第二行的第二和第三列 -->
  </div>
</body>
</html>

```
## ✨**注释总结**:
Grid容器：通过设置display: grid或display: inline-grid将一个元素定义为网格容器。
Grid项目：网格容器的直接子元素自动成为网格项目。
grid-template-columns：定义网格容器的列数和每列的宽度。
grid-template-rows：定义网格容器的行数和每行的高度。
grid-gap：设置网格单元格之间的间距。
grid-column：定义网格项目在列方向上的位置和跨度。
grid-row：定义网格项目在行方向上的位置和跨度。

# 📝简单操作补充
- 给line<mark style="background: #BBFABBA6;">起名字</mark>:用中括号将名称括起来即可
🌰：grid-template-columns: \[first] 40px;
- 使用`repeat(n,_)`<mark style="background: #BBFABBA6;">减少重复劳动</mark>： 表示写了n次_中的东西
- 使用`fr`按照比例分配：
🌰： grid-template-columns: 1fr 50px 2fr 1fr
>从父级元素取50px作为第二列，然后将剩下的横向空间按照1:2:1分配
## 网格区域的命名和引用
- 使用属性：`grid-area`
- 步骤：
	1. **命名网格区域**：使用`grid-template-areas`定义网格容器的布局结构；
	2. **将网格项目分配到命名的区域**：使用`grid-area`属性
- 🌰
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Grid Example with Grid Area</title>
  <style>
    /* 定义.grid-container为一个网格容器 */
    .grid-container {
      display: grid; /* 启用Grid布局 */
      
      /* 定义网格容器的列数和每列的宽度 */
      grid-template-columns: 100px 200px 100px;
      
      /* 定义网格容器的行数和每行的高度 */
      grid-template-rows: 50px 100px;
      
      /* 设置行和列之间的间距为10px */
      grid-gap: 10px;
      
      /* 使用grid-template-areas定义命名的网格区域 */
      grid-template-areas:
        "header header header"
        "sidebar main main";
    }
    
    /* 定义.grid-item的通用样式 */
    .grid-item {
      background-color: lightblue; /* 背景颜色 */
      border: 1px solid #333;      /* 边框 */
      padding: 20px;               /* 内边距 */
      text-align: center;          /* 文本居中 */
    }
    
    /* 将网格项目分配到命名的区域 */
    .header { grid-area: header; }
    .sidebar { grid-area: sidebar; }
    .main { grid-area: main; }
  </style>
</head>
<body>
  <!-- 定义网格容器 -->
  <div class="grid-container">
    <!-- 定义网格项目并分配到命名区域 -->
    <div class="grid-item header">Header</div>    <!-- 头部，放置在header区域 -->
    <div class="grid-item sidebar">Sidebar</div>   <!-- 侧边栏，放置在sidebar区域 -->
    <div class="grid-item main">Main Content</div> <!-- 主内容区，放置在main区域 -->
  </div>
</body>
</html>
```
📝注释总结：
- **grid-template-areas**：定义网格容器的布局结构，使用名称表示不同的网格区域。每个名称表示一个区域，可以通过<mark style="background: #FFF3A3A6;">空格分隔列</mark>，通过<mark style="background: #FFF3A3A6;">引号分隔行</mark>。
- **grid-area**：用于将网格项目分配到命名的网格区域，确保每个项目放置在预定义的位置。
- 实际应用中，为`grid-area`属性特别分配了一个规定了位置的类，然后<mark style="background: #FFF3A3A6;">叠加选择器</mark>
---
## justify-self
- 作用：
	- 控制 CSS Grid 布局中单个网格项目（**grid item**）在其网格单元内的水平对齐方式的属性--(作用于item)
	- 定义了项目相对于其所在单元格左右边缘的位置。
- 可选的属性值
	 - `start`: 将项目对齐到单元格的起始边（左边）
	 -  `end`: 将项目对齐到单元格的结束边（右边）
	 -  `center`: 将项目在单元格内居中对齐。
	 -  `stretch`: 默认值。将项目拉伸以填充整个单元格的宽度（如果项目本身没有固定的宽度）
- 🌰基本语法
```css
.element {
    justify-self: value;
}
```
- 🌰应用实现
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Justify Self Example</title>
    <style>
        .container {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            grid-template-rows: 100px;
            gap: 10px;
            border: 1px solid black;
        }
        .item1 {
            background-color: lightblue;
            justify-self: start;
        }
        .item2 {
            background-color: lightcoral;
            justify-self: center;
        }
        .item3 {
            background-color: lightgreen;
            justify-self: end;
        }
        .item4 {
            background-color: lightgoldenrodyellow;
            justify-self: stretch;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item1">Start</div>
        <div class="item2">Center</div>
        <div class="item3">End</div>
        <div class="item4">Stretch</div>
    </div>
</body>
</html>

```
---
## jutify-items
- 作用对象：父级元素
- 作用：指定所有的子元素的布局方式
- 🌰基本语法
```css
	.container{
		justify-items:start | end | center | stretch;
	}
```
🌰`start`:
![Pasted image 20240517170633.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517170633.png)

---
## justify-content
- 作用：设置在父级元素上，沿主轴布局
- 🌰基本语法
```css
	.container{
		justify-content: start | end | center | stretch | space-around | space-between | space-evenly；
	}
```
🌰`end`:
![Pasted image 20240517170914.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517170914.png)
- ❓<mark style="background: #BBFABBA6;">那么沿着`cross axis`的类似布局呢？</mark>
	- ✅轮到`align-content`登场！
	- 可以选用的属性值保持不变
	- 🌰：`start`![Pasted image 20240517171107.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517171107.png)
---
# ✨非凡的布局技巧
## repeat与minmax
<mark style="background: #BBFABBA6;">主人公</mark>：**`repeat(auto-fit, minmax(250px, 1fr))`**
<mark style="background: #ADCCFFA6;">介绍</mark>
- **`repeat()`**: 该函数用于重复定义的列或行数。`auto-fit` 关键字意味着浏览器将**根据容器的可用空间自动调整列数**，使得列在<mark style="background: #FFF3A3A6;">一行中尽可能地适应容器宽度</mark>。
- **`minmax(250px, 1fr)`**: 该函数用于定义每个列的最小和最大尺寸
- **`250px`**: 定义了列的最小宽度。列的宽度不会小于 250px。
- **`1fr`**: 定义了列的最大宽度。`1fr` 表示分配给列的剩余可用空间。`fr` 单位表示网格容器中可用的空间份额。
<mark style="background: #ADCCFFA6;">功能实现</mark>
- **响应式布局**: 网格布局会根据容器的宽度自动调整列数，使列尽可能适应容器宽度。
- **最小列宽度**: 每列的最小宽度为 250px，确保内容不会过于拥挤。
- **最大列宽度**: 每列可以扩展到最大宽度 `1fr`，即网格容器中所有列均分剩余空间。