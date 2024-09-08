---
{"dg-publish":true,"permalink":"/obsidian///xlab/html-css-js/css/","created":"2024-05-16T18:30:15.516+08:00","updated":"2024-09-08T15:25:05.443+08:00"}
---

# 相关概念
## 继承
- 含义：CSS属性从父元素传递给子元素，但并非全部
- 常见的可继承属性
	- 文本相关
	- 列表相关
	- 表格相关
- 大多数CSS属性不可继承
	- 🌰：**布局**、**盒模型**和**定位相关**的属性，如`margin`、`padding`、`border`、`width`、`height`、`position`、`display`等
### <mark style="background: #BBFABBA6;">强制继承和阻止继承</mark>
①**强制继承**：
使用 `inherit` 关键字可以强制某个属性从父元素继承
```css
.child {
  color: inherit; /* 强制从父元素继承color属性 */
}
```
②**阻止继承**
使用初始值 `initial` 或者将属性明确设置为某个值：
```css
.child {
  color: initial; /* 将color属性重置为其初始值 */
}
```
## 盒模型
>https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/The_box_model#%E4%BB%80%E4%B9%88%E6%98%AF_css_%E7%9B%92%E6%A8%A1%E5%9E%8B%EF%BC%9F
## 空白
- CSS 声明通过空白字符分离不同的值，**属性名称不应该含有空白字符**
- 将属性名称和属性值放在一起，作为一个不间断的字符串。
- 用至少一个空格将不同的值分开
## 注释的书写
- 用`/*`开头，`*/`结尾
## 简写属性
- 规则：
	1. 四值：从顶部开始的瞬时值赋值
	2. 二值：从左往右赋值
🌰四值属性的简写：
```css
/* 在像 padding 和 margin 这样的 4 值简写语法中，
   数值的应用顺序是上、右、下、左（从顶部顺时针方向）。
   也有其他的简写类型，例如 2 值简写，
   它为顶部/底部设置 padding/margin，然后是左侧/右侧 */
padding: 10px 15px 15px 5px;
```

## @规则
- **作用**：用于控制样式表的规则和指令，可以用于导入其他样式表、嵌入条件语句、定义字体等；
	以下为一些常见的规则
1.  `@import` 导入其他CSS文件：
```css
@import url('styles.css');
或
@import "styles.css";
```
2.  `@media` 查询媒体信息并采取对应的样式化
```css
@media (min-width: 30em) {
  body {
    background-color: blue;
  }
}
```
如果浏览器的视口宽于 30em，接下来的媒体查询则定义了蓝色背景;
## CSS声明
- CSS声明：一个属性和一个值的配对，称为~
	1. 用`:`冒号分隔
	2. 当某个声明无效时，会自动被忽略
	3. 语言表达存在不确定时，以美式英语为主，比如应为`color`而非`colour`
- CSS声明块：一堆的CSS声明组成了~
- CSS规则集：选择器与CSS声明块组成了
### <mark style="background: #BBFABBA6;">以函数作为值</mark>
- `calc()`函数进行简单的计算
🌰:计算内容应该具有的宽度
```css
.outer {
  border: 5px solid black;
}

.box {
  padding: 10px;
  width: calc(90% - 30px);
  background-color: rebeccapurple;
  color: white;
}
```
```html
<div class="outer"><div class="box">内部盒子的宽度为 90% - 30px。</div></div>

```
- `transform`函数进行二维/三维的变换
🌰:
```css
.translate-example {
  transform: translate(50px, 100px);
}

.rotate-example {
  transform: rotate(45deg);
}

.scale-example {
  transform: scale(2, 0.5);
}

.skew-example {
  transform: skew(30deg, 20deg);
}

.matrix-example {
  transform: matrix(1, 0.5, -0.5, 1, 100, 100);
}
```
>- **`.translate-example`**：将元素沿 x 轴平移 50 像素，沿 y 轴平移 100 像素。
- **`.rotate-example`**：将元素旋转 45 度。
- **`.scale-example`**：将元素沿 x 轴放大 2 倍，沿 y 轴缩小 0.5 倍。
- **`.skew-example`**：将元素沿 x 轴倾斜 30 度，沿 y 轴倾斜 20 度。
- **`.matrix-example`**：应用 2D 转换矩阵，将元素进行复杂的组合变换。
也可以对多个函数值同时作用
```css
transform: translateX(10px) rotate(10deg) translateY(5px);
```
	作用效果为从右到左生效
## CSS选择器
>https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_selectors#%E5%9F%BA%E6%9C%AC%E9%80%89%E6%8B%A9%E5%99%A8

1. <mark style="background: #BBFABBA6;">基本选择器</mark>
	- 通用选择器 `*`
	- 元素选择器 `p` 选择`<p>`元素
	- 类选择器 
	- ID选择器
	- **属性选择器**
