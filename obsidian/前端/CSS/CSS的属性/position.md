CSS **`position`** 属性用于指定一个元素在文档中的定位方式。[`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top)，[`right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/right)，[`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom) 和 [`left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/left) 属性则决定了该元素的最终位置。

# [定位类型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E5%AE%9A%E4%BD%8D%E7%B1%BB%E5%9E%8B)

- **定位元素**（positioned element）是其[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `relative`, `absolute`, `fixed` 或 `sticky` 的一个元素（换句话说，除`static`以外的任何东西）。
- **相对定位元素**（relatively positioned element）是[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `relative`的元素。
- **绝对定位元素**（absolutely positioned element）是[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `absolute` 或 `fixed` 的元素。
- **粘性定位元素**（stickily positioned element）是[计算后](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)位置属性为 `sticky` 的元素。

大多数情况下，[`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)和[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 被设定为 auto 的绝对定位元素，按其内容大小调整尺寸。但是，被绝对定位的元素可以通过指定[`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top)和[`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom) ，保留[`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)未指定（即`auto`），来填充可用的垂直空间。它们同样可以通过指定[`left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/left) 和 [`right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/right)并将[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 指定为`auto`来填充可用的水平空间。

```css
.box{

        border: 1px solid aqua;

        height: 300px;

        width: 800px;

        position: relative;

    }

    .box2{

        position:absolute;

        width: auto;

        height: auto;

        top: 150px;

        bottom: 30px;

        left: 400px;

        right: 200px;

        background-color: bisque;

    }
```

```html
<div class="box">

        <div class="box2">

        </div>

    </div>
```

![[Pasted image 20241017101028.png]]
当绝对定位的元素height和width设置为auto时，left和right设置值时，可以将剩余的设为元素的width，height同理。
# [语法](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E8%AF%AD%E6%B3%95)

`position` 属性被指定为从下面的值列表中选择的单个关键字。

## [取值](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E5%8F%96%E5%80%BC)

[`static`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#static)

该关键字指定元素使用正常的布局行为，即元素在文档常规流中当前的布局位置。此时 `top`, `right`, `bottom`, `left` 和 `z-index` 属性无效。

[`relative`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#relative)

该关键字下，元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。position:relative 对 table-*-group, table-row, table-column, table-cell, table-caption 元素无效。

[`absolute`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#absolute)

元素会被移出正常文档流，并不为元素预留空间，通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。

[`fixed`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#fixed)

元素会被移出正常文档流，并不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。元素的位置在屏幕滚动时不会改变。打印时，元素会出现在的每页的固定位置。`fixed` 属性会创建新的层叠上下文。当元素祖先的 `transform`、`perspective`、`filter` 或 `backdrop-filter` 属性非 `none` 时，容器由视口改为该祖先。

[`sticky`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#sticky)

元素根据正常文档流进行定位，然后相对它的_最近滚动祖先_（nearest scrolling ancestor）和 [containing block](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Containing_block)（最近块级祖先 nearest block-level ancestor），包括 table-related 元素，基于 `top`、`right`、`bottom` 和 `left` 的值进行偏移。偏移值不会影响任何其他元素的位置。 该值总是创建一个新的[层叠上下文](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_positioned_layout/Understanding_z-index/Stacking_context)（stacking context）。注意，一个 sticky 元素会“固定”在离它最近的一个拥有“滚动机制”的祖先上（当该祖先的 `overflow` 是 `hidden`、`scroll`、`auto` 或 `overlay` 时），即便这个祖先不是最近的真实可滚动祖先。这有效地抑制了任何“sticky”行为（详情见 [Github issue on W3C CSSWG](https://github.com/w3c/csswg-drafts/issues/865)）。

# [示例](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E7%A4%BA%E4%BE%8B)

## [相对定位](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E7%9B%B8%E5%AF%B9%E5%AE%9A%E4%BD%8D)

相对定位的元素是在文档中的正常位置偏移给定的值，但是不影响其他元素的偏移。

## [绝对定位](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E7%BB%9D%E5%AF%B9%E5%AE%9A%E4%BD%8D)

相对定位的元素并未脱离文档流，而绝对定位的元素则脱离了文档流。在布置文档流中其他元素时，绝对定位元素不占据空间。绝对定位元素相对于_最近的非 `static` 祖先元素_定位。当这样的祖先元素不存在时，则相对于 ICB（initial containing block，初始包含块）。

<font color="#ff0000"> 当元素设置为绝对定位时，元素的默认位置会被别的元素占据。</font>

## [固定定位](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E5%9B%BA%E5%AE%9A%E5%AE%9A%E4%BD%8D)

固定定位与绝对定位相似，但元素的包含块为 viewport 视口。该定位方式常用于创建在滚动屏幕时仍固定在相同位置的元素。

## [粘性定位](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position#%E7%B2%98%E6%80%A7%E5%AE%9A%E4%BD%8D)

粘性定位可以被认为是相对定位和固定定位的混合。元素在跨越特定阈值前为相对定位，之后为固定定位。

