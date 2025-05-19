Three. Js 中的坐标辅助器（CoordinateHelper）用于可视化显示场景中的坐标轴，以帮助调试和定位物体。以下是在 Three. Js 中使用坐标辅助器的步骤：

1. **引入 Three. Js 库：**
   在 HTML 文件中引入 Three. Js 库，你可以从 [Three.js 官方网站](https://threejs.org/) 下载，或者使用 CDN：

   ```html
   <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
   ```

2. **创建场景、相机和渲染器：**
   ```javascript
   // 创建场景
   const scene = new THREE.Scene();

   // 创建相机
   const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
   camera.position.z = 5;

   // 创建渲染器
   const renderer = new THREE.WebGLRenderer();
   renderer.setSize(window.innerWidth, window.innerHeight);
   document.body.appendChild(renderer.domElement);
   ```

3. **创建坐标辅助器：**
   ```javascript
   const axesHelper = new THREE.AxesHelper(2); // 传递坐标轴长度作为参数
   scene.add(axesHelper);
   ```

   在这里，`THREE.AxesHelper` 用于创建坐标辅助器，你可以通过传递长度参数来设置坐标轴的长度。

4. **创建一个物体（可选）：**
   在场景中添加其他物体，以便观察坐标辅助器的作用：
   ```javascript
   const geometry = new THREE.BoxGeometry();
   const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
   const cube = new THREE.Mesh(geometry, material);
   scene.add(cube);
   ```

5. **渲染场景：**
   ```javascript
   function animate() {
       requestAnimationFrame(animate);

       // 在此处可以添加动画或其他更新逻辑

       renderer.render(scene, camera);
   }

   animate();
   ```

   在 `animate` 函数中，你可以添加动画或其他场景更新逻辑。

6. **查看结果：**
   打开你的浏览器，你应该能够看到一个包含坐标轴的 Three. Js 场景。

完整的代码示例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Three.js Coordinate Helper</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
</head>
<body>
    <script>
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        camera.position.z = 5;

        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        const axesHelper = new THREE.AxesHelper(2);
        scene.add(axesHelper);

        const geometry = new THREE.BoxGeometry();
        const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
        const cube = new THREE.Mesh(geometry, material);
        scene.add(cube);

        function animate() {
            requestAnimationFrame(animate);

            // 在此处可以添加动画或其他更新逻辑

            renderer.render(scene, camera);
        }

        animate();
    </script>
</body>
</html>
```

这将在浏览器中显示一个带有坐标轴和一个绿色立方体的场景。****