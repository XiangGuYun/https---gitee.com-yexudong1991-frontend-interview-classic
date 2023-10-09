**AJAX**（Asynchronous JavaScript and XML）是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。其核心是允许你执行异步 HTTP 请求，这意味着能够与服务器进行小批量数据的交换，并在不影响现有页面的情况下更新部分页面内容。虽然名字中包含XML，但现在AJAX通常使用JSON作为数据格式，因为JSON通常更简单、轻量。

### 关键部分
1. **Asynchronous（异步）**：意味着你可以在等待服务器响应的时候执行其他代码。
2. **JavaScript**：执行异步请求、接收响应、处理数据（例如更新UI）的脚本语言。
3. **XML/JSON**：数据的传输格式，尽管XML经常用于这种目的，但目前JSON更为常用。

### AJAX 的工作流程
1. 通过JavaScript创建一个XHR对象（或使用Fetch API）。
2. 发送一个HTTP请求到服务器。
3. 一旦接收到服务器响应，JavaScript可以更新部分页面。

### 例子
这里是一个使用`XMLHttpRequest`对象执行一个简单的AJAX请求的示例：

```javascript
// 创建一个新的XMLHttpRequest对象
var xhr = new XMLHttpRequest();

// 配置它：GET请求到URL
xhr.open('GET', 'https://api.example.com/data', true);

// 设置响应类型为 JSON 
xhr.responseType = 'json';

// 当请求收到响应时执行
xhr.onload = function() {
    if(xhr.status == 200) { // 如果状态码为200，说明是一个成功的请求
        console.log(xhr.response); // 处理响应
    } else {
        console.log("Error " + xhr.status); // 否则显示状态码
    }
};

// 发送请求
xhr.send();
```

也可以使用`Fetch API`，这是一个现代的、基于 Promise 的API，它提供了一个更加简洁和强大的方式来处理 HTTP 请求。

```javascript
fetch('https://api.example.com/data')
    .then(response => {
        if (!response.ok) {
            throw new Error('Network response was not ok' + response.statusText);
        }
        return response.json();
    })
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error('There has been a problem with your fetch operation:', error);
    });
```

### 注意
- AJAX 请求可能受同源策略的限制。除非服务器实现了某种方式来允许跨源资源共享（CORS），否则请求可能会受到限制。
- 在处理异步请求时，可能需要考虑到各种可能的网络问题，并在实现时进行处理，例如超时和请求失败等情况。