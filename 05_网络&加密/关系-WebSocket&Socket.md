# 关系-WebSocket&Socket

## 概述版

- `WebSocket`是一个专门为Web浏览器与Web服务器之间、需要在单一持久连接上进行全双工通信设计的协议。
- `Socket`则是一个更通用的概念，为各种不同的环境和应用场景提供底层通信支持的机制。

### 比喻法

它们之间的关系有点像是：所有的正方形（WebSocket）都是矩形（Socket），但不是所有的矩形（Socket）都是正方形（WebSocket）。WebSocket提供了一种特定的使用场景的解决方案，而Socket提供了一种更底层、更通用的数据通信机制。


## 详述版

`WebSocket` 和 `Socket` 两者都是通信协议，它们存在一些共同点但也有显著的不同之处。

### **关联与区别：**

1. **共同点：**
   - **实时性**：它们都提供了一种在网络上进行实时双向通信的方式。
   - **基于套接字**：两者都在某种层面上涉及到“套接字”（Socket）这一通信机制。

2. **主要区别：**
   - **应用层面差异：**
      - `WebSocket`：是一个协议标准，并且是一个双向协议。它基于TCP协议，并实现在应用层，用于Web环境，解决了Web实时通信的问题。
      - `Socket`：通常指网络编程中的套接字，是一个编程接口(API)。它可以是基于TCP/UDP的，用于不同设备之间的数据通信。
   - **运行环境的区别：**
      - `WebSocket`：主要运行在浏览器和Web服务器上，用于Web应用程序。
      - `Socket`：可以在任何环境下运行，例如我们可以在两台服务器间通过Socket API建立TCP连接进行数据通信。
   - **协议规范的区别：**
      - `WebSocket`：协议较为简洁、轻量，只需一次握手就能创建持久的连接，并在连接过程中信息头部数据较少。
      - `Socket`：没有协议上的限制，能够进行复杂多变的操作。

## 追问

### 除了WebSocket，还有哪些Socket？

1. **TCP Socket：**
   - **概念**：基于传输层协议TCP的Socket通信。
   - **特点**：面向连接、可靠的字节流服务。

2. **UDP Socket：**
   - **概念**：基于传输层协议UDP的Socket通信。
   - **特点**：无连接的、尽最大努力交付的数据报服务。

3. **Unix Domain Socket：**
   - **概念**：用于同一台机器上的进程间通信的Socket。
   - **特点**：不涉及网络栈，较为轻量，数据传输较快。

4. **Raw Socket：**
   - **概念**：能够允许应用程序直接访问底层网络协议的Socket。
   - **特点**：通常用于开发网络监控工具或定制特定协议的通信。

5. **Secure Socket（SSL/TLS Socket）：**
   - **概念**：在Socket通信上应用安全协议（如SSL/TLS）进行加密通信的技术。
   - **特点**：提供安全的数据传输。

在开发实际应用时，选择使用何种类型的Socket、或是WebSocket，依赖于项目需求，例如是否要求连接持久、是否要求数据交换实时性、是否有安全性要求等。这些“分类”是使用Socket通信机制在不同协议和场景下的不同实现和应用。
