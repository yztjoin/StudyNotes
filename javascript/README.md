浏览器具体运行情况

浏览器访问（计算机网络）

# javaScripte历史

起始的目的是为了代替Perl等服务器语言处理输入验证；

因为极慢的网上容忍不了在输入完表单后几分钟响应的错误返回，所以在浏览器上加入javascript作为表单验证

## DOM（Document Object Model：文档对象模型）

DOM通过创建表示文档的树，开发者可以随心所以的控制网页的内容和结构。使用Dom API可以轻松的删除、添加、替换、修改节点

开发者可以做到不刷新页面而修改页面外观的内容，由于网景和微软采用不同思路开发DHTML（Dynamic HTML）动态HTML

**DOM1**：作为映射文档结构

**DOM2**

- DOM视图：
- DOM事件：描述事件及事件处理接口
- DOM样式：描述处理元素CSS样式的接口
  DOM遍历和范围：描述遍历和操作DOM树的接口

**DOM3**

- 验证文档的方法（DOM Validation）。
- 支持了所有 XML 1.0 的特性

其他**DOM**

- 可伸缩矢量图（SVG，Scalable Vector Graphics）
- 数学标记语言（MathML，Mathematical Markup Language）
- 同步多媒体集成语言（SMIL，Synchronized Multimedia Integration Language）

## BOM：浏览器对象模型

用于支持访问和操作浏览器的窗口。

没有相关标准的JavaScript实现，HTML5改变了这个局面

**扩展能力：**

- 弹出新浏览器窗口的能力；
- 移动、缩放和关闭浏览器窗口的能力；
- navigator 对象，提供关于浏览器的详尽信息；
- location 对象，提供浏览器加载页面的详尽信息；
- screen 对象，提供关于用户屏幕分辨率的详尽信息；
- performance 对象，提供浏览器内存占用、导航行为和时间统计的详尽信息；
- 对 cookie 的支持；
- 其他自定义对象，如 XMLHttpRequest 和 IE 的 ActiveXObject。

## 小结

**三个主要组曾部分**

- ECMAScript：由 ECMA-262 定义并提供核心功能。
- 文档对象模型（DOM）：提供与网页内容交互的方法和接口。
- 浏览器对象模型（BOM）：提供与浏览器交互的方法和接口。

有点像网络结构？网络边缘、网络核心、接入网

# HTML内的JavaScript

## script标签元素

script标签元素有八个属性

