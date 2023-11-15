以下是一些常用的 JavaScript 获取 HTML 元素的方法，并提供了详细说明：

### 1. **`document.getElementById(id)`**

- **描述：** 通过元素的 ID 获取元素。
- **示例：**
  ```javascript
  var element = document.getElementById("exampleElement");
  ```

### 2. **`document.getElementsByClassName(className)`**

- **描述：** 通过类名获取元素集合。
- **示例：**
  ```javascript
  var elements = document.getElementsByClassName("exampleClass");
  ```

### 3. **`document.getElementsByTagName(tagName)`**

- **描述：** 通过标签名获取元素集合。
- **示例：**
  ```javascript
  var elements = document.getElementsByTagName("div");
  ```

### 4. **`document.querySelector(selector)`**

- **描述：** 通过 CSS 选择器获取第一个匹配的元素。
- **示例：**
  ```javascript
  var element = document.querySelector("#exampleElement");
  ```

### 5. **`document.querySelectorAll(selector)`**

- **描述：** 通过 CSS 选择器获取所有匹配的元素集合。
- **示例：**
  ```javascript
  var elements = document.querySelectorAll(".exampleClass");
  ```

### 6. **`element.parentNode`**

- **描述：** 获取元素的父节点。
- **示例：**
  ```javascript
  var parentElement = document.getElementById("exampleElement").parentNode;
  ```

### 7. **`element.children`**

- **描述：** 获取元素的所有子元素集合。
- **示例：**
  ```javascript
  var childElements = document.getElementById("exampleElement").children;
  ```

### 8. **`element.nextElementSibling`**

- **描述：** 获取元素的下一个同级元素。
- **示例：**
  ```javascript
  var nextElement = document.getElementById("exampleElement").nextElementSibling;
  ```

### 9. **`element.previousElementSibling`**

- **描述：** 获取元素的上一个同级元素。
- **示例：**
  ```javascript
  var prevElement = document.getElementById("exampleElement").previousElementSibling;
  ```

### 10. **`document.querySelector` 和 `document.querySelectorAll` 结合使用的高级选择**

- **描述：** 可以结合多个选择器，实现更复杂的元素选择。
- **示例：**
  ```javascript
  var complexElements = document.querySelectorAll(".parentClass .childClass");
  ```

### 11. **`document.querySelector` 和 `element.querySelector`**

- **描述：** 可以在整个文档或特定元素的范围内使用 CSS 选择器。
- **示例：**
  ```javascript
  var element = document.getElementById("exampleElement");
  var nestedElement = element.querySelector(".nestedClass");
  ```

这些是一些常用的获取 HTML 元素的方法，你可以根据你的需求选择合适的方法。使用这些方法时，请确保选择器、类名、ID 等信息正确匹配你的 HTML 结构。