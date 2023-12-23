当你编写 Three. Js 应用时，确保在窗口大小变化时适应新的视口尺寸是很重要的。以下是这段代码的详细解释，以笔记的方式：

```javascript
// 监听窗口大小变化事件
window.addEventListener('resize', () => {
    // 更新相机的纵横比（aspect ratio）
    camera.aspect = window.innerWidth / window.innerHeight;

    // 更新相机的投影矩阵
    camera.updateProjectionMatrix();

    // 更新渲染器的大小
    renderer.setSize(window.innerWidth, window.innerHeight);

    // 设置渲染器的像素比，通常用于支持高DPI（Retina）屏幕
    renderer.setPixelRatio(window.devicePixelRatio);
});
```

#### 1. 更新相机的纵横比

```javascript
// 更新相机的纵横比
camera.aspect = window.innerWidth / window.innerHeight;
```

- **用途：** 窗口大小变化时，更新相机的纵横比，确保渲染的内容不会变形。
- **解释：** 纵横比是窗口宽度除以窗口高度。通过更新相机的纵横比，我们确保视景体（视锥体）的形状适应新的窗口大小。

#### 2. 更新相机的投影矩阵

```javascript
// 更新相机的投影矩阵
camera.updateProjectionMatrix();
```

- **用途：** 当相机的参数（如纵横比）发生变化时，需要调用此方法更新相机的投影矩阵。
- **解释：** 投影矩阵负责将 3 D 场景映射到 2 D 屏幕上。通过调用 `updateProjectionMatrix()`，我们告诉 Three. Js 相机需要根据新的参数重新计算投影矩阵。

#### 3. 更新渲染器的大小

```javascript
// 更新渲染器的大小
renderer.setSize(window.innerWidth, window.innerHeight);
```

- **用途：** 确保渲染器的画布大小与新的窗口大小一致。
- **解释：** 如果不更新渲染器的大小，可能会导致画布尺寸不正确，产生白边或变形。

#### 4. 设置渲染器的像素比

```javascript
// 设置渲染器的像素比，通常用于支持高DPI（Retina）屏幕
renderer.setPixelRatio(window.devicePixelRatio);
```

- **用途：** 支持高 DPI（Retina）屏幕，确保渲染的图像质量在高分辨率屏幕上更清晰。
- **解释：** `window.devicePixelRatio` 表示设备的像素比，通常是 1，但在高 DPI 屏幕上可能是 2 或更高。通过设置像素比，我们适应不同分辨率的屏幕。

综合起来，这段代码保证了在窗口大小变化时，Three. Js 场景能够适应新的视口尺寸，从而保持正确的渲染。