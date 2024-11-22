# [计算属性缓存 vs 方法](https://v2.cn.vuejs.org/v2/guide/computed.html#%E8%AE%A1%E7%AE%97%E5%B1%9E%E6%80%A7%E7%BC%93%E5%AD%98-vs-%E6%96%B9%E6%B3%95 "计算属性缓存 vs 方法")
 在Vue.js中，`computed`和`methods`用于处理数据和逻辑，但它们有不同的用途和行为：  
  
## `computed`（计算属性）  
  
- **缓存特性**: 计算属性的结果会被缓存，只有当其依赖的响应式数据发生变化时才会重新计算。这提高了性能，尤其是在复杂计算的情况下。  
    
- **使用场景**: 适用于依赖于其他响应式数据并需要缓存的场景。  
  
- **语法**:  
  
  ```javascript  
  computed: {  
    fullName() {  
      return this.firstName + ' ' + this.lastName;  
    }  
  }  
  ```  
  
## `methods`（方法）  
  
- **无缓存**: 方法在每次调用时都会执行代码，不会缓存结果。  
  
- **使用场景**: 用于事件处理或不需要缓存的逻辑。  
  
- **语法**:  
  
  ```javascript  
  methods: {  
    calculateSum(a, b) {  
      return a + b;  
    }  
  }  
  ```  
  
## 区别总结  
  
- **缓存**: `computed`会缓存结果，`methods`不会。  
- **调用方式**: `computed`属性像数据属性一样使用，而`methods`需要显式调用。  
- **适用场景**: `computed`适合需要依赖响应式数据且需要缓存的场合，`methods`适合处理事件或不需要缓存的逻辑。  
  
# [计算属性 vs 侦听属性](https://v2.cn.vuejs.org/v2/guide/computed.html#%E8%AE%A1%E7%AE%97%E5%B1%9E%E6%80%A7-vs-%E4%BE%A6%E5%90%AC%E5%B1%9E%E6%80%A7 "计算属性 vs 侦听属性")
Vue 提供了一种更通用的方式来观察和响应 Vue 实例上的数据变动：**侦听属性**。当你有一些数据需要随着其它数据变动而变动时，你很容易滥用 `watch`——特别是如果你之前使用过 AngularJS。然而，通常更好的做法是使用计算属性而不是命令式的 `watch` 回调。
  
## 计算属性（Computed Properties）  
  
- **缓存特性**: 计算属性会缓存结果，只有在其依赖的响应式数据发生变化时才会重新计算。  
    
- **适用场景**: 适用于需要根据其他响应式数据进行计算并返回一个结果的场合。  
  
- **语法**:  
  
  ```javascript  
  computed: {  
    fullName() {  
      return this.firstName + ' ' + this.lastName;  
    }  
  }  
  ```  
  
- **优点**: 通过缓存提高性能，适合用于模板中的复杂计算。  
  
## 侦听属性（Watchers）  
  
- **无缓存**: 侦听属性不缓存结果，每次数据变化时都会执行指定的回调函数。  
  
- **适用场景**: 适用于需要在数据变化时执行异步操作或复杂逻辑的场合，如API调用、手动 DOM 操作等。  
  
- **语法**:  
  
  ```javascript  
  watch: {  
    firstName(newVal, oldVal) {  
      console.log(`First name changed from ${oldVal} to ${newVal}`);  
    }  
  }  
  ```  
  
- **优点**: 灵活性高，可以执行复杂的逻辑和异步操作。  
  
## 区别总结  
  
- **缓存**: 计算属性会缓存结果，侦听属性不会。  
- **用途**: 计算属性适合用于模板中的计算，侦听属性适合处理数据变化时的副作用。  
- **复杂性**: 侦听属性更适合处理复杂的逻辑和异步操作。
# [绑定 HTML Class](https://v2.cn.vuejs.org/v2/guide/class-and-style.html#%E7%BB%91%E5%AE%9A-HTML-Class "绑定 HTML Class")
## [用在组件上](https://v2.cn.vuejs.org/v2/guide/class-and-style.html#%E7%94%A8%E5%9C%A8%E7%BB%84%E4%BB%B6%E4%B8%8A "用在组件上")
当在一个自定义组件上使用 `class` property 时，这些 class 将被添加到该组件的根元素上面。这个元素上已经存在的 class 不会被覆盖。
# [绑定内联样式](https://v2.cn.vuejs.org/v2/guide/class-and-style.html#%E7%BB%91%E5%AE%9A%E5%86%85%E8%81%94%E6%A0%B7%E5%BC%8F "绑定内联样式")
## [对象语法](https://v2.cn.vuejs.org/v2/guide/class-and-style.html#%E5%AF%B9%E8%B1%A1%E8%AF%AD%E6%B3%95-1 "对象语法")

