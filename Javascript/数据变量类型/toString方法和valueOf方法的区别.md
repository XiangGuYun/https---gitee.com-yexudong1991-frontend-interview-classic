在 JavaScript 中，`toString` 方法和 `valueOf` 方法都是对象（`Object`）的内置方法，通常用于获取对象的字符串表示或原始值表示。它们在处理对象转换（尤其是对象与原始数据类型之间的转换）时起到关键作用。

### `toString` 方法
- **目的**：获取对象的字符串表示。
- **返回值**：返回对象的字符串表示。
- **常见应用**：当一个对象被视为一个字符串时，`toString` 方法会被自动调用。

```javascript
const obj = {key: 'value'};
console.log(obj.toString()); // [object Object]
```

### `valueOf` 方法
- **目的**：获取对象的原始值表示。
- **返回值**：通常返回对象自己，除非原始值有明确的表示。
- **常见应用**：在对象涉及到算术运算或比较运算时，`valueOf` 方法通常会被调用。

```javascript
const numObj = new Number(5);
console.log(numObj.valueOf()); // 5
```

### 区别与联系
1. **用途**：
   - `toString` 倾向于返回对象的**字符串表示**。
   - `valueOf` 倾向于返回对象的**原始值表示**（如果有的话）。

2. **调用场景**：
   - 当对象参与**字符串操作**（如连接运算）时，通常会调用 `toString` 方法。
   - 当对象参与**数值运算**或**比较运算**时，通常会调用 `valueOf` 方法。

3. **默认行为**：
   - 在默认情况下，对象的 `toString` 方法返回格式为 `"[object Type]"` 的字符串。
   - 默认情况下，对象的 `valueOf` 方法返回对象本身。

4. **可定制**：
   - 你可以为自定义对象重写这两个方法，以便实现特定的转换逻辑。

### 示例
```javascript
function MyObj() {
  this.value = 10;
}

MyObj.prototype.toString = function() {
  return `This object has value: ${this.value}`;
};

MyObj.prototype.valueOf = function() {
  return this.value;
};

const obj = new MyObj();

console.log(obj + 10); // 20 (valueOf is called due to addition operation)
console.log(obj + ''); // This object has value: 10 (toString is called due to concatenation)
```

这两个方法在实际应用中非常有用，尤其是当你创建自定义对象，并且想要控制这些对象如何转换为原始数据类型时。