## 构造函数和普通函数的区别

在 JavaScript 中，每一个函数都有 `prototype` 属性（箭头函数除外，它没有自己的 `prototype` 属性），这包括普通函数和构造函数。但是，它们的用途和用法有所不同，下面来详细探讨一下这两者的区别。

### 普通函数：
- **用途：** 通常用于执行特定的任务，并且可能会返回一个值。
- **`prototype` 属性的使用场景：** 在普通函数中，我们较少使用到它的 `prototype` 属性，除非我们要让一个普通函数充当构造函数的角色。

### 构造函数：
- **用途：** 用于创建对象，并初始化对象的状态。
- **`prototype` 属性的使用场景：** 构造函数的 `prototype` 属性特别重要，因为通过它我们可以实现对象的原型链继承。所有通过构造函数创建的实例对象共享同一个原型对象，即 `构造函数.prototype`。这样，通过原型链，一个实例对象可以访问原型对象上的属性和方法。

#### 对比：

1. **调用方式的区别：**
   - 构造函数通常使用 `new` 关键字来调用。
   - 普通函数直接调用。
   
2. **返回值的区别：**
   - 构造函数在被调用时会自动返回一个新的对象实例。
   - 普通函数默认返回 `undefined`，除非在函数体内指定返回值。

3. **创建对象实例：**
   - 构造函数通常用来创建新的对象实例。
   - 普通函数通常不用来创建对象实例。

4. **`this` 关键字的使用场景：**
   - 在构造函数中，`this` 指向新创建的对象实例。
   - 在普通函数中，`this` 的指向取决于函数调用的上下文，它可能指向全局对象、某个对象或其他上下文。

5. **`prototype` 属性的实际应用：**
   - 在构造函数中，`prototype` 属性通常被用来为创建的对象实例添加共享的属性和方法。
   - 在普通函数中，`prototype` 属性很少被实际用到。

### 举例：
```javascript
// 构造函数
function Car(make, model) {
    this.make = make;
    this.model = model;
}
Car.prototype.start = function() {
    console.log(this.make + ' ' + this.model + ' started!');
};

// 使用构造函数创建新的对象实例
var myCar = new Car('Toyota', 'Corolla');
myCar.start();  // Output: Toyota Corolla started!

// 普通函数
function add(a, b) {
    return a + b;
}
console.log(add(1, 2));  // Output: 3
```
在这个例子中，`Car` 是一个构造函数，它有一个 `prototype` 属性，我们在 `prototype` 上定义了一个 `start` 方法，所有通过 `Car` 构造函数创建的对象实例都可以访问这个方法。而 `add` 是一个普通函数，它完成一项任务（添加两个数字）并返回一个值。