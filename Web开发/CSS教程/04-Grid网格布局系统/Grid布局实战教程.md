# CSS Grid布局详解

Grid（网格）布局是CSS中最强大的布局系统，它可以轻松创建二维布局。本章将详细介绍Grid布局的使用方法和最佳实践。

## 1. Grid基础概念

### 1.1 容器和项目
Grid布局由两个主要部分组成：
- Grid容器（父元素）
- Grid项目（子元素）

```css
/* 创建Grid容器 */
.container {
  display: grid; /* 或 display: inline-grid */
}
```

### 1.2 网格线和网格单元
- 网格线：构成网格的水平和垂直分隔线
- 网格单元：网格线之间的空间
- 网格轨道：两条相邻网格线之间的空间（行或列）
- 网格区域：由四条网格线包围的空间

## 2. Grid容器属性

### 2.1 grid-template-columns/rows
定义列和行的大小。

```css
.container {
  /* 固定宽度 */
  grid-template-columns: 100px 200px 100px;
  
  /* 百分比 */
  grid-template-columns: 25% 50% 25%;
  
  /* fr单位 */
  grid-template-columns: 1fr 2fr 1fr;
  
  /* 混合单位 */
  grid-template-columns: 100px 1fr 2fr;
  
  /* repeat函数 */
  grid-template-columns: repeat(3, 1fr);
  
  /* 自动填充 */
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}
```

### 2.2 grid-gap
定义网格间距。

```css
.container {
  gap: 20px;                    /* 行列间距相同 */
  gap: 20px 10px;              /* 行间距 列间距 */
  row-gap: 20px;               /* 行间距 */
  column-gap: 10px;            /* 列间距 */
}
```

### 2.3 grid-template-areas
通过命名定义网格区域。

```css
.container {
  grid-template-areas: 
    "header header header"
    "sidebar main main"
    "footer footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

### 2.4 justify-items/align-items
定义项目在单元格内的对齐方式。

```css
.container {
  justify-items: start | end | center | stretch;
  align-items: start | end | center | stretch;
}
```

### 2.5 justify-content/align-content
定义整个网格在容器内的对齐方式。

```css
.container {
  justify-content: start | end | center | space-between | space-around;
  align-content: start | end | center | space-between | space-around;
}
```

## 3. Grid项目属性

### 3.1 grid-column/row
定义项目的位置和跨度。

```css
.item {
  /* 起始位置/结束位置 */
  grid-column: 1 / 3;
  grid-row: 2 / 4;
  
  /* 跨度 */
  grid-column: span 2;
  grid-row: span 2;
  
  /* 简写 */
  grid-area: 2 / 1 / 4 / 3;
}
```

### 3.2 justify-self/align-self
定义单个项目的对齐方式。

```css
.item {
  justify-self: start | end | center | stretch;
  align-self: start | end | center | stretch;
}
```

## 4. 高级特性

### 4.1 minmax()函数
定义大小范围。

```css
.container {
  grid-template-columns: minmax(100px, 1fr) 2fr 1fr;
}
```

### 4.2 auto-fit和auto-fill
自动调整列数。

```css
.container {
  /* 自动填充 */
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  
  /* 自动适应 */
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```

### 4.3 网格线命名
```css
.container {
  grid-template-columns: [start] 1fr [middle] 2fr [end];
  grid-template-rows: [top] auto [bottom];
}

.item {
  grid-column: start / end;
  grid-row: top / bottom;
}
```

## 5. 常见布局实例

### 5.1 响应式网格布局
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

### 5.2 杂志布局
```css
.magazine {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(100px, auto);
  gap: 20px;
}

.feature {
  grid-column: span 2;
  grid-row: span 2;
}
```

### 5.3 仪表板布局
```css
.dashboard {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: auto;
  gap: 15px;
}

.widget-large {
  grid-column: span 8;
}

.widget-small {
  grid-column: span 4;
}
```

## 6. 响应式设计

### 6.1 使用媒体查询
```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

@media (max-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .grid {
    grid-template-columns: 1fr;
  }
}
```

### 6.2 自适应布局
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(
    clamp(200px, 25vw, 300px),
    1fr
  ));
  gap: 1rem;
}
```

## 7. 最佳实践

1. 使用命名网格区域提高可读性
2. 合理使用fr单位和minmax()
3. 优先使用grid-template-areas进行布局
4. 使用auto-fit/auto-fill实现响应式
5. 避免过度复杂的网格结构

## 练习题

1. 创建一个响应式图片画廊
2. 实现一个复杂的仪表板布局
3. 构建一个类似Pinterest的瀑布流布局
4. 实现一个自适应的博客布局

## 扩展阅读

- [MDN Grid布局指南](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Grid_Layout)
- [Grid Garden](https://cssgridgarden.com/) - 交互式学习游戏
- [CSS-Tricks Grid完整指南](https://css-tricks.com/snippets/css/complete-guide-grid/) 