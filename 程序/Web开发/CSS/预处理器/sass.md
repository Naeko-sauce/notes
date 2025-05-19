# Sass 预处理器教程

[[../README|← 返回CSS指南]]

#CSS #Sass #预处理器 #前端开发

## 什么是Sass？
Sass（Syntactically Awesome Style Sheets）是一个CSS预处理器，它扩展了CSS的功能，添加了变量、嵌套、混合、函数等特性，使CSS的编写更加强大和灵活。

## 安装和使用

### 1. 安装Sass
```bash
# 使用npm安装
npm install -g sass

# 使用yarn安装
yarn global add sass
```

### 2. 编译Sass
```bash
# 单文件编译
sass input.scss output.css

# 监听文件变化
sass --watch input.scss output.css

# 监听整个目录
sass --watch src/scss:dist/css
```

## 基础语法

### 1. 变量
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

### 2. 嵌套
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

### 3. 部分文件（Partials）
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

### 4. 混合（Mixins）
```scss
// 基础混合
@mixin border-radius($radius) {
    -webkit-border-radius: $radius;
    -moz-border-radius: $radius;
    border-radius: $radius;
}

// 使用混合
.button {
    @include border-radius(5px);
}

// 复杂混合
@mixin button-variant($background, $color: white) {
    background-color: $background;
    color: $color;
    
    &:hover {
        background-color: darken($background, 10%);
    }
}

.primary-button {
    @include button-variant($primary-color);
}
```

### 5. 扩展/继承
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

## 高级特性

### 1. 函数
```scss
// 颜色函数
$base-color: #007bff;

.element {
    background: lighten($base-color, 10%);
    border-color: darken($base-color, 10%);
    color: complement($base-color);
}

// 自定义函数
@function calculate-width($n) {
    @return $n * 100px;
}

.container {
    width: calculate-width(5); // 返回500px
}
```

### 2. 控制指令
```scss
// if语句
@mixin text-color($light-theme: true) {
    @if $light-theme {
        color: #000;
    } @else {
        color: #fff;
    }
}

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
```

### 3. 列表和映射
```scss
// 列表
$font-sizes: 12px, 14px, 16px, 18px;

@each $size in $font-sizes {
    .font-#{$size} {
        font-size: $size;
    }
}

// 映射
$theme-colors: (
    "primary": #007bff,
    "secondary": #6c757d,
    "success": #28a745
);

@each $name, $color in $theme-colors {
    .text-#{$name} {
        color: $color;
    }
}
```

## 最佳实践

### 1. 文件组织
```scss
// 推荐的目录结构
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

### 2. 命名约定
```scss
// 变量命名
$color-primary: #007bff;
$font-size-base: 16px;
$spacing-unit: 8px;

// 混合命名
@mixin button-base {
    // ...
}

// 函数命名
@function calculate-em($pixels) {
    // ...
}
```

### 3. 性能考虑
```scss
// 避免深层嵌套
.nav {
    &__item {
        // 最多嵌套3层
        &--active {
            // ...
        }
    }
}

// 使用占位符选择器
%button-base {
    // 共享样式
}

.button {
    @extend %button-base;
}
```

## 工具和集成

### 1. 开发工具配置
```json
// package.json
{
    "scripts": {
        "sass": "sass src/scss:dist/css --watch",
        "sass:build": "sass src/scss:dist/css --style compressed"
    }
}
```

### 2. 与PostCSS集成
```js
// postcss.config.js
module.exports = {
    plugins: [
        require('autoprefixer'),
        require('cssnano')
    ]
}
```

### 3. 与Webpack集成
```js
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

## 调试技巧
1. 使用source maps
2. 使用@debug和@warn指令
3. 合理组织模块和依赖

## 相关资源
- [Sass官方文档](https://sass-lang.com/documentation)
- [Sass指南](https://sass-guidelin.es/)
- [Sass在线编译器](https://www.sassmeister.com/)

#更新日期_2024_03_18 