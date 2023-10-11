`VueRouter` 提供了多种导航守卫（也称为路由钩子），允许我们在路由进行各种阶段时执行逻辑。主要可以分为全局的、单个路由独享的以及组件内的钩子函数。

### 1. 全局守卫

- **beforeEach**: 这个钩子函数在导航触发时先全局调用。在导航被确认之前，整个导航在所有守卫 resolve 完之前一直暂停。

  ```javascript
  router.beforeEach((to, from, next) => {
    // ...
  })
  ```
  
- **beforeResolve**: 在 beforeRouteEnter 和 beforeRouteUpdate (新) 守卫解析完之后，在导航被确认的时候调用。

  ```javascript
  router.beforeResolve((to, from, next) => {
    // ...
  })
  ```
  
- **afterEach**: 这个钩子没有 next 函数，并且不会改变导航本身。

  ```javascript
  router.afterEach((to, from) => {
    // ...
  })
  ```
  
### 2. 路由独享守卫

- **beforeEnter**: 这些守卫不会被任何版本的 `beforeResolve` 守卫调用。

  ```javascript
  {
    path: '/foo',
    component: Foo,
    beforeEnter: (to, from, next) => {
      // ...
    }
  }
  ```
  
### 3. 组件内的守卫

- **beforeRouteEnter**: 在渲染该组件的对应路由被 confirm 前调用。

  ```javascript
  export default {
    beforeRouteEnter (to, from, next) {
      // ...
    }
  }
  ```
  
- **beforeRouteUpdate** (2.2 新增): 在当前路由改变，但是该组件被复用时调用。

  ```javascript
  export default {
    beforeRouteUpdate (to, from, next) {
      // ...
    }
  }
  ```
  
- **beforeRouteLeave**: 在当前路由从当前页面导航离开时被调用。

  ```javascript
  export default {
    beforeRouteLeave (to, from, next) {
      // ...
    }
  }
  ```

### 注意事项：

- **`next` 函数**: 在所有守卫中，`next` 函数用来确认或中断当前的导航。`next(false)` 中断当前导航；`next('/')` 或 `next({ path: '/' })` 重定向到其他地址；`next()` 则确认当前导航。

这些钩子函数为我们提供了在路由导航过程中执行代码的能力，允许我们实现例如验证、懒加载数据、路由转向等功能。在实际项目中根据需求选择合适的钩子来实现特定的功能。