---

title: JavaScript 模块
date: 2021-10-12 09:43
tags: [JavaScript]

---

## 一、什么是JavaScript模块

将大功能拆分成小功能。一个小功能就是一个模块。

## 二、import和 export

JavaScript 模块依赖于import和 export。

<!--more-->

### 2.1 导出模块的功能

#### 2.1.1 命名导出

-   方法1 在需要导出的功能前加export

```
export const name = "xiaoming";
export const getNumber=()=>{
	return 333;
}
```
-   方法2 在模块文件的末尾使用一个export 语句

```
const name = "xiaoming";
const getNumber=()=>{
	return 333;
}

export{
	name,
	getNumber,
}
```

#### 2.1.2 默认导出(一个模块只能有一个)

```
const name = "xiaoming";
const getNumber=()=>{
	return 333;
}
export{
	getNumber,
}
export default{
	name,
	getNumber
}
```

### 2.2 向JavaScript脚本文件导入模块

-   方法1 导入全部功能

```
import * as m1 from "./m1.js";
console.log(m1.name)
```

-   方法2 导入多个功能

```
import {name,getNumber} from "./m1.js";
console.log(name)
var a = getNumber();
console.log(a)
```

-   方法2 已别名方式导入多个功能

```
import {name as n,getNumber as g} from "./m1.js";
console.log(n)
var a = g();
console.log(a)
```

-   方法3 作为副作用导入  
    (副作用：  
    执行全局代码，但不导入任何值。  
    可以理解为模块中会直接运行的代码。  
    原则上来说，模块不能有副作用。)

```
//m1.js
const name = "xiaoming";
const getNumber=()=>{
	return 333;
}

console.log("副作用")

export{
	name,
	getNumber,
}

//main.js
import "./m1.js";
```

-   方法4 导入默认值

```
//m1.js
const name = "xiaoming";
export default{
	name
}

//main.js
import de from "./m1.js";
console.log(de.name)
```

-   方法5.1 默认导入+命名导入

```
//m1.js
const name = "xiaoming";
const getNumber=()=>{
	return 333;
}
export{
	getNumber,
}
export default{
	name,
	getNumber
}

//de:默认导入
//myDe:命名导入
import de, * as myDe from "./m1.js";
console.log(de.name)
console.log(myDe.getNumber())
```

-   方法5.2 默认导入+命名导入

```
//de:默认导入
//myDe:命名导入
import de, {getNumber} from "./m1.js";
console.log(de.name)
console.log(getNumber())
```

### 2.3 应用模块到HTML

现在，main.js的引入与普通脚本的引入不同：

```
//type="module" 声明main是一个模块
<script type="module" src="main.js"></script>
```

只能在模块内部使用 import 和export 语句

## 三、动态import、静态import

### 3.1 静态import

上边的就是静态import，会在加载时就被编译，降低首页加载速度。

### 3.2 动态import:import()

-   方法1 返回promise

```
import("./m1.js")
.then(m=>{
	console.log(m.getNumber())
})
```

-   方法2 await

```
let m = await import("./m1.js");
console.log(m.getNumber())
```

## 参考

1.  [JavaScript modules 模块 - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules)

2.  [import - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/import)

3.  [export - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/export)