# 什么是WebSocket

## 概述版

WebSocket是一种网络通信协议，支持双向通信，用于在客户端和服务器之间实时传输数据，通常用于Web应用中的实时通信。

### 比喻法-🚀 **实时聊天屋：神奇的WebSocket**

🕸️ **WebSocket**：想象一个有大玻璃窗的屋子（**持久连接**），你（客户端）和你的朋友（服务器）通过窗子无需敲门（**无需重新建立连接**）就能轻松聊天（**实时双向通信**）。你们可以在任何时候抛出话题（数据包），对方都能立即接住并回应。这个全时无障碍的沟通窗口让你们的对话（数据交换）更流畅，不再需要来回跑动（频繁的请求和响应）。

在这种方式下，交流变得更及时、直接且亲密。

## 详述版

**WebSocket** 是一种网络通信协议，提供了任意两端之间的、全双工的通信渠道。WebSocket 通信协议于2011年被IETF定为标准RFC 6455，并被W3C用于Web标准。WebSocket解决了Web实时化问题，使得数据可以更加实时地进行双向传输。

### WebSocket的特点：

1. **建立在TCP协议之上**：它借用了HTTP协议来建立连接，但在数据传输上并不共享其他特性。
   
2. **实时性强**：它能更实时地进行数据传输。当服务器有数据更新时，可以主动传递给客户端。

3. **协议标识符**：ws（如果加密，则为wss）。

4. **持久连接**：一旦WebSocket的数据通道打开，数据可以双向传输直到其中一方断开连接。

5. **头信息量小**：在传输数据时，协议头部信息比HTTP小很多，减少了数据的传送量。

### WebSocket与HTTP的区别：

- **实时性**：HTTP通常需由客户端发起请求，服务器响应。WebSocket允许服务器主动推送信息给客户端。
  
- **连接**：HTTP连接使用完必须关闭，WebSocket则建立持久连接。

- **头信息**：WebSocket的头信息量小，更适合于移动端的使用。

### 使用场景：

WebSocket 通常用于那些需要实时交互的场景，例如：
- 在线聊天
- 实时广播
- 在线游戏
- 实时交易
- 协同编辑
- 实时监控等

### 示例：

在使用WebSocket时，客户端浏览器和服务器通过WebSocket协议创建连接。以下是在浏览器环境中创建WebSocket连接的简单示例：

```javascript
// 创建WebSocket连接
const socket = new WebSocket('ws://example.com/socketserver');

// 连接打开时触发
socket.onopen = function (event) {
    console.log("WebSocket is open now.");
};

// 接收到服务器消息时触发
socket.onmessage = function (event) {
    console.log("Received data from server: ", event.data);
};

// 连接关闭时触发
socket.onclose = function (event) {
    console.log("WebSocket is closed now.");
};

// 使用send方法发送数据
socket.send("Hello Server!");
```

WebSocket通常用于前端与服务器之间需要快速、双向、持久通信的场景，在某些需要高实时性的应用中具有非常重要的作用。