2. <mark style="background: #BBFABBA6;">分组选择器</mark>
	- `,` 不同的选择器组合在一起
	- ` `（空格） 组合器选择前一个元素的后代节点
	- `>` 前一个元素的直接子代
	- `A ~ B` 选择共享一个父节点，且在前一个节点A后任意位置的B
	- `A + B` 在上述的前提下，紧邻的兄弟选择器
	- `col || td` 匹配所有`<col>`内的`<td>`元素
3. 伪选择器
	详见[[obsidian/个人知识库/大一/Xlab/HTML CSS JS/CSS#📝CSS的伪类\|CSS#📝CSS的伪类]]
	
### <mark style="background: #ADCCFFA6;"><mark style="background: #BBFABBA6;">属性选择器</mark></mark>
🌰一览：
```css
/* 选择所有包含 title 属性的元素，文本颜色设为蓝色 */
[title] {
  color: blue;
}

/* 选择所有 type 属性值为 "text" 的 input 元素，添加边框 */
input[type="text"] {
  border: 1px solid #ccc;
}

/* 选择 class 属性值中包含 "featured" 单词的元素，背景颜色设为黄色 */
[class~="featured"] {
  background-color: yellow;
}

/* 选择所有 href 属性值以 "https" 开头的 a 元素，文本颜色设为绿色 */
a[href^="https"] {
  color: green;
}

/* 选择所有 href 属性值以 ".pdf" 结尾的 a 元素，文本颜色设为红色 */
a[href$=".pdf"] {
  color: red;
}

/* 选择所有 href 属性值中包含 "example" 子字符串的 a 元素，添加下划线 */
a[href*="example"] {
  text-decoration: underline;
}

/* 选择所有 lang 属性值以 "en" 开头的元素，文本样式设为斜体 */
[lang|="en"] {
  font-style: italic;
}

```
# 基本操作
## 颜色设置
>https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_colors/Applying_color#%E5%A6%82%E4%BD%95%E6%8F%8F%E8%BF%B0%E9%A2%9C%E8%89%B2
## 文字效果
### 重置下划线颜色
<mark style="background: #ADCCFFA6;">格式</mark>：🌰
```css
text-decoration-color: red;
```
### <mark style="background: #BBFABBA6;">添加阴影</mark>
<mark style="background: #ADCCFFA6;">格式</mark>：如果参数不完整，CSS将不会绘制
```css
text-shadow: h-offset v-offset blur color;
```
- `h-offset`（必需）：水平偏移，阴影相对于文本的水平位置。可以是正值（向右偏移）或负值（向左偏移）。
- `v-offset`（必需）：垂直偏移，阴影相对于文本的垂直位置。可以是正值（向下偏移）或负值（向上偏移）。
- `blur`（可选）：模糊半径，阴影的模糊程度。默认值为0，表示没有模糊效果。
- `color`（可选）：阴影颜色。如果没有指定，默认使用文本的颜色。
<mark style="background: #ADCCFFA6;">举例</mark>：🌰
```css
text-shadow: 2px 2px 5px black;
```
<mark style="background: #ADCCFFA6;">多重阴影</mark> :用逗号分隔多个阴影
```css
text-shadow: 2px 2px 5px black, -1px -1px 3px red, 1px 1px 2px blue;
```

## ❓操作之前需要如何连接
>在一个文件下下面分别常见html与css文件，并在html的**<mark style="background: #FFF3A3A6;">头部中引用css文件</mark>**
```html
<!doctype html>
<html lang="en">
  <head>
  
<link rel="stylesheet" href="styles.css" /> // 在本地文件目录中寻找名为stycles.css的文件

    <meta charset="utf-8" />
    <title>开始学习 CSS</title>
  </head>

  <body>
    <h1>我是一级标题</h1>

    <p>
      这是一个段落文本。在文本中有一个 <span>span element</span> 并且还有一个
      <a href="http://example.com">链接</a>.
    </p>

    <p>这是第二段。包含了一个 <em>强调</em> 元素。</p>

    <ul>
      <li>项目 1</li>
      <li>项目 2</li>
      <li>项目 <em>三</em></li>
    </ul>
  </body>
</html>

```
🌰下面是css文件的示例（不需要具有对html的定位）：
```css
h1 {
  color: red;
}
```
## 📝样式化
- <mark style="background: #BBFABBA6;">什么是选择器？</mark>
选择器就是CSS中选择生效的部位，一般是html中的markup(标记). 
- <mark style="background: #BBFABBA6;">如何一次对多个选择器进行操作？</mark>
只需要用逗号分隔即可，比如🌰:
```css
p,
li {
  color: green;
}

```
>表示将所有的列表和段落编变成绿色
- <mark style="background: #BBFABBA6;">样式化中可以改变什么？</mark>

- <mark style="background: #BBFABBA6;">如果我不喜欢默认的列表形式呢？</mark>
1. 你可以添加CSS代码去除这一默认属性：
```css
li {
  list-style-type: none;
}
```
2. 另外，`list-style-type`还可以用来做别的事情，下面给出总结
```css
/* Partial list of types */
list-style-type: disc;//默认的实心圆点
list-style-type: circle;//空心圆点
list-style-type: square;//实心方块
list-style-type: decimal;//十进制阿拉伯数字
list-style-type: georgian;//中日韩十进制数
list-style-type: trad-chinese-informal;//
list-style-type: kannada;

/* <string> value */
list-style-type: "-";

/* Identifier matching an @counter-style rule */
list-style-type: custom-counter-style;

/* Keyword value */
list-style-type: none;

/* Global values */
list-style-type: inherit;
list-style-type: initial;
list-style-type: unset;
```
---

### **<mark style="background: #FFF3A3A6;">根据位置确定样式</mark>**
①<mark style="background: #ADCCFFA6;">嵌套</mark>：用`空格`分隔选择器，表示在前者的内部对后者的作用
🌰列表项的段落内
```css
li em {
  color: rebeccapurple;
}
```
②<mark style="background: #ADCCFFA6;">后继</mark>：用`+`连接两个选择器`a`,`b`，表示对出现在a后且具有相同层级的b样式化
🌰:综合
```html
<h1>I am a level one heading</h1>

<p>This is a paragraph of text. In the text is a <span>span element</span>
and also a <a href="http://example.com">link</a>.</p>

<p>This is the second paragraph. It contains an <em>emphasized</em> element.</p>

<ul>
  <li>Item <span>one</span></li>
  <li>Item two</li>
  <li>Item <em>three</em></li>
</ul>
```
```css
li em {
  color: rebeccapurple;
}

h1 + p {
  font-size: 150%;
}
p  span {
    color : red;
}
```

---
### <mark style="background: #FFF3A3A6;">根据状态确定样式</mark>
1. 链接是否访问过的状态
🌰:
```html
<h1>I am a level one heading</h1>

<p>This is a paragraph of text. In the text is a <span>span element</span>
and also a <a href="http://example.com">link</a>.</p>

<p>This is the second paragraph. It contains an <em>emphasized</em> element.</p>

<ul>
  <li>Item one</li>
  <li>Item two</li>
  <li>Item <em>three</em></li>
</ul>
```
```css
a:link {
  color: pink;
}

a:visited {
  color: green;
}

a:hover {
  text-decoration: none;
}
```
	分别定义了未访问、已访问和鼠标悬停时的链接样式
### 其他样式化的操作
- <mark style="background: #BBFABBA6;">ID选择器</mark>
**步骤**：
1. 在HTML中设置ID属性
🌰:
```html
<h1 id="main-heading">Welcome to My Website</h1>
```
2. 在CSS中定义ID选择器
🌰:
```css
#main-heading {
    color: blue;            /* 文本颜色设置为蓝色 */
    text-align: center;     /* 文本居中对齐 */
    font-size: 2.5em;       /* 字体大小设置为2.5倍默认大小 */
}
```
注意：
	1. **格式**：在CSS中用`#`开头，接HTML中定义的ID名
	2. <mark style="background: #FFF3A3A6;">优先级最高</mark>，若同时匹配标签选择器、类选择器与ID选择器，将呈现ID选择器样式

- `*`通配符选择器：选择所有的元素
- `.box p` 组合选择器：选择所有`box`类中的`<p>`元素
- `.box p:first-child` 伪类选择器:选择所有`box`类的第一个子`<p>`元素
- `h1,h2,.intro` 组选择器：选择所有`<h1>`,`<h2>`元素以及`intro`类元素
- ---
### 层叠与优先级
####  **层叠**规则
在CSS中后出现的同级选择器将会覆盖前面定义的内容
#### **优先级**
>https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance#%E4%BC%98%E5%85%88%E7%BA%A7_2

注意：由<mark style="background: #FF5582A6;">内联样式</mark>所定义的样式，<mark style="background: #FF5582A6;">优先级最高</mark>！
注意的注意：`!important`相当于管理员介入，忽视以上所有规则，将元素选择该样式
🌰:
```css
.better {
  background-color: gray;
  border: none !important;
}
```
---
#### 覆盖声明的规则
>相互冲突的声明将按以下顺序应用，后一种声明将覆盖前一种声明：
1. 用户代理样式表中的声明（例如，浏览器的默认样式，在没有设置其他样式时使用）。
2. 用户样式表中的常规声明（由用户设置的自定义样式）。
3. 作者样式表中的常规声明（这些是我们 web 开发人员设置的样式）。
4. 作者样式表中的 `!important` 声明
5. 用户样式表中的 `!important` 声明
6. 用户代理样式表中的 `!important` 声明

🆙**备注：** 标记为 `!important` 的样式的优先级顺序是颠倒的。web 开发人员的样式表覆盖用户的样式表是有意义的，因此设计可以按预期进行，但是有时用户有充足的理由覆盖 web 开发人员的样式，正如上面提到的——这可以通过在他们的规则中使用 `!important` 来实现。

---
## ✨<mark style="background: #BBFABBA6;">利用Class进行样式化</mark>
- 在选择器内部加入`class="__"`的标记,对<mark style="background: #ADCCFFA6;">当前的选择器</mark>样式化
🌰:
```html

<p class="note">[Lights go up and wind blows; Caspian enters stage right]</p>

```
对应的CSS代码：
```css
.note {
  font-style: italic;
  font-weight: bold;
}
```
	1. 注意格式，css当中，类型前有`.`，类名后的操作用`{} `包括
	2. 如果在`.`前面添加HTML元素选择器，表示将所有该元素都采取后面的样式化
		🌰 : li.special{...}
---
-  在`class="_"`当中用<mark style="background: #ADCCFFA6;">空格分隔</mark>类名，可以对某个选择器同时<mark style="background: #ADCCFFA6;">作用多个样式化</mark>
🌰:
```html
<p class=" note editorial">Above point sounds a bit obvious. Remove/rewrite?</p>
```
对应的CSS代码：
```css
.note {
  font-style: italic;
  font-weight: bold;
}

.editorial {
  background: rgb(255, 0, 0, 0.25);
  padding: 10px;
}
```

---
- 使用<mark style="background: #ADCCFFA6;">伪元素</mark>`before`与`after`可以对该类的前后添加元素
🌰:HTML
```html
<div class="author">John Doe</div>
```
对应的CSS代码：
```css
.author:before {
  content: 'Author: ';
  font-weight: bold; /* 加粗字体 */
  color: blue; /* 文本颜色为蓝色 */
}
.author:after {
  content: ' ✍️';
  font-size: 1.2em; /* 调整图标大小 */
  margin-left: 5px; /* 添加左边距 */
}
```
---
### 📖<mark style="background: #ADCCFFA6;">元素属性</mark>
①**布局属性**
>这些属性用于控制元素的大小、显示方式和布局。
- `width` / `height`: 设置元素的宽度和高度。
- `margin`: 设置元素的外边距。
- `padding`: 设置元素的内边距。
- `display`: 设置元素的显示类型，如 `block`, `inline`, `flex` 等。
- `position`: 设置元素的定位方式，如 `static`, `relative`, `absolute`, `fixed`, `sticky`。
- `top`, `right`, `bottom`, `left`: 配合 `position` 属性使用，定义元素的位置。
- `float`: 控制元素的浮动。
- `clear`: 控制元素的清除浮动行为。
---
②**文本属性**
>控制文本的样式和对齐方式
- `color`: 设置文本颜色。
- `font-size`: 设置文本字体大小。
- `font-family`: 设置文本字体。
- `font-weight`: 设置文本字体粗细。
- `text-align`: 设置文本对齐方式，如 `left`, `right`, `center`, `justify`。
- `text-decoration`: 设置文本装饰，如 `underline`, `line-through`, `none`。
- `line-height`: 设置行高。
- `letter-spacing`: 设置字母间距。
- `text-transform`: 控制文本大小写，如 `uppercase`, `lowercase`, `capitalize`。
---
③**背景属性**
>设置元素的背景样式。
- `background-color`: 设置背景颜色。
- `background-image`: 设置背景图片。
- `background-size`: 设置背景图片大小。
- `background-repeat`: 设置背景图片是否重复。
- `background-position`: 设置背景图片的位置。
- `background-attachment`: 设置背景图片是否固定或随页面滚动。
- --
④**边框属性**
>设置元素的边框样式
- `border`: 简写属性，设置边框的宽度、样式和颜色。
- `border-width`: 设置边框宽度。
- `border-style`: 设置边框样式，如 `solid`, `dashed`, `dotted`, `none`。
- `border-color`: 设置边框颜色。
- `border-radius`: 设置边框圆角。
---
⑤**定位属性**
>用于精确控制元素的位置
- `z-index`: 设置元素的堆叠顺序。
- `overflow`: 设置溢出内容的处理方式，如 `visible`, `hidden`, `scroll`, `auto`
---
⑥**动画和过渡属性**
>设置元素的动画效果和过渡效果。
- `transition`: 简写属性，设置过渡效果的属性、时长、延迟和方式。
- `animation`: 简写属性，设置动画效果的名称、时长、时序函数、延迟、次数和方向。
---
⑦其他常用属性
- `opacity`: 设置元素的不透明度。
- `box-shadow`: 设置元素的阴影效果。
- `text-shadow`: 设置文本的阴影效果。
- `cursor`: 设置鼠标指针样式，如 `pointer`, `default`, `move` 等
### 😍鼠标悬停
>在类中用hover关键词实现

🌰:
```html
<div class="my-element">Hover over me!</div>
```
对应的CSS代码：
```css
.my-element {
  font-size:15px;
  width: 100px;
  height: 100px;
  background-color: lightblue;
  color: yellow;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: all 0.2s ease; /* 添加平滑过渡效果 */
}

.my-element:hover {
  background-color: green;
  color: red;
  transform: scale(1.1);
  font-size:20px;
}
```
注意，` `也就是空格不会被自动忽略，必须保证选择器或者类名与`:hover`之间不存在空格
#### 📝CSS的伪类
>你已经发现了，在上面的class中出现了`:{伪类名称}`的声明，这是CSS的**伪类**，下面介绍几种常见的伪类
- **`:hover`**  当用户将鼠标悬停在元素上时的状态
```css
a:hover {
  color: red;
}
```
注意，伪类不必和class一起使用，可以单独附在选择器后面
- **`:active`**  当用户激活元素（例如，点击按钮或链接）时的状态
```css
button:active {
  background-color: green;
}
```
- 其他
	1. **`:focus`**
	2. **`:visited`**  选择已访问的链接
	3. **`:link`**   未访问的链接
	4. **`:empty`** 选择没有子元素的元素
---
✨<mark style="background: #FFF3A3A6;">伪类可以直接写在html头部当中的`style`里，或者写在CSS代码中</mark>

---

🌰①
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    a:hover {
      color: red;
    }
    button:active {
      background-color: green;
    }
    input:focus {
      border-color: blue;
    }
    a:visited {
      color: purple;
    }
    p:first-child {
      font-weight: bold;
    }
    p:last-child {
      font-style: italic;
    }
    li:nth-child(2) {
      color: red;
    }
    p:only-child {
      color: green;
    }
    div:empty {
      background-color: yellow;
    }
  </style>
</head>
<body>

<a href="#section1">Visit section 1</a><br>
<a href="#section2">Visit section 2</a><br>

<button>Click me</button>

<input type="text" placeholder="Focus me">

<p>First paragraph</p>
<p>Second paragraph</p>
<p>Third paragraph</p>

<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

<div></div>

</body>
</html>

```
🌰②:
```html
<!DOCTYPE html>
<html lang="en">      <!-- lang表示文档的主语言，这里的en表示英语,此外还有fr发育法语,es西班牙语,zh中文等-->
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pseudo-class Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

<a href="#section1">Visit Section 1</a><br>
<a href="#section2">Visit Section 2</a><br>

<button>Click me</button>

<input type="text" placeholder="Focus me">

<p>First paragraph</p>
<p>Second paragraph</p>
<p>Third paragraph</p>

<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

<div></div>

</body>
</html>

```
对应的CSS代码⌨️
```css
/* Hover state for links */
a:hover {
  color: red;
}

/* Active state for buttons */
button:active {
  background-color: green;
}

/* Focus state for input fields */
input:focus {
  border-color: blue;
}

/* Visited state for links */
a:visited {
  color: purple;
}

/* First child paragraph */
p:first-child {
  font-weight: bold;
}

/* Last child paragraph */
p:last-child {
  font-style: italic;
}

/* Second child list item */
li:nth-child(2) {
  color: red;
}

/* Only child paragraph */
p:only-child {
  color: green;
}

/* Empty divs */
div:empty {
  background-color: yellow;
}
```
---
## 设置背景图像
可以用`backgroung-image`为元素设置一个或多个背景图像
🌰从文件夹中引用图像绘制：
```css
background-image: url("../../media/examples/lizard.png"),
                  url("../../media/examples/star.png");
```
- 规则：
	- 先指定的图像在后指定的图像图层上方
# CSS的组成
>https://developer.mozilla.org/zh-CN/docs/Learn/CSS/First_steps/How_CSS_is_structured#%E5%9C%A8_html_%E4%B8%AD%E5%BA%94%E7%94%A8_css
>---

## 外部样式表
- 元素：`link` ，放在头部\<head>内
- 格式：
🌰同一文件夹下
```html
<link rel="stylesheet" href="{CSS文件名}“ />
```
🌰不同文件夹需要指明路径：
```html
<!-- 在当前目录中，引用子文件夹 styles 中的样式表文件 -->
<link rel="stylesheet" href="styles/style.css" />

<!-- 在当前目录中，引用子文件夹 styles 中的子文件夹 general 中的样式表文件 -->
<link rel="stylesheet" href="styles/general/style.css" />

<!-- 在当前目录的父级目录中，引用子文件夹 styles 中的样式表文件 -->
<link rel="stylesheet" href="../styles/style.css" />
```
总结来说，`/`表示在文件夹中寻找,`..`表示进入当前目录的父级目录中寻找

---
## 内部样式表
- 格式：与其他CSS的代码一样，如果要将CSS的代码直接写入html，需要放置在头部`<head>`/`<style>`内
- 🌰：
```html
<!doctype html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8" />
    <title>我的 CSS 测试</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }
      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>这是我的第一个 CSS 示例</p>
  </body>
</html>
```
- 使用情形：一个内容管理系统，其外部 CSS 文件是不可以直接修改
---
## 内联样式
- 形式：将样式先写入html的`style`当中，再将后者放在主体`body`内部
- 一般不推荐这样写，因为不方便维护和阅读理解
- 适用情景：当工作要求仅能编辑html的主体部分时，可以用内联样式
🌰：
```html
<!doctype html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8" />
    <title>我的 CSS 测试</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">
      Hello World!
    </h1>
    <p style="color:red;">这是我的第一个 CSS 示例</p>
  </body>
</html>

```
---
# CSS的工作流程
>https://developer.mozilla.org/zh-CN/docs/Learn/CSS/First_steps/How_CSS_works#css_%E7%A9%B6%E7%AB%9F%E6%98%AF%E6%80%8E%E4%B9%88%E5%B7%A5%E4%BD%9C%E7%9A%84%EF%BC%9F

---
# 必要的关注点
## Flexbox
### 代码与基础
- 作用：
	- 用于设计复杂布局的强大工具
	- 主要目标是为容器内的元素提供一种高效的排列方式,使其能够适应不同的屏幕尺寸和设备
- 相关概念：
	- **Flex容器（Flex Container）**
		![Pasted image 20240517153508.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517153508.png)
	- **Flex项目（Flex Items）**：
		- Flex容器内的直接子元素被称为Flex项目
- 🌰使用实例：
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    /* 定义Flex容器 */
    .container {
      display: flex; /* 将容器设置为Flexbox容器 */
      
      /* flex-direction: 定义主轴方向 */
      /* row: 水平从左到右（默认） */
      /* row-reverse: 水平从右到左 */
      /* column: 垂直从上到下 */
      /* column-reverse: 垂直从下到上 */
      flex-direction: row; /* 可以改为row-reverse, column, column-reverse */

      /* flex-wrap: 定义是否换行 */
      /* nowrap: 不换行（默认） */
      /* wrap: 换行 */
      /* wrap-reverse: 反向换行 */
      flex-wrap: wrap; /* 可以改为nowrap, wrap-reverse */

      /* flex-flow: flex-direction 和 flex-wrap 的简写 */
      /* flex-flow: <flex-direction> <flex-wrap>; */
      flex-flow: row wrap; /* 可以改为column nowrap等组合 */

      /* justify-content: 定义在主轴上的对齐方式 */
      /* flex-start: 起始对齐（默认） */
      /* flex-end: 末端对齐 */
      /* center: 居中对齐 */
      /* space-between: 两端对齐，项目之间间隔相等 */
      /* space-around: 项目之间间隔相等，项目两边有半个间隔 */
      /* space-evenly: 项目之间间隔相等，项目两边有完整间隔 */
      justify-content: space-between; /* 可以改为flex-start, flex-end, center, space-around, space-evenly */

      /* align-items: 定义在交叉轴上的对齐方式 */
      /* stretch: 拉伸适应容器（默认） */
      /* flex-start: 交叉轴起始对齐 */
      /* flex-end: 交叉轴末端对齐 */
      /* center: 交叉轴居中对齐 */
      /* baseline: 项目基线对齐 */
      align-items: center; /* 可以改为flex-start, flex-end, stretch, baseline */

      /* align-content: 定义多行的内容在交叉轴上的对齐方式（适用于多行时） */
      /* stretch: 拉伸适应容器（默认） */
      /* flex-start: 交叉轴起始对齐 */
      /* flex-end: 交叉轴末端对齐 */
      /* center: 交叉轴居中对齐 */
      /* space-between: 多行两端对齐，行之间间隔相等 */
      /* space-around: 多行之间间隔相等，行两边有半个间隔 */
      align-content: space-between; /* 可以改为flex-start, flex-end, center, space-around */
      
      height: 100vh; /* 设置容器高度 */
      background-color: #f0f0f0; /* 设置容器背景颜色 */
    }
    
    /* 定义Flex项目 */
    .item {
      flex: 1; /* 设置项目的flex属性，项目平分空间 */
      padding: 20px; /* 设置项目内边距 */
      background-color: lightblue; /* 设置项目背景颜色 */
      margin: 10px; /* 设置项目外边距 */
      text-align: center; /* 设置项目文本居中 */
      flex-grow: 1;/*尝试向flex容器扩展空间*/
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
  </div>
</body>
</html>
```
### 官网海报
	 ![Pasted image 20240517160804.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240517160804.png)
### 应用
1. 导航栏
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flex Navigation Bar</title>
    <style>
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #333;
            padding: 10px 20px;
        }
        .navbar .logo {
            color: white;
            font-size: 24px;
        }
        .navbar .nav-links {
            display: flex;
            gap: 20px;
        }
        .navbar .nav-links a {
            color: white;
            text-decoration: none;
            padding: 8px 16px;
            background-color: #007BFF;
            border-radius: 5px;
        }
        .navbar .nav-links a:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="navbar">
        <div class="logo">MyLogo</div>
        <div class="nav-links">
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#services">Services</a>
            <a href="#contact">Contact</a>
        </div>
    </div>
