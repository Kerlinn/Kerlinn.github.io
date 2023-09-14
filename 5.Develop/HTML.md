# HTML文件结构

## 文档结构

html的所有标签为树形结构，例如：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Web应用课</title>
</head>
<body>
    <h1>第一讲</h1>
</body>
</html>
```

### `<html>`标签

HTML `<html>` 元素 表示一个 HTML 文档的根（顶级元素），所以它也被称为根元素。所有其他元素必须是此元素的后代。

### `<head>`标签

HTML `<head>` 元素 规定文档相关的配置信息（元数据），包括文档的标题，引用的文档样式和脚本等。

### `<body>`标签

HTML`<body>` 元素表示文档的内容。`document.body` 属性提供了可以轻松访问文档的 body 元素的脚本。

### `<title>`标签

HTML` <title>` 元素 定义文档的标题，显示在浏览器的标题栏或标签页上。它只应该包含文本，若是包含有标签，则它包含的任何标签都将被忽略。

### `<meta>`

HTML `<meta>` 元素表示那些不能由其它 HTML 元相关（meta-related）元素（`<base>`、`<link>`, `<script>`、`<style>` 或 `<title>`）之一表示的任何元数据信息。

常见属性：

- `charset`：这个属性声明了文档的字符编码。如果使用了这个属性，其值必须是与 ASCII 大小写无关（ASCII case-insensitive）的”utf-8”。
- `name`：name 和 content 属性可以一起使用，以`名 - 值对`的方式给文档提供元数据，其中 name 作为元数据的名称，content 作为元数据的值。

```HTML
<meta charset="utf-8">

<!-- Redirect page after 3 seconds -->
<meta http-equiv="refresh" content="3;url=https://www.mozilla.org">
```

### `<icon>`

```HTML
<link rel="icon" href="images/icon.png">
```

<!-- 多行注释 -->
示例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!--   
        这里的内容均为注释
        <h1>第一讲</h1>
        <p>
            段落。
        </p>
    -->
</body>
</html>
```



## 文本标签

文本标签虽然很多，但大部分可看成是预定好样式的`<div>`和`<span>`。

### `<div>`标签

> 一整行

`<div>`元素 (或 HTML 文档分区元素) 是一个通用型的**流内容容器**，在不使用CSS的情况下，其对内容或布局没有任何影响。其他块级标签例如：`<h1>`, `<p>`, `<pre>`, `<ul>`, `<ol>`, `<table>`。

### `<span>`标签

> 一小块

`<span>` 元素是短语内容的通用**行内容器**，并没有任何特殊语义。可以使用它来编组元素以达到某种样式意图（通过使用类或者 Id 属性），或者这些元素有着共同的属性，比如lang。应该在没有其他合适的语义元素时才使用它。`<span>` 与 `<div>` 元素很相似，但 `<div>` 是一个 块元素 而 `<span>` 则是 行内元素。其他内联标签例如：`<i>`,`<b>`, `<del>`, `<ins>`, `<td>`, `<a>`。

### `<h1> - <h6>`标签

> 加大加粗的div

`<h1>–<h6>` 标题 (Heading) 元素呈现了六个不同的级别的标题，`<h1>`级别最高，而 `<h6>` 级别最低。

### `<p>`标签

> - 一段话，加了前后行间距的div
> - 将空格和回车都过滤掉
>
> ```CSS
> p {
>     display: block;
>     margin-block-start: 1em;
>     margin-block-end: 1em;
>     margin-inline-start: 0px;
>     margin-inline-end: 0px;
> }
> ```

`<p>`元素（或者说 HTML 段落元素）表示文本的一个段落。该元素通常表现为一整块与相邻文本分离的文本，或以垂直的空白隔离或以首行缩进。另外，`<p>` 是块级元素。

### `<pre>`标签

> 保留回车，空格的`<p>`

`<pre>` 元素表示预定义格式文本。在该元素中的文本通常按照原文件中的编排，以等宽字体的形式展现出来，文本中的空白符（比如空格和换行符）都会显示出来。(紧跟在 `<pre>` 开始标签后的换行符也会被省略)

### `<br>`标签

> 指定位置处换行

` <br>` 元素在文本中生成一个换行（回车）符号。此元素在写诗和地址时很有用，这些地方的换行都非常重要。

### `<hr>`标签

> 水平线

`<hr>` 元素表示段落级元素之间的主题转换（例如，一个故事中的场景的改变，或一个章节的主题的改变）。

在 HTML 的早期版本中，它是一个水平线。现在它仍能在可视化浏览器中表现为水平线，但目前被定义为语义上的，而不是表现层面上。所以如果想画一条横线，请使用适当的 css 样式来修饰。

