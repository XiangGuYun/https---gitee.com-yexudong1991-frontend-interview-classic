JavaScript 提供了多种数据结构来处理不同类型的数据和不同种类的数据处理需求。以下是一些在 JavaScript 中常用的数据结构：

### 1. 数组（Array）
数组是一个用于存储数据的线性结构。数组中的元素可以通过索引来访问和修改。

```javascript
let fruits = ['apple', 'banana', 'orange'];
```

### 2. 对象（Object）
对象是一种包含键-值对（key-value pair）的数据结构。对象可以存储多种类型的数据（包括其他对象）。

```javascript
let person = {
    name: 'John',
    age: 30,
    address: {
        city: 'New York',
        zip: '10001'
    }
};
```

### 3. Set
Set 是一种包含不重复元素的数据结构。Set 也是一种线性数据结构，你可以遍历其元素的顺序。

```javascript
let uniqueNumbers = new Set([1, 2, 3, 4, 4]);
```

### 4. Map
Map 是一种包含键值对的数据结构，与 Object 类似，但 Map 的键可以是任意类型的。

```javascript
let user = new Map();
user.set('name', 'John');
user.set('age', 30);
```

### 5. Stack
虽然 JavaScript 没有内置的栈类型，但可以使用 Array 来实现栈的所有功能（比如，使用 `push` 和 `pop` 方法）。

```javascript
let stack = [];
stack.push(1);
stack.push(2);
stack.pop(); // Removes 2
```

### 6. 队列（Queue）
与栈类似，JavaScript 没有内置的队列类型，但可以使用 Array 来实现队列的功能（例如，使用 `push` 和 `shift` 方法）。

```javascript
let queue = [];
queue.push(1);
queue.push(2);
queue.shift(); // Removes 1
```

### 7. 链表（Linked List）
JavaScript 没有内置的链表数据结构，但你可以使用对象和/或类来实现链表。

```javascript
class Node {
    constructor(data, next = null) {
        this.data = data;
        this.next = next;
    }
}
let node1 = new Node(1);
let node2 = new Node(2);
node1.next = node2;
```

### 8. 树（Tree）和图（Graph）
JavaScript 没有内置的树或图数据结构，但你可以使用对象和数组的组合或类来实现这些复杂数据结构。

```javascript
class TreeNode {
    constructor(data) {
        this.data = data;
        this.children = [];
    }
}
```

以上就是在 JavaScript 中常用的一些数据结构。在实际应用中，你可能需要根据特定的场景或问题选择使用适当的数据结构。