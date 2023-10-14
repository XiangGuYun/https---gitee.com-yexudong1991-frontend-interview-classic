ECMAScript 5（ES5）和 ECMAScript 2015（通常被称为 ES6）之间有很多关键的差异和新引入的特性。ES6 带来了一系列广泛的改进和新特性，它意在使 JavaScript 成为一种更加强大和灵活的编程语言。下面是一些 ES5 和 ES6 之间的主要区别：

### 1. 变量声明
- **ES5**: 主要使用 `var` 关键字进行变量声明。
  
- **ES6**: 引入了 `let` 和 `const` 两个新的关键字用于变量声明。

### 2. 模板字符串
- **ES5**: 没有模板字符串。
  
- **ES6**: 提供模板字符串功能，允许内嵌变量和表达式。使用反撇号（`` ` ``）标识。

```javascript
let name = "World";
let greeting = `Hello, ${name}!`; // ES6
```

### 3. 默认参数和剩余参数
- **ES5**: 不直接支持默认参数和剩余参数。
  
- **ES6**: 支持默认参数和剩余参数（`...` 操作符）。

```javascript
function greet(name, greeting="Hello") { // ES6
    console.log(`${greeting}, ${name}!`);
}

function sum(...numbers) { // ES6
    return numbers.reduce((acc, num) => acc + num, 0);
}
```

### 4. 箭头函数
- **ES5**: 使用 `function` 关键字定义函数。

- **ES6**: 引入了箭头函数，提供了一个更简洁的函数语法。

```javascript
const add = (a, b) => a + b; // ES6
```

### 5. 类（Class）
- **ES5**: 使用函数和原型链创建类似类的结构。

- **ES6**: 引入了类（`class`）的概念和语法。

```javascript
class Person { // ES6
    constructor(name) {
        this.name = name;
    }
    
    greet() {
        console.log(`Hello, my name is ${this.name}.`);
    }
}
```

### 6. 解构赋值
- **ES5**: 不直接支持解构赋值。
  
- **ES6**: 支持数组和对象的解构赋值。

```javascript
let [a, b] = [1, 2]; // 数组解构 ES6
let {c, d} = {c: 3, d: 4}; // 对象解构 ES6
```

### 7. 模块导入/导出
- **ES5**: 不直接支持模块系统。
  
- **ES6**: 引入了模块系统，支持 `import` 和 `export`。

```javascript
// module.js
export const greet = (name) => `Hello, ${name}!`; // ES6

// main.js
import { greet } from './module.js'; // ES6
```

### 8. 增强的对象字面量
- **ES5**: 标准的对象字面量。
  
- **ES6**: 提供了增强的对象字面量，简化了代码写法。

```javascript
let name = "World";
let obj = {
    name,  // 属性简写
    greet() { // 方法简写
        console.log(`Hello, ${this.name}!`);
    }
}; // ES6
```

### 9. Promise
- **ES5**: 不直接支持 `Promise`。
  
- **ES6**: 引入了 `Promise` 对象用于异步编程。

### 10. 生成器和迭代器
- **ES5**: 不直接支持生成器和迭代器。
  
- **ES6**: 引入了生成器和迭代器概念及其语法。

```javascript
function* generator() { // 生成器 ES6
    yield 1;
    yield 2;
    yield 3;
}
```

### 11. Map 和 Set 数据结构
- **ES5**: 没有 Map 和 Set 数据结构。
  
- **ES6**: 引入了 Map 和 Set 数据结构。

以上列出的是 ES5 和 ES6 之间一些显著的差异和新特性。ES6 提供了很多强大的功能和语法糖，帮助开发者编写更加简洁、易读和强大的代码。在当前的前端开发中，ES6 已经得到了广泛的应用和支持。