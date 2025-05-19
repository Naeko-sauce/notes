# CSS动画详解

CSS动画允许我们创建从一个样式配置逐渐改变为另一个样式配置的动画效果。本章将详细介绍CSS动画的使用方法和最佳实践。

## 1. 过渡（Transitions）

### 1.1 基本语法
```css
.element {
  /* 单个属性过渡 */
  transition: background-color 0.3s ease;
  
  /* 多个属性过渡 */
  transition: background-color 0.3s ease,
             transform 0.3s ease-in-out;
             
  /* 所有属性过渡 */
  transition: all 0.3s ease;
}
```

### 1.2 过渡属性
```css
.element {
  /* 分开写法 */
  transition-property: transform;      /* 过渡属性 */
  transition-duration: 0.3s;          /* 持续时间 */
  transition-timing-function: ease;    /* 时间函数 */
  transition-delay: 0.1s;             /* 延迟时间 */
}
```

### 1.3 时间函数
```css
.element {
  /* 预定义函数 */
  transition-timing-function: linear;
  transition-timing-function: ease;
  transition-timing-function: ease-in;
  transition-timing-function: ease-out;
  transition-timing-function: ease-in-out;
  
  /* 贝塞尔曲线 */
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  
  /* 阶跃函数 */
  transition-timing-function: steps(4, end);
}
```

## 2. 动画（Animations）

### 2.1 关键帧定义
```css
@keyframes slide-in {
  0% {
    transform: translateX(-100%);
    opacity: 0;
  }
  
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

/* 使用动画 */
.element {
  animation: slide-in 0.5s ease-out;
}
```

### 2.2 动画属性
```css
.element {
  /* 分开写法 */
  animation-name: slide-in;           /* 动画名称 */
  animation-duration: 0.5s;           /* 持续时间 */
  animation-timing-function: ease;    /* 时间函数 */
  animation-delay: 0.1s;             /* 延迟时间 */
  animation-iteration-count: 2;       /* 重复次数 */
  animation-direction: alternate;     /* 方向 */
  animation-fill-mode: forwards;      /* 填充模式 */
  animation-play-state: running;      /* 播放状态 */
  
  /* 简写形式 */
  animation: slide-in 0.5s ease 0.1s 2 alternate forwards;
}
```

### 2.3 多个动画
```css
.element {
  animation: 
    slide-in 0.5s ease,
    fade-in 0.3s ease 0.5s;
}
```

## 3. 变换（Transforms）

### 3.1 2D变换
```css
.element {
  /* 平移 */
  transform: translate(50px, 100px);
  transform: translateX(50px);
  transform: translateY(100px);
  
  /* 缩放 */
  transform: scale(1.5);
  transform: scaleX(2);
  transform: scaleY(0.5);
  
  /* 旋转 */
  transform: rotate(45deg);
  
  /* 倾斜 */
  transform: skew(10deg, 20deg);
  
  /* 组合变换 */
  transform: translate(50px, 100px) rotate(45deg) scale(1.5);
}
```

### 3.2 3D变换
```css
.element {
  /* 3D平移 */
  transform: translate3d(50px, 100px, 200px);
  transform: translateZ(200px);
  
  /* 3D旋转 */
  transform: rotateX(45deg);
  transform: rotateY(45deg);
  transform: rotateZ(45deg);
  transform: rotate3d(1, 1, 1, 45deg);
  
  /* 3D透视 */
  perspective: 1000px;
  transform-style: preserve-3d;
}
```

## 4. 性能优化

### 4.1 硬件加速
```css
.element {
  /* 触发硬件加速 */
  transform: translateZ(0);
  will-change: transform;
}
```

### 4.2 性能提示
```css
/* 优化重排和重绘 */
.element {
  /* 使用transform代替位置改变 */
  transform: translate(100px, 0);  /* 好 */
  left: 100px;                     /* 差 */
  
  /* 使用opacity代替visibility */
  opacity: 0;                      /* 好 */
  visibility: hidden;              /* 差 */
}
```

## 5. 常见动画效果

### 5.1 淡入淡出
```css
@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.fade-in {
  animation: fade-in 0.3s ease-in;
}
```

### 5.2 弹跳效果
```css
@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}

.bounce {
  animation: bounce 0.5s ease infinite;
}
```

### 5.3 脉冲效果
```css
@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(1);
  }
}

.pulse {
  animation: pulse 1s ease infinite;
}
```

### 5.4 摇晃效果
```css
@keyframes shake {
  0%, 100% {
    transform: translateX(0);
  }
  10%, 30%, 50%, 70%, 90% {
    transform: translateX(-5px);
  }
  20%, 40%, 60%, 80% {
    transform: translateX(5px);
  }
}

.shake {
  animation: shake 0.8s ease-in-out;
}
```

## 6. 交互动画

### 6.1 悬停效果
```css
.button {
  background: #007bff;
  transition: all 0.3s ease;
}

.button:hover {
  background: #0056b3;
  transform: translateY(-2px);
  box-shadow: 0 2px 8px rgba(0,0,0,0.2);
}
```

### 6.2 点击效果
```css
.button:active {
  transform: translateY(1px);
  box-shadow: none;
}
```

## 7. 响应式动画

### 7.1 基于媒体查询
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

### 7.2 动画暂停
```css
.animation-paused {
  animation-play-state: paused;
}
```

## 8. 最佳实践

1. 使用合适的动画时长（通常0.2s-0.5s）
2. 选择恰当的缓动函数
3. 避免过度使用动画
4. 注意性能优化
5. 考虑可访问性

## 练习题

1. 创建一个加载动画
2. 实现一个卡片翻转效果
3. 制作一个按钮悬停动画
4. 实现一个页面切换动画

## 扩展阅读

- [MDN CSS动画指南](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Animations)
- [CSS动画性能优化](https://developers.google.com/web/fundamentals/design-and-ux/animations/animations-and-performance)
- [CSS Triggers](https://csstriggers.com/) - 了解CSS属性如何影响性能 