- async：可选。异步加载文件，只针对外部文件有效
- charset：可选。使用src属性指定的代码字符集，很少使用，大多数浏览器忽略他的值
- crossorigin：可选。配置相关请求的CORS（跨源资源共享）设置。默认不使用CORS。crossorigin= "anonymous"配置文件请求不必设置凭据标志。crossorigin="use-credentials"设置凭据 标志，意味着出站请求会包含凭据。引申：[crossorigin详解](https://blog.csdn.net/qq_40028324/article/details/107076751)
- defer：可选。延迟加载，表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。
- integrity：可选。允许比对接收到的资源和指定的加密签名以验证子资源完整性（SRI， Subresource Integrity）。如果接收到的资源的签名与这个属性指定的签名不匹配，则页面会报错， 脚本不会执行。这个属性可以用于确保内容分发网络（CDN，Content Delivery Network）不会提 供恶意内容
- language：废弃。最初用于表示代码中的脚本语言言（如"JavaScript"、"JavaScript 1.2" 或"VBScript"）。大多数浏览器都会忽略这个属性，不应该再使用它。
- src：可选。表示包含要执行的代码的外部文件。
- type：可选。代替language表示代码块中脚本语言的内容类型（也称 MIME 类型）。按照惯 例，这个值始终都是"text/javascript"，尽管"text/javascript"和"text/ecmascript" 都已经废弃了。JavaScript 文件的 MIME 类型通常是"application/x-javascript"，不过给 type 属性这个值有可能导致脚本被忽略。在非 IE 的浏览器中有效的其他值还有 "application/javascript"和"application/ecmascript"。如果这个值是 module，则代 码会被当成 ES6 模块，而且只有这时候代码中才能出现 import 和 export 关键字。

使用了 src 属性的标签中再包含其他 JavaScript 代码。如果两者都提供的话，则浏览器只会下载并执行脚本文件，从而忽略行内代码。

```Html
// 过去，所有<script>元素都被放在页面的<head>标签内，如下面的例子所示：
<html>
 <head>
 <title>Example HTML Page</title>
 <script src="example1.js"></script>
 <script src="example2.js"></script>
 </head>
 <body>
 <!-- 这里是页面内容 -->
 </body>
</html>
```

这种做法的主要目的是把外部的 CSS 和 JavaScript 文件都集中放到一起。不过，把所有 JavaScript 文件都放在里，也就意味着必须把所有 JavaScript 代码都下载、解析和解释完成后，才能开始渲 染页面（页面在浏览器解析到的起始标签时开始渲染）。对于需要很多 JavaScript 的页面，这会 导致页面渲染的明显延迟，在此期间浏览器窗口完全空白。为解决这个问题，现代 Web 应用程序通常 将所有 JavaScript 引用放在元素中的页面内容后面

## 文档模式

IE5.5发明了文档模式概念，即可以使用doctype切换文档模式。

最初的文档模式有两种：**混杂模式（quirks mode）、标准模式（standards mode）**、**准标准模式（almost standards mode）**

![image-20220406154542709](assets/image-20220406154542709.png)

# 语言基础

## 语言标准和惯例

- javascript区分大小写
- 标识符（变量、函数、属性或函数参数的名称）：第一个字符必须是一个字母、下户线或$，剩下的其他字符可以是字母、下划线、美元符号或者数字
- 惯例：标识符使用驼峰大小写，即第一个单次的首字母小写，后面的每个单次的首字母大写
- 注释：// 单行注释 、/* 多行注释 */

## 严格模式

严格模式是一种不同的 JavaScript 解析和执 行模型，ECMAScript 3 的一些不规范写法在这种模式下会被处理，对于不安全的活动将抛出错误。

>要对 整个脚本启用严格模式，在脚本开头加上这一行： "use strict"; 

选择这种语法形式的目的是不破坏 ECMAScript 3 语法。 也可以单独指定一个函数在严格模式下执行，只要把这个预处理指令放到函数体开头即可

```javascript
 function doSomething() { 
 	"use strict"; // 函数体 
 } 
```

## 关键字保留

>**ECMA-262 第 6 版规定的所 有关键字如下**

| break    | do       | in         | typeof |
| -------- | -------- | ---------- | ------ |
| case     | else     | instanceof | var    |
| catch    | export   | new        | void   |
| class    | extends  | return     | while  |
| const    | finally  | super      | with   |
| continue | for      | switch     | yield  |
| debugger | function | this       | import |
| default  | if       | throw      | try    |
| delete   |          |            |        |

>**未来保留字**

始终保留：enum

严格模式下保留：implements、package、public、interface、protected、static、let、private 

模块代码中保留：await

## var关键字

**作用域**

- 函数作用域：在函数内声明的变量在函数外无法访问
- 块级作用域：只要是{}内声明的变量，在{}外无法访问

**1、var声明作用域**

函数作用域：在函数内部定义会在函数退出时被销毁

```javascript
function test() {
 var message = "hi"; // 局部变量
}
test();
console.log(message); // 出错！
```

**2、var生命提升**

声明的变量会自动提升到作用域的顶部，不会报错

```javascript
function foo() {
 console.log(age);
 var age = 26;
}
foo(); // undefined 
// 之所以不会报错，是因为 ECMAScript 运行时把它看成等价于如下代码：
function foo() {
 var age;
 console.log(age);
 age = 26;
}
foo(); // undefined
```

此外，反复生命多次var变量也没有问题：

```javascript
function foo() {
 var age = 16;
 var age = 26;
 var age = 36;
 console.log(age);
}
foo(); // 36 
```

## let 声明

**特点**：块级作用域、没有变量提升、没有全局声明

**1、块级作用域**

块作用域 是函数作用域的子集，因此适用于 var 的作用域限制同样也适用于 let。

let在if、for等大括号内的变量声明后不会在大括号外访问到----块级作用域

**2、暂时性死区**

let和var的不同是，let没有变量提升

```javascript
// name 会被提升
console.log(name); // undefined
var name = 'Matt';
// age 不会被提升
console.log(age); // ReferenceError：age 没有定义
let age = 26;
```

在解析代码时，JavaScript 引擎也会注意出现在块后面的 let 声明，只不过在此之前不能以任何方 式来引用未声明的变量。在 let 声明之前的执行瞬间被称为“暂时性死区”（temporal dead zone），在此 阶段引用任何后面才声明的变量都会抛出 ReferenceError。

**3、全局声明**

let关键字不同，var在全局作用域中声明的变量会挂载在window对象上，但是let不会成为window对象的属性

```javascript
var name = 'Matt';
console.log(window.name); // 'Matt'
let age = 26;
console.log(window.age); // undefined 
```

## const声明

const的行为与let基本相同，位移一个区别是它声明变量时必须初始化变量，而且尝试修改const声明的变量会导致运行错误。

const声明对象，改变对象值不会违反const的限制

## 数据类型

ECMAScript有种简单数据类型（也称为原始类型）：Undefined、Null、Boolean、Number、 String 和 Symbol。Symbol（符号）是 ECMAScript 6 新增的。还有一种复杂数据类型叫 Object（对 象）。Object 是一种无序名值对的集合。

因为 ECMAScript 的类型系统是松散的，所以需要一种手段来确定任意变量的数据类型。**typeof** 操作符就是为此而生的。对一个值使用 typeof 操作符会返回下列字符串之一： 

- "undefined"表示值未定义：Undefined 类型只有一个值，就是特殊值 undefined。当使用 var 或 let 声明了变量但没有初始 化时，就相当于给变量赋予了 undefined 值，undefined值的变量和未定义的变量是有区别的。

  ```javascript
  let message; // 这个变量被声明了，只是值为 undefined
  // 确保没有声明过这个变量
  // let age
  console.log(message); // undefined
  console.log(age); // 报错
  ```

- "boolean"表示值为布尔值； 

- "string"表示值为字符串； 

- "number"表示值为数值；

- "object"表示值为对象（而不是函数）或 null； 

- "function"表示值为函数；

- "symbol"表示值为符号。

>严格来讲，函数在 ECMAScript 中被认为是对象，并不代表一种数据类型。可是， 函数也有自己特殊的属性。为此，就有必要通过 typeof 操作符来区分函数和其他对象。

undefined 值是由 null 值派生而来的，因此 ECMA-262 将它们定义为表面上相等，如下面的例 子所示：

```javascript
 console.log(null == undefined); // true
```

即使 null 和 undefined 有关系，它们的用途也是完全不一样的。永远不必显式地将变量值设置为 undefined。但 null 不是这样的。任何时候，只要变量要保存对象，而当时又没有那个 对象可保存，就要用 null 来填充该变量。这样就可以保持 null 是空对象指针的语义，并进一步将其 与 undefined 区分开来。

也就是说初始化对象并且没有特定的值的时候设置为null

### **Boolean类型**

其他类型对布尔类型的转换

| 数据类型  | 转换为 true 的值       | 转换为 false 的值 |
| --------- | ---------------------- | ----------------- |
| Boolean   | true                   | false             |
| String    | 非空字符串             | ""（空字符串）    |
| Number    | 非零数值（包括无穷值） | 0、NaN            |
| Object    | 任意对象               | null              |
| Undefined | N/A（不存在）          | undefined         |

### **Number类型**

0.000 000 000 000 000 03。这个数值用科学记数法 可以表示为 3e-17。

```javascript
let floatNum = 3.125e7; // 等于 31250000
```

例外：浮点值的精确度最高可达 17 位小数，但在算术计算中远不如整数精确。例如，0.1 加 0.2 得到的不 是 0.3，而是 0.300 000 000 000 000 04。由于这种微小的舍入错误，导致很难测试特定的浮点值。

>注意 之所以存在这种错误，是因为使用了 IEEE 754 数值，这种错误并非 ECMAScript 所独有。其他使用相同格式的语言也有这个问题。

**1、值的范围**

ECMAScript，由于内存问题，ECMAScript并不支持表示这个世界上所有的数值。

- Number.Min_VALUE：最小数值，大多数浏览器中是5e-324
- Number.MAX_VALUE：最大数值，大所属浏览器中是1.797 693 134 862 315 7e+308

如果计算出来的值超过了这个返回会自动转换为Infinity表示，该值将不能再进一步用于任何计算

要确定一个值是不是有限大（即介于 JavaScript 能表示的 最小值和最大值之间），可以使用 isFinite()函数，如下所示： 

```javascript
let result = Number.MAX_VALUE + Number.MAX_VALUE; 
console.log(isFinite(result)); // false 
```

>使用 Number.NEGATIVE_INFINITY 和 Number.POSITIVE_INFINITY 也可以获 取正、负 Infinity。没错，这两个属性包含的值分别就是-Infinity 和 Infinity。

**2、NaN**

有一个特殊的数值叫 NaN，意思是“不是数值”（Not a Number），用于表示本来要返回数值的操作 失败了（而不是抛出错误）。比如，用 0 除任意数值在其他语言中通常都会导致错误，从而中止代码执 行。但在 ECMAScript 中，0、+0 或0 相除会返回 NaN：

```javascript
console.log(0/0); // NaN
console.log(-0/+0); // NaN
// 如果分子是非 0 值，分母是有符号 0 或无符号 0，则会返回 Infinity 或-Infinity：
console.log(5/0); // Infinity
console.log(5/-0); // -Infinity
```

- NaN，任何涉及到NaN的操始终返回NaN

- NaN不同于包括NaN在内的任何值。

  ```javascript
  console.log(NaN == NaN); // false 
  // 为此提供了isNaN()函数，传一个参数，为任何不能转换为数值的值返回false
  console.log(isNaN(NaN)); // true
  console.log(isNaN(10)); // false，10 是数值
  console.log(isNaN("10")); // false，可以转换为数值 10
  console.log(isNaN("blue")); // true，不可以转换为数值
  console.log(isNaN(true)); // false，可以转换为数值 1
  ```

>虽然不常见，但 isNaN()可以用于测试对象。此时，首先会调用对象的 valueOf() 方法，然后再确定返回的值是否可以转换为数值。如果不能，再调用 toString()方法， 并测试其返回值。这通常是 ECMAScript 内置函数和操作符的工作方式

**3、数值转换**

>Number()、parseInt()、parseFloat() 三个转型函数

Number()转换规则

- 布尔值，true 转换为 1，false 转换为 0。
- 数值，直接返回
- null，返回 0
- undefined，返回 NaN
- 字符串规则，几种情况，有数字、无数字、数字字母混合、空字符
  1. 如果字符串包含数值字符，包括数值字符前面带加、减号的情况，则转换为一个十进制数值。 因此，Number("1")返回 1，Number("123")返回 123，Number("011")返回 11（忽略前面 的零）。
  2. 如果字符串包含有效的浮点值格式如"1.1"，则会转换为相应的浮点值（同样，忽略前面的零）。
  3. 如果字符串包含有效的十六进制格式如"0xf"，则会转换为与该十六进制值对应的十进制整 数值。
  4. 如果是空字符串（不包含字符），则返回 0。
  5. 如果字符串包含除上述情况之外的其他字符，则返回 NaN。
- 对象，调用 valueOf()方法，并按照上述规则转换返回的值。如果转换结果是 NaN，则调用 toString()方法，再按照转换字符串的规则转换。

parseInt()：会从第一个不是空字符的位置开始判断，如果第一个不是数字直接返回NaN，如果第一个字符 是数值字符、加号或减号，则继续依次检测每个字符，直到字符串末尾，或碰到非数值字符。

```javascript
let num1 = parseInt("1234blue"); // 1234
let num2 = parseInt(""); // NaN
let num3 = parseInt("0xA"); // 10，解释为十六进制整数
let num4 = parseInt(22.5); // 22
let num5 = parseInt("70"); // 70，解释为十进制值
let num6 = parseInt("0xf"); // 15，解释为十六进制整数
// 不同的数值格式很容易混淆，因此 parseInt()也接收第二个参数，用于指定底数（进制数）。
let num1 = parseInt("AF", 16); // 175
let num2 = parseInt("AF"); // NaN 
```

### **String类型**

**1、字符字面量**

| 字 面 量 | 含 义                                                        |
| -------- | ------------------------------------------------------------ |
| \n       | 换行                                                         |
| \t       | 制表                                                         |
| \b       | 退格                                                         |
| \r       | 回车                                                         |
| \f       | 换页                                                         |
| \\\      | 反斜杠（\）                                                  |
| \\'      | 单引号（'），在字符串以单引号标示时使用，例如'He said, \'hey.\'' |
| \\"      | 双引号（"），在字符串以双引号标示时使用，例如"He said, \"hey.\"" |
| \\`      | 反引号（`），在字符串以反引号标示时使用，例如`He said, \`hey.\`` |
| \xnn     | 以十六进制编码 nn 表示的字符（其中 n 是十六进制数字 0~F），例如\x41 等于"A" |
| \unnnn   | 以十六进制编码 nnnn 表示的 Unicode 字符（其中 n 是十六进制数字 0~F），例如\u03a3 等于希腊字 符"Σ" |

**2、转换字符串**

有两种方式把一个值转换为字符串。首先是使用几乎所有值都有的 toString()方法。这个方法唯 一的用途就是返回当前值的字符串等价物

所有值都有**toString()方法**，这个方法位移的用途就是返回当前值的字符串等价物。

```javascript
let age = 11;
let ageAsString = age.toString(); // 字符串"11"
let found = true;
let foundAsString = found.toString(); // 字符串"true" 
```

**通过传入参数**，可以得到数值的**二进制、八进制、十六进制**，或者其他任何有效基 数的字符串表示

```javascript
let num = 10;
console.log(num.toString()); // "10"
console.log(num.toString(2)); // "1010"
console.log(num.toString(8)); // "12"
console.log(num.toString(10)); // "10"
console.log(num.toString(16)); // "a"
```

3、模板字符串、

------------------------------49





