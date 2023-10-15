延迟加载（或称懒加载）JavaScript的目标是优化页面加载时间和用户体验，通过推迟非关键JS资源的加载来加速页面的初始渲染。下面是一些在网页开发中常用的延迟加载JavaScript的策略：

<div style="border: 1px solid;border-radius:5px;padding:5px;font-size:0.9rem;font-style:italic">
记忆：ad属性、创建s标签、事件触发、交集观察者、ajax、Webpack分割
</div>

### 1. 使用`async`和`defer`属性

在`<script>`标签中使用`async`或`defer`属性可以使得脚本异步加载。

- **`async`：** 脚本将异步加载并在加载完成后立即执行。多个`async`脚本不能保证加载顺序。
  ```html
  <script async src="path-to-your-script.js"></script>
  ```
- **`defer`：** 脚本将异步加载但会在所有页面内容解析完成后，按脚本顺序执行。
  ```html
  <script defer src="path-to-your-script.js"></script>
  ```

### 2. 动态创建`<script>`标签

通过JavaScript动态添加`<script>`标签来加载JS代码。

```javascript
var script = document.createElement('script');
script.src = "path-to-your-script.js";
document.body.appendChild(script);
```

### 3. 使用事件触发

将非关键的JS脚本放在某些事件触发后才加载执行，例如滚动事件、点击事件或其他用户互动事件。

```javascript
window.addEventListener("scroll", function loadScriptOnScroll() {
    // 逻辑判断：例如判断页面滚动到一定位置
    var script = document.createElement('script');
    script.src = "path-to-your-script.js";
    document.body.appendChild(script);
    // 取消事件监听，防止多次加载
    window.removeEventListener("scroll", loadScriptOnScroll);
});
```

### 4. 使用Intersection Observer API

利用Intersection Observer API在元素进入视窗时进行加载。

```javascript
var observer = new IntersectionObserver(function(entries) {
    if(entries[0].isIntersecting) {
        var script = document.createElement('script');
        script.src = "path-to-your-script.js";
        document.body.appendChild(script);
        observer.disconnect();
    }
}, { threshold: [0] });

observer.observe(document.getElementById('your-element-id'));
```

### 5. 使用AJAX

通过AJAX请求获取JS代码并使用`eval()`或`new Function()`执行。

```javascript
var xhr = new XMLHttpRequest();
xhr.open("GET", "path-to-your-script.js", true);
xhr.onreadystatechange = function() {
    if(xhr.readyState === 4 && xhr.status === 200) {
        eval(xhr.responseText);
    }
};
xhr.send();
```

### 6. 使用Webpack代码分割

在构建工具（如Webpack）层面进行代码分割和懒加载。

```javascript
// 使用import()语法动态导入模块
button.addEventListener('click', () => {
    import('./path-to-your-module.js')
        .then(module => {
            module.yourFunction();
        })
        .catch(err => {
            console.log('模块加载失败：', err);
        });
});
```

以上就是一些在前端开发中常见的延迟加载JavaScript的方法，可以根据项目的实际需求和场景选择最适合的策略。