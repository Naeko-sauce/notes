在 Three. Js 中，物体的旋转属性通常用弧度（radians）来表示，而不是角度（degrees）。Math. PI 是一个 JavaScript 中表示圆周率的常量，约等于 3.14159。

在你的代码中，`gsap.to(cube.rotation, { y: Math.PI / 2, duration: 5 })` 的意思是让方块绕其 y 轴旋转 π/2 弧度，即 90 度。这是因为一个完整的圆周共有 2π 弧度，所以 π/2 弧度相当于四分之一圆周，即 90 度。

使用弧度而不是角度是因为在计算机图形学和数学中，弧度更为自然和方便。三角函数（如 sin、cos、tan）通常使用弧度作为输入。在 Three. Js 中，旋转、角度等属性都是以弧度为单位的。

如果你更习惯使用角度，你可以使用 Three. Js 的 `THREE.MathUtils.degToRad()` 方法将角度转换为弧度。例如：

```javascript
gsap.to(cube.rotation, { y: THREE.MathUtils.degToRad(90), duration: 5 });
``` 

这里，`THREE.MathUtils.degToRad(90)` 将 90 度转换为对应的弧度。