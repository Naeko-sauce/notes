# CSS 变量（自定义属性）

[[../README|← 返回CSS指南]]

#CSS #变量 #自定义属性 #前端开发

## 什么是CSS变量？
CSS变量（也称为自定义属性）允许开发者定义可重用的值，这些值可以在整个样式表中多次使用。通过使用变量，可以更容易地维护和更新样式，特别是在处理主题和响应式设计时。

## 基本语法

### 1. 声明变量
```css
:root {
    --primary-color: #007bff;
    --secondary-color: #6c757d;
    --font-size-base: 16px;
    --spacing-unit: 8px;
    --max-width: 1200px;
}
```

### 2. 使用变量
```css
.button {
    background-color: var(--primary-color);
    padding: var(--spacing-unit) calc(var(--spacing-unit) * 2);
    font-size: var(--font-size-base);
}

.container {
    max-width: var(--max-width);
    margin: 0 auto;
}
```

### 3. 提供默认值
```css
.element {
    /* 如果--text-color未定义，使用#333 */
    color: var(--text-color, #333);
}
```

## 变量作用域

### 1. 全局作用域
```css
:root {
    --global-color: blue;
}

/* 在任何地方都可以使用 */
.element {
    color: var(--global-color);
}
```

### 2. 局部作用域
```css
.card {
    --card-padding: 20px;
    padding: var(--card-padding);
}

.card-header {
    /* 可以访问父元素定义的变量 */
    padding: calc(var(--card-padding) / 2);
}
```

### 3. 媒体查询中的变量
```css
:root {
    --font-size: 16px;
}

@media (min-width: 768px) {
    :root {
        --font-size: 18px;
    }
}
```

## 动态变量使用

### 1. JavaScript操作
```javascript
// 获取变量值
const rootStyles = getComputedStyle(document.documentElement);
const primaryColor = rootStyles.getPropertyValue('--primary-color');

// 设置变量值
document.documentElement.style.setProperty('--primary-color', '#ff0000');
```

### 2. 响应式设计
```css
:root {
    --sidebar-width: 200px;
    --content-padding: 20px;
}

@media (max-width: 768px) {
    :root {
        --sidebar-width: 100%;
        --content-padding: 10px;
    }
}

.sidebar {
    width: var(--sidebar-width);
}

.content {
    padding: var(--content-padding);
}
```

### 3. 主题切换
```css
/* 亮色主题 */
:root {
    --bg-color: #ffffff;
    --text-color: #333333;
    --border-color: #dddddd;
}

/* 暗色主题 */
[data-theme="dark"] {
    --bg-color: #333333;
    --text-color: #ffffff;
    --border-color: #666666;
}

/* 使用变量 */
body {
    background-color: var(--bg-color);
    color: var(--text-color);
}
```

## 计算与函数

### 1. calc()函数
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

### 2. 嵌套计算
```css
:root {
    --base-size: 16px;
    --scale-factor: 1.2;
}

h1 { font-size: calc(var(--base-size) * var(--scale-factor) * 2); }
h2 { font-size: calc(var(--base-size) * var(--scale-factor) * 1.5); }
h3 { font-size: calc(var(--base-size) * var(--scale-factor)); }
```

## 最佳实践

### 1. 命名约定
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

### 2. 组织变量
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

### 3. 组件变量
```css
.button {
    /* 组件特定变量 */
    --button-bg: var(--color-primary);
    --button-color: white;
    --button-padding: var(--spacing-small) var(--spacing-medium);
    
    /* 使用组件变量 */
    background-color: var(--button-bg);
    color: var(--button-color);
    padding: var(--button-padding);
}

.button:hover {
    --button-bg: var(--color-primary-dark);
}
```

## 常见用例

### 1. 响应式布局
```css
:root {
    --container-padding: 15px;
    --grid-columns: 12;
    --grid-gap: 30px;
}

@media (max-width: 768px) {
    :root {
        --container-padding: 10px;
        --grid-gap: 15px;
    }
}

.container {
    padding: var(--container-padding);
}

.grid {
    display: grid;
    grid-template-columns: repeat(var(--grid-columns), 1fr);
    gap: var(--grid-gap);
}
```

### 2. 主题系统
```css
/* 定义主题变量 */
.theme-light {
    --color-bg: #ffffff;
    --color-text: #333333;
    --color-primary: #007bff;
    --color-secondary: #6c757d;
}

.theme-dark {
    --color-bg: #333333;
    --color-text: #ffffff;
    --color-primary: #4da3ff;
    --color-secondary: #a1a8ae;
}

/* 使用主题变量 */
body {
    background-color: var(--color-bg);
    color: var(--color-text);
}
```

## 浏览器兼容性
- 现代浏览器都支持CSS变量
- IE11不支持
- 可以使用CSS预处理器或后处理器提供回退方案

## 调试技巧
1. 使用浏览器开发者工具查看变量
2. 在控制台中修改变量值进行测试
3. 使用CSS.registerProperty()注册变量属性

## 相关资源
- [MDN CSS自定义属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Using_CSS_custom_properties)
- [CSS变量指南](https://css-tricks.com/a-complete-guide-to-custom-properties/)
- [CSS变量浏览器支持](https://caniuse.com/css-variables)

#更新日期_2024_03_18 