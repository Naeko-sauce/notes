当在 Three. Js 中使用轨道控制器（`OrbitControls`）时，可以通过以下方式设置和配置它。以下是一些关于轨道控制器的常见用法的笔记：

### 导入 Three. Js 和轨道控制器：

```javascript
import * as THREE from 'three';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';
```

### 创建场景、相机和渲染器：

```javascript
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
```

### 创建轨道控制器：

```javascript
const controls = new OrbitControls(camera, renderer.domElement);
```

### 设置轨道控制器参数：

```javascript
// 使动画循环使用时阻尼或自转，意思是否有惯性
controls.enableDamping = true;

// 阻尼系数（阻止缩放）
controls.dampingFactor = 0.25;

// 是否启用屏幕空间平移
controls.screenSpacePanning = false;

// 限制鼠标拖动的垂直角度
controls.maxPolarAngle = Math.PI / 2;
```

### 动画循环中更新轨道控制器：

```javascript
function animate() {
    requestAnimationFrame(animate);
    controls.update(); // 更新轨道控制器
    renderer.render(scene, camera);
}

animate();
```

### 注意事项：

- **更新频率：** 在动画循环中调用 `controls.update()` 是很重要的，以确保在每帧都更新轨道控制器的内部状态。
  
- **事件监听器：** 轨道控制器可以通过事件监听器响应用户输入，例如 `change` 事件。

- **自定义设置：** 根据项目需求，可以根据文档设置其他参数，如 `maxDistance`、`minPolarAngle`、`enableZoom` 等。

- **依赖项：** 确保正确导入轨道控制器的依赖项（例如鼠标、触摸等事件处理器）。

以上是一个基本的配置示例，可以根据具体需求和项目进行调整。在使用轨道控制器时，务必查阅 Three. Js 文档和轨道控制器的源代码以获取详细信息。