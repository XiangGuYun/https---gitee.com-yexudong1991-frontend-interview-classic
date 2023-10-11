# Vue.mixin

**Vue.mixin** 是一个全局方法，允许你为 **Vue** 的每个实例注入可复用的功能，但需谨慎使用，以避免不必要的冲突。

### 使用场景

1. **全局注册公共方法或属性**：`Vue.mixin` 可以用来全局注册在多个组件中重复使用的选项，例如生命周期钩子、methods、computed 等。

```javascript
Vue.mixin({
  created() {
    console.log('Global mixin created!');
  },
  methods: {
    greet() {
      alert('Hello from mixin!');
    }
  }
});
```

2. **插件开发**：`Vue.mixin` 在开发插件时非常有用，插件可以用全局混入的方式添加一些自定义功能。

```javascript
Vue.mixin({
  methods: {
    customPluginMethod() {
      // ...some code
    }
  }
});
```

3. **实现某些特性**：例如，在全局混入一个 `watch`，用于检测用户的网络状态变化。

```javascript
Vue.mixin({
  data() {
    return {
      isOnline: navigator.onLine
    };
  },
  created() {
    window.addEventListener('online', this.updateOnlineStatus);
    window.addEventListener('offline', this.updateOnlineStatus);
  },
  destroyed() {
    window.removeEventListener('online', this.updateOnlineStatus);
    window.removeEventListener('offline', this.updateOnlineStatus);
  },
  methods: {
    updateOnlineStatus() {
      this.isOnline = navigator.onLine;
    }
  }
});
```

### 注意事项
- **冲突处理**：混入对象的钩子将在组件自身钩子之前调用。如果出现命名冲突，则组件的选项将优先使用。
- **全局影响**：使用全局混入 (`Vue.mixin()`) 时需谨慎，因为它会影响到每个单独创建的 Vue 实例（包括第三方组件）。

### 原理

1. **选项合并**：当组件和混入对象含有重叠的选项时，这些选项将以合适的方式混合。比如，数据对象在内部进行递归合并，并在发生冲突时以组件数据优先。

2. **生命周期钩子合并**：当混入和组件对象都声明了生命周期钩子方法时，它们将被合并为一个数组，因此两个生命周期钩子都将被调用。

   ```javascript
   // 输出结果：'mixin hook called' 和 'component hook called'
   Vue.mixin({
     created: function () {
       console.log('mixin hook called')
     }
   })
   new Vue({
     created: function () {
       console.log('component hook called')
     }
   })
   ```

3. **值为对象的选项**：例如 `methods`, `components` 和 `directives`，将被合并为同一个对象。两个对象键名冲突时，取组件对象的键值对。

4. **响应式机制**：混入的数据对象将遵循 Vue 的响应式机制，当数据变化时，所有使用这些数据的组件都将更新。

在 Vue 的组件系统中，`mixin` 是一种分发 Vue 组件中可复用功能的非常灵活的方式。希望这些信息对你有所帮助！

***

## 《巧克力工厂：Vue.mixin 的秘密配方》🍫

想象一下，你正在运营一个巧克力工厂。你有各种各样的巧克力产品，它们都需要添加可可和糖。在这种情况下，你可能会把可可和糖视为“基础配方”，而每种巧克力产品——无论是黑巧克力、牛奶巧克力还是榛果巧克力——在生产过程中都会使用这个基础配方。

```javascript
var ChocoFactory = new Vue({
  created: function () {
    this.addCocoa()
    this.addSugar()
  },
  methods: {
    addCocoa: function () { /* ... */ },
    addSugar: function () { /* ... */ }
  }
})
```

这就像 Vue 中的 `mixin`。Mixin 是一种分发 Vue 组件中可复用功能的灵活方式。如果你的应用程序中有几个组件需要共享同样的方法，那么就可以使用 mixin。

*在这个比喻中，"基础配方"（即可可和糖）就像是 Vue 中的 `mixin`。我们可以创建一个包含 `addCocoa` 和 `addSugar` 方法的 mixin，并将其添加到所有需要这些方法的 Vue 组件中。*

接下来，让我们制作一些巧克力产品。比如，我们现在要做牛奶巧克力。我们需要在基础配方的基础上添加牛奶。

```javascript
var MilkChoco = new Vue({
  mixins: [ChocoFactory],
  created: function () {
    this.addMilk()
  },
  methods: {
    addMilk: function () { /* ... */ }
  }
})
```

同样，如果我们要制作榛果巧克力，我们只需在基础配方的基础上添加榛果。

```javascript
var HazelnutChoco = new Vue({
  mixins: [ChocoFactory],
  created: function () {
    this.addHazelnuts()
  },
  methods: {
    addHazelnuts: function () { /* ... */ }
  }
})
```

*在这个比喻中，“添加牛奶”和“添加榛果”的步骤代表了各自的 Vue 组件特有的功能。尽管它们都使用了相同的 mixin（即“基础配方”），但它们也可以根据需要添加额外的方法。*

所以，你看，Vue 的 `mixin` 就像是巧克力工厂的秘密配方一样，让我们能够轻松地制作各种美味的巧克力产品！🍫✨