
---

## 🌟 一、`apply` 是谁的？

`apply` 是**函数对象（Function）的一个方法**，每个函数都可以使用它。

它的作用是：

> **调用一个函数，并手动指定这个函数运行时的 `this`（也就是它的“上下文”），同时通过数组传参。**

---

## 🧠 二、apply 的语法

```js
func.apply(thisArg, [argsArray])
```

### 参数解释：

|参数|作用|
|---|---|
|`thisArg`|要把函数内部的 `this` 设置成这个值|
|`argsArray`|把参数作为一个**数组**传入函数|

---

## 🎯 三、举个最简单的例子

```js
function sayName(age) {
  console.log(this.name, age);
}

const person = {
  name: "小明"
};

sayName.apply(person, [18]);  // 输出：小明 18
```

解释：

- `sayName` 是一个独立的函数
    
- 本来直接调用 `sayName()` 时，`this` 是 `window`
    
- 现在我们用 `apply(person, [18])` 把 `this` 指定成 `person`，把参数 `18` 用数组传进去
    

---

## 🧩 四、和 call 的区别

```js
// apply
func.apply(thisArg, [参数1, 参数2, ...]);

// call
func.call(thisArg, 参数1, 参数2, ...);
```

唯一的区别就是：

- `call` 用 **逗号** 传参
    
- `apply` 用 **数组** 传参
    

### 举例：

```js
function sum(a, b) {
  console.log(this.title, a + b);
}

const book = { title: "JavaScript高级" };

sum.call(book, 2, 3);       // JavaScript高级 5
sum.apply(book, [2, 3]);    // JavaScript高级 5
```

---

## 🧰 五、apply 的常见应用场景

### 1. ✅ 借用其他对象的方法

```js
const obj = {
  name: 'Alice'
};

function show() {
  console.log(this.name);
}

show.apply(obj);  // Alice
```

---

### 2. ✅ 伪数组变成真数组（老写法）

```js
function demo() {
  // arguments 是伪数组
  const args = Array.prototype.slice.apply(arguments);
  console.log(args); // 真数组
}

demo(1, 2, 3); // [1, 2, 3]
```

---

### 3. ✅ 利用 apply 实现数组最大值最小值

```js
const nums = [3, 99, 45, 23];

console.log(Math.max.apply(null, nums)); // 99
console.log(Math.min.apply(null, nums)); // 3
```

`Math.max` 不能直接接数组，要拆开，而 `apply` 可以帮你拆！

---

## 🖼️ 六、图解：apply 过程

```
function say(age) {
  console.log(this.name, age);
}

const person = { name: "小红" };

say.apply(person, [18]);

          ↓

say 函数内部运行时：

this -> 指向 person
参数 -> [18]
相当于执行 person.say(18)
```

---

## 🚫 七、注意事项

### 1. `thisArg` 可以是 `null` 或 `undefined`

```js
function test() {
  console.log(this);
}

test.apply(null); // 浏览器中：this 是 window
```

### 2. 参数必须是数组或类似数组的对象

```js
func.apply(obj, [1, 2]); // ✅
func.apply(obj, 1, 2);   // ❌ 错误写法
```

---

## 📦 八、apply、call、bind 的对比总结

|方法|是否立即执行|参数形式|this 指定方式|
|---|---|---|---|
|`call`|✅ 立即执行|参数用逗号分隔|指定 this|
|`apply`|✅ 立即执行|参数用数组传入|指定 this|
|`bind`|❌ 返回一个新函数|参数用逗号分隔|指定 this|

---

## ✅ 总结一句话

> `apply` 是用来**改变函数内部的 `this` 指向，并用数组传参的工具函数**，在需要手动控制 `this` 和传入参数格式时非常有用。

---

如果你还想看动画演示，或结合项目实际使用场景（比如事件委托、借用原型方法等）我也可以继续讲。要不要继续深入？