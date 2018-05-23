# CSS编码规范
[1  前言](#user-content-1--前言)

[2  代码风格](#user-content-2--代码风格)

　　[2.1  缩进](#user-content-21--缩进)

　　[2.2  空格](#user-content-22--空格)

　　[2.3  行长度](#user-content-23--行长度)

　　[2.4  选择器](#user-content-24--选择器)

　　[2.5  属性](#user-content-25--属性)

　　[2.6  空行](#user-content-26--空行)

[3  通用](#user-content-3--通用)

　　[3.1  选择器](#user-content-31--选择器)

[4  值与单位](#user-content-4--值与单位)

　　[4.1  url()](#user-content-41--url())

　　[4.2  长度](#user-content-42--长度)

　　[4.3  颜色](#user-content-43--颜色)

　　[4.4  2D位置](#user-content-44--2D位置)

[5  文本编排](#user-content-5--文本编排)

　　[5.1  字体族](#user-content-51--字体族)

　　[5.2  字号](#user-content-52--字号)

　　[5.3  字体风格](#user-content-53--字体风格)

　　[5.4  字重](#user-content-54--字重)

##  1  前言

本文档的目标是使 CSS 代码风格保持一致，容易被理解和被维护。



##  2  代码风格

###  2.1  缩进

**[强制] 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。**

示例：

```css
.selector {
    margin: 0;
    padding: 0;
}
```

###  2.2  空格

**[强制] `选择器` 与 `{` 之间必须包含空格。**

示例：

```css
.selector {
}
```

**[强制] `属性名` 与之后的 `:` 之间不允许包含空格， `:` 与 `属性值` 之间必须包含空格。**

示例：

```css
margin: 0;
```

**[强制] `列表型属性值` 书写在单行时，`,` 后必须跟一个空格。**

示例：

```css
font-family: Arial, sans-serif;
```

###  2.3  行长度

**[强制] 每行不得超过 `120` 个字符，除非单行不可分割。**

解释：

常见不可分割的场景为URL超长。

**[建议] 对于超长的样式，在样式值的 `空格` 处或 `,` 后换行，建议按逻辑分组。**

示例：

```css
/* 不同属性值按逻辑分组 */
background:
    transparent url(aVeryVeryVeryLongUrlIsPlacedHere)
    no-repeat 0 0;

/* 可重复多次的属性，每次重复一行 */
background-image:
    url(aVeryVeryVeryLongUrlIsPlacedHere)
    url(anotherVeryVeryVeryLongUrlIsPlacedHere);

/* 类似函数的属性值可以根据函数调用的缩进进行 */
background-image: -webkit-gradient(
    linear,
    left bottom,
    left top,
    color-stop(0.04, rgb(88,94,124)),
    color-stop(0.52, rgb(115,123,162))
);
```

###  2.4  选择器

**[强制] 当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行。**

示例：

```css
/* good */
.post,
.page,
.comment {
    line-height: 1.5;
}

/* bad */
.post, .page, .comment {
    line-height: 1.5;
}
```

**[强制] `>`、`+`、`~` 选择器的两边各保留一个空格。**

示例：

```css
/* good */
main > nav {
    padding: 10px;
}

label + input {
    margin-left: 5px;
}

input:checked ~ button {
    background-color: #69C;
}

/* bad */
main>nav {
    padding: 10px;
}

label+input {
    margin-left: 5px;
}

input:checked~button {
    background-color: #69C;
}
```

**[强制] 属性选择器中的值必须用双引号包围。**

解释：

不允许使用单引号，不允许不使用引号。

示例：

```css
/* good */
article[character="juliet"] {
    voice-family: "Vivien Leigh", victoria, female;
}

/* bad */
article[character='juliet'] {
    voice-family: "Vivien Leigh", victoria, female;
}
```

###  2.5  属性

**[强制] 属性定义必须另起一行。**

示例：

```css
/* good */
.selector {
    margin: 0;
    padding: 0;
}

/* bad */
.selector { margin: 0; padding: 0; }
```

**[强制] 属性定义后必须以分号结尾。**

示例：

```css
/* good */
.selector {
    margin: 0;
}

/* bad */
.selector {
    margin: 0
}
```

###  2.6  空行

**[强制] '}'后跟一个空行**

示例：

```css
/* good */
h1 {
    font-weight:600;
}

h2 {
    font-weight:700;
}

/* bad */
h1 {
    font-weight:600;
}
h2 {
    font-weight:700;
}
```



##  3  通用



###  3.1  选择器

**[强制] 如无必要，不得为 `id`、`class` 选择器添加类型选择器进行限定。**

解释：

在性能和维护性上，都有一定的影响。

示例：

```css
/* good */
#error,
.danger-message {
    font-color: #c00;
}

/* bad */
dialog#error,
p.danger-message {
    font-color: #c00;
}
```

**[建议] 选择器的嵌套层级应不大于 `3` 级，位置靠后的限定条件应尽可能精确。**

示例：

```css
/* good */
#username input {}
.comment .avatar {}

/* bad */
.page .header .login #username input {}
.comment div * {}
```

**[建议] 尽量不使用 `!important` 声明。**



##  4  值与单位

###  4.1  url()

**[强制] `url()` 函数中的路径不加引号。**

示例：

```css
body {
    background: url(bg.png);
}
```

###  4.2  长度

**[强制] 长度为 `0` 时须省略单位。 (也只有长度单位可省)**

示例：

```css
/* good */
body {
    padding: 0 5px;
}

/* bad */
body {
    padding: 0px 5px;
}
```

###  4.3  颜色

**[强制] RGB颜色值必须使用十六进制记号形式 `#rrggbb`。不允许使用 `rgb()`。**

解释：

带有alpha的颜色信息可以使用 `rgba()`。使用 `rgba()` 时每个逗号后必须保留一个空格。

示例：

```css
/* good */
.success {
    box-shadow: 0 0 2px rgba(0, 128, 0, .3);
    border-color: #008000;
}

/* bad */
.success {
    box-shadow: 0 0 2px rgba(0,128,0,.3);
    border-color: rgb(0, 128, 0);
}
```

**[强制] 颜色值可以缩写时，必须使用缩写形式。**

示例：

```css
/* good */
.success {
    background-color: #aca;
}

/* bad */
.success {
    background-color: #aaccaa;
}
```

**[强制] 颜色值不允许使用命名色值。**

示例：

```css
/* good */
.success {
    color: #90ee90;
}

/* bad */
.success {
    color: lightgreen;
}
```

**[建议] 颜色值中的英文字符采用小写。**

示例：

```css
/* good */
.success {
    background-color: #aca;
    color: #90ee90;
}

/* bad */
.success {
    background-color: #ACA;
    color: #90EE90;
}
```

###  4.4  2D位置

**[强制] 必须同时给出水平和垂直方向的位置。**

解释：

2D 位置初始值为 `0% 0%`，但在只有一个方向的值时，另一个方向的值会被解析为 center。为避免理解上的困扰，应同时给出两个方向的值。[background-position属性值的定义](http://www.w3.org/TR/CSS21/colors.html#propdef-background-position)

示例：

```css
/* good */
body {
    background-position: center top; /* 50% 0% */
}

/* bad */
body {
    background-position: top; /* 50% 0% */
}
```





##  5  文本编排

###  5.1  字体族

**[强制] `font-family` 属性中的字体族名称应使用字体的英文 `Family Name`，其中如有空格，须放置在引号中。**

解释：

所谓英文 Family Name，为字体文件的一个元数据，常见名称如下：

| 字体        | 操作系统    | Family Name        |
| --------- | ------- | ------------------ |
| 宋体 (中易宋体) | Windows | SimSun             |
| 黑体 (中易黑体) | Windows | SimHei             |
| 微软雅黑      | Windows | Microsoft YaHei    |
| 微软正黑      | Windows | Microsoft JhengHei |
| 华文黑体      | Mac/iOS | STHeiti            |
| 冬青黑体      | Mac/iOS | Hiragino Sans GB   |

示例：

```css
/* good */
h1 {
    font-family: "Microsoft YaHei";
}

/* bad */
h1 {
    font-family:"微软雅黑";
}
```

###  5.2  字号

**[强制] 字号应不小于 `12px`。**

解释：

由于 Windows 的字体渲染机制，小于 `12px` 的文字显示效果极差、难以辨认。

###  5.3  字体风格

**[建议] 不要使用除 `normal` 外的 `font-style`。**

解释：

由于中文字体没有 `italic` 风格的实现，所有浏览器下都会 fallback 到 `obilique` 实现 (自动拟合为斜体)，小字号下 (特别是 Windows 下会在小字号下使用点阵字体的情况下) 显示效果差，造成阅读困难。

###  5.4  字重

**[强制] `font-weight` 属性必须使用数值方式描述。**

解释：

CSS 的字重分 100 – 900 共九档，但目前受字体本身质量和浏览器的限制，实际上支持 `400` 和 `700` 两档，分别等价于关键词 `normal` 和 `bold`。

浏览器本身使用一系列[启发式规则](http://www.w3.org/TR/CSS21/fonts.html#propdef-font-weight)来进行匹配，在 `<700` 时一般匹配字体的 Regular 字重，`>=700` 时匹配 Bold 字重。

但已有浏览器开始支持 `=600` 时匹配 Semibold 字重 (见[此表](http://justineo.github.io/slideshows/font/#/3/15))，故使用数值描述增加了灵活性，也更简短。

示例：

```css
/* good */
h1 {
    font-weight: 700;
}

/* bad */
h1 {
    font-weight: bold;
}
```

