在 Vue.js 中，数组的变异方法被包装以便它们也能触发视图的更新。当你在组件的 `data` 中定义一个数组，Vue 会使用这些包装过的方法替换掉数组实例的默认方法。这些被改写的方法有：`push()`, `pop()`, `shift()`, `unshift()`, `splice()`, `sort()`, 和 `reverse()`。

### 工作原理简述

Vue 不能检测以下数组变动的情况：

1. 当你利用索引直接设置一个项时，例如：`vm.items[indexOfItem] = newValue`；
2. 当你修改数组的长度时，例如：`vm.items.length = newLength`。

为了解决第一点，你可以使用 Vue.set：

```javascript
Vue.set(vm.items, indexOfItem, newValue)
```

或者用数组的 `splice` 方法：

```javascript
vm.items.splice(indexOfItem, 1, newValue)
```

为了解决第二点，你可以使用 `splice`：

```javascript
vm.items.splice(newLength)
```

### 针对数组的响应式处理

让我们更深入了解一下 Vue 是如何处理数组响应式的。Vue 通过在数组实例上覆盖上述这些方法，使它们变为变异方法（mutator methods），来检测数组的变化。这些方法被改写以便可以发出更新事件。

例如，当你调用 `push` 方法添加一个新项到数组时：

```javascript
vm.items.push(newItem)
```

Vue 首先调用改写过的 `push` 方法，添加新项，然后通知依赖（即在此数组上有数据绑定的指令或计算属性）更新视图。

### 注意事项

由于 JavaScript 的限制，Vue 不能检测数组和对象的变化。因此，需要特殊的方法来处理这些类型的变化，并触发视图更新。对于数组，Vue 提供了上述变异方法来检测变化并更新视图。对于对象，Vue 不能检测到对象属性的添加或删除，但它可以检测到直接修改属性值的变化。