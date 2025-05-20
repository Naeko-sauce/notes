# CSS实战项目与布局模式

本章将介绍常见的CSS布局模式和实际项目中的应用，帮助你掌握CSS的实战技巧。

## 1. 常见布局模式

### 1.1 圣杯布局
```css
.holy-grail {
  display: grid;
  grid-template: 
    "header header header" auto
    "nav main aside" 1fr
    "footer footer footer" auto
    / auto 1fr auto;
  min-height: 100vh;
}

.header { grid-area: header; }
.nav { grid-area: nav; }
.main { grid-area: main; }
.aside { grid-area: aside; }
.footer { grid-area: footer; }
```

### 1.2 双飞翼布局
```css
.double-wing {
  display: flex;
}

.main {
  flex: 1;
  margin: 0 200px;
}

.left, .right {
  width: 200px;
}

.left {
  margin-left: -100%;
}

.right {
  margin-left: -200px;
}
```

### 1.3 瀑布流布局
```css
.masonry {
  columns: 4 300px;
  gap: 20px;
}

.item {
  break-inside: avoid;
  margin-bottom: 20px;
}
```

## 2. 响应式组件实战

### 2.1 响应式导航栏
```css
.nav {
  display: flex;
  justify-content: space-between;
  padding: 1rem;
}

.nav-links {
  display: flex;
  gap: 1rem;
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
  }
  
  .nav-links.active {
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: white;
    padding: 1rem;
  }
}
```

### 2.2 卡片网格
```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  padding: 2rem;
}

.card {
  display: flex;
  flex-direction: column;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.card-image {
  aspect-ratio: 16/9;
  object-fit: cover;
}

.card-content {
  padding: 1rem;
}
```

## 3. 高级交互效果

### 3.1 悬停动画
```css
.hover-effect {
  position: relative;
  overflow: hidden;
}

.hover-effect::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: currentColor;
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.3s ease;
}

.hover-effect:hover::after {
  transform: scaleX(1);
  transform-origin: left;
}
```

### 3.2 滚动动画
```css
.scroll-reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.6s ease;
}

.scroll-reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* 配合 Intersection Observer API 使用 */
```

## 4. 实用布局技巧

### 4.1 居中对齐
```css
/* Flexbox方式 */
.center-flex {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Grid方式 */
.center-grid {
  display: grid;
  place-items: center;
}

/* 绝对定位方式 */
.center-absolute {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

### 4.2 自适应内容
```css
.auto-fit {
  width: fit-content;
  max-width: 100%;
}

.line-clamp {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```

## 5. 实战项目示例

### 5.1 响应式作品集网站
```css
/* 布局结构 */
.portfolio {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  padding: 2rem;
}

/* 作品卡片 */
.portfolio-item {
  position: relative;
  overflow: hidden;
  border-radius: 8px;
}

/* 悬停效果 */
.portfolio-overlay {
  position: absolute;
  inset: 0;
  background: rgba(0,0,0,0.8);
  display: grid;
  place-items: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.portfolio-item:hover .portfolio-overlay {
  opacity: 1;
}
```

## 6. 性能优化技巧

### 6.1 减少重排重绘
```css
/* 使用transform代替位置属性 */
.optimize {
  transform: translateX(100px);
  will-change: transform;
}

/* 使用opacity代替visibility */
.fade {
  opacity: 0;
  transition: opacity 0.3s;
}
```

### 6.2 优化动画性能
```css
/* 使用CSS硬件加速 */
.hardware-accelerated {
  transform: translateZ(0);
  backface-visibility: hidden;
}
```

## 练习项目

1. 创建一个响应式作品集网站
2. 实现一个带动画的导航菜单
3. 设计一个瀑布流图片展示
4. 开发一个响应式仪表板界面

## 扩展阅读

- [CSS布局模式详解](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Layout_mode)
- [CSS Grid完全指南](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [现代CSS布局解决方案](https://1linelayouts.glitch.me/) 