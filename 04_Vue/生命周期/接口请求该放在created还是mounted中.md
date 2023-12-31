## 在Vue2中，刚进页面请求数据时，请求方法应该放在created还是mounted中?

在 Vue.js 2.x 中，你可以在 `created` 或 `mounted` 生命周期钩子中发起数据请求，具体选择哪个阶段取决于你的需求：

### 1. `created` 生命周期钩子
- **何时触发**：在组件实例创建之后触发，此时数据观测 (`data` 属性) 和事件配置已经完成，但 `$el` 还不可用，也就是说模板和虚拟 DOM 还未挂载或渲染。
  
- **使用场景**：通常在此阶段进行初步的数据请求或操作，因为这个阶段允许你更早地获取数据，并在数据到达时即可进行渲染，这通常会使得用户感觉页面加载更快。

  ```javascript
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      // 发起你的数据请求
    }
  }
  ```

### 2. `mounted` 生命周期钩子
- **何时触发**：在组件模板挂载完成之后触发。在这个阶段，你可以进行一些涉及到 DOM 的操作，因为在 `mounted` 阶段虚拟 DOM 已经被挂载到真实 DOM 上。

- **使用场景**：如果你的数据请求和 DOM 有关或者依赖于 DOM 元素（例如需要获取元素的大小或位置等），通常在这个阶段进行数据请求或操作更加合适。

  ```javascript
  mounted() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      // 发起你的数据请求
    }
  }
  ```

### 结论：
- 如果你的数据请求不依赖于 DOM 元素，并且你想尽早获取数据，那么放在 `created` 钩子中是一个不错的选择。
- 如果数据请求依赖于 DOM （例如需要首先计算元素的位置或大小），或者你需要在页面渲染完成后再发起请求，那么应该放在 `mounted` 钩子中。

选择合适的生命周期钩子可以确保你的应用有更好的性能和用户体验。希望这些信息对你有帮助！