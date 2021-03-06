# HTML编码规范
[1  前言](#user-content-1--前言)

[2  代码风格](#user-content-2--代码风格)

　　[2.1  缩进与换行](#user-content-21--缩进与换行)

　　[2.2  命名](#user-content-22--命名)

　　[2.3  属性](#user-content-23--属性)

[3  通用](#user-content-3--通用)

　　[3.1  DOCTYPE](#user-content-31--DOCTYPE)

　　[3.2  编码](#user-content-32--编码)

　　[3.3  CSS和JavaScript引入](#user-content-33--CSS和JavaScript引入)

[4  head](#user-content-4--head)

　　[4.1  title](#user-content-41--title)

　　[4.2  favicon](#user-content-42--favicon)

[5  图片](#user-content-5--图片)

[6  表单](#user-content-6--表单)

　　[6.1  控件标题](#user-content-61--控件标题)

　　[6.2  按钮](#user-content-62--按钮)

　　[6.3  可访问性](#user-content-63--可访问性)

##  1  前言

本文档的目标是使 HTML 代码风格保持一致，容易被理解和被维护。



##  2  代码风格

###  2.1  缩进与换行

**[强制] 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。**

**[建议] 每行不得超过 `120` 个字符。**

解释：

过长的代码不容易阅读与维护。但是考虑到 HTML 的特殊性，不做硬性要求。

###  2.2  命名

**[强制] `class` 必须单词全字母小写，单词间以 `-` 分隔。**

**[强制] `class` 必须代表相应模块或部件的内容或功能，不得以样式信息进行命名。**

示例：

```html
<!-- good -->
<div class="sidebar"></div>

<!-- bad -->
<div class="left"></div>
```

**[强制] 元素 `id` 必须保证页面唯一。**

解释：

同一个页面中，不同的元素包含相同的 `id`，不符合 `id` 的属性含义。并且使用 `document.getElementById` 时可能导致难以追查的问题。

**[建议] `id` 建议单词全字母小写，单词间以 `-` 分隔。同项目必须保持风格一致。**

**[建议] `id`、`class` 命名，在避免冲突并描述清楚的前提下尽可能短。**

示例：

```html
<!-- good -->
<div id="nav"></div>
<!-- bad -->
<div id="navigation"></div>

<!-- good -->
<p class="comment"></p>
<!-- bad -->
<p class="com"></p>

<!-- good -->
<span class="author"></span>
<!-- bad -->
<span class="red"></span>
```

**[强制] 禁止为了 `hook 脚本`，创建无样式信息的 `class`。**

解释：

不允许 `class` 只用于让 JavaScript 选择某些元素，`class` 应该具有明确的语义和样式。否则容易导致 CSS class 泛滥。

使用 `id`、属性选择作为 hook 是更好的方式。

**[强制] 对 `HTML5` 中规定允许省略的闭合标签，不允许省略闭合标签。**

示例：

```html
<!-- good -->
<ul>
    <li>first</li>
    <li>second</li>
</ul>

<!-- bad -->
<ul>
    <li>first
    <li>second
</ul>
```

**[强制] 标签使用必须符合标签嵌套规则。**

解释：

比如 `div` 不得置于 `p` 中，`tbody` 必须置于 `table` 中。

**[建议] 在 CSS 可以实现相同需求的情况下不得使用表格进行布局。**

解释：

在兼容性允许的情况下应尽量保持语义正确性。对网格对齐和拉伸性有严格要求的场景允许例外，如多列复杂表单。

**[建议] 标签的使用应尽量简洁，减少不必要的标签。**

示例：

```html
<!-- good -->
<img class="avatar" src="image.png">

<!-- bad -->
<span class="avatar">
    <img src="image.png">
</span>
```

**[建议]尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。**

###  2.3  属性

**[强制] 属性名必须使用小写字母。**

示例：

```html
<!-- good -->
<table cellspacing="0">...</table>

<!-- bad -->
<table cellSpacing="0">...</table>
```

**[强制] 属性值必须用双引号包围。**

****解释：

不允许使用单引号，不允许不使用引号。

示例：

```html
<!-- good -->
<script src="esl.js"></script>

<!-- bad -->
<script src='esl.js'></script>
<script src=esl.js></script>
```

**[建议] 布尔类型的属性，建议不添加属性值。**

示例：

```html
<input type="text" disabled>
<input type="checkbox" value="1" checked>
```

**[强制] 自定义属性建议以 `data-` 为前缀**

解释：

使用前缀有助于区分自定义属性和标准定义的属性。

示例：

```html
<li data-menuid="100"></li>
```



##  3  通用

###  3.1  DOCTYPE

**[强制] 使用 `HTML5` 的 `DOCTYPE` 来启用标准模式。**

示例：

```html
<!DOCTYPE html>
```

###  3.2  编码

**[强制] 页面必须明确指定字符编码。指定字符编码的 `meta` 必须是 `head` 的第一个直接子元素。**

示例：

```html
<html>
    <head>
        <meta charset="UTF-8">
        ......
    </head>
    <body>
        ......
    </body>
</html>
```



###  3.3  CSS和JavaScript引入

**[强制] 引入 `CSS` 时必须指明 `rel="stylesheet"`。**

示例：

```html
<link rel="stylesheet" href="page.css">
```

**[建议] 引入 `CSS` 和 `JavaScript` 时无须指明 `type` 属性。**

解释：

`text/css` 和 `text/javascript` 是 `type` 的默认值。

**[建议] 展现定义放置于外部 `CSS` 中，行为定义放置于外部 `JavaScript` 中。**

解释：

结构-样式-行为的代码分离，对于提高代码的可阅读性和维护性都有好处。

**[建议] 在 `head` 中引入页面需要的所有 `CSS` 资源。**

解释：

在页面渲染的过程中，新的CSS可能导致元素的样式重新计算和绘制，页面闪烁。

**[建议] `JavaScript` 应当放在页面末尾。**

解释：

将 `script` 放在页面中间将阻断页面的渲染。出于性能方面的考虑，如非必要，请遵守此条建议。

示例：

```html
<body>
    <!-- a lot of elements -->
    <script src="init-behavior.js"></script>
</body>
```



##  4  head

###  4.1  title

**[强制] 页面必须包含 `title` 标签声明标题。**

**[强制] `title` 必须作为 `head` 的直接子元素，并紧随 `charset` 声明之后。**

解释：

`title` 中如果包含 ASCII 之外的字符，浏览器需要知道字符编码类型才能进行解码，否则可能导致乱码。

示例：

```html
<head>
    <meta charset="UTF-8">
    <title>页面标题</title>
</head>
```

###  4.2  favicon

**[强制] 保证 `favicon` 可访问。**

解释：

在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 `favicon.ico` 。为了保证 favicon 可访问，避免 404，必须遵循以下两种方法之一：

1. 在 Web Server 根目录放置 `favicon.ico` 文件。
2. 使用 `link` 指定 favicon。

示例：

```html
<link rel="shortcut icon" href="path/to/favicon.ico">
```



##  5  图片



**[强制] 禁止 `img` 的 `src` 取值为空。延迟加载的图片也要增加默认的 `src`。**

**[建议] 避免为 `img` 添加不必要的 `title` 属性。**

解释：

多余的 `title` 影响看图体验，并且增加了页面尺寸。

**[建议] 为重要图片添加 `alt` 属性。**

解释：

可以提高图片加载失败时的用户体验。

**[建议] 有下载需求的图片采用 `img` 标签实现，无下载需求的图片采用 CSS 背景图实现。**

解释：

1. 产品 logo、用户头像、用户产生的图片等有潜在下载需求的图片，以 `img` 形式实现，能方便用户下载。
2. 无下载需求的图片，比如：icon、背景、代码使用的图片等，尽可能采用 CSS 背景图实现。

##  6  表单

###  6.1  控件标题

**[强制] 有文本标题的控件必须使用 `label` 标签将其与其标题相关联。**

解释：

有两种方式：

1. 将控件置于 `label` 内。
2. `label` 的 `for` 属性指向控件的 `id`。

推荐使用第一种，减少不必要的 `id`。如果 DOM 结构不允许直接嵌套，则应使用第二种。

示例：

```html
<label><input type="checkbox" name="confirm" value="on"> 我已确认上述条款</label>

<label for="username">用户名：</label> <input type="textbox" name="username" id="username">
```

###  6.2  按钮

**[强制] 使用 `button` 元素时必须指明 `type` 属性值。**

解释：

`button` 元素的默认 `type` 为 `submit`，如果被置于 `form` 元素中，点击后将导致表单提交。为显示区分其作用方便理解，必须给出 `type` 属性。

示例：

```html
<button type="submit">提交</button>
<button type="button">取消</button>
```

**[建议] 尽量不要使用按钮类元素的 `name` 属性。**

解释：

由于浏览器兼容性问题，使用按钮的 `name` 属性会带来许多难以发现的问题。

###  6.3  可访问性

**[建议] 负责主要功能的按钮在 DOM 中的顺序应靠前。**

示例：

```html
<!-- good -->
<div class="buttons">
    <div class="button-group">
        <button type="submit">提交</button>
        <button type="button">取消</button>
    </div>
</div>

<!-- bad -->
<div class="buttons">
    <button type="button">取消</button>
    <button type="submit">提交</button>
</div>
```

