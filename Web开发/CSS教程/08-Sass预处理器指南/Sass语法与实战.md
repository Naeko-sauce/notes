# Sass预处理器详解

Sass（Syntactically Awesome Style Sheets）是一个强大的CSS预处理器，它扩展了CSS的功能，添加了变量、嵌套、混合、函数等特性。本章将详细介绍Sass的使用方法和最佳实践。

## 1. Sass基础

### 1.1 安装和使用
```bash
# 使用npm安装
npm install -g sass

# 使用yarn安装
yarn global add sass

# 编译Sass文件
sass input.scss output.css

# 监听文件变化
sass --watch input.scss:output.css

# 监听整个目录
sass --watch src/scss:dist/css
```

### 1.2 基本语法
```scss
// 变量定义
$primary-color: #007bff;
$font-stack: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto;
$spacing: 20px;

// 使用变量
body {
  font-family: $font-stack;
  color: $primary-color;
  padding: $spacing;
}
```

## 2. 嵌套语法

### 2.1 基本嵌套
```scss
nav {
  background: #333;
  
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  
  li {
    display: inline-block;
    
    a {
      color: white;
      padding: 10px 15px;
      
      &:hover {
        background: #444;
      }
    }
  }
}
```

### 2.2 属性嵌套
```scss
.button {
  font: {
    family: Arial;
    size: 16px;
    weight: bold;
  }
  
  margin: {
    top: 10px;
    bottom: 10px;
  }
}
```

## 3. 混合（Mixins）

### 3.1 基础混合
```scss
// 定义混合
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  border-radius: $radius;
}

// 使用混合
.button {
  @include border-radius(5px);
}
```

### 3.2 高级混合
```scss
@mixin button-variant($background, $color: white) {
  background-color: $background;
  color: $color;
  
  &:hover {
    background-color: darken($background, 10%);
  }
  
  &:active {
    background-color: darken($background, 15%);
  }
}

.primary-button {
  @include button-variant($primary-color);
}

.secondary-button {
  @include button-variant($secondary-color, black);
}
```

## 4. 继承和占位符

### 4.1 基本继承
```scss
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}
```

### 4.2 占位符选择器
```scss
%button-base {
  display: inline-block;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  
  &:focus {
    outline: none;
  }
}

.button {
  @extend %button-base;
  background: $primary-color;
}
```

## 5. 函数和运算

### 5.1 内置函数
```scss
// 颜色函数
$base-color: #007bff;

.element {
  background: lighten($base-color, 10%);
  border-color: darken($base-color, 10%);
  color: complement($base-color);
}

// 数学函数
.container {
  width: percentage(0.8);    // 80%
  height: round(3.7px);      // 4px
  margin: ceil(3.2px);       // 4px
  padding: floor(3.8px);     // 3px
}
```

### 5.2 自定义函数
```scss
@function calculate-width($n) {
  @return $n * 100px;
}

.container {
  width: calculate-width(5); // 500px
}
```

## 6. 控制指令

### 6.1 条件语句
```scss
@mixin text-color($light-theme: true) {
  @if $light-theme {
    color: #000;
    background: #fff;
  } @else {
    color: #fff;
    background: #000;
  }
}

.light-theme {
  @include text-color(true);
}
```

### 6.2 循环
```scss
// for循环
@for $i from 1 through 3 {
  .col-#{$i} {
    width: 100% / $i;
  }
}

// each循环
$sizes: (small: 10px, medium: 20px, large: 30px);
@each $name, $size in $sizes {
  .margin-#{$name} {
    margin: $size;
  }
}

// while循环
$i: 1;
@while $i <= 3 {
  .item-#{$i} {
    width: 100px * $i;
  }
  $i: $i + 1;
}
```

## 7. 模块化

### 7.1 文件组织
```scss
// _variables.scss
$primary-color: #007bff;
$secondary-color: #6c757d;

// _mixins.scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

// main.scss
@import 'variables';
@import 'mixins';

.container {
  @include flex-center;
  background: $primary-color;
}
```

### 7.2 推荐的目录结构
```
scss/
|-- abstracts/
|   |-- _variables.scss
|   |-- _functions.scss
|   |-- _mixins.scss
|-- base/
|   |-- _reset.scss
|   |-- _typography.scss
|-- components/
|   |-- _buttons.scss
|   |-- _forms.scss
|-- layout/
|   |-- _header.scss
|   |-- _footer.scss
|-- pages/
|   |-- _home.scss
|   |-- _about.scss
|-- main.scss
```

## 8. 工具集成

### 8.1 与构建工具集成
```javascript
// webpack.config.js
module.exports = {
  module: {
    rules: [{
      test: /\.scss$/,
      use: [
        'style-loader',
        'css-loader',
        'sass-loader'
      ]
    }]
  }
}
```

### 8.2 PostCSS集成
```javascript
// postcss.config.js
module.exports = {
  plugins: [
    require('autoprefixer'),
    require('cssnano')
  ]
}
```

## 9. 最佳实践

1. 使用合适的文件组织结构
2. 避免过度嵌套（最多3层）
3. 合理使用混合和继承
4. 保持变量命名一致性
5. 使用注释说明复杂的逻辑

## 练习题

1. 创建一个完整的按钮组件系统
2. 实现一个响应式栅格系统
3. 设计一个主题切换系统
4. 创建一个表单样式库

## 扩展阅读

- [Sass官方文档](https://sass-lang.com/documentation)
- [Sass指南](https://sass-guidelin.es/)
- [Sass在线编译器](https://www.sassmeister.com/) 