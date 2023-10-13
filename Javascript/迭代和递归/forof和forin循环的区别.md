`for...of` 和 `for...in` 循环在JavaScript中都用于迭代，但它们的使用场景和迭代方式有所不同。

### `for...in` 循环
- **使用场景**: 主要用于遍历==对象的可枚举属性（包括其原型链上的属性）==。
- **迭代对象的键**: 遍历时获取的是对象的键（key）。
- **例子**:

  ```javascript
  const object = { a: 1, b: 2, c: 3 };

  for (const key in object) {
    console.log(key, object[key]); // 输出键和对应的值
  }
  ```
- **注意点**:
  - 由于 `for...in` 也遍历对象的原型链，通常我们使用 `hasOwnProperty` 方法来过滤掉原型链上的属性。

    ```javascript
    for (const key in object) {
      if (object.hasOwnProperty(key)) {
        console.log(key, object[key]);
      }
    }
    ```

### `for...of` 循环
- **使用场景**: 主要用于遍历==具有 iterator 接口的对象==（如数组、字符串、Set、Map等）。
- **迭代对象的值**: 遍历时获取的是对象的值（value）。
- **例子**:

  ```javascript
  const array = [1, 2, 3];

  for (const value of array) {
    console.log(value); // 输出数组的每一个值
  }
  ```
- **注意点**:
  - ==不能用于普通对象的遍历==，除非该对象实现了[Symbol.iterator]接口。

### 对比

|             | `for...in`            | `for...of`             |
|-------------|-----------------------|------------------------|
| **用途**    | 遍历对象的键          | 遍历可迭代对象的值     |
| **对象**    | 所有对象              | 仅限可迭代对象         |
| **获取的内容** | 键（字符串）          | 值                     |
| **原型链**  | 遍历原型链上的属性    | 不适用                |

综上，你会发现`for...in`和`for...of`各自适用于不同的情况。在实际开发中根据需求选择更合适的遍历方式。