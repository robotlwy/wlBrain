# 基本的数据类型
本页试图用简单的语言描述各种对象和类型。但是，有一些不同的数据类型在 API 中传递，你应该注意到。

**备注** 因为绝大多数使用 DOM 的代码都是围绕着操作 HTML 文档进行的，所以我们通常把 DOM 中的节点称为**元素**（element），尽管严格来说并不是每个节点都是一个元素。

下面的表格大致描述了这些数据类型。

|数据类型（接口）|描述|
|---|---|
|[`Document`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document)|当一个成员返回 `document` 对象（例如，元素的 `ownerDocument` 属性返回它所属的 `document`），这个对象就是 root `document` 对象本身。[DOM `document` 参考](https://developer.mozilla.org/zh-CN/docs/Web/API/Document)一章对 `document` 对象进行了描述。|
|[`Node`](https://developer.mozilla.org/zh-CN/docs/Web/API/Node)|位于文档中的每个对象都是某种类型的节点。在一个 HTML 文档中，一个对象可以是一个元素节点，也可以是一个文本节点或属性节点。|
|[`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element)|`element` 类型是基于 `node` 的。它指的是一个元素或一个由 DOM API 的成员返回的 `element` 类型的节点。例如，我们不说 [`document.createElement()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createElement) 方法返回一个 `node` 的对象引用，而只是说这个方法返回刚刚在 DOM 中创建的 `element`。`element` 对象实现了 DOM 的 `Element` 接口和更基本的 `Node` 接口，这两个接口都包含在本参考中。在 HTML 文档中，元素通过 HTML DOM API 的 [`HTMLElement`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLElement) 接口以及其他描述特定种类元素能力的接口（例如用于 [`<table>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/table) 元素的 [`HTMLTableElement`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLTableElement) 接口）进一步强化。|
|[`NodeList`](https://developer.mozilla.org/zh-CN/docs/Web/API/NodeList)|`nodeList` 是由元素组成的数组，如同 [`document.querySelectorAll()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelectorAll) 等方法返回的类型。`nodeList` 中的条目通过索引有两种方式进行访问：<br><br>- list.item(1)<br>- list[1]<br><br>两种方式是等价的，第一种方式中 `item()` 是 `nodeList` 对象中的单独方法。后面的方式则使用了经典的数组语法来获取列表中的第二个条目。|
|[`Attr`](https://developer.mozilla.org/zh-CN/docs/Web/API/Attr)|当 `attribute` 通过成员函数（例如通过 `createAttribute()` 方法）返回时，它是一个为属性暴露出专门接口的对象引用。DOM 中的属性也是节点，就像元素一样，只不过你可能会很少使用它。|
|[`NamedNodeMap`](https://developer.mozilla.org/zh-CN/docs/Web/API/NamedNodeMap)|`namedNodeMap` 和数组类似，但是条目是由名称或索引访问的，虽然后一种方式仅仅是为了枚举方便，因为在 list 中本来就没有特定的顺序。出于这个目的， `namedNodeMap` 有一个 item() 方法，你也可以从 `namedNodeMap` 添加或移除条目。|

还有一些常见的术语需要记住。例如，通常把任何 [`Attr`](https://developer.mozilla.org/zh-CN/docs/Web/API/Attr) 节点称为 `attribute`，把 DOM 节点组成的数组称为 `nodeList`。你会发现这些术语和其他术语将在整个文档中被介绍和使用。