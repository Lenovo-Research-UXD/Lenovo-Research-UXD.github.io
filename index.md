# UXD Code Guideline

2021年7月1日

## PART1  代码规范

### 0 命名原则

#### 以小驼峰形式命名

第一个字母小写，剩下的每个单词的首字母大写。

#### 常量可以采用全大写的形式，但普通的`const`修饰的变量不应该大写

#### 两个字母的缩略词都大写，大于两个则改驼峰

#### 下划线是有特定意义的，不要乱用

#### 使用具描述性的名字

- 命名要精确表意，不能太宽泛，更不能词不达意
  - 同一个事物可能有多个单词适配，选最合适的
  - 同一个词有多种含义
- 使用业务术语。应避免从电脑的视角去命名，而是应该从人类认识事物的角度去命名
- 尽量避免用缩略语。
- 避免使用黑话。

#### 用词应尽量精简，无法精简长些也无妨，不能为了精简而放弃语义

#### 在上下文中保证意义明确

命名不应该重复上下文信息

#### 保证动词的统一性

常用的动词有`get` `set` `read` `create` `add` `update` `reset` `delete` `remove`等

#### 函数或方法名尽量采用动词或判断性词汇

函数名一般由一个 动词 加一个 名词 组成，如 getUser getInfo isArray

#### 布尔值的命名

布尔值一般用`is` `can` `has` `need`等助动词开头，如 isVisible hasLicense canEvaluate shouldAbort。返回布尔值的函数或方法，命名规则相同，如 Array.isArray(arr)。但这样容易出现函数名和变量名冲突的情况，这个时候可以在函数前加`check` `get`等区分

#### 数值的命名

首选有意义的简短命名，如 width length count，如果没有合适的就采用 numberOfXXX xxxCount 之类的通用命名

#### 类名的命名

以名词命名，首字母大写

#### 字典(Map)的命名

使用 valuesByKey 的方式，如 usersByID

### 1 命名规则

#### 项目命名

全部采用小写方式，以下划线分隔

#### 目录命名

参考项目命名规则；有复数时，采用复数命名法

### 2 HTML规范

#### 语法

- 缩进使用soft tab(4个空格)
- 嵌套的节点应缩进
- 在属性上使用双引号，不要使用单引号
- 属性名全小写，用中划线`-`做分隔符
- 不要在自动闭合标签结尾使用斜线
- 不要忽略可选的关闭标签

#### HTML5 doctype

在页面开头使用doctype来启用标准模式，使其在每个浏览器中尽可能一致的展现； 

```html
<!DOCTYPE html>
<html>
    ...
</html>
```

#### lang属性

在html标签上加上lang属性，这会对语音工具和翻译工具有帮助。

```html
<!DOCTYPE html>
<html lang="en-us">
    ...
</html>
```

