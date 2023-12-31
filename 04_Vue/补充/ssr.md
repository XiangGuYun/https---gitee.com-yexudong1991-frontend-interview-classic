# SSR

SSR（**Server-Side Rendering**）是**服务器端渲染**的缩写。

它指的是在服务器端将应用或页面渲染成最终的HTML，然后再发送到客户端浏览器进行展示。

SSR的主要优势在于：
1. 更快的首屏加载时间
2. 更好的SEO（搜索引擎优化）
3. 对于不支持或禁用JavaScript的环境有更好的兼容性。

## 餐厅的即时外卖🍱 vs. 自炊🍳

想象一下，你饿了，想吃饭。你可以选择去餐厅外卖一个已经做好的饭菜（**SSR**），这样你可以立即得到并享受它。或者，你也可以选择回家，从冰箱拿出食材，然后自己动手做一顿饭（**CSR**）。虽然自炊可能会更加符合你的口味，但你需要等待食材烹饪完成。

在这里，**餐厅的即时外卖**就像服务器端渲染，你直接得到一个完整的、可以立即使用的页面。而**自炊**则像客户端渲染，页面是在浏览器中逐步构建的，可能需要更多的时间。

>  在Web开发中，SSR提供了一个预渲染的页面，使得用户能够快速看到内容，而不必等待JavaScript加载和执行。而CSR则是在浏览器中逐步加载和渲染页面内容。🌐🖥️


## 追问

### 服务端渲染属于Node.js的技术栈吗

服务端渲染（SSR）不是特定于Node.js的技术，但Node.js是实现SSR的流行工具之一。SSR可以在任何服务器端语言或框架中实现，如Java、PHP、Ruby、Python等。但由于JavaScript同时适用于浏览器和Node.js，这使得Node.js成为现代Web框架（如React、Vue、Svelte等）实现SSR的理想选择，因为它可以重复使用相同的代码库来在服务器和客户端上渲染。所以，虽然SSR不是Node.js技术栈的专有技术，但Node.js确实在SSR领域中非常受欢迎。