`var` 和 `let` 是 JavaScript 中用于声明变量的关键字，它们的用法相似，但在作用域、提升（hoisting）及全局对象属性等方面存在一些显著的差异。这些差异主要体现在以下几个方面：

### 1. 作用域 Scope

- **`var`**: 声明的变量拥有函数作用域（function scope）或全局作用域（global scope）。
- **`let`**: 声明的变量拥有块作用域（block scope）。

### 2. 提升 Hoisting

- **`var`**: 变量声明会被提升到它们所在的函数或全局作用域的顶部。
- **`let`**: 变量声明不会被提升到块作用域的顶部，如果在声明前使用它们会抛出一个错误。

### 3. 重新声明 Re-declaration

- **`var`**: 在同一作用域中，可以多次重新声明同一个变量。
- **`let`**: 不允许在相同作用域内重新声明同一个变量。

### 4. 全局对象属性

- **`var`**: 在最外层（全局作用域）声明的变量会变成全局对象的属性（例如，浏览器环境中的`window`对象）。
- **`let`**: 在任何地方声明的变量都不会被添加到全局对象中。

### 例子

以下示例展示了 `var` 和 `let` 的一些区别：

```javascript
// 1. 作用域的区别
if (true) {
    var varVariable = "I am var";
    let letVariable = "I am let";
}
console.log(varVariable); // 输出：I am var
// console.log(letVariable); // 抛出错误：letVariable is not defined

// 2. 提升的区别
console.log(hoistedVar); // 输出：undefined
// console.log(hoistedLet); // 抛出错误：Cannot access 'hoistedLet' before initialization
var hoistedVar = "I am a var variable";
let hoistedLet = "I am a let variable";

// 3. 重新声明的区别
var reDeclareVar = "First var";
var reDeclareVar = "Second var";
// let reDeclareLet = "First let";
// let reDeclareLet = "Second let"; // 抛出错误：Identifier 'reDeclareLet' has already been declared
```

在现代的JavaScript开发中，通常建议使用 `let` 和 `const` 来声明变量，因为它们提供了更加直观和易于理解的作用域规则。而 `var` 由于其一些非直观的行为和问题，正在逐渐被淘汰。