sitepoint的[语言列表](http://reference.sitepoint.com/html/lang-codes)
微软给出的[详细语言列表](http://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx),其中细分了zh-cn,zh-hk,zh-tw等等

#### 字符编码

通常指定为`UTF-8`

#### IE兼容模式

用`<meta>`指定页面用什么版本的IE来渲染

#### CSS/JS引入

引入时不需要指明`type`，因为有默认值`text/css`和`text/javascript`
HTML5规范链接

- [使用link](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
- [使用style](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
- [使用script](http://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)

```html
<!-- External CSS -->
<link rel="stylesheet" href="code_guide.css">

<!-- In-document CSS -->
<style>
    ...
</style>

<!-- External JS -->
<script src="code_guide.js"></script>

<!-- In-document JS -->
<script>
    ...
</script>
```

#### 属性顺序

属性应该以特定顺序出现 以保证易读性

1. `class`
2. `id`
3. `name`
4. `data-*`
5. `src` `for` `type` `href` `value` `max-length` `max` `min` `pattern`
6. `placeholder` `title` `alt`
7. `aria-*` `role`
8. `required` `readonly` `disabled`

```html
<a class="..." id="..." data-modal="toggle" href="#">Example link</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

#### boolean属性

boolean属性指不需要声明取值的属性。但XHTML需要每个属性声明取值，HTML5不需要。

>boolean属性存在 即表示取值为true 不存在即表示取值为false

#### JS生成标签

在JS文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。

#### 减少标签数量

避免多余的父节点

```html
<!-- Not well -->
<span class="avatar">
    <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

#### ✨实用高于完美

尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；
任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

### 3 css/sass

#### 缩进

使用soft tab(4个空格)

#### 分号

每个属性声明末尾都要加分号

#### 空格

以下情况不需要空格

- 属性名后
- 多个规则的分隔符`,`前
- `!important`的`!`后
- 属性值`(`后、`)前`
- 行末不要有多余的空格

以下情况需要空格

- 属性值前
- 选择器`>`、`+`、`~`前后
- `{`前
- `!important`的`!`前
- `@else`前后
- 属性值中的`,`后
- 注释`/*`后 `*/`前

#### 空行

以下几种情况需要空行：

- 文件最后保留一个空行
- '}'后最好跟一个空行，包括scss中嵌套的规则
- 属性之间需要适当的空行，具体见[属性声明顺序](http://alloyteam.github.io/CodeGuide/#css-declaration-order)

#### 换行

以下几种情况不需要换行：

- '{'前

以下几种情况需要换行：

- '{'后和'}'前
- 每个属性独占一行
- 多个规则的分隔符','后

#### 注释

- 注释统一用'/* */'（scss中也不要用'//'），具体参照右边的写法；
- 缩进与下一行代码保持一致；
- 可位于一个代码行的末尾，与代码间隔一个空格。

#### 引号

- 最外层统一使用双引号；
- url的内容要用引号；
- 属性选择器中的属性值需要引号。

#### 命名

- 类名使用小写字母，以中划线分隔
- id采用驼峰式命名
- scss中的变量、函数、混合、placeholder采用驼峰式命名

#### 属性声明顺序

相关的属性声明按右边的顺序做分组处理，组之间需要有一个空行。

```css
.declaration-order {
    display: block;
    float: right;

    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;

    border: 1px solid #e5e5e5;
    border-radius: 3px;
    width: 100px;
    height: 100px;

    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    text-align: center;

    color: #333;
    background-color: #f5f5f5;

    opacity: 1;
}
```

下面是推荐的属性的顺序

```css
[
    [
        "display",
        "visibility",
        "float",
        "clear",
        "overflow",
        "overflow-x",
        "overflow-y",
        "clip",
        "zoom"
    ],
    [
        "table-layout",
        "empty-cells",
        "caption-side",
        "border-spacing",
        "border-collapse",
        "list-style",
        "list-style-position",
        "list-style-type",
        "list-style-image"
    ],
    [
        "-webkit-box-orient",
        "-webkit-box-direction",
        "-webkit-box-decoration-break",
        "-webkit-box-pack",
        "-webkit-box-align",
        "-webkit-box-flex"
    ],
    [
        "position",
        "top",
        "right",
        "bottom",
        "left",
        "z-index"
    ],
    [
        "margin",
        "margin-top",
        "margin-right",
        "margin-bottom",
        "margin-left",
        "-webkit-box-sizing",
        "-moz-box-sizing",
        "box-sizing",
        "border",
        "border-width",
        "border-style",
        "border-color",
        "border-top",
        "border-top-width",
        "border-top-style",
        "border-top-color",
        "border-right",
        "border-right-width",
        "border-right-style",
        "border-right-color",
        "border-bottom",
        "border-bottom-width",
        "border-bottom-style",
        "border-bottom-color",
        "border-left",
        "border-left-width",
        "border-left-style",
        "border-left-color",
        "-webkit-border-radius",
        "-moz-border-radius",
        "border-radius",
        "-webkit-border-top-left-radius",
        "-moz-border-radius-topleft",
        "border-top-left-radius",
        "-webkit-border-top-right-radius",
        "-moz-border-radius-topright",
        "border-top-right-radius",
        "-webkit-border-bottom-right-radius",
        "-moz-border-radius-bottomright",
        "border-bottom-right-radius",
        "-webkit-border-bottom-left-radius",
        "-moz-border-radius-bottomleft",
        "border-bottom-left-radius",
        "-webkit-border-image",
        "-moz-border-image",
        "-o-border-image",
        "border-image",
        "-webkit-border-image-source",
        "-moz-border-image-source",
        "-o-border-image-source",
        "border-image-source",
        "-webkit-border-image-slice",
        "-moz-border-image-slice",
        "-o-border-image-slice",
        "border-image-slice",
        "-webkit-border-image-width",
        "-moz-border-image-width",
        "-o-border-image-width",
        "border-image-width",
        "-webkit-border-image-outset",
        "-moz-border-image-outset",
        "-o-border-image-outset",
        "border-image-outset",
        "-webkit-border-image-repeat",
        "-moz-border-image-repeat",
        "-o-border-image-repeat",
        "border-image-repeat",
        "padding",
        "padding-top",
        "padding-right",
        "padding-bottom",
        "padding-left",
        "width",
        "min-width",
        "max-width",
        "height",
        "min-height",
        "max-height"
    ],
    [
        "font",
        "font-family",
        "font-size",
        "font-weight",
        "font-style",
        "font-letiant",
        "font-size-adjust",
        "font-stretch",
        "font-effect",
        "font-emphasize",
        "font-emphasize-position",
        "font-emphasize-style",
        "font-smooth",
        "line-height",
        "text-align",
        "-webkit-text-align-last",
        "-moz-text-align-last",
        "-ms-text-align-last",
        "text-align-last",
        "vertical-align",
        "white-space",
        "text-decoration",
        "text-emphasis",
        "text-emphasis-color",
        "text-emphasis-style",
        "text-emphasis-position",
        "text-indent",
        "-ms-text-justify",
        "text-justify",
        "letter-spacing",
        "word-spacing",
        "-ms-writing-mode",
        "text-outline",
        "text-transform",
        "text-wrap",
        "-ms-text-overflow",
        "text-overflow",
        "text-overflow-ellipsis",
        "text-overflow-mode",
        "-ms-word-wrap",
        "word-wrap",
        "-ms-word-break",
        "word-break"
    ],
    [
        "color",
        "background",
        "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader",
        "background-color",
        "background-image",
        "background-repeat",
        "background-attachment",
        "background-position",
        "-ms-background-position-x",
        "background-position-x",
        "-ms-background-position-y",
        "background-position-y",
        "-webkit-background-clip",
        "-moz-background-clip",
        "background-clip",
        "background-origin",
        "-webkit-background-size",
        "-moz-background-size",
        "-o-background-size",
        "background-size"
    ],
    [
        "outline",
        "outline-width",
        "outline-style",
        "outline-color",
        "outline-offset",
        "opacity",
        "filter:progid:DXImageTransform.Microsoft.Alpha(Opacity",
        "-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha",
        "-ms-interpolation-mode",
        "-webkit-box-shadow",
        "-moz-box-shadow",
        "box-shadow",
        "filter:progid:DXImageTransform.Microsoft.gradient",
        "-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient",
        "text-shadow"
    ],
    [
        "-webkit-transition",
        "-moz-transition",
        "-ms-transition",
        "-o-transition",
        "transition",
        "-webkit-transition-delay",
        "-moz-transition-delay",
        "-ms-transition-delay",
        "-o-transition-delay",
        "transition-delay",
        "-webkit-transition-timing-function",
        "-moz-transition-timing-function",
        "-ms-transition-timing-function",
        "-o-transition-timing-function",
        "transition-timing-function",
        "-webkit-transition-duration",
        "-moz-transition-duration",
        "-ms-transition-duration",
        "-o-transition-duration",
        "transition-duration",
        "-webkit-transition-property",
        "-moz-transition-property",
        "-ms-transition-property",
        "-o-transition-property",
        "transition-property",
        "-webkit-transform",
        "-moz-transform",
        "-ms-transform",
        "-o-transform",
        "transform",
        "-webkit-transform-origin",
        "-moz-transform-origin",
        "-ms-transform-origin",
        "-o-transform-origin",
        "transform-origin",
        "-webkit-animation",
        "-moz-animation",
        "-ms-animation",
        "-o-animation",
        "animation",
        "-webkit-animation-name",
        "-moz-animation-name",
        "-ms-animation-name",
        "-o-animation-name",
        "animation-name",
        "-webkit-animation-duration",
        "-moz-animation-duration",
        "-ms-animation-duration",
        "-o-animation-duration",
        "animation-duration",
        "-webkit-animation-play-state",
        "-moz-animation-play-state",
        "-ms-animation-play-state",
        "-o-animation-play-state",
        "animation-play-state",
        "-webkit-animation-timing-function",
        "-moz-animation-timing-function",
        "-ms-animation-timing-function",
        "-o-animation-timing-function",
        "animation-timing-function",
        "-webkit-animation-delay",
        "-moz-animation-delay",
        "-ms-animation-delay",
        "-o-animation-delay",
        "animation-delay",
        "-webkit-animation-iteration-count",
        "-moz-animation-iteration-count",
        "-ms-animation-iteration-count",
        "-o-animation-iteration-count",
        "animation-iteration-count",
        "-webkit-animation-direction",
        "-moz-animation-direction",
        "-ms-animation-direction",
        "-o-animation-direction",
        "animation-direction"
    ],
    [
        "content",
        "quotes",
        "counter-reset",
        "counter-increment",
        "resize",
        "cursor",
        "-webkit-user-select",
        "-moz-user-select",
        "-ms-user-select",
        "user-select",
        "nav-index",
        "nav-up",
        "nav-right",
        "nav-down",
        "nav-left",
        "-moz-tab-size",
        "-o-tab-size",
        "tab-size",
        "-webkit-hyphens",
        "-moz-hyphens",
        "hyphens",
        "pointer-events"
    ]
]
```

#### 颜色

颜色16进制用小写字母；颜色16进制尽量用简写；

```css
/* not good */
.element {
    color: #ABCDEF;
    background-color: #001122;
}

/* good */
.element {
    color: #abcdef;
    background-color: #012;
}
```

#### 属性简写

属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以**建议尽量分开声明**会更加清晰；

`margin` 和 `padding` 相反，需要使用简写；

常见的属性简写包括：

- `font`
- `background`
- `transition`
- `animation`

#### 媒体查询

尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。

#### SCSS相关

提交的代码中不要有 `@debug`；

声明顺序：

- `@extend`
- 不包含 `@content` 的 `@include`
- 包含 `@content` 的 `@include`
- 自身属性
- 嵌套规则

`@import` 引入的文件不需要开头的'_'和结尾的'.scss'；

嵌套最多不能超过5层；

`@extend` 中使用placeholder选择器；

去掉不必要的父级引用符号'&'。

```css
/* not good */@import "_dialog.scss";/* good */@import "dialog";/* not good */.fatal {    @extend .error;}/* good */.fatal {    @extend %error;}/* not good */.element {    & > .dialog {        ...    }}/* good */.element {    > .dialog {        ...    }}
```

#### 杂项

不允许有空的规则；

元素选择器用小写字母；

去掉小数点前面的0；

去掉数字中不必要的小数点和末尾的0；

属性值'0'后面不要加单位；

同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法；

无前缀的标准属性应该写在有前缀的属性后面；

不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；

不要在一个文件里出现两个相同的规则；

用 `border: 0;` 代替 `border: none;`；

选择器不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写）；

发布的代码中不要有 `@import`；

尽量少用'*'选择器。

```css
/* not good */.element {}/* not good */LI {    ...}/* good */li {    ...}/* not good */.element {    color: rgba(0, 0, 0, 0.5);}/* good */.element {    color: rgba(0, 0, 0, .5);}/* not good */.element {    width: 50.0px;}/* good */.element {    width: 50px;}/* not good */.element {    width: 0px;}/* good */.element {    width: 0;}/* not good */.element {    border-radius: 3px;    -webkit-border-radius: 3px;    -moz-border-radius: 3px;    background: linear-gradient(to bottom, #fff 0, #eee 100%);    background: -webkit-linear-gradient(top, #fff 0, #eee 100%);    background: -moz-linear-gradient(top, #fff 0, #eee 100%);}/* good */.element {    -webkit-border-radius: 3px;       -moz-border-radius: 3px;            border-radius: 3px;    background: -webkit-linear-gradient(top, #fff 0, #eee 100%);    background:    -moz-linear-gradient(top, #fff 0, #eee 100%);    background:         linear-gradient(to bottom, #fff 0, #eee 100%);}/* not good */.element {    color: rgb(0, 0, 0);    width: 50px;    color: rgba(0, 0, 0, .5);}/* good */.element {    color: rgb(0, 0, 0);    color: rgba(0, 0, 0, .5);}
```

### 4 JavaScript/TypeScript

#### 缩进

使用soft tab（4个空格）

#### 单行长度

不要超过80，但如果编辑器开启word wrap可以不考虑单行长度。

#### 分号

以下几种情况后需加分号：

- 变量声明
- 表达式
- return
- throw
- break
- continue
- do-while

```js
/* let declaration */let x = 1;/* expression statement */x++;/* do-while */do {    x++;} while (x < 10);
```

#### 空格

以下情况不需要空格：

- 对象的属性名后
- 前缀一元运算符后
- 后缀一元运算符前
- 函数调用括号前
- 无论是函数声明还是函数表达式，'('前不要空格
- 数组的'['后和']'前
- 对象的'{'后和'}'前
- 运算符'('后和')'前

以下情况需要空格：

- 二元运算符前后
- 三元运算符'?:'前后
- 代码块'{'前
- 下列关键字前：`else`, `while`, `catch`, `finally`
- 下列关键字后：`if`, `else`, `for`, `while`, `do`, `switch`, `case`, `try`, `catch`, `finally`, `with`, `return`, `typeof`
- 单行注释'//'后（若单行注释和代码同行，则'//'前也需要），多行注释'*'后
- 对象的属性值前
- for循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
- 无论是函数声明还是函数表达式，'{'前一定要有空格
- 函数的参数之间

```js
// not goodlet a = {    b :1};// goodlet a = {    b: 1};// not good++ x;y ++;z = x?1:2;// good++x;y++;z = x ? 1 : 2;// not goodlet a = [ 1, 2 ];// goodlet a = [1, 2];// not goodlet a = ( 1+2 )*3;// goodlet a = (1 + 2) * 3;// no space before '(', one space before '{', one space between function parameterslet doSomething = function(a, b, c) {    // do something};// no space before '('doSomething(item);// not goodfor(i=0;i<6;i++){    x++;}// goodfor (i = 0; i < 6; i++) {    x++;}
```

#### 空行

以下几种情况需要空行：

- 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
- 注释前（当注释在代码块的第一行时，则无需空行）
- 代码块后（在函数调用、数组、对象中则无需空行）
- 文件最后保留一个空行

```js
// need blank line after letiable declarationlet x = 1;// not need blank line when letiable declaration is last expression in the current blockif (x >= 1) {    let y = x + 1;}let a = 2;// need blank line before line commenta++;function b() {    // not need blank line when comment is first line of block    return a;}// need blank line after blocksfor (let i = 0; i < 2; i++) {    if (true) {        return false;    }    continue;}let obj = {    foo: function() {        return 1;    },    bar: function() {        return 2;    }};// not need blank line when in argument list, array, objectfunc(    2,    function() {        a++;    },    3);let foo = [    2,    function() {        a++;    },    3];let foo = {    a: 2,    b: function() {        a++;    },    c: 3};
```

#### 换行

换行的地方，行末必须有','或者运算符；

以下几种情况不需要换行：

- 下列关键字后：`else`, `catch`, `finally`
- 代码块'{'前

以下几种情况需要换行：

- 代码块'{'后和'}'前
- 变量赋值后

```js
// not goodvar a = {    b: 1    , c: 2};x = y    ? 1 : 2;// goodvar a = {    b: 1,    c: 2};x = y ? 1 : 2;x = y ?    1 : 2;// no need line break with 'else', 'catch', 'finally'if (condition) {    ...} else {    ...}try {    ...} catch (e) {    ...} finally {    ...}// not goodfunction test(){    ...}// goodfunction test() {    ...}// not goodvar a, foo = 7, b,    c, bar = 8;// goodvar a,    foo = 7,    b, c, bar = 8;
```

#### 引号

最外层统一使用**单引号**

```js
// not goodvar x = "test";// goodvar y = 'foo',    z = '<div id="test"></div>';
```

#### 变量命名

- 标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到cgi返回的数据）
- 'ID'在变量名中全大写
- 'URL'在变量名中全大写
- 'Android'在变量名中大写第一个字母
- 'iOS'在变量名中小写第一个，大写后两个字母
- 常量全大写，用下划线连接
- 构造函数，大写第一个字母
- jquery对象必须以'$'开头命名

#### 变量声明

一个函数作用域中所有的变量声明尽量提到函数首部，根据情况采用let或const声明，尽量不采用var。

#### 函数

无论是函数声明还是函数表达式，'('前不要空格，但'{'前一定要有空格；

函数调用括号前不需要空格；

立即执行函数外必须包一层括号；

不要给inline function命名；

参数之间用', '分隔，注意逗号后有一个空格。

```js
// no space before '(', but one space before'{'
var doSomething = function(item) {
    // do something
};

function doSomething(item) {
    // do something
}

// not good
doSomething (item);

// good
doSomething(item);

// requires parentheses around immediately invoked function expressions
(function() {
    return 1;
})();

// not good
[1, 2].forEach(function x() {
    ...
});

// good
[1, 2].forEach(function() {
    ...
});

// not good
var a = [1, 2, function a() {
    ...
}];

// good
var a = [1, 2, function() {
    ...
}];

// use ', ' between function parameters
var doSomething = function(a, b, c) {
    // do something
};
```

#### 数组/对象

- 对象属性名不需要加引号；
- 对象以缩进的形式书写，不要写在一行；
- 数组、对象最后不要有逗号。

#### 括号

下列关键字后必须有大括号（即使代码块的内容只有一行）

`if`, `else`, `for`, `while`, `do`, `switch`, `try`, `catch`, `finally`, `with`。

#### null使用场景

适用场景：

- 初始化一个将来可能被赋值为对象的变量
- 与已经初始化的变量做比较
- 作为一个参数为对象的函数的调用传参
- 作为一个返回对象的函数的返回值

不适用场景：

- 不要用null来判断函数调用时有无传参
- 不要与未初始化的变量做比较

#### undefined判断

永远不要直接使用undefined进行变量判断；

使用typeof和字符串'undefined'对变量进行判断。

```js
// not good
if (person === undefined) {
    ...
}

// good
if (typeof person === 'undefined') {
    ...
}
```

#### jshint

- 用'===', '!=='代替'==', '!='；
- for-in里一定要有hasOwnProperty的判断；
- 不要在内置对象的原型上添加方法，如Array, Date；
- 不要在内层作用域的代码里声明了变量，之后却访问到了外层作用域的同名变量；
- 变量不要先使用后声明；
- 不要在一句代码中单单使用构造函数，记得将其赋值给某个变量；
- 不要在同个作用域下声明同名变量；
- 不要在一些不需要的地方加括号，例：delete(a.b)；
- 不要使用未声明的变量（全局变量需要加到.jshintrc文件的globals属性里面）；
- 不要声明了变量却不使用；
- 不要在应该做比较的地方做赋值；
- debugger不要出现在提交的代码里；
- 数组中不要存在空元素；
- 不要在循环内部声明函数；
- 不要像这样使用构造函数，例：`new function () { ... }`, `new Object`；

#### 杂项

- 不要混用tab和space；
- 不要在一处使用多个tab或space；
- 换行符统一用'LF'；
- 对上下文this的引用只能使用'_this', 'that', 'self'其中一个来命名；
- 行尾不要有空白字符；
- switch的falling through和no default的情况一定要有注释特别说明；
- 不允许有空的代码块。

```js
// not good
var a   = 1;

function Person() {
    // not good
    var me = this;

    // good
    var _this = this;

    // good
    var that = this;

    // good
    var self = this;
}

// good
switch (condition) {
    case 1:
    case 2:
        ...
        break;
    case 3:
        ...
    // why fall through
    case 4
        ...
        break;
    // why no default
}

// not good with empty block
if (condition) {

}
```

### 5 代码注释

注释虽然写起来很痛苦, 但对保证代码可读性至关重要。下面的规则描述了如何注释以及在哪儿注释. 当然也要记住: 注释固然很重要, 但最好的代码本身应该是自文档化. 有意义的类型名和变量名, 要远胜过要用注释解释的含糊不清的名字。

#### [JSDoc](https://jsdoc.app/)

如果你在项目中使用 JavaScript 作为开发语言，那么我强烈建议你使用 JSDoc。它可以为 VSCode 生成智能提示，从而使开发者很容易了解整个类和其中的属性和方法，并且快速知道如何使用，从而提高开发效率，降低维护成本。而且，VSCode 对于 JSDoc 的支持是开箱即用的。

如果你在项目中使用 TypeScript，依然应当使用 JSDoc 来作为文档注释。得益于 TypeScript 的类型系统，你通常只需要 `@param` 和 `@return` 标签即可。

> 注意：JSDoc 使用 Markdown 格式来编写。

以下内容均假设你已经在使用 JSDoc 进行注释。

#### 注释风格

除了使用 JSDoc 以外，你可能还需要使用普通的注释来解释你的代码，此时使用 `//` 或是 `/* */` 都可以，保证风格统一即可。

#### 单行注释

- 双斜线后，**必须跟一个空格**；
- **缩进**与下一行代码保持一致；
- 可位于一个代码行的末尾，与代码**间隔一个**空格。

#### 多行注释

最少三行, '*'后跟一个空格，具体参照下边的写法；

建议在以下情况下使用：

- 难于理解的代码段
- 可能存在错误的代码段
- 浏览器特殊的HACK代码
- 业务逻辑强相关的代码

```js
/*
 * one space after '*'
 */
let x = 1;
```

#### 文档注释

各类标签@param, @method等请参考[usejsdoc](http://usejsdoc.org/)和[JSDoc Guide](http://yuri4ever.github.io/jsdoc/)；

建议在以下情况下使用：

- 所有常量
- 所有函数
- 所有类

```js
/** * @func * @desc 一个带参数的函数 * @param {string} a - 参数a * @param {number} b=1 - 参数b默认值为1 * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx * @param {object} d - 参数d为一个对象 * @param {string} d.e - 参数d的e属性 * @param {string} d.f - 参数d的f属性 * @param {object[]} g - 参数g为一个对象数组 * @param {string} g.h - 参数g数组中一项的h属性 * @param {string} g.i - 参数g数组中一项的i属性 * @param {string} [j] - 参数j是一个可选参数 */function foo(a, b, c, d, g, j) {    ...}
```

#### 变量注释

如果根据本规则，那么变量名本身足以很好说明变量用途。但是在某些特殊情况下，你仍然需要为变量添加注释。

1. 类成员和对象属性应该用注释标注类型，说明含义以及用途。如果变量可以接受 NULL 或 -1 等警戒值, 须加以说明。
2. 全局变量应该用注释标注类型，说明含义以及用途。

#### 函数注释

注释位于声明之前, 对函数功能及用法进行描述。
函数声明处的注释应当至少包括以下内容:

1. 函数的描述
2. 函数的输参数及其类型
3. 函数的输出及其类型

你也可以添加其他标签，如 `@deprecated` 表示不推荐使用。

如果需要注释说明函数功能和实现要点，在函数内部使用普通注释即可。但是如果注释涉及到了某个变量，还是应当使用 JSDoc 来标注变量类型。

如果某个类方法是对子类中同签名方法的重写，则必须要添加`@override` 标签，此时 JSDoc 会从子类方法中继承标签，无需重复注释类型。

#### 类注释

每个类都应当附带一份注释，包括描述、参数、实现接口、可见性以及其他属性。类描述应当提供信息告诉其他人如何使用。

#### 枚举注释和类型定义

所有的枚举和类型定义都应当使用对应的 JSDoc 标签进行注释(`@enum` 或 `@typedef`)。枚举类型中每一个独立的枚举项也应使用 JSDoc 进行注释。

#### 类型注解

1. 非空 (non-null) 和可空 (nullable) 标识符

   类型系统定义了 `!` 和 `?` 运算符来表示非空和可空。原始类型 (`string`, `number`, `boolean`, `symbol`, `undefined`, `null`) 和字面量 (`{function(...): ...}` 和 `{{foo: string...}}`) 默认是非空类型，在类型前面加 `?` 可以使它们可空; 对于引用类型，应当显式使用 `?` 或 `!` 来表示它们是否可空。

2. 模板参数

   对于模板类型，必须显式指定其参数类型。例如:

   ``` javascript
    // bad const /** !Object */ users = {}; const /** !Array */ books = []; const /** !Promise */ response = ...;  // good const /** !Object<string, !User> */ users = {}; const /** !Array<string> */ books = []; const /** !Promise<!Response> */ response = ...; 
   ```

3. 函数类型表达式 (function type expression)

   > 函数类型表达式是指类型注解中带有`function`关键字的类型注解

   当有函数定义时，使用 `@param` 和 `@return` 进行注解，不要使用函数类型表达式。在将匿名函数或已定义函数赋值给变量时，才应该使用函数类型表达式。在使用函数类型表达式时，显式写出返回类型。

4. 格式要求

   在类型注解中，应当在每个逗号或分号后面插入一个空格或换行。额外的空行可以增加可读性，同时避免超过编辑器列宽限制。

### 6 代码校验

为了保证每个人的代码风格与本规范一致，应使用 [ESLint](http://eslint.cn/) + [Prettier](https://www.prettier.cn/) 来格式化代码。

ESLint 关闭格式化功能，仅启用静态检查功能，代码格式化检查由 Prettier 负责。

## PART2 GIT提交规范

### 1 项目负责人及分工

每个项目有一名负责人，项目由负责人在github上进行仓库初始化，并划分功能模块，每个项目成员在各自分支维护若干功能模块。

### 2 分支合并

分支合并时，由成员发起合并请求，项目负责人审核后可合并至主分支。

### 3 每日push

正常情况下，每位同学至少push一次当天工作内容，以便版本管理及个人任务量查看。

各commit标注清楚本次提交内容，便于其他成员查看。

### 4 Commit Message规范

Commit Message 参考 Angular 规范，并做了一定的简化。信息的提交格式为:

```
<type>(<scope>): <subject><BLANK LINE><body>
```

#### type

`type` 用于说明 commit 类型，只能是以下类型之一。

|   类型   |                描述                |
| :------: | :--------------------------------: |
|   feat   |            新增feature             |
|   fix    |              修复bug               |
|   docs   |             仅修改文档             |
|  style   |             仅修改格式             |
| refactor |              重构代码              |
|   perf   |              优化相关              |
|   test   | 测试相关，包括单元测试、集成测试等 |
|  chore   | 改变构建流程，或改动依赖库、工具等 |
|  revert  |                回滚                |

#### scope 

`scope` 用于说明 commit 影响的范围。如果没有合适的范围，可以使用 `*`。

#### subject 

`subject` 是 commit 目的的简短描述，其规则为:

- 不超过50个字符
- 以动词开头，使用第一人称现在时，比如change，而不是changed或changes
- 第一个字母小写
- 结尾不加句点

#### body (可选)

`body`是对本次 commit 的详细描述，可以分成多行。规则为：

- 使用第一人称现在时
- 应该说明代码变动的动机，以及与以前行为的对比。

### 5 Git Hooks

可以使用 [Git Hooks](https://git-scm.com/docs/githooks) 在代码提交前执行检察。最常见的用法是安装 [lint-staged](https://github.com/okonet/lint-staged#readme) 和 [Husky](https://github.com/typicode/husky#readme)，在`pre-commit`阶段执行检查，强制规范代码格式和 Commit Message。

## PART3 项目规范

### 1. 项目内容

我们推荐使用 [Visual Studio Code](https://code.visualstudio.com) 来编写项目代码。在你新建项目时，在根目录下新建 `.vscode` 文件夹，并在其中写入配置文件。你的 `.vscode` 文件夹中至少应包含如下文件:

1. `settings.json` - 用于统一编辑器和插件设置
2. `launch.json` - 用于调试项目

除此以外，你还可以提供 `extension.json` 来统一项目开发者使用的插件。

### 2. 项目管理

#### 项目分工及任务流

基于github project看板实现



## PART4 技术分享

### 1. 分享方式

时间：每周一上午11:00-11:30

地点：UXD实验室

成员：初雨墨、黄显鹏、李金星、沈祖煜

内容：以前端技术为主题，包括但不限于近期项目中遇到的问题及技术解决方案

### 2. 分享顺序

1. 初雨墨
2. 黄显鹏
3. 李金星

> 基于姓氏首字母排序



## PART5 成员技术栈及优势方向

> 确定个人技术优势方向，便于成员间请教问题

### 初雨墨

- 技术栈 - 前端: React/TypeScript，后端: Flask/Python

### 黄显鹏

- 技术栈 - vue2.0/js
- 擅长后台管理系统的前端实现
- 熟悉各种html布局方式，写过小程序

### 李金星

- 技术栈 - 前端vue3/javascript; 后端flask/python; 原生微信小程序
- 擅长动画特效绘制 - 基于CSS animation或 JS canvas
- 擅长css多数属性 - 可快速基于设计稿实现静态布局效果

### 沈祖煜

- 传感器等硬件开发方向

## 参考

1. [JavaScript变量命名](https://juejin.cn/post/6977245873797349413)
2. [Google JavaScript Style Guideline](https://google.github.io/styleguide/jsguide.html)
3. [Google TypeScript Style Guideline](https://google.github.io/styleguide/tsguide.html)
4. [AngularJS Git Commit Message Conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#)
5. [Code Guide by @AlloyTeam](http://alloyteam.github.io/CodeGuide/)