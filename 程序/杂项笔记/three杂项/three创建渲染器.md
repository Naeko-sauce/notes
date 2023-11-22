## 创建渲染器 console. Log (canvas); const renderer = new THREE. WebGLRenderer ({ canvas: canvas })
这段代码用于创建 Three. Js 的渲染器（`THREE.WebGLRenderer`）并将其连接到一个 HTML 5 Canvas 元素上。让我逐步解释：

1. `THREE`：这是 Three. Js 库的命名空间，其中包含了创建和操作 3 D 图形的各种类和函数。

2. `WebGLRenderer`：`THREE.WebGLRenderer` 是 Three. Js 中表示使用 WebGL 渲染的渲染器类。WebGL 是一种用于在浏览器中进行高性能图形渲染的技术。

3. `const renderer = new THREE.WebGLRenderer({ canvas: canvas })`：这是创建 `THREE.WebGLRenderer` 类的一个新实例，即创建了一个新的 WebGL 渲染器对象。构造函数的参数是一个包含配置选项的对象。

   - `{ canvas: canvas }`：这个选项指定了渲染器要使用的 HTML 5 Canvas 元素。在这里，`canvas` 变量应该是在代码的其他地方定义的一个引用，指向你的 HTML 文件中的 `<canvas>` 元素。

   - 通过将渲染器连接到特定的 Canvas 元素，你告诉 Three. Js 在这个 Canvas 上进行图形渲染。

4. `console.log(canvas)`：这是一个用于在控制台输出日志的语句，将 `canvas` 变量的值打印到控制台。这有助于验证 `canvas` 是否被正确引用。

总体来说，这段代码创建了一个 Three. Js 渲染器，并将其连接到指定的 HTML 5 Canvas 元素上，以便在这个 Canvas 上进行 3 D 场景的渲染。





  