### `<i>`标签

> 斜体

 `<i>` 用于表现因某些原因需要区分普通文本的一系列文本。例如技术术语、外文短语或是小说中人物的思想活动等，它的内容通常以斜体显示。

### `<b>`标签

> 加粗

`<b>`，提醒注意（Bring Attention To）元素用于吸引读者的注意到该元素的内容上（如果没有另加特别强调）。这个元素过去被认为是粗体（Boldface）元素，并且大多数浏览器仍然将文字显示为粗体。尽管如此，你不应将 `<b>` 元素用于显示粗体文字；替代方案是使用 CSS `font-weight` 属性来创建粗体文字。

### `<del>`标签

`<del>`标签表示一些被从文档中删除的文字内容。比如可以在需要显示修改记录或者源代码差异的情况使用这个标签。`<ins>`标签的作用恰恰于此相反：表示文档中添加的内容。

### `<ins>`标签

`<ins>` 元素定义已经被插入文档中的文本。

### 空格标签

#### `&nbsp;`

不换行空格，全称No-Break Space，它是按下space键产生的空格。在HTML中，如果你用空格键产生此空格，空格是不会累加的（只算1个）。要使用html实体表示才可累加，该空格占据宽度受字体影响明显而强烈。

#### `&ensp;`

半角空格，全称是En Space，en是字体排印学的计量单位，为em宽度的一半。根据定义，它等同于字体度的一半（如16px字体中就是8px）。名义上是小写字母n的宽度。此空格传承空格家族一贯的特性：透明的，此空格有个相当稳健的特性，就是其**占据的宽度正好是1/2个中文宽度**，而且基本上不受字体影响。

#### `&emsp;`

全角空格，全称是Em Space，em是字体排印学的计量单位，相当于当前指定的点数。例如，1 em在16px的字体中就是16px。此空格也传承空格家族一贯的特性：透明的，此空格也有个相当稳健的特性，就是其**占据的宽度正好是1个中文宽度**，而且基本上不受字体影响。

#### `&thinsp;`

窄空格，全称是Thin Space。我们不妨称之为“瘦弱空格”，就是该空格长得比较瘦弱，身体单薄，占据的宽度比较小。它是em之六分之一宽。

## 图片

`<img>` 元素将一份图像嵌入文档。默认为行内元素，即`display: inline`。

> 一行放不下会自动换行

### `src`属性

该属性是必须的，它包含了你想嵌入的图片的文件路径。

### `alt`属性

该属性包含一条对图像的文本描述，这不是强制性的，但对可访问性而言，它难以置信地有用——屏幕阅读器会将这些描述读给需要使用阅读器的使用者听，让他们知道图像的含义。如果由于某种原因无法加载图像，普通浏览器也会在页面上显示alt 属性中的备用文本：例如，网络错误、内容被屏蔽或链接过期时。

### `height`属性

图像的高度，在 HTML5 中的单位是 CSS 像素，在 HTML 4 中既可以是像素，也可以是百分比。可以只指定 width 和 height 中的一个值，浏览器会根据原始图像进行缩放。

### `width`属性

图像的宽度，在 HTML5 中单位是 CSS 像素， 在 HTML 4 中可以是像素也可以是百分比

## 音频与视频

### `<audio>`标签

`<audio>` 元素用于在文档中嵌入音频内容。 `<audio>` 元素可以包含一个或多个音频资源， 这些音频资源可以使用 src 属性或者`<source>` 元素来进行描述：浏览器将会选择最合适的一个来使用。也可以使用 MediaStream 将这个元素用于流式媒体。

- 使用src属性播放

示例：

```HTML
<audio
    controls
    src="/audios/bgm.mp3">
        Your browser does not support the
        <code>audio</code> element.
</audio>
```

- `<audio>` 与多个 `<source>` 元素

这个例子包含了多个 `<source>` 元素。如果能够播放的话，浏览器就会试图去加载第一个 source 元素；如果不行，那就退而求其次去加载第二个。

```HTML
<audio controls>
    <source src="/audios/sound1" type="audio/mpeg"/>
    <source src="/audios/sound2" type="audio/mpeg"/>
</audio>
```

### `<video>`标签

`<video>` 元素 用于在 HTML 或者 XHTML 文档中嵌入媒体播放器，用于支持文档内的视频播放。你也可以将 `<video>` 标签用于音频内容，但是 `<audio>` 元素可能在用户体验上更合适。

示例：

