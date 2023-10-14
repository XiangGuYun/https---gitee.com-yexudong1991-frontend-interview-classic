# 极简回答

除了比喻，归纳和概述也是很重要的学习方法。

### BFC是什么

BFC（Block Formatting Context）是一种在HTML和CSS中用于布局的概念，它创建了一个独立的容器，其中的元素按照一定规则进行排列和定位，不会影响到外部元素的布局。

### display有哪些值

1. `block`：将元素显示为块级元素，独占一行，默认宽度为父元素宽度，可设置宽高。
2. `inline`：将元素显示为内联元素，不独占一行，宽高由内容决定。
3. `inline-block`：将元素显示为内联块级元素，不独占一行，可设置宽高。
4. `none`：隐藏元素，不占据空间，完全不显示。
5. `flex`：将元素显示为弹性盒子，可通过弹性布局调整元素的排列方式。
6. `grid`：将元素显示为网格容器，可通过网格布局调整元素的排列方式。

### position有哪些值

1. Static（默认）：元素按文档流定位。
2. Relative：相对自身原位置定位。
3. Absolute：相对最近的非static定位祖先定位。
4. Fixed：相对浏览器视口定位，不随滚动。
5. Sticky：基于滚动位置和祖先定位，粘性定位。

### css选择器的优先级

内联样式→ID选择器→类选择器→元素选择器。使用!important可以覆盖所有优先级。

### 清除浮动的方式

1. 使用额外标签方法
2. 使用伪元素::after清除法
3. 给父级添加overflow属性
4. 使用clearfix类
5. 以及flexbox和grid布局自动清除浮动。

### px、em、rem

px是固定像素单位；em相对于父元素的字体大小；rem相对于根元素字体大小的单位。

### 隐藏元素的方式
1. 设置display: none;完全隐藏元素；
2. 用visibility: hidden;使元素不可见但占位；
3. 或应用opacity: 0;使元素透明。
4. 也可用position或transform移出视窗。

### 元素水平居中
1. 设置margin: auto;；
2. text-align: center;对内联元素居中；
3. flexbox的justify-content: center;
4. grid的place-items: center;
5. absolute定位配合left和transform等方法实现。

### 元素垂直居中

垂直居中可用`line-height`等同高度方法，`flexbox`的`align-items: center;`，`grid`的`place-items: center;`，或用`absolute`定位加`top`和`transform`实现。

### 属性继承

属性继承是CSS中的一种机制，允许子元素继承父元素的某些样式属性，如文字颜色、字体大小等，减少样式代码的冗余。

### 重绘和重排

重绘是元素样式改变不影响布局时的重新渲染，重排是元素布局改变需要重新计算元素位置和大小。

### 对盒模型的理解

盒模型是CSS中的布局模型，将元素看作矩形盒子，包括内容、内边距、边框和外边距，用于控制元素在页面上的大小和间距。

### 行内元素和块级元素区别

行内元素在一行内水平排列，不占据整行；块级元素独占一行，可设置宽高，垂直排列。

### margin合并

Margin合并是指相邻块级元素的上下外边距会合并成一个较大的外边距，而不是简单叠加。