在 Vue.js 中，`v-for` 的优先级高于 `v-if`。这意味着如果你在同一个元素上同时使用了 `v-for` 和 `v-if`，`v-for` 将比 `v-if` 先执行。

这里有一个使用两者的例子：

```html
<ul>
  <li v-for="item in items" v-if="item.isActive">
    {{ item.name }}
  </li>
</ul>
```

在这个例子中，`v-for` 将首先遍历 `items` 数组，然后 `v-if` 会过滤那些不满足 `isActive` 条件的项目。

**注意**：Vue 官方文档建议尽可能避免在同一个元素上同时使用 `v-for` 和 `v-if`，因为这样做可能会导致性能问题。如果你需要在循环中进行条件判断，最佳的做法通常是计算属性中处理这些逻辑，使得模板保持简洁和高效。例如：

```html
<template>
  <ul>
    <li v-for="item in activeItems" :key="item.id">
      {{ item.name }}
    </li>
  </ul>
</template>

<script>
export default {
  computed: {
    activeItems() {
      return this.items.filter(item => item.isActive);
    }
  },
  data() {
    return {
      items: [
        { id: 1, name: 'Item 1', isActive: true },
        { id: 2, name: 'Item 2', isActive: false },
        // ... more items
      ]
    };
  }
};
</script>
```

在这个优化后的例子中，`activeItems` 计算属性会提前过滤出活跃的项，模板中就不需要 `v-if` 检查了，也避免了在同一个元素上同时使用 `v-for` 和 `v-if` 的潜在性能问题。