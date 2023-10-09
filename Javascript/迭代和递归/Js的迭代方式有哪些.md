在 JavaScript 中，迭代主要体现在数组、对象、字符串等数据结构的遍历上。下面介绍一些常用的迭代方式：

### 1. `for` 循环

这可能是最基础的迭代方式之一了，常用于数组的遍历。

```javascript
for (let i = 0; i < array.length; i++) {
    console.log(array[i]);
}
```

### 2. `for...in` 循环

`for...in` 循环主要用于遍历对象的键名。

```javascript
const obj = {a: 1, b: 2, c: 3};
for (let key in obj) {
    console.log(key, obj[key]);
}
```

### 3. `for...of` 循环

`for...of` 循环用于遍历可迭代对象的值，如数组、字符串、Map、Set 等。

```javascript
const arr = [1, 2, 3];
for (let value of arr) {
    console.log(value);
}
```

### 4. `forEach` 方法

数组的 `forEach` 方法接收一个回调函数，该函数将为数组的每个元素执行一次。

```javascript
const array = [1, 2, 3];
array.forEach(function(item, index, array) {
    console.log(item, index);
});
```

### 5. `map` 方法

数组的 `map` 方法返回一个新数组，其内容为原数组中的每个元素调用一个提供的函数的结果。

```javascript
const array = [1, 2, 3];
const newArray = array.map(item => item * 2);
```

### 6. `filter` 方法

`filter` 方法创建一个新数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

```javascript
const array = [1, 2, 3];
const newArray = array.filter(item => item > 1);
```

### 7. `reduce` 方法

`reduce` 方法对数组中的每个元素执行一个由您提供的reducer函数(升序执行)，将其结果汇总为单个返回值。

```javascript
const array = [1, 2, 3];
const sum = array.reduce((accumulator, currentValue) => {
    return accumulator + currentValue;
}, 0);
```

### 8. `some` 和 `every` 方法

- `some` 方法测试数组中是否有些元素通过由提供的函数实现的测试。
- `every` 方法检测数组所有元素是否都符合指定的条件。

```javascript
const array = [1, 2, 3];
const hasPositiveNumbers = array.some(num => num > 0);
const allPositiveNumbers = array.every(num => num > 0);
```

### 9. `Object.keys()`, `Object.values()`, `Object.entries()`

这些方法分别用于迭代对象的键、值或键值对。

```javascript
const obj = {a: 1, b: 2, c: 3};
Object.keys(obj).forEach(key => console.log(key));
Object.values(obj).forEach(value => console.log(value));
Object.entries(obj).forEach(([key, value]) => console.log(key, value));
```

这些就是在 JavaScript 中常见的迭代方式。每种方法都有自己的用途和优点，在不同的场景中根据需求选择合适的迭代方式。