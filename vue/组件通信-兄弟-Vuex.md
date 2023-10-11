如果项目已经引入了 Vuex 这个状态管理库，兄弟组件间的通信也可以通过共享的全局状态来实现。

首先在 Vuex store 中定义一个 state 来保存数据：

```javascript
export default new Vuex.Store({
  state: {
    dataFromA: null
  },
  mutations: {
    setDataFromA(state, data) {
      state.dataFromA = data;
    }
  }
})
```

组件 A 修改状态：

```html
<script>
export default {
  methods: {
    sendData() {
      this.$store.commit('setDataFromA', 'Some data...');
    }
  }
}
</script>
```

组件 B 读取状态：

```html
<template>
  <div>{{ dataFromA }}</div>
</template>

<script>
export default {
  computed: {
    dataFromA() {
      return this.$store.state.dataFromA;
    }
  }
}
</script>
```