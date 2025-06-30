在 JavaScript 中，`this` 是一个非常重要但又经常让人困惑的概念，它代表的是**当前函数执行时的上下文对象**。  
但 `this` 究竟指向谁，是有一套“**绑定规则**”的。

---

## 🌟 this 的五大绑定规则（经典版）

我们可以用一个口诀来记：

> **默认规则、隐式规则、显式规则、new绑定、箭头函数**

---

## 🧠 一、默认绑定（普通函数调用）

### 规则：

如果一个函数是 **普通调用**，即不是被对象调用、没有 call/apply/bind，也不是箭头函数，那么 `this` 默认指向：

- **非严格模式下**：`this` 是 `window`
    
- **严格模式下**：`this` 是 `undefined`
    

### 示例：

```js
function show() {
  console.log(this);
}
show(); // 浏览器中：输出 window
```

严格模式：

```js
"use strict";
function show() {
  console.log(this);
}
show(); // 输出 undefined
```

---

## 🧠 二、隐式绑定（通过对象调用）

### 规则：

如果一个函数是**通过对象调用的**，那么 `this` 就是**那个对象**。

### 示例：

```js
const obj = {
  name: "小明",
  say() {
    console.log(this.name);
  }
};

obj.say(); // 输出：小明
```

---

## ❗ 注意隐式丢失（经典坑）

```js
const obj = {
  name: "小明",
  say() {
    console.log(this.name);
  }
};

const fn = obj.say;
fn(); // 输出：undefined（默认绑定，this 是 window）
```

---

## 🧠 三、显式绑定（call / apply / bind）

### 规则：

你可以使用 `call` / `apply` / `bind` 显式地指定 `this` 是谁。

### 示例：

```js
function show() {
  console.log(this.name);
}

const person = { name: "小红" };

show.call(person);  // 输出：小红
show.apply(person); // 输出：小红
```

#### bind 特别注意：

`bind` 返回一个**新函数**，并不会立即调用：

```js
const fn = show.bind(person);
fn(); // 输出：小红
```

---

## 🧠 四、new 绑定（构造函数）

### 规则：

当你使用 `new` 关键字调用函数时，`this` 会被绑定到**新创建的对象**上。

### 示例：

```js
function Person(name) {
  this.name = name;
  console.log(this);
}

const p = new Person("小明"); // this 是新创建的对象
```

---

## 🧠 五、箭头函数绑定（词法绑定）

### 规则：

箭头函数的 `this` **不会改变**，它的 `this` 取决于它**定义时所在的作用域**，不是调用方式决定的。

### 示例：

```js
const obj = {
  name: "小明",
  say: () => {
    console.log(this.name);
  }
};

obj.say(); // 输出 undefined，因为箭头函数的 this 是 window
```

再看一个常用例子：

```js
function outer() {
  const arrow = () => {
    console.log(this);
  };
  arrow();
}

outer.call({ name: "小红" }); // this 是 { name: "小红" }
```

箭头函数中的 `this` 来自 `outer` 的调用环境。

---

## 🔁 this 指向优先级（记住这个）

当多种规则同时出现时，有以下**优先级**：

```
new 绑定 > 显式绑定 (call/apply/bind) > 隐式绑定 > 默认绑定
```

比如：

```js
function foo() {
  console.log(this.name);
}

const obj = { name: "隐式", foo };
const other = { name: "显式" };

obj.foo.call(other); // 输出：显式（显式绑定 > 隐式绑定）
```

---

## 📦 总结成表格：

| 场景              | this 指向                      |
| --------------- | ---------------------------- |
| 普通函数调用          | 非严格模式下是 window；严格是 undefined |
| 对象方法调用          | 该对象                          |
| call/apply/bind | 被绑定的对象                       |
| 构造函数调用（new）     | 新创建的对象                       |
| 箭头函数            | 定义时所在作用域的 this               |
