在 Vue 2.x 版本中，`Vue.observable` 是一个被引入用来使对象变得可响应的方法。这个 API 在创建可响应数据的同时，可以在非组件系统的上下文（例如普通的 JavaScript 对象和类）中工作。`Vue.observable` 在 Vue 2.6.0 版本中被引入，作为 Vue 响应系统的一部分暴露出来。

这是一个基本的 `Vue.observable` 的使用例子：

```javascript
const state = Vue.observable({ count: 0 })

const demo = new Vue({
  render: h => h('button', {
    on: { click: () => { state.count++ } }
  }, `count is: ${state.count}`)
}).$mount('#demo')
```

在这个例子中，我们创建了一个可观察（observable）的 `state` 对象，然后在 Vue 组件的渲染函数中使用它。当我们点击按钮，`state.count` 的值会增加，并且组件会重新渲染，显示最新的 `count` 值。

**注意：** 在 Vue 3.x 中，这个 API 已经不再以 `Vue.observable` 的形式存在，因为 Vue 3 使用了一个全新的响应式系统。在 Vue 3 中，你可以使用 `reactive` 或 `ref` API 从 `vue` 包中导入来创建响应式数据。例如：

```javascript
import { reactive } from 'vue';

const state = reactive({ count: 0 });
```

这会提供一个类似的响应性功能，在 Vue 组件和普通 JavaScript 对象中同样可以使用。