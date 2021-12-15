# UXD Code Guideline

2021 年 7 月 1 日

[TOC]



## PART1 代码规范

### 0 命名原则

1. 以小驼峰形式命名

   第一个字母小写，剩下的每个单词的首字母大写。

2. 常量可以采用全大写的形式，但普通的`const`修饰的变量不应该大写

3. 两个字母的缩略词都大写，大于两个则改驼峰

4. 下划线是有特定意义的，不要乱用

5. 使用具描述性的名字

   - 命名要精确表意，不能太宽泛，更不能词不达意
     - 同一个事物可能有多个单词适配，选最合适的
     - 同一个词有多种含义

   - 使用业务术语。应避免从电脑的视角去命名，而是应该从人类认识事物的角度去命名

   - 尽量避免用缩略语。

   - 避免使用黑话。


6. 用词应尽量精简，无法精简长些也无妨，不能为了精简而放弃语义

7. 在上下文中保证意义明确

   命名不应该重复上下文信息

8. 保证动词的统一性

   常用的动词有`get` `set` `read` `create` `add` `update` `reset` `delete` `remove`等

9. 函数或方法名尽量采用动词或判断性词汇

   函数名一般由一个 动词 加一个 名词 组成，如 getUser getInfo isArray

10. 布尔值的命名

    布尔值一般用`is` `can` `has` `need`等助动词开头，如 isVisible hasLicense canEvaluate shouldAbort。返回布尔值的函数或方法，命名规则相同，如 Array.isArray(arr)。但这样容易出现函数名和变量名冲突的情况，这个时候可以在函数前加`check` `get`等区分

11. 数值的命名

    首选有意义的简短命名，如 width length count，如果没有合适的就采用 numberOfXXX xxxCount 之类的通用命名

12. 类名的命名

    以名词命名，首字母大写

13. 字典(Map)的命名

    使用 valuesByKey 的方式，如 `usersByID`

### 1 命名规则

1. 项目命名

   全部采用小写方式，以下划线分隔

2. 目录命名

   参考项目命名规则；有复数时，采用复数命名法

### 2 HTML 规范

1. 语法

   - 缩进使用 soft tab(2 个空格)

   - 嵌套的节点应缩进

   - 在属性上使用双引号，不要使用单引号

   - 属性名全小写，用中划线`-`做分隔符

   - 不要在自动闭合标签结尾使用斜线

   - 不要忽略可选的关闭标签


2. HTML5 doctype

   在页面开头使用 doctype 来启用标准模式，使其在每个浏览器中尽可能一致的展现；

   ```html
   <!DOCTYPE html>
   <html>
     ...
   </html>
   ```

3. lang 属性

   在 html 标签上加上 lang 属性，这会对语音工具和翻译工具有帮助。

   ```html
   <!DOCTYPE html>
   <html lang="en-us">
     ...
   </html>
   ```