</body>
</html>
```
>使用`justify-content: space-between`将logo和导航链接分开，并使用`gap`属性在导航链接之间创建间距

②tags集合
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tags Collection</title>
    <style>
        .tags-container {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            padding: 20px;
            background-color: #f9f9f9;
        }
        .tag {
            background-color: #007BFF;
            color: white;
            padding: 10px 20px;
            border-radius: 20px;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <div class="tags-container">
        <div class="tag">Tag 1</div>
        <div class="tag">Tag 2</div>
        <div class="tag">Tag 3</div>
        <div class="tag">Tag 4</div>
        <div class="tag">Tag 5</div>
    </div>
</body>
</html>
```
>创建了一个包含标签的容器，并使用`flex-wrap`属性使标签在容器中换行。

### 媒体查询与弹性盒子
🌰:二者结合实现最佳的呈现效果
```html
<!DOCTYPE html>
<head>
	<style>
.container {
            display: flex;
            flex-wrap: wrap;
            padding: 20px;
            gap: 20px;
        }
        .box {
            flex: 1 1 200px;
            background-color: #007BFF;
            color: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }

        /* Media Query for tablets */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
                align-items: center;
            }
            .box {
                width: 100%;
                margin-bottom: 20px;
            }
        }

        /* Media Query for mobile devices */
        @media (max-width: 480px) {
            .box {
                padding: 10px;
                font-size: 14px;
            }
        }
        </style>
</head>
```
- 平板设备（最大宽度768px）：当屏幕宽度小于或等于768像素时，容器的布局方向变为列方向（flex-direction: column），并且居中对齐（align-items: center）。每个.box元素的宽度设置为100%。
- 移动设备（最大宽度480px）：当屏幕宽度小于或等于480像素时，每个.box元素的内边距和字体大小减小，以适应较小的屏幕。

