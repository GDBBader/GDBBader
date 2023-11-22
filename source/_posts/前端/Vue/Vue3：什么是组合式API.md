---


title: Vue3：什么是组合式API
date: 2021-09-01 15:22
tags: [vue,JavaScript]
type:

---


## 一、什么是组合式API

简单理解就是：在`setup`中写的就是组合式API。

与组合式API（vue3）相对的是**选项式 API**（vue2）。

<-- more -->
如下（vue2）,使用 (`data`、`computed`、`methods`、`watch`) 组件选项来组织逻辑，当项目过大时，这种碎片化使得理解和维护复杂组件变得困难。**逻辑关注点**过于分离。
![[options-api.png]]

组合式API就是：你按照以下的写法来组织代码我（vue3）就能理解（以下内容是写在setup函数内的）

```javascript

//逻辑关注点1
const data1;
const methods1 = ()=>{}
watch(()=>data1,()=>{})

//逻辑关注点2
const data2;
const methods2 = ()=>{}
watch(()=>data2,()=>{})

//逻辑关注点3
const data3;
const methods3 = ()=>{}
watch(()=>data3,()=>{})
```


## 二、setup

```javascript
//setup函数
export default {
  components: { RepositoriesFilters, RepositoriesSortBy, RepositoriesList },
  props: {
    user: {
      type: String,
      required: true
    }
  },
  setup(props) {
    console.log(props) // { user: '' }

    return {} // 这里返回的任何内容都可以用于组件的其余部分
  }
  // 组件的“其余部分”
}
```

注意：

- 在 `setup` 中应该避免使用 `this`，因为它不会找到组件实例。因为 `setup()` 是在解析其它组件选项之前被调用的，所以 `setup()` 内部的 `this` 的行为与其它选项中的 `this` 完全不同。[Setup | Vue.js](https://v3.cn.vuejs.org/guide/composition-api-setup.html#%E4%BD%BF%E7%94%A8-this)
- `setup` 的调用发生在 `data` property、`computed` property 或 `methods` 被解析之前，所以它们无法在 `setup` 中被获取。
- `setup` 返回的所有内容都暴露给组件的其余部分 (计算属性、方法、生命周期钩子等等) 以及组件的模板。

> 执行 `setup` 时，组件实例尚未被创建。因此，你只能访问以下 property：
-   `props`
-   `attrs`
-   `slots`
-   `emit`
换句话说，你**将无法访问**以下组件选项：
-   `data`
-   `computed`
-   `methods`


[Setup | Vue.js](https://v3.cn.vuejs.org/guide/composition-api-setup.html#%E8%AE%BF%E9%97%AE%E7%BB%84%E4%BB%B6%E7%9A%84-property)

> 如果 `setup` 返回一个对象，那么该对象的 property 以及传递给 `setup` 的 `props` 参数中的 property 就都可以在模板中访问到[Setup | Vue.js](https://v3.cn.vuejs.org/guide/composition-api-setup.html#%E7%BB%93%E5%90%88%E6%A8%A1%E6%9D%BF%E4%BD%BF%E7%94%A8)



## 三、setup中的data需要是响应式的


### 方法1 ：ref函数

ref函数返回的是一个对象（JS中对象是引用类型）。

> 接受一个内部值并返回一个响应式且可变的 ref 对象。ref 对象具有指向内部值的单个 property `.value`。


```javascript
import { ref } from 'vue'

const counter = ref(0)

console.log(counter) // { value: 0 }
console.log(counter.value) // 0

counter.value++
console.log(counter.value) // 1
```

> `reactive` 将解包所有深层的 [refs](https://v3.cn.vuejs.org/api/refs-api.html#ref)，同时维持 ref 的响应性。
[响应性基础 API | Vue.js](https://v3.cn.vuejs.org/api/basic-reactivity.html#reactive)


理解：烧脑，看起来就是比ref少使用了value。


### 方法2：reactive 函数

> 返回对象的响应式副本。


> `reactive` 将解包所有深层的 [refs](https://v3.cn.vuejs.org/api/refs-api.html#ref)，同时维持 ref 的响应性。


> 当将 [ref](https://v3.cn.vuejs.org/api/refs-api.html#ref) 分配给 `reactive` property 时，ref 将被自动解包。


[响应性基础 API | Vue.js](https://v3.cn.vuejs.org/api/basic-reactivity.html#%E5%93%8D%E5%BA%94%E6%80%A7%E5%9F%BA%E7%A1%80-api)

```javascript
import { reactive } from 'vue'

// 响应式状态
const state = reactive({
  count: 0
})
```

烧脑：

> 这就是 Vue 响应性系统的本质。当从组件中的 `data()` 返回一个对象时，它在内部交由 `reactive()` 使其成为响应式对象。模板会被编译成能够使用这些响应式 property 的[渲染函数](https://v3.cn.vuejs.org/guide/render-function.html)。
[响应性基础 | Vue.js](https://v3.cn.vuejs.org/guide/reactivity-fundamentals.html#%E5%A3%B0%E6%98%8E%E5%93%8D%E5%BA%94%E5%BC%8F%E7%8A%B6%E6%80%81)



## 参考

1. [介绍 | Vue.js](https://v3.cn.vuejs.org/guide/composition-api-introduction.html#%E7%BB%84%E5%90%88%E5%BC%8F-api-%E5%9F%BA%E7%A1%80)
2. [Refs | Vue.js](https://v3.cn.vuejs.org/api/refs-api.html#isref)
