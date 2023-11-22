---

title: bind()如何使用
date: 2023-05-25 00:05
tags: [JavaScript]

---
`bind()`方法可以用于绑定函数中的`this`关键字，并返回一个新的函数。

`bind()`方法的语法如下：

```
function.bind(thisArg[, arg1[, arg2[, ...]]])
```

其中，`thisArg`参数是`bind()`方法中要绑定到函数中的`this`关键字的值。如果这个参数为`null`或`undefined`，则会使用全局对象代替。

除了`thisArg`参数外，我们还可以在`bind()`方法中传入一些参数，这些参数会被绑定到函数的参数列表中，并返回一个新函数。

举个例子，假设我们有一个名为`multiply`的函数，它接受两个参数并返回它们的乘积。我们可以使用`bind()`方法来绑定函数中的第一个参数为`2`，并返回一个新函数`double`，这个新函数只需要一个参数，就可以计算出原始函数`multiply`中的第二个参数和这个参数的乘积：

```
function multiply(a, b) {
  return a * b;
}

const double = multiply.bind(null, 2); // 返回一个新函数
console.log(double(5)); // 输出10
```

在上面的代码中，我们使用`bind()`方法将`multiply`函数中的第一个参数绑定为`2`，并返回一个新函数`double`。这个新函数只需要一个参数，就可以计算出原始函数`multiply`中的第二个参数和这个参数的乘积。