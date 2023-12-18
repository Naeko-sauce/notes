## GSAP 设置 Three. Js 延迟运动

### 1. 引入 GSAP 库

```html
<!-- 使用 CDN 引入 GSAP -->
<script src="https://unpkg.com/gsap@3.9.2/dist/gsap.min.js"></script>
```

### 2. 创建 Three. Js 场景和对象

```javascript
// 创建 Three.js 场景
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// 创建 Three.js 立方体
const cubeGeometry = new THREE.BoxGeometry();
const cubeMaterial = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(cubeGeometry, cubeMaterial);
scene.add(cube);

// 设置相机位置
camera.position.z = 5;
```

### 3. 使用 GSAP 进行延迟运动

```javascript
// 使用 GSAP 进行延迟运动
gsap.to(cube.position, {
  x: 2,
  duration: 2,
  delay: 1, // 设置延迟时间，单位为秒
  onComplete: () => {
    console.log("Animation completed!");
  }
});
```

### 4. 完整示例代码

```javascript
// 完整示例代码
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

const cubeGeometry = new THREE.BoxGeometry();
const cubeMaterial = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(cubeGeometry, cubeMaterial);
scene.add(cube);

camera.position.z = 5;

gsap.to(cube.position, {
  x: 2,
  duration: 2,
  delay: 1,
  onComplete: () => {
    console.log("Animation completed!");
  }
});

const animate = () => {
  requestAnimationFrame(animate);
  renderer.render(scene, camera);
};

animate();
```

### 5. 总结

- 结合 GSAP 和 Three. Js，可以使用 GSAP 的 Tween 功能轻松实现 Three. Js 对象的延迟运动。
- `delay` 属性用于设置延迟时间，单位为秒。
- 完整示例代码包含了创建场景、相机、渲染器以及动画循环。