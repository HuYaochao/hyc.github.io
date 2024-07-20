---
layout: post
title: "W-HTML5-CSS-JS"
date: 2024-1-27
tags: [HTML5,CSS,JS]
comments: true
author: hyc
---


# 填空题

HTML： 超文本标记语言

HTML 中表格的 3 个基本组成：table 、tr、td

无序列表：` <ul>`

鼠标事件：

**click**: 当用户单击鼠标按钮时触发。

**dblclick**: 当用户双击鼠标按钮时触发。

**mousedown**: 当用户按下鼠标按钮时触发。

**mouseup**: 当用户释放鼠标按钮时触发。

**mouseover**: 当鼠标指针移动到元素上方时触发。

**mouseout**: 当鼠标指针移出元素时触发。

**mousemove**: 当鼠标指针在元素内移动时触发。

**mouseenter**: 当鼠标指针移到元素上时触发，仅在元素首次被进入时触发，不冒泡。

**mouseleave**: 当鼠标指针离开元素时触发，仅在元素首次被离开时触发，不冒泡。

**contextmenu**: 当用户右键点击鼠标时触发，通常用于显示上下文菜单。

URL: URL（统一资源定位符，Uniform Resource Locator）是指向网页或网络资源的地址

JS：

- 修改元素的两种方式： DOM 属性修改, innerHTML
- 事件三要素： 事件的目标（Event Target） , 事件的类型（Event Type） , 事件的处理程序（Event Handler）
- 获取自定义属性的方式： getAttribute() 方法 , dataset 属性
- 如何创建： createElement() 方法
- 删除： remove() 方法
- 两种定时器的语法 setTimeout() , setInterval()
- 清除两种定时器： clearTimeout() , clearInterval()

# 简答题

## css3 种引入方式：行内式、嵌入式（头部）、外联式

## css 基础选择器：

| 选择器       | 作用                           | 缺点                     | 使用情况   | 用法                 |
| ------------ | ------------------------------ | ------------------------ | ---------- | -------------------- |
| 标签选择器   | 可以选出所有相同的标签，比如 p | 不能差异化选择           | 较多       | p { color：red;}     |
| 类选择器     | 可以选出 1 个或者多个标签      | 可以根据需求选择         | 非常多     | .nav { color: red; } |
| id 选择器    | 一次只能选择器 1 个标签        | 只能使用一次             | 不推荐使用 | #nav {color: red;}   |
| 通配符选择器 | 选择所有的标签                 | 选择的太多，有部分不需要 | 不推荐使用 | \* {color: red;}     |

## 标签的显示模式：

| 元素模式   | 元素排列               | 设置样式               | 默认宽度         | 包含                     |
| ---------- | ---------------------- | ---------------------- | ---------------- | ------------------------ |
| 块级元素   | 一行只能放一个块级元素 | 可以设置宽度高度       | 容器的 100%      | 容器级可以包含任何标签   |
| 行内元素   | 一行可以放多个行内元素 | 不可以直接设置宽度高度 | 它本身内容的宽度 | 容纳文本或则其他行内元素 |
| 行内块元素 | 一行放多个行内块元素   | 可以设置宽度和高度     | 它本身内容的宽度 |                          |

## 诸简述外边距会带来哪些问题：

````
外边距（Margin）是CSS中用来控制元素与其周围元素之间的距离的重要属性。然而，外边距在布局和设计中可能会带来一些问题和挑战。以下是一些常见的外边距问题：

### 1. **外边距折叠（Margin Collapse）**

