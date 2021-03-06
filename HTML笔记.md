#### 1.HTML元素分类（行内元素与块级元素、置换元素与非置换元素）

**行内元素与块级元素对比**

一般情况下，行内元素只能包含数据和其他行内元素。
而块级元素可以包含行内元素和其他块级元素。这种结构上的包含继承区别可以使块级元素创建比行内元素更”大型“的结构。
默认情况下，行内元素不会以新行开始，而块级元素会新起一行。

行内元素列

下面的元素都是行内元素：

```html
b, big, i, small, tt

abbr, acronym, cite, code, dfn, em, kbd, strong, samp, var

a, bdo, br, img, map, object, q, script, span, sub, sup

button, input, label, select, textarea
```

块级元素列表

```html
<address>联系方式信息。
<article> HTML5文章内容。
<aside> HTML5伴随内容。
<audio> HTML5音频播放。
<blockquote>块引用。
<Canvas> HTML5绘制图形。
<dd>定义列表中定义条目描述。
<div>文档分区。
<dl>定义列表。
<fieldset>表单元素分组。
<figcaption> HTML5图文信息组标题
<figure> HTML5图文信息组 (参照 <figcaption>)。
<footer> HTML5区段尾或页尾。
<form>表单。
<h1>, <h2>, <h3>, <h4>, <h5>, <h6>标题级别 1-6.
<header> HTML5区段头或页头。
<hgroup> HTML5标题组。
<hr>水平分割线。
<noscript>不支持脚本或禁用脚本时显示的内容。
<ol>有序列表。
<output> HTML5表单输出。
<p>行。
<pre>预格式化文本。
<section> HTML5一个页面区段。
<table>表格。
<tfoot>表脚注。
<ul>无序列表。
<video> HTML5视频。
```

之前说了行内元素与块级元素区别时提到行内元素不可以定义宽和高，那么问题来了img标签、input标签为啥可以设置呢？

先进一个题外话

在面试一个 重构（各大公司的叫法可能不太一样）时，我喜欢从一个点开始问，然后一直延展下去成为一条线，甚至是一个面，直到问到不会的地方，然后又换另外一个点。

例如：我可能会说，能简单聊聊 行内级元素 和 块级元素 的区别吗。

一般这时，候选人都会说到 行内级元素 不会换新行，而 块级元素 会格式化为块状，即换行。但也有些遗憾的方面（如：混淆了块元素和块级元素，行内元素和行内级元素），当然这看起来似乎不是特别重要。

这时我会继续问，行内元素 能够定义宽度和高度吗？

不少候选人会说：不能

我会继续问，说几个你熟悉的 行内元素 吧

于是 span, strong, em… 答案我还是比较满意的。

我仍然会继续，img 是行内元素么？

候选人这时通常会迟疑一下，可能意识到我接下来想问啥了，但还是会回答：是

于是我会说，那 img 能定义宽度和高度么？

有的候选人这时会犹豫，因为如果回答是，就会推翻他之前说的 行内元素不能定义宽高，如果回答不是，似乎又和他所熟知的经验不一致。但通常最后还是会回答：能

那我就又得问，你之前不是说 行内元素不能定义宽高 吗？为什么 img 可以？

到这里，候选人基本上不知道要怎么回答好了，最后可能会告诉我，因为 img 是特殊元素

当然，虽然这么回答也不能说是错误的，但基本上也能知道候选人对这条线的基础的掌握程度了。

但我希望听到的答案是通过解释置换元素相关的概念从而给出答案。



**什么是置换元素？**

一个 内容 不受CSS视觉格式化模型控制，CSS渲染模型并不考虑对此内容的渲染，且元素本身一般拥有固有尺寸（宽度，高度，宽高比）的元素，被称之为置换元素。

**什么是非置换元素？**

w3c并没有给出明确的非置换元素的解释，但能确定的是除置换元素之外，所有的元素都是非置换元素。

**行内级置换和非置换元素的宽度定义**

对于行内级非置换元素，宽度设置是不适用的。

对于行内级置换元素来说，其宽度的设置需遵循以下几点：

若宽高的计算值都为 auto 且元素有固有宽度，则 width 的使用值为该固有宽度；
典型的例子是：拥有默认宽高的 input 当宽度的计算值为auto时，则宽度使用值为其默认的固有宽度

若宽度的计算值为 auto 且元素有固有宽度，则 width 的使用值为该固有宽度；
例子同上

若宽度的计算值为 auto 且高度有 非auto 的计算值，并且元素有固有宽高比，则width 的使用值为 高度使用值 * 固有宽高比；
典型的例子：img 当只定义了其高度值时，其宽度将会根据固有宽高比进行等比设置

除此之外，当 width 的计算值为 auto 时，则宽度的使用值为 300px
典型的例子：比如iframe, canvas

其它类型的置换元素，其宽度的定义都参照行内置换元素的定义。

**行内级置换和非置换元素的高度定义**

对于行内级非置换元素，高度设置是不适用的。

对于行内级置换元素来说，其高度的设置需遵循以下几点：

若宽高的计算值都为 auto 且元素有固有高度，则 height 的使用值为该固有高度；
若高度的计算值为 auto 且元素有固有高度，则 height 的使用值为该固有高度；
若高度的计算值为 auto 且宽度有 非auto 的计算值，并且元素有固有宽高比，则height 的使用值为：宽度使用值 / 固有宽高比；
若高度的计算值为 auto 且上述条件完全不符，则 height 的使用值 不能大于150px，且宽度不能大于长方形高度的2倍。
其它类型的置换元素，其高度的定义都参照行内置换元素的定义。

#### 2.