```HTML
<video controls width="800">
    <source src="/videos/video1.mp4"
            type="video/mp4">
    <source src="/videos/video2.mp4"
            type="video/mp4">
    Sorry, your browser doesn't support embedded videos.
</video>
```

## 超链接

HTML `<a>` 元素（或称锚元素）可以通过它的 `href` 属性创建通向其他网页、文件、同一页面内的位置、电子邮件地址或任何其他 URL 的超链接。`<a>` 中的内容应该指明链接的意图。如果存在 `href` 属性，当 `<a>` 元素聚焦时按下回车键就会激活它。

常用选项

- 点击链接**打开新标签页面**时加入属性：`target="_blank"`

## 表单

### `<form>`标签

`<form>` 元素表示文档中的一个区域，此区域包含交互控件，用于向 Web 服务器提交信息。

`<input>`标签
HTML `<input>`用来填写内容，常见类型有：

- `<input type="text">`：创建基础的单行文本框。
  `<input type="number">`：用于让用户输入一个数字。其包括内置验证以拒绝非数字输入。浏览器可能会选择提供步进箭头，让用户可以使用鼠标增加和减少输入的值，或者只需用指尖敲击即可。
- `<input type="email">`：带有 “email” (电子邮箱) 类型标记的输入框元素 (`<input>`) 能够让用户输入或编辑一个电子邮箱地址，此外，如果指定了multiple属性，用户还可以输入多个电子邮箱地址。在表单提交前，输入框会自动验证输入值是否是一个或多个合法的电子邮箱地址 (非空值且符合电子邮箱地址格式). CSS 伪标签 `:valid` 和 `:invalid` 能够在校验后自动应用。
- `<input type="password">`：`<input>` 元素 里有一种叫做 “password” 的值，给我们一个方法让用户更加安全的输入密码。这个元素是作为一行纯文本编辑器控件呈现的，其中文本被遮蔽以致于无法读取，通常通过用诸如星号（`*`）或点（`•`）等符号替换每个字符来实现。这个符号会根据用户的浏览器和操作系统来具体显示哪个。
- `<input type="radio">`：`<input>` 的 `radio` 类型元素默认渲染为小型圆圈图表，填充即为激活，类似于之前描述额复选框（checkbox）类型。单选按钮允许你选择单一的值来提交表单。

常用属性有：

- `name`: 名称
- `id`: 唯一ID
- `maxlength`：最大长度
- `minlength`：最小长度
- `required`：是否必填
- `placeholder`：当表单控件为空时，控件中显示的内容

### `<textarea>`标签

`<textarea>` 元素表示一个多行纯文本编辑控件，当你希望用户输入一段相当长的、不限格式的文本，例如评论或反馈表单中的一段意见时，这很有用。

### `<select>`与`<option>`标签

`<select>` 元素表示一个提供选项菜单的控件。


示例：

```HTML
<label for="pet-select">Choose a pet:</label>
<select name="pets" id="pet-select">
    <option value="">--Please choose an option--</option>
    <option value="dog">Dog</option>
    <option value="cat">Cat</option>
    <option value="hamster">Hamster</option>
    <option value="parrot">Parrot</option>
    <option value="spider">Spider</option>
    <option value="goldfish">Goldfish</option>
</select>
```

### `<button>`标签

`<button>` 元素表示一个可点击的按钮，可以用在表单或文档其它需要使用简单标准按钮的地方。 默认情况下，HTML 按钮的显示样式接近于 user agent 所在的宿主系统平台（用户操作系统）的按钮， 但你可以使用 CSS 来改变按钮的样貌。

## 列表

### `<ul>`与`<li>`标签

`<ul>` 元素（或称 HTML 无序列表元素）表示一个内可含多个元素的无序列表或项目符号列表。

示例：

```HTML
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```

### `<ol>`与`<li>`标签

 `<ol>` 元素表示有序列表，通常渲染为一个带编号的列表。

示例：

```HTML
<ol>
  <li>Fee</li>
  <li>Fi</li>
  <li>Fo</li>
  <li>Fum</li>
</ol>
```

### `<dl>`、`<dt>`与`<dd>`标签

HTML `<dl>` 元素 （或 HTML 描述列表元素）是一个包含术语定义以及描述的列表，通常用于展示词汇表或者元数据 (键 - 值对列表)。


示例：

```HTML
<dl>
    <dt>Name</dt>
    <dd>Godzilla</dd>
    <dt>Born</dt>
    <dd>1952</dd>
    <dt>Birthplace</dt>
    <dd>Japan</dd>
    <dt>Color</dt>
    <dd>Green</dd>
    <dd>Orange</dd>
</dl>
```


