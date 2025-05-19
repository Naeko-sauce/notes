`className` 是 JavaScript 中用于访问和操作 HTML 元素的 `class` 属性的属性。`class` 属性用于为元素指定一个或多个样式类，这些样式类定义了元素的外观和样式。

### 获取元素的 `class`：

要获取 HTML 元素的 `class` 属性值，可以使用 `className` 属性。以下是一个简单的例子：

```javascript
var element = document.getElementById("exampleElement");
var classValue = element.className;

console.log(classValue);
```

上述代码中，`exampleElement` 应该替换为你想要获取样式类的 HTML 元素的实际 ID。`className` 将返回一个字符串，其中包含该元素的所有样式类，以空格分隔。

### 设置元素的 `class`：

要设置 HTML 元素的 `class` 属性值，同样可以使用 `className` 属性。下面是一个设置样式类的例子：

```javascript
var element = document.getElementById("exampleElement");
element.className = "newClass1 newClass2";

// 或者通过追加样式类
element.className += " additionalClass";
```

上述代码中，`newClass1`、`newClass2` 和 `additionalClass` 是你要设置的样式类。注意，通过直接赋值，你会覆盖元素原有的样式类。如果要追加样式类而不覆盖，可以使用字符串拼接或者使用 `classList`。

### 使用 `classList` 进行更灵活的样式类操作：

`classList` 是一个 DOMTokenList 对象，提供了一组方法来操作元素的类列表。这些方法包括：

- `add(className)`: 添加一个样式类。
- `remove(className)`: 移除一个样式类。
- `toggle(className)`: 切换一个样式类的状态（如果存在则移除，如果不存在则添加）。
- `contains(className)`: 检查元素是否包含某个样式类。

```javascript
var element = document.getElementById("exampleElement");

// 添加一个样式类
element.classList.add("newClass");

// 移除一个样式类
element.classList.remove("oldClass");

// 切换一个样式类的状态
element.classList.toggle("toggleClass");

// 检查是否包含某个样式类
var hasClass = element.classList.contains("checkClass");
```

使用 `classList` 的方法可以更方便地进行对样式类的增加、删除、切换和检查。这是一个更现代和灵活的方式，特别是在需要动态地操作样式类时。