---
## 元素重叠时的遮盖关系
### <mark style="background: #BBFABBA6;">z-index</mark>
- 定义：
	- 用于控制HTML元素在Z轴上的叠放顺序的CSS属性
	- 用于绝对定位、固定定位或相对定位的元素
	- 值越大，元素越靠前；值越小，元素越靠后；可正可负
🌰红色盒子覆盖蓝色盒子：
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>z-index 示例</title>
<style>
  .box {
    position: absolute;
    width: 100px;
    height: 100px;
  }
  .red-box {
    background-color: red;
    top: 50px;
    left: 50px;
    z-index: 2;
  }
  .blue-box {
    background-color: blue;
    top: 80px;
    left: 80px;
    z-index: 1;
  }
</style>
</head>
<body>
  <div class="box red-box"></div>
  <div class="box blue-box"></div>
</body>
</html>
```
>红色的框具有更高的 **z-index** 值（2），因此显示在蓝色的框（ **z-index** 值为1）之上。

❓如果具有相同的`z-index`值呢？
	在HTML文档中的顺序将决定它们的堆叠顺序，文档中<mark style="background: #FFF3A3A6;">后面</mark>的元素<mark style="background: #FFF3A3A6;">会覆盖前面</mark>的元素。

## 基本样式的补充
>[CSS3 边框 | 菜鸟教程 (runoob.com)](https://www.runoob.com/css3/css3-borders.html)
或者MDN中：
>https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Backgrounds_and_borders
### <mark style="background: #BBFABBA6;">需要掌握的操作</mark>
1. 背景颜色 `backgroung-color`
2. 背景图像 `bakcgroung-image`
3. 控制背景的平铺行为 `bakcgroung-repeat`
4. 调整背景的大小 `background-size`
	`auto` 默认值 保持其原始尺寸
	**`length`**（例如 `px`, `em`, `rem`）
	**百分比值** `background-size: 50% 50%;`
	`cover` 按比例缩放，以<mark style="background: #FFF3A3A6;">完全覆盖</mark>背景区域，可能被裁剪
	`contain` 按比例缩放，以<mark style="background: #FFF3A3A6;">适应</mark>背景区域  （完全显示，但可能不会覆盖整个背景区域）
	**单个值**（例如 `100px`, `50%`) 此时第二个值被默认为`auto`
## Accessiblity 可访问性
- 目的：
	- 确保内容对于所有用户都易于访问和使用
	- 包括那些有视力障碍、听力障碍、运动障碍或其他残疾的用户。
### 📝方法
- **色彩对比和可读性**
>确保文本和背景之间有足够的对比度，使得文本对所有用户，包括视力受损的用户，都容易阅读。
-  **使用可缩放的单位**
>使用相对单位（如`em`, `rem`, `%`）而不是绝对单位（如`px`）;
>确保文本和布局可以根据用户的浏览器设置进行缩放。
```css
body {
    font-size: 1rem; /* 基于根元素的字体大小 */
}

