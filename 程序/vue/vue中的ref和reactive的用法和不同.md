在 Vue 3 中，`ref` 和 `reactive` 是两种用于创建响应式数据的不同方法，它们的使用方法和特点有所不同。

1. **`ref`**：

   - 使用方法：`ref` 函数接受一个初始值作为参数，并返回一个包装后的响应式对象。

     ```javascript
     import { ref } from 'vue';
     
     const count = ref(0);
     ```

   - 特点：
     - `ref` 创建的对象是一个包装了基本数据类型的响应式对象，例如数字、字符串等。
     - 访问 `ref` 创建的对象的值需要使用 `.value` 属性，例如 `count.value`。
     - 通常用于创建单一的响应式数据。

2. **`reactive`**：

   - 使用方法：`reactive` 函数接受一个普通对象作为参数，并返回一个包装后的响应式代理对象。

     ```javascript
     import { reactive } from 'vue';
     
     const state = reactive({ count: 0 });
     ```

   - 特点：
     - `reactive` 创建的对象可以包含多个属性，这些属性都会成为响应式数据。
     - 可以直接访问 `reactive` 创建的对象的属性，例如 `state.count`。
     - 通常用于创建包含多个属性的响应式数据。

关于这两者之间的主要不同点：
- `ref` 适用于包装单一的基本数据类型（例如数字、字符串）。
- `reactive` 适用于包装普通 JavaScript 对象，可以包含多个属性。

在实际开发中，根据您的需求和数据结构的复杂性，选择使用 `ref` 或 `reactive`。通常，如果只需要管理一个简单的值，可以使用 `ref`，而如果需要管理包含多个属性的对象，则可以使用 `reactive`。例如，管理一个计数器的值可以使用 `ref`，而管理一个表单的数据可以使用 `reactive`。