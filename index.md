# UXD Code Guideline

2021年6月25日

## 一、代码规范

### 1. [命名原则](https://juejin.cn/post/6977245873797349413)

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

### 2. 命名规则

#### 项目命名

全部采用小写方式，以下划线分隔

#### 目录命名

参考项目命名规则；有复数时，采用复数命名法

### 3. HTML规范

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

### 4. 代码注释

注释虽然写起来很痛苦, 但对保证代码可读性至关重要。下面的规则描述了如何注释以及在哪儿注释. 当然也要记住: 注释固然很重要, 但最好的代码本身应该是自文档化. 有意义的类型名和变量名, 要远胜过要用注释解释的含糊不清的名字。

#### [JSDoc](https://jsdoc.app/)
如果你在项目中使用 JavaScript 作为开发语言，那么我强烈建议你使用 JSDoc。它可以为 VSCode 生成智能提示，从而使开发者很容易了解整个类和其中的属性和方法，并且快速知道如何使用，从而提高开发效率，降低维护成本。而且，VSCode 对于 JSDoc 的支持是开箱即用的。

如果你在项目中使用 TypeScript，依然应当使用 JSDoc 来作为文档注释。得益于 TypeScript 的类型系统，你通常只需要 `@param` 和 `@return` 标签即可。

> 注意：JSDoc 使用 Markdown 格式来编写。

以下内容均假设你已经在使用 JSDoc 进行注释。

#### 注释风格

除了使用 JSDoc 以外，你可能还需要使用普通的注释来解释你的代码，此时使用 `//` 或是 `/* */` 都可以，保证风格统一即可。

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

    当有函数定义时，使用 `@param` 和 `@return` 进行注解，不要使用函数类型表达式。在将匿名函数或已定义函数赋值给变量时，才应该使用函数类型表达式。在使用函数类型表达式时，显式写出返回类型。

4. 格式要求
   
    在类型注解中，应当在每个逗号或分号后面插入一个空格或换行。额外的空行可以增加可读性，同时避免超过编辑器列宽限制。
### 5. 代码校验

为了保证每个人的代码风格与本规范一致，应使用 [ESLint](http://eslint.cn/) + [Prettier](https://www.prettier.cn/) 来格式化代码。

ESLint 关闭格式化功能，仅启用静态检查功能，代码格式化检查由 Prettier 负责。

## 二、GIT提交规范

### 1. 项目负责人及分工

每个项目有一名负责人，项目由负责人在github上进行仓库初始化，并划分功能模块，每个项目成员在各自分支维护若干功能模块。

### 2. 分支合并

分支合并时，由成员发起合并请求，项目负责人审核后可合并至主分支。

### 3. 每日push

正常情况下，每位同学至少push一次当天工作内容，以便版本管理及个人任务量查看。

各commit标注清楚本次提交内容，便于其他成员查看。

### 4. Commit Message规范

Commit Message 参考 Angular 规范，并做了一定的简化。信息的提交格式为:
```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
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

### 5. Git Hooks

可以使用 [Git Hooks](https://git-scm.com/docs/githooks) 在代码提交前执行检察。最常见的用法是安装 [lint-staged](https://github.com/okonet/lint-staged#readme) 和 [Husky](https://github.com/typicode/husky#readme)，在`pre-commit`阶段执行检查，强制规范代码格式和 Commit Message。

## 三、项目规范

### 1. 项目内容

我们推荐使用 [Visual Studio Code](https://code.visualstudio.com) 来编写项目代码。在你新建项目时，在根目录下新建 `.vscode` 文件夹，并在其中写入配置文件。你的 `.vscode` 文件夹中至少应包含如下文件:
1. `settings.json` - 用于统一编辑器和插件设置
2. `launch.json` - 用于调试项目

除此以外，你还可以提供 `extension.json` 来统一项目开发者使用的插件。

### 2. 项目管理

#### 项目分工及任务流

基于github project看板实现



## 四、技术分享

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



## 五、成员技术栈及优势方向

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