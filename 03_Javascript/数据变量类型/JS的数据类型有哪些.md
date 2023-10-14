JavaScript 提供了一系列的数据类型来处理各种不同的数据。下面列举了 JavaScript 中常用的数据类型：

### 1. 原始数据类型 (Primitive Data Types)

#### a. Number
表示整数或浮点数。
```javascript
let num = 123;
let floatNum = 123.45;
```

#### b. String
表示文本数据或字符串。
```javascript
let str = 'Hello, World!';
```

#### c. Boolean
表示逻辑真/假。
```javascript
let isTrue = true;
let isFalse = false;
```

#### d. Null
表示一个故意留空或无值的变量。
```javascript
let emptyValue = null;
```

#### e. Undefined
表示变量已声明但未赋值。
```javascript
let noValue;
console.log(noValue); // undefined
```

#### f. Symbol
创建唯一的标识符，常用于对象属性的键。
```javascript
let sym = Symbol("description");
```

#### g. BigInt
用于表示大整数。
```javascript
let bigIntValue = 1234567890123456789012345678901234567890n;
```

### 2. 复杂数据类型 (Object Data Type)

#### a. Object
用于存储键值对的实例。
```javascript
let obj = {
  key1: 'value1',
  key2: 'value2'
};
```

#### b. Array
用于存储有序的元素集合。
```javascript
let arr = [1, 2, 3, 4, 5];
```

#### c. Function
用于存储可执行的代码块。
```javascript
let func = function() {
  console.log('Hello, Function!');
};
```

#### d. Date
用于处理日期和时间。
```javascript
let currentDate = new Date();
```

#### e. RegExp
用于处理正则表达式。
```javascript
let reg = /ab+c/;
```

#### f. Map, Set, WeakMap, WeakSet
用于存储集合（集合中的元素是唯一的）和映射（键值对的集合）。
```javascript
let mySet = new Set();
let myMap = new Map();
```

### 3. 特殊数据类型

#### a. NaN
表示不是一个数字的特殊数值。

JavaScript 的这些数据类型提供了丰富的工具来处理不同种类的数据和操作，比如存储数据、文本处理、数学计算、逻辑操作等。