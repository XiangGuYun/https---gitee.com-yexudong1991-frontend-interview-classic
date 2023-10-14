JavaScript 存储数据主要通过变量、数据结构和存储API来实现。下面我们详细探讨这几方面：

### 1. 变量和常量

- **基本数据类型**：存储简单数据，例如 `string`、`number`、`boolean`、`null`、`undefined` 和 `symbol`。
- **复杂数据类型**：例如对象（`object`）和数组（`array`），它们能存储多个数据项或键值对。

```javascript
let name = 'Alice';
const pi = 3.14159;
let person = { firstName: 'John', lastName: 'Doe' };
let numbers = [1, 2, 3, 4, 5];
```

### 2. 数据结构

- **数组（Arrays）**：有序的数据集合。
- **对象（Objects）**：键值对的无序集合。
- **Map 和 Set**：ES6 中新增的数据结构。
- **堆栈和队列**：可以用数组实现的先进后出（stack）和先进先出（queue）的数据结构。

```javascript
let students = ['Bob', 'Alice', 'Charlie'];
let car = { make: 'Toyota', model: 'Corolla' };
let map = new Map();
let set = new Set();
```

### 3. 存储 API

- **localStorage**：提供一个简单的键值对的存储，数据是持久的，并且只能被同源的页面访问。
- **sessionStorage**：与 localStorage 类似，但数据只在当前会话（session）期间有效。
- **IndexedDB**：一个低级的 API 用于存储大量结构化数据（包括，文件/ blobs）。

```javascript
localStorage.setItem('key', 'value');
sessionStorage.setItem('key', 'value');
```

### 4. Cookies

- 用于存储少量数据，这些数据会在服务器和客户端之间自动传递。
  
```javascript
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2023 12:00:00 UTC; path=/";
```

### 5. Web Storage API

- **Cache API**：允许缓存网络资源，提供快速的读取。

### 6. 全局变量和作用域

- **全局变量**：在整个应用中可访问的变量。
- **局部变量**：只在特定代码块或函数中可访问的变量。

```javascript
var globalVar = 'I am global!';
function exampleFunction() {
    let localVar = 'I am local!';
}
```

这些存储数据的方法提供了不同的用途和限制。选择哪一种方法通常取决于你的特定需求：例如，数据的大小、生命周期、是否需要在客户端和服务器之间传输等。