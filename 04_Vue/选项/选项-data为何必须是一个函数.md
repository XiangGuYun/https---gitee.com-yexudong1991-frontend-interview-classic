在 Vue 组件中，`data` 必须是一个函数，这个函数返回一个对象，对象里面的属性就是这个组件的状态（data）。这个设计选择是出于**组件复用**的考虑。

让我们先看一下如果 `data` 是一个对象会发生什么：

```javascript
const MyComponent = {
  data: {
    count: 0
  },
  template: '<button @click="count++">{{ count }}</button>'
};
```

假设我们在多个地方使用这个组件：

```html
<my-component></my-component>
<my-component></my-component>
```

由于 JavaScript 中对象是按引用传递的，这意味着如果 `data` 是一个对象，那么所有的组件实例将共享相同的数据对象。那样的话，改变其中一个组件的状态会影响到所有其他的使用这个组件的地方，这并不是我们想要的。

为了解决这个问题，Vue 要求每个组件实例有一个独立的、隔离的数据拷贝。这样，每个组件实例都可以维护一份独立的数据副本。这就是为什么我们需要提供一个函数作为 `data` 的值：

```javascript
const MyComponent = {
  data() {
    return {
      count: 0
    }
  },
  template: '<button @click="count++">{{ count }}</button>'
};
```

每次创建一个新的组件实例（也就是每次使用 `<my-component></my-component>`），`data` 函数就会被调用，返回一个全新的数据对象副本。由于函数提供了一个新的作用域，这个数据对象不会与其他实例共享，每个实例都是独立的，互不影响。