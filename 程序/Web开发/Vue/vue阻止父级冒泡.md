要阻止点击事件冒泡到父级元素，您可以在子元素上使用 `@click` 指令，并在事件处理程序中调用 `event.stopPropagation()` 方法。以下是示例代码：

```vue
<template>
  <div @click="parentClick">
    <button @click="childClick">Click Me</button>
  </div>
</template>

<script>
export default {
  methods: {
    parentClick() {
      console.log('Parent Clicked');
    },
    childClick(event) {
      // 阻止事件冒泡到父级元素
      event.stopPropagation();
      console.log('Child Clicked');
    },
  },
};
</script>
```

在上面的示例中，当您点击 "Click Me" 按钮时，会触发子元素上的 `childClick` 方法，但不会触发父级元素上的 `parentClick` 方法，因为 `event.stopPropagation()` 阻止了事件冒泡。

这是一种常见的方式，可以在需要时精确地控制事件冒泡行为。