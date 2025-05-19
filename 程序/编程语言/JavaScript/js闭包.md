# JavaScript 闭包

#技术笔记 #JavaScript #函数式编程

## 概述
> 闭包是 JavaScript 中的一个重要概念，它允许函数记住并访问其创建时的作用域，即使该函数在其他地方执行。通过闭包，我们可以实现数据私有化、状态保持等重要功能。

## 核心要点
1. 闭包是函数和其词法环境的组合
2. 内部函数可以访问外部函数的变量
3. 闭包可以维持状态，实现数据私有化
4. 需要注意内存管理和性能影响

## 基础概念
### 1. 词法作用域
- 解释：函数的作用域在函数定义时就已确定
- 示例代码
```javascript
let name = "全局";
function outer() {
    let name = "外部";
    function inner() {
        console.log(name); // 输出"外部"
    }
    inner();
}
outer();
```
- 注意：闭包遵循词法作用域规则，始终访问定义时的变量

### 2. 函数作为返回值
- 解释：当函数返回函数时，返回的函数会记住其定义时的环境
```javascript
function createCounter() {
    let count = 0;
    return function() {
        return ++count;
    };
}
const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

## 实际应用
### 1. 数据私有化
- 场景描述：创建私有变量，防止外部直接访问
```javascript
function createUser(name) {
    let age = 0;
    return {
        getName: () => name,
        getAge: () => age,
        growOlder: () => ++age
    };
}
const user = createUser("张三");
```

### 2. 函数工厂
- 场景描述：创建具有特定行为的函数
```javascript
function multiply(x) {
    return function(y) {
        return x * y;
    };
}
const double = multiply(2);
console.log(double(5)); // 10
```

## 最佳实践
1. 合理使用
   - 只在必要时创建闭包
   - 及时清除不再使用的闭包引用
2. 避免常见陷阱
   - 使用 let/const 替代 var
   - 注意循环中的闭包问题

## 常见问题
### 内存泄漏
- 问题描述：闭包会持续占用内存
- 解决方案：
```javascript
let closure = createLargeClosure();
// 使用完后清除引用
closure = null;
```
- 预防：合理管理闭包的生命周期

### 循环中的闭包
- 问题描述：var 声明在循环中可能导致意外结果
- 解决方案：使用 let 或 IIFE

## 高级特性
- 模块化封装
- 柯里化实现
- 事件处理和回调函数
- 异步编程中的应用

## 相关链接
- [[js作用域链]]
- [[js垃圾回收机制]]
- [[js箭头函数]]

## 参考资源
- MDN 文档：[闭包](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)
- JavaScript 高级程序设计（第4版）
- You Don't Know JS：作用域与闭包

#更新日期_2024_03_18