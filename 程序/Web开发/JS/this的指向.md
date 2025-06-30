 * 在大多数情况下，this 都是出现在函数中
```
console.log(this)

```
* 在全局作用域下 this 的指向是 window（global object）
* 在 node 环境下 this 指向的是空 {}
```
// this的指向是什么跟函数的位置是没有关系的

// 跟函数的调用方式是有关系的

console.log(this);

function foo() {

  console.log(this);

}

foo(); // 在浏览器中，this指向window对象

var obj = {

  name: 'obj',

  foo:foo

}

obj.foo(); // 在浏览器中，this指向obj对象

foo.apply("asd")// 在浏览器中，
```