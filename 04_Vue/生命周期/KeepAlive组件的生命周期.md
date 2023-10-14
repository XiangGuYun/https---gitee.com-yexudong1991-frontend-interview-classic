# keep-alive组件一般会经历怎么样的生命周期

在 Vue.js 中，`<keep-alive>` 是一个抽象组件，它用来保留组件的状态或避免重新渲染。当组件被包裹在 `<keep-alive>` 标签中时，它的部分生命周期钩子的行为会有所改变。这里是 `<keep-alive>` 的使用示例及其对组件生命周期的影响：

## 使用 `keep-alive`

```html
<keep-alive>
  <your-component v-if="shouldShowComponent"></your-component>
</keep-alive>
```

## 生命周期钩子的影响

### 1. 首次渲染组件：

- `beforeCreate`
- `created`
- `beforeMount`
- `mounted`

### 2. 当组件被切换（被包裹在 `keep-alive` 中的组件被切换走）：

- `deactivated`：当组件被缓存时触发。

### 3. 当组件被激活（从缓存中恢复显示）：

- `activated`：当组件被激活时触发。

### 4. 当组件被销毁：

- `beforeDestroy`
- `destroyed`

这里要注意的是，在组件被 `keep-alive` 缓存后，当组件切换时不会经历常规的卸载过程，而是触发 `deactivated` 钩子；同样地，当从缓存中恢复组件时，不会从头开始创建组件和挂载过程，而是触发 `activated` 钩子。

### 示例：

```javascript
export default {
  created() {
    console.log('created');
  },
  mounted() {
    console.log('mounted');
  },
  activated() {
    console.log('activated');
  },
  deactivated() {
    console.log('deactivated');
  },
  beforeDestroy() {
    console.log('beforeDestroy');
  },
  destroyed() {
    console.log('destroyed');
  }
}
```

通过合理利用 `activated` 和 `deactivated` 钩子，你可以实现在组件切换时保持或获取数据的逻辑，从而实现更加丰富和高效的页面切换效果。希望这些信息能帮助你更好地理解和利用 `keep-alive`！

## keep-alive组件的销毁时机是什么

在 Vue.js 中，`<keep-alive>` 组件用于保持被包裹的组件的状态，防止它们被销毁并且避免重新渲染。当 `keep-alive` 缓存一个组件时，即使它在视图中被切换掉，它也不会被销毁，并且相关的状态（例如数据、状态等）也会被保留。

但有些情况下，被 `keep-alive` 缓存的组件会被销毁：

### 1. `<keep-alive>` 的缓存限制
`<keep-alive>` 组件提供了 `max` 属性，这个属性用于定义它最多可以缓存多少个组件实例。如果缓存的组件实例数量超过了 `max` 设定的值，那么最旧的组件实例会被销毁。

### 2. 被包裹的组件不再符合 `include` 或 `exclude` 规则
`<keep-alive>` 组件提供 `include` 和 `exclude` 属性，用于定义哪些组件应该被缓存，哪些不应该。如果一个正在被缓存的组件由于某种原因（比如动态改变 `include` 或 `exclude` 的值）不再符合这些规则，那么它将会在下次渲染时被销毁。

### 3. `<keep-alive>` 自身被销毁
如果 `<keep-alive>` 组件本身被销毁（例如它可能在一个条件渲染的分支中，并且条件变为 `false`），那么它缓存的所有组件实例也将被销毁。

### 4. 手动清除缓存
如果你通过编程的方式清除了 Vue 实例的缓存（例如通过 `$destroy()` 方法或者使用 Vue 的 `vm.$cache` 对象），缓存的组件实例将会被销毁。

请注意，通常而言，`<keep-alive>` 是设计用来缓存组件的，即使它们不再可见。一般来说，除非你有很强烈的理由要销毁一个被 `<keep-alive>` 缓存的组件，否则最好让 Vue.js 管理它的生命周期，以获得最佳性能和用户体验。

