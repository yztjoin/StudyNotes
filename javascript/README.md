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

**3、模板字符串**

```javascript
let a = 6;
let b = 9;
function simpleTag(strings, aValExpression, bValExpression, sumExpression) {
 console.log(strings);
 console.log(aValExpression);
 console.log(bValExpression);
 console.log(sumExpression);
 return 'foobar';
}
let untaggedResult = `${ a } + ${ b } = ${ a + b }`;
let taggedResult = simpleTag`${ a } + ${ b } = ${ a + b }`;
// ["", " + ", " = ", ""]
// 6
// 9
// 15
console.log(untaggedResult); // "6 + 9 = 15"
console.log(taggedResult); // "foobar" 
```

### Object类型

ECMAScript中的对象其实就是一组数据和功能的集合。

开发者可以通过创建 Object 类型的实例来创建自己的对象，然后再给对象添加属性和方法： 

```javascript
let o = new Object();
```

Object实例都有入戏属性和方法：

- constructor：用于创建当前对象的函数，在前面的例子中，这个属性的值就是 Object() 函数。

- hasOwnProperty( propertyName )：用于判断当前对象实例（不是原型）上是否存在给定的属性。

- isPrototypeOf(object)：用于判断当前对象是否为另一个对象的原型。

- propertyIsEnumerable( propertyName )：用于判断给定的属性是否可以使用for-in枚举。

- toLocaleString()：返回对象的字符串表示，该字符串反应对象坐在的本地化执行环境。

  ```javascript
  let obj = {};
  obj.toLocaleString(); // '[object Object]'
  ```

- toString()：返回对象的字符串表示

  ```javascript
  let obj = {}
  obj.toString() // '[object Object]'
  ```

- valueOf()：返回对象对应的字符串、数值或者布尔值表示

## 操作符

### **一元操作符**

>只操作一个值的操作符叫一元操作符（unary operator）。

**1、递增/递减操作符**：++age、--age、age++、age--

符号在前，先自加（自减）再计算，符号在后先计算再自加（自减）

2、一元家和减

**一元加**：+num

如果将一元加应用到非数值，则会执行与使用 Number()转型函数一样的类型转换：布尔值 false 和 true 转换为 0 和 1，字符串根据特殊规则进行解析，对象会调用它们的 valueOf()和/或 toString() 方法以得到可以转换的值。

```javascript
let s1 = "01";
let s2 = "1.1"; 
let s3 = "z";
let b = false;
let f = 1.1;
let o = {
 valueOf() {
 return -1;
 }
};
s1 = +s1; // 值变成数值 1
s2 = +s2; // 值变成数值 1.1
s3 = +s3; // 值变成 NaN
b = +b; // 值变成数值 0
f = +f; // 不变，还是 1.1
o = +o; // 值变成数值-1 
```

**一元加减**：-num

一元减由一个减号（-）表示，放在变量前头，主要用于把数值变成负值

对数值使用一元减会将其变成相应的负值（如上面的例子所示）。在应用到非数值时，一元减会遵 循与一元加同样的规则，先对它们进行转换，然后再取负值

### 位操作符

位运算用于数值的底层操作

ECMAScript中所有数值都是以IEEE 754 64位格式存储，但是位操作不直接应用到64位表示，二十先把值转换位32位正数，再进行操作，之后再把结果转换为64位

**有符号正式使用32位的前31位表示整数**，最后一位表示符号：0（正数）、1（负数），空的用0填充

**负数**是以补码的二进制编码储存

补码：正数的补码是其二进制表示，与原码相同、**负数的补码是将其原码除符号位外的所有位取反**

```javascript
// 基于上述步骤确定18 的二进制表示，首先从 18 的二进制表示开始
0000 0000 0000 0000 0000 0000 0001 0010
然后，计算一补数，即反转每一位的二进制值：
1111 1111 1111 1111 1111 1111 1110 1101
最后，给一补数加 1：
1111 1111 1111 1111 1111 1111 1110 1101
 1
----------------------------------------------
1111 1111 1111 1111 1111 1111 1110 1110
```

**2、按位非**

按位非操作符用波浪符（~）表示，它的作用是返回数值的一补数

```javascript
let num1 = 25; // 二进制 00000000000000000000000000011001
let num2 = ~num1; // 二进制 11111111111111111111111111100110
console.log(num2); // -26
```

**3、按位与**

按位与操作符用和号（&）表示，有两个操作数。本质上，按位与就是将两个数的每一个位对齐， 然后基于真值表中的规则，对每一位执行相应的与操作。

按位与操作在两个位都是 1 时返回 1，在任何一位是 0 时返回 0。

```javascript
let result = 25 & 3;
console.log(result); // 1 
// 25 = 0000 0000 0000 0000 0000 0000 0001 1001
// 3 =  0000 0000 0000 0000 0000 0000 0000 0011
---------------------------------------------
// AND= 0000 0000 0000 0000 0000 0000 0000 0001
```

**4、按位或**

按位或操作符用管道符（|）表示，同样有两个操作数

