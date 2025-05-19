在 JavaScript 中，`var`、`let` 和 `const` 是用于声明变量的关键字，但它们之间有一些重要的区别，主要体现在作用域、重声明、可变性以及提升行为上。

---

### 1. **作用域**

- **`var`**
    
    - 具有函数作用域 (Function Scope)，如果在函数外声明，它会被视为全局变量。
    - 它不会受块作用域 (Block Scope) 的限制，容易导致变量泄漏。
    
    ```javascript
    if (true) {
        var x = 10;
    }
    console.log(x); // 输出: 10
    ```
    
- **`let`**
    
    - 具有块作用域 (Block Scope)，在 `{}` 内声明的变量，只在块内有效。
    
    ```javascript
    if (true) {
        let y = 20;
    }
    console.log(y); // ReferenceError: y is not defined
    ```
    
- **`const`**
    
    - 也具有块作用域，与 `let` 一样仅在块内有效。

---

### 2. **重声明**

- **`var`**
    
    - 可以在同一个作用域内多次声明同名变量，后者会覆盖前者。
    
    ```javascript
    var a = 5;
    var a = 10; // 允许
    console.log(a); // 输出: 10
    ```
    
- **`let` 和 `const`**
    
    - 在同一作用域内不允许重复声明同名变量。
    
    ```javascript
    let b = 15;
    let b = 25; // SyntaxError: Identifier 'b' has already been declared
    ```
    

---

### 3. **可变性**

- **`var` 和 `let`**
    
    - 声明的变量是可变的，可以重新赋值。
    
    ```javascript
    let c = 30;
    c = 35; // 允许
    ```
    
- **`const`**
    
    - 声明的变量是不可变的，必须立即赋值，并且不能重新赋值。
    
    ```javascript
    const d = 40;
    d = 45; // TypeError: Assignment to constant variable
    ```
    
    > 注意：对于对象或数组，`const` 限制的是变量的绑定，而不是对象本身的内容。可以修改对象的属性或数组的元素。
    
    ```javascript
    const obj = { name: "Alice" };
    obj.name = "Bob"; // 允许
    console.log(obj.name); // 输出: "Bob"
    ```
    

---

### 4. **提升 (Hoisting)**

- **`var`**
    
    - 会被提升到其作用域的顶部，但不会初始化。
    
    ```javascript
    console.log(e); // 输出: undefined
    var e = 50;
    ```
    
- **`let` 和 `const`**
    
    - 也会被提升，但存在 **暂时性死区 (Temporal Dead Zone)**，在变量声明之前访问会导致错误。
    
    ```javascript
    console.log(f); // ReferenceError: Cannot access 'f' before initialization
    let f = 60;
    ```
    

---

### 总结

|特性|`var`|`let`|`const`|
|---|---|---|---|
|**作用域**|函数作用域|块作用域|块作用域|
|**重声明**|允许|不允许|不允许|
|**可变性**|可变|可变|不可变（绑定）|
|**提升行为**|提升且初始化为 `undefined`|提升但不可用（死区）|提升但不可用（死区）|

推荐：

- **使用 `let` 和 `const`** 来代替 `var`。
- 对于不会重新赋值的变量，优先使用 `const`。