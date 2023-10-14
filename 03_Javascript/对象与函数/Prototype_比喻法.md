# 比喻法

### 故事：图书馆和书籍

想象一下，`prototype`就像一个图书馆里的书籍模板或原型。

在一个小镇上，有一个图书馆，它拥有各种各样的书。有一天，图书馆决定每本书都需要包含一些基本的信息：它的名称、作者、出版日期、以及一个方法`getSummary()`来提供关于这本书的简要信息。

这些基本信息和方法是每本书都应该拥有的，但是为了避免重复在每本书上写下相同的信息和方法，图书馆创建了一个“书的原型（或模板）”。这个“书的原型”包含了上述的基本信息和方法，从而可以被所有的书共享。

在JavaScript的世界中，这个“书的原型”就是`prototype`。我们可以这样理解：

- **书的原型（`prototype`）**：它包含了所有书共享的属性和方法。
  
```javascript
function Book() {}

Book.prototype.name = '';
Book.prototype.author = '';
Book.prototype.publishedDate = '';
Book.prototype.getSummary = function() {
    return `${this.name} 是由 ${this.author} 写的，发表于 ${this.publishedDate}`;
};
```
- **具体的一本书**：它有自己的特定属性（比如：特定的名字、作者等），但它共享在原型上定义的方法和某些属性。

```javascript
let myBook = new Book();
myBook.name = 'JavaScript 101';
myBook.author = 'Coder A';
myBook.publishedDate = '2023';

console.log(myBook.getSummary()); // 输出: "JavaScript 101 是由 Coder A 写的，发表于 2023"
```
在这个案例中，即便`myBook`对象没有`getSummary`方法，它可以使用在`Book.prototype`上定义的`getSummary`，这得益于JavaScript的原型链。

当我们尝试调用`myBook`上的`getSummary`方法时，JavaScript会首先在`myBook`对象上查找这个方法。如果没找到，它会沿着原型链，也就是它会在`Book.prototype`上查找这个方法。由于`Book.prototype`上确实有这个方法，所以`myBook.getSummary()`可以成功调用并返回正确的结果。

希望这个形象的比喻能够帮助初学者更好地理解JavaScript中的`prototype`概念！