- **问题描述**：当垂直相邻的块级元素的上外边距和下外边距重叠时，较大的外边距将取代较小的外边距，而不是两者相加。这通常发生在父子元素和兄弟元素之间。
- **解决方案**：可以通过增加边框、填充或使用`overflow: hidden`来解决外边距折叠问题。
  ```css
  /* 添加边框解决外边距折叠 */
  .element {
      border: 1px solid transparent;
  }

  /* 使用填充解决外边距折叠 */
  .element {
      padding: 1px;
  }

  /* 使用 overflow 解决外边距折叠 */
  .element {
      overflow: hidden;
  }
````

### 2. **外边距合并（Margin Aggregation）**

- **问题描述**：当两个块级元素垂直相邻时，如果它们的外边距相加会导致意想不到的布局问题，例如额外的空间。
- **解决方案**：可以通过调整其中一个元素的外边距或者使用内边距（Padding）来避免外边距合并。

  ```css
  /* 调整其中一个元素的外边距 */
  .element1 {
    margin-bottom: 10px;
  }
  .element2 {
    margin-top: 0;
  }

  /* 使用内边距 */
  .element1 {
    padding-bottom: 10px;
  }
  ```

### 3. **外边距百分比问题**

- **问题描述**：外边距使用百分比时，参考的是包含块（通常是父元素）的宽度，而不是高度。这在响应式设计中可能会带来布局上的问题。
- **解决方案**：避免使用百分比来定义外边距，改用固定值（像素）或相对单位（例如 em、rem）。

  ```css
  /* 避免使用百分比 */
  .element {
    margin-top: 10px;
  }

  /* 使用相对单位 */
  .element {
    margin-top: 1em;
  }
  ```

### 4. **外边距的重置**

- **问题描述**：不同浏览器的默认样式表对元素外边距的处理不一致，可能导致跨浏览器的布局差异。
- **解决方案**：使用 CSS 重置样式或规范化样式表（如 Normalize.css）来消除浏览器默认的样式差异。

  ```css
  /* 简单的CSS重置 */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  /* 使用Normalize.css */
  @import url("https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css");
  ```

### 5. **外边距导致溢出问题**

- **问题描述**：在包含元素中应用外边距时，可能会导致包含元素的溢出，影响布局和滚动条的显示。
- **解决方案**：使用内边距替代外边距，或者调整布局结构避免溢出。
  ```css
  /* 使用内边距替代外边距 */
  .container {
    padding: 20px;
  }
  ```

## 什么是浮动?浮动有哪些作用?

浮动（Float）是一个在网页布局中常用的 CSS 属性。它可以让一个元素在页面中向左或向右浮动，并让后续的内容围绕该元素流动。

**清除浮动（Clearfix）**：当容器中所有子元素都浮动时，容器会出现高度塌陷的情况。为了避免这种情况，需要清除浮动，可以使用伪元素或`clear`属性

浮动元素会脱离文档的正常流，因此后续的元素会被其影响，需要额外处理。

## 伪元素和伪类是什么？

### 伪元素（Pseudo-elements）

伪元素用于选择元素的某个部分，如第一个字母、第一行等，或者在元素的内容前后插入内容。常见的伪元素有：

1. **::before** 和 **::after**：用于在元素内容之前或之后插入内容。
2. **::first-line**：用于选择元素的第一行文本。
3. **::first-letter**：用于选择元素的第一个字母。
4. **::selection**：用于选择被用户选中的文本部分

CSS 伪类用于选择元素的特定状态或条件

```
a:link {color:#FF0000;} /* 未访问的链接 */
a:visited {color:#00FF00;} /* 已访问的链接 */
a:hover {color:#FF00FF;} /* 鼠标悬停链接 */
a:active {color:#0000FF;} /* 已选中的链接 */
```

## 定位模式及其特点？

定位（positioning）模式决定了一个元素在页面上的定位方式。主要有五种定位模式：静态定位（static）、相对定位（relative）、绝对定位（absolute）、固定定位（fixed）和粘性定位（sticky）。

在 CSS 中，定位（positioning）模式决定了一个元素在页面上的定位方式。主要有五种定位模式：静态定位（static）、相对定位（relative）、绝对定位（absolute）、固定定位（fixed）和粘性定位（sticky）。每种定位模式都有其特点和应用场景。

### 1. 静态定位（static）

**特点**：

- 默认定位方式。
- 元素按照正常文档流进行排列。
- `top`、`right`、`bottom`、`left` 和 `z-index` 属性对静态定位的元素无效。

**示例**：

```css
.element {
  position: static;
}
```

### 2. 相对定位（relative）

**特点**：

- 元素在文档流中的位置保持不变，但可以使用 `top`、`right`、`bottom`、`left` 属性相对于其正常位置进行偏移。
- 偏移后，元素仍然占据其原本的空间。

**示例**：

```css
.element {
  position: relative;
  top: 10px;
  left: 20px;
}
```

### 3. 绝对定位（absolute）

**特点**：

- 元素脱离文档流，不占据空间，其他元素会填补它的位置。
- 使用 `top`、`right`、`bottom`、`left` 属性相对于最近的定位祖先元素（即 `position` 不为 `static` 的祖先元素）进行定位。
- 如果没有定位祖先，则相对于初始包含块（通常是视口）进行定位。

**示例**：

```css
.container {
  position: relative;
}
.element {
  position: absolute;
  top: 10px;
  left: 20px;
}
```

### 4. 固定定位（fixed）

**特点**：

- 元素脱离文档流，不占据空间。
- 使用 `top`、`right`、`bottom`、`left` 属性相对于视口（viewport）进行定位。
- 滚动页面时，固定定位的元素保持在固定位置。

**示例**：

```css
.element {
  position: fixed;
  top: 10px;
  left: 20px;
}
```

### 5. 粘性定位（sticky）

**特点**：

- 元素在到达设定的偏移位置前为相对定位，之后为固定定位。
- 适用于滚动页面时，希望元素在特定位置保持固定，但超过某一临界点后继续随文档流移动。

**示例**：

```css
.element {
  position: sticky;
  top: 10px;
}
```

### 总结

- **静态定位**：默认定位方式，元素按正常文档流排列。
- **相对定位**：相对于元素的正常位置进行偏移，仍占据原本空间。
- **绝对定位**：脱离文档流，相对于最近的定位祖先元素定位。
- **固定定位**：脱离文档流，相对于视口定位，页面滚动时位置固定。
- **粘性定位**：结合相对定位和固定定位，元素在滚动到设定偏移位置时变为固定定位。

## css 的复合选择器有哪些？简述

CSS 复合选择器（combinator selectors）是将多个简单选择器（如类型选择器、类选择器、ID 选择器等）组合在一起以便更精确地选择 HTML 元素。

复合选择器包括后代选择器、子选择器、相邻兄弟选择器和一般兄弟选择器。

CSS 复合选择器（combinator selectors）是将多个简单选择器（如类型选择器、类选择器、ID 选择器等）组合在一起以便更精确地选择 HTML 元素。复合选择器包括后代选择器、子选择器、相邻兄弟选择器和一般兄弟选择器。下面是每种复合选择器的简述及示例。

### 1. 后代选择器（Descendant Selector）

后代选择器用于选择某元素的所有后代元素（不管其直接或间接层级）。

**语法**：

```css
A B {
  ...;
}
```

**示例**：

```css
div p {
  color: blue;
}
```

此选择器会将所有位于 `div` 内部的 `p` 元素的文字颜色设置为蓝色。

### 2. 子选择器（Child Selector）

子选择器用于选择某元素的直接子元素。

**语法**：

```css
A > B {
  ...;
}
```

**示例**：

```css
ul > li {
  list-style-type: none;
}
```

此选择器会将所有直接位于 `ul` 内的 `li` 元素的列表样式设置为无序列表。

### 3. 相邻兄弟选择器（Adjacent Sibling Selector）

相邻兄弟选择器用于选择紧接在另一个指定元素之后的兄弟元素。

**语法**：

```css
A + B {
  ...;
}
```

**示例**：

```css
h1 + p {
  margin-top: 0;
}
```

此选择器会将所有紧跟在 `h1` 元素后的第一个 `p` 元素的上边距设置为 0。

### 4. 一般兄弟选择器（General Sibling Selector）

一般兄弟选择器用于选择所有位于另一个指定元素之后的兄弟元素。

**语法**：

```css
A ~ B {
  ...;
}
```

**示例**：

```css
h1 ~ p {
  color: green;
}
```

此选择器会将所有位于 `h1` 元素之后的 `p` 元素的文字颜色设置为绿色。

### 5. 组选择器（Group Selector）

组选择器用于将多个选择器组合在一起，以便为它们应用相同的样式。

**语法**：

```css
A,
B,
C {
  ...;
}
```

**示例**：

```css
h1,
h2,
h3 {
  font-family: Arial, sans-serif;
}
```

此选择器会将 `h1`、`h2` 和 `h3` 元素的字体设置为 Arial 或 sans-serif。

### 6. 属性选择器（Attribute Selector）

属性选择器用于选择具有指定属性的元素。

**语法**：

```css
[attribute] {
  ...;
}
[attribute="value"] {
  ...;
}
[attribute~="value"] {
  ...;
}
[attribute|="value"] {
  ...;
}
[attribute^="value"] {
  ...;
}
[attribute$="value"] {
  ...;
}
[attribute*="value"] {
  ...;
}
```

**示例**：

```css
input[type="text"] {
  border: 1px solid #000;
}
```

此选择器会将所有类型为文本的 `input` 元素的边框设置为黑色实线。

### 7. 伪类选择器和伪元素选择器（Pseudo-classes and Pseudo-elements）

伪类选择器和伪元素选择器用于选择元素的特定状态或特定部分。

**伪类选择器语法**：

```css
selector:pseudo-class {
  ...;
}
```

**示例**：

```css
a:hover {
  color: red;
}
```

此选择器会将鼠标悬停在 `a` 元素上的文字颜色设置为红色。

**伪元素选择器语法**：

```css
selector::pseudo-element {
  ...;
}
```

**示例**：

```css
p::first-line {
  font-weight: bold;
}
```

此选择器会将所有 `p` 元素的第一行文字设置为粗体。

## 表单控件 input 的 type 属性值？

HTML 中的`<input>`元素用于创建多种不同类型的表单控件，通过设置其`type`属性，可以指定控件的类型。以下是`<input>`元素的`type`属性可能的值及其描述：

1. **text**：单行文本输入。

   ```html
   <input type="text" />
   ```

2. **password**：密码输入，内容以星号或点号显示。

   ```html
   <input type="password" />
   ```

3. **submit**：提交按钮，用于提交表单。

   ```html
   <input type="submit" value="Submit" />
   ```

4. **reset**：重置按钮，用于重置表单中的所有控件。

   ```html
   <input type="reset" value="Reset" />
   ```

5. **button**：普通按钮，可通过 JavaScript 实现自定义功能。

   ```html
   <input type="button" value="Click Me" />
   ```

6. **radio**：单选按钮，允许用户在一组选项中选择一个。

   ```html
   <input type="radio" name="option" value="1" /> Option 1
   <input type="radio" name="option" value="2" /> Option 2
   ```

7. **checkbox**：复选框，允许用户在一组选项中选择多个。

   ```html
   <input type="checkbox" name="item" value="1" /> Item 1
   <input type="checkbox" name="item" value="2" /> Item 2
   ```

8. **file**：文件选择器，允许用户选择文件上传。

   ```html
   <input type="file" />
   ```

9. **hidden**：隐藏输入字段，不在页面上显示，但会提交其值。

   ```html
   <input type="hidden" name="hiddenField" value="hiddenValue" />
   ```

10. **image**：图像提交按钮，点击时提交表单，类似`submit`。

    ```html
    <input type="image" src="submit.png" alt="Submit" />
    ```

11. **date**：日期选择器，允许用户选择日期。

    ```html
    <input type="date" />
    ```

12. **datetime-local**：日期和时间选择器，不包括时区。

    ```html
    <input type="datetime-local" />
    ```

13. **month**：月选择器，允许用户选择月份和年份。

    ```html
    <input type="month" />
    ```

14. **week**：周选择器，允许用户选择年份中的某一周。

    ```html
    <input type="week" />
    ```

15. **time**：时间选择器，允许用户选择时间。

    ```html
    <input type="time" />
    ```

16. **number**：数字输入，带有加减按钮，限制输入为数字。

    ```html
    <input type="number" min="1" max="10" />
    ```

17. **range**：范围输入，带有滑块，允许用户选择一个范围值。

    ```html
    <input type="range" min="1" max="100" />
    ```

18. **color**：颜色选择器，允许用户选择颜色。

    ```html
    <input type="color" />
    ```

19. **email**：电子邮件输入，验证电子邮件格式。

    ```html
    <input type="email" />
    ```

20. **tel**：电话号码输入，验证电话号码格式。

    ```html
    <input type="tel" />
    ```

21. **url**：URL 输入，验证 URL 格式。

    ```html
    <input type="url" />
    ```

22. **search**：搜索输入，带有清除按钮。
    ```html
    <input type="search" />
    ```

通过设置`<input>`元素的`type`属性，可以创建适合不同输入需求的表单控件，提升用户体验和表单数据的准确性。

---

## JavaScript 的数据类型?

JavaScript 有七种基本数据类型（也称为原始类型）和一种对象类型。每种类型有其特定的特性和用途。以下是详细的介绍：

### 基本数据类型（Primitive Types）

1. **字符串（String）**：用于表示文本数据。字符串是不可变的，可以使用单引号、双引号或反引号（用于模板字符串）表示。

   ```javascript
   let str1 = "Hello";
   let str2 = "World";
   let str3 = `Hello, ${str2}`;
   ```

2. **数值（Number）**：用于表示整数和浮点数。JavaScript 中没有专门的整数类型，所有数值都是浮点数。

   ```javascript
   let intNum = 42;
   let floatNum = 3.14;
   ```

3. **大整数（BigInt）**：用于表示任意精度的整数。使用`n`后缀表示。

   ```javascript
   let bigIntNum = 9007199254740991n;
   ```

4. **布尔值（Boolean）**：用于表示真（true）或假（false）。

   ```javascript
   let isTrue = true;
   let isFalse = false;
   ```

5. **未定义（Undefined）**：表示变量未赋值时的默认值。

   ```javascript
   let unassignedVar;
   console.log(unassignedVar); // 输出: undefined
   ```

6. **空值（Null）**：表示空或无值的对象指针。

   ```javascript
   let emptyVar = null;
   ```

7. **符号（Symbol）**：表示唯一且不可变的标识符。通常用于对象属性的唯一标识。
   ```javascript
   let sym = Symbol("uniqueIdentifier");
   ```

### 对象类型（Object）

1. **对象（Object）**：用于存储键值对和复杂数据结构。对象可以通过对象字面量、构造函数或类创建。

   ```javascript
   let obj = {
     name: "Alice",
     age: 25,
   };
   ```

2. **数组（Array）**：对象的特殊类型，用于存储有序的集合。

   ```javascript
   let arr = [1, 2, 3, 4, 5];
   ```

3. **函数（Function）**：对象的特殊类型，用于定义可调用的代码块。

   ```javascript
   function greet(name) {
     return `Hello, ${name}!`;
   }
   ```

4. **日期（Date）**：内置对象，用于处理日期和时间。

   ```javascript
   let now = new Date();
   ```

5. **正则表达式（RegExp）**：内置对象，用于模式匹配字符串。

   ```javascript
   let regex = /hello/i;
   ```

6. **地图（Map）**：用于存储键值对，键可以是任意类型。

   ```javascript
   let map = new Map();
   map.set("key", "value");
   ```

7. **集合（Set）**：用于存储唯一值的集合。
   ```javascript
   let set = new Set([1, 2, 3, 3]);
   ```

### 特殊值

- **NaN**（Not-a-Number）：表示不是一个合法数值。

  ```javascript
  let notNumber = NaN;
  ```

- **Infinity 和 -Infinity**：表示正无穷大和负无穷大。
  ```javascript
  let positiveInfinity = Infinity;
  let negativeInfinity = -Infinity;
  ```

### 类型检测

可以使用`typeof`运算符来检测变量的数据类型：

```javascript
console.log(typeof 42); // 输出: "number"
console.log(typeof "Hello"); // 输出: "string"
console.log(typeof true); // 输出: "boolean"
console.log(typeof undefined); // 输出: "undefined"
console.log(typeof null); // 输出: "object"（这是一个历史遗留的bug）
console.log(typeof Symbol("sym")); // 输出: "symbol"
console.log(typeof {}); // 输出: "object"
console.log(typeof []); // 输出: "object"
console.log(typeof function () {}); // 输出: "function"
console.log(typeof BigInt(123)); // 输出: "bigint"
```

## 循环语句以及区别?

JavaScript 提供了几种循环语句，用于重复执行代码块。每种循环语句有其特定的用途和特点。以下是 JavaScript 中常见的循环语句及其区别：

### 1. `for` 循环

`for` 循环是最常用的循环之一，适用于已知循环次数的情况。它包含三个部分：初始化表达式、条件表达式和增量表达式。

**语法**：

```javascript
for (initialization; condition; increment) {
  // 代码块
}
```

**示例**：

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

### 2. `while` 循环

`while` 循环在条件为 `true` 时重复执行代码块，适用于条件控制的循环。

**语法**：

```javascript
while (condition) {
  // 代码块
}
```

**示例**：

```javascript
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

### 3. `do...while` 循环

`do...while` 循环与 `while` 循环类似，但它在条件检查之前至少执行一次代码块。

**语法**：

```javascript
do {
  // 代码块
} while (condition);
```

**示例**：

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

### 4. `for...in` 循环

`for...in` 循环用于遍历对象的可枚举属性。注意，它不适用于遍历数组，因为它遍历的是属性名而不是索引。

**语法**：

```javascript
for (key in object) {
  // 代码块
}
```

**示例**：

```javascript
const obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
  console.log(key, obj[key]);
}
```

### 5. `for...of` 循环

`for...of` 循环用于遍历可迭代对象（如数组、字符串、Map、Set 等），它遍历的是值而不是属性名。

**语法**：

```javascript
for (value of iterable) {
  // 代码块
}
```

**示例**：

```javascript
const arr = [1, 2, 3, 4, 5];
for (let value of arr) {
  console.log(value);
}
```

### 区别

- **`for` 循环**：适用于已知循环次数的情况。通过三个表达式（初始化、条件和增量）来控制循环。
- **`while` 循环**：适用于条件控制的循环，只要条件为真就会重复执行代码块。条件检查在循环开始之前。

- **`do...while` 循环**：类似 `while` 循环，但至少会执行一次代码块，因为条件检查在代码块之后。

- **`for...in` 循环**：用于遍历对象的可枚举属性，适合对象而非数组，因为遍历的是属性名。

- **`for...of` 循环**：用于遍历可迭代对象，适合数组、字符串、Map、Set 等，遍历的是值。

### 示例对比

**`for` 循环**：

```javascript
for (let i = 0; i < 3; i++) {
  console.log(i); // 输出 0, 1, 2
}
```

**`while` 循环**：

```javascript
let i = 0;
while (i < 3) {
  console.log(i); // 输出 0, 1, 2
  i++;
}
```

**`do...while` 循环**：

```javascript
let i = 0;
do {
  console.log(i); // 输出 0, 1, 2
  i++;
} while (i < 3);
```

**`for...in` 循环**：

```javascript
const obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
  console.log(key); // 输出 "a", "b", "c"
}
```

**`for...of` 循环**：

```javascript
const arr = ["a", "b", "c"];
for (let value of arr) {
  console.log(value); // 输出 "a", "b", "c"
}
```

理解这些循环语句及其适用场景，可以帮助你在编写 JavaScript 代码时选择最合适的循环结构，提高代码的可读性和性能。

## 构造函数创建一个对象，属性和方法自定义，手写代码

构造函数是 JavaScript 中用于创建对象的一种方式。使用构造函数可以创建具有相同属性和方法的多个对象。下面是一个示例，演示如何使用构造函数创建一个对象，并自定义其属性和方法。

假设我们要创建一个表示人的对象，每个人都有名字、年龄和职业，并且有一个方法用于显示这些信息。以下是实现的步骤和代码：

### 步骤

1. 创建一个构造函数 `Person`，在其中定义对象的属性（`name`、`age` 和 `job`）。
2. 在构造函数的原型上定义一个方法 `displayInfo`，用于显示对象的信息。

### 代码

```javascript
// 构造函数
function Person(name, age, job) {
  this.name = name;
  this.age = age;
  this.job = job;
}

// 在原型上定义一个方法
Person.prototype.displayInfo = function () {
  console.log(`Name: ${this.name}, Age: ${this.age}, Job: ${this.job}`);
};

// 使用构造函数创建对象
let person1 = new Person("Alice", 30, "Engineer");
let person2 = new Person("Bob", 25, "Designer");

// 调用方法
person1.displayInfo(); // 输出: Name: Alice, Age: 30, Job: Engineer
person2.displayInfo(); // 输出: Name: Bob, Age: 25, Job: Designer
```

### 解释

1. **构造函数 `Person`**：使用 `function` 关键字定义构造函数，并在其中定义属性。`this` 关键字用于指向将要创建的对象实例。

   ```javascript
   function Person(name, age, job) {
     this.name = name;
     this.age = age;
     this.job = job;
   }
   ```

2. **方法 `displayInfo`**：将方法定义在构造函数的原型上，这样所有实例共享同一个方法，节省内存。

   ```javascript
   Person.prototype.displayInfo = function () {
     console.log(`Name: ${this.name}, Age: ${this.age}, Job: ${this.job}`);
   };
   ```

3. **创建对象实例**：使用 `new` 关键字调用构造函数创建对象实例。

   ```javascript
   let person1 = new Person("Alice", 30, "Engineer");
   let person2 = new Person("Bob", 25, "Designer");
   ```

4. **调用方法**：调用对象的方法 `displayInfo`，输出对象的信息。
   ```javascript
   person1.displayInfo(); // 输出: Name: Alice, Age: 30, Job: Engineer
   person2.displayInfo(); // 输出: Name: Bob, Age: 25, Job: Designer
   ```

通过这种方式，可以方便地创建多个具有相同属性和方法的对象实例，且这些实例之间共享方法，节省内存，提高性能。

## break、continue、return 区别

`return` 语句用于终止函数的执行，并返回一个指定的值给函数的调用者。如果没有指定返回值，则返回 `undefined`。

## 局部变量和全局变量的区别

### 区别总结

- **作用域**：
  - 局部变量只能在其声明的函数或块级作用域内部访问。
  - 全局变量可以在整个代码的任何地方访问。
- **生命周期**：
  - 局部变量的生命周期仅限于其声明的函数或块级作用域的执行期间。
  - 全局变量的生命周期从其声明开始，直到页面关闭或被显式销毁。
- **命名冲突**：
  - 局部变量具有更小的命名冲突可能性，因为它们的作用域有限。
  - 全局变量可能会因为不同模块或库中相同名称的全局变量而导致命名冲突和不可预测的行为。

## 定义函数的两种写法

函数声明（Function Declaration）和函数表达式（Function Expression）

在 JavaScript 中，可以通过多种方式定义函数。最常用的两种方式是函数声明（Function Declaration）和函数表达式（Function Expression）。每种方式都有其特点和适用场景。以下是这两种方式的详细介绍和示例：

### 1. 函数声明（Function Declaration）

函数声明使用 `function` 关键字直接定义一个函数，并且必须给函数命名。函数声明可以在其定义之前调用，因为 JavaScript 在执行代码时会将函数声明提升（hoist）到其作用域的顶部。

**语法**：

```javascript
function functionName(parameters) {
  // 代码块
}
```

**示例**：

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet("Alice")); // 输出: Hello, Alice!
```

### 2. 函数表达式（Function Expression）

函数表达式也是使用 `function` 关键字定义的，但它是将函数赋值给变量。这种函数可以是匿名的，也可以是有名称的。函数表达式不会提升，因此在定义之前调用会导致错误。

**语法**：

```javascript
const functionName = function (parameters) {
  // 代码块
};
```

**示例**：

```javascript
const greet = function (name) {
  return `Hello, ${name}!`;
};

console.log(greet("Bob")); // 输出: Hello, Bob!
```

### 区别

1. **提升（Hoisting）**：

   - 函数声明会提升，因此可以在定义之前调用。
   - 函数表达式不会提升，必须在定义之后调用。

2. **匿名函数**：

   - 函数声明必须有名称。
   - 函数表达式可以是匿名的。

3. **可读性**：
   - 函数声明在代码中更为显眼，便于查找。
   - 函数表达式常用于需要将函数作为值传递或赋值的场景。

### 示例对比

**函数声明**：

```javascript
console.log(add(2, 3)); // 输出: 5

function add(a, b) {
  return a + b;
}
```

**函数表达式**：

```javascript
console.log(add(2, 3)); // 错误: add is not defined

const add = function (a, b) {
  return a + b;
};

console.log(add(2, 3)); // 输出: 5
```

### 箭头函数（Arrow Function）

箭头函数是函数表达式的一种简写形式，特别适用于定义简短的函数，并且没有自己的 `this` 绑定。箭头函数也不会提升。

**语法**：

```javascript
const functionName = (parameters) => {
  // 代码块
};
```

**示例**：

```javascript
const greet = (name) => `Hello, ${name}!`;

console.log(greet("Charlie")); // 输出: Hello, Charlie!
```

### 总结

- **函数声明**：适用于需要提升的场景，便于代码组织和查找。
- **函数表达式**：适用于将函数赋值给变量或传递函数作为值的场景，通常结合箭头函数使用。

## 手写冒泡排序

冒泡排序（Bubble Sort）是一种简单的排序算法，它重复地遍历要排序的列表，比较相邻的两个元素，并交换它们直到整个列表有序。这种算法的名字由于越小（或越大）的元素会经由交换慢慢“浮”到数列的顶端，因此称为冒泡排序。

下面是 JavaScript 中冒泡排序的手写实现：

```javascript
function bubbleSort(arr) {
  const len = arr.length;
  // 外层循环控制比较的轮数，共需比较 len - 1 轮
  for (let i = 0; i < len - 1; i++) {
    // 内层循环进行相邻元素的比较与交换
    for (let j = 0; j < len - 1 - i; j++) {
      // 如果前面的元素大于后面的元素，则交换它们
      if (arr[j] > arr[j + 1]) {
        // 使用解构赋值进行交换
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
      }
    }
  }
  return arr;
}

// 示例
const array = [64, 34, 25, 12, 22, 11, 90];
console.log("排序前:", array);
console.log("排序后:", bubbleSort(array));
```

### 解释：

1. **函数 `bubbleSort`**：定义了一个函数来实现冒泡排序。
2. **参数 `arr`**：传入待排序的数组。
3. **`len` 变量**：存储数组的长度，避免多次计算。
4. **外层循环 `for (let i = 0; i < len - 1; i++)`**：控制排序的轮数，每轮确定一个最大值（或最小值）的位置。
5. **内层循环 `for (let j = 0; j < len - 1 - i; j++)`**：在每轮比较中，通过相邻元素比较和交换将较大（或较小）的元素向右侧移动。
6. **条件判断 `if (arr[j] > arr[j + 1])`**：如果当前元素大于相邻的后一个元素，则交换它们的位置。
7. **交换操作 `[arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];`**：使用解构赋值进行元素交换。
8. **返回排序后的数组 `return arr;`**：函数返回排序完成后的数组。

### 示例输出：

对于数组 `[64, 34, 25, 12, 22, 11, 90]`，经过冒泡排序后的输出结果为：

```
排序前: [64, 34, 25, 12, 22, 11, 90]
排序后: [11, 12, 22, 25, 34, 64, 90]
```

这段代码演示了冒泡排序的基本原理和实现方法，通过多次比较和交换来达到排序数组的目的。

## 获取 DOM 元素的五种方法及其区别?

在 JavaScript 中获取 DOM 元素有多种方法，每种方法适用于不同的场景和需求。以下是常见的五种获取 DOM 元素的方法及它们的区别：

### 1. `getElementById`

`getElementById` 方法通过指定元素的 `id` 属性来获取 DOM 元素。因为 `id` 在文档中应该是唯一的，所以该方法返回的是单个元素（如果存在匹配的元素），或者是 `null`（如果没有匹配的元素）。

**示例**：

```javascript
let element = document.getElementById("myElementId");
```

**特点**：

- 返回匹配指定 `id` 的元素，如果不存在则返回 `null`。
- 适用于获取页面中唯一标识的元素。

### 2. `getElementsByClassName`

`getElementsByClassName` 方法通过指定元素的类名来获取 DOM 元素，返回一个 HTMLCollection 对象，其中包含所有指定类名的元素。

**示例**：

```javascript
let elements = document.getElementsByClassName("myClassName");
```

**特点**：

- 返回所有匹配指定类名的元素的集合。
- 如果没有匹配的元素，返回空的 HTMLCollection。
- 可以通过索引访问集合中的元素。

### 3. `getElementsByTagName`

`getElementsByTagName` 方法通过指定元素的标签名来获取 DOM 元素，返回一个 HTMLCollection 对象，其中包含所有指定标签名的元素。

**示例**：

```javascript
let elements = document.getElementsByTagName("div");
```

**特点**：

- 返回所有匹配指定标签名的元素的集合。
- 如果没有匹配的元素，返回空的 HTMLCollection。
- 可以通过索引访问集合中的元素。

### 4. `querySelector`

`querySelector` 方法通过 CSS 选择器来获取匹配的第一个元素，如果没有找到匹配的元素，则返回 `null`。

**示例**：

```javascript
let element = document.querySelector("#myElementId");
// 或者
let element = document.querySelector(".myClassName");
// 或者
let element = document.querySelector("div");
```

**特点**：

- 返回第一个匹配 CSS 选择器的元素。
- 如果没有匹配的元素，返回 `null`。
- 可以使用 CSS 选择器语法选择元素，非常灵活。

### 5. `querySelectorAll`

`querySelectorAll` 方法通过 CSS 选择器来获取所有匹配的元素，返回一个 NodeList 对象，其中包含所有匹配的元素。

**示例**：

```javascript
let elements = document.querySelectorAll(".myClassName");
// 或者
let elements = document.querySelectorAll("div");
```

**特点**：

- 返回所有匹配 CSS 选择器的元素的 NodeList。
- 如果没有匹配的元素，返回空的 NodeList。
- 可以通过索引访问 NodeList 中的元素。

### 区别总结

- **返回类型**：

  - `getElementById` 返回单个元素或 `null`。
  - `getElementsByClassName` 和 `getElementsByTagName` 返回 HTMLCollection 对象。
  - `querySelector` 返回第一个匹配的元素或 `null`。
  - `querySelectorAll` 返回所有匹配的元素的 NodeList。

- **适用范围**：

  - `getElementById` 用于获取具有唯一 `id` 的元素。
  - `getElementsByClassName` 和 `getElementsByTagName` 适用于获取多个具有相同类名或标签名的元素。
  - `querySelector` 和 `querySelectorAll` 可以使用更复杂的 CSS 选择器语法，获取符合条件的元素，更为灵活。

- **兼容性**：
  - `getElementById`、`getElementsByClassName` 和 `getElementsByTagName` 是较早的 DOM 方法，兼容性较好。
  - `querySelector` 和 `querySelectorAll` 从 DOM Level 4 开始引入，较新，但现代浏览器基本支持。

## 内置对象有哪些?以及每个对象中常用的方法?

JavaScript 中的内置对象是指在运行时自动创建的对象，它们可以直接使用而无需显式地实例化。这些对象包括全局对象、原生对象和构造函数对象等，它们提供了各种功能和方法来处理不同的任务。以下是一些常见的内置对象及每个对象中常用的方法的概述：

### 1. 全局对象（Global Objects）

全局对象是 JavaScript 运行环境中的顶层对象，在浏览器中通常是 `window` 对象，在 Node.js 中是 `global` 对象。它们提供了一些全局性的方法和属性。

**常见方法**：

- `setTimeout`, `setInterval`: 设置定时器，用于延时执行或定期执行函数。
- `clearTimeout`, `clearInterval`: 清除定时器。
- `console.log`, `console.error`, `console.warn`: 输出日志消息到控制台。
- `parseInt`, `parseFloat`: 将字符串解析为整数或浮点数。
- `isNaN`, `isFinite`: 检查一个值是否是 `NaN` 或有限数。
- `encodeURIComponent`, `decodeURIComponent`: 对 URI 进行编码和解码。

### 2. 数字对象（Number）

JavaScript 中的数字对象是基本数据类型 `number` 的包装对象，提供了处理数字的方法。

**常见方法**：

- `toFixed`: 将数字格式化为指定小数位的字符串。
- `toPrecision`: 将数字格式化为指定精度的字符串。
- `toString`: 将数字转换为字符串。
- `valueOf`: 返回数字的原始值。
- `isNaN`, `isFinite`: 与全局对象中的同名方法相同，检查数字是否是 `NaN` 或有限数。

### 3. 字符串对象（String）

JavaScript 中的字符串对象是基本数据类型 `string` 的包装对象，提供了处理字符串的方法。

**常见方法**：

- `charAt`, `charCodeAt`: 获取指定位置的字符或字符编码。
- `concat`: 连接字符串。
- `indexOf`, `lastIndexOf`: 查找子字符串的位置。
- `toUpperCase`, `toLowerCase`: 将字符串转换为大写或小写。
- `slice`, `substring`, `substr`: 提取子字符串。

### 4. 数组对象（Array）

JavaScript 中的数组对象提供了处理数组的方法，可以动态地增加、删除和修改元素。

**常见方法**：

- `push`, `pop`: 在数组末尾添加或删除元素。
- `shift`, `unshift`: 在数组头部添加或删除元素。
- `concat`: 连接数组。
- `join`: 将数组元素连接成字符串。
- `slice`: 返回数组的一部分。

### 5. 日期对象（Date）

JavaScript 中的日期对象用于处理日期和时间。

**常见方法**：

- `getFullYear`, `getMonth`, `getDate`, `getDay`: 获取年份、月份、日期和星期。
- `getHours`, `getMinutes`, `getSeconds`: 获取小时、分钟和秒数。
- `setFullYear`, `setMonth`, `setDate`, `setHours`: 设置年份、月份、日期和小时。
- `toISOString`: 将日期转换为 ISO 格式的字符串。
- `getTime`: 返回日期的时间戳。

### 6. 数学对象（Math）

JavaScript 中的数学对象提供了数学相关的常量和方法。

**常见方法**：

- `Math.abs`, `Math.round`, `Math.ceil`, `Math.floor`: 数值运算和取整。
- `Math.max`, `Math.min`: 返回一组数中的最大值和最小值。
- `Math.random`: 返回一个介于 0（包括）与 1（不包括）之间的随机数。
- `Math.sqrt`, `Math.pow`: 计算平方根和指数运算。
- `Math.sin`, `Math.cos`, `Math.tan`: 计算三角函数。

### 其他常见内置对象

除了上述几种常见的内置对象外，JavaScript 还有其他一些内置对象，如正则表达式对象（RegExp）、错误对象（Error）、Promise 对象等，它们分别提供了处理正则表达式、错误处理和异步编程的方法和功能。

## 请简要描述一下什么是事件冒泡，它是如何执行的，如何利用 JS 取消事件冒泡机制。

事件冒泡是指在 DOM 中，当一个事件发生时，它会从最具体的元素（事件目标）开始，然后逐级向上冒泡到较不具体的元素，直到根元素（通常是 `document` 对象）。这种机制允许开发者在较高层次的元素上监听事件，而无需在每个具体元素上单独监听。

### 如何执行事件冒泡

1. **事件触发**: 事件从事件目标（最具体的元素）开始触发。
2. **事件捕获**: 事件向上冒泡，逐级传递到其父元素、祖先元素，直到 `document` 对象。
3. **事件处理**: 事件在每一级元素上触发相关的事件处理程序（event handlers）。

### 示例

假设你有以下 HTML 结构：

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>
```

如果你为 `parent` 和 `child` 元素都设置了点击事件处理程序，点击 `button` 时，事件会先在 `button` 上触发，然后冒泡到 `div`，最后到达 `document`。

### 取消事件冒泡

在 JavaScript 中，可以使用 `event.stopPropagation()` 方法来取消事件的冒泡行为。这会阻止事件继续向上冒泡到父元素或 `document` 对象。

### 示例代码

```javascript
document.getElementById('parent').addEventListener('click', function() {
  console.log('Parent clicked');
});

document.getElementById('child').addEventListener('click', function(event) {
  console.log('Child clicked');
  event.stopPropagation(); // 阻止事件冒泡
});
```

在上面的代码中，点击 `button` 时，控制台将只输出 `'Child clicked'`，因为 `event.stopPropagation()` 阻止了事件冒泡到 `div` 上。

通过这种方式，开发者可以控制事件的传播行为，确保事件处理只在所需的层级上进行。

## 结果

```
console.log('1')
var timer = setTimeout(function(){
    console.log(num);
    console.log('2');
    var num=0;
    console.log(num);
},0);
console.log('3');

1 3 undefined 2 0
```

## 请阐述 DOM 和 BOM 的区别?

### 区别总结

- **DOM** 是用于表示和操作文档结构的接口，将文档视为节点树，允许修改内容、结构和样式。
- **BOM** 提供了与浏览器窗口交互的接口，包括控制窗口大小、位置、导航历史和弹出对话框等功能。
- **DOM** 是 W3C 标准的一部分，跨浏览器兼容性良好；**BOM** 则由浏览器厂商定义和实现，不同浏览器可能会有差异。
- **DOM** 是操作网页内容和结构的核心，而 **BOM** 则提供了浏览器窗口级别的控制和操作能力。

## 什么是事件委托，事件委托原理是什么?

一直 用于处理事件监听和处理的（js）编程模式。

它利用事件冒泡的特性，将事件监听器绑定在父元素上，而不是直接绑定在子元素上。

通过检查事件的目标（target），可以确定实际触发事件的子元素，从而执行相应的处理逻辑。

### 原理

事件委托的原理可以简述为以下几步：

1. **事件冒泡**：当子元素上的事件（比如点击事件）被触发时，这个事件会像水泡一样冒泡到父元素、祖父元素，直至文档根节点。

2. **事件目标**：在事件冒泡过程中，可以通过事件对象的 `event.target` 属性获取实际触发事件的元素。

3. **事件处理**：通过在父元素上绑定一个事件监听器，当事件冒泡到父元素时，可以根据 `event.target` 判断事件的实际触发元素，从而执行相应的处理逻辑。

### 优势

使用事件委托的主要优势包括：

- **减少内存消耗**：不需要为大量子元素分别添加事件监听器，而是通过一个监听器管理整个父元素下的事件，节省内存和提升性能。
- **动态元素处理**：对于动态生成的元素（比如通过 AJAX 加载的内容），事件委托可以自动处理这些新添加的元素，无需重新绑定事件。

- **简化代码**：减少了重复的事件绑定代码，使代码更加简洁和易于维护。

### 示例

考虑一个列表项（`<ul>` 中的 `<li>` 元素），需要为每个列表项添加点击事件处理。使用事件委托的方法如下：

```html
<ul id="myList">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
</ul>

<script>
  // 获取父元素
  const list = document.getElementById("myList");

  // 添加事件监听器到父元素
  list.addEventListener("click", function (event) {
    // 检查点击的是否是列表项
    if (event.target.tagName === "LI") {
      // 执行点击列表项的处理逻辑
      console.log("Clicked on:", event.target.textContent);
    }
  });
</script>
```

在上述示例中，事件监听器被绑定在父元素 `<ul>` 上。当用户点击任何一个 `<li>` 元素时，事件会冒泡到 `<ul>` 元素，并且通过检查 `event.target.tagName` 来确定是否点击了 `<li>` 元素。这样做不仅简化了事件管理，还确保了动态添加的列表项也能被正确处理。

总之，事件委托通过利用事件冒泡机制，将事件处理逻辑集中管理在父元素上，是一种优雅和高效的事件处理方式，特别适用于动态页面和大量相似元素的场景。

## 什么是同步和异步，异步事件

在 JavaScript 中，常见的异步事件包括：

- **定时器（setTimeout, setInterval）**：延迟一定时间后执行代码。
- **AJAX 请求**：发送网络请求并等待响应。
- **事件监听器**：监听用户的交互事件（如点击、滚动等）。
- **Promise 对象**：处理异步操作的状态和结果。
- **回调函数**：作为异步操作完成后执行的函数。

## 事件对象有哪些?以及阐述 this 和 e.target 区别?

在 JavaScript 中，事件对象（Event Object）是在事件被触发时自动生成的对象，它包含了与事件相关的信息和方法。常见的事件对象包括以下属性：

### 常见的事件对象属性：

1. **`type`**：事件的类型（如 `click`、`mouseover` 等）。
2. **`target`**：触发事件的目标元素。
3. **`currentTarget`**：当前绑定事件处理函数的元素（事件处理函数所在的元素）。
4. **`bubbles`**：布尔值，表示事件是否冒泡。
5. **`cancelable`**：布尔值，表示事件是否可以被取消。
6. **`eventPhase`**：表示事件流的当前阶段（捕获阶段、目标阶段或冒泡阶段）。
7. **`stopPropagation()`**：阻止事件在 DOM 层次中的传播。
8. **`preventDefault()`**：取消事件的默认行为。
9. **`stopImmediatePropagation()`**：阻止事件的传播，并阻止后续事件处理函数执行。
10. **`isTrusted`**：布尔值，表示事件是由用户操作触发（true），还是由脚本触发（false）。

### `this` 和 `e.target` 的区别：

1. **`this`**：在事件处理函数中，`this` 指向绑定事件处理函数的当前元素（即事件处理函数所在的元素）。

   ```javascript
   document.getElementById("myButton").addEventListener("click", function () {
     console.log(this); // 输出绑定事件处理函数的元素
   });
   ```

   在上述示例中，`this` 指向了 id 为 `myButton` 的元素，即事件绑定的目标元素。

2. **`e.target`**：表示触发事件的实际目标元素。它指向了事件最初触发的元素，即使事件在冒泡过程中被捕获或传播到其他元素，`e.target` 仍然保持指向最初的目标元素。

   ```javascript
   document
     .getElementById("parentElement")
     .addEventListener("click", function (e) {
       console.log(e.target); // 输出触发事件的实际目标元素
     });
   ```

   在上述示例中，无论点击了父元素还是其子元素，`e.target` 总是指向实际点击的元素。

### 区别总结：

- **`this`**：指向绑定事件处理函数的当前元素，由事件处理函数所在的上下文决定。
- **`e.target`**：指向触发事件的实际目标元素，始终保持指向最初触发事件的元素，不受事件冒泡影响。

理解 `this` 和 `e.target` 的区别可以帮助开发者在事件处理函数中准确地操作和处理事件的来源和目标。
