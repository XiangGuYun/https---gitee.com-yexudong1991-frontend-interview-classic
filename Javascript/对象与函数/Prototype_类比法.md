# 类比法

### 类比1：prototype和extends

> 🤔Dog.prototype = new Animal()是否类似于Java中的class Dog extends Animal{}

是的，这个类比是相当贴切的！在很多面向对象的编程语言（比如 Java）中，类的继承通常使用 `extends` 关键字来表示。在 JavaScript 中，由于它的原型链继承机制，我们通常通过设置一个类（函数）的 `prototype` 为另一个类的实例来实现类似的继承效果。因此：

```javascript
Dog.prototype = new Animal();
```

这行代码的作用，的确与 Java 中的

```java
class Dog extends Animal {}
```

类似。但还是要注意，这两者在实现上还是有所不同的。

在 **JavaScript** 中：
- `Dog.prototype = new Animal();` 实际上设置了 `Dog` 的原型对象为 `Animal` 的一个实例。所以 `Dog` 的实例在查找属性或方法时如果在自身没有找到，会在其原型（即 `Animal` 的实例）上查找。

在 **Java** 中：
- `class Dog extends Animal {}` 则表示 `Dog` 类继承了 `Animal` 类的所有公共和受保护的字段和方法。这在内部实现上与 JavaScript 的原型链有所不同，尽管从效果上看起来非常类似。

两者主要的差别在于 JavaScript 使用基于原型的继承（一个对象实例继承自另一个对象实例），而 Java 使用的是基于类的继承。不过，在 ES6 及以后的版本中，JavaScript 也引入了 `class` 和 `extends` 关键字来实现更易于理解的基于类的继承写法。例如：

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  sayName() {
    console.log(this.name);
  }
}

class Dog extends Animal {
  bark() {
    console.log('Woof!');
  }
}
```

在这个 JavaScript 例子中，使用 `class` 和 `extends` 关键字的写法更接近 Java 或其他面向对象编程语言的风格，也更容易被从这些语言背景转过来的开发者理解。

> 🤔es6引入class机制后，prototype使用是不是变少了

确实，自从 ES6 引入了 `class` 这一概念之后，JavaScript 中基于原型（`prototype`）的编程风格在某些场景（特别是类的定义和继承）中确实变得不那么明显或直接了。使用 `class` 语法进行面向对象编程比使用 `prototype` 链更加直观和简洁，它提供了一种更接近传统面向对象语言的编程方式。

下面是一个使用 `class` 的简单例子：

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  sayName() {
    console.log(this.name);
  }
}

class Dog extends Animal {
  bark() {
    console.log('Woof!');
  }
}

const myDog = new Dog('Buddy');
myDog.sayName(); // 输出：Buddy
myDog.bark();    // 输出：Woof!
```

这种方式对于许多具有其他编程语言背景（例如 Java 或 C++）的开发者来说，可能更易理解和采纳。

然而，`prototype` 仍然在幕后发挥着作用。实际上，**`class` 语法只是基于 `prototype` 的语法糖**。即便我们在使用 `class` 和 `extends` 关键字时，JavaScript 依然在后台使用原型链来处理对象的创建和继承。以下两个例子从功能上是等价的：

**使用 `prototype`:**
```javascript
function Animal(name) {
  this.name = name;
}
Animal.prototype.sayName = function() {
  console.log(this.name);
};

function Dog(name) {
  Animal.call(this, name);
}
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;
Dog.prototype.bark = function() {
  console.log('Woof!');
};

const myDog = new Dog('Buddy');
myDog.sayName(); // 输出：Buddy
myDog.bark();    // 输出：Woof!
```

**使用 `class`:**
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  sayName() {
    console.log(this.name);
  }
}

class Dog extends Animal {
  bark() {
    console.log('Woof!');
  }
}

const myDog = new Dog('Buddy');
myDog.sayName(); // 输出：Buddy
myDog.bark();    // 输出：Woof!
```

在一些场景下（尤其是库和框架的开发中），明确的使用 `prototype` 仍然是很有价值的，因为它提供了更多的灵活性和控制能力。同时，在进行一些与性能相关的优化时，直接操作原型可能会提供额外的优势。所以，尽管在许多常见用例中我们可能更倾向于使用 `class`，`prototype` 仍然是 JavaScript 对象模型中不可或缺的一部分。

### 类比2：JS的function vs Java的class

在 ES6 引入 `class` 之前，JavaScript 通过使用 `function` 关键字和 `prototype` 属性来实现类似于其他面向对象编程语言的 "类" 的功能。

在 JavaScript 中，函数（使用 `function` 关键字定义的）不仅是一种可调用对象，而且也可以拥有属性和方法——这允许它们被用作构造函数来创建对象的实例。使用 `prototype` 属性，我们可以将方法和属性添加到由构造函数创建的所有对象实例中。

看下面这个例子：

```javascript
function Dog(name) {
  this.name = name; 
}

Dog.prototype.bark = function() {
  console.log(this.name + " says woof");
};
```

在这里，`Dog` 是一个使用 `function` 关键字创建的函数，但同时它也被用作一个构造函数，因为我们可以使用 `new` 关键字来基于它创建新的对象实例：

```javascript
var myDog = new Dog("Buddy");
```

通过将方法添加到 `Dog.prototype`，这些方法将成为通过 `Dog` 构造函数创建的所有对象实例的一部分：

```javascript
myDog.bark();  // 输出：Buddy says woof
```

在这方面，`Dog` 函数起着类似于 Java 中 `class` 的作用——它允许我们基于一个通用的模板（构造函数加上其 `prototype` 中的方法）创建对象实例。在 ES6 中引入的 `class` 关键字实际上提供了一种更直观、更符合其他OOP语言的方式来实现相同的功能。但在幕后，`class` 语法实际上还是基于 JavaScript 原型继承的语法糖。

因此，你可以说在引入 `class` 关键字之前，`function` 和 `prototype` 起着实现面向对象编程的类似作用。