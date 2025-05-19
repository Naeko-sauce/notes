### 移动 Three. Js 方块使用 GSAP

#### 步骤概览：

1. **准备 Three. Js 场景：** 创建 Three. Js 场景、相机和方块。

2. **引入 GSAP：** 确保正确引入 GSAP 库。

3. **创建方块对象：** 使用 Three. Js 创建一个方块对象，并添加到场景中。

4. **使用 GSAP 创建动画：** 使用 GSAP 的 Tween 动画来移动方块的位置。

5. **启动动画循环：** 创建一个动画循环函数，以渲染场景。

#### 代码示例：

```javascript
// 引入 Three.js 和 GSAP 库
import * as THREE from 'three';
import gsap from 'gsap';

// 创建 Three.js 场景、相机和渲染器
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// 创建方块对象
const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

// 设置相机位置
camera.position.z = 5;

// 使用 GSAP 移动方块
gsap.to(cube.position, {
  x: 2,         // 目标 x 坐标
  duration: 2,  // 动画持续时间（秒）
  ease: 'power2.inOut', // 缓动函数
  onComplete: () => {
    console.log('Animation complete');
  },
});

// 创建动画循环
function animate() {
  requestAnimationFrame(animate);
  renderer.render(scene, camera);
}

// 启动动画循环
animate();
```

#### 代码解释：

1. **引入库：** 使用 `import` 语句引入 Three. Js 和 GSAP 库。

2. **创建 Three. Js 元素：** 创建场景、相机、渲染器，以及方块对象。

3. **GSAP 移动动画：** 使用 `gsap.to` 方法创建 Tween 动画，将方块的位置逐渐移动到目标位置。

4. **动画循环：** 创建 `animate` 函数，使用 `requestAnimationFrame` 启动动画循环，以渲染场景。

通过这些步骤，你可以轻松使用 GSAP 和 Three. Js 结合创建动画效果。