JavaScript 中的 `Object` 对象提供了多种方法，帮助我们在处理对象时变得更加方便。以下是一些常用的 `Object` 方法以及相应的代码说明：

### 1. `Object.keys()`
返回一个包含对象自身所有可枚举属性名称的数组。

```javascript
const obj = { a: 1, b: 2, c: 3 };
console.log(Object.keys(obj)); // Output: ['a', 'b', 'c']
```

### 2. `Object.values()`
返回一个包含对象自身所有可枚举属性值的数组。

```javascript
const obj = { a: 1, b: 2, c: 3 };
console.log(Object.values(obj)); // Output: [1, 2, 3]
```

### 3. `Object.entries()`
返回一个给定对象自身可枚举属性的 `[key, value]` 数组。

```javascript
const obj = { a: 1, b: 2, c: 3 };
console.log(Object.entries(obj)); // Output: [['a', 1], ['b', 2], ['c', 3]]
```

### 4. `Object.assign()`
用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。

```javascript
const target = { a: 1 };
const source = { b: 2, c: 3 };
Object.assign(target, source);
console.log(target); // Output: { a: 1, b: 2, c: 3 }
```

### 5. `Object.freeze()`
阻止一个对象被修改（包括添加新的属性、删除已有属性、修改属性值或属性特性等）

```javascript
const obj = { a: 1 };
Object.freeze(obj);
obj.a = 2;  // No effect
obj.b = 3;  // No effect
console.log(obj); // Output: { a: 1 }
```

### 6. `Object.create()`
使用指定的原型对象和其属性创建一个新对象。

```javascript
const person = {
    isHuman: false,
    printIntroduction: function () {
        console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
    }
};
const me = Object.create(person);
me.name = 'Matthew';
me.isHuman = true;
me.printIntroduction();
// Output: My name is Matthew. Am I human? true
```

### 7. `Object.defineProperty()`
在一个对象上定义一个新属性，或修改一个对象的现有属性，并返回此对象。

```javascript
const obj = {};
Object.defineProperty(obj, 'property1', {
    value: 42,
    writable: false
});
console.log(obj.property1); // Output: 42
obj.property1 = 77;
// throws an error in strict mode, otherwise it just fails silently
console.log(obj.property1); // Output: 42
```

### 8. `Object.hasOwnProperty()`
用来检查某个对象是否含有指定的自身（非继承）属性。

```javascript
const obj = { a: 1 };
console.log(obj.hasOwnProperty('a')); // Output: true
console.log(obj.hasOwnProperty('b')); // Output: false
```

以上就是一些常用的 `Object` 方法，每个方法都有其特定的使用场景和目的，能够帮助我们更方便、更高效地处理对象相关操作。