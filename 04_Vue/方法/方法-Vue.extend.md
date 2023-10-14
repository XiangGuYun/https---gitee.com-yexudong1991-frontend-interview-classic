# Vue.extend

`Vue.extend` 是 Vue 构造函数的一个类方法，用来“扩展” Vue 构造器，从而创建出一个自定义的“子类”。你可以通过传递一个选项对象来定制这个子类。最常用的它的场景之一就是在创建可复用的组件时。

`Vue.extend` 创建的“子类”通常用于创建可复用的组件。这个“子类”本质上就是一个包含了一堆预设选项的 Vue 实例的构造函数。

### 基础的用法示例

```javascript
// 创建一个 Vue.extend “子类”
const MyComponent = Vue.extend({
  template: '<div>Hello, {{name}}!</div>',
  data() {
    return {
      name: 'World'
    }
  }
});

// 创建 MyComponent 的实例，并挂载到一个元素上。
new MyComponent().$mount('#my-component');
```

在上面的代码中：

- 使用 `Vue.extend` 创建一个“子类”或“子组件”（`MyComponent`）。
- 这个子组件有自己的模板和数据。
- 使用 `new MyComponent().$mount('#my-component')` 来实例化并挂载这个子组件。

### 使用`Vue.component`

通常我们不会直接这样用 `Vue.extend`，而是在 `Vue.component` 中用它，以定义一个全局的组件。

```javascript
// 定义一个名为 'my-component' 的新组件
Vue.component('my-component', {
  template: '<div>Hello, {{name}}!</div>',
  data() {
    return {
      name: 'World'
    }
  }
});
```

在这个场景下，`Vue.component` 内部使用 `Vue.extend` 来创建一个新的“子类”，然后这个“子类”就变成了我们定义的新组件。

这样我们就可以在一个 Vue 实例的模板中多次使用这个组件，只要使用它的标签名（在这个例子中是 `my-component`）即可。

```html
<div id="app">
  <my-component></my-component>
</div>
```
```javascript
new Vue({ el: '#app' });
```

无论是通过直接使用 `Vue.extend` 还是通过 `Vue.component` 使用，这个方法提供了一种封装和重用代码的有效方式，特别是在创建 UI 组件时。

***
## 魔法书与召唤术 📜✨
<div align=center><img src="img/20231011160900.png" width="60%"></div>

想象你是一个魔法师，手中有一本魔法书。书中的每一页都是一个特殊的魔法。有一天，你决定创建一个全新的魔法，这个魔法是基于书中某一页的魔法，但你加入了自己的特殊元素使其更加强大。

这个过程就像使用`Vue.extend`，你基于一个现有的Vue构造器，扩展出一个新的构造器。

```javascript
// 基于现有的魔法（Vue构造器）创建新的魔法
const NewSpell = Vue.extend({
  template: '<div>I am a new spell!</div>'
});
```

但是，为了频繁地召唤这个新魔法，你需要一个简单的召唤术。所以，你给这个魔法取了个名字，并把它放入你的快速召唤列表中。

这个快速召唤过程就像使用`Vue.component`，你将这个扩展后的构造器注册为一个全局可用的组件。

```javascript
// 把新魔法加入快速召唤列表（全局组件）
Vue.component('new-spell', NewSpell);
```

*在这个比喻中，`Vue.extend`就像是基于魔法书中的魔法创造新的魔法，而`Vue.component`则是为这个新魔法创建一个简单的召唤术，使其可以被快速使用。* 🧙‍♂️🔮