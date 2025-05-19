# CSS Flexbox布局详解

Flexbox（弹性盒子）是一种现代的CSS布局方式，它可以帮助我们更简单、更灵活地进行页面布局。本章将详细介绍Flexbox的使用方法和最佳实践。

## 1. Flexbox基础概念

### 1.1 容器和项目
Flexbox布局由两个主要部分组成：
- Flex容器（父元素）
- Flex项目（子元素）

```css
/* 创建Flex容器 */
.container {
  display: flex; /* 或 display: inline-flex */
}
```

### 1.2 主轴和交叉轴
- 主轴（Main Axis）：由flex-direction定义的方向
- 交叉轴（Cross Axis）：垂直于主轴的方向

## 2. Flex容器属性

### 2.1 flex-direction
定义主轴的方向。

```css
.container {
  flex-direction: row;            /* 默认值：从左到右 */
  flex-direction: row-reverse;    /* 从右到左 */
  flex-direction: column;         /* 从上到下 */
  flex-direction: column-reverse; /* 从下到上 */
}
```

### 2.2 flex-wrap
定义是否换行。

```css
.container {
  flex-wrap: nowrap;       /* 默认值：不换行 */
  flex-wrap: wrap;         /* 换行 */
  flex-wrap: wrap-reverse; /* 反向换行 */
}
```

### 2.3 justify-content
定义项目在主轴上的对齐方式。

```css
.container {
  justify-content: flex-start;    /* 默认值：左对齐 */
  justify-content: flex-end;      /* 右对齐 */
  justify-content: center;        /* 居中对齐 */
  justify-content: space-between; /* 两端对齐 */
  justify-content: space-around;  /* 项目两侧间隔相等 */
  justify-content: space-evenly;  /* 项目间隔完全相等 */
}
```

### 2.4 align-items
定义项目在交叉轴上的对齐方式。

```css
.container {
  align-items: stretch;     /* 默认值：拉伸填充 */
  align-items: flex-start; /* 顶部对齐 */
  align-items: flex-end;   /* 底部对齐 */
  align-items: center;     /* 居中对齐 */
  align-items: baseline;   /* 基线对齐 */
}
```

### 2.5 align-content
定义多行项目在交叉轴上的对齐方式。

```css
.container {
  align-content: flex-start;    /* 顶部堆叠 */
  align-content: flex-end;      /* 底部堆叠 */
  align-content: center;        /* 居中堆叠 */
  align-content: space-between; /* 两端堆叠 */
  align-content: space-around;  /* 均匀堆叠 */
  align-content: stretch;       /* 默认值：拉伸填充 */
}
```

## 3. Flex项目属性

### 3.1 flex-grow
定义项目的放大比例。

```css
.item {
  flex-grow: 0; /* 默认值：不放大 */
  flex-grow: 1; /* 平均分配剩余空间 */
  flex-grow: 2; /* 分配剩余空间的2倍 */
}
```

### 3.2 flex-shrink
定义项目的缩小比例。

```css
.item {
  flex-shrink: 1; /* 默认值：等比缩小 */
  flex-shrink: 0; /* 不缩小 */
  flex-shrink: 2; /* 以2倍比例缩小 */
}
```

### 3.3 flex-basis
定义项目在主轴上的初始大小。

```css
.item {
  flex-basis: auto;   /* 默认值：项目本身大小 */
  flex-basis: 0;      /* 完全依赖flex-grow分配 */
  flex-basis: 200px;  /* 指定具体大小 */
}
```

### 3.4 flex简写
flex属性是flex-grow、flex-shrink和flex-basis的简写。

```css
.item {
  flex: 0 1 auto;   /* 默认值 */
  flex: 1;          /* 等价于 flex: 1 1 0% */
  flex: auto;       /* 等价于 flex: 1 1 auto */
  flex: none;       /* 等价于 flex: 0 0 auto */
}
```

### 3.5 align-self
允许单个项目有不同于其他项目的对齐方式。

```css
.item {
  align-self: auto;       /* 默认值：继承align-items */
  align-self: flex-start; /* 顶部对齐 */
  align-self: flex-end;   /* 底部对齐 */
  align-self: center;     /* 居中对齐 */
  align-self: baseline;   /* 基线对齐 */
  align-self: stretch;    /* 拉伸填充 */
}
```

## 4. 常见布局实例

### 4.1 居中布局
```css
/* 水平垂直居中 */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

### 4.2 导航栏布局
```css
/* 响应式导航栏 */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
}

.nav-links {
  display: flex;
  gap: 1rem;
}
```

### 4.3 卡片网格布局
```css
/* 自适应卡片网格 */
.card-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.card {
  flex: 1 1 300px;
  /* 最小宽度300px，可以增长和收缩 */
}
```

### 4.4 圣杯布局
```css
/* 经典的圣杯布局 */
.holy-grail {
  display: flex;
  min-height: 100vh;
}

.sidebar {
  flex: 0 0 200px;
}

.main-content {
  flex: 1;
}
```

## 5. 响应式设计

### 5.1 基于Flex的响应式布局
```css
/* 响应式容器 */
.container {
  display: flex;
  flex-wrap: wrap;
}

/* 响应式列 */
.column {
  flex: 1 1 300px;
}

@media (max-width: 768px) {
  .column {
    flex: 1 1 100%;
  }
}
```

## 6. 最佳实践

1. 使用flex简写属性
2. 合理使用gap属性代替margin
3. 注意flex-basis和width的区别
4. 使用flex-wrap实现响应式布局
5. 避免过度嵌套flex容器

## 练习题

1. 创建一个响应式导航栏
2. 实现一个卡片网格布局
3. 构建一个居中的模态框
4. 实现一个自适应的页脚布局

## 扩展阅读

- [MDN Flexbox指南](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout)
- [Flexbox Froggy](https://flexboxfroggy.com/) - 交互式学习游戏
- [CSS-Tricks完整指南](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) 