## 示例1 - 离开表单页面提醒（beforeRouteLeave）

我们将使用 Vue Router 的 `beforeRouteLeave`导航守卫。

在用户试图离开当前组件时，显示确认对话框。这是一个非常实用的功能。

### 场景介绍

当用户在一个表单页面进行了一些输入，但是尝试在提交之前离开页面时，我们可能想要提醒用户。

```html
<!-- Component.vue -->
<template>
  <div>
    <!-- Your Component Template -->
    <h1>Are you sure you want to leave?</h1>
    <input v-model="inputData" placeholder="Type something...">
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 它是用来绑定到输入框的数据。当我们更改这个输入框的内容时，
      // 我们希望在尝试离开组件之前提醒用户。
      inputData: ''
    };
  },
  methods: {
    // 这个方法包含一个检查，用于确定是否安全地离开页面。
    // 如果 `inputData` 是空的，我们认为是安全的。
    // 否则，我们将显示一个确认对话框来警告用户可能的数据丢失。
    async confirmLeave() {
      return this.inputData === '' || 
        window.confirm('You have unsaved changes! Do you really want to leave?');
    }
  },
  // 这个守卫被调用当路由改变，且当组件被复用时（例如，对用户 id 的改变）。
  beforeRouteLeave(to, from, next) {
    // 我们使用 `confirmLeave` 方法来决定是否允许用户离开
    if (this.confirmLeave()) {
      // 调用 `next()` 允许导航。
      next();  
    } else {
      // 调用 `next(false)` 阻止导航。
      next(false); 
    }
  }
}
</script>
```

## 示例二：未登录或Token失效时重定向到登录页（beforeEach）

下面的伪代码演示了如何使用 Vue Router 的全局守卫 (`beforeEach`) 来检查用户是否登录。未登录的用户在尝试访问需要登录的页面时将被重定向到登录页面。

```javascript
// router/index.js

import Vue from 'vue';
import VueRouter from 'vue-router';

Vue.use(VueRouter);

// 在这里定义了三个示例路由，分别是 `/public`, `/private`, 和 `/login`。
const routes = [
  {
    path: '/public',
    component: PublicComponent 
  },
  {
    path: '/private',
    component: PrivateComponent, 
    // 为需要身份验证的路由添加一个自定义的元数据 `requiresAuth` 作为标记，
    // 以便在导航守卫中快速检查它。
    meta: { requiresAuth: true } 
  },
  {
    path: '/login',
    component: LoginComponent 
  }
];

const router = new VueRouter({
  routes
});

// 你需要实现这个函数来根据你的认证逻辑检查用户是否已登录。
// 这可能涉及到检查 Vuex 存储、Cookie、LocalStorage 中的令牌等。
function isAuthenticated() {
  // Implement logic here
  // E.g., Check token/cookie in storage
}

// 在这里，我们为所有的路由转换定义了逻辑：
   - 
   -
router.beforeEach((to, from, next) => {
  if (to.matched.some(record => record.meta.requiresAuth)) {
    if (!isAuthenticated()) {
      // 如果目标路由（或其嵌套路径）需要身份验证（`requiresAuth: true`）且用户未认证（`!isAuthenticated()`），
      // 我们通过 `next({ path: '/login' })` 跳转到登录页面。
      next({ path: '/login' });
    } else {
      // 如果用户已认证，我们调用 `next()` 允许访问。
      next();
    }
  } else {
    // 如果目标路由不要求认证，我们也直接允许访问。
    next();
  }
});

export default router;
```
### 实现步骤总结：

1. **定义路由**：创建路由配置，包含公开和受保护的路由，并在需要认证的路由上通过`meta`属性标记。

2. **检查认证**：实现`isAuthenticated`函数，根据实际业务判断用户是否已登录。

3. **使用守卫**：在`router.beforeEach`导航守卫中，判断目标路由是否需要认证。

4. **处理未登录**：如果目标路由需要认证且用户未认证，重定向到登录页面。

5. **允许访问**：如果不需认证或用户已认证，允许路由导航。