## 导航故障

指导航过程中的失败或错误，如在 Vue Router 中由导航守卫阻止，或尝试访问不存在的路由引发的问题。

> 在 Vue.js 的上下文中（特别是与 Vue Router 一起使用时），"导航故障"（Navigation Failure）指的是**在导航过程中出现的错误或者未能成功完成的导航**。这种情况通常涉及到某种形式的导航守卫逻辑阻止了路由的变更，或者在尝试访问的路由不存在的情况下尝试导航到一个新的路由。

### 处理

Vue Router 提供了一种方式来识别和处理这些导航故障。在 Vue Router 3.x+ 的版本中，可以使用 `router.push` 或 `router.replace` 的 `Promise` 来捕获导航故障。

### 示例

一个常见的导航故障的示例是当使用 `next(false)` 在导航守卫中阻止导航时：

```javascript
router.beforeEach((to, from, next) => {
  if (/* some condition */) {
    next(false); // prevents navigation
  } else {


    next();
  }
});
```

或者当尝试导航到一个不存在的路由时：

```javascript
router.push("/non-existent-route").catch((failure) => {
  if (failure.name === 'NavigationDuplicated') {
    // Ignore navigation to current location
  } else {
    // Handle other navigation failures
  }
});
```

在这个例子中，我们尝试导航到一个不存在的路由，并使用 `.catch` 捕获导航故障。可以在这个 `.catch` 块中处理故障，例如回退到一个备用页面或者显示一个错误消息给用户。

总的来说，了解和恰当处理导航故障是构建一个健壮和用户友好的 Vue SPA（单页应用程序）的关键部分。