按位或操作在至少一位是 1 时返回 1，两位都是 0 时返回 0

仍然用按位与的示例，如果对 25 和 3 执行按位或，代码如下所示：

```javascript
let result = 25 | 3;
console.log(result); // 27
// 可见 25 和 3 的按位或操作的结果是 27：
//25 = 0000 0000 0000 0000 0000 0000 0001 1001
// 3 = 0000 0000 0000 0000 0000 0000 0000 0011
---------------------------------------------
// OR= 0000 0000 0000 0000 0000 0000 0001 1011
```

**5、左移**

左移操作符用两个小于号（<<）表示，会按照指定的位数将数值的所有位向左移动

比如，**如果数 值 2（二进制 10）向左移 5 位，就会得到 64**（二进制 1000000），如下所示

```javascript
let oldValue = 2; // 等于二进制 10
let newValue = oldValue << 5; // 等于二进制 1000000，即十进制 64
```

![image-20220409161113873](assets/image-20220409161113873.png)

>**注意：**左移会保留它所操作数值的符号。比如，如果-2 左移 5 位，将得到-64，而不是正 64

**6、有符号右移**

有符号右移由两个大于号（>>）表示，会将数值的所有 32 位都向右移，同时保留符号（正或负）。 有符号右移实际上是左移的逆运算

比如，如果将 64 右移 5 位，那就是 2

```javascript
let oldValue = 64; // 等于二进制 1000000
let newValue = oldValue >> 5; // 等于二进制 10，即十进制 2
```

**7、无符号右移**

无符号右移用 3 个大于号表示（>>>），会将数值的所有 32 位都向右移。对于正数，无符号右移与 有符号右移结果相同。仍然以前面有符号右移的例子为例，64 向右移动 5 位，会变成 2

```javascript
let oldValue = 64; // 等于二进制 1000000
let newValue = oldValue >>> 5; // 等于二进制 10，即十进制 2 
```

负数的存储是按照补码存储，因此负数右移之后结果会变得非常大

```javascript
let oldValue = -64; // 等于二进制 11111111111111111111111111000000
let newValue = oldValue >>> 5; // 等于十进制 134217726 
```

### 布尔操作符

!（取反）、&&（与）、||（或）

### 指数操作符

ECMAScript 7 新增了指数操作符，**Math.pow()**现在有了自己的操作符**，结果是一样的

```javascript
console.log(Math.pow(3, 2); // 9
console.log(3 ** 2); // 9
console.log(Math.pow(16, 0.5); // 4
console.log(16** 0.5); // 4
```

指数操作符也有自己的指数赋值操作符**=，该操作符执行指数运算和结果的赋值操作

```javascript
let squared = 3;
squared **= 2;
console.log(squared); // 9 
let sqrt = 16;
sqrt **= 0.5;
console.log(sqrt); // 4
```

### 减法操作符

减法操作符也有一组规则用于处理 ECMAScript 中不同类型之间的转换

- 如果两个操作数都是数值，则执行数学减法运算并返回结果。
- 如果有任一操作数是 NaN，则返回 NaN。
- 如果是 Infinity 减 Infinity，则返回 NaN。
- 如果是-Infinity 减-Infinity，则返回 NaN。
- 如果是 Infinity 减-Infinity，则返回 Infinity。
- 如果是-Infinity 减 Infinity，则返回-Infinity。
- 如果是+0 减+0，则返回+0。
- 如果是+0 减-0，则返回-0。
- 如果是-0 减-0，则返回+0。
- 如果有任一操作数是字符串、布尔值、null 或 undefined，则先在后台使用 Number()将其转 换为数值，然后再根据前面的规则执行数学运算。如果转换结果是 NaN，则减法计算的结果是 NaN。
- 如果有任一操作数是对象，则调用其 valueOf()方法取得表示它的数值。如果该值是 NaN，则 减法计算的结果是 NaN。如果对象没有 valueOf()方法，则调用其 toString()方法，然后再 将得到的字符串转换为数值。

```javascript
let result1 = 5 - true; // true 被转换为 1，所以结果是 4
let result2 = NaN - 1; // NaN
let result3 = 5 - 3; // 2
let result4 = 5 - ""; // ""被转换为 0，所以结果是 5
let result5 = 5 - "2"; // "2"被转换为 2，所以结果是 3
let result6 = 5 - null; // null 被转换为 0，所以结果是 5
```

### 关系操作符

关系操作符执行比较两个值的操作，包括**小于**（<）、**大于**（>）、**小于等于**（<=）和**大于等于**（>=）， 

- 如果操作数都是数值，则执行数值比较。
- 如果操作数都是字符串，则逐个比较字符串中对应字符的编码。
- 如果有任一操作数是数值，则将另一个操作数转换为数值，执行数值比较
- 如果有任一操作数是对象，则调用其 valueOf()方法，取得结果后再根据前面的规则执行比较。 如果没有 valueOf()操作符，则调用 toString()方法，取得结果后再根据前面的规则执行比较。
- 如果有任一操作数是布尔值，则将其转换为数值再执行比较。

