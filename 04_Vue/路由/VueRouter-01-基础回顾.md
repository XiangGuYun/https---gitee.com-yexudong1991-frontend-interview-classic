**Vue Router** 是 Vue.js 官方的路由管理器。它和 Vue.js 核心深度集成，让构建单页面应用（Single Page Applications，简称 SPA）变得易如反掌。包含的功能有嵌套的路由/视图表，模块化的、基于组件的路由配置，路由参数、查询、通配符，视图过渡效果等。

在单页面应用中，大多数资源（HTML/CSS/JS）都是在 App 的初始化时一次性加载。而在具体的视图间切换时，并不会重新请求资源，而是通过改变 URL 中的 hash 或使用 HTML5 History API 来更新视图，所有的页面切换、数据交换、动作行为都在客户端进行。

### 主要概念：

#### 1. **路由配置**
定义一些路由配置，每个路由应该映射到一个组件。在 Vue Router 中我们通过一个 routes 的配置数组来实现这个映射：

```javascript
import Vue from 'vue';
import Router from 'vue-router';
import Home from '@/components/Home';
import About from '@/components/About';

Vue.use(Router);

export default new Router({
  routes: [
    { path: '/home', component: Home },
    { path: '/about', component: About }
  ]
});
```

#### 2. **router-view**
在 App 组件中定义一个 `<router-view>`，它会根据当前的路径动态的渲染不同的 component：

```html
<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>
```

#### 3. **router-link**
使用 `<router-link>` 组件来导航：

```html
<router-link to="/home">Home</router-link>
<router-link to="/about">About</router-link>
```

#### 4. **动态路由**
可以通过动态路径参数来捕获值，动态路径参数以冒号":"标记：

```javascript
routes: [
  { path: '/user/:id', component: User }
]
```

然后在对应的组件中，可以使用 `$route.params.id` 来获取这个动态路径参数。

#### 5. **嵌套路由**
可以创建嵌套的路由配置，将子路由配置到父路由的 children 属性中：

```javascript
const router = new VueRouter({
  routes: [
    {
      path: '/user/:id',
      component: User,
      children: [
        {
          path: 'profile',
          component: UserProfile
        },
        {
          path: 'posts',
          component: UserPosts
        }
      ]
    }
  ]
})
```

#### 6. **导航守卫**
Vue Router 提供了导航守卫来保护路由或路由变更（例如，确认用户是否真的要离开当前页面、是否已登录等）：

- 全局守卫： `router.beforeEach`
- 组件内的守卫： `beforeRouteEnter`, `beforeRouteUpdate`, `beforeRouteLeave`
- 路由独享的守卫： `beforeEnter`
- 全局解析守卫： `router.beforeResolve`

Vue Router 在单页应用（SPA）开发中能够管理视图与数据分离，对前端路由进行灵活管理，帮助开发者实现多视图切换。