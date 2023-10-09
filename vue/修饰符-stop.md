`stop` 修饰符用于阻止事件冒泡。在 DOM 编程中，事件冒泡是指一个事件触发后，不仅在该元素触发，还会在它的所有祖先元素中依次触发。使用 `.stop` 修饰符，我们可以阻止这种冒泡行为。

下面是一个示例，说明 `.stop` 修饰符如何起作用：

### HTML

```html
<template>
  <div @click="parentClick">
    Parent
    <button @click.stop="buttonClick">Button</button>
  </div>
</template>
```

### JavaScript

```javascript
<script>
export default {
  methods: {
    parentClick() {
      alert("Parent Div Clicked!");
    },
    buttonClick() {
      alert("Button Clicked!");
    }
  }
};
</script>
```

在这个示例中，我们有一个包含按钮的 `div` 元素。我们为 `div` 和 `button` 元素分别绑定了不同的点击事件处理器。正常情况下，如果你点击了按钮，两个处理器都会被触发，因为点击事件从按钮冒泡到了 `div` 元素。

但在这个案例中，我们在按钮的点击事件处理器上使用了 `.stop` 修饰符，所以当你点击按钮时，只有 `buttonClick` 方法会被调用，`parentClick` 方法不会被调用，因为 `.stop` 阻止了事件冒泡到父元素 `div`。

简而言之：
- 点击 "Button"：你只会看到 "Button Clicked!" 的警告框，因为 `.stop` 阻止了事件冒泡。
- 点击 "Parent" 文字：你会看到 "Parent Div Clicked!" 的警告框。

这就是 `.stop` 修饰符的基本作用。希望这个示例能够清晰地展示它是如何工作的！