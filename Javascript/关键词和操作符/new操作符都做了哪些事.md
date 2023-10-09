在 JavaScript 中，`new` 操作符用于创建一个用户定义的对象类型的实例或具有构造函数的内置对象类型之一。使用 `new` 操作符来调用构造函数的过程通常称为“实例化对象”。

下面是使用 `new` 操作符时，背后发生的步骤：

### 1. 创建一个新对象
当我们使用 `new` 操作符调用构造函数时，JavaScript 会自动创建一个新的空对象。

### 2. 设置原型链
新创建的对象的 `[[Prototype]]`（或者说 `__proto__`）属性被链接到构造函数的 `prototype` 对象。这样新对象就可以访问构造函数原型上的方法和属性。

### 3. 绑定 `this` 值
在构造函数内部，`this` 关键字引用新创建的对象。这样，构造函数内部对 `this` 的操作实际上就是在操作新创建的对象。

### 4. 执行构造函数中的代码
构造函数中的代码被执行，通常这会涉及初始化新对象的属性和方法等。

### 5. 返回新对象
除非构造函数显式返回一个对象值，否则 `new` 操作符调用的函数返回新创建的对象。若构造函数返回了一个对象，那么这个对象会作为整个表达式的返回值。如果构造函数没有返回对象，则返回 `this`（即新创建的对象）。

下面的代码展示了一个使用 `new` 操作符创建对象的例子，并附带上注释说明各个步骤：

```javascript
function Car(make, model) {
    // Step 3: `this` 关键字引用新创建的对象
    this.make = make; 
    this.model = model; 
}

Car.prototype.getMakeModel = function() {
    return this.make + ' ' + this.model;
}

// Step 1: 创建一个新对象
// Step 2: 设置原型链
// Step 3: 绑定 `this` 值
// Step 4: 执行构造函数中的代码
// Step 5: 返回新对象
var myCar = new Car("Toyota", "Corolla");

console.log(myCar.getMakeModel());  // Output: "Toyota Corolla"
```

这个例子包括上述所有步骤，并通过 `myCar` 对象的 `getMakeModel` 方法的调用，展示了新对象是如何通过原型链访问构造函数的 `prototype` 上的方法的。