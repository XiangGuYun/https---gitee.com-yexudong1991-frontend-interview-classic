### JSONP（JSON with Padding）

**JSONP** 是一种跨域数据交互的方案。它利用了浏览器在请求脚本（`<script>` 标签）时不受同源策略限制的特点来进行跨域请求。JSONP 的实质是动态添加一个 `<script>` 标签来调用服务器提供的脚本。

**JSONP 的主要流程如下**：

1. 客户端：在全局作用域下定义一个处理数据的回调函数。
2. 客户端：通过动态创建 `<script>` 标签，并指定其 `src` 属性为目标URL（URL中通常包含查询参数，其中一个参数是刚刚定义的回调函数的名称）。
3. 服务器：接收请求后，在服务器端获取到回调函数名，并将数据用该函数名包裹起来，形成类似`callbackName(data)`这样的字符串，返回给客户端。
4. 客户端：由于返回的是脚本内容，浏览器自动执行这个脚本，也就执行了回调函数，数据作为参数传入，实现了跨域数据的获取和处理。

**JSONP 使用示例**：

```javascript
// 定义处理数据的函数
function handleData(data) {
    console.log(data);
}

// 动态创建script标签
const script = document.createElement('script');
script.src = 'http://example.com/data?callback=handleData';  // 设置请求URL，并指定回调函数名
document.body.appendChild(script);
```

在服务器端，响应内容可能类似这样：

```javascript
handleData({"key": "value"});
```

浏览器接收到响应后会自动执行这段代码，也就调用了`handleData`函数，并将数据对象`{"key": "value"}`传递给它。

### 使用 JSONP 实现跨域

JSONP 可以用来实现跨域数据请求。其关键在于利用 `<script>` 标签的 `src` 属性请求的脚本不会被同源策略所限制，因此可以从不同的域请求数据。

### 需要注意的点：

1. **只能发送GET请求**：由于是基于 `<script>` 标签的，JSONP 只能用于 GET 请求。
   
2. **安全性问题**：由于 JSONP 是纯粹的执行脚本操作，如果对方服务器返回的脚本存在恶意代码，则可能对网站安全造成威胁。
   
3. **不支持错误处理**：JSONP 的请求不同于 XMLHttpRequest，没有标准的错误处理机制。

4. **兼容性问题**：虽然 JSONP 能兼容绝大多数的浏览器，但在某些特定的使用场景下（例如需要进行错误处理、需要使用POST方法的场景下），JSONP 的局限性就表现得尤为明显。

尽管 JSONP 是实现跨域请求的一种简单方法，但由于其存在上述的一些局限性和安全问题，现在在很多场景下我们更倾向于使用CORS（跨域资源共享）策略来实现跨域控制。

## 比喻法

让我们通过一个“图书馆借书”的比喻来理解JSONP及其跨域能力。📚

***

在一个小城镇里，有两座图书馆🏛️（两个不同源的服务器）。居民们（web页面）通常只在自己所属的图书馆借阅图书（获取数据）。

- 图书馆的基础规则（同源策略）：居民只能从自己所在地区的图书馆借书，不允许去其他图书馆借书。
  
现在，图书馆A🏛️有一本珍贵的古籍📜（特殊数据），图书馆B🏛️没有。一位居民🧑（web页面）想要借阅那本来自图书馆A的古籍。

***

因为不允许居民直接从其他图书馆借书，所以他们想出了一个巧妙的方法🎩（JSONP）：
  

```javascript
// 居民🧑写了一本书📘（创建一个callback函数）
function receiveAncientBook(content) {
    console.log("I got the ancient book: ", content);
}

// 接着，他把这本书放在图书馆A的一个特定的书架上🗄️
// （通过<script>标签插入一个回调函数到web页面）
var script = document.createElement('script');
script.src = 'http://libraryA.com/getAncientBook?callback=receiveAncientBook';
document.body.appendChild(script);
```

服务器（图书馆A）的部分可能是这样的：

```javascript
// 图书馆A的管理员👩（服务器端）看到这本书，
// 按照约定，把古籍的内容摘抄在那本书中
// （服务器包装数据成一个函数调用），
// 然后再归还给居民（通过src属性发送数据）。

// 假设有一个HTTP请求到达了，例如：
// GET /getAncientBook?callback=receiveAncientBook

// 服务器可能会这样响应：
res.setHeader('Content-Type', 'application/javascript');
res.send(`receiveAncientBook("The content of the ancient book...");`);
```

在这个示例中：
- `receiveAncientBook` 是居民🧑编写的书（回调函数），用来记录古籍的内容。
- 当居民把书放在图书馆A的书架上（通过`<script>`标签请求数据）时，图书馆A的管理员（服务器端）收到了这个请求，看到书中的约定。
- 然后，管理员摘抄古籍内容，将它写入这本书，并返回给居民。这是通过将数据包装在预定的回调函数中，使其作为JS代码发送给客户端来实现的。
- 当这个JS代码在客户端运行，预定义的回调函数将被调用，从而居民得知了古籍的内容。

通过这个巧妙的方法，居民成功地"借阅"到了另一座图书馆的珍贵古籍，也就是实现了跨图书馆的“借书”行为（跨域请求数据）。