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

非常好，我们继续深入拆解：

---

## 🎯 我们现在要搞懂的是：

> 为什么 `Array.prototype.slice.call(arguments)` 能把 `arguments` 变成数组？

---

## ✅ 第一步：理解 `call` 的作用

---

### 🔹 `call()` 是 JavaScript 中的函数方法

**作用：**  
👉 `call()` 用来**手动指定函数中的 `this` 指向**，然后立即执行这个函数。

### 🧪 示例：

```js
function sayName() {
  console.log(this.name);
}

const obj = { name: "张三" };

sayName.call(obj); // 输出：张三
```

解释：

- 本来 `sayName()` 中的 `this` 是 undefined 或 window
    
- `call(obj)` 强制让 `this = obj`
    

---

## ✅ 第二步：理解 `slice()` 是干嘛的

---

### 🔹 `slice()` 是数组的方法

**作用：** 从数组中“切”出一个新数组。

### 🧪 示例：

```js
const arr = [10, 20, 30, 40];
const result = arr.slice(1, 3);
console.log(result); // [20, 30]
```

---

## ✅ 第三步：组合起来使用

我们来看这一句完整的用法：

```js
Array.prototype.slice.call(arguments)
```

它的意思是：

1. 先找到数组的 `slice()` 方法（它本来是数组专属的）
    
2. 然后用 `call()` 强制把 `arguments` 当作 `slice()` 的作用目标（即：让 `this = arguments`）
    
3. `slice()` 方法就会把 `arguments` 这个类数组“切”成一个**新的数组**
    

---

### 🧠 图示理解：

```text
┌──────────────────────┐
│ Array.prototype.slice│ ← 数组自带的切片方法
└──────────┬───────────┘
           │
           ▼
      call(arguments)      ← 强行把类数组当作数组用
           │
           ▼
    实际执行效果：
    slice.call(arguments)
    === 把 arguments 拷贝成真数组
```

---

## 🧪 验证一下 `this` 是谁：

```js
function test() {
  function whoAmI() {
    console.log(this); // 查看this
  }
  whoAmI.call(arguments); // this 被设置为 arguments
}
test("张三", "李四");
```

输出：

```js
[Arguments] { '0': '张三', '1': '李四' }
```

这说明：**call(arguments)** 会把 `this` 变成 `arguments`。

---

## ✅ 最终结论

```js
Array.prototype.slice.call(arguments);
```

==> 就是在说：

> “我要借用数组的 `slice()` 方法，用它来处理 `arguments`，然后得到一个**真正的数组**”。

---

## 🔥 拓展：为什么不直接用 `arguments.slice()`？

因为 `arguments` 是个“**类数组**”，不是“真正的数组”，所以：

```js
arguments.slice(); // ❌ 报错：arguments.slice is not a function
```

这就是为什么我们必须“**借用**”数组的方法。

---

## ✨ ES6之后更简单：

你现在可以直接这样写：

```js
const args = [...arguments]; // ✅ 展开符
```

或者：

```js
const args = Array.from(arguments); // ✅
```

---


# ✅ `Array.prototype` 是什么？

---

## 🔍 一句话解释：

> `Array.prototype` 是 **所有数组实例共享的原型对象**，它上面定义了所有数组能用的方法，比如 `push()`、`pop()`、`map()`、`slice()` 等。

---

## 🧠 逐步拆解理解

---

### 🔸 JavaScript 中一切皆对象（包括数组）

当你写：

```js
let arr = [1, 2, 3];
```

你其实是创建了一个数组对象，它内部是通过构造函数 `Array()` 创建的。

就像这样：

```js
let arr = new Array(1, 2, 3);
```

---

### 🔸 所有数组都是 `Array` 构造函数造出来的

每个由 `Array` 构造函数创建的对象（数组），都会自动连接到 `Array.prototype` 上，也就是说：

```js
arr.__proto__ === Array.prototype // ✅ true
```

---

### 🔸 举个例子：

```js
let arr = [1, 2, 3];

console.log(arr.map); // [Function: map]
console.log(arr.filter); // [Function: filter]
```

这些方法（`map`, `filter`, `slice`, `push` 等）其实都定义在：

```js
Array.prototype.map
Array.prototype.filter
Array.prototype.slice
Array.prototype.push
```

---

## ✅ 所以 `Array.prototype` 是什么？

它是一个对象，里面装着数组的“通用方法”：

```js
console.log(Object.getOwnPropertyNames(Array.prototype));
```

输出（部分）：

```js
[
  'constructor',
  'toString',
  'push',
  'pop',
  'map',
  'filter',
  'slice',
  'forEach',
  'reduce',
  ...
]
```

---

## 🔁 原型链中的角色

你可以这样看待：

```js
let arr = [1, 2, 3];

arr → __proto__ → Array.prototype → Object.prototype
```

当你写 `arr.map()` 时，JavaScript 会顺着原型链去找：

1. 在 `arr` 自己身上找有没有 `map`
    
2. 找不到就去 `arr.__proto__`，也就是 `Array.prototype` 上找
    
3. 还找不到就继续往 `Object.prototype` 找
    

---

## 🔧 为什么 `Array.prototype.slice.call()` 能借用？

因为 `slice()` 是定义在 `Array.prototype` 上的函数：

```js
Array.prototype.slice
```

它默认作用于数组对象：

```js
[1,2,3].slice(0, 2) // ['1', '2']
```

你可以通过 `.call(XXX)` 强行让它作用于“像数组的对象”（比如 `arguments`），这就是所谓的“借用”。

---

## ✅ 总结重点：

|术语|含义|
|---|---|
|`Array`|数组的构造函数|
|`Array.prototype`|所有数组的原型对象|
|`arr.__proto__`|实际等于 `Array.prototype`|
|数组的方法从哪来？|都来自 `Array.prototype`|
|`slice` 的定义位置？|就是 `Array.prototype.slice`|

---

如果你还不清楚什么是 **原型链** 或 `__proto__` / `prototype` / `constructor` 的区别，我也可以帮你系统整理这三者的概念。

要继续吗？