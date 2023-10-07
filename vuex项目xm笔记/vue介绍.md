Vue 是一个用于构建用户界面的 JavaScript 框架，它基于标准的 HTML、CSS 和 JavaScript 构建，并提供了一套声明式的、组件化的编程模型，帮助你高效地开发用户界面。无论是简单还是复杂的界面，Vue 都可以胜任。下面是一个最基本的示例：

```html
<div id="app">
  <p>{{ message }}</p>
</div>
```

```js
import { createApp } from "vue";
createApp({
  data() {
    return { message: "Vue 3 Hello World" };
  },
}).mount("#app");
```

结果展示

<p>Vue 3 Hello World</p>

上面的示例展示了 Vue 的两个核心功能：

- 声明式渲染：Vue 基于标准 HTML 拓展了一套模板语法，使得我们可以声明式地描述最终输出的 HTML 和 JavaScript 状态之间的关系。
- 响应性：Vue 会自动跟踪 JavaScript 状态并在其发生变化时响应式地更新 DOM。

你可能已经有了些疑问——先别急，在后续的文档中我们会详细介绍每一个细节。现在，请继续看下去，以确保你对 Vue 作为一个框架到底提供了什么有一个宏观的了解。

预备知识

文档接下来的内容会假设你对 HTML、CSS 和 JavaScript 已经基本熟悉。如果你对前端开发完全陌生，最好不要直接从一个框架开始进行入门学习——最好是掌握了基础知识再回到这里。你可以通过这篇 来检验你的 JavaScript 知识水平。如果之前有其他框架的经验会很有帮助，但也不是必须的。

渐进式框架

Vue 是一个框架，也是一个生态。其功能覆盖了大部分前端开发常见的需求。但 Web 世界是十分多样化的，不同的开发者在 Web 上构建的东西可能在形式和规模上会有很大的不同。考虑到这一点，Vue 的设计非常注重灵活性和“可以被逐步集成”这个特点。根据你的需求场景，你可以用不同的方式使用 Vue：

- 无需构建步骤，渐进式增强静态的 HTML
- 在任何页面中作为 Web Components 嵌入
- 单页应用 (SPA)
- 全栈 / 服务端渲染 (SSR)
- Jamstack / 静态站点生成 (SSG)
- 开发桌面端、移动端、WebGL，甚至是命令行终端中的界面

如果你是初学者，可能会觉得这些概念有些复杂。别担心！理解教程和指南的内容只需要具备基础的 HTML 和 JavaScript 知识。即使你不是这些方面的专家，也能够跟得上。如果你是有经验的开发者，希望了解如何以最合适的方式在项目中引入 Vue，或者是对上述的这些概念感到好奇，我们在 中讨论了有关它们的更多细节。

无论再怎么灵活，Vue 的核心知识在所有这些用例中都是通用的。即使你现在只是一个初学者，随着你的不断成长，到未来有能力实现更复杂的项目时，这一路上获得的知识依然会适用。如果你已经是一个老手，你可以根据实际场景来选择使用 Vue 的最佳方式，在各种场景下都可以保持同样的开发效率。这就是为什么我们将 Vue 称为“渐进式框架”：它是一个可以与你共同成长、适应你不同需求的框架。

单文件组件

在大多数启用了构建工具的 Vue 项目中，我们可以使用一种类似 HTML 格式的文件来书写 Vue 组件，它被称为单文件组件(也被称为 *.vue文件，英文 Single-File Components，缩写为 SFC)。顾名思义，Vue 的单文件组件会将一个组件的逻辑 (JavaScript)，模板 (HTML) 和样式 (CSS) 封装在同一个文件里。下面我们将用单文件组件的格式重写上面的计数器示例：

```html
<script>
export default {
  data() {
    return { count: 0 };
  },
};
</script>
<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>
<style scoped>
button {
  font-weight: bold;
}
</style>
```

单文件组件是 Vue 的标志性功能。如果你的用例需要进行构建，我们推荐用它来编写 Vue 组件。你可以在后续相关章节里了解更多关于单文件组件的用法及用途。但你暂时只需要知道 Vue 会帮忙处理所有这些构建工具的配置就好。

API 风格

Vue 的组件可以按两种不同的风格书写：选项式 API和组合式 API。

选项式 API (Options API)

使用选项式 API，我们可以用包含多个选项的对象来描述组件的逻辑，例如 data、methods和 mounted。选项所定义的属性都会暴露在函数内部的 this上，它会指向当前的组件实例。

```html
<script>
export default {
  // data() 返回的属性将会成为响应式的状态
  // 并且暴露在 `this` 上
  data() {
    return { count: 0 };
  },
  // methods 是一些用来更改状态与触发更新的函数
  // 它们可以在模板中作为事件监听器绑定
  methods: {
    increment() {
      this.count++;
    },
  },
  // 生命周期钩子会在组件生命周期的各个不同阶段被调用
  // 例如这个函数就会在组件挂载完成后被调用
  mounted() {
    console.log(`The initial count is ${this.count}.`);
  },
};
</script>
<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

选项式 API 是 Vue 最初提供的 API 风格，也是目前最常见和广泛使用的风格。如果你之前有其他框架（如 React）的经验，可能会觉得这种风格有些奇怪，但它有一些优点：

- 它很容易上手，因为每个选项都有明确的含义和作用。
- 它很容易阅读和理解，因为每个选项都是按照功能进行分组和命名。
- 它很容易测试和调试，因为每个选项都是独立且可复用的。

你可以在后续相关章节里了解更多关于选项式 API 的用法及用途。