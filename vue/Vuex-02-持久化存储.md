在 Vuex 中实现持久化存储主要有以下几种常见的方式：

### 1. **使用本地存储（LocalStorage/SessionStorage）**

你可以在 mutation 中使用 `localStorage` 或 `sessionStorage` 来存储状态的快照，以实现简单的状态持久化。

例如：

```javascript
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment(state) {
      state.count++;
      localStorage.setItem('count', state.count);
    }
  }
})
```

同时，在创建 store 的时候，你可以从本地存储中恢复状态：

```javascript
const store = new Vuex.Store({
  state: {
    count: localStorage.getItem('count') || 0
  },
  mutations: {
    increment(state) {
      state.count++;
      localStorage.setItem('count', state.count);
    }
  }
})
```

### 2. **使用 Vuex 插件**

你也可以使用 Vuex 插件来实现状态的持久化。例如，`vuex-persistedstate` 是一个非常流行的插件，用来将状态保持到本地存储。

首先，你需要安装这个插件：

```bash
npm install vuex-persistedstate
```

然后，你可以按照下面的方式使用它：

```javascript
import createPersistedState from 'vuex-persistedstate';

const store = new Vuex.Store({
  // ...
  plugins: [createPersistedState()]
});
```

在上述代码中，我们导入了 `createPersistedState` 函数，并将它添加到 store 的 `plugins` 数组中。`vuex-persistedstate` 插件将自动将状态保存到本地存储，并在页面刷新时自动恢复。

你还可以对 `createPersistedState` 进行配置，以调整它的行为。例如，你可以选择只持久化一部分状态：

```javascript
import createPersistedState from 'vuex-persistedstate';

const store = new Vuex.Store({
  // ...
  plugins: [createPersistedState({
    paths: ['count']
  })]
});
```

在上述代码中，我们使用 `paths` 选项来选择只持久化 `count` 状态。

这些方法可以根据你的具体需求选择使用，帮助你在 Vuex 中实现持久化存储。