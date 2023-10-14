在 JavaScript 中，作用域可以被理解为一个变量的可访问范围，即在哪些地方我们可以访问到某个变量。在 JS 中主要有两种类型的作用域：

### 1. 全局作用域（Global Scope）

- **定义**：任何在代码的最外层定义的变量或函数都位于全局作用域。在浏览器环境中，全局作用域的对象通常是`window`。
- **可访问性**：全局作用域中的变量和函数可以在代码的任何地方被访问和修改。

```javascript
var globalVar = "I am global!"; // 全局变量

function show() {
    console.log(globalVar); // 可以访问全局变量
}
```

### 2. 局部作用域（Local Scope）

局部作用域又可分为函数作用域和块级作用域。

- **函数作用域（Function Scope）**
    - **定义**：在函数内部声明的变量和函数。
    - **可访问性**：只有函数内部的代码能够访问这些变量和函数。
    ```javascript
    function exampleFunction() {
        var functionScopeVar = "I am local to function!";
        console.log(functionScopeVar); // 可访问
    }
    // console.log(functionScopeVar); // 报错，不可访问
    ```

- **块级作用域（Block Scope）**
    - **定义**：使用`let`和`const`关键字在代码块（例如`if`语句、`for`循环等）中定义的变量或常量。
    - **可访问性**：只在该代码块及其嵌套的代码块中可访问。
    ```javascript
    if(true){
        let blockScopeVar = "I am local to block!";
        console.log(blockScopeVar); // 可访问
    }
    // console.log(blockScopeVar); // 报错，不可访问
    ```

### 注意事项

- **变量提升（Hoisting）**：`var`声明的变量会发生变量提升，即它们会在执行流进入它们所在的上下文（全局或函数）时先被初始化为`undefined`。而`let`和`const`不会发生变量提升。
- **词法作用域（Lexical Scope）**：JavaScript 的作用域是词法的，也就是说，它们是在代码书写阶段就定义好的，与执行流控制无关。

### 总结

理解作用域及其规则对于编写可维护和错误较少的代码是非常关键的。它会影响变量的生命周期、可见性、以及如何和何时它们会被回收。