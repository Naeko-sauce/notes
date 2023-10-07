- 性能优化：Vue 3 使用了 Proxy 代替 Object.defineProperty 来实现响应式系统，提高了数据变化的检测速度和精确度。同时，Vue 3 也引入了 Tree-shaking 和 Fragments 等技术，减少了打包体积和渲染开销。
- 组合式 API：Vue 3 提供了一套新的 API 风格，允许我们在 setup 函数中使用 reactive、ref、computed、watch、watchEffect 等函数来组织和复用组件的逻辑。这样可以让我们按照功能而不是选项来组织代码，提高了可读性和可维护性。
- 更好的 TypeScript 支持：Vue 3 的源码完全用 TypeScript 重写，提供了更完善的类型定义和推断。同时，Vue 3 也支持在单文件组件中使用 TypeScript 语法，让我们可以享受类型检查和智能提示的优势。
- 新增的组件：Vue 3 新增了三个内置组件：Fragment、Teleport 和 Suspense。Fragment 允许我们在模板中返回多个根节点，而不需要额外的包裹元素。Teleport 允许我们将子组件的内容传送到 DOM 中的任意位置，例如模态框或弹出框。Suspense 允许我们在等待异步组件时显示一个备用内容，例如加载中或错误提示。
- 自定义渲染器 API：Vue 3 提供了一个自定义渲染器 API，让我们可以使用 Vue 的响应式系统和组合式 API 来渲染任何目标平台，例如 Canvas、SVG 或 Webgl。这样可以让我们开发出更多富有创意和交互性的应用。

以上是我为你找到的 Vue 3 的新特性的概览，希望对你有所帮助。如果你想要更详细的说明，你可以参考以下的链接：

- vue3新特性概览_vue3 tree_devincob的博客-CSDN博客