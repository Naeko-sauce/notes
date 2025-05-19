# CSS工程化实践

CSS工程化是一种系统化、规范化的CSS开发方法论，它包括目录结构组织、命名规范、模块化开发、构建工具等多个方面。本章将详细介绍CSS工程化的最佳实践。

## 1. 目录结构组织

### 1.1 基本目录结构
```
src/
|-- styles/
    |-- base/              # 基础样式
        |-- _reset.css     # 重置样式
        |-- _typography.css # 排版样式
        |-- _variables.css  # 变量定义
    |-- components/        # 组件样式
        |-- _button.css
        |-- _form.css
        |-- _card.css
    |-- layouts/           # 布局样式
        |-- _header.css
        |-- _footer.css
        |-- _sidebar.css
    |-- pages/            # 页面特定样式
        |-- _home.css
        |-- _about.css
    |-- utils/            # 工具类
        |-- _helpers.css
        |-- _mixins.css
    |-- vendors/          # 第三方样式
        |-- _bootstrap.css
        |-- _normalize.css
    |-- main.css          # 主样式文件
```

### 1.2 模块化导入
```css
/* main.css */
@import 'base/_reset.css';
@import 'base/_typography.css';
@import 'base/_variables.css';

@import 'components/_button.css';
@import 'components/_form.css';
@import 'components/_card.css';

@import 'layouts/_header.css';
@import 'layouts/_footer.css';
```

## 2. 命名规范

### 2.1 BEM命名规范
```css
/* Block */
.card { }

/* Element */
.card__title { }
.card__content { }
.card__button { }

/* Modifier */
.card--featured { }
.card--dark { }
.card__button--primary { }
```

### 2.2 命名空间前缀
```css
/* 布局 */
.l-header { }
.l-sidebar { }

/* 组件 */
.c-button { }
.c-card { }

/* 工具类 */
.u-clearfix { }
.u-hidden { }

/* 状态类 */
.is-active { }
.has-error { }

/* JavaScript钩子 */
.js-toggle { }
.js-slider { }
```

## 3. CSS架构方法论

### 3.1 ITCSS（Inverted Triangle CSS）
```css
/* 1. Settings - 变量、配置 */
:root {
  --primary-color: #007bff;
  --spacing-unit: 8px;
}

/* 2. Tools - 函数、混合 */
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 3. Generic - 重置、标准化 */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* 4. Elements - 未加类的HTML元素 */
body {
  font-family: sans-serif;
  line-height: 1.5;
}

/* 5. Objects - 无外观的设计模式 */
.o-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* 6. Components - 具体UI组件 */
.c-button {
  padding: 10px 20px;
  border-radius: 4px;
}

/* 7. Utilities - 工具类 */
.u-text-center {
  text-align: center;
}
```

### 3.2 Atomic CSS
```css
/* 间距 */
.m-0 { margin: 0; }
.p-1 { padding: 0.25rem; }
.mt-2 { margin-top: 0.5rem; }

/* 颜色 */
.text-primary { color: var(--primary-color); }
.bg-white { background-color: white; }

/* 布局 */
.flex { display: flex; }
.grid { display: grid; }
```

## 4. 模块化开发

### 4.1 CSS Modules
```javascript
// webpack.config.js
module.exports = {
  module: {
    rules: [{
      test: /\.css$/,
      use: [
        'style-loader',
        {
          loader: 'css-loader',
          options: {
            modules: true
          }
        }
      ]
    }]
  }
}
```

```css
/* Button.module.css */
.button {
  padding: 10px 20px;
}

.primary {
  background: blue;
  color: white;
}
```

```javascript
// Button.js
import styles from './Button.module.css';

const Button = () => (
  <button className={styles.button}>
    Click me
  </button>
);
```

### 4.2 CSS-in-JS
```javascript
// 使用styled-components
import styled from 'styled-components';

const Button = styled.button`
  padding: 10px 20px;
  background: ${props => props.primary ? 'blue' : 'gray'};
  color: white;
  
  &:hover {
    opacity: 0.8;
  }
`;
```

## 5. 构建工具链

### 5.1 PostCSS配置
```javascript
// postcss.config.js
module.exports = {
  plugins: [
    require('autoprefixer'),
    require('cssnano'),
    require('postcss-preset-env'),
    require('postcss-import'),
    require('tailwindcss'),
  ]
}
```

### 5.2 webpack配置
```javascript
// webpack.config.js
module.exports = {
  module: {
    rules: [{
      test: /\.css$/,
      use: [
        'style-loader',
        {
          loader: 'css-loader',
          options: {
            importLoaders: 1
          }
        },
        'postcss-loader'
      ]
    }]
  }
}
```

## 6. 性能优化

### 6.1 CSS压缩
```javascript
// webpack.config.js生产环境配置
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const CssMinimizerPlugin = require('css-minimizer-webpack-plugin');

module.exports = {
  optimization: {
    minimizer: [
      new CssMinimizerPlugin()
    ]
  },
  plugins: [
    new MiniCssExtractPlugin({
      filename: '[name].[contenthash].css'
    })
  ]
}
```

### 6.2 关键CSS提取
```html
<head>
  <style>
    /* 关键CSS直接内联 */
    .header { /* ... */ }
    .hero { /* ... */ }
  </style>
  
  <link rel="preload" href="main.css" as="style" onload="this.rel='stylesheet'">
</head>
```

### 6.3 代码分割
```javascript
// webpack.config.js
module.exports = {
  optimization: {
    splitChunks: {
      cacheGroups: {
        styles: {
          name: 'styles',
          test: /\.css$/,
          chunks: 'all',
          enforce: true
        }
      }
    }
  }
}
```

## 7. 质量控制

### 7.1 StyleLint配置
```javascript
// .stylelintrc
{
  "extends": "stylelint-config-standard",
  "rules": {
    "indentation": 2,
    "string-quotes": "single",
    "no-duplicate-selectors": true,
    "color-hex-case": "lower",
    "color-hex-length": "short",
    "selector-combinator-space-after": "always",
    "declaration-block-trailing-semicolon": "always",
    "declaration-colon-space-before": "never",
    "declaration-colon-space-after": "always",
    "block-opening-brace-space-before": "always",
    "declaration-block-semicolon-newline-after": "always"
  }
}
```

### 7.2 Git Hooks
```json
// package.json
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.css": ["stylelint --fix", "git add"]
  }
}
```

## 8. 部署策略

### 8.1 缓存策略
```nginx
# Nginx配置
location ~* \.(?:css|js)$ {
    expires 1y;
    add_header Cache-Control "public, no-transform";
}
```

### 8.2 CDN配置
```html
<link 
  rel="stylesheet" 
  href="https://cdn.example.com/styles/main.123456.css"
  crossorigin="anonymous"
>
```

## 9. 最佳实践

1. 采用合适的CSS架构方法论
2. 使用模块化开发方式
3. 实施严格的命名规范
4. 建立完整的构建流程
5. 重视性能优化
6. 实施代码质量控制
7. 制定合理的部署策略

## 练习题

1. 搭建一个完整的CSS工程化开发环境
2. 实现一个基于BEM的组件库
3. 配置完整的构建和部署流程
4. 优化现有项目的CSS架构

## 扩展阅读

- [CSS架构](https://www.smashingmagazine.com/2018/06/css-architecture-for-modern-web-applications/)
- [CSS Modules](https://github.com/css-modules/css-modules)
- [PostCSS](https://postcss.org/)
- [StyleLint](https://stylelint.io/) 