# Attribute和Property
## Attribute  
- **定义**: HTML标签上的属性，通常在HTML中以字符串形式定义。  
- **获取/设置**: 通过`getAttribute()`和`setAttribute()`方法进行操作。  
- **作用**: 描述初始的HTML属性值。  
- **示例**:  
  ```html  
  <input type="text" value="Hello">  
  ```  
  ```javascript  
  const input = document.querySelector('input');  
  console.log(input.getAttribute('value')); // 输出 "Hello"  
  ```  
  
## Property  
  
- **定义**: DOM对象的属性，是JavaScript对象的特性。  
- **获取/设置**: 通过直接访问或赋值操作。  
- **作用**: 描述当前的状态和行为，可能会随用户交互而改变。  
- **示例**:  
  ```javascript  
  const input = document.querySelector('input');  
  console.log(input.value); // 输出当前输入框的值  
  input.value = "World"; // 改变输入框的值  
  ```
 
# 什么是事件
在JavaScript中，事件（Event）是一个非常重要的概念，它代表了文档或浏览器中发生的特定交互或动作。当用户与网页进行交互时（如点击按钮、提交表单、移动鼠标等），或者当网页加载完成、脚本执行等特定情况发生时，浏览器就会生成一个事件。

事件通常与事件监听器（或称为事件处理程序、事件处理器）一起使用。事件监听器是一个指定了当事件发生时应该执行哪些操作的函数或方法。开发者可以通过JavaScript将事件监听器附加到文档中的元素上，以响应用户的交互或其他事件。

事件对象（Event Object）是与每个事件相关联的信息集合。当事件发生时，浏览器会创建一个事件对象，并包含有关事件的详细信息，如事件类型（如`click`、`load`、`mouseover`等）、触发事件的元素、事件发生的时间等。事件对象作为参数传递给事件监听器函数，使开发者能够访问这些信息并据此编写逻辑。

JavaScript中的事件机制是基于观察者模式的。在这种模式中，对象（在这里是DOM元素）会维持一个或多个依赖于它的观察者（在这里是事件监听器），并在状态发生变化时自动通知它们。在Web开发中，这允许DOM元素在发生特定事件时通知JavaScript代码，从而创建动态和交互式的网页。

事件类型有很多，包括但不限于：

- 鼠标事件（如`click`、`dblclick`、`mouseover`、`mouseout`等）
- 键盘事件（如`keydown`、`keypress`、`keyup`等）
- 表单事件（如`submit`、`change`、`focus`、`blur`等）
- 窗口事件（如`load`、`resize`、`scroll`等）
- 剪贴板事件（如`copy`、`cut`、`paste`等）
- 拖放事件（如`dragstart`、`drag`、`dragenter`、`dragleave`、`dragover`、`drop`、`dragend`等）

# 命名方式

[风格指南](https://v2.cn.vuejs.org/v2/style-guide/#%E5%9F%BA%E7%A1%80%E7%BB%84%E4%BB%B6%E5%90%8D-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)

## 组件的命名方式
在注册一个组件的时候，我们始终需要给它一个名字。比如在全局注册的时候我们已经看到了：
```js
Vue.component('my-component-name', { /* ... */ })
```
当直接在 DOM 中使用一个组件 (而不是在字符串模板或[单文件组件](https://v2.cn.vuejs.org/v2/guide/single-file-components.html)) 的时候，我们强烈推荐遵循 [W3C 规范](https://html.spec.whatwg.org/multipage/custom-elements.html#valid-custom-element-name)中的自定义组件名 (字母全小写且必须包含一个连字符)。这会帮助你避免和当前以及未来的 HTML 元素相冲突。
## Prop

### [Prop 的大小写 (camelCase vs kebab-case)](https://v2.cn.vuejs.org/v2/guide/components-props.html#Prop-%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%86%99-camelCase-vs-kebab-case "Prop 的大小写 (camelCase vs kebab-case)")

HTML 中的 attribute 名是大小写不敏感的，所以浏览器会把所有大写字符解释为小写字符。这意味着当你使用 DOM 中的模板时，camelCase (驼峰命名法) 的 prop 名需要使用其等价的 kebab-case (短横线分隔命名) 命名：

```js
Vue.component('blog-post', {  // 在 JavaScript 中是 camelCase 的  props: ['postTitle'],  template: '<h3>{{ postTitle }}</h3>'})
```

```html
<!-- 在 HTML 中是 kebab-case 的 -->  
<blog-post post-title="hello!"></blog-post>
```