4. sitepoint 的[语言列表](http://reference.sitepoint.com/html/lang-codes)
   微软给出的[详细语言列表](<http://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx>),其中细分了 zh-cn,zh-hk,zh-tw 等等
   
5. 字符编码

   通常指定为`UTF-8`

6. IE 兼容模式

   用`<meta>`指定页面用什么版本的 IE 来渲染

7. CSS/JS 引入

    引入时不需要指明`type`，因为有默认值`text/css`和`text/javascript`
    HTML5 规范链接

    - [使用 link](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
    - [使用 style](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
    - [使用 script](http://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)

    ```html
    <!-- External CSS -->
    <link rel="stylesheet" href="code_guide.css" />
    
    <!-- In-document CSS -->
    <style>
      ...;
    </style>
    
    <!-- External JS -->
    <script src="code_guide.js"></script>
    
    <!-- In-document JS -->
    <script>
      ...
    </script>
    ```



8. 属性顺序

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
   
   <input class="form-control" type="text" />
   
   <img src="..." alt="..." />
   ```


9. boolean 属性

   boolean 属性指不需要声明取值的属性。但 XHTML 需要每个属性声明取值，HTML5 不需要。

   > boolean 属性存在 即表示取值为 true 不存在即表示取值为 false

10. JS 生成标签

    在 JS 文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。

11. 减少标签数量
  
    避免多余的父节点
   
    ```html
    <!-- Not well -->
    <span class="avatar">
      <img src="..." />
    </span>
    
    <!-- Better -->
    <img class="avatar" src="..." />
    ```


12. ✨ 实用高于完美
    
    尽量遵循 HTML 标准和语义，但是不应该以浪费实用性作为代价；

    任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

### 3 css/sass

1. 缩进

    使用 soft tab(2 个空格)

2. 分号

    每个属性声明末尾都要加分号

3. 空格

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

4. 空行

    以下几种情况需要空行：

    - 文件最后保留一个空行
    - '}'后最好跟一个空行，包括 scss 中嵌套的规则
    - 属性之间需要适当的空行，具体见[属性声明顺序](http://alloyteam.github.io/CodeGuide/   #css-declaration-order)

5. 换行

    以下几种情况不需要换行：

    - '{'前

    以下几种情况需要换行：

    - '{'后和'}'前
    - 每个属性独占一行
    - 多个规则的分隔符','后

6. 注释

    - 注释统一用'/\* \*/'（scss 中也不要用'//'），具体参照右边的写法；
    - 缩进与下一行代码保持一致；
    - 可位于一个代码行的末尾，与代码间隔一个空格。

7. 引号

    - 最外层统一使用双引号；
    - url 的内容要用引号；
    - 属性选择器中的属性值需要引号。

8. 命名

    - 类名使用小写字母，以中划线分隔
    - id 采用驼峰式命名
    - scss 中的变量、函数、混合、placeholder 采用驼峰式命名

9. 属性声明顺序

相关的属性声明按右边的顺序做分组处理，组之间需要有一个空行。

10. 颜色

    颜色 16 进制用小写字母；颜色 16 进制尽量用简写；

    ```css
    /* not good */
    .element {
      color: #abcdef;
      background-color: #001122;
    }

    /* good */
    .element {
      color: #abcdef;
      background-color: #012;
    }
    ```

11. 属性简写

    属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以**建议尽量分开声明**    会更加清晰；

    `margin` 和 `padding` 相反，需要使用简写；

    常见的属性简写包括：

    - `font`
    - `background`
    - `transition`
    - `animation`

12. 媒体查询

    尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。

13. SCSS 相关

    提交的代码中不要有 `@debug`；

    声明顺序：

    - `@extend`
    - 不包含 `@content` 的 `@include`
    - 包含 `@content` 的 `@include`
    - 自身属性
    - 嵌套规则

    `@import` 引入的文件不需要开头的'\_'和结尾的'.scss'；

    嵌套最多不能超过 5 层；

    `@extend` 中使用 placeholder 选择器；

    去掉不必要的父级引用符号'&'。

    ```css
    /* not good */
    @import "_dialog.scss";

    /* good */
    @import "dialog";

    /* not good */
    .fatal {
      @extend .error;
    }

    /* good */
    .fatal {
      @extend %error;
    }

    /* not good */
    .element {
      & > .dialog {
        ...;
      }
    }

    /* good */
    .element {
      > .dialog {
        ...;
      }
    }
    ```

14. 杂项

    - 不允许有空的规则；
    - 元素选择器用小写字母；
    - 去掉小数点前面的 0；
    - 去掉数字中不必要的小数点和末尾的 0；
    - 属性值'0'后面不要加单位；
    - 同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法；
    - 无前缀的标准属性应该写在有前缀的属性后面；
    - 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；
    - 不要在一个文件里出现两个相同的规则；
    - 用 `border: 0;` 代替 `border: none;`；
    - 选择器不要超过 4 层（在 scss 中如果超过 4 层应该考虑用嵌套的方式来写）；
    - 发布的代码中不要有 `@import`；
    - 尽量少用'\*'选择器。

### 4 JavaScript/TypeScript

1. 缩进

    使用 soft tab（2 个空格）

2. 单行长度

    不要超过 80，但如果编辑器开启 word wrap 可以不考虑单行长度。

3. 分号

    以下几种情况后需加分号：

    - 变量声明
    - 表达式
    - return
    - throw
    - break
    - continue
    - do-while

    ```js
    /* let declaration */
    let x = 1;

    /* expression statement */
    x++;

    /* do-while */
    do {
      x++;
    } while (x < 10);
    ```

4. 空格

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
    - 下列关键字后：`if`, `else`, `for`, `while`, `do`, `switch`, `case`, `try`, `catch`, `finally`,    `with`, `return`, `typeof`
    - 单行注释'//'后（若单行注释和代码同行，则'//'前也需要），多行注释'\*'后
    - 对象的属性值前
    - for 循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
    - 无论是函数声明还是函数表达式，'{'前一定要有空格
    - 函数的参数之间

5. 空行

    以下几种情况需要空行：

    - 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
    - 注释前（当注释在代码块的第一行时，则无需空行）
    - 代码块后（在函数调用、数组、对象中则无需空行）
    - 文件最后保留一个空行


6. 换行

    换行的地方，行末必须有','或者运算符；

    以下几种情况不需要换行：

    - 下列关键字后：`else`, `catch`, `finally`
    - 代码块'{'前

    以下几种情况需要换行：

    - 代码块'{'后和'}'前
    - 变量赋值后

7. 引号

    最外层统一使用**单引号**

    ```js
    // not good
    var x = "test";

    // good
    var y = "foo",
      z = '<div id="test"></div>';
    ```

8. 变量命名

    - 标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到 cgi 返回的数据）
    - 'ID'在变量名中全大写
    - 'URL'在变量名中全大写
    - 'Android'在变量名中大写第一个字母
    - 'iOS'在变量名中小写第一个，大写后两个字母
    - 常量全大写，用下划线连接
    - 构造函数，大写第一个字母
    - jquery 对象必须以'$'开头命名

9. 变量声明

    一个函数作用域中所有的变量声明尽量提到函数首部，根据情况采用 let 或 const 声明，尽量不采用 var。

10. 函数

    - 无论是函数声明还是函数表达式，'('前不要空格，但'{'前一定要有空格；
    - 
    - 函数调用括号前不需要空格；
    - 
    - 立即执行函数外必须包一层括号；
    - 
    - 不要给 inline function 命名；
    - 
    - 参数之间用', '分隔，注意逗号后有一个空格。


11. 数组/对象

    - 对象属性名不需要加引号；
    - 对象以缩进的形式书写，不要写在一行；
    - 数组、对象最后不要有逗号。

12. 括号

    下列关键字后必须有大括号（即使代码块的内容只有一行）

    `if`, `else`, `for`, `while`, `do`, `switch`, `try`, `catch`, `finally`, `with`。

13. null 使用场景

    适用场景：

    - 初始化一个将来可能被赋值为对象的变量
    - 与已经初始化的变量做比较
    - 作为一个参数为对象的函数的调用传参
    - 作为一个返回对象的函数的返回值

    不适用场景：

    - 不要用 null 来判断函数调用时有无传参
    - 不要与未初始化的变量做比较

13. undefined 判断

    永远不要直接使用 undefined 进行变量判断；

    使用 typeof 和字符串'undefined'对变量进行判断。

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

14. 杂项

    - 不要混用 tab 和 space；
    - 不要在一处使用多个 tab 或 space；
    - 换行符统一用'LF'；
    - 对上下文 this 的引用只能使用'\_this', 'that', 'self'其中一个来命名；
    - 行尾不要有空白字符；
    - switch 的 falling through 和 no default 的情况一定要有注释特别说明；
    - 不允许有空的代码块。


### 5 代码注释

注释虽然写起来很痛苦, 但对保证代码可读性至关重要。下面的规则描述了如何注释以及在哪儿注释. 当然也要记住: 注释固然很重要, 但最好的代码本身应该是自文档化. 有意义的类型名和变量名, 要远胜过要用注释解释的含糊不清的名字。

1. [JSDoc](https://jsdoc.app/)

    如果你在项目中使用 JavaScript 作为开发语言，那么我强烈建议你使用 JSDoc。它可以为 VSCode 生成智能提示，从而使开发者很容易了解整个类和其中的属性和方法，并且快速知道如何使用，从而提高开发效率，降低维护成本。而且，VSCode 对于 JSDoc 的支持是开箱即用的。

    如果你在项目中使用 TypeScript，依然应当使用 JSDoc 来作为文档注释。得益于 TypeScript 的类型系统，你通常只需要 `@param` 和 `@return` 标签即可。

    > 注意：JSDoc 使用 Markdown 格式来编写。

    以下内容均假设你已经在使用 JSDoc 进行注释。

2. 注释风格

    除了使用 JSDoc 以外，你可能还需要使用普通的注释来解释你的代码，此时使用 `//` 或是 `/* */` 都可以，保证风格统一即可。

3. 单行注释

    - 双斜线后，**必须跟一个空格**；
    - **缩进**与下一行代码保持一致；
    - 可位于一个代码行的末尾，与代码**间隔一个**空格。

4. 多行注释

    最少三行, '\*'后跟一个空格，具体参照下边的写法；

    建议在以下情况下使用：

    - 难于理解的代码段
    - 可能存在错误的代码段
    - 浏览器特殊的 HACK 代码
    - 业务逻辑强相关的代码

    ```js
    /*
    * one space after '*'
    */
    let x = 1;
    ```

5. 注释规则

    各类标签@param, @method 等请参考[usejsdoc](http://usejsdoc.org/)和[JSDoc Guide](http://yuri4ever.github.io/jsdoc/)；

    建议在以下情况下使用：

    - 所有常量
    - 所有函数
    - 所有类

    ```js
    /**
    * @func
    * @desc 一个带参数的函数
    * @param {string} a - 参数a
    * @param {number} b=1 - 参数b默认值为1
    * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx
    * @param {object} d - 参数d为一个对象
    * @param {string} d.e - 参数d的e属性
    * @param {string} d.f - 参数d的f属性
    * @param {object[]} g - 参数g为一个对象数组
    * @param {string} g.h - 参数g数组中一项的h属性
    * @param {string} g.i - 参数g数组中一项的i属性
    * @param {string} [j] - 参数j是一个可选参数
    */
    function foo(a, b, c, d, g, j) {
        ...
    }
    ```

6. 变量注释

    如果根据本规则，那么变量名本身足以很好说明变量用途。但是在某些特殊情况下，你仍然需要为变量添加注释。

    1. 类成员和对象属性应该用注释标注类型，说明含义以及用途。如果变量可以接受 NULL 或 -1 等警戒值, 须加以说明。

    2. 全局变量应该用注释标注类型，说明含义以及用途。

7. 函数注释

    注释位于声明之前, 对函数功能及用法进行描述。
    函数声明处的注释应当至少包括以下内容:

    1. 函数的描述
    2. 函数的输参数及其类型
    3. 函数的输出及其类型

    你也可以添加其他标签，如 `@deprecated` 表示不推荐使用。

    如果需要注释说明函数功能和实现要点，在函数内部使用普通注释即可。但是如果注释涉及到了某个变量，还是应当使用 JSDoc 来标注变量类型。

    如果某个类方法是对子类中同签名方法的重写，则必须要添加`@override` 标签，此时 JSDoc 会从子类方法中继承标签，无需重复注释类型。

8. 类注释

    每个类都应当附带一份注释，包括描述、参数、实现接口、可见性以及其他属性。类描述应当提供信息告诉其他人如何使用。

9. 枚举注释和类型定义

    所有的枚举和类型定义都应当使用对应的 JSDoc 标签进行注释(`@enum` 或 `@typedef`)。枚举类型中每一个独立的枚举项也应使用 JSDoc 进行注释。

10. 类型注解

    1. 非空 (non-null) 和可空 (nullable) 标识符

       类型系统定义了 `!` 和 `?` 运算符来表示非空和可空。原始类型 (`string`, `number`, `boolean`, `symbol`,     `undefined`, `null`) 和字面量 (`{function(...): ...}` 和 `{{foo: string...}}`) 默认是非空类型，在类型   前面加 `?` 可以使它们可空; 对于引用类型，应当显式使用 `?` 或 `!` 来表示它们是否可空。

    2. 模板参数

       对于模板类型，必须显式指定其参数类型。例如:

       ```javascript
        // bad
        const /** !Object */ users = {};
        const /** !Array */ books = [];
        const /** !Promise */ response = ...;

        // good
        const /** !Object<string, !User> */ users = {};
        const /** !Array<string> */ books = [];
        const /** !Promise<!Response> */ response = ...;

       ```

    3. 函数类型表达式 (function type expression)

       > 函数类型表达式是指类型注解中带有`function`关键字的类型注解

       当有函数定义时，使用 `@param` 和 `@return` 进行注解，不要使用函数类型表达式。在将匿名函数或已定义函数赋值给变量    时，才应该使用函数类型表达式。在使用函数类型表达式时，显式写出返回类型。

    4. 格式要求

       在类型注解中，应当在每个逗号或分号后面插入一个空格或换行。额外的空行可以增加可读性，同时避免超过编辑器列宽限制。

### 6 代码校验

  为了保证每个人的代码风格与本规范一致，应使用 [ESLint](http://eslint.cn/) + [Prettier](https://www.prettier.cn/) 来格式化代码。

  ESLint 关闭格式化功能，仅启用静态检查功能，代码格式化检查由 Prettier 负责。

## PART2 GIT 提交规范

### 1 项目负责人及分工

每个项目有一名负责人，项目由负责人在 github 上进行仓库初始化，并划分功能模块，每个项目成员在各自分支维护若干功能模块。
    
正常情况下，每位同学每完成一个功能点，及时commit。而每周push至少一次，以便版本管理及个人任务量查看。

### 2 分支合并

分支合并时，由成员发起合并请求(pull requests)，项目负责人审核后可合并至主分支。

### 3 Commit Message 规范

1. 提交格式:

    ```
    <type>(<scope>): <subject>
    <BLANK LINE>
    <body>
    <BLANK LINE>
    <Footer>
    ```


2. 参数说明

   - type
     

       `type` 用于说明 commit 类型，只能是以下类型之一。

       | 类型     | 描述                               |
       | :------- | ---------------------------------- |
       | feat     | 新增 feature                       |
       | fix      | 修复 bug                           |
       | docs     | 修改文档                           |
       | style    | 修改样式                           |
       | refactor | 重构代码                           |
       | perf     | 优化相关                           |
       | test     | 测试相关，包括单元测试、集成测试等 |
       | chore    | 改变构建流程，或改动依赖库、工具等 |
       | revert   | 回滚                               |

     - scope
       - `scope` 用于说明 commit 影响的范围。如果没有合适的范围，可以使用 `*`。
     
     - subject
       - `subject` 是 commit 目的的简短描述，其规则为:
       - 不超过 50 个字符
       - 以动词开头，使用第一人称现在时，比如 change，而不是 changed 或 changes
       - 第一个字母小写
       - 结尾不加句点

   - body (可选)
     - `body`是对本次 commit 的详细描述，可以分成多行。规则为：
       - 使用第一人称现在时
       - 应该说明代码变动的动机，以及与以前行为的对比。

   - footer(可选)

     footer里的主要放置**不兼容变更**和**Issue关闭**的信息

   

3. 自动格式化工具

   `commitizen`

   - 优点

     替代`git commit -m "<type(scope)>: <subject>"`命令，提供一个便捷的交互式面板。

     ![img](https://upload-images.jianshu.io/upload_images/1966717-1dbd6294bb208b46.gif?imageMogr2/auto-orient/strip|imageView2/2/w/791/format/webp)

   

   - 使用方式

     将修改项加入本地暂存区后(即git add *操作)，执行`git cz`或`npx cz`，即可进入交互式面板。
     
     在交互区输入相应信息后，即可自动生成格式化commit message。
     
   - 推荐全局安装

     ```
     npm install -g commitizen
     ```



### 4 Git Branch

| 分支        | 命名        | 说明                                                 |
| :---------- | :---------- | :--------------------------------------------------- |
| 主分支      | main        | 所有提供给用户使用的正式版本，都在这个主分支上发布。 |
| 开发分支    | dev         | 永远是功能最新最全的分支                             |
| 新特性分支  | feature/xxx | 新功能分支，某个功能点正在开发阶段。                 |
| BUG修复分支 | fix/xxx     | 修复线上代码的 bug。                                 |



### 5 Git Hooks

可以使用 [Git Hooks](https://git-scm.com/docs/githooks) 在代码提交前执行检察。最常见的用法是安装 [lint-staged](https://github.com/okonet/lint-staged#readme) 和 [Husky](https://github.com/typicode/husky#readme)，在`pre-commit`阶段执行检查，强制规范代码格式和 Commit Message。

## PART3 项目规范

### 1. 项目内容

推荐使用 [Visual Studio Code](https://code.visualstudio.com) 来编写项目代码。

新建项目时，在根目录下新建 `.vscode` 文件夹，并在其中写入配置文件。你的 `.vscode` 文件夹中至少应包含如下文件:

1. `settings.json` - 用于统一编辑器和插件设置
2. `launch.json` - 用于调试项目

除此以外，提供 `extension.json` 来统一项目开发者使用的插件。

### 2. 项目管理

## 参考

1. [JavaScript 变量命名](https://juejin.cn/post/6977245873797349413)
2. [Google JavaScript Style Guideline](https://google.github.io/styleguide/jsguide.html)
3. [Google TypeScript Style Guideline](https://google.github.io/styleguide/tsguide.html)
4. [AngularJS Git Commit Message Conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#)
5. [Code Guide by @AlloyTeam](http://alloyteam.github.io/CodeGuide/)
