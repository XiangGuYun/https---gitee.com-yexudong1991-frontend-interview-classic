# 父子组件的生命周期顺序

在Vue框架中，父子组件的生命周期的执行顺序如下：

> 只需要记住子组件的挂载和销毁是优先的,其它都靠后.

1. **加载渲染过程**:
    - 父组件 `beforeCreate`
    - 父组件 `created`
    - 父组件 `beforeMount`
    - 子组件 `beforeCreate`
    - 子组件 `created`
    - 子组件 `beforeMount`
    - 子组件 `mounted`
    - 父组件 `mounted`

2. **子组件更新过程**:
    - 父组件 `beforeUpdate`
    - 子组件 `beforeUpdate`
    - 子组件 `updated`
    - 父组件 `updated`

3. **父组件更新过程**:
    - 父组件 `beforeUpdate`
    - 父组件 `updated`

4. **销毁过程**:
    - 父组件 `beforeDestroy`
    - 子组件 `beforeDestroy`
    - 子组件 `destroyed`
    - 父组件 `destroyed`

这种执行顺序确保了父组件的初始化或销毁不会被子组件的行为所影响，而子组件的加载和更新完全嵌套在父组件的生命周期中。