h1 {
    font-size: 2rem; /* 两倍于根元素的字体大小 */
}
```
- **焦点样式**
>确保交互元素（如链接和按钮）在获得焦点时有清晰的可见样式; 
>对于使用键盘导航的用户特别重要。
```css
a:focus,
button:focus {
    outline: 2px solid #000;
    outline-offset: 2px;
}
```
- 确保足够的点击区域
```css
button,
a {
    padding: 10px 20px;
}
```
- 动画和过渡效果
```css
@media (prefers-reduced-motion: reduce) {
    * {
        animation: none;
        transition: none;
    }
}
```
---
## Responsive 响应设计 
### <mark style="background: #BBFABBA6;">媒体查询</mark>
🌰查询设备的特性来选择不同的样式
```css
/* 针对小屏幕设备 */
@media (max-width: 600px) {
    body {
        background-color: lightblue;
    }

    .container {
        padding: 10px;
    }
}

/* 针对中等屏幕设备 */
@media (min-width: 601px) and (max-width: 1024px) {
    body {
        background-color: lightgreen;
    }

    .container {
        padding: 20px;
    }
}

/* 针对大屏幕设备 */
@media (min-width: 1025px) {
    body {
        background-color: lightcoral;
    }

    .container {
        padding: 30px;
    }
}
```
### <mark style="background: #BBFABBA6;">流体网络布局</mark>
>使用百分比来定义，而非固定的像素，使布局在不同屏幕尺寸下自适应。
🌰：
```css
.container {
    width: 100%;
    padding: 20px;
}

