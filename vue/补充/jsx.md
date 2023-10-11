JSX (JavaScript XML)是 JavaScript 的语法扩展，允许以类似 XML 的语法编写 UI 组件，并在编译阶段转换成 JavaScript。

它来自于 Facebook 的一个开源库——React，用于描述 UI 组件的结构和状态。虽然它主要用在 React 中，但其他库也可以使用 JSX。

### 一些特点和概念：
- **语法糖**：JSX 不是一种编程语言，它仅仅是一个语法糖，最终会被转换成 JavaScript 代码。
  
- **声明式语法**：JSX 提供了一种声明式的语法，允许你直观地描述 UI 应该呈现的样子。

- **表达式插入**：你可以在 JSX 中嵌入任何 JavaScript 表达式，方法是把表达式括起来 `{ }`。

### 基本语法和使用：

```jsx
// 使用 JSX 描述 UI 组件
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);

// JSX 被转译为纯 JavaScript
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

### JSX 中的 JavaScript 表达式：
```jsx
// 嵌入变量
const name = 'World';
const element = <h1>Hello, {name}</h1>;

// 嵌入表达式
const element = <h1>{1 + 2}</h1>;
```

### 注意点：
- JSX 产出的是 React 元素，它并不是真实的 DOM 元素，而是存在于虚拟 DOM 系统的一个轻量级表示。

- 由于 JSX 更接近 JavaScript，所以它使用 `className` 而不是 `class`，使用 `htmlFor` 而不是 `for` 等。

- JSX 标签必须被闭合，如果是单标签，也要写成 `<img src="..." />` 的形式。

虽然使用 JSX 不是在使用 React 时的必须条件，但它却能极大地提高在构建 UI 时的开发体验。