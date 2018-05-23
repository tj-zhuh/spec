# JavaScript编码规范
[1  前言](#user-content-1--前言)

[2  代码风格](#user-content-2--代码风格)

　　[2.1  结构](#user-content-21--结构)

　　　　[2.1.1  缩进](#user-content-211--缩进)

　　　　[2.1.2  空格](#user-content-212--空格)

　　　　[2.1.3  换行](#user-content-213--换行)

　　　　[2.1.4  语句](#user-content-214--语句)

　　[2.2  命名](#user-content-22--命名)

　　[2.3  注释](#user-content-23--注释)

　　　　[2.3.1  单行注释](#user-content-231--单行注释)

　　　　[2.3.2  多行注释](#user-content-232--多行注释)

　　　　[2.3.3  文件注释](#user-content-233--文件注释)

[3  语言特性](#user-content-3--语言特性)

　　[3.1  变量](#user-content-31--变量)

　　[3.2  条件](#user-content-32--条件)

　　[3.3  循环](#user-content-33--循环)

　　[3.4  类型](#user-content-34--类型)

　　　　[3.4.1  类型转换](#user-content-341--类型转换)

　　[3.5  字符串](#user-content-35--字符串)

　　[3.6  对象](#user-content-36--对象)

　　[3.7  数组](#user-content-37--数组)

　　[3.8  函数](#user-content-38--函数)

　　　　[3.8.1  函数长度](#user-content-381--函数长度)

　　　　[3.8.2  参数设计](#user-content-382--参数设计)

　　　　[3.8.3  闭包](#user-content-383--闭包)

　　　　[3.8.4  空函数](#user-content-384--空函数)

　　[3.9  动态特性](#user-content-39--动态特性)

　　　　[3.9.1  eval](#user-content-391--eval)

　　　　[3.9.2  with](#user-content-392--with)

　　　　[3.9.3  delete](#user-content-393--delete)

　　　　[3.9.4  对象属性](#user-content-394--对象属性)

[4  浏览器环境](#user-content-4--浏览器环境)

　　[4.1  模块化](#user-content-41--模块化)

　　　　[4.1.1  AMD](#user-content-411--AMD)

　　　　[4.1.2  define](#user-content-412--define)

　　[4.2  DOM](#user-content-42--DOM)

　　　　[4.2.1  元素获取](#user-content-421--元素获取)

　　　　[4.2.2  样式获取](#user-content-422--样式获取)

　　　　[4.2.3  样式设置](#user-content-423--样式设置)

　　　　[4.2.4  DOM操作](#user-content-424--DOM操作)

　　　　[4.2.5  DOM事件](#user-content-425--DOM事件)

##  1  前言

本文档的目标是使 JavaScript 代码风格保持一致，容易被理解和被维护。





##  2  代码风格





###  2.1  结构



####  2.1.1  缩进

**[强制] 使用 `4` 个空格做为一个缩进层级，不允许使用 `2` 个空格 或 `tab` 字符。**

**[强制] `switch` 下的 `case` 和 `default` 必须增加一个缩进层级。**

示例：

```javascript
// good
switch (variable) {

    case '1':
        // do...
        break;

    case '2':
        // do...
        break;

    default:
        // do...

}

// bad
switch (variable) {

case '1':
    // do...
    break;

case '2':
    // do...
    break;

default:
    // do...

}
```

####  2.1.2  空格



**[强制] 二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。**

示例：

```javascript
var a = !arr.length;
a++;
a = b + c;
```

 **[强制] 用作代码块起始的左花括号 `{` 前必须有一个空格。**

示例：

```javascript
// good
if (condition) {
}

while (condition) {
}

function funcName() {
}

// bad
if (condition){
}

while (condition){
}

function funcName(){
}
```

**[强制] `if / else / for / while / function / switch / do / try / catch / finally` 关键字后，必须有一个空格。**

示例：

```javascript
// good
if (condition) {
}

while (condition) {
}

(function () {
})();

// bad
if(condition) {
}

while(condition) {
}

(function() {
})();
```

**[强制] 在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格。**

示例：

```javascript
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

// bad
var obj = {
    a : 1,
    b:2,
    c :3
};
```

**[强制] 函数声明、具名函数表达式、函数调用中，函数名和 `(` 之间不允许有空格。**

示例：

```javascript
// good
function funcName() {
}

var funcName = function funcName() {
};

funcName();

// bad
function funcName () {
}

var funcName = function funcName () {
};

funcName ();
```

**[强制] `,` 和 `;` 前不允许有空格。如果不位于行尾，`,` 和 `;` 后必须跟一个空格。**

示例：

```javascript
// good
callFunc(a, b);

// bad
callFunc(a , b) ;
```

**[强制] 在函数调用、函数声明、括号表达式、属性访问、`if / for / while / switch / catch` 等语句中，`()` 和 `[]` 内紧贴括号部分不允许有空格。**

示例：

```javascript
// good

callFunc(param1, param2, param3);

save(this.list[this.indexes[i]]);

needIncream && (variable += increament);

if (num > list.length) {
}

while (len--) {
}


// bad

callFunc( param1, param2, param3 );

save( this.list[ this.indexes[ i ] ] );

needIncreament && ( variable += increament );

if ( num > list.length ) {
}

while ( len-- ) {
}
```

 **[强制] 单行声明的数组与对象，如果包含元素，`{}` 和 `[]` 内紧贴括号部分不允许包含空格。**

解释：

声明包含元素的数组与对象，只有当内部元素的形式较为简单时，才允许写在一行。元素复杂的情况，还是应该换行书写。

示例：

```javascript
// good
var arr1 = [];
var arr2 = [1, 2, 3];
var obj1 = {};
var obj2 = {name: 'obj'};
var obj3 = {
    name: 'obj',
    age: 20,
    sex: 1
};

// bad
var arr1 = [ ];
var arr2 = [ 1, 2, 3 ];
var obj1 = { };
var obj2 = { name: 'obj' };
var obj3 = {name: 'obj', age: 20, sex: 1};
```

####  2.1.3  换行

 **[强制] 每个独立语句结束后必须换行。**

 **[强制] 每行不得超过 `120` 个字符。**

解释：

超长的不可分割的代码允许例外，比如复杂的正则表达式。长字符串不在例外之列。

 **[强制] 运算符处换行时，运算符必须在新行的行首。**

示例：

```javascript
// good
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

var result = number1 + number2 + number3
    + number4 + number5;


// bad
if (user.isAuthenticated() &&
    user.isInRole('admin') &&
    user.hasAuthority('add-admin') ||
    user.hasAuthority('delete-admin')) {
    // Code
}

var result = number1 + number2 + number3 +
    number4 + number5;
```

**[强制] 在函数声明、函数表达式、函数调用、对象创建、数组创建、`for` 语句等场景中，不允许在 `,` 或 `;` 前换行。**

****示例：

```javascript
// good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);


// bad
var obj = {
    a: 1
    , b: 2
    , c: 3
};

foo(
    aVeryVeryLongArgument
    , anotherVeryLongArgument
    , callback
);
```

 **[建议] 不同行为或逻辑的语句集，使用空行隔开，更易阅读。**

示例：

```javascript
// 仅为按逻辑换行的示例，不代表setStyle的最优实现
function setStyle(element, property, value) {
    if (element == null) {
        return;
    }

    element.style[property] = value;
}
```

 **[建议] 在语句的行长度超过 `120` 时，根据逻辑条件合理缩进。**

示例：

```javascript
// 较复杂的逻辑条件组合，将每个条件独立一行，逻辑运算符放置在行首进行分隔，或将部分逻辑按逻辑组合进行分隔。
// 建议最终将右括号 ) 与左大括号 { 放在独立一行，保证与 `if` 内语句块能容易视觉辨识。
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

// 按一定长度截断字符串，并使用 + 运算符进行连接。
// 分隔字符串尽量按语义进行，如不要在一个完整的名词中间断开。
// 特别的，对于 HTML 片段的拼接，通过缩进，保持和 HTML 相同的结构。
var html = '' // 此处用一个空字符串，以便整个 HTML 片段都在新行严格对齐
    + '<article>'
    +     '<h1>Title here</h1>'
    +     '<p>This is a paragraph</p>'
    +     '<footer>Complete</footer>'
    + '</article>';

// 也可使用数组来进行拼接，相对 `+` 更容易调整缩进。
var html = [
    '<article>',
        '<h1>Title here</h1>',
        '<p>This is a paragraph</p>',
        '<footer>Complete</footer>',
    '</article>'
];
html = html.join('');

// 当参数过多时，将每个参数独立写在一行上，并将结束的右括号 ) 独立一行。
// 所有参数必须增加一个缩进。
foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);

// 也可以按逻辑对参数进行组合。
// 最经典的是 baidu.format 函数，调用时将参数分为“模板”和“数据”两块
baidu.format(
    dateFormatTemplate,
    year, month, date, hour, minute, second
);

// 当函数调用时，如果有一个或以上参数跨越多行，应当每一个参数独立一行。
// 这通常出现在匿名函数或者对象初始化等作为参数时，如 `setTimeout` 函数等。
setTimeout(
    function () {
        alert('hello');
    },
    200
);

order.data.read(
    'id=' + me.model.id,
    function (data) {
        me.attchToModel(data.result);
        callback();
    },
    300
);

// 链式调用较长时采用缩进进行调整。
$('#items')
    .find('.selected')
    .highlight()
    .end();

// 三元运算符由3部分组成，因此其换行应当根据每个部分的长度不同，形成不同的情况。
var result = thisIsAVeryVeryLongCondition
    ? resultA : resultB;

var result = condition
    ? thisIsAVeryVeryLongResult
    : resultB;

// 数组和对象初始化的混用，严格按照每个对象的 `{` 和结束 `}` 在独立一行的风格书写。
var array = [
    {
        // ...
    },
    {
        // ...
    }
];
```

 **[建议] 对于 `if...else...`、`try...catch...finally` 等语句，推荐使用在 `}` 号后添加一个换行 的风格，使代码层次结构更清晰，阅读性更好。**

****示例：

```javascript
if (condition) {
    // some statements;
}
else {
    // some statements;
}

try {
    // some statements;
}
catch (ex) {
    // some statements;
}
```



####  2.1.4  语句

**[强制] 不得省略语句结束的分号。**

**[强制] 在 `if / else / for / do / while` 语句中，即使只有一行，也不得省略块 `{...}`。**

示例：

```javascript
// good
if (condition) {
    callFunc();
}

// bad
if (condition) callFunc();
if (condition)
    callFunc();
```

 **[强制] 函数定义结束不允许添加分号。**

示例：

```javascript
// good
function funcName() {
}

// bad
function funcName() {
};

// 如果是函数表达式，分号是不允许省略的。
var funcName = function () {
};
```

 **[强制] `IIFE` 必须在函数表达式外添加 `(`，非 `IIFE` 不得在函数表达式外添加 `(`。**

解释：

IIFE = Immediately-Invoked Function Expression.

额外的 ( 能够让代码在阅读的一开始就能判断函数是否立即被调用，进而明白接下来代码的用途。而不是一直拖到底部才恍然大悟。

示例：

```javascript
// good
var task = (function () {
   // Code
   return result;
})();

var func = function () {
};


// bad
var task = function () {
    // Code
    return result;
}();

var func = (function () {
});
```





###  2.2  命名

 **[强制] `变量` 使用 `Camel命名法`。**

示例：

```javascript
var loadingModules = {};
```

 **[强制] `常量` 使用 `全部字母大写，单词间下划线分隔` 的命名方式。**

示例：

```javascript
var HTML_ENTITY = {};
```

**[强制] `函数` 使用 `Camel命名法`。**

示例：

```javascript
function stringFormat(source) {
}
```

**[强制] 函数的 `参数` 使用 `Camel命名法`。**

示例：

```javascript
function hear(theBells) {
}
```

 **[强制] `类` 使用 `Pascal命名法`。**

示例：

```javascript
function TextNode(options) {
}
```

 **[强制] 类的 `方法` / `属性` 使用 `Camel命名法`。**

示例：

```javascript
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};
```

**[强制] `枚举变量` 使用 `Pascal命名法`，`枚举的属性` 使用 `全部字母大写，单词间下划线分隔` 的命名方式。**

示例：

```javascript
var TargetState = {
    READING: 1,
    READED: 2,
    APPLIED: 3,
    READY: 4
};
```

**[强制] `命名空间` 使用 `Camel命名法`。**

示例：

```javascript
equipments.heavyWeapons = {};
```

**[强制] 由多个单词组成的缩写词，在命名中，根据当前命名法和出现的位置，所有字母的大小写与首字母的大小写保持一致。**

示例：

```javascript
function XMLParser() {
}

function insertHTML(element, html) {
}

var httpRequest = new HTTPRequest();
```

**[强制] `类名` 使用 `名词`。**

示例：

```javascript
function Engine(options) {
}
```

**[建议] `函数名` 使用 `动宾短语`。**

示例：

```javascript
function getStyle(element) {
}
```

**[建议] `boolean` 类型的变量使用 `is` 或 `has` 开头。**

示例：

```javascript
var isReady = false;
var hasMoreCommands = false;
```



###  2.3  注释

####  2.3.1  单行注释

**[强制] 必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。**

####  2.3.2  多行注释

**[建议] 避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。**

####  2.3.3  文件注释

**[强制] 文件顶部必须包含文件注释**

示例：

```javascript
/**
 * 该模块实现了……
 */
```



##  3  语言特性





###  3.1  变量

**[强制] 变量、函数在使用前必须先定义。**

解释：

不通过 var 定义变量将导致变量污染全局环境。

示例：

```javascript
// good
var name = 'MyName';

// bad
name = 'MyName';
```

**[强制] 每个 `var` 只能声明一个变量。**

解释：

一个 `var` 声明多个变量，容易导致较长的行长度，并且在修改时容易造成逗号和分号的混淆。

示例：

```javascript
// good
var hangModules = [];
var missModules = [];
var visited = {};

// bad
var hangModules = [],
    missModules = [],
    visited = {};
```

**[强制] 变量必须 `即用即声明`，不得在函数或其它形式的代码块起始位置统一声明所有变量。**

解释：

变量声明与使用的距离越远，出现的跨度越大，代码的阅读与维护成本越高。虽然JavaScript的变量是函数作用域，还是应该根据编程中的意图，缩小变量出现的距离空间。

示例：

```javascript
// good
function kv2List(source) {
    var list = [];

    for (var key in source) {
        if (source.hasOwnProperty(key)) {
            var item = {
                k: key,
                v: source[key]
            };

            list.push(item);
        }
    }

    return list;
}

// bad
function kv2List(source) {
    var list = [];
    var key;
    var item;

    for (key in source) {
        if (source.hasOwnProperty(key)) {
            item = {
                k: key,
                v: source[key]
            };

            list.push(item);
        }
    }

    return list;
}
```





###  3.2  条件

**[建议] 尽可能使用简洁的表达式。**

示例：

```javascript
// 字符串为空

// good
if (!name) {
    // ......
}

// bad
if (name === '') {
    // ......
}
```

```javascript
// 字符串非空

// good
if (name) {
    // ......
}

// bad
if (name !== '') {
    // ......
}
```

```javascript
// 数组非空

// good
if (collection.length) {
    // ......
}

// bad
if (collection.length > 0) {
    // ......
}
```

```javascript
// 布尔不成立

// good
if (!notTrue) {
    // ......
}

// bad
if (notTrue === false) {
    // ......
}
```

```javascript
// null 或 undefined

// good
if (noValue == null) {
  // ......
}

// bad
if (noValue === null || typeof noValue === 'undefined') {
  // ......
}
```

**[建议] 按执行频率排列分支的顺序。**

解释：

按执行频率排列分支的顺序好处是：

1. 阅读的人容易找到最常见的情况，增加可读性。
2. 提高执行效率。

**[建议] 对于相同变量或表达式的多值条件，用 `switch` 代替 `if`。**

示例：

```javascript
// good
switch (typeof variable) {
    case 'object':
        // ......
        break;
    case 'number':
    case 'boolean':
    case 'string':
        // ......
        break;
}

// bad
var type = typeof variable;
if (type === 'object') {
    // ......
}
else if (type === 'number' || type === 'boolean' || type === 'string') {
    // ......
}
```

**[建议] 如果函数或全局中的 `else` 块后没有任何语句，可以删除 `else`。**

示例：

```javascript
// good
function getName() {
    if (name) {
        return name;
    }

    return 'unnamed';
}

// bad
function getName() {
    if (name) {
        return name;
    }
    else {
        return 'unnamed';
    }
}
```





###  3.3  循环

**[建议] 不要在循环体中包含函数表达式，事先将函数提取到循环体外。**

解释：

循环体中的函数表达式，运行过程中会生成循环次数个函数对象。

示例：

```javascript
// good
function clicker() {
    // ......
}

for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', clicker);
}


// bad
for (var i = 0, len = elements.length; i < len; i++) {
    var element = elements[i];
    addListener(element, 'click', function () {});
}
```



###  3.4  类型

####  3.4.1  类型转换

**[建议] 转换成 `string` 时，使用 `+ ''`。**

示例：

```javascript
// good
num + '';

// bad
new String(num);
num.toString();
String(num);
```

[建**议] 转换成 `number` 时，通常使用 `+`。**

示例：

```javascript
// good
+str;

// bad
Number(str);
parseInt(str);
```

**[建议] 转换成 `boolean` 时，使用 `!!`。**

示例：

```javascript
var num = 3.14;
!!num;
```



###  3.5  字符串

**[强制] 字符串开头和结束使用单引号 `'`。**

解释：

1. 输入单引号不需要按住 `shift`，方便输入。
2. 实际使用中，字符串经常用来拼接 HTML。为方便 HTML 中包含双引号而不需要转义写法。

示例：

```javascript
var str = '我是一个字符串';
var html = '<div class="cls">拼接HTML可以省去双引号转义</div>';
```



###  3.6  对象

**[强制] 使用对象字面量 `{}` 创建新 `Object`。**

示例：

```javascript
// good
var obj = {};

// bad
var obj = new Object();
```

**[强制] 不允许修改和扩展任何原生对象和宿主对象的原型。**

示例：

```javascript
// 以下行为绝对禁止
String.prototype.trim = function () {
};
```

**[建议] `for in` 遍历对象时, 使用 `hasOwnProperty` 过滤掉原型中的属性。**

示例：

```javascript
var newInfo = {};
for (var key in info) {
    if (info.hasOwnProperty(key)) {
        newInfo[key] = info[key];
    }
}
```



###  3.7  数组

**[强制] 使用数组字面量 `[]` 创建新数组，除非想要创建的是指定长度的数组。**

示例：

```javascript
// good
var arr = [];

// bad
var arr = new Array();
```

**[强制] 遍历数组不使用 `for in`。**

解释：

数组对象可能存在数字以外的属性, 这种情况下 `for in` 不会得到正确结果。

示例：

```javascript
var arr = ['a', 'b', 'c'];

// 这里仅作演示, 实际中应使用 Object 类型
arr.other = 'other things';

// 正确的遍历方式
for (var i = 0, len = arr.length; i < len; i++) {
    console.log(i);
}

// 错误的遍历方式
for (var i in arr) {
    console.log(i);
}
```

**[建议] 清空数组使用 `.length = 0`。**



###  3.8  函数



####  3.8.1  函数长度

**[建议] 一个函数的长度控制在 `50` 行以内。**

解释：

将过多的逻辑单元混在一个大函数中，易导致难以维护。一个清晰易懂的函数应该完成单一的逻辑单元。复杂的操作应进一步抽取，通过函数的调用来体现流程。

特定算法等不可分割的逻辑允许例外。

示例：

```javascript
function syncViewStateOnUserAction() {
    if (x.checked) {
        y.checked = true;
        z.value = '';
    }
    else {
        y.checked = false;
    }

    if (a.value) {
        warning.innerText = '';
        submitButton.disabled = false;
    }
    else {
        warning.innerText = 'Please enter it';
        submitButton.disabled = true;
    }
}

// 直接阅读该函数会难以明确其主线逻辑，因此下方是一种更合理的表达方式：

function syncViewStateOnUserAction() {
    syncXStateToView();
    checkAAvailability();
}

function syncXStateToView() {
    y.checked = x.checked;

    if (x.checked) {
        z.value = '';
    }
}

function checkAAvailability() {
    if (a.value) {
        clearWarnignForA();
    }
    else {
        displayWarningForAMissing();
    }
}
```

####  3.8.2  参数设计

**[建议] 一个函数的参数控制在 `6` 个以内。**

解释：

除去不定长参数以外，函数具备不同逻辑意义的参数建议控制在 `6` 个以内，过多参数会导致维护难度增大。

**[建议] 通过 `options` 参数传递非数据输入型参数。**

解释：

有些函数的参数并不是作为算法的输入，而是对算法的某些分支条件判断之用，此类参数建议通过一个 `options` 参数传递。

如下函数：

```javascript
/**
 * 移除某个元素
 *
 * @param {Node} element 需要移除的元素
 * @param {boolean} removeEventListeners 是否同时将所有注册在元素上的事件移除
 */
function removeElement(element, removeEventListeners) {
    element.parent.removeChild(element);

    if (removeEventListeners) {
        element.clearEventListeners();
    }
}
```

可以转换为下面的签名：

```javascript
/**
 * 移除某个元素
 *
 * @param {Node} element 需要移除的元素
 * @param {Object} options 相关的逻辑配置
 * @param {boolean} options.removeEventListeners 是否同时将所有注册在元素上的事件移除
 */
function removeElement(element, options) {
    element.parent.removeChild(element);

    if (options.removeEventListeners) {
        element.clearEventListeners();
    }
}
```

这种模式有几个显著的优势：

- `boolean` 型的配置项具备名称，从调用的代码上更易理解其表达的逻辑意义。
- 当配置项有增长时，无需无休止地增加参数个数，不会出现 `removeElement(element, true, false, false, 3)` 这样难以理解的调用代码。
- 当部分配置参数可选时，多个参数的形式非常难处理重载逻辑，而使用一个 options 对象只需判断属性是否存在，实现得以简化。

####  3.8.3  闭包

**[建议] 使用 `IIFE` 避免 `Lift 效应`。**

解释：

在引用函数外部变量时，函数执行时外部变量的值由运行时决定而非定义时，最典型的场景如下：

```javascript
var tasks = [];
for (var i = 0; i < 5; i++) {
    tasks[tasks.length] = function () {
        console.log('Current cursor is at ' + i);
    };
}

var len = tasks.length;
while (len--) {
    tasks[len]();
}
```

以上代码对 tasks 中的函数的执行均会输出 `Current cursor is at 5`，往往不符合预期。

此现象称为 **Lift 效应** 。解决的方式是通过额外加上一层闭包函数，将需要的外部变量作为参数传递来解除变量的绑定关系：

```javascript
var tasks = [];
for (var i = 0; i < 5; i++) {
    // 注意有一层额外的闭包
    tasks[tasks.length] = (function (i) {
        return function () {
            console.log('Current cursor is at ' + i);
        };
    })(i);
}

var len = tasks.length;
while (len--) {
    tasks[len]();
}
```

####  3.8.4  空函数

**[建议] 空函数不使用 `new Function()` 的形式。**

示例：

```javascript
var emptyFunction = function () {};
```

**[建议] 对于性能有高要求的场合，建议存在一个空函数的常量，供多处使用共享。**

示例：

```javascript
var EMPTY_FUNCTION = function () {};

function MyClass() {
}

MyClass.prototype.abstractMethod = EMPTY_FUNCTION;
MyClass.prototype.hooks.before = EMPTY_FUNCTION;
MyClass.prototype.hooks.after = EMPTY_FUNCTION;
```



###  3.9  动态特性

####  3.9.1  eval

**[建议] 避免使用 `eval` 函数。**

如果有特殊情况需要使用 `eval`，需在代码中用详细的注释说明为何必须使用 `eval`，同时需要其他资深工程师进行 Code Review。

####  3.9.2  with

**[建议] 尽量不要使用 `with`。**

####  3.9.3  delete

**[建议] 尽量不要使用 `delete` 。**

####  3.9.4  对象属性

**[建议] 避免修改外部传入的对象。**

解释：

JavaScript 因其脚本语言的动态特性，当一个对象未被 seal 或 freeze 时，可以任意添加、删除、修改属性值。

但是随意地对 非自身控制的对象 进行修改，很容易造成代码在不可预知的情况下出现问题。因此，设计良好的组件、函数应该避免对外部传入的对象的修改。

下面代码的 **selectNode** 方法修改了由外部传入的 **datasource** 对象。如果 **datasource** 用在其它场合（如另一个 Tree 实例）下，会造成状态的混乱。

```javascript
function Tree(datasource) {
    this.datasource = datasource;
}

Tree.prototype.selectNode = function (id) {
    // 从datasource中找出节点对象
    var node = this.findNode(id);
    if (node) {
        node.selected = true;
        this.flushView();
    }
};
```

对于此类场景，需要使用额外的对象来维护，使用由自身控制，不与外部产生任何交互的 **selectedNodeIndex** 对象来维护节点的选中状态，不对 **datasource** 作任何修改。

```javascript
function Tree(datasource) {
    this.datasource = datasource;
    this.selectedNodeIndex = {};
}

Tree.prototype.selectNode = function (id) {

    // 从datasource中找出节点对象
    var node = this.findNode(id);

    if (node) {
        this.selectedNodeIndex[id] = true;
        this.flushView();
    }

};
```

除此之外，也可以通过 deepClone 等手段将自身维护的对象与外部传入的分离，保证不会相互影响。





##  4  浏览器环境



###  4.1  模块化

####  4.1.1  AMD

**[强制] 使用 `AMD` 作为模块定义。**

解释：

AMD 作为由社区认可的模块定义形式，提供多种重载提供灵活的使用方式，并且绝大多数优秀的 Library 都支持 AMD，适合作为规范。

####  4.1.2  define

**[建议] 使用 `define(factory)` 的形式进行模块定义。**

示例：

```javascript
define(
    function (require) {
    }
);
```

[建议] 使用变量 `exports` 来描述返回的模块定义。

示例：

```javascript
define(
    function (require) {
        var exports = {};

        // ...

        return exports;
    }
);
```





###  4.2  DOM

####  4.2.1  元素获取

**[建议] 对于单个元素，尽可能使用 `document.getElementById` 获取，避免使用`document.all`。**

**[建议] 对于多个元素的集合，尽可能使用 `context.getElementsByTagName` 获取。其中 `context` 可以为 `document` 或其他元素。指定 `tagName` 参数为 `*` 可以获得所有子元素。**

**[建议] 遍历元素集合时，尽量缓存集合长度。如需多次操作同一集合，则应将集合转为数组。**

解释：

原生获取元素集合的结果并不直接引用 DOM 元素，而是对索引进行读取，所以 DOM 结构的改变会实时反映到结果中。

示例：

```html
<div></div>
<span></span>

<script>
var elements = document.getElementsByTagName('*');

// 显示为 DIV
alert(elements[0].tagName);

var div = elements[0];
var p = document.createElement('p');
docpment.body.insertBefore(p, div);

// 显示为 P
alert(elements[0].tagName);
</script>
```

**[建议] 获取元素的直接子元素时使用 `children`。避免使用`childNodes`，除非预期是需要包含文本、注释和属性类型的节点。**



####  4.2.2  样式获取

**[建议] 获取元素实际样式信息时，应使用 `getComputedStyle` 或 `currentStyle`。**

解释：

通过 style 只能获得内联定义或通过 JavaScript 直接设置的样式。通过 CSS class 设置的元素样式无法直接通过 style 获取。



####  4.2.3  样式设置

**[建议] 尽可能通过为元素添加预定义的 className 来改变元素样式，避免直接操作 style 设置。**

**[强制] 通过 style 对象设置元素样式时，对于带单位非 0 值的属性，不允许省略单位。**

解释：

除了 IE，标准浏览器会忽略不规范的属性值，导致兼容性问题。



####  4.2.4  DOM操作

**[建议] 操作 `DOM` 时，尽量减少页面 `reflow`。**

解释：

页面 reflow 是非常耗时的行为，非常容易导致性能瓶颈。下面一些场景会触发浏览器的reflow：

- DOM元素的添加、修改（内容）、删除。
- 应用新的样式或者修改任何影响元素布局的属性。
- Resize浏览器窗口、滚动页面。
- 读取元素的某些属性（offsetLeft、offsetTop、offsetHeight、offsetWidth、scrollTop/Left/Width/Height、clientTop/Left/Width/Height、getComputedStyle()、currentStyle(in IE)) 。

**[建议] 尽量减少 `DOM` 操作。**

解释：

DOM 操作也是非常耗时的一种操作，减少 DOM 操作有助于提高性能。举一个简单的例子，构建一个列表。我们可以用两种方式：

1. 在循环体中 createElement 并 append 到父元素中。
2. 在循环体中拼接 HTML 字符串，循环结束后写父元素的 innerHTML。

第一种方法看起来比较标准，但是每次循环都会对 DOM 进行操作，性能极低。在这里推荐使用第二种方法。



####  4.2.5  DOM事件

**[建议] 使用 `addEventListener` 绑定事件，且第三个参数使用 false。**