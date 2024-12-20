[CSS 重要概念：视觉格式化模型 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/679883474)
CSS **视觉格式化模型**（visual formatting model）是用来处理和在视觉媒体上显示文档时使用的计算规则。该模型是 CSS 的基础概念之一。

视觉格式化模型会根据 [CSS 盒子模型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model)将文档中的元素转换为一个个盒子，每个盒子的布局由以下因素决定：

- 盒子的尺寸：精确指定、由约束条件指定或没有指定
- 盒子的类型：行内盒子（inline）、行内级盒子（inline-level）、原子行内级盒子（atomic inline-level）、块盒子（block）
- [定位方案（positioning scheme）](https://developer.mozilla.org/zh-CN/docs/CSS/Box_positioning_scheme "This is a link to an unwritten page")：普通流定位、浮动定位或绝对定位
- 文档树中的其他元素：即当前盒子的子元素或兄弟元素
- [视口](https://developer.mozilla.org/zh-CN/docs/Glossary/Viewport)尺寸与位置
- 所包含的图片的尺寸
- 其他的某些外部因素

该模型会根据盒子的包含块（_containing block_）的边界来渲染盒子。通常，盒子会创建一个包含其后代元素的包含块，但是盒子并不由包含块所限制，当盒子的布局跑到包含块的外面时称为溢出（_overflow）_。

# 元素的定位体系

任何一个元素，必须属于其中一种定位体系。
定位体系有三种：常规流（normal flow）、浮动（float）、绝对定位（absolute positioned）。

| `开始→position的值是absolute或``fixed``?→否→``float``的值是left或right？→否`<br><br>                                                          ↓                         ↓                                                                 ↓<br><br>                                                          是                         是                                                            常规流<br><br>                                                          ↓                         ↓             <br><br>                                                    绝对定位                浮动 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
## 常规流
>又叫普通流、文档流、普通文档流。
>盒模型中的auto值：块级元素在常规流定位体系中尺寸取值为自动值的时候计算尺寸方式如下： 
>>①水平方向： - 常规流盒子水平方向上的尺寸，必须等于包含块的宽度。
>>>块级元素在常规流中水平居中的方法：一是给块级元素一个固定宽值，二是margin的左和右设置为auto。这样就可以水平自动居中。
>>>当左右外边距和width都是固定，无法满足包含块的宽度时，则右外边距会被强制改成auto，从未撑满包含块的宽度。
>>②垂直方向： - margin为auto时，垂直方向上为0px。
>>>height为auto时，适应内容的宽度。
>>>若两个外边距相邻，则进行合并（折叠）：当都是正值时，取最大值；当都是负值时，取最小值；当两个数一正一负时，取相加。
>>>若外边距取负值时，可调整标签的位置，即两个标签可以相互重叠。

## 浮动
当元素的float属性取值为left或right时，元素属于浮动定位。
### 盒模型中的auto值

| 属性                 | 常规流     | 浮动     |
| ------------------ | ------- | ------ |
| margin-left:auto   | 尽量撑满包含块 | 0px    |
| margin-right:auto  | 尽量撑满包含块 | 0px    |
| margin-top:auto    | 0px     | 0px    |
| margin-bottom:auto | 0px     | 0px    |
| width:auto         | 尽量撑满包含块 | 适应内容宽度 |
| height:auto        | 适应内容高度  | 适应内容高度 |
### 盒子的位置
- 左浮动的盒子：先向上再向左排列。
- 右浮动的盒子：先向上再向右排列。
- 浮动盒子的顶边不得高于上一个盒子的顶边。
- 若剩余空间无法放下浮动的盒子，则该盒子向下移动，直到具备足够的空间能容纳盒子，然后再向左或向右移动。
### 当常规流遇上浮动
- 浮动盒子在摆放时，要避开常规流盒子。
- 常规流盒子在摆放时，无视浮动盒子。
- 浮动盒子脱离文档流，子级元素浮动时、父级元素高度塌陷。
### 清除浮动（解决高度塌陷）
对一个元素，清除浮动，可以让该元素在摆放时，出现在浮动元素的下方。
```css
header:after{         在header元素里创建的最后一个元素
content:``""``;       元素内容为空
display:block;        改为块级元素
clear:both;}          清除左右浮动
```
通过以上方法，将父级元素的高度计算至最底边。
### clear取值-不可继承
none（默认值）：不清除浮动
left：清除左浮动，元素在左浮动的盒子下方摆放。
right：清除右浮动，元素在右浮动的盒子下方摆放。
both：清除左右浮动，元素在左右浮动的盒子下方摆放。
## 绝对定位体系
### 盒子的相对位置
- 指相对于盒子在原来定位体系下的位置。
       - 不会脱离文档流。
       - 将盒子的position属性设置成ralative，以启用相对位置。
              - position属性：不可继承。
              - static（默认）：静态位置（原本位置）。
              - relative：相对位置，盒子相对原本的位置进行便偏移。
              - absolute：绝对位置。
              - fixed：固定位置。
 - 盒子偏移后，不会对其他盒子位置造成影响，但可能出现覆盖其他内容的情况。
        - 以下情况可用相对位置：
               - 原有位置需要继续占用时。
               - 盒子间需要重叠的时候。
### 绝对定位 
       -当浮动元素被设置为绝对定位，float属性会被强制设置为none。
        - 绝对定位不会对其他腾和元素造成任何影响，而且不占原来的位置。
        - 绝对定位可通过left、top、right、bottom来设置。
         ①固定位置（position:fixed）
        - 固定位置根据相对视口的偏移量来变化，要脱离文档流。
        - 一般在形成重叠时使用。
        - 代码所在位置先后对固定位置的标签没有影响，故一般写到body结束标签前。
        ②绝对位置（position:absolute）
        `子元素起始位置判断：`
`position:absolute`
        `↓`
`从里往外依次判断元素是否`
`拥有position≠``static``的  → 否 → 初始化包含块左上角开始（即视口左上角）`
`祖先元素（离得最近的上级）`
       `↓`
       `是`
       `↓`
 `从该元素的填充盒开始`
# 盒模型中的尺寸：

- em：取父级元素的倍数。例如：font-size：2em；表示取父级元素font-size的2倍。
- rem：取根元素的倍数。
- %：百分率，表示取父级元素的宽度的百分比。
- auto：自动，一般来说，是元素内容所占的宽度。
- 盒模型中的尺寸-%：表示尺寸是包含块尺寸的百分比。
- margin、padding、width的百分比：指包含块宽度的百分比。
- height（很少用）。
- 盒模型中的auto：尺寸收到定位体系的影响，不同定位体系，auto的计算规则不一样。
- margin的取值可取负值，这样两个盒子就形成重叠。

# 术语解释
## 块
block，一个抽象的概念，一个块在文档流上占据一个独立的区域，块与块之间在垂直方向上按照顺序依次堆叠（默认情况之下）。
## 包含块
containing block，包含其他盒子的块称为包含块。

> he position and size of an element's box(es) are sometimes calculated relative to a certain rectangle, called the containing block of the element.

大至意思是，盒子的定位和大小都是参考一个矩形边缘来计算的，而这个矩形就是元素的容器块。

一个元素的容器块大概定义如下：

- 首先根元素就是一个初始容器块（Initial Containing Block）
- 其次，如果元素的 `position`是 `relative`或`static`，其容器块就是由离它最近的块容器父元素或创建了一个格式化上下文的父级元素生成
- 如果元素设置了`position:fixed`，它的容器块一般由视窗生成
- 如果元素设置了`position:absolute`，它的容器块就由设置了`position`值为`relative`、`absolute`或`fixed`的最近父元素生成，如果父级元素都没有设置，则由根元素生成
- `transform`属性值为非`none`的元素会生成一个容器块，其`fixed`的子元素会以此定位


## 盒子
box，一个抽象的概念，由 CSS 引擎根据文档中的内容所创建，主要用于文档元素的定位、布局和格式化等用途。盒子与元素并不是一一对应的，有时多个元素会合并生成一个盒子，有时一个元素会生成多个盒子（如匿名盒子）。
## 块级元素
block-level element，元素的 `display` 为 `block`、`list-item`、`table` 时，该元素将成为块级元素。元素是否是块级元素仅是元素本身的属性，并不直接用于格式化上下文的创建或布局。
## 块级盒子
block-level box，由块级元素生成。一个块级元素至少会生成一个块级盒子，但也有可能生成多个（例如列表项元素）。
## 块盒子
block box，如果一个块级盒子同时也是一个块容器盒子（见下），则称其为块盒子。除具名块盒子之外，还有一类块盒子是匿名的，称为匿名块盒子（Anonymous block box），匿名盒子无法被 CSS 选择符选中。
## 块容器盒子
block container box 或 block containing box，块容器盒子侧重于当前盒子作为“容器”的这一角色，它不参与当前块的布局和定位，它所描述的仅仅是当前盒子与其后代之间的关系。换句话说，块容器盒子主要用于确定其子元素的定位、布局等。

注意：盒子分为“块盒子”和“块级盒子”两种，但元素只有“块级元素”，而没有“块元素”。下面的“行内级元素”也是一样。

## 行内级元素
inline-level element，`display` 为 `inline`、`inline-block`、`inline-table` 的元素称为行内级元素。与块级元素一样，元素是否是行内级元素仅是元素本身的属性，并不直接用于格式化上下文的创建或布局。
## 行内级盒子
inline-level box，由行内级元素生成。同样的，一个行内元素至少会生成一个行内级盒子。行内级盒子包括行内盒子和原子行内级盒子两种，区别在于该盒子是否参与行内格式化上下文的创建。

<font color="#ff0000">注：简单地说，块元素生成块组盒子，行内元素或行内级元素生成行内级盒子。两种盒子可以通过`display`来进行切换。</font>

### 行内盒子
 inline box，参与行内格式化上下文创建的行内级盒子称为行内盒子。与块盒子类似，行内盒子也分为具名行内盒子和匿名行内盒子（anonymous inline box）两种。
### 原子行内级盒子
atomic inline-level box，不参与行内格式化上下文创建的行内级盒子。原子行内级盒子一开始叫做原子行内盒子（atomic inline box），后被修正。原子行内级盒子的内容不会拆分成多行显示。

<font color="#ff0000">视觉格式化模型中的盒子和 CSS 中盒模型指的盒子是不是同一个盒子？</font>

>**盒子是同一个盒子，但两个模型做着不同的事情。CSS 的盒模型是计算盒子尺寸（_`width`、`height`、`padding`、`border`和`margin`来决定_）；视觉格式化模型是用来计算盒子位置（由前面提到的七个因素来决定）！

# 格式化上下文
默认情况下，盒子按照元素**在 HTML 中的先后位置从左至右自上而下依次堆叠**
![[Pasted image 20241016175457.png]]
从图中可以看出来，有些元素的盒子被渲染为完整的一行，比如 `h1`、`li` 等元素；有些元素的盒子则被渲染为水平排列的，直到该行被占满然后换行，比如 `em`、`strong` 等元素。

这是因为不同的盒子使用的是不同的格式化上下文（Formatting Context）来布局，每个格式化上下文都拥有自己不同的渲染规则，而这些规则是用来决定其子元素如何定位，以及和其他元素的关系。

在CSS中格式化上下文有很多种，比如**IFC（Inline Formatting Context）**、**BFC（Block Formatting Context）**、**FFC（Flexbox Formatting Context）** 和 **GFC（Grid Formatting Contexgt）** 等。而这些格式化上下文的集合可以称作**视觉格式化模型**。

# 盒子的生成
盒子的生成是 CSS 视觉格式化模型的一部分，用于从文档元素生成盒子。盒子有不同的类型，不同类型的盒子的格式方法也有所不同，不同的盒子也会影响元素或其后代元素的行为。在 CSS 中，通常使用 `display` 属性来明确盒子的类型。

CSS 的 `display` 属性的值，将导致文档里的元素生成一个主盒（Principal Box）以包含后代盒子和内容，同时其自身也是参与到定位方案中的盒子。而有些元素除了会生成主盒之外，还可能会生成额外的盒子。比如设置了 `display` 值为 `list-item` 元素。这些额外的盒子的放置位置与主盒有关。

> CSS的 `display` 切换不同的值时，会产生生成不同的盒子；同时客户端渲染HTML文档时都会为每个元素自带一个盒子。

# 一切都是盒子

在 CSS 中，一切都会生成盒子。Web 页面本质上是一组块级盒子和内联级盒子。可以在浏览器的开发者工具中选择页面上的元素，就可以很好的理解这些盒子。可以看到构成布局的盒以及盒子的各种属性（外边距 `margin`、内距`padding`、边框`border`和内容`content`等）。

# 控制盒子生成

前面提到过，在 CSS 中任何东西都是一个盒子，盒子之间的类型还可以使用 `display` 的不同值来进行切换。在 `display` 中还有两个不同的值 `none` 和 `contents` ，**可以用来控制盒子是否应该显式**。如果你希望 HTML 中的元素不想在 CSS 中生成盒子，就需要以某种方式来抑制盒子的生成。你可能想做两件事：

- 防止元素及其后代元素生成一个盒子
- 防止元素自身生成一个盒子，但其后代元素仍然会生成一个盒子

在 CSS 中的 `display` 属性的 `none` 和 `contents` 即可帮助我们做到这两点：

- 如果元素的 `display` 取值为 `none` 时，元素和其后代元素都将不可见，也不会生成任何盒子
- 如果元素的 `display` 取值为 `contents` 时，元素自身的盒子属性（`margin`、`padding` 和 `border` 等）都将丢失，但其后代元素不受任何影响。也就是说，元素自身不再是一个盒子，但其后代元素依旧是一个盒子

也就是说，CSS 的 `display` 属性控制盒子生成：

- 元素的 `display` 值不是 `none` 或 `contents` 时，元素即可生成一个盒子，盒子的类型由其值的类型来决定
- 元素的 `display` 值是 `none` 时，元素及其后代元素都不会生成盒子
- 元素的 `display` 值是 `contents` 时，元素自身不会生成盒子，但其后代元素依旧会根据 `display` 生成相应的盒子