**两个字符串的比较并不是按照字母顺序比较，而是使用编码数值**

```javascript
let result = "Brick" < "alphabet"; // true 
// 在这里，字符串"Brick"被认为小于字符串"alphabet"，因为字母 B 的编码是 66，字母 a 的编码是 97
```

**两个字符串数字比较时并不会有理想的结果，因为两个字符串比较也是使用编码比较**

```javascript
// 字符"2"的编码是 50，而字符"3"的编码是 51
let result = "23" < "3"; // true
```

**任何涉及到NaN都会返回false**

```javascript
let result1 = NaN < 3; // false
let result2 = NaN >= 3; // false 
```

### 相等操作符

等于操作符用两个等于号（==）表示，如果操作数相等，则会返回 true。不等于 操作符用叹号和等于号（!=）表示，如果两个操作数不相等，则会返回 true。

- 如果任一操作数是布尔值，则将其转换为数值再比较是否相等。false 转换为 0，true 转换 为 1。
- 如果一个操作数是字符串，另一个操作数是数值，则尝试将字符串转换为数值，再比较是否 相等。
- 如果一个操作数是对象，另一个操作数不是，则调用对象的 valueOf()方法取得其原始值，再 根据前面的规则进行比较。
- null 和 undefined 相等。
- null 和 undefined 不能转换为其他类型的值再进行比较。
- 如果有任一操作数是 NaN，则相等操作符返回 false，不相等操作符返回 true。记住：即使两 个操作数都是 NaN，相等操作符也返回 false，因为按照规则，NaN 不等于 NaN。
- 如果两个操作数都是对象，则比较它们是不是同一个对象。如果两个操作数都指向同一个对象， 则相等操作符返回 true。否则，两者不相等。

```javascript
null == undefined  // true
"NaN" == NaN //false
5 == NaN //false
NaN == NaN //false
NaN != NaN //true
false == 0 //true
true == 1 //true
true == 2 //false
undefined == 0 //false
null == 0 //false
"5" == 5 //true
```

**全等和不全等**

全等和不全等操作符与相等和不相等操作符类似，只不过它们在比较相等时不转换操作数。全等操 作符由 3 个等于号（===）表示，只有两个操作数在不转换的前提下相等才返回 true

```javascript
let result1 = ("55" == 55); // true，转换后相等
let result2 = ("55" === 55); // false，不相等，因为数据类型不同
```

### 赋值操作符

复合赋值使用乘性、加性或位操作符后跟等于号（=）表示。这些赋值操作符是类似如下常见赋值 操作的简写形式：

```javascript
let num = 10;
num = num + 10; 
// 以上代码的第二行可以通过复合赋值来完成
```

## 小结

因为只提取一些比较缺漏的知识点，所以没有都做笔记

- ECMAScript 中的基本数据类型包括：undefined、null、number、String、Booolean、Symbol
- 与其他语言不同，ECMAScript 不区分整数和浮点值，只有 Number 一种数值数据类型。
- Object 是一种复杂数据类型，它是这门语言中所有对象的基类。
- ECMAScript 提供了 C 语言和类 C 语言中常见的很多基本操作符，包括数学操作符、布尔操作符、 关系操作符、相等操作符和赋值操作符等。
- 这门语言中的流控制语句大多是从其他语言中借鉴而来的，比如 if 语句、for 语句和 switch 语句等

ECMAScript 中的函数与其他语言中的函数不一样。

- 不需要指定函数的返回值，因为任何函数可以在任何时候返回任何值。
- 不指定返回值的函数实际上会返回特殊值 undefined。

# 变量、作用域和内存

## 原始值和引用值

ECMAScript变量

- 引用值（primitive value）：最简单的数据
- 引用值（reference value）：是由多个值构成的对象

在把一个值赋给变量时，javaScript引擎必须确定这个值是原始值还是引用值。

**原始值**：undefined、null、boolean、string、number、symbol，原始值的变量是按值访问的，因为我们操作的就是存储在变量中的实际值。

引用值是保存在内存中对象。javascript不允许直接访问内存位置，因此不能直接操作对象所在的内存空间。因此实际上操作的是该对象的引用而非本身。为此，保存引用值的变量是按照引用访问的

>**注意：** 在很多语言中，字符串是使用对象表示的，因此被认为是引用类型。ECMAScript
>打破了这个惯例。

### 动态属性

原始值和引用值定义类似，但是可以对值做什么差别很大，原始值无法操作属性，引用值可以操作属性

**注意**，原始类型的初始化可以只使用原始字面量形式。如果使用的是 new 关键字，则 JavaScript 会 创建一个 Object 类型的实例，但其行为类似原始值。下面来看看这两种初始化方式的差异

```javascript
let name1 = "Nicholas";
let name2 = new String("Matt");
name1.age = 27;
name2.age = 26;
console.log(name1.age); // undefined
console.log(name2.age); // 26
console.log(typeof name1); // string
console.log(typeof name2); // object
```

### 复制值

原始值复制值会

存储方式、复制方式

84

