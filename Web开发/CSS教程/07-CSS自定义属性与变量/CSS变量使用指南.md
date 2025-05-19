# CSS变量详解

CSS变量（自定义属性）是一种强大的样式复用机制，它允许我们定义可重用的值，使样式表更易于维护和更新。本章将详细介绍CSS变量的使用方法和最佳实践。

## 1. 变量基础

### 1.1 声明变量
```css
:root {
  /* 颜色变量 */
  --primary-color: #007bff;
  --secondary-color: #6c757d;
  --success-color: #28a745;
  
  /* 尺寸变量 */
  --spacing-unit: 8px;
  --container-width: 1200px;
  
  /* 字体变量 */
  --font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto;
  --font-size-base: 16px;
  --line-height: 1.5;
}
```

### 1.2 使用变量
```css
.button {
  background-color: var(--primary-color);
  padding: var(--spacing-unit) calc(var(--spacing-unit) * 2);
  font-family: var(--font-family);
  font-size: var(--font-size-base);
}

.container {
  max-width: var(--container-width);
  margin: 0 auto;
}
```

### 1.3 提供默认值
```css
.element {
  /* 如果--text-color未定义，使用#333 */
  color: var(--text-color, #333);
  
  /* 嵌套使用 */
  margin: var(--margin, var(--spacing-unit, 20px));
}
```

## 2. 变量作用域

### 2.1 全局作用域
```css
:root {
  --global-color: blue;
  --global-spacing: 20px;
}

/* 在任何地方都可以使用 */
.element {
  color: var(--global-color);
  padding: var(--global-spacing);
}
```

### 2.2 局部作用域
```css
.card {
  --card-padding: 20px;
  --card-border-radius: 8px;
  
  padding: var(--card-padding);
  border-radius: var(--card-border-radius);
}

.card-header {
  /* 可以访问父元素定义的变量 */
  padding: calc(var(--card-padding) / 2);
}
```

## 3. 动态变量

### 3.1 媒体查询中的变量
```css
:root {
  --font-size: 16px;
  --container-padding: 20px;
}

@media (min-width: 768px) {
  :root {
    --font-size: 18px;
    --container-padding: 40px;
  }
}

@media (min-width: 1200px) {
  :root {
    --font-size: 20px;
    --container-padding: 60px;
  }
}
```

### 3.2 JavaScript操作
```javascript
// 获取变量值
const rootStyles = getComputedStyle(document.documentElement);
const primaryColor = rootStyles.getPropertyValue('--primary-color');

// 设置变量值
document.documentElement.style.setProperty('--primary-color', '#ff0000');
```

## 4. 主题切换

### 4.1 亮色主题
```css
:root {
  --bg-color: #ffffff;
  --text-color: #333333;
  --border-color: #dddddd;
  --shadow-color: rgba(0, 0, 0, 0.1);
}
```

### 4.2 暗色主题
```css
[data-theme="dark"] {
  --bg-color: #333333;
  --text-color: #ffffff;
  --border-color: #666666;
  --shadow-color: rgba(255, 255, 255, 0.1);
}

/* 使用主题变量 */
body {
  background-color: var(--bg-color);
  color: var(--text-color);
}

.card {
  border: 1px solid var(--border-color);
  box-shadow: 0 2px 4px var(--shadow-color);
}
```

## 5. 计算与函数

### 5.1 calc()函数
```css
:root {
  --spacing: 8px;
  --columns: 12;
}

.grid {
  width: calc(100% / var(--columns));
  margin: calc(var(--spacing) * 2);
  padding: calc(var(--spacing) / 2);
}
```

### 5.2 嵌套计算
```css
:root {
  --base-size: 16px;
  --scale-factor: 1.2;
  --h1-size: calc(var(--base-size) * var(--scale-factor) * 2);
  --h2-size: calc(var(--base-size) * var(--scale-factor) * 1.5);
  --h3-size: calc(var(--base-size) * var(--scale-factor));
}

h1 { font-size: var(--h1-size); }
h2 { font-size: var(--h2-size); }
h3 { font-size: var(--h3-size); }
```

## 6. 组织变量

### 6.1 命名约定
```css
:root {
  /* 使用描述性名称 */
  --color-primary: #007bff;
  --color-secondary: #6c757d;
  --color-success: #28a745;
  
  /* 使用功能性名称 */
  --text-color-body: #333;
  --text-color-heading: #000;
  --text-color-muted: #666;
  
  /* 使用组件相关名称 */
  --button-padding-x: 1rem;
  --button-padding-y: 0.5rem;
  --card-border-radius: 0.25rem;
}
```

### 6.2 变量系统
```css
:root {
  /* 颜色系统 */
  --color-primary: #007bff;
  --color-primary-light: #4da3ff;
  --color-primary-dark: #0056b3;
  
  /* 排版系统 */
  --font-family-base: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto;
  --font-size-base: 1rem;
  --line-height-base: 1.5;
  
  /* 间距系统 */
  --spacing-unit: 0.25rem;
  --spacing-small: calc(var(--spacing-unit) * 2);
  --spacing-medium: calc(var(--spacing-unit) * 4);
  --spacing-large: calc(var(--spacing-unit) * 8);
  
  /* 断点系统 */
  --breakpoint-sm: 576px;
  --breakpoint-md: 768px;
  --breakpoint-lg: 992px;
  --breakpoint-xl: 1200px;
}
```

## 7. 最佳实践

1. 使用有意义的变量名
2. 在:root中定义全局变量
3. 使用局部变量控制组件样式
4. 提供合理的默认值
5. 保持变量系统的一致性

## 8. 浏览器兼容性

### 8.1 检测支持
```css
@supports (--custom: property) {
  /* 支持CSS变量的样式 */
}

@supports not (--custom: property) {
  /* 不支持CSS变量的回退样式 */
}
```

### 8.2 回退方案
```css
.element {
  color: #007bff; /* 回退值 */
  color: var(--primary-color);
}
```

## 练习题

1. 创建一个完整的主题切换系统
2. 实现一个基于CSS变量的栅格系统
3. 设计一个组件库的变量系统
4. 使用CSS变量创建响应式布局

## 扩展阅读

- [MDN CSS自定义属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Using_CSS_custom_properties)
- [CSS变量指南](https://css-tricks.com/a_complete_guide_to_custom_properties/)
- [CSS变量浏览器支持](https://caniuse.com/css-variables) 