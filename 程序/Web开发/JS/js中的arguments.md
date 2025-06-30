`arguments` 是 JavaScript 中函数内部的一个**类数组对象**，它包含了传递给函数的所有参数。

---

## ✅ 你必须掌握的重点：

### 🌟 1. `arguments` 是什么？

- 它是一个 **类数组对象**（不是数组）。
    
- 包含了调用函数时传入的所有 **实参**。
    
- 只在**普通函数**中可用，**箭头函数中没有** `arguments`。
    

---

### 🌟 2. 示例

```js
function test(a, b) {
  console.log(arguments);
  console.log(arguments[0]); // 第一个参数
  console.log(arguments.length); // 参数个数
}
test(1, 2, 3);
```

输出：

```
[Arguments] { '0': 1, '1': 2, '2': 3 }
1
3
```

---

### 🌟 3. 类数组的意思？

`arguments` 拥有 `length` 和通过索引访问的能力，但没有数组的方法（如 `forEach`、`map` 等）。

你可以用下列方法转为真正数组：

```js
let args = Array.from(arguments);
// 或
let args = [...arguments]; // ES6 语法
```

---

### 🌟 4. `arguments` 和形参的关系

```js
function foo(x) {
  arguments[0] = 100;
  console.log(x); // 100
}
foo(1);
```

在非严格模式下，`arguments[0]` 和 `x` 是**绑定的**，改一个另一个也变。

但在严格模式（`'use strict'`）下，它们**不会联动**。

---

### 🌟 5. 在箭头函数中无效

```js
const arrow = () => {
  console.log(arguments);
};
arrow(1, 2, 3); // ❌ 报错：arguments is not defined
```

箭头函数中根本没有 `arguments`，要用 rest 参数代替：

```js
const arrow = (...args) => {
  console.log(args); // ✅ [1, 2, 3]
};
```

---

## ✅ 小结（一定要记住）：

| 特性      | 是否成立     |
| ------- | -------- |
| 类数组对象   | ✅        |
| 只有函数作用域 | ✅        |
| 箭头函数可用？ | ❌        |
| 可修改参数值？ | ✅（非严格模式） |
| 能用数组方法？ | ❌        |

---

