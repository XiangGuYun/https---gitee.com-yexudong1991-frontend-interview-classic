AJAX（Asynchronous JavaScript and XML）的底层实现主要依赖于浏览器提供的 `XMLHttpRequest` 对象或现代浏览器提供的 `Fetch API`。

### XMLHttpRequest

`XMLHttpRequest` 是 AJAX 的基础，它是一个浏览器提供的对象，用于执行异步请求以及处理HTTP响应。下面是使用 `XMLHttpRequest` 对象发起一个简单的GET请求的基础示例：

```javascript
var xhr = new XMLHttpRequest();  // 创建一个 XMLHttpRequest 对象
xhr.open('GET', 'https://api.example.com/data', true);  // 配置请求类型、URL、是否异步
xhr.onload = function() {  // 定义响应处理函数
    if(xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();  // 发送请求
```

### Fetch API

`Fetch API` 提供了一个更现代、更灵活且更强大的方法来发起HTTP请求，并且基于Promises设计，使得异步代码更加简洁。Fetch 不仅可以用于发送 HTTP 请求，还支持很多高级特性，例如请求和响应的拦截、缓存等。

```javascript
fetch('https://api.example.com/data')
    .then(response => response.json())  // 解析响应为 JSON
    .then(data => console.log(data))  // 处理数据
    .catch(error => console.error('Error:', error));  // 处理错误
```

两者在实现上都允许浏览器与服务器进行异步通信，使页面可以在不刷新的情况下更新数据，但它们在API设计、使用方式和功能上存在一些不同。

- **XMLHttpRequest** 是旧的API，它不返回Promise，使得异步操作稍显繁琐和复杂。
- **Fetch API** 是现代的API，基于Promise设计，它返回Promise，使异步代码更加优雅，并提供更加丰富和强大的功能。

两者在底层的网络通信层面实际上都是基于浏览器提供的网络I/O操作来实现的。它们抽象了复杂的底层细节，为开发者提供了更简单易用的API来进行网络请求。