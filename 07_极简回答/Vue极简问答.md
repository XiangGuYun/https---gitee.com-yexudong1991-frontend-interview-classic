# 极简问答

### Pinia是什么

Pinia是一个基于Vue 3的状态管理库，用于管理全局状态和在应用程序中进行状态共享。

### Vite是什么

Vite，法文“快”的意思，由尤雨溪创建，致力于提供一个轻量且快速的前端构建解决方案，利用 ES Module 提升冷启动效率。

### Vue2的生命周期

创（beforeCreate, created）、载（beforeMount, mounted）、新（beforeUpdate, updated）、灭（beforeDestroy, destroyed）。

### Vue3的生命周期

Vue 3的生命周期包括：创建、挂载、更新和销毁，每个阶段都有对应的钩子函数用于执行相关操作。

> 注意名称前面需要加on。

### Vue3-模板编译优化

Vue 3中的模板编译优化通过静态分析和编译器优化，提供更快的渲染性能和更小的包体积。


## VueRouter

### 是什么

VueRouter，Vue.js官方的路由管理器，它能够用于构建单页面应用，轻松映射URL到组件。

### 两种路由模式

VueRouter提供hash模式用URL哈希值管理路由，及history模式利用HTML5 History API实现无#路径。

### 导航守卫

VueRouter提供导航守卫，如`beforeEach`、`beforeResolve`、`afterEach`，实现路由跳转前后逻辑控制。

### 导航故障

VueRouter导航故障指路由导航过程中因某些原因无法成功达到目标位置，例如重定向、钩子函数或解析异步组件出错。

### Vuex是什么

Vuex是Vue.js的状态管理库，用于集中管理Vue应用中的状态数据，实现组件之间的通信和数据共享。

### Vuex持久化

Vuex可以通过插件如`vuex-persistedstate`来持久化存储状态到本地存储（如LocalStorage）或Cookie，确保数据在刷新页面后仍然可用。

### Vuex监听数据变化

要监听Vuex的数据变化，可以使用`$watch`或`mapState`方法，也可以订阅Vuex的`store.subscribe`方法，或使用Vue组件中的`computed`属性。

### mutaion和action的区别

Mutation用于同步更改Vuex状态，Action用于异步操作或包含业务逻辑的操作，然后提交Mutation来更改状态。

### Webpack是什么

Webpack是一个模块打包工具，用于将多个前端资源（如JavaScript、CSS、图片）打包成一个或多个文件，以提高性能和开发效率。

### Webpack dev server是什么

webpack-dev-server是一个用于开发环境的小型Node.js Express服务器，用于提供实时重新加载和开发时的热模块替换（HMR）。

### Webpack如何处理样式

Webpack处理样式通过加载各种loader，如style-loader和css-loader，将样式文件转换为JavaScript对象，以便在应用中使用。

### .lazy

.lazy修饰符用于Vue.js的v-model指令，将输入事件改为失去焦点后才触发数据绑定，提高性能。

### .self

修饰符.self用于Vue.js的事件绑定指令，要求事件只有在事件源元素本身触发时才执行，忽略子元素触发。

### .stop

修饰符.stop用于Vue.js的事件绑定指令，用于停止事件冒泡传播，阻止事件继续向上传播到父元素。

### .sync

修饰符.sync用于Vue.js的组件通信，允许子组件修改父组件中的数据，以保持数据的双向绑定。

### .capture

修饰符.capture用于Vue.js的事件绑定指令，用于添加事件监听器时将事件捕获阶段替代冒泡阶段。

### diff算法

Diff算法是用于比较两个数据结构之间的不同之处，通常在前端框架中用于高效更新虚拟DOM或UI。

### New Vue做了什么

new Vue()实例化Vue→初始化数据和组件→编译模板→挂载DOM→建立响应式数据绑定→监听事件→启动Vue应用。

### template转render函数

template转render函数：模板解析→生成虚拟DOM→createElement函数调用→创建真实DOM→渲染页面。

### Vue如何做依赖收集

