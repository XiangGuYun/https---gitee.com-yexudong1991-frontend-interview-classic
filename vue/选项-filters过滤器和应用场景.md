### Vue的过滤器 (Filters)

在 Vue.js 中，过滤器主要用于在模板中格式化文本，它常用在双花括号插值和 `v-bind` 表达式中。**过滤器不会改变原始数据，只会改变输出的视觉表现**。过滤器函数总接收表达式的值（表达式的结果）作为第一个参数。

> 在 Vue 2.x 中，过滤器的使用非常广泛，但在 Vue 3.x 中，官方推荐使用计算属性或方法替代过滤器。

##### 基本语法：
```html
<!-- 在双花括号中 -->
{{ message | capitalize }}

<!-- 在 `v-bind` 中 -->
<div v-bind:id="rawId | formatId"></div>
```

##### 定义过滤器的方式：
```javascript
// 局部过滤器
new Vue({
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
})

// 全局过滤器
Vue.filter('capitalize', function (value) {
  if (!value) return ''
  value = value.toString()
  return value.charAt(0).toUpperCase() + value.slice(1)
})
```

### 过滤器的应用场景：

1. **文本格式化：**
   - 将文本转换为大写或小写。
   - 为文本添加前缀或后缀。
   
```html
{{ userName | uppercase }}
```
   
2. **数值格式化：**
   - 格式化价格（比如添加货币符号、控制小数位数等）。
   - 格式化日期时间。
   
```html
{{ price | formatCurrency }}
```
   
3. **图片地址格式化：**
   - 将相对路径转换为绝对路径。
   - 添加特定的参数或后缀。
   
```html
<img :src="imgPath | formatImgUrl" />
```
   
4. **内容裁切：**
   - 截取文本的一部分，添加省略号等。
   
```html
{{ content | truncate(100) }}
```
   
5. **数据占位符处理：**
   - 当数据为空或未定义时，提供一个默认值或占位符。
   
```html
{{ address | default('N/A') }}
```

### 注意事项：

- 过滤器应当保持简单，不要在过滤器中执行复杂的操作或副作用。
- 如果需要在多个组件或场景复用同一逻辑，考虑使用计算属性、方法或提取到工具函数中。
- 由于在 Vue 3.x 中，过滤器已被移除，因此在新项目中推荐使用计算属性或方法来替代过滤器的功能。

在实际应用中，合理使用过滤器（或计算属性、方法）可以帮助我们减少模板中的重复代码，提高代码的可维护性。