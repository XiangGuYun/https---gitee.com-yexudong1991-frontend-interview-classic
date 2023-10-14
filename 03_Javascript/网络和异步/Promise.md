### JavaScript 的 Promise

在 JavaScript 中，`Promise` 是一种处理异步操作的对象。异步操作通常包括一些不会立即完成的操作，如网络请求、定时器等。`Promise` 提供了一种优雅的方式来处理这些异步操作的最终完成（或失败），以及它们的结果值。

#### Promise 的三种状态：

1. **Pending（等待）**：初始化状态，既不是成功，也不是失败。
   
2. **Fulfilled（完成）**：操作成功完成。
   
3. **Rejected（拒绝）**：操作失败或出错。

一个 `Promise` 必定处在这三种状态中的一种。

#### 基本结构

`Promise` 对象通常在创建时接收一个函数（通常称为“执行器”），这个函数带有两个参数：`resolve` 和 `reject`，它们是两个用于将 `Promise` 状态从等待转移到完成或拒绝的函数。

```javascript
let promise = new Promise((resolve, reject) => {
    // 异步操作

    if(/* 异步操作成功 */) {
        resolve('Operation successful');
    } else {
        reject('Operation failed');
    }
});
```

- `resolve(value)`：将 Promise 状态转为 fulfilled，并将操作结果 `value` 传递出去。
  
- `reject(reason)`：将 Promise 状态转为 rejected，并将错误或拒绝的原因 `reason` 传递出去。

#### 使用 Promise

##### `.then()` 和 `.catch()`

当 Promise 被 resolve（完成）时，`.then()` 方法会被调用。当 Promise 被 reject（拒绝）时，`.catch()` 方法会被调用。

```javascript
promise
    .then((value) => {
        console.log(value); // 'Operation successful'
    })
    .catch((reason) => {
        console.error(reason); // 'Operation failed'
    });
```

##### 链式调用

`.then()` 和 `.catch()` 方法都返回新的 Promise，允许它们被链接起来。

```javascript
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));
```

在这个示例中，我们发起一个网络请求（`fetch` 返回一个 Promise）。一旦第一个 `.then()` 完成（并返回新的 Promise），第二个 `.then()` 将被调用。如果在链中的任何地方发生错误，`.catch()` 将被调用。

#### Promise 静态方法


- `Promise.all(iterable)`: 在 iterable 参数中所有的 promise 都 `fulfilled` 或其中一个 `rejected` 时，返回一个 promise。

- `Promise.resolve(value)`: 返回一个以给定值解析后的 Promise 对象。

- `Promise.reject(reason)`: 返回一个带有拒绝原因的 Promise 对象。


#### 搭配async、await使用

```javascript
async function fetchData() {
    try {
        let response = await fetch('https://api.example.com/data');  // 等待，直到 Promise 完成
        let data = await response.json();  // 等待，直到 Promise 完成
        console.log(data);  // 输出获取到的数据
    } catch (error) {
        console.error('Error:', error);  // 如果有错误，捕获并输出
    }
}

fetchData();  // 调用函数

```

* 当我们调用 fetchData() 函数时，JavaScript 将在碰到 await 关键字时暂停函数的执行，等待 Promise 完成，然后继续执行函数的剩余部分。
* 如果 Promise 被成功解析（fulfilled），await 将返回解析后的值。
* 如果 Promise 被拒绝（rejected），await 会抛出一个异常。我们可以使用 try/catch 语句来捕获这些异常并优雅地处理它们


#### 小结

Promise 是 JavaScript 中处理异步逻辑的一种强大工具。它允许开发者在异步操作完成或失败时获得通知，并能够以链式调用的形式组合异步操作，使得异步代码更加清晰和易于理解。