依赖收集：模板解析→getter触发数据访问→Dep对象记录依赖→setter触发数据变化→Dep通知更新→更新视图。

### Vue如何检测数组变化

Vue使用"Object.defineProperty"或"Proxy"来拦截数组操作，如push、pop等，以便捕获和响应数组的变化，并触发视图更新。

### 虚拟DOM

虚拟DOM是JavaScript对象表示的内存中的虚拟树，用于高效地更新真实DOM，以减少页面重绘和提高性能。

### v-for和v-if的优先级

v-for的优先级更高，会在v-if之前处理，即v-for会遍历所有项，而v-if会根据条件进行筛选。

### v-show和v-if区别

v-show在条件为false时会将元素保留在DOM中，只是隐藏，而v-if会根据条件渲染或销毁元素。

### 自定义指令的应用场景

自定义指令适用于需要DOM操作和事件监听的场景，如自定义输入框格式、自定义滚动行为、权限控制等。

### keep-alive组件

keep-alive组件用于保留缓存的组件状态，以提高页面切换性能，适用于tab切换、路由缓存等场景。

### 函数式组件

函数式组件是无状态的，用函数代替对象，通常用于纯展示性UI，性能高，不支持实例方法和生命周期。

### 动态组件

动态组件是根据条件或数据选择渲染的组件，用于构建灵活的页面，允许在不同组件之间切换或嵌套。

### 异步组件

异步组件是按需加载的Vue组件，通过import()或require.ensure()实现，提高应用程序性能。

### 递归组件

递归组件是自身调用的组件，用于处理具有嵌套结构的相似数据，如评论回复。

### EventBus

使用EventBus，在Vue应用中创建一个中央事件总线，通过$emit和$on方法实现组件之间的通信，触发和监听自定义事件。

### Vux

使用Vuex，组件可以通过提交(mutations)或分发(actions)来修改或获取共享的状态，从而实现组件间的通信和数据共享。

### 共同父组件通信

兄弟组件可以通过共同父组件作为中介，将数据通过props或事件传递给父组件，再由父组件分发给另一个兄弟组件。

### provide&inject和Props&Events异同点

provide&inject：祖先组件提供数据，后代组件注入，用于高级（跨级）组件通信。

Props&Events：父组件传递数据给子组件，子组件通过触发事件通知父组件。常用于父子组件通信。

### Vue3和Vue2的区别

1.性能：Vue3更快，有更高效的虚拟DOM算法和Tree-Shaking支持。
2.组件：Vue3引入Composition API，提供更灵活的组件组织方式。
3.响应性：Vue3的响应性系统重构，更可靠。
4.模板：Vue3的模板支持了多个根元素。
5.编译：Vue3编译器更快，支持片段和静态提升。
6.容器：Vue3支持多个根组件实例。
7.插件：Vue3插件系统改进。
8.型检查：Vue3支持TypeScript更好。
9.自定义渲染：Vue3支持自定义渲染器。
10.生命周期：Vue3的生命周期钩子改变。

### 你对Vue组件化的理解

Vue组件化是一种前端开发方法，将UI和功能划分成独立可复用的组件，提高代码组织性、维护性和可测试性。

### 谈谈你对SPA的理解

SPA（单页应用）是一种网页应用程序的架构模式，通过在单个页面中动态加载内容，实现流畅的用户体验和无需刷新整个页面的交互效果。

### 谈谈你对响应式数据的理解

响应式数据是指那些能够自动检测变化并根据变化更新UI界面的数据，常见于现代前端框架如Vue或React中。

### data为什么必须是一个函数

Vue的`data`必须是一个函数，以便每个组件实例都有独立的数据副本，避免不同实例间的数据相互影响和干扰。

### 过滤器和应用场景

Vue的过滤器用于对插值表达式和v-bind表达式的输出进行预处理，常见应用场景包括格式化日期、货币或文本等。

### methods和computed的区别

`methods` 是用于定义在 Vue 实例中可调用的方法，而 `computed` 是用于定义基于响应式数据计算的属性。