客户端标记的概念：

在 Vue 项目中，特别是使用 SSR（服务端渲染）的项目里，代码会在两个地方运行：
1. 服务器端（Node. Js 环境）
2. 浏览器端（客户端）

但是 Three. Js 这样的 3 D 库需要访问浏览器特有的 API（比如 WebGL），这些在服务器端是不存在的。所以我们需要告诉 Vue："这段代码只能在浏览器中运行"。

这就是为什么要添加客户端标记：

```typescript:d:\learn\blog\components\practice\donut.vue
const isBrowser = typeof window !== 'undefined'  // 检查是否在浏览器环境

onMounted(() => {
  if (!isBrowser) return  // 如果不是浏览器环境就不执行

  // Three.js 相关代码
  const scene = new THREE.Scene()
  // ... 其他代码
})
```

简单来说：
- `typeof window !== 'undefined'` 检查是否存在 `window` 对象
- 在浏览器中 `window` 总是存在的
- 在服务器端 `window` 是 `undefined`
- 这样就能确保 Three. Js 代码只在浏览器中运行

如果你的其他 Three. Js 组件没问题，可能是因为它们刚好不会在服务器端执行，但添加这个检查是一个好习惯，可以预防潜在的问题。![[Pasted image 20250318232010.png]]