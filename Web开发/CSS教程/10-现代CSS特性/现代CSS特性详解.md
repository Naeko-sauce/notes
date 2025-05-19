# 现代CSS特性详解

本章将介绍现代CSS中的一些重要特性和最佳实践，帮助你掌握最新的CSS技术。

## 1. CSS自定义属性（CSS变量）

### 1.1 基本用法
```css
:root {
  --primary-color: #007bff;
  --secondary-color: #6c757d;
  --font-size-base: 16px;
}

.button {
  background-color: var(--primary-color);
  font-size: var(--font-size-base);
}
```

### 1.2 动态更新
```css
.dark-theme {
  --primary-color: #ffffff;
  --secondary-color: #333333;
}
```

## 2. CSS Grid布局进阶

### 2.1 自动布局
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}
```

### 2.2 命名网格线
```css
.grid {
  display: grid;
  grid-template-columns: [start] 1fr [center] 1fr [end];
  grid-template-rows: [top] auto [middle] auto [bottom];
}
```

## 3. CSS容器查询

### 3.1 基本用法
```css
.card {
  container-type: inline-size;
}

@container (min-width: 400px) {
  .card {
    display: grid;
    grid-template-columns: 1fr 2fr;
  }
}
```

## 4. CSS逻辑属性

### 4.1 方向感知
```css
.element {
  margin-block: 1rem;    /* 上下边距 */
  margin-inline: 2rem;   /* 左右边距 */
  padding-block: 1rem;   /* 上下内边距 */
  padding-inline: 2rem;  /* 左右内边距 */
}
```

## 5. CSS选择器新特性

### 5.1 :is() 和 :where()
```css
/* 使用:is() */
:is(header, main, footer) p {
  color: blue;
}

/* 使用:where() */
:where(header, main, footer) p {
  color: blue;
}
```

### 5.2 :has() 选择器
```css
/* 选择包含图片的卡片 */
.card:has(img) {
  background: #f0f0f0;
}

/* 选择包含特定子元素的元素 */
div:has(> p) {
  border: 1px solid #ccc;
}
```

## 6. CSS滚动捕捉

### 6.1 基本用法
```css
.scroll-container {
  scroll-snap-type: x mandatory;
  overflow-x: scroll;
  display: flex;
}

.scroll-item {
  scroll-snap-align: start;
  flex: 0 0 100%;
}
```

## 7. CSS滤镜和混合模式

### 7.1 滤镜效果
```css
.image {
  filter: blur(5px) brightness(1.2) contrast(1.1);
}

/* 背景模糊 */
.modal-backdrop {
  backdrop-filter: blur(5px);
}
```

### 7.2 混合模式
```css
.overlay {
  background-color: rgba(255, 0, 0, 0.5);
  mix-blend-mode: multiply;
}
```

## 8. CSS性能优化

### 8.1 渲染性能
```css
/* 使用transform代替位置属性 */
.animate {
  transform: translateX(100px);
  will-change: transform;
}

/* 使用contain属性优化渲染 */
.isolated {
  contain: content;
}
```

### 8.2 加载优化
```css
/* 使用content-visibility优化渲染 */
.lazy-section {
  content-visibility: auto;
  contain-intrinsic-size: 0 500px;
}
```

## 9. CSS最佳实践

1. 使用CSS变量实现主题切换
2. 采用移动优先的响应式设计
3. 合理使用CSS Grid和Flexbox
4. 注意选择器性能
5. 使用现代CSS特性提升开发效率

## 练习题

1. 实现一个使用CSS变量的主题切换系统
2. 创建一个响应式图片网格
3. 使用容器查询实现组件级响应式设计
4. 实现一个滚动捕捉的图片轮播

## 扩展阅读

- [MDN Web文档](https://developer.mozilla.org/zh-CN/docs/Web/CSS)
- [CSS技巧](https://css-tricks.com/)
- [现代CSS解决方案](https://moderncss.dev/) 