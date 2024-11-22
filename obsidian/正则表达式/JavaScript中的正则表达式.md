# 概述
正则表达式（regular expression）是一种表达文本模式（即字符串结构）的方法，有点像字符串的模板，常常用来按照“给定模式”匹配文本。比如，正则表达式给出一个 Email 地址的模式，然后用它来确定一个字符串是否为 Email 地址。

新建正则表达式有两种方法。一种是使用字面量，以斜杠表示开始和结束。
```JavaScript
var regex = /xyz/;
```
另一种是使用`RegExp`构造函数。
```JavaScript
var regex = new RegExp('xyz');
```
上面两种写法是等价的，都新建了一个内容为`xyz`的正则表达式对象。它们的主要区别是，第一种方法在引擎编译代码时，就会新建正则表达式，第二种方法在运行时新建正则表达式，所以前者的效率较高。而且，前者比较便利和直观，所以实际应用中，基本上都采用字面量定义正则表达式。

`RegExp`构造函数还可以接受第二个参数，表示修饰符（详细解释见下文）。
```Java
var regex = new RegExp('xyz', 'i');
// 等价于
var regex = /xyz/i;
```

上面代码中，正则表达式`/xyz/`有一个修饰符`i`。

# 实例属性
正则对象的实例属性分成两类。

一类是修饰符相关，用于了解设置了什么修饰符。

- `RegExp.prototype.ignoreCase`：返回一个布尔值，表示是否设置了`i`修饰符。
- `RegExp.prototype.global`：返回一个布尔值，表示是否设置了`g`修饰符。
- `RegExp.prototype.multiline`：返回一个布尔值，表示是否设置了`m`修饰符。
- `RegExp.prototype.flags`：返回一个字符串，包含了已经设置的所有修饰符，按字母排序。

上面四个属性都是只读的。
```JavaScript
var r = /abc/igm;

r.ignoreCase // true
r.global // true
r.multiline // true
r.flags // 'gim'
```
另一类是与修饰符无关的属性，主要是下面两个。

- `RegExp.prototype.lastIndex`：返回一个整数，表示下一次开始搜索的位置。该属性可读写，但是只在进行连续搜索时有意义，详细介绍请看后文。
- `RegExp.prototype.source`：返回正则表达式的字符串形式（不包括反斜杠），该属性只读。

```JavaScript
var r = /abc/igm;

r.lastIndex // 0
r.source // "abc"
```

# 实例方法

