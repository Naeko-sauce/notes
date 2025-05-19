在 Three. Js 中，阻尼通常与控制器（例如 OrbitControls）一起使用，以增加摄像机的惯性和平滑性。以下是一个简单的例子，演示如何在 Three. Js 中设置阻尼：

```javascript
// 导入Three.js库
import * as THREE from 'three';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';

// 创建场景
const scene = new THREE.Scene();

// 创建相机
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
camera.position.set(0, 0, 5);

// 创建渲染器
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// 创建一个立方体
const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

// 添加光源
const light = new THREE.PointLight(0xffffff, 1, 100);
light.position.set(0, 0, 5);
scene.add(light);

// 创建OrbitControls并设置阻尼
const controls = new OrbitControls(camera, renderer.domElement);
controls.enableDamping = true; // 启用阻尼
controls.dampingFactor = 0.25; // 阻尼系数

// 动画循环
function animate() {
  requestAnimationFrame(animate);

  // 更新控制器
  controls.update();

  renderer.render(scene, camera);
}

// 调整窗口大小时更新相机的纵横比
window.addEventListener('resize', () => {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});

// 开始动画循环
animate();
```

在这个例子中，`OrbitControls` 被用来控制相机，`enableDamping` 被设置为 `true` 以启用阻尼，然后通过 `dampingFactor` 控制阻尼的程度。你可以调整 `dampingFactor` 的值来达到你想要的阻尼效果。