.column {
    float: left;
    width: 50%;
}

/* 清除浮动 */
.row::after {
    content: "";
    clear: both;
    display: table;
}
```
### <mark style="background: #BBFABBA6;">灵活的图片和媒体</mark>
>使用`max-width`属性,确保图片和媒体内容不会超过其容器的宽度。
🌰:
```css
img {
    max-width: 100%;
    height: auto;
}

video {
    max-width: 100%;
    height: auto;
}
```
# 思考题
## ❓标签的选择
- **思考**：①用各色的HTML标签调节样式；②用单一的\<div>与\<span>等Division标签，主要用CSS进行样式调节，这两种方式各有什么优劣？
---
 ①优点：
 1. **简单直观**：
    
    - 对于小型项目或简单的样式调整，直接使用HTML标签可以快速实现效果。
    - 无需编写额外的CSS样式，初学者容易上手。
2. **即插即用**：
    
    - HTML标签自带样式，使用这些标签可以立即看到效果。
①缺点：
1. **样式分离性差**：
    - 样式和内容混杂在一起，不符合现代网页设计的最佳实践。
    - 难以维护和管理，当样式需要统一修改时，需要逐个标签进行调整。
2. **灵活性差**：
    - HTML标签提供的样式选项有限，无法实现复杂的设计需求。
    - <mark style="background: #FFF3A3A6;">难以响应式设计</mark>，不能根据设备和屏幕尺寸进行动态调整。
3. **语义不明确**：
    - 某些标签如`<b>`、`<i>`等，虽然能实现样式效果，但它们的语义含义较弱，不利于SEO和可访问性。
---
②优点：
1. **样式和内容分离**：
    - 使HTML结构清晰，样式集中在CSS文件中，便于维护和管理。
    - 修改样式只需在CSS中进行，便于全局更新和一致性维护。
2. **灵活性高**：
    - CSS提供丰富的样式属性和选择器，可以实现复杂的设计需求。
    - 便于响应式设计和动态样式调整，适应不同设备和屏幕尺寸。
3. **提高可维护性和复用性**：
    - 通过类和ID选择器，样式可以复用，减少冗余代码。
    - HTML结构语义化，增强SEO和可访问性。
②缺点：
1. **初始复杂性**：
    - 初学者可能觉得分离HTML和CSS较为复杂。
    - 需要编写和管理额外的CSS文件，增加了初始工作量。
2. **调试复杂性**：
    - 样式问题可能较难定位，需要借助浏览器开发者工具进行调试。
🌰：
```html
<p class="bold-italic">This is bold and italic text.</p>
```
```css
.bold-italic {
  font-weight: bold;
  font-style: italic;
}
```
---
**总结**：
1. 1. **使用各色HTML标签调节样式**：适用于小型、简单项目，快速实现样式效果，但不利于维护和扩展，不符合现代最佳实践。
2.  **使用`<div>`和`<span>`等标签，通过CSS调节样式**：适用于大型、复杂项目，符合现代网页设计的最佳实践，具有更高的灵活性和可维护性，但初学者可能需要时间适应。
