# EventBus

```html
import Vue from 'vue';

// 创建一个事件总线
export const EventBus = new Vue();
```

在组件 A 中：

```html
<script>
import { EventBus } from './event-bus.js';

export default {
  methods: {
    sendData() {
      EventBus.$emit('dataFromA', 'Some data...');
    }
  }
}
</script>
```

在组件 B 中：

```html
<script>
import { EventBus } from './event-bus.js';

export default {
  created() {
    EventBus.$on('dataFromA', (data) => {
      console.log(data);
    });
  }
}
</script>
```

## EventBus在Vue3中是否已被弃用

在 Vue 3 中，事件总线 (`EventBus`) 这一概念并没有被弃用，但由于 Vue 3 的 Composition API 引入了许多新的概念和方法来组织代码和管理状态，通常我们有更加灵活的方式来实现跨组件通信，而不必依赖一个全局的事件总线。

Vue 3 中可以使用一个简单的 `emitter` 函数创建一个自定义的事件总线。在 Vue 3 中，我们可以使用 `createApp` 创建一个新的应用实例，并将事件总线挂载到这个实例上，使它在整个应用中都可用。下面是一个简单的示例：

### 创建 EventBus

```javascript
import { createApp, reactive, readonly } from "vue";

// 定义状态
const state = reactive({
  // your state here
});

// 创建事件总线
const bus = createApp({
  methods: {
    emit(event, ...args) {
      this.$emit(event, ...args);
    },
    on(event, callback) {
      this.$on(event, callback);
    },
    off(event, callback) {
      this.$off(event, callback);
    },
  },
});

// 导出API
export const useEventBus = () => {
  return {
    state: readonly(state),
    emit: bus.emit,
    on: bus.on,
    off: bus.off,
  };
};
```

### 使用 EventBus

在组件中使用 `emit` 和 `on` 来发送和监听事件：

```html
<template>
  <!-- your template -->
</template>

<script>
import { useEventBus } from '@/path-to-your-event-bus';

export default {
  setup() {
    const { emit, on, off } = useEventBus();
    
    // 发送事件
    emit('my-event', 'Hello, World!');
    
    // 监听事件
    on('my-event', handleMyEvent);
    
    // 生命周期钩子
    onBeforeUnmount(() => {
      // 移除事件监听
      off('my-event', handleMyEvent);
    });

    return {};
  },
  methods: {
    handleMyEvent(payload) {
      console.log(payload); // Hello, World!
    }
  }
}
</script>
```

在 Vue 3 中使用事件总线的时候，要注意移除不再需要的事件监听，防止内存泄漏。

Vue 3 提供了强大的组合 API，对于跨组件状态管理，也可以使用 `provide` 和 `inject` 方法或者使用全局状态管理库（如 Vuex）等多种方式，可以根据项目的实际需求来选择最合适的方法。