`v-bind:style` 的对象语法十分直观——看着非常像 CSS，但其实是一个 JavaScript 对象。CSS property 名可以用驼峰式 (camelCase) 或短横线分隔 (kebab-case，记得用引号括起来) 来命名：

直接绑定到一个样式对象通常更好，这会让模板更清晰：

同样的，对象语法常常结合返回对象的计算属性使用。

## [数组语法](https://v2.cn.vuejs.org/v2/guide/class-and-style.html#%E6%95%B0%E7%BB%84%E8%AF%AD%E6%B3%95-1 "数组语法")

`v-bind:style` 的数组语法可以将多个样式对象应用到同一个元素上：


## [自动添加前缀](https://v2.cn.vuejs.org/v2/guide/class-and-style.html#%E8%87%AA%E5%8A%A8%E6%B7%BB%E5%8A%A0%E5%89%8D%E7%BC%80 "自动添加前缀")

当 `v-bind:style` 使用需要添加[浏览器引擎前缀](https://developer.mozilla.org/zh-CN/docs/Glossary/Vendor_Prefix)的 CSS property 时，如 `transform`，Vue.js 会自动侦测并添加相应的前缀。

## [多重值](https://v2.cn.vuejs.org/v2/guide/class-and-style.html#%E5%A4%9A%E9%87%8D%E5%80%BC "多重值")

> 2.3.0+

从 2.3.0 起你可以为 `style` 绑定中的 property 提供一个包含多个值的数组，常用于提供多个带前缀的值，例如：


这样写只会渲染数组中最后一个被浏览器支持的值。在本例中，如果浏览器支持不带浏览器前缀的 flexbox，那么就只会渲染 `display: flex`。

# 条件渲染
## [用 `key` 管理可复用的元素](https://v2.cn.vuejs.org/v2/guide/conditional.html#%E7%94%A8-key-%E7%AE%A1%E7%90%86%E5%8F%AF%E5%A4%8D%E7%94%A8%E7%9A%84%E5%85%83%E7%B4%A0 "用 key 管理可复用的元素")

Vue 会尽可能高效地渲染元素，通常会复用已有元素而不是从头开始渲染。这么做除了使 Vue 变得非常快之外，还有其它一些好处。例如，如果你允许用户在不同的登录方式之间切换：

那么在上面的代码中切换 `loginType` 将不会清除用户已经输入的内容。因为两个模板使用了相同的元素，`<input>` 不会被替换掉——仅仅是替换了它的 `placeholder`。

这样也不总是符合实际需求，所以 Vue 为你提供了一种方式来表达“这两个元素是完全独立的，不要复用它们”。只需添加一个具有唯一值的 `key` attribute 即可：

## [`v-if` vs `v-show`](https://v2.cn.vuejs.org/v2/guide/conditional.html#v-if-vs-v-show "v-if vs v-show")

`v-if` 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。

`v-if` 也是**惰性的**：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。

相比之下，`v-show` 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。

一般来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 `v-show` 较好；如果在运行时条件很少改变，则使用 `v-if` 较好。

## [`v-if` 与 `v-for` 一起使用](https://v2.cn.vuejs.org/v2/guide/conditional.html#v-if-%E4%B8%8E-v-for-%E4%B8%80%E8%B5%B7%E4%BD%BF%E7%94%A8 "v-if 与 v-for 一起使用")

**不推荐**同时使用 `v-if` 和 `v-for`。请查阅[风格指南](https://v2.cn.vuejs.org/v2/style-guide/#%E9%81%BF%E5%85%8D-v-if-%E5%92%8C-v-for-%E7%94%A8%E5%9C%A8%E4%B8%80%E8%B5%B7-%E5%BF%85%E8%A6%81)以获取更多信息。

当 `v-if` 与 `v-for` 一起使用时，`v-for` 具有比 `v-if` 更高的优先级。请查阅[列表渲染指南](https://v2.cn.vuejs.org/v2/guide/list.html#v-for-with-v-if)以获取详细信息。