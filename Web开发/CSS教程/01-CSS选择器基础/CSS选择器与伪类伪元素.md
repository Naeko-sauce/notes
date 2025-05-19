# CSS选择器详解

CSS选择器是CSS规则的核心，它们使我们能够精确地选择和样式化HTML元素。本章将详细介绍各种选择器的使用方法和最佳实践。

## 1. 基本选择器

### 1.1 通用选择器 (*)
```css
/* 选择所有元素 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

### 1.2 元素选择器
```css
/* 选择所有段落元素 */
p {
  font-size: 16px;
  line-height: 1.5;
}

/* 选择所有标题元素 */
h1 {
  font-size: 2em;
  margin-bottom: 20px;
}
```

### 1.3 类选择器 (.)
```css
/* 选择具有特定类的元素 */
.highlight {
  background-color: yellow;
}

/* 多个类选择器组合 */
.btn.primary {
  background-color: blue;
  color: white;
}
```

### 1.4 ID选择器 (#)
```css
/* 选择特定ID的元素 */
#header {
  position: fixed;
  top: 0;
  width: 100%;
}
```

## 2. 组合选择器

### 2.1 后代选择器（空格）
```css
/* 选择article内的所有p元素 */
article p {
  text-indent: 2em;
}
```

### 2.2 子选择器（>）
```css
/* 只选择直接子元素 */
nav > ul {
  display: flex;
}
```

### 2.3 相邻兄弟选择器（+）
```css
/* 选择紧跟在h1后面的p元素 */
h1 + p {
  font-weight: bold;
}
```

### 2.4 通用兄弟选择器（~）
```css
/* 选择同级的所有p元素 */
h1 ~ p {
  color: gray;
}
```

## 3. 属性选择器

### 3.1 基本属性选择器
```css
/* 具有某个属性的元素 */
[title] {
  cursor: help;
}

/* 具有特定属性值的元素 */
[type="text"] {
  border: 1px solid #ccc;
}
```

### 3.2 部分匹配选择器
```css
/* 以特定值开头 */
[class^="btn-"] {
  padding: 5px 10px;
}

/* 以特定值结尾 */
[href$=".pdf"] {
  background: url(pdf-icon.png) no-repeat;
}

/* 包含特定值 */
[class*="container"] {
  width: 100%;
}
```

## 4. 伪类选择器

### 4.1 状态伪类
```css
/* 鼠标悬停 */
button:hover {
  background-color: #eee;
}

/* 激活状态 */
button:active {
  transform: translateY(1px);
}

/* 访问过的链接 */
a:visited {
  color: purple;
}
```

### 4.2 结构伪类
```css
/* 第一个子元素 */
li:first-child {
  font-weight: bold;
}

/* 最后一个子元素 */
li:last-child {
  border-bottom: none;
}

/* 奇数项 */
tr:nth-child(odd) {
  background-color: #f9f9f9;
}
```

## 5. 伪元素选择器

```css
/* 首字母 */
p::first-letter {
  font-size: 2em;
  font-weight: bold;
}

/* 首行 */
p::first-line {
  color: #666;
}

/* 在元素前后添加内容 */
.quote::before {
  content: """;
}
.quote::after {
  content: """;
}
```

## 6. 选择器优先级

优先级从高到低：
1. !important
2. 内联样式
3. ID选择器
4. 类选择器、属性选择器、伪类
5. 元素选择器、伪元素
6. 通用选择器

```css
/* 优先级示例 */
#header {
  color: black;          /* 优先级高 */
}
.header {
  color: blue;          /* 优先级中等 */
}
header {
  color: red;           /* 优先级低 */
}
```

## 练习题

1. 创建一个导航栏，使用不同的选择器来样式化其中的元素
2. 实现一个表格的斑马纹样式
3. 使用属性选择器来样式化不同类型的输入框
4. 创建一个带有伪元素装饰的引用块

## 最佳实践

1. 避免过度使用ID选择器
2. 保持选择器简短，避免过度嵌套
3. 使用类选择器来提高可重用性
4. 避免使用!important
5. 按照特定的命名规范组织类名（如BEM方法论）

## 扩展阅读

- [MDN CSS选择器参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Selectors)
- [CSS选择器优先级计算器](https://specificity.keegan.st/)
- [CSS选择器游戏](https://flukeout.github.io/) 