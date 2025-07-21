##  **一、JavaScript基础 **

###  **1.JavaScript介绍 **

####  1.1 JavaScript 是什么  

1. JavaScript （是什么？）

是一种运行在客户端（浏览器）的编程语言，实现人机交互效果。 

2. 作用（做什么？）

– 网页特效 (监听用户的一些行为让网页作出对应的反馈)

– 表单验证 (针对表单数据的合法性进行判断)

– 数据交互 (获取后台的数据, 渲染到前端)

– 服务端编程 (node.js)

3. JavaScript的组成（有什么？）

 ●  ECMAScript: 规定了js基础语法核心知识。

比如：变量、分支语句、循环语句、对象等等

 ●  Web APIs :

- DOM 操作文档，比如对页面元素进行移动、大小、添加删除等操作
- BOM 操作浏览器，比如页面弹窗，检测窗口宽度、存储数据到浏览器等等

####  1.2 JavaScript 书写位置 

 1. 内部 JavaScript  

直接写在html文件里，用script标签包住

 规范 ：script标签写在</body>上面

```javascript
<body>    <!-- 内部 -->    <script>        alert('努力，奋斗');    </script></body>
```

 注意事项 ：

将`<script>`放在HTML文件的底部附近的原因是浏览器会按照代码在文件中的顺序加载HTML。

如果先加载的JavaScript期望修改其下方 HTML，那么它可能由于HTML尚未被加载而失效。

因此，将JavaScript代码放在HTM页面的底部附近通常是最好的策略。

 2. 外部 JavaScript 

代码写在以.js结尾的文件里

 语法 ：通过script标签，引入到html页面中。

![](https://i-blog.csdnimg.cn/blog_migrate/ec0c5d694af5499ac2bcfcf2184644f8.png)

```javascript
<body>    <!-- 外部 -->    <script src="./js/my.js"></script></body>
```

 注意事项 ：

1. script标签中间无需写代码，否则会被忽略！

2. 外部JavaScript会使代码更加有序，更易于复用，且没有了脚本的混合，HTML也会更加易读，因此这是个好的习惯。

 3. 内联 JavaScript 

代码写在标签内部

 语法： 

```javascript
<body>    <button onclick="alert('努力，奋斗')">点击</button></body>
```

####  1.3 JavaScript 注释  

● 单行注释（//）

 作用： //右边这一行的代码会被忽略

 快捷键： ctrl + /

● 块注释（/* */）

 作用： 在/* 和 */ 之间的所有内容都会被忽略

  快捷键： shift + alt + A

####  1.4 JavaScript 结束符 

● 结束符

 作用：  使用英文的 ; 代表语句结束

 实际情况：  实际开发中， 可写可不写 , 浏览器(JavaScript引擎)可以自动推断语句的结束位置

 现状：  在实际开发中，越来越多的人主张，书写JavaScript代码时省略结束符

 约定： 为了风格统一，结束符要么每句都写，要么每句都不写（按照团队要求）

####  1.5 JavaScript 输入输出语法 

输出和输入也可理解为人和计算机的交互，用户通过键盘、鼠标等向计算机输入信息，计算机处理后再展示结果给用户，这便是一次输入和输出的过程。

 1.输出语法：  

 语法1： ![](https://i-blog.csdnimg.cn/blog_migrate/0d01035b5fd3ff65b27210893274c3b9.png)

 作用： 向body内输出内容

 注意： 如果输出的内容写的是标签，也会被解析成网页元素，如：

![](https://i-blog.csdnimg.cn/blog_migrate/675e03fc62bb3f7dc6a4ac93ba4cdd9b.png)

![](https://i-blog.csdnimg.cn/blog_migrate/06893e954f33c5d15f38d91ede364928.png)

 语法2： ![](https://i-blog.csdnimg.cn/blog_migrate/bd0de13a0c4e0cd9bc5a08408f1a26d7.png)

 作用： 页面弹出警告对话框

 语法3：  ![](https://i-blog.csdnimg.cn/blog_migrate/f9d49a6f28322e2d8935e0e41c475f87.png)

 作用： 控制台输出语法，程序员调试使用

 2. 输入语法： 

 语法：  ![](https://i-blog.csdnimg.cn/blog_migrate/3768717567c13343768762d9cd561294.png)

 作用： 显示一个对话框，对话框中包含一条文字信息，用来提示用户输入文字

 3.JavaScript 代码执行顺序： 

按HTML文档流顺序执行JavaScript代码

alert() 和 prompt() 它们会跳过页面渲染先被执行

####  1.6 字面量 

在计算机科学中，字面量（literal）是在计算机中描述 事/物

比如：

我们工资是： 8000 此时8000就是数字字面量；'黑马程序员' 字符串字面量；还有接下来学的 `[]` 数组字面量 {} 对象字面量 等等

### 2. **变量**

####  2.1 变量是什么？ 

 变量： 

 ●  白话：变量就是一个装东西的盒子。

 ●  通俗：变量是计算机中用来 存储数据 的“容器”，它可以让计算机变得有记忆。

 ●  注意：变量不是数据本身，它们仅仅是一个用于存储数值的容器。可以理解为是一个个用来装东西的纸箱子。

####  2.2 变量的基本使用 

 1. 声明变量：  

要想使用变量，首先需要创建变量（也称为声明变量或者定义变量）

 语法： ![](https://i-blog.csdnimg.cn/blog_migrate/1ff23a208605eaa9a45eb6fea29b9d8e.png)

声明变量有两部分构成：声明关键字、变量名（标识）

let 即关键字 (let: 允许、许可、让)，所谓关键字是系统提供的专门用来声明（定义）变量的词语

  举例：let age 

我们声明了一个age变量，age 即变量的名称，也叫标识符

 2. 变量赋值： 

定义了一个变量后，就能够初始化它（赋值）。在变量名之后跟上一个“=”，然后是数值。![](https://i-blog.csdnimg.cn/blog_migrate/1a578d1ace58f3da24b26129dea8b1da.png)

注意：是通过变量名来获得变量里面的数据

简单点，也可以声明变量的时候直接完成赋值操作,这种操作也称为 变量 初始化 。

![](https://i-blog.csdnimg.cn/blog_migrate/54f31c72516d615da7772808f7e7946d.png)

 3. 更新变量：  

变量赋值后，还可以通过简单地给它一个不同的值来更新它。

![](https://i-blog.csdnimg.cn/blog_migrate/50595b64754a63f08eb30c200114aec7.png)

注意：  let 不允许多次声明一个变量 。

 4. 声明多个变量：  

变量赋值后，还可以通过简单地给它一个不同的值来更新它。

 语法： 多个变量中间用逗号隔开。

![](https://i-blog.csdnimg.cn/blog_migrate/a009f13da673cfb1ce54d7681c3a14de.png)

 说明： 看上去代码长度更短，但并 不推荐 这样。为了更好的可读性，请一行只声明一个变量。

![](https://i-blog.csdnimg.cn/blog_migrate/0107c3c9b292b50bb2a37677cbc82d6d.png)

 变量案例：交换变量的值 

核心思路：使用一个临时变量temp用来做中间存储。

```javascript
<body>  <script>    let num1 = 'pink老师'    let num2 = '周深'    let temp    // 都是把右边给左边    temp = num1    num1 = num2    num2 = temp    console.log(num1, num2)  </script></body>
```

####  2.3 变量的本质 

 内存： 计算机中存储数据的地方，相当于一个空间

 变量本质： 是程序在内存中申请的一块用来存放数据的小空间

####  2.4 变量命名规则与规范 

 规则： 必须遵守，不遵守报错 (法律层面)

 规范： 建议，不遵守不会报错，但不符合业内通识 （道德层面）

 1. 规则： 

不能用关键字。关键字：有特殊含义的字符，JavaScript内置的一些英语词汇。例如：let、var、if、for等

只能用下划线、字母、数字、$组成，且 数字不能开头  

字母严格区分大小写，如Age和age是不同的变量

 2. 规范： 

起名要有意义

遵守小驼峰命名法

第一个单词首字母小写，后面每个单词首字母大写。例：userName、myFirstName

![](https://i-blog.csdnimg.cn/blog_migrate/fd36ff315f3fe2519884b075734ad44b.png)

####  2.5变量拓展-let和var的区别 

 let 和 var 区别： 

在较旧的JavaScript，使用关键字 var 来声明变量 ，而不是 let。

var 现在开发中一般不再使用它，只是我们可能再老版程序中看到它。

let 为了解决 var 的一些问题。

var 声明:

○ 可以先使用 在声明 (不合理)

○ var 声明过的变量可以重复声明(不合理)

○ 比如变量提升、全局变量、没有块级作用域等等

 结论： 以后声明变量统一使用 let

####  2.6变量拓展-数组 

● 数组 (Array) —— 一种将 一组数据存储在单个变量名下 的优雅方式

![](https://i-blog.csdnimg.cn/blog_migrate/e50df16408dfed57b0ebe96a8b18074c.png)

 2.6.1 数组的基本使用 

 1. 声明语法：let 数组名 = [数据1, 数据2, ..., 数据n] 

○ 数组是按顺序保存，所以每个数据都有自己的编号

○ 计算机中的编号从0开始，第二个数据编号为1，以此类推

○ 在数组中，数据的编号也叫 索引或下标 

○ 数组可以存储任意类型的数据

 2.取值语法：数组名[下标] 

通过下标取数据。取出来是什么类型的，就根据这种类型特点来访问。

 3.一些术语： 

●  元素： 数组中保存的每个数据都叫数组元素

●  下标： 数组中数据的编号

●  长度： 数组中数据的个数，通过数组的length属性获得

```javascript
let arr = ['刘德华', '张学友', '黎明', '郭富城', 'pink老师', 10]console.log(arr.length)  // 6
```

###  **3.常量 **

 概念： 使用 const 声明的变量称为“常量”。

 使用场景： 当某个变量永远 不会改变 的时候，就可以使用 const 来声明，而不是let。

 命名规范： 和变量一致

 常量使用： 

```javascript
// 1.常量 不允许更改值    const PI = 3.14    console.log(PI)
```

 注意：  常量不允许重新赋值,声明的时候必须赋值（初始化）

 小技巧： 不需要重新赋值的数据使用const 

const — 类似于 let ，但是变量的值无法被修改。

###  4.数据类型 

 JS 数据类型整体分为两大类： 

● 基本数据类型

● 引用数据类型

![](https://i-blog.csdnimg.cn/blog_migrate/e822253773f9884ea8ab1e51a7ec9288.png)

####  4.1 数据类型 – 数字类型（Number） 

即我们数学中学习到的数字，可以是整数、小数、正数、负数。

![](https://i-blog.csdnimg.cn/blog_migrate/19910b79814afe12b247f408b1e5023c.png)

JavaScript 中的正数、负数、小数等 统一称为 数字类型。

 注意事项： 

JS是弱数据类型，变量属于哪种类型，只有赋值之后我们才能确认

Java是强数据类型 例如 int a = 3 必须是整数

数字可以有很多操作，比如，乘法 * 、除法 / 、加法 + 、减法 - 等等，所以经常和算术运算符一起。

数学运算符也叫 算术运算符 ，主要包括加、减、乘、除、取余（求模）。

➱ `+`：求和

➱ `-`：求差

➱ `*`：求积

➱`/`：求商

➱ %：取模（取余数），开发中经常作为某个数字是否被整除

同时使用多个运算符编写程序时，会按着某种顺序先后执行，我们称为优先级。

JavaScript中优先级越高越先被执行，优先级相同时以书从左向右执行。

● 总结： 先乘除取余，后加减，有小括号先算小括号里面的

NaN 代表一个计算错误。它是一个不正确的或者一个未定义的数学操作所得到的结果。

![](https://i-blog.csdnimg.cn/blog_migrate/9a6ffa541deef70110b1faf1e533511d.png)

NaN 是粘性的。任何对 NaN 的操作都会返回 NaN

 
 
 注意事项： 

1. 无论单引号或是双引号必须成对使用

2. 单引号/双引号可以互相嵌套，但是不以自已嵌套自已（口诀：外双内单，或者外单内双）

3. 必要时可以使用转义符 \，输出单引号或双引号

 字符串拼接 

 场景 ： + 运算符 可以实现字符串的拼接。

**口诀：数字相加，字符相连**

```javascript
    let age = 25    document.write('我今年' + age + '岁了')
```

 模板字符串 

 使用场景： 拼接字符串和变量

在没有它之前，要拼接变量比较麻烦

![](https://i-blog.csdnimg.cn/blog_migrate/5c587d56f1718cb9989e875740b8b183.png)

 语法： `` (反引号) 在英文输入模式下按键盘的tab键上方那个键（1左边那个键）。内容拼接变量时，用 ${ } 包住变量

```javascript
  <script>    // // 模板字符串 外面用`` 里面 ${变量名}    let uname = prompt('请输入您的姓名:')    let age = prompt('请输入您的年龄:')    document.write(`大家好，我叫${uname}， 我今年贵庚${age}岁了`)  </script>
```

####  4.3数据类型 – 布尔类型（boolean） 

表示肯定或否定时在计算机中对应的是布尔类型数据。

它有两个固定的值true和false，表示肯定的数据用true（真），表示否定的数据用false（假）。

####  4.4数据类型 – 未定义类型（undefined） 

未定义是比较特殊的类型，只有一个值undefined。

 什么情况出现未定义类型？ 

只声明变量，不赋值的情况下，变量的默认值为undefined，一般很少直接为某个变量赋值为undefined。

```javascript
    // 未定义类型   弱数据类型   声明一个变量未赋值就是 undefined    let num    console.log(num)
```

 工作中的使用场景： 

我们开发中经常声明一个变量，等待传送过来的数据。如果我们不知道这个数据是否传递过来，此时我们可以通过检测这个变量是不是undefined，就判断用户是否有数据传递过来。

####  4.5数据类型 – null（空类型） 

JavaScript 中的 null 仅仅是一个代表“无”、“空”或“值未知”的特殊值

```javascript
    //  null 空的    let obj = null    console.log(obj)
```

 null 和 undefined 区别： 

● undefined 表示没有赋值

● null 表示赋值了，但是内容为空

```javascript
    // 计算有区别    console.log(undefined + 1)  // NaN    console.log(null + 1) // 1
```

 null 开发中的使用场景： 

官方解释：把null作为尚未创建的对象

通俗解释：将来有个变量里面存放的是一个对象，但是对象还没创建好，可以先给个null

####  4.6控制台输出语句和检测数据类型 

 1.控制台输出语句： 

控制台语句经常用于测试结果来使用。

数字型和布尔型颜色为蓝色，字符串和undefined颜色为灰色

 2.   通过 typeof   关键字检测数据类型 

typeof 运算符可以返回被检测的数据类型。它支持两种语法形式：

1. 作为运算符： typeof x （常用的写法）

2. 函数形式： typeof(x)

换言之，有括号和没有括号，得到的结果是一样的，所以我们直接使用运算符的写法。

 ![](https://i-blog.csdnimg.cn/blog_migrate/cb232ebb2695f880d0622e42d92e9b51.png)![](https://i-blog.csdnimg.cn/blog_migrate/e5e902fc2f5b2cd556eac32907304816.png)

###  **5.类型转换**

####  5.1 为什么需要类型转换 

JavaScript是弱数据类型： JavaScript也不知道变量到底属于那种数据类型，只有赋值了才清楚。

坑：使用表单、prompt 获取过来的数据默认是字符串类型的，此时不能直接进行加法运算。

此时需要转换变量的数据类型。

通俗来说，就是把一种数据类型的变量转换成我们需要的数据类型。

####  5.2 隐式转换 

某些运算符被执行时，系统内部自动将数据类型进行转换，这种转换称为隐式转换。

 规则： 

1. + 号两边只要有一个是字符串，都会把另外一个转成字符串

```javascript
    console.log('pink' + 1) // pink1    console.log(2 + 2)   // 4    console.log(2 + '2') // 22
```

2. 除了+以外的算术运算符 比如 - * / 等都会把数据转成数字类型

```javascript
    console.log(2 - 2)    // 0    console.log(2 - '2')  // 0 
```

 缺点：  转换类型不明确，靠经验才能总结

 小技巧： 

1. +号作为正号解析可以转换成数字型

```javascript
console.log(+'123')  // 转换为数字型 123
```

2.任何数据和字符串相加结果都是字符串

####  5.3 显式转换 

编写程序时过度依靠系统内部的隐式转换是不严禁的，因为隐式转换规律并不清晰，大多是靠经验总结的规律。为了避免因隐式转换带来的问题，通常根逻辑需要对数据进行显示转换。

 概念：  自己写代码告诉系统该转成什么类型

 转换为数字型有三种方法： 

 ●  Number(数据)

        转成数字类型

        如果字符串内容里有非数字，转换失败时结果为NaN（Not a Number）即不是一个数字

        NaN也是number类型的数据，代表非数字

 ●  parseInt(数据) 只保留整数

 ●  parseFloat(数据) 可以保留小数

 转换为字符型: 

 ●  String(数据)

 ●  变量.toString(进制)

###  综合案例：用户订单信息案例 

![](https://i-blog.csdnimg.cn/blog_migrate/c00396e1d393ce19fa85b40d36d6f706.png)

```html
<!DOCTYPE html><html lang="en"><head>    <meta charset="UTF-8">    <meta http-equiv="X-UA-Compatible" content="IE=edge">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <title>Document</title>    <style>        h2 {            text-align: center;        }        table,        th,        td {            border: 1px solid #000;        }        table {            /* 合并相邻边框 */            border-collapse: collapse;            text-align: center;            height: 80px;            margin: 0 auto;        }        th {            padding: 10px 30px;        }    </style></head><body>    <h2>订单确认</h2>    <script>        let price = +prompt('请输入商品价格：')        let num = +prompt('请输入商品数量：')        let address = prompt('请输入收货地址：')        let total = price * num        document.write(`        <table>            <thead>                <th>商品名称</th>                <th>商品价格</th>                <th>商品数量</th>                <th>总价</th>                <th>收货地址</th>            </thead>            <tbody>                <tr>                    <td>小米手机青春PLUS</td>                    <td>${price}元</td>                    <td>${num}</td>                    <td>${total}元</td>                    <td>${address}</td>                </tr>            </tbody>        </table>        `)    </script></body></html>
```

###   6.运算符 

####  6.1 赋值运算符 

赋值运算符（=）：对变量进行赋值的运算符

= 将等号右边的值赋予给左边, 要求左边必须是一个容器

其他赋值运算符： += 、-= 、*= 、/= 、%=

使用这些运算符可以在对变量赋值时进行快速操作

![](https://i-blog.csdnimg.cn/blog_migrate/36bfd52aff453314da6b4076eaa68725.png)

####  6.2 一元运算符 

众多的JavaScript的运算符可以根据所需表达式的个数，分为一元运算符、二元运算符、三元运算符。

**●** **自增（++）** 

作用：让变量的值 +1

**● 自减（--）**

作用：让变量的值 -1

●  使用场景： 经常用于计数来使用。 比如进行10次操作，用它来计算进行了多少次了

●  自增运算符的用法： 

  前置自增：                                                          后置自增： 

![](https://i-blog.csdnimg.cn/blog_migrate/fe81f0585d7ebc91b957b7bf696eb143.png)![](https://i-blog.csdnimg.cn/blog_migrate/0c0035206173ccdbcbcd4d58dff7c5b9.png)

前置自增和后置自增的 区别 ：

前置自增：先自加再使用（记忆口诀：++在前 先加）

 ![](https://i-blog.csdnimg.cn/blog_migrate/54f9ccea91ed7d99fea4d8e1ac1a01f7.png)

后置自增：先使用再自加（记忆口诀：++在后 后加）

![](https://i-blog.csdnimg.cn/blog_migrate/2c7c0e1cd7c1e38bb9e807237c0ad62a.png)

 注意： 

1. 前置自增和后置自增独立使用时二者并没有差别！

2. 实际开发中，我们一般都是单独使用的，后置自增会使用相对较多

拓展：

![](https://i-blog.csdnimg.cn/blog_migrate/2e9b6efa568fbfaf1e0759f3ecd0430e.png)

输出7

####  6.3 比较运算符 

使用场景：比较两个数据大小、是否相等

>： 左边是否大于右边

<： 左边是否小于右边

>=： 左边是否大于或等于右边

<=： 左边是否小于或等于右边

==： 左右两边 值 是否相等

===： 左右两边是否 类型 和 值 都相等

!==： 左右两边是否不全等

比较运算符有隐式转换。比较结果为boolean类型，即只会得到true或false。

 = 和 == 和 === 对比 ：

**●** = 单等是赋值

**●** == 是判断

**●** === 是全等

 开发中判断是否相等，强烈推荐使用 === 

**●** 字符串比较，是比较的字符对应的ASCII码

        从左往右依次比较，如果第一位一样再比较第二位，以此类推

**●** NaN不等于任何值，包括它本身，涉及到NaN都是false

**●** 尽量不要比较小数，因为小数有精度问题

**●** 不同类型之间比较会发生隐式转换

        最终把数据隐式转换转成number类型再比较

        所以开发中，如果进行准确的比较我们更喜欢 === 或者 !==

####  6.4 逻辑运算符 

![](https://i-blog.csdnimg.cn/blog_migrate/670082716d97669c20badbe3ca6f3587.png)

表达式1 && 表达式2：表达式1为真，返回表达式2；表达式1为假，返回表达式1

表达式1  ||  表达式2：表达式1为真，返回表达式1；表达式1为假，返回表达式2

####   6.5 运算符优先级 

![](https://i-blog.csdnimg.cn/blog_migrate/64e79d33de0fe9278a451bf0ebe8cae0.png)

一元运算符里面的逻辑非优先级很高。逻辑与比逻辑或优先级高。

###  7.语句 

####  7.1 表达式语句 

**●** 表达式：表达式是可以被求值的代码，JavaScript 引擎会将其计算出一个结果。

**●** 语句：语句是一段可以执行的代码。比如：prompt()可以弹出一个输入框，还有if语句、for循环语句等等

 区别： 

 表达式： 因为表达式可被求值，所以它可以写在赋值语句的右侧。如：num = 3 + 4

 语句： 而语句不一定有值，所以比如alert()、for和break等语句就不能被用于赋值。

####  7.2 分支语句（ if语句、三元运算符、switch语句 ） 

程序三大流程控制语句

**●** 以前我们写的代码，写几句就从上往下执行几句，这种叫**顺序结构**

**●** 有的时候要根据条件选择执行代码，这种就叫**分支结构**

**●** 某段代码被重复执行，就叫**循环结构**

![](https://i-blog.csdnimg.cn/blog_migrate/08306475b559fe3ec1d289da59acae50.png)

**●** 分支语句可以让我们有选择性的执行想要的代码

**●** 分支语句包含：if分支语句、三元运算符、switch语句

 7.2.1 if语句 

if语句有三种使用：单分支、双分支、多分支

**●** 单分支 if 语法：

![](https://i-blog.csdnimg.cn/blog_migrate/640fe22a85c5200d99cd6c06711470d3.png)

        括号内的条件为true时，进入大括号里执行代码；小括号内的结果若不是布尔类型时，会发生隐式转换转为布尔类型。除了0 所有的数字都为真，除了''所有的字符串都为真true

        如果大括号只有一个语句，大括号可以省略，但是不提倡这么做

**●** 双分支 if 语法：

![](https://i-blog.csdnimg.cn/blog_migrate/4d7c34f22197197c38fb6788730fa376.png)

**●** 多分支 if 语法：

 使用场景： 适合于有多个结果的时候，比如学习成绩可以分为： 优 良 中 差

![](https://i-blog.csdnimg.cn/blog_migrate/0a7541c142b044a4194583a72304593d.png)

先判断条件1，若满足条件1就执行代码1，其他不执行；若不满足则向下判断条件2，满足条件2执行代码2，其他不执行；若依然不满足继续往下判断，依次类推；若以上条件都不满足，执行else里的代码n 

 7.2.2 三元运算符 

 使用场景：  其实是比if双分支更简单的写法，可以使用 三元表达式，一般用来取值

 符号： ? 与 : 配合使用

 语法： ![](https://i-blog.csdnimg.cn/blog_migrate/f082516b604b6a5281fba8eb09d4db37.png)

**数字补0案例**

用户输入1个数，如果数字小于10，则前面进行补0， 比如09

```javascript
  <script>    // 1. 用户输入     let num = prompt('请您输入一个数字:')    // 2. 判断输出- 小于10才补0    num = num < 10 ? 0 + num : num    alert(num)  </script>
```

 7.2.3   switch语句 

 语法： 

![](https://i-blog.csdnimg.cn/blog_migrate/95766b55cd82526c5d1d5f180bcb7861.png)

 释义： 

找到跟小括号里数据 全等 的case值，并执行里面对应的代码，例：数据若跟值2全等，则执行代码2；若没有全等 === 的则执行default里的代码 

 注意事项： 

1. switch case语句一般用于等值判断,不适合于区间判断

2. switch case一般需要配合break关键字使用，没有break会造成case穿透

**简单计算器案例**

```javascript
<script>    // 1.用户输入  2个数字 +  操作符号  + - *  /     let num1 = +prompt('请您输入第一个数字:')    let num2 = +prompt('请您输入第二个数字:')    let sp = prompt('请您输入 + - * / 其中一个:')    // 2. 判断输出    switch (sp) {      case '+':        alert(`两个数的加法操作是${num1 + num2}`)        break      case '-':        alert(`两个数的减法操作是${num1 - num2}`)        break      case '*':        alert(`两个数的乘法操作是${num1 * num2}`)        break      case '/':        alert(`两个数的除法操作是${num1 / num2}`)        break      default:        alert(`请输入+-*/`)    }   </script>
```

####  7.3 循环结构 

 7.3.1 断点调试 

作用：学习时可以帮助更好的理解代码运行，工作时可以更快找到bug

浏览器打开调试界面

        1. 按F12打开开发者工具

        2. 点到sources一栏

        3. 选择代码文件，添加断点并刷新

断点：在某句代码上加的标记就叫断点，当程序执行到这句有标记的代码时会停下来

![](https://i-blog.csdnimg.cn/blog_migrate/8b8b20e85b8c809ea02c6e1ef327314f.png)

 7.3.2 while 循环 

 while循环 就是在满足条件期间，重复执行某些代码。

 1. while 循环基本语法： 

![](https://i-blog.csdnimg.cn/blog_migrate/f5f1b7c96e57e23cc7ca8469a1c3dece.png)

 释义： 

跟if语句很像，都要满足小括号里的条件为true才会进入循环体执行代码。while大括号里代码执行完毕后不会跳出，而是继续回到小括号里判断条件是否满足，若满足又执行大括号里的代码，然后再回到小括号判断条件，直到括号内条件不满足，即跳出。

 2. while 循环三要素： 

循环的本质就是以某个变量为起始值，然后不断产生变化量，慢慢靠近终止条件的过程。

所以，while循环需要具备三要素：

1. 变量起始值

2. 终止条件（没有终止条件，循环会一直执行，造成死循环）

3. 变量变化量（用自增或者自减）

 3 循环退出 

循环结束：

● break：退出循环

● continue：结束本次循环，继续下次循环

 区别：  

● continue退出本次循环，一般用于排除或者跳过某一个选项的时候, 可以使用continue

● break退出整个循环，一般用于结果已经得到, 后续的循环不需要的时候可以使用

###  综合案例：简易ATM取款机案例 

```javascript
<script>    // 1. 开始循环 输入框写到 循环里面    // 3. 准备一个总的金额    let money = 100    while (true) {      let re = +prompt(`        请您选择操作：        1.存钱        2.取钱        3.查看余额        4.退出        `)      // 2. 如果用户输入的 4 则退出循环， break  写到if 里面，没有写到switch里面， 因为4需要break退出循环      if (re === 4) {        break      }      // 4. 根据输入做操作      switch (re) {        case 1:          // 存钱          let cun = +prompt('请输入存款金额')          money = money + cun          break        case 2:          // 存钱          let qu = +prompt('请输入取款金额')          money = money - qu          break        case 3:          // 存钱          alert(`您的银行卡余额是${money}`)          break      }    }  </script>
```

###  8.for循环 

 1. for循环语法 

 作用： 重复执行代码

 好处： 把声明起始值、循环条件、变化值写到一起，让人一目了然，它是最常使用的循环形式

![](https://i-blog.csdnimg.cn/blog_migrate/99061116868c968c19183b88e3e49f3f.png)

 2. 退出循环 

● continue退出本次循环，一般用于排除或者跳过某一个选项的时候,可以使用continue 

● break退出整个for循环，一般用于结果已经得到, 后续的循环不需要的时候可以使用

 了解： 

1. while(true) 来构造“无限”循环，需要使用break退出循环。

2. for(;;) 也可以来构造“无限”循环，同样需要使用break退出循环。

 for循环和while循环的区别：  

● 当如果明确了循环的次数的时候推荐使用for循环

● 当不明确循环的次数的时候推荐使用while循环

 3. for 循环嵌套： 一个循环里再套一个循环，一般用在for循环里

![](https://i-blog.csdnimg.cn/blog_migrate/f066a26a7927f3e20aee4c6679300526.png)

 案例：九九乘法表 

```javascript
  <script>    // 1. 外层循环控制行数    for (let i = 1; i <= 9; i++) {      // 2. 里层循环控制列数      for (let j = 1; j <= i; j++) {        document.write(`<span>${j} X ${i} = ${i * j}</span>`)      }      // 换行      document.write('<br>')    }  </script>
```

### 9. 数 组 

####  9.1 数组是什么 

数组：(Array)是一种可以按顺序保存数据的 数据类型

场景：如果有多个数据可以用数组保存起来，然后放到一个变量中，管理非常方便

#### **9.2 数组的基本使用**

**1. 声明语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/9257977205df781fb0cd409ae5d27bba.png)

![](https://i-blog.csdnimg.cn/blog_migrate/8b88c083d95999835d95284defdce5c5.png)

数组是按顺序保存，所以每个数据都有自己的编号

计算机中的编号从0开始，所以小明的编号为0，小刚编号为1，以此类推

在数组中，数据的编号也叫 索引或下标 

数组可以存储任意类型的数据

**2. 取值语法：数组名[下标]**

通过下标取数据，取出来是什么类型的，就根据这种类型特点来访问

**3. 一些术语：**

元素：数组中保存的每个数据都叫数组元素

下标：数组中数据的编号

长度：数组中数据的个数，通过数组的length属性获得

**4. 遍历数组(重点)**

用循环把数组中每个元素都访问到,一般会用for循环遍历

语法：

![](https://i-blog.csdnimg.cn/blog_migrate/c52026afb74a544af25f50ac734d787c.png)

#### 9.3 操作数组

数组本质是数据集合, 操作数据无非就是 增 删 改 查

**语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/596b31d0d77ac82ba179068645c5a81c.png)

 **操作数组-新增**

arr.push() 方法将一个或多个元素添加到数组的**末尾**，并返回该数组的新长度 (重点)

**语法：** ![](https://i-blog.csdnimg.cn/blog_migrate/7a73ed6896a9f97d26650aa32a8f1d2a.png)

![](https://i-blog.csdnimg.cn/blog_migrate/10d5172c6dffdebef2cc1c637fe91ad3.png)

arr.unshift(新增的内容) 方法将一个或多个元素添加到数组的 **开头** ，并返回该数组的新长度

**语法：** ![](https://i-blog.csdnimg.cn/blog_migrate/ec0d9c212f24f796bdba38c7496473ab.png)

![](https://i-blog.csdnimg.cn/blog_migrate/8cf4acc7a91c8f43e55da03a4f94066b.png)

**操作数组-删除** 

arr. pop() 方法从数组中删除**最后一个**元素，并返回该元素的值

**语法：arr.pop()**

![](https://i-blog.csdnimg.cn/blog_migrate/01c0859ec744403481c043e56e01f18b.png)

arr. shift() 方法从数组中删除**第一个**元素，并返回该元素的值

**语法：arr.shift()**

![](https://i-blog.csdnimg.cn/blog_migrate/8123859df3c244829b9804c1dab77596.png)

数组. splice() 方法 删除指定元素

**语法：数组.splice(start, deleteCount, item1, item2, ..., itemN)**

从start开始删除deleteCount个数组元素，并从start处开始添加item（item可加可不加）

**使用场景：**

1. 随机抽奖，中奖的用户就需要从数组里面删除，不允许重复抽奖

2. 点击删除按钮，相关的数据会从商品数据中删除

**语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/02464459e75878454f47a3f3c39308b9.png)

解释：

start 起始位置： 指定修改的开始位置（从0计数）

deleteCount：  表示要移除的数组元素的个数。可选的，如果省略则默认从指定的起始位置删

除到最后。

### 综合案例：根据数据生成柱形图

```html
<!DOCTYPE html><html lang="en"> <head>    <meta charset="UTF-8">    <meta http-equiv="X-UA-Compatible" content="IE=edge">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <title>Document</title>    <style>        * {            margin: 0;            padding: 0;        }         .box {            display: flex;            width: 700px;            height: 300px;            border-left: 1px solid pink;            border-bottom: 1px solid pink;            margin: 100px auto;            justify-content: space-around;            align-items: flex-end;            text-align: center;        }         .box>div {            display: flex;            width: 50px;            background-color: pink;            flex-direction: column;            justify-content: space-between;        }         .box div span {             margin-top: -20px;        }         .box div h4 {            margin-bottom: -35px;            width: 70px;            margin-left: -10px;        }    </style></head> <body>    <script>        // 1. 四次弹框效果        // 声明一个新的数组        let arr = []        for (let i = 1; i <= 4; i++) {            // let num = prompt(`请输入第${i}季度的数据:`)            // arr.push(num)            arr.push(prompt(`请输入第${i}季度的数据:`))            // push记得加小括号，不是等号赋值的形式        }        // console.log(arr)  ['123','135','345','234']        // 盒子开头        document.write(` <div class="box">`)         // 盒子中间 利用循环的形式  跟数组有关系        for (let i = 0; i < arr.length; i++) {            document.write(`              <div style="height: ${arr[i]}px;">                <span>${arr[i]}</span>                <h4>第${i + 1}季度</h4>              </div>                      `)        }        // 盒子结尾        document.write(` </div>`)    </script></body> </html>
```

#### 9.4 冒泡排序

冒泡排序是一种简单的排序算法。

它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。走访

数列的工作是重 复地进行直到没有再需要交换，也就是说该数列已经排序完成。

![](https://i-blog.csdnimg.cn/blog_migrate/c2a3d96e3e98604c4d6d3172a391f886.png)

#### **9.5 数组排序**

数组. sort() 方法可以排序

```javascript
let arr = [4, 2, 5, 1, 3]// 1.升序排列写法arr.sort(function (a, b) {return a - b})console.log(arr) // [1, 2, 3, 4, 5]// 降序排列写法arr.sort(function (a, b) {return b - a})console.log(arr) // [5, 4, 3, 2, 1]
```

### 10.函数

#### 10.1 为什么需要函数

**函数：** function，是被设计为 执行特定任务 的代码

**说明：**函数可以把具有相同或相似逻辑的代码“包裹”起来，通过函数调用执行这些被“包裹”的代码逻辑，这么做的优势是有利于 精简代码方便复用 ，提高开发效率 。

比如我们前面使用的 alert() 、 prompt() 和 console.log() 都是一些 js **函数** ，只不过已经封装好了，我们直接使用的。

#### 10.2 函数使用

**函数的声明语法**：

![](https://i-blog.csdnimg.cn/blog_migrate/c25d6164414dc39554977bcff2d1834c.png)

**函数名命名规范**：

和变量命名基本一致；尽量小驼峰式命名法；前缀应该为动词。命名建议：常用动词约定

![](https://i-blog.csdnimg.cn/blog_migrate/d4e3752e8320252e5591a78e5dd5f719.png)

**函数的调用语法：函数名()**

注意：声明（定义）的函数必须调用才会真正被执行，使用 () 调用函数

![](https://i-blog.csdnimg.cn/blog_migrate/af69ce20809d2d88abb402a3ffb60faa.png)

我们曾经使用的 alert() , parseInt() 这种名字后面跟小括号的本质都是函数的调用

**函数体：**

函数体是函数的构成部分，它负责将相同或相似代码“包裹”起来，直到函数调用时函数体内的代码才会被执行。函数的功能代码都要写在函数体当中。

**函数的复用代码和循环重复代码有什么不同？**

●  循环代码写完即执行，不能很方便控制执行位置。

● 函数的复用代码可 随时调用，随时执行，可重复调用。

#### 10.3 函数传参

若函数完成功能需要调用者传入数据，那就需要有参数的函数。 这样可以极大提高函数的灵活性。

**声明语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/eb2453ada61c51e94022459c3b3788b0.png)

**参数列表：** 传入数据列表；声明这个函数需要传入几个数据；多个数据用逗号隔开。

**调用语法：函数名(传递的参数列表)**

调用函数时，需要传入几个数据就写几个，用逗号隔开。

![](https://i-blog.csdnimg.cn/blog_migrate/0b98c538d504ecef9baba4880cbeed4a.png)

![](https://i-blog.csdnimg.cn/blog_migrate/7cf88a2da7b8a8adc8fdaeed70bf77b2.png)

**形参：**声明函数时写在函数名右边小括号里的叫形参（形式上的参数）

**实参：**调用函数时写在函数名右边小括号里的叫实参（实际上的参数）

形参可以理解为是 在这个函数内声明的 变量 （比如 num1 = 10）实参可以理解为是给这个变量赋值

开发中尽量保持形参和实参个数一致

我们曾经使用过的 alert('打印'), parseInt('11'), Number('11') 本质上都是函数调用的传参。

形参： 可以看做变量，但是如果一个变量不给值， 默认是 undefined  

但是如果做用户不输入实参，刚才的案例则出现 undefined + undefined 结果是 NaN

可以改进下，用户不输入实参，可以给 **形参默认值** ，默认为 0, 这样程序更严谨，可以如下操作：

![](https://i-blog.csdnimg.cn/blog_migrate/16fba39d7ac6d85fdc018284d4929062.png)

 这个默认值只会在缺少实参参数传递时才会被执行，所以有参数会优先执行传递过来的实参, 否则默认为undefined

#### **10.4 函数返回值**

有 返回值 函数的概念： 当调用某个函数，这个函数会返回一个结果出来。

当函数需要返回数据出去时，用 return 关键字。这样 对执行结果的扩展性更高，可以让其他的程序使用这个结果。

**语法：return 数据**

![](https://i-blog.csdnimg.cn/blog_migrate/85e716e767ca0cc9302d4d53b4b7d9ac.png)

在函数体中使用 return 关键字能将内部的执行结果交给函数外部使用。return 后面代码不会再被执行，会立即结束当前函数，所以 return 后面的数据不要换行写。 return函数可以没有 return ，这种情况 **函数默认返回值为 undefined** 。

#### 10.5 函数细节补充

● 两个相同的函数后面的会覆盖前面的函数

● 在Javascript中 实参的个数和形参的个数可以不一致

        如果形参过多 会自动填上undefined (了解即可)

        如果实参过多 那么多余的实参会被忽略 (函数内部有一个arguments，里面装着所有的实参)

● 函数一旦碰到return就不会在往下执行了，函数的结束用return

**break的结束和return结束有什么区别？**

●  break用来跳出整个语句块，结束当前循环的执行。另外我们要特别注意， break语句总是跳出自己所在的那一层循环。当两个for循环嵌套时，如果break语句位于内层的for循环，它只会跳出内层的for循环，但不会跳出外层的for循环。

●  return并不是专门用来结束循环的关键字，但它可以用来结束一个方法或循环，而且还能返回return中的值。当一个方法执行到return语句时，该方法就会被结束。与break和continue不同的是， return是直接结束整个方法，不管这个return处在多少层的循环之内。

#### **10.6 作用域**

通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而限定这个名字的 可用性的代码范围 就是这个名字的 **作用域** 。

作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字冲突。

![](https://i-blog.csdnimg.cn/blog_migrate/fcf0a892ca7b6ce31997568c70f89c91.png)

 在JavaScript中，根据作用域的不同，变量可以分为：

![](https://i-blog.csdnimg.cn/blog_migrate/5a080b50ba1604bb79771f8bac14492f.png)

**特殊情况：**

1.如果函数内部，变量没有声明，直接赋值 ，也当 全局变量 看，但是强烈不推荐

2.但是有一种情况，函数内部的形参可以看做是局部变量。

**变量的访问原则：**

只要是代码，就至少有一个作用域。如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域。

访问原则： **在能够访问到的情况下 先局部， 局部没有在找全局**

**作用域链：**采取**就近原则**的方式来查找变量最终的值

```javascript
  <script>    let a = 1    function fn1() {        let a = 2        let b = '22'        fn2()        function fn2() {          let a = 3          fn3()          function fn3() {            let a = 4            console.log(a) //a的值 ?            console.log(b) //b的值 ?          }        }    }    fn1()  </script>
```

 a 的值为4，b的值为 ‘22’

#### 10.7 匿名函数

![](https://i-blog.csdnimg.cn/blog_migrate/c08511de28ef387f82e4281c537ae2e7.png)

**匿名函数：** 没有名字的函数, 无法直接使用。

**使用方式（有两种）：**1.函数表达式   2.立即执行函数。

**1. 函数表达式**

将匿名函数赋值给一个变量，并且通过变量名称进行调用 我们将这个称为 **函数表达式**

**语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/7aa411dd8489cb8a736ccc4dbc2b10a3.png)

**调用：**

![](https://i-blog.csdnimg.cn/blog_migrate/b18f282bb52b1f39a8ac714e68503c36.png)

其中函数的形参和实参使用跟具名函数一致。

**函数表达式要求必须先声明，再调用。**

![](https://i-blog.csdnimg.cn/blog_migrate/f1c354fc9e4c62881002dceef07f17d0.png)

运行结果为：程序报错 

**2. 立即执行函数**

场景介绍: 避免全局变量之间的污染

**语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/faa7179030e9b07260e92535efb38eaa.png)

**注意：** 多个立即执行函数要用 ; 隔开，要不然会报错 

### 综合案例：转换时间案例

用户输入秒数，可以自动转换为时分秒

**计算公式：计算时分秒**

小时： h = parseInt(总秒数 / 60 / 60 % 24)

分钟： m = parseInt(总秒数 / 60 % 60 )

秒数: s = parseInt(总秒数 % 60)

```javascript
  <script>    // 1. 用户输入    let second = +prompt('请输入秒数:')    // 2.封装函数    function getTime(t) {      // 3. 转换       let h = parseInt(t / 60 / 60 % 24)      let m = parseInt(t / 60 % 60)      let s = parseInt(t % 60)      h = h < 10 ? '0' + h : h      m = m < 10 ? '0' + m : m      s = s < 10 ? '0' + s : s      return `转换完毕之后是${h}小时${m}分${s}秒`    }    let str = getTime(second)    document.write(str)  </script>
```

#### **10.8 逻辑中断**

开发中，还会见到以下的写法：

![](https://i-blog.csdnimg.cn/blog_migrate/f0f80feeb313a0d2fd49dcc5cd3b6ab3.png)

其实类似参数的默认值写法 

**1. 逻辑运算符里的短路**

**短路：**只存在于 && 和 || 中，当满足一定条件会让右边代码不执行

![](https://i-blog.csdnimg.cn/blog_migrate/5485cfcc933fdb8fbdc7211867d59c05.png)

**原因：**通过左边能得到整个式子的结果，因此没必要再判断右边

**运算结果：**无论 && 还是 || ，运算结果都是最后被执行的表达式值，一般用在变量赋值

表达式1 && 表达式2：表达式1为真，返回表达式2；表达式1为假，返回表达式1

表达式1  ||  表达式2：表达式1为真，返回表达式1；表达式1为假，返回表达式2

**2. 转换为Boolean型**

**显示转换：** Boolean(内容)

**记忆** ： **‘’ 、0、undefined、null、false、NaN 转换为布尔值后都是false, 其余则为 true**

![](https://i-blog.csdnimg.cn/blog_migrate/ebfcef499e9668762a35405493e450ea.png)

**隐式转换：**

1. 有字符串的加法 “” + 1 ，结果是 “1”

2. 减法 - （像大多数数学运算一样）只能用于数字，它会使空字符串 "" 转换为 0

3. null 经过数字转换之后会变为 0

4. undefined 经过数字转换之后会变为 NaN

![](https://i-blog.csdnimg.cn/blog_migrate/86ca4508720076c82128766f8881cef4.png)

### 10.对象

#### 10.1 对象是什么

对象（object）：JavaScript 里的一种数据类型。

可以理解为是一种 无序的数据集合 ， 注意数组是有序的数据集合。 用来描述某个事物 ，例如描述一个人，人有姓名、年龄、性别等信息、还有吃饭睡觉打代码等功能。 如果用多个变量保存则比较散，用对象比较统一。

![](https://i-blog.csdnimg.cn/blog_migrate/3c2cb5b3a4b774e8a86c96d89661c3e3.png)

#### 10.2 对象使用

**1. 对象声明语法**

![](https://i-blog.csdnimg.cn/blog_migrate/839499fc5e0baf8f43ae54fbdbbb73db.png)![](https://i-blog.csdnimg.cn/blog_migrate/c2b984f6ca81009815575069ec143509.png) 

**2. 对象由属性和方法组成**

**属性：**信息或叫 特征 （名词）。 比如 手机尺寸、颜色、重量等…

**方法：**功能或叫 行为 （动词）。 比如 手机打电话、发短信、玩游戏…

![](https://i-blog.csdnimg.cn/blog_migrate/5edb0c3ea07bd62961aa0a4934a3f0a7.png)

**3. 属性**

数据描述性的信息称为属性，如人的姓名、身高、年龄、性别等，一般是名词性的。

![](https://i-blog.csdnimg.cn/blog_migrate/3c2cb5b3a4b774e8a86c96d89661c3e3.png)

● 属性都是成对出现的，包括 属性名 和 值 ，它们之间使用英文 : 分隔

● 多个属性之间使用英文 , 分隔

● 属性就是依附在对象上的变量（外面是变量，对象内是属性）

● 属性名可以使用 "" 或 ''， 一般情况下省略 ，除非名称遇到特殊符号如空格、中横线等

**4.对象中的方法**

数据行为性的信息称为方法，如跑步、唱歌等，一般是动词性的，其本质是函数。

![](https://i-blog.csdnimg.cn/blog_migrate/d99e86a586932634f079bca4abf33079.png)

● 方法是由方法名和函数两部分构成，它们之间使用 : 分隔

● 多个属性之间使用英文 , 分隔

● 方法是依附在对象中的函数

●  方法名可以使用 "" 或 ''，一般情况下省略，除非名称遇到特殊符号如空格、中横线等

#### 10.2 对象使用

对象本质是无序的数据集合, 操作数据无非就是 增 删 改 查

![](https://i-blog.csdnimg.cn/blog_migrate/5ef91aaf99c47e45ef401429b3f417f9.png)

**查询对象：**

1. 对象名.属性

声明对象，并添加了若干属性后，可以使用 . 获得对象中属性对应的值，我称之为属性访问。

简单理解就是获得对象里面的属性值。

![](https://i-blog.csdnimg.cn/blog_migrate/05e4e2e6641e60ba3a9b52a532aa6b83.png)

2. 对象[‘属性’] （ ‘’ 或 "" 都可以）

对于多词属性或则 - 等属性，点操作就不能用了。

![](https://i-blog.csdnimg.cn/blog_migrate/56fe79c2eb79d2d049ad68a516bfdcdb.png)

![](https://i-blog.csdnimg.cn/blog_migrate/e4b068fdde02b05394a3aa3179189ecc.png)  

[ ] 语法里面的值如果不添加引号 默认会当成变量解析

**总结：** 没有必要的时候直接使用点语法, 在需要解析变量的时候使用 [] 语法

**修改属性：** 对象名.属性 = 新值

**增加属性：** 对象名.新属性 = 新值

**删除属性：** delete 对象名.属性

**方法调用：** 声明对象，并添加了若干方法后，可以使用 . 调用对象中函数，称之为方法调用。

也可以添加形参和实参。

#### 10.3 遍历对象

![](https://i-blog.csdnimg.cn/blog_migrate/90f44b339386a3fad36a6dd5fae04dc6.png)

一般不用这种方式遍历数组、主要是用来遍历对象

for in语法中的 k 是一个变量, 在循环的过程中依次代表对象的属性名

由于 k 是变量, 所以必须使用 [ ] 语法解析

**一定记住：** **k** 是获得对象的 **属性名** ， **对象名[k]** 是获得 **属性值**

案例：渲染学生信息表

```html
<!DOCTYPE html><html lang="en"> <head>    <meta charset="UTF-8">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <title>Document</title>    <style>        table {            width: 600px;            text-align: center;        }         table,        th,        td {            border: 1px solid #ccc;            border-collapse: collapse;        }         caption {            font-size: 18px;            margin-bottom: 10px;            font-weight: 700;        }         tr {            height: 40px;            cursor: pointer;        }         table tr:nth-child(1) {            background-color: #ddd;        }         table tr:not(:first-child):hover {            background-color: #eee;        }    </style></head> <body>    <h2>学生信息</h2>    <p>将数据渲染到页面中...</p>     <table>        <caption>学生列表</caption>        <tr>            <th>序号</th>            <th>姓名</th>            <th>年龄</th>            <th>性别</th>            <th>家乡</th>        </tr>        <!-- script写到这里 -->        <script>            // 1. 数据准备            let students = [                { name: '小明', age: 18, gender: '男', hometown: '河北省' },                { name: '小红', age: 19, gender: '女', hometown: '河南省' },                { name: '小刚', age: 17, gender: '男', hometown: '山西省' },                { name: '小丽', age: 18, gender: '女', hometown: '山东省' },                { name: '晓强', age: 16, gender: '女', hometown: '蓝翔技校' }            ]            // 2. 渲染页面            for (let i = 0; i < students.length; i++) {                document.write(`                <tr>                    <td>${i + 1}</td>                    <td>${students[i].name}</td>                    <td>${students[i].age}</td>                    <td>${students[i].gender}</td>                    <td>${students[i].hometown}</td>                </tr>                `)            }        </script>    </table> </body>  </html>
```

#### **10.4 内置对象**

**1.内置对象是什么？**

JavaScript 内部提供的对象，包含各种属性和方法给开发者调用。

思考：我们之前用过内置对象吗？

document.write() 、console.log()

**2.内置对象-Math**

**介绍：** Math对象是JavaScript提供的一个“数学”对象

**作用：** 提供了一系列做数学运算的方法

Math对象包含的方法有：

● random：生成0-1之间的随机数（包含0不包括1）

● ceil：向上取整

● floor：向下取整

● max：找最大数

● min：找最小数

● pow：幂运算

● abs：绝对值

生成任意范围随机数

Math.random() 随机数函数， 返回一个0 - 1之间，并且包括0不包括1的随机小数 [0, 1）

如何生成0-10的随机数呢？      Math . floor ( Math . random () * ( 10 + 1 ))

如何生成5-10的随机数？          Math . floor ( Math . random () * ( 5 + 1 )) + 5

如何生成N-M之间的随机数？   Math . floor ( Math . random () * ( M - N + 1 )) + N

案例： 猜数字游戏（限定次数）

```javascript
  <script>    // 1. 随机生成一个数字 1~10    // 取到 N ~ M 的随机整数    function getRandom(N, M) {      return Math.floor(Math.random() * (M - N + 1)) + N    }    let random = getRandom(1, 10)    // 2. 设定三次  三次没猜对就直接退出    let flag = true  // 开关变量     for (let i = 1; i <= 3; i++) {      let num = +prompt('请输入1~10之间的一个数字:')      if (num > random) {        alert('您猜大了，继续')      } else if (num < random) {        alert('您猜小了，继续')      } else {        flag = false        alert('猜对了，真厉害')        break      }    }    // 写到for的外面来    if (flag) {      alert('次数已经用完')    }  </script>
```

案例：生成随机颜色

如果参数传递的是true或者无参数，则输出 一个随机十六进制的颜色

如果参数传递的是false，则输出 一个随机rgb的颜色

```javascript
  <script>    // 1. 自定义一个随机颜色函数    function getRandomColor(flag = true) {      if (flag) {        // 3. 如果是true 则返回 #ffffff        let str = '#'        let arr = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f']        // 利用for循环随机抽6次 累加到 str里面        for (let i = 1; i <= 6; i++) {          // 每次要随机从数组里面抽取一个            // random 是数组的索引号 是随机的          let random = Math.floor(Math.random() * arr.length)          str += arr[random]        }        return str       } else {        // 4. 否则是 false 则返回 rgb(255,255,255)        let r = Math.floor(Math.random() * 256)  // 255        let g = Math.floor(Math.random() * 256)  // 255        let b = Math.floor(Math.random() * 256)  // 255        return `rgb(${r},${g},${b})`      }     }    // 2. 调用函数 getRandomColor(布尔值)    console.log(getRandomColor(false))    console.log(getRandomColor(true))    console.log(getRandomColor())   </script>
```

### 综合案例：学成在线页面渲染案例

```html
<!DOCTYPE html><html lang="en"> <head>    <meta charset="UTF-8">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <meta http-equiv="X-UA-Compatible" content="ie=edge">    <title>学车在线首页</title>    <link rel="stylesheet" href="./css/style.css">    <style>     </style></head> <body>     <!-- 4. box核心内容区域开始 -->    <div class="box w">        <div class="box-hd">            <h3>精品推荐</h3>            <a href="#">查看全部</a>        </div>        <div class="box-bd">            <ul class="clearfix">                <!-- <li>                    <a href="#">                        <img src="images/course01.png" alt="">                        <h4>                            Think PHP 5.0 博客系统实战项目演练                        </h4>                        <div class="info">                            <span>高级</span> • <span>1125</span>人在学习                        </div>                    </a>                </li> -->                <script>                    let data = [                        {                            src: 'images/course01.png',                            title: 'Think PHP 5.0 博客系统实战项目演练',                            num: 1125                        },                        {                            src: 'images/course02.png',                            title: 'Android 网络动态图片加载实战',                            num: 357                        },                        {                            src: 'images/course03.png',                            title: 'Angular2大前端商城实战项目演练',                            num: 22250                        },                        {                            src: 'images/course04.png',                            title: 'AndroidAPP实战项目演练',                            num: 389                        },                        {                            src: 'images/course05.png',                            title: 'UGUI源码深度分析案例',                            num: 124                        },                        {                            src: 'images/course06.png',                            title: 'Kami2首页界面切换效果实战演练',                            num: 432                        },                        {                            src: 'images/course07.png',                            title: 'UNITY 从入门到精通实战案例',                            num: 888                        },                        {                            src: 'images/course08.png',                            title: 'Cocos 深度学习你不会错过的实战',                            num: 590                        },                        {                            src: 'images/course04.png',                            title: '自动添加的模块',                            num: 1000                        }                    ]                     for (let i = 0; i < data.length; i++) {                        document.write(`                        <li>                            <a href="#">                                <img src=${data[i].src} title="${data[i].title}">                                <h4>                                   ${data[i].title}                                </h4>                                <div class="info">                                    <span>高级</span> • <span>${data[i].num}</span>人在学习                                </div>                            </a>                        </li>                      `)                    }                </script>            </ul>        </div>    </div> </body> </html>
```

附：style.css

```css
* {    margin: 0;    padding: 0;}.w {    width: 1200px;    margin: auto;}body {    background-color: #f3f5f7;}li {    list-style: none;}a {    text-decoration: none;}.clearfix:before,.clearfix:after {    content:"";    display:table;   }  .clearfix:after {    clear:both;  }  .clearfix {     *zoom:1;  }     .box {    margin-top: 30px;}.box-hd {    height: 45px;}.box-hd h3 {    float: left;    font-size: 20px;    color: #494949;}.box-hd a {    float: right;    font-size: 12px;    color: #a5a5a5;    margin-top: 10px;    margin-right: 30px;}/* 把li 的父亲ul 修改的足够宽一行能装开5个盒子就不会换行了 */.box-bd ul {    width: 1225px;}.box-bd ul li {    position: relative;    top: 0;    float: left;    width: 228px;    height: 270px;    background-color: #fff;    margin-right: 15px;    margin-bottom: 15px;    transition: all .3s;   }.box-bd ul li a {    display: block;}.box-bd ul li:hover {    top: -8px;    box-shadow: 0 15px 30px rgb(0 0 0 / 10%);}.box-bd ul li img {    width: 100%;}.box-bd ul li h4 {    margin: 20px 20px 20px 25px;    font-size: 14px;    color: #050505;    font-weight: 400;}.box-bd .info {    margin: 0 20px 0 25px;    font-size: 12px;    color: #999;}.box-bd .info span {    color: #ff7c2d;}
```

#### 拓展-术语解释

![](https://i-blog.csdnimg.cn/blog_migrate/522fe8e7bf52583466265db1ce4247bd.png)

#### 拓展- 基本数据类型和引用数据类型 

简单类型又叫做基本数据类型或者 值类型 ，复杂类型又叫做 引用类型 。

● 值类型：简单数据类型/基本数据类型，在存储时变量中存储的是 值本身 ，因此叫做值类型

string ，number，boolean，undefined，null

● 引用类型：复杂数据类型，在存储时变量中存储的仅仅是 地址（引用） ，因此叫做引用数据类型

通过 new 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等

简单数据类型存放到栈里面，引用数据类型存放到堆里面。

![](https://i-blog.csdnimg.cn/blog_migrate/b79bedcbe3ec5ea863047586abe72d24.jpeg)

简单数据类型传参，是把 值复制给形参，在方法内部对形参做任何改变， 不影响外部变量。

复杂数据类型传参，把变量在栈空间里保存的堆地址复制给了形参，形参和实参保存同一个堆地址， 操作的是同一个对象。

#### 拓展- 变量声明

变量声明： 有了变量先给const，如果发现它后面是要被修改的，再改为let

const 声明的值不能更改，而且const声明变量的时候需要里面进行初始化。 但是 对于引用数据类型 ， const声明的变量，里面存的不是值，是**地址** 。

建议数组和对象使用 const 来声明。

![](https://i-blog.csdnimg.cn/blog_migrate/ddb3e678ffaf2ad09b49fdd2e3d6c0d7.png)

 ![](https://i-blog.csdnimg.cn/blog_migrate/d5e860531fe0e7a5b3a15272cb922312.png)

## 二、Web APIs

### 1. Web API 基本认知

#### 1.1 作用和分类

Web API是浏览器提供的一套操作浏览器功能和页面元素的API(BOM和DOM)。

作用: 就是使用 JS 去操作 html 和浏览器

分类： DOM (文档对象模型)、 BOM （浏览器对象模型）

![](https://i-blog.csdnimg.cn/blog_migrate/83631849da8d0c2a1cf073a40c24c5dc.png)

#### 1.2 什么是DOM

DOM（Document Object Model—— 文档对象模型 ）是用来呈现以及与任意 HTML 或 XML文档交互的API。即DOM是浏览器提供的一套专门用来 **操作网页内容** 的功能。

**DOM作用：** 开发网页内容特效和实现用户交互

#### 1.3 DOM树

将 HTML 文档以树状结构直观的表现出来，称之为文档树或 DOM 树。

**作用：** 文档树直观的体现了标签与标签之间的关系

![](https://i-blog.csdnimg.cn/blog_migrate/65a640bcb606781d03c9723b353cb4ac.png)

文档：一个页面就是一个文档，DOM中使用document表示

元素：页面中的所有标签都是元素，DOM中使用element表示

节点：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM中使用node表示

 DOM 把以上内容都看做是对象 

#### 1.4 DOM对象（重要）

**● DOM 对象：** 浏览器根据 html 标签生成的 JS对象

所有的标签属性都可以在这个对象上面找到，修改这个对象的属性会自动映射到标签身上。

● **DOM 的核心思想：** 把网页内容当做 对象 来处理

● **document 对象：** 是 DOM 提供的一个 **对象，** 网页所有内容都在document里面。

document 提供的属性和方法都是 **用来访问和操作网页内** **容的。** 例：document.write() 

### 2.获取DOM对象

**查找元素DOM元素就是利用 JS 选择页面中标签元素**

#### 2.1 根据CSS选择器来获取DOM元素 (重点)

**1. 选择匹配的第一个元素**

**语法：**

```javascript
document.querySelector('css选择器')
```

**参数:** 包含一个或多个有效的CSS选择器 **字符串**  选择器需要加符号，如类名 .box，id名 #nav

**返回值：** 返回CSS选择器匹配的 第一个元素 （HTMLElement对象），如果没有匹配则返回 null。

获取的元素可直接修改。

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>

  <div class="box">123</div>
  <div class="box">abc</div>
  <ul class="nav">
    <li>测试1</li>
    <li>测试2</li>
    <li>测试3</li>
  </ul>

  <script>
    // 获取匹配的第一个元素
    const box = document.querySelector('.box');
    // 123
    console.log(box);

    // 获取 ul 第一个小 li
    const li = document.querySelector('ul li:first-child');
    console.log(li);
  </script>

</body>
</html>
```

**2. 选择匹配的多个元素**

**语法：**

```javascript
document.querySelectorAll('css选择器')
```

**参数:**  包含一个或多个有效的CSS选择器 **字符串**

**返回值：** CSS选择器匹配的  NodeList 对象集合

获取的对象集合不可以直接修改， 只能通过遍历的方式依次给里面的元素做修改。

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>
<body>

  <ul class="nav">
    <li>测试1</li>
    <li>测试2</li>
    <li>测试3</li>
  </ul>

  <script>
    // 获取所有类名为 'nav' 的 ul 元素下的 li 元素
    const lis = document.querySelectorAll('.nav li');
    // 打印 NodeList
    console.log(lis);
  </script>

</body>
</html>
```

querySelectAll() 得到的是一个 **伪数组** ： 有长度有索引号，但是没有 pop() push() 等数组方法 。

想要得到里面的每一个对象，则需要遍历（for）的方式获得。

```javascript
    const lis = document.querySelectorAll('.nav li')    for (let i = 0; i < lis.length; i++) {      console.log(lis[i]) // 每一个小li对象    }
```

**注意事项：**

哪怕只有一个元素，通过querySelectAll() 获取过来的也是一个 **伪数组** ，里面只有一个元素而已。

若要修改可通过 变量名[0] 进行修改。

```javascript
<body>  <p id="nav">导航栏</p>  <script>    const p = document.querySelectorAll('#nav')    p[0].style.color = 'red'  </script></body>
```

**querySelector() 和 querySelectorAll() 的区别：**

**●**  querySelector()只能选择一个元素， 可以直接操作。

**●**  querySelectorAll() 可以选择多个元素，得到的是伪数组，需要遍历得到每一个元素。

#### **2.2 其他获取DOM元素方法（了解）**

![](https://i-blog.csdnimg.cn/blog_migrate/21c503f84b7ec62d2e781f02af32e7cc.png)

**获取特殊元素**

1. 获取body元素：doucumnet.body // 返回body元素对象

2. 获取html元素：document.documentElement // 返回html元素对象

### 3. 操作元素内容 

DOM对象都是根据标签生成的，所以操作标签本质上就是操作DOM对象。

如果想要修改标签元素的里面的 **内容** ，则可以使用两种方式：

**1. 元素innerText 属性**

将文本内容添加/更新到任意标签位置。 显示纯文本， 不解析标签 。

```html
<body>  <div class="box">我是文字的内容</div>  <script>    // 1. 获取元素    const box = document.querySelector('.box')    // 2. 修改文字内容  对象.innerText 属性    box.innerText = '我是一个盒子'  // 修改文字内容    // box.innerText = '<strong>我是一个盒子</strong>'  // 不解析标签  </script></body>
```

**2. 元素.innerHTML 属性**

将文本内容添加/更新到任意标签位置。 会解析标签 ，多标签建议使用模板字符。

```html
<body>  <div class="box">我是文字的内容</div>  <script>    // 获取元素    const box = document.querySelector('.box')    // innerHTML 解析标签    // box.innerHTML = '我要更换'    box.innerHTML = '<strong>我要更换</strong>'  </script></body>
```

如果还在纠结到底用谁，可以选择innerHTML

案例： 年会抽奖

```html
<!DOCTYPE html><html lang="en"> <head>  <meta charset="UTF-8" />  <meta http-equiv="X-UA-Compatible" content="IE=edge" />  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  <title>年会抽奖</title>  <style>    .wrapper {      width: 840px;      height: 420px;      background: url(./images/bg01.jpg) no-repeat center / cover;      padding: 100px 250px;      box-sizing: border-box;    }  </style></head> <body>  <div class="wrapper">    <strong>传智教育年会抽奖</strong>    <h1>一等奖：<span id="one">???</span></h1>    <h3>二等奖：<span id="two">???</span></h3>    <h5>三等奖：<span id="three">???</span></h5>  </div>  <script>    // 1.声明数组    const personArr = ['周杰伦', '刘德华', '周星驰', 'Pink老师', '张学友']    // 2. 先做一等奖    // 2.1 随机数 数组的下标    const random = Math.floor(Math.random() * personArr.length)    // console.log(personArr[random])    // 2.2 获取one 元素     const one = document.querySelector('#one')    // 2.3 把名字给 one    one.innerHTML = personArr[random]    // 2.4 删除数组这个名字    personArr.splice(random, 1)    // console.log(personArr)      // 3. 二等奖    // 2.1 随机数 数组的下标    const random2 = Math.floor(Math.random() * personArr.length)    // console.log(personArr[random])    // 2.2 获取one 元素     const two = document.querySelector('#two')    // 2.3 把名字给 one    two.innerHTML = personArr[random2]    // 2.4 删除数组这个名字    personArr.splice(random2, 1)     // 4. 三等奖    // 2.1 随机数 数组的下标    const random3 = Math.floor(Math.random() * personArr.length)    // console.log(personArr[random])    // 2.2 获取one 元素     const three = document.querySelector('#three')    // 2.3 把名字给 one    three.innerHTML = personArr[random3]    // 2.4 删除数组这个名字    personArr.splice(random3, 1)  </script></body> </html>
```

### 4.操作元素属性

#### 4.1 操作元素常用属性

还可以通过 JS 设置/修改标签元素属性，比如通过 src更换 图片

最常见的属性比如： href、title、src 等

**语法：** **对象.属性 = 值**

```html
<body>  <img src="./images/1.webp" alt="">  <script>    // 1. 获取图片元素    const img = document.querySelector('img')    // 2. 修改图片对象的属性   对象.属性 = 值    img.src = './images/2.webp'    img.title = 'pink老师的艺术照'  </script></body>
```

#### 4.2 操作元素**样式**属性

还可以通过 JS 设置/修改标签元素的样式属性。

比如通过 轮播图小圆点自动更换颜色样式；点击按钮可以滚动图片，移动的图片的位置 left 等等

**1.通过 style 属性操作CSS**

**语法：** **对象.style.样式属性 = 值**

![](https://i-blog.csdnimg.cn/blog_migrate/cc0bfb3b834d6dd875e22b8c2f36d329.png)

**注意：**

1. 修改样式通过 style 属性引出

2. 如果属性有 - 连接符，需要转换为 小驼峰 命名法

3. 赋值的时候，需要的时候不要忘记加 css单位

4.JS修改style样式操作，产生的是行内样式，CSS权重比较高

**2. 操作类名(className) 操作CSS**

如果修改的样式比较多，直接通过style属性修改比较繁琐，我们可以通过借助于css类名的形式。可以同时修改多个样式。

**语法：** **元素.className = 'css类名'**

**注意：**

1. 由于 class 是关键字, 所以使用  className  去代替

2. className 是使用新值 换 旧值, 如果需要添加一个类，需要保留之前的类名， 直接使用 className 赋值会覆盖以前的类名。

**3.** **通过 classList 操作类控制CSS**

为了解决className 容易覆盖以前的类名，我们可以通过classList方式追加和删除类名。

**语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/94e948feed3f42a9227c99d9884b6bc6.png)

```html
<!DOCTYPE html><html lang="en"> <head>  <meta charset="UTF-8">  <meta http-equiv="X-UA-Compatible" content="IE=edge">  <meta name="viewport" content="width=device-width, initial-scale=1.0">  <title>Document</title>  <style>    .box {      width: 200px;      height: 200px;      color: #333;    }     .active {      color: red;      background-color: pink;    }  </style></head> <body>  <div class="box active">文字</div>  <script>    // 通过classList添加    // 1. 获取元素    const box = document.querySelector('.box')    // 2. 修改样式    // 2.1 追加类 add() 类名不加点，并且是字符串    // box.classList.add('active')    // 2.2 删除类  remove() 类名不加点，并且是字符串    // box.classList.remove('box')    // 2.3 切换类  toggle()  有还是没有啊， 有就删掉，没有就加上    box.classList.toggle('active')  </script></body> </html>
```

#### **案例：轮播图随机版**

```html
<!DOCTYPE html><html lang="en"> <head>  <meta charset="UTF-8" />  <meta http-equiv="X-UA-Compatible" content="IE=edge" />  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  <title>轮播图点击切换</title>  <style>    * {      box-sizing: border-box;    }     .slider {      width: 560px;      height: 400px;      overflow: hidden;    }     .slider-wrapper {      width: 100%;      height: 320px;    }     .slider-wrapper img {      width: 100%;      height: 100%;      display: block;    }     .slider-footer {      height: 80px;      background-color: rgb(100, 67, 68);      padding: 12px 12px 0 12px;      position: relative;    }     .slider-footer .toggle {      position: absolute;      right: 0;      top: 12px;      display: flex;    }     .slider-footer .toggle button {      margin-right: 12px;      width: 28px;      height: 28px;      appearance: none;      border: none;      background: rgba(255, 255, 255, 0.1);      color: #fff;      border-radius: 4px;      cursor: pointer;    }     .slider-footer .toggle button:hover {      background: rgba(255, 255, 255, 0.2);    }     .slider-footer p {      margin: 0;      color: #fff;      font-size: 18px;      margin-bottom: 10px;    }     .slider-indicator {      margin: 0;      padding: 0;      list-style: none;      display: flex;      align-items: center;    }     .slider-indicator li {      width: 8px;      height: 8px;      margin: 4px;      border-radius: 50%;      background: #fff;      opacity: 0.4;      cursor: pointer;    }     .slider-indicator li.active {      width: 12px;      height: 12px;      opacity: 1;    }  </style></head> <body>  <div class="slider">    <div class="slider-wrapper">      <img src="./images/slider01.jpg" alt="" />    </div>    <div class="slider-footer">      <p>对人类来说会不会太超前了？</p>      <ul class="slider-indicator">        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>      </ul>      <div class="toggle">        <button class="prev">&lt;</button>        <button class="next">&gt;</button>      </div>    </div>  </div>  <script>    // 1. 初始数据    const sliderData = [      { url: './images/slider01.jpg', title: '对人类来说会不会太超前了？', color: 'rgb(100, 67, 68)' },      { url: './images/slider02.jpg', title: '开启剑与雪的黑暗传说！', color: 'rgb(43, 35, 26)' },      { url: './images/slider03.jpg', title: '真正的jo厨出现了！', color: 'rgb(36, 31, 33)' },      { url: './images/slider04.jpg', title: '李玉刚：让世界通过B站看到东方大国文化', color: 'rgb(139, 98, 66)' },      { url: './images/slider05.jpg', title: '快来分享你的寒假日常吧~', color: 'rgb(67, 90, 92)' },      { url: './images/slider06.jpg', title: '哔哩哔哩小年YEAH', color: 'rgb(166, 131, 143)' },      { url: './images/slider07.jpg', title: '一站式解决你的电脑配置问题！！！', color: 'rgb(53, 29, 25)' },      { url: './images/slider08.jpg', title: '谁不想和小猫咪贴贴呢！', color: 'rgb(99, 72, 114)' },    ]     // 1. 需要一个随机数     const random = parseInt(Math.random() * sliderData.length)    // console.log(sliderData[random])    // 2. 把对应的数据渲染到标签里面    // 2.1 获取图片    const img = document.querySelector('.slider-wrapper img')    // 2.2. 修改图片路径  =  对象.url    img.src = sliderData[random].url    // 3. 把p里面的文字内容更换    // 3.1 获取p    const p = document.querySelector('.slider-footer p')    // 3.2修改p    p.innerHTML = sliderData[random].title    // 4. 修改背景颜色    const footer = document.querySelector('.slider-footer')    footer.style.backgroundColor = sliderData[random].color    // 5. 小圆点    const li = document.querySelector(`.slider-indicator li:nth-child(${random + 1})`)    // 让当前这个小li 添加 active这个类    li.classList.add('active')  </script></body> </html>
```

#### 4.3 操作表单元素属性

表单很多情况也需要修改属性，比如点击眼睛，可以看到密码，本质是把表单类型转换为文本框。

**获取:** DOM对象.属性名

**设置:** DOM对象.属性名 = 新值

表单属性中添加就有效果，移除就没有效果，一律使用布尔值表示。如果为true代表添加了该属性， 如果是false 代表移除了该属性。比如： disabled、checked、selected

```html
<body>  <button>点击</button>  <script>    // 1.获取    const button = document.querySelector('button')    // console.log(button.disabled)  // 默认false 不禁用    button.disabled = true   // 禁用按钮  </script></body>
```

#### 4.4 自定义属性

**标准属性:** 标签天生自带的属性，比如class、id、title等, 可以直接使用点语法操作。比如： disabled、checked、 selected

**自定义属性：** 在html5中推出来了专门的data-自定义属性，在标签上一律 以data-开头 ，在DOM对象上一律以 dataset对象 方式获取。

![](https://i-blog.csdnimg.cn/blog_migrate/23a51c40b92eaa667392be4b2ac8c6ff.png)

### 5.定时器-间歇函数

网页中经常会需要一种功能：每隔一段时间需要自动执行一段代码，不需要我们手动去触发。

例如：网页中的倒计时。要实现这种需求，需要定时器函数。

定时器函数可以开启和关闭定时器，可以根据时间自动重复执行某些代码。

**1. 开启定时器**

```javascript
setInterval(函数, 间隔时间)
```

**作用：**每隔一段时间调用这个函数

**注意：**

1. 函数名字 **不需要加括号**

**2. 定时器返回的是一个id数字**

3. 间隔时间单位是毫秒（1s = 1000ms）

```javascript
  <script>    // setInterval(函数, 间隔时间)    // 1.直接写匿名函数    // setInterval(function () {    //   console.log('一秒执行一次')    // }, 1000)    // 2.调用函数，只写函数名，不要加小括号    function fn() {      console.log('一秒执行一次')    }    let n = setInterval(fn, 1000)    // setInterval('fn()', 1000)  </script>
```

**2. 关闭定时器**

```javascript
let 变量名 = setInterval(函数, 间隔时间)clearInterval(变量名)
```

一般不会刚创建就停止，而是满足一定条件再停止。

案例： 阅读注册协议

```javascript
<body>    <textarea name="" id="" cols="30" rows="10">        用户注册协议        欢迎注册成为京东用户！在您注册过程中，您需要完成我们的注册流程并通过点击同意的形式在线签署以下协议，请您务必仔细阅读、充分理解协议中的条款内容后再点击同意（尤其是以粗体或下划线标识的条款，因为这些条款可能会明确您应履行的义务或对您的权利有所限制）。        【请您注意】如果您不同意以下协议全部或任何条款约定，请您停止注册。您停止注册后将仅可以浏览我们的商品信息但无法享受我们的产品或服务。如您按照注册流程提示填写信息，阅读并点击同意上述协议且完成全部注册流程后，即表示您已充分阅读、理解并接受协议的全部内容，并表明您同意我们可以依据协议内容来处理您的个人信息，并同意我们将您的订单信息共享给为完成此订单所必须的第三方合作方（详情查看    </textarea>    <br>    <button class="btn" disabled>我已经阅读用户协议(5)</button>    <script>        // 1. 获取元素        const btn = document.querySelector('.btn')        // console.log(btn.innerHTML)  butto按钮特殊用innerHTML        // 2. 倒计时        let i = 5        // 2.1 开启定时器        let n = setInterval(function () {            i--            btn.innerHTML = `我已经阅读用户协议(${i})`            if (i === 0) {                clearInterval(n)  // 关闭定时器                // 定时器停了，我就可以开按钮                btn.disabled = false                btn.innerHTML = '同意'            }        }, 1000)    </script></body>
```

### 综合案例：轮播图定时器版

```html
<!DOCTYPE html><html lang="en"> <head>  <meta charset="UTF-8" />  <meta http-equiv="X-UA-Compatible" content="IE=edge" />  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  <title>轮播图点击切换</title>  <style>    * {      box-sizing: border-box;    }     .slider {      width: 560px;      height: 400px;      overflow: hidden;    }     .slider-wrapper {      width: 100%;      height: 320px;    }     .slider-wrapper img {      width: 100%;      height: 100%;      display: block;    }     .slider-footer {      height: 80px;      background-color: rgb(100, 67, 68);      padding: 12px 12px 0 12px;      position: relative;    }     .slider-footer .toggle {      position: absolute;      right: 0;      top: 12px;      display: flex;    }     .slider-footer .toggle button {      margin-right: 12px;      width: 28px;      height: 28px;      appearance: none;      border: none;      background: rgba(255, 255, 255, 0.1);      color: #fff;      border-radius: 4px;      cursor: pointer;    }     .slider-footer .toggle button:hover {      background: rgba(255, 255, 255, 0.2);    }     .slider-footer p {      margin: 0;      color: #fff;      font-size: 18px;      margin-bottom: 10px;    }     .slider-indicator {      margin: 0;      padding: 0;      list-style: none;      display: flex;      align-items: center;    }     .slider-indicator li {      width: 8px;      height: 8px;      margin: 4px;      border-radius: 50%;      background: #fff;      opacity: 0.4;      cursor: pointer;    }     .slider-indicator li.active {      width: 12px;      height: 12px;      opacity: 1;    }  </style></head> <body>  <div class="slider">    <div class="slider-wrapper">      <img src="./images/slider01.jpg" alt="" />    </div>    <div class="slider-footer">      <p>对人类来说会不会太超前了？</p>      <ul class="slider-indicator">        <li class="active"></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>      </ul>      <div class="toggle">        <button class="prev">&lt;</button>        <button class="next">&gt;</button>      </div>    </div>  </div>  <script>    // 1. 初始数据    const sliderData = [      { url: './images/slider01.jpg', title: '对人类来说会不会太超前了？', color: 'rgb(100, 67, 68)' },      { url: './images/slider02.jpg', title: '开启剑与雪的黑暗传说！', color: 'rgb(43, 35, 26)' },      { url: './images/slider03.jpg', title: '真正的jo厨出现了！', color: 'rgb(36, 31, 33)' },      { url: './images/slider04.jpg', title: '李玉刚：让世界通过B站看到东方大国文化', color: 'rgb(139, 98, 66)' },      { url: './images/slider05.jpg', title: '快来分享你的寒假日常吧~', color: 'rgb(67, 90, 92)' },      { url: './images/slider06.jpg', title: '哔哩哔哩小年YEAH', color: 'rgb(166, 131, 143)' },      { url: './images/slider07.jpg', title: '一站式解决你的电脑配置问题！！！', color: 'rgb(53, 29, 25)' },      { url: './images/slider08.jpg', title: '谁不想和小猫咪贴贴呢！', color: 'rgb(99, 72, 114)' },    ]    // 1. 获取元素     const img = document.querySelector('.slider-wrapper img')    const p = document.querySelector('.slider-footer p')    let i = 0  // 信号量 控制图片的张数    // 2. 开启定时器    setInterval(function () {      i++      // 无缝衔接位置  一共八张图片，到了最后一张就是 8， 数组的长度就是 8      if (i >= sliderData.length) {        i = 0      }      // 更换图片路径        img.src = sliderData[i].url      // 把字写到 p里面      p.innerHTML = sliderData[i].title      // 小圆点      // 先删除以前的active      document.querySelector('.slider-indicator .active').classList.remove('active')      // 只让当前li添加active      document.querySelector(`.slider-indicator li:nth-child(${i + 1})`).classList.add('active')    }, 1000)   </script></body> </html>
```

### **6.事件监听（绑定）**

#### 6.1 事件监听

**什么是事件？**

事件是在编程时系统内发生的 **动作** 或者发生的事情。比如用户在网页上 **单击** 一个按钮

**什么是事件监听？**

就是让程序检测是否有事件产生，一旦有事件触发，就立即调用一个函数做出响应，也称为 绑定事件或者注册事件， 比如鼠标经过显示下拉菜单，比如点击可以播放轮播图等等。

**语法：**

```javascript
元素对象.addEventListener('事件类型', 要执行的函数)
```

**事件监听三要素：**

**事件源：** 事件被触发的对象 。dom元素被事件触发了，要获取dom元素

**事件类型：** 用什么方式触发，比如鼠标单击 click、鼠标经过 mouseover 等

**事件调用的函数：** 要做什么事

![](https://i-blog.csdnimg.cn/blog_migrate/e043919d97281947dce6af44b75dc979.png)

**注意：**

1. 事件类型要 加引号

2. 函数是点击之后再去执行，每次点击都会执行一次

**案例：随机点名**

```html
<!DOCTYPE html><html lang="en"> <head>    <meta charset="UTF-8">    <meta name="viewport" content="width=device-width, initial-scale=1.0">    <title>Document</title>    <style>        * {            margin: 0;            padding: 0;        }         h2 {            text-align: center;        }         .box {            width: 600px;            margin: 50px auto;            display: flex;            font-size: 25px;            line-height: 40px;        }         .qs {             width: 450px;            height: 40px;            color: red;         }         .btns {            text-align: center;        }         .btns button {            width: 120px;            height: 35px;            margin: 0 50px;        }    </style></head> <body>    <h2>随机点名</h2>    <div class="box">        <span>名字是：</span>        <div class="qs">这里显示姓名</div>    </div>    <div class="btns">        <button class="start">开始</button>        <button class="end">结束</button>    </div>     <script>        // 数据数组        const arr = ['马超', '黄忠', '赵云', '关羽', '张飞']        // 定时器的全局变量        let timerId = 0        // 随机号要全局变量        let random = 0        // 业务1.开始按钮模块        const qs = document.querySelector('.qs')        // 1.1 获取开始按钮对象        const start = document.querySelector('.start')        // 1.2 添加点击事件        start.addEventListener('click', function () {            timerId = setInterval(function () {                // 随机数                random = parseInt(Math.random() * arr.length)                // console.log(arr[random])                qs.innerHTML = arr[random]            }, 35)            // 如果数组里面只有一个值了，还需要抽取吗？  不需要  让两个按钮禁用就可以            if (arr.length === 1) {                // start.disabled = true                // end.disabled = true                start.disabled = end.disabled = true            }        })         // 2. 关闭按钮模块        const end = document.querySelector('.end')        end.addEventListener('click', function () {            clearInterval(timerId)            // 结束了，可以删除掉当前抽取的那个数组元素            arr.splice(random, 1)            console.log(arr)        })    </script></body> </html>
```

#### 6.2 事件监听版本

事件源.on事件 = function() { }

事件源.addEventListener(事件， 事件处理函数)

**区别：**

on方式会被覆盖， addEventListener 方式可绑定多次，拥有事件更多特性，推荐使用

### 7.事件类型

![](https://i-blog.csdnimg.cn/blog_migrate/71bd38c96432a1c8b1499fa8b73c8d28.png)

#### 案例：轮播图完整版

```html
<!DOCTYPE html><html lang="en"> <head>  <meta charset="UTF-8" />  <meta http-equiv="X-UA-Compatible" content="IE=edge" />  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  <title>轮播图点击切换</title>  <style>    * {      box-sizing: border-box;    }     .slider {      width: 560px;      height: 400px;      overflow: hidden;    }     .slider-wrapper {      width: 100%;      height: 320px;    }     .slider-wrapper img {      width: 100%;      height: 100%;      display: block;    }     .slider-footer {      height: 80px;      background-color: rgb(100, 67, 68);      padding: 12px 12px 0 12px;      position: relative;    }     .slider-footer .toggle {      position: absolute;      right: 0;      top: 12px;      display: flex;    }     .slider-footer .toggle button {      margin-right: 12px;      width: 28px;      height: 28px;      appearance: none;      border: none;      background: rgba(255, 255, 255, 0.1);      color: #fff;      border-radius: 4px;      cursor: pointer;    }     .slider-footer .toggle button:hover {      background: rgba(255, 255, 255, 0.2);    }     .slider-footer p {      margin: 0;      color: #fff;      font-size: 18px;      margin-bottom: 10px;    }     .slider-indicator {      margin: 0;      padding: 0;      list-style: none;      display: flex;      align-items: center;    }     .slider-indicator li {      width: 8px;      height: 8px;      margin: 4px;      border-radius: 50%;      background: #fff;      opacity: 0.4;      cursor: pointer;    }     .slider-indicator li.active {      width: 12px;      height: 12px;      opacity: 1;    }  </style></head> <body>  <div class="slider">    <div class="slider-wrapper">      <img src="./images/slider01.jpg" alt="" />    </div>    <div class="slider-footer">      <p>对人类来说会不会太超前了？</p>      <ul class="slider-indicator">        <li class="active"></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>        <li></li>      </ul>      <div class="toggle">        <button class="prev">&lt;</button>        <button class="next">&gt;</button>      </div>    </div>  </div>  <script>    // 1. 初始数据    const data = [      { url: './images/slider01.jpg', title: '对人类来说会不会太超前了？', color: 'rgb(100, 67, 68)' },      { url: './images/slider02.jpg', title: '开启剑与雪的黑暗传说！', color: 'rgb(43, 35, 26)' },      { url: './images/slider03.jpg', title: '真正的jo厨出现了！', color: 'rgb(36, 31, 33)' },      { url: './images/slider04.jpg', title: '李玉刚：让世界通过B站看到东方大国文化', color: 'rgb(139, 98, 66)' },      { url: './images/slider05.jpg', title: '快来分享你的寒假日常吧~', color: 'rgb(67, 90, 92)' },      { url: './images/slider06.jpg', title: '哔哩哔哩小年YEAH', color: 'rgb(166, 131, 143)' },      { url: './images/slider07.jpg', title: '一站式解决你的电脑配置问题！！！', color: 'rgb(53, 29, 25)' },      { url: './images/slider08.jpg', title: '谁不想和小猫咪贴贴呢！', color: 'rgb(99, 72, 114)' },    ]    // 获取元素    const img = document.querySelector('.slider-wrapper img')    const p = document.querySelector('.slider-footer p')    const footer = document.querySelector('.slider-footer')    // 1. 右按钮业务    // 1.1 获取右侧按钮     const next = document.querySelector('.next')    let i = 0  // 信号量 控制播放图片张数    // 1.2 注册点击事件    next.addEventListener('click', function () {      i++      i = i >= data.length ? 0 : i      // 调用函数      toggle()    })     // 2. 左侧按钮业务    // 2.1 获取左侧按钮     const prev = document.querySelector('.prev')    // 2.2 注册点击事件    prev.addEventListener('click', function () {      i--      i = i < 0 ? data.length - 1 : i      // 调用函数      toggle()    })     // 声明一个渲染的函数作为复用    function toggle() {      // 1.4 渲染对应的数据      img.src = data[i].url      p.innerHTML = data[i].title      footer.style.backgroundColor = data[i].color      // 1.5 更换小圆点    先移除原来的类名， 当前li再添加 这个 类名      document.querySelector('.slider-indicator .active').classList.remove('active')      document.querySelector(`.slider-indicator li:nth-child(${i + 1})`).classList.add('active')    }     // 3. 自动播放模块    let timerId = setInterval(function () {      // 利用js自动调用点击事件  click()  一定加小括号调用函数      next.click()    }, 1000)     // 4. 鼠标经过大盒子，停止定时器    const slider = document.querySelector('.slider')    // 注册事件    slider.addEventListener('mouseenter', function () {      // 停止定时器      clearInterval(timerId)    })     // 5. 鼠标离开大盒子，开启定时器    // 注册事件    slider.addEventListener('mouseleave', function () {      // 停止定时器      if (timerId) clearInterval(timerId)      // 开启定时器      timerId = setInterval(function () {        // 利用js自动调用点击事件  click()  一定加小括号调用函数        next.click()      }, 1000)    })  </script></body> </html>
```

### 8.事件对象

#### 8.1 获取事件对象

**事件对象是什么？**

事件对象也是个对象，这个对象里有事件触发时的相关信息 。例如：鼠标点击事件中，事件对象就存了鼠标点在哪个位置等信息。

**使用场景：**

可以判断用户按下哪个键，比如按下回车键可以发布新闻

可以判断鼠标点击了哪个元素，从而做相应的操作

**语法：**

![](https://i-blog.csdnimg.cn/blog_migrate/d11b822b225cc12676adc0cf750e6f16.png)

在事件绑定的回调函数的第一个参数就是事件对象 ，一般命名为event、ev、e

#### 8.2 事件对象常用属性

**部分常用属性：**

type：获取当前的事件类型

clientX/clientY：获取光标相对于浏览器可见窗口左上角的位置

offsetX/offsetY：获取光标相对于当前DOM元素左上角的位置

key：用户按下的键盘键的值，现在不提倡使用keyCode

拓展：字符串.trim()  可去除字符串左右的空格

案例： 评论回车发布

```html
<!DOCTYPE html><html lang="en"> <head>  <meta charset="UTF-8">  <meta http-equiv="X-UA-Compatible" content="IE=edge">  <meta name="viewport" content="width=device-width, initial-scale=1.0">  <title>评论回车发布</title>  <style>    .wrapper {      min-width: 400px;      max-width: 800px;      display: flex;      justify-content: flex-end;    }     .avatar {      width: 48px;      height: 48px;      border-radius: 50%;      overflow: hidden;      background: url(./images/avatar.jpg) no-repeat center / cover;      margin-right: 20px;    }     .wrapper textarea {      outline: none;      border-color: transparent;      resize: none;      background: #f5f5f5;      border-radius: 4px;      flex: 1;      padding: 10px;      transition: all 0.5s;      height: 30px;    }     .wrapper textarea:focus {      border-color: #e4e4e4;      background: #fff;      height: 50px;    }     .wrapper button {      background: #00aeec;      color: #fff;      border: none;      border-radius: 4px;      margin-left: 10px;      width: 70px;      cursor: pointer;    }     .wrapper .total {      margin-right: 80px;      color: #999;      margin-top: 5px;      opacity: 0;      transition: all 0.5s;    }     .list {      min-width: 400px;      max-width: 800px;      display: flex;    }     .list .item {      width: 100%;      display: flex;    }     .list .item .info {      flex: 1;      border-bottom: 1px dashed #e4e4e4;      padding-bottom: 10px;    }     .list .item p {      margin: 0;    }     .list .item .name {      color: #FB7299;      font-size: 14px;      font-weight: bold;    }     .list .item .text {      color: #333;      padding: 10px 0;    }     .list .item .time {      color: #999;      font-size: 12px;    }  </style></head> <body>  <div class="wrapper">    <i class="avatar"></i>    <textarea id="tx" placeholder="发一条友善的评论" rows="2" maxlength="200"></textarea>    <button>发布</button>  </div>  <div class="wrapper">    <span class="total">0/200字</span>  </div>  <div class="list">    <div class="item" style="display: none;">      <i class="avatar"></i>      <div class="info">        <p class="name">zhuie</p>        <p class="text">大家都辛苦啦，感谢各位大大的努力，能圆满完成真是太好了[笑哭][支持]</p>        <p class="time">2023-05-17 20:33:21</p>      </div>    </div>  </div>  <script>    const tx = document.querySelector('#tx')    const total = document.querySelector('.total')    const item = document.querySelector('.item')    const text = document.querySelector('.text')    // 1. 当我们文本域获得了焦点，就让 total 显示出来    tx.addEventListener('focus', function () {      total.style.opacity = 1    })    // 2. 当我们文本域失去了焦点，就让 total 隐藏出来    tx.addEventListener('blur', function () {      total.style.opacity = 0    })    // 3. 检测用户输入    tx.addEventListener('input', function () {      // console.log(tx.value.length)  得到输入的长度      total.innerHTML = `${tx.value.length}/200字`    })     // 4. 按下回车发布评论    tx.addEventListener('keyup', function (e) {      // 只有按下的是回车键，才会触发      if (e.key === 'Enter') {        // 如果用户输入的不为空就显示和打印        if (tx.value.trim()) {          item.style.display = 'block'          // console.log(tx.value)  // 用户输入的内容          text.innerHTML = tx.value        }        // 等我们按下回车，结束，清空文本域        tx.value = ''        // 按下回车之后，就要把 字符统计 复原        total.innerHTML = '0/200字'      }     })  </script></body> </html>
```

### 9.环境对象

**环境对象：** 指的是函数内部特殊的 **变量 this** ， 它代表着当前函数运行时所处的环境

**作用：** 弄清楚this的指向，可以让我们代码更简洁

函数的调用方式不同，this 指代的对象也不同

【谁调用， this 就是谁】 是判断 this 指向的粗略规则

直接调用函数，其实相当于是 window.函数，所以 this 指代 window

### 10.回调函数

如果将函数 A 做为参数传递给函数 B 时，我们称函数 A 为 回调函数

简单理解： 当一个函数当做参数来传递给另外一个函数的时候，这个函数就是 回调函数

常见的使用场景： ![](https://i-blog.csdnimg.cn/blog_migrate/e9443b939f9ed2c15f9486f93ecd056d.png)

![](https://i-blog.csdnimg.cn/blog_migrate/5830ebed23606e9f7f3b60e92112be14.png)

回调函数本质还是函数，只不过把它当成参数使用。使用匿名函数做为回调函数比较常见。

#### 综合案例：Tab栏切换

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>tab栏切换</title>
  <style>
    * {
      margin: 0;
      padding: 0;
    }

    .tab {
      width: 590px;
      height: 340px;
      margin: 20px;
      border: 1px solid #e4e4e4;
    }

    .tab-nav {
      width: 100%;
      height: 60px;
      line-height: 60px;
      display: flex;
      justify-content: space-between;
    }

    .tab-nav h3 {
      font-size: 24px;
      font-weight: normal;
      margin-left: 20px;
    }

    .tab-nav ul {
      list-style: none;
      display: flex;
      justify-content: flex-end;
    }

    .tab-nav ul li {
      margin: 0 20px;
      font-size: 14px;
    }

    .tab-nav ul li a {
      text-decoration: none;
      border-bottom: 2px solid transparent;
      color: #333;
    }

    .tab-nav ul li a.active {
      border-color: #e1251b;
      color: #e1251b;
    }

    .tab-content {
      padding: 0 16px;
    }

    .tab-content .item {
      display: none;
    }

    .tab-content .item.active {
      display: block;
    }
  </style>
</head>
<body>

  <div class="tab">
    <div class="tab-nav">
      <h3>每日特价</h3>
      <ul>
        <li><a class="active" href="javascript:;" data-id="0">精选</a></li>
        <li><a href="javascript:;" data-id="1">美食</a></li>
        <li><a href="javascript:;" data-id="2">百货</a></li>
        <li><a href="javascript:;" data-id="3">个护</a></li>
        <li><a href="javascript:;" data-id="4">预告</a></li>
      </ul>
    </div>
    <div class="tab-content">
      <div class="item active"><img src="./images/tab00.png" alt="" /></div>
      <div class="item"><img src="./images/tab01.png" alt="" /></div>
      <div class="item"><img src="./images/tab02.png" alt="" /></div>
      <div class="item"><img src="./images/tab03.png" alt="" /></div>
      <div class="item"><img src="./images/tab04.png" alt="" /></div>
    </div>
  </div>

  <script>
    // 1. 获取所有类名为 'tab-nav' 的元素下的 a 元素
    const as = document.querySelectorAll('.tab-nav a');

    // 循环遍历每个 a 元素
    for (let i = 0; i < as.length; i++) {
      // 为每个 a 元素添加鼠标经过事件监听器
      as[i].addEventListener('mouseenter', function () {
        // 鼠标经过时执行以下操作

        // 移除当前激活的链接的 'active' 类
        document.querySelector('.tab-nav .active').classList.remove('active');

        // 将 'active' 类添加到当前链接
        this.classList.add('active');

        // 移除当前激活的 item 的 'active' 类
        document.querySelector('.tab-content .item.active').classList.remove('active');

        // 将 'active' 类添加到与当前链接对应索引的 item 元素
        document.querySelector(`.tab-content .item:nth-child(${i + 1})`).classList.add('active');
      });
    }
  </script>

</body>
</html>
```

拓展：css伪类选择器checked（选择被勾选的复选框）

#### 重点案例：全选文本框

```html
<!DOCTYPE html> <html> <head lang="en">  <meta charset="UTF-8">  <title></title>  <style>    * {      margin: 0;      padding: 0;    }     table {      border-collapse: collapse;      border-spacing: 0;      border: 1px solid #c0c0c0;      width: 500px;      margin: 100px auto;      text-align: center;    }     th {      background-color: #09c;      font: bold 16px "微软雅黑";      color: #fff;      height: 24px;    }     td {      border: 1px solid #d0d0d0;      color: #404060;      padding: 10px;    }     .allCheck {      width: 80px;    }  </style></head> <body>  <table>    <tr>      <th class="allCheck">        <input type="checkbox" name="" id="checkAll"> <span class="all">全选</span>      </th>      <th>商品</th>      <th>商家</th>      <th>价格</th>    </tr>    <tr>      <td>        <input type="checkbox" name="check" class="ck">      </td>      <td>小米手机</td>      <td>小米</td>      <td>￥1999</td>    </tr>    <tr>      <td>        <input type="checkbox" name="check" class="ck">      </td>      <td>小米净水器</td>      <td>小米</td>      <td>￥4999</td>    </tr>    <tr>      <td>        <input type="checkbox" name="check" class="ck">      </td>      <td>小米电视</td>      <td>小米</td>      <td>￥5999</td>    </tr>  </table>  <script>    // 1. 获取大复选框    const checkAll = document.querySelector('#checkAll')    // 2. 获取所有的小复选框    const cks = document.querySelectorAll('.ck')    // 3. 点击大复选框  注册事件    checkAll.addEventListener('click', function () {      // 得到当前大复选框的选中状态      // console.log(checkAll.checked)  // 得到 是 true 或者是 false      // 4. 遍历所有的小复选框 让小复选框的checked  =  大复选框的 checked      for (let i = 0; i < cks.length; i++) {        cks[i].checked = this.checked      }    })    // 5. 小复选框控制大复选框    for (let i = 0; i < cks.length; i++) {      // 5.1 给所有的小复选框添加点击事件      cks[i].addEventListener('click', function () {        // 判断选中的小复选框个数 是不是等于  总的小复选框个数        // console.log(document.querySelectorAll('.ck:checked').length)        // console.log(document.querySelectorAll('.ck:checked').length === cks.length)        checkAll.checked = document.querySelectorAll('.ck:checked').length === cks.length      })    }  </script></body> </html>
```

### 11.事件流

#### 11.1 事件流和两个阶段说明

事件流 指的是事件完整执行过程中的流动路径。

![](https://i-blog.csdnimg.cn/blog_migrate/0d3435fe5fc89e35bfe95b7aa14692f7.png)

![](https://i-blog.csdnimg.cn/blog_migrate/461b3b2a0c852ecd2081029b2365fdf6.png)

说明：假设页面里有个div，当触发事件时，会经历两个阶段，分别是捕获阶段、冒泡阶段

简单来说：捕获阶段是从父到子，冒泡阶段是从子到父

实际工作都是使用事件冒泡为主。

#### 11.2 事件捕获

**事件捕获概念：** 从DOM的根元素开始去执行对应的事件 (从外到里)

**代码：** DOM.addEventListener(事件类型, 事件处理函数, 是否使用捕获机制)

说明：

**●** addEventListener第三个参数传入 true 代表是 捕获阶段 触发（很少使用）

**●** 若传入 false 代表 冒泡阶段 触发，默认就是false

**●** 若是用 L0 事件监听，则只有冒泡阶段，没有捕获

#### 11.3 事件冒泡

**事件冒泡概念:** 当一个元素的事件被触发时，同样的事件将会在该元素的所有祖先元素中依次被触发。这一过程被称为事件冒泡。

**简单理解：**当一个元素触发事件后，会依次向上调用所有父级元素的 同名事件 。比如click事件

事件冒泡是默认存在的。L2事件监听第三个参数是 false，或者默认都是冒泡。

#### 11.4 阻止冒泡

**问题：** 因为默认就有冒泡模式的存在，所以容易导致事件影响到父级元素

**需求：** 若想把事件就限制在当前元素内，就需要阻止事件冒泡

**前提：** 阻止事件冒泡需要拿到事件对象

**语法：** 事件对象.stopPropagation()

**注意：** 此方法可以阻断事件流动传播，不光在冒泡阶段有效，捕获阶段也有效

```html
<body>  <div class="father">    <div class="son"></div>  </div>  <script>    const fa = document.querySelector('.father')    const son = document.querySelector('.son')    document.addEventListener('click', function () {      alert('我是爷爷')    })    fa.addEventListener('click', function () {      alert('我是爸爸')    })    son.addEventListener('click', function (e) {      alert('我是儿子')      // 阻止流动传播  事件对象.stopPropagation()      e.stopPropagation()    })   </script></body>
```

**我们某些情况下需要** 阻止 **默认行为** 的发生，比如 阻止 链接的跳转，表单域跳转

**语法：** e.preventDefault()

```html
<body>  <form action="http://www.itcast.cn">    <input type="submit" value="免费注册">  </form>  <script>    const form = document.querySelector('form')    form.addEventListener('submit', function (e) {      // 阻止默认行为  提交      e.preventDefault()    })  </script></body>
```

#### 11.5 解绑事件

on事件方式，直接使用null覆盖偶就可以实现事件的解绑

**语法：**

```html
<body>  <button>点击</button>  <script>    const btn = document.querySelector('button')    btn.onclick = function () {      alert('点击了')      // L0 事件移除解绑      btn.onclick = null    }  </script></body>
```

addEventListener方式必须使用：

removeEventListener(事件类型, 事件处理函数, [获取捕获或者冒泡阶段])

```html
<body>  <button>点击</button>  <script>    const btn = document.querySelector('button')    function fn() {      alert('点击了')    }    btn.addEventListener('click', fn)    // L2 事件移除解绑    btn.removeEventListener('click', fn)  </script></body>
```

**注意：匿名函数无法被解绑**

#### 拓展：鼠标经过事件的区别、**两种注册事件的区别**

**鼠标经过事件：**

**●** mouseover 和 mouseout 会有冒泡效果

**●** mouseenter 和 mouseleave 没有冒泡效果 (推荐)

**两种注册事件：**

**●** 传统on注册（L0）

同一个对象,后面注册的事件会覆盖前面注册(同一个事件)

直接使用null覆盖偶就可以实现事件的解绑

都是冒泡阶段执行的

**●** 事件监听注册（L2）

语法: addEventListener(事件类型, 事件处理函数, 是否使用捕获)

后面注册的事件不会覆盖前面注册的事件(同一个事件)

可以通过第三个参数去确定是在冒泡或者捕获阶段执行

必须使用removeEventListener(事件类型, 事件处理函数, 获取捕获或者冒泡阶段)

匿名函数无法被解绑

### 12.事件委托

事件委托是利用事件流的特征解决一些开发需求的知识技巧。

**优点：**减少注册次数，可以提高程序性能。

**原理：**事件委托其实是利用 事件冒泡 的特点。 给 父元素注册事件 ，当我们触发子元素的时候，会冒泡到父元素身上，从而触发父元素的事件。

**实现：** 事件对象.target. tagName 可以获得真正触发事件的元素 u

如：ul.addEventListener('click' , function(){}) 执行父级点击事件

#### 案例：tab栏切换改造

**思路：**

①：给 a的父级 注册点击事件，采取事件委托方式

②：如果点击的是A , 则进行排他思想，删除添加类，注意判断的方式 利用 e.target.tagName

③：因为没有索引号了，所以这里我们可以自定义属性data-id，给5个链接添加序号

④：下面大盒子获取索引号的方式 e.target.dataset.id 号， 然后进行排他思想

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>tab栏切换</title>
  <style>
    * {
      margin: 0;
      padding: 0;
    }

    .tab {
      width: 590px;
      height: 340px;
      margin: 20px;
      border: 1px solid #e4e4e4;
    }

    .tab-nav {
      width: 100%;
      height: 60px;
      line-height: 60px;
      display: flex;
      justify-content: space-between;
    }

    .tab-nav h3 {
      font-size: 24px;
      font-weight: normal;
      margin-left: 20px;
    }

    .tab-nav ul {
      list-style: none;
      display: flex;
      justify-content: flex-end;
    }

    .tab-nav ul li {
      margin: 0 20px;
      font-size: 14px;
    }

    .tab-nav ul li a {
      text-decoration: none;
      border-bottom: 2px solid transparent;
      color: #333;
    }

    .tab-nav ul li a.active {
      border-color: #e1251b;
      color: #e1251b;
    }

    .tab-content {
      padding: 0 16px;
    }

    .tab-content .item {
      display: none;
    }

    .tab-content .item.active {
      display: block;
    }
  </style>
</head>
<body>

  <div class="tab">
    <div class="tab-nav">
      <h3>每日特价</h3>
      <ul>
        <li><a class="active" href="javascript:;" data-id="0">精选</a></li>
        <li><a href="javascript:;" data-id="1">美食</a></li>
        <li><a href="javascript:;" data-id="2">百货</a></li>
        <li><a href="javascript:;" data-id="3">个护</a></li>
        <li><a href="javascript:;" data-id="4">预告</a></li>
      </ul>
    </div>
    <div class="tab-content">
      <div class="item active"><img src="./images/tab00.png" alt="" /></div>
      <div class="item"><img src="./images/tab01.png" alt="" /></div>
      <div class="item"><img src="./images/tab02.png" alt="" /></div>
      <div class="item"><img src="./images/tab03.png" alt="" /></div>
      <div class="item"><img src="./images/tab04.png" alt="" /></div>
    </div>
  </div>

  <script>
    // 采取事件委托的形式实现 tab 栏切换

    // 1. 获取 ul 父元素，因为 ul 只有一个
    const ul = document.querySelector('.tab-nav ul');

    // 2. 获取所有 item 元素
    const items = document.querySelectorAll('.tab-content .item');

    // 3. 添加事件监听器到 ul 元素
    ul.addEventListener('click', function (e) {
      // 只有点击了 a 元素才会触发效果
      if (e.target.tagName === 'A') {
        // 移除之前激活的链接的 'active' 类
        document.querySelector('.tab-nav .active').classList.remove('active');

        // 将 'active' 类添加到当前点击的链接
        e.target.classList.add('active');

        // 获取当前链接的 data-id 属性值，并转换为数字
        const i = +e.target.dataset.id;

        // 移除之前激活的 item 元素的 'active' 类
        document.querySelector('.tab-content .item.active').classList.remove('active');

        // 将 'active' 类添加到与当前链接对应的 item 元素
        items[i].classList.add('active');
      }
    });
  </script>

</body>
</html>
```

### 13.其他事件

#### 13.1 页面加载事件

**1.外部资源（如图片、外联CSS和JavaScript等）加载完毕时触发的事件**

**原因：** 有些时候需要等页面资源全部处理完了做一些事情，老代码喜欢把 script 写在 head 中，这时候直接找 dom 元素找不到。

**事件名：** **load**

监听页面所有资源加载完毕：给 window 添加 load 事件

![](https://i-blog.csdnimg.cn/blog_migrate/6a49c053e7ff1811fe96bf17fa65d9e3.png)

**●** 注意：不光可以监听整个页面资源加载完毕，也可以针对某个资源绑定load事件

**2.当初始的HTML文档被完全加载和解析完成之后，DOMContentLoaded 事件被触发，而无需等待样式表、图像等完全加载**

**事件名：** **DOMContentLoaded**

监听页面DOM加载完毕：给 document 添加 DOMContentLoaded 事件

![](https://i-blog.csdnimg.cn/blog_migrate/a2b204e0fee2936c47b4bb98bd838e59.png)

#### 13.2 页面滚动事件

**滚动条在滚动的时候持续触发的事件**。很多网页需要检测用户把页面滚动到某个区域后做一些处理， 比如固定导航栏，比如返回顶部。

**事件名：scroll**

监听整个页面滚动： ![](https://i-blog.csdnimg.cn/blog_migrate/e133ae88a17e7884e0b675babba87852.png)
一般给 window 或 document 添加 scroll 事件，监听某个元素的内部滚动直接给某个元素加即可。

**13.2 页面滚动事件-获取位置**

scrollLeft 和 scrollTop （属性）：

获取被卷去的大小，获取元素内容往左、往上滚出去看不到的距离，这两个值是可 **读写** 的。 ![](https://i-blog.csdnimg.cn/blog_migrate/3686170105866efd9024d80f646c8282.png)

尽量在scroll事件里面获取被卷去的距离。

开发中，我们经常检测页面滚动的距离，比如页面滚动100像素，就可以显示一个元素，或者固定一个元素。

```javascript
<script>    const div = document.querySelector('div')    // 页面滚动事件    window.addEventListener('scroll', function () {      // 获取html元素写法        // document.documentElement        const n = document.documentElement.scrollTop      if (n >= 100) {        div.style.display = 'block'      } else {        div.style.display = 'none'      }    })  </script>
```

**注意：document.documentElement**     HTML文档返回对象为HTML元素![](https://i-blog.csdnimg.cn/blog_migrate/6a3789cc27a20b43b44153b55d095185.png)

**13.2 页面滚动事件-滚动到指定的坐标**

scrollTo() 方法可把内容滚动到指定的坐标

**语法：**元素.scrollTo(x, y)

**案例：返回顶部**

```javascript
    <script>        // 点击返回页面顶部        const backTop = document.querySelector('#backTop')        backTop.addEventListener('click', function () {            // 可读写            // document.documentElement.scrollTop = 0            window.scrollTo(0, 0)        })    </script>
```

#### 13.3 页面尺寸事件

会在窗口尺寸改变的时候触发事件：resize![](https://i-blog.csdnimg.cn/blog_migrate/bfed691648d47526b89018241ef2f86a.png)

**13.3 页面尺寸事件-获取元素宽高**

获取元素的可见部分宽高（不包含边框，margin，滚动条等）:  clientWidth和clientHeight ![](https://i-blog.csdnimg.cn/blog_migrate/8a888bb8076812f32da0a920a24181ce.png)

**案例：Rem基准值**![](https://i-blog.csdnimg.cn/blog_migrate/84ada66b5a345702f31bd4c9e81dc67b.png)

#### 13.4 元素尺寸与位置

就是通过js的方式，得到 元素在页面中的位置

**●**  **获取宽高：** offsetWidth和offsetHeight （内容 + padding + border）

获取元素的自身宽高、包含元素自身设置的宽高、padding、border。 获取的是数值，方便计算。

**注意:** 获取的是可视宽高, 如果盒子是隐藏的,获取的结果是0

**●**  **获取位置：**

1.offsetLeft和offsetTop

获取元素距离自己 定位父级元素 的左、上距离， 如果都没有则以 文档左上角 为准。

注意：offsetLeft和offsetTop 是只读属性

![](https://i-blog.csdnimg.cn/blog_migrate/fb5ca2f74c75b96e0ad373c6d67cc692.png)

 **案例：仿京东固定导航栏案例**

```html
<body>    <div class="header">我是顶部导航栏</div>    <div class="content">        <div class="sk">秒杀模块</div>    </div>    <div class="backtop">        <img src="./images/close2.png" alt="">        <a href="javascript:;"></a>    </div>    <script>        const sk = document.querySelector('.sk')        const header = document.querySelector('.header')        // 页面滚动事件        window.addEventListener('scroll', function () {            // 当页面滚动到 秒杀模块的时候，就改变 头部的 top值            // 页面被卷去的头部 >=  秒杀模块的位置 offsetTop            const n = document.documentElement.scrollTop            header.style.top = n >= sk.offsetTop ? 0 : '-80px'        })    </script></body>
```

**案例：实现bilibili 点击小滑块移动效果**

```javascript
  <script>    // 1. 事件委托的方法 获取父元素 tabs-list    const list = document.querySelector('.tabs-list')    const line = document.querySelector('.line')    // 2. 注册点击事件    list.addEventListener('click', function (e) {      // 只有点击了A 才有触发效果      if (e.target.tagName === 'A') {        // 得到当前点击元素的位置        // console.log(e.target.offsetLeft)        // 把我们点击的a链接盒子的位置  然后移动        line.style.transform = `translateX(${e.target.offsetLeft}px)`      }    })  </script>
```

2. element.getBoundingClientRect()

方法返回元素的大小及其相对于视口的位置

#### 总结![](https://i-blog.csdnimg.cn/blog_migrate/8aed356c3b4fb275d0527bc0727afd4c.png)

#### 综合案例：电梯导航

```javascript
  <script>    // 第一大模块，页面滑动可以显示和隐藏    (function () {      // 获取元素      const entry = document.querySelector('.xtx_entry')      const elevator = document.querySelector('.xtx-elevator')      // 1. 当页面滚动大于 300像素，就显示 电梯导航      // 2. 给页面添加滚动事件      window.addEventListener('scroll', function () {        // 被卷去的头部大于 300         const n = document.documentElement.scrollTop        elevator.style.opacity = n >= entry.offsetTop ? 1 : 0      })       // 点击返回页面顶部      const backTop = document.querySelector('#backTop')      backTop.addEventListener('click', function () {        // 可读写        // document.documentElement.scrollTop = 0        window.scrollTo(0, 0)      })    })();     // 第二第三都放到另外一个执行函数里面    (function () {      // 2. 点击页面可以滑动       const list = document.querySelector('.xtx-elevator-list')      list.addEventListener('click', function (e) {        // console.log(11)        if (e.target.tagName === 'A' && e.target.dataset.name) {          // 排他思想            // 先移除原来的类active           // 先获取这个active的对象          const old = document.querySelector('.xtx-elevator-list .active')          // console.log(old)          // 判断 如果原来有active类的对象，就移除类，如果开始就没有对象，就不删除，所以不报错          if (old) old.classList.remove('active')          // 当前元素添加 active           e.target.classList.add('active')          // 获得自定义属性  new   topic           // console.log(e.target.dataset.name)          // 根据小盒子的自定义属性值 去选择 对应的大盒子          // console.log(document.querySelector(`.xtx_goods_${e.target.dataset.name}`).offsetTop)          // 获得对应大盒子的 offsetTop          const top = document.querySelector(`.xtx_goods_${e.target.dataset.name}`).offsetTop          // 让页面滚动到对应的位置          document.documentElement.scrollTop = top         }      })       // 3. 页面滚动，可以根据大盒子选 小盒子 添加 active 类      window.addEventListener('scroll', function () {        //  3.1  先移除类         // 先获取这个active的对象        const old = document.querySelector('.xtx-elevator-list .active')        // console.log(old)        // 判断 如果原来有active类的对象，就移除类，如果开始就没有对象，就不删除，所以不报错        if (old) old.classList.remove('active')        // 3.2 判断页面当前滑动的位置，选择小盒子         // 获取4个大盒子        const news = document.querySelector('.xtx_goods_new')        const popular = document.querySelector('.xtx_goods_popular')        const brand = document.querySelector('.xtx_goods_brand')        const topic = document.querySelector('.xtx_goods_topic')        const n = document.documentElement.scrollTop        if (n >= news.offsetTop && n < popular.offsetTop) {          // 选择第一个小盒子          document.querySelector('[data-name=new]').classList.add('active')        } else if (n >= popular.offsetTop && n < brand.offsetTop) {          document.querySelector('[data-name=popular]').classList.add('active')        } else if (n >= brand.offsetTop && n < topic.offsetTop) {          document.querySelector('[data-name=brand]').classList.add('active')        } else if (n >= topic.offsetTop) {          document.querySelector('[data-name=topic]').classList.add('active')        }      })    })();  </script>
```

### 14. 日期对象

**日期对象：**用来表示时间的对象

**作用：**可以得到当前系统时间

#### 14.1 实例化

**●** 在代码中发现了 new 关键字时，一般将这个操作称为 **实例化**

**●** 创建一个时间对象并获取时间

获得当前时间：

```javascript
const date = new Date()
```

获取指定时间：

```javascript
const date = new Date('2023-5-25')
```

#### 14.2 日期对象方法

**使用场景：**因为日期对象返回的数据我们不能直接使用，所以需要转换为实际开发中常用的格式![](https://i-blog.csdnimg.cn/blog_migrate/61a5f9e59286b3a0ba22bc80dc617ada.png)

**案例：页面显示时间** 

```html
<body>  <div></div>  <script>    const div = document.querySelector('div')    function getMyDate() {      const date = new Date()      let h = date.getHours()      let m = date.getMinutes()      let s = date.getSeconds()      h = h < 10 ? '0' + h : h      m = m < 10 ? '0' + m : m      s = s < 10 ? '0' + s : s      return `今天是: ${date.getFullYear()}年${date.getMonth() + 1}月${date.getDate()}号 ${h}:${m}:${s}`    }     div.innerHTML = getMyDate()    setInterval(function () {      div.innerHTML = getMyDate()    }, 1000)  </script></body>
```

#### 14.3 时间戳

**● 使用场景：** 如果计算倒计时效果，前面方法无法直接计算，需要借助于时间戳完成

**● 时间戳：**是指1970年01月01日00时00分00秒起至现在的 毫秒数 ，是一种特殊的计量时间的方式

**● 算法：**

将来的时间戳 - 现在的时间戳 = 剩余时间毫秒数

剩余时间毫秒数 转换为 剩余时间的 年月日时分秒 就是 倒计时时间

比如：将来时间戳 2000ms - 现在时间戳 1000ms = 1000ms，1000ms 转换为就是 0小时0分1秒

**●** **三种方式获取时间戳：**

1. 使用 getTime() 方法

```javascript
const date = new Date()console.log(date.getTime())
```

**2.简写 +new Date()**

重点记住 +new Date() 因为可以返回当前时间戳或者指定的时间戳

```javascript
console.log(+new Date())
```

3. 使用 Date.now()

```javascript
console.log(Date.now())
```

无需实例化， 但是只能得到当前的时间戳， 而前面两种可以返回指定时间的时间戳

**案例：倒计时效果**

```javascript
  <script>    // 函数封装 getCountTime    function getCountTime() {      // 1. 得到当前的时间戳      const now = +new Date()      // 2. 得到将来的时间戳      const last = +new Date('2022-4-1 18:30:00')      // console.log(now, last)      // 3. 得到剩余的时间戳 count  记得转换为 秒数      const count = (last - now) / 1000      // console.log(count)      // 4. 转换为时分秒      // h = parseInt(总秒数 / 60 / 60 % 24)      // 计算小时      // m = parseInt(总秒数 / 60 % 60)           // 计算分数      // s = parseInt(总秒数 % 60)                // 计算当前秒数      // let d = parseInt(count / 60 / 60 / 24)  // 计算当前天数      let h = parseInt(count / 60 / 60 % 24)      h = h < 10 ? '0' + h : h      let m = parseInt(count / 60 % 60)      m = m < 10 ? '0' + m : m      let s = parseInt(count % 60)      s = s < 10 ? '0' + s : s      console.log(h, m, s)       // 把时分秒写到对应的盒子里面      document.querySelector('#hour').innerHTML = h      document.querySelector('#minutes').innerHTML = m      document.querySelector('#scond').innerHTML = s    }    // 先调用一次    getCountTime()     // 开启定时器    setInterval(getCountTime, 1000)  </script>
```

### 15.节点操作

#### 15.1 DOM节点

**DOM节点：** DOM树里每一个内容都称之为节点 ![](https://i-blog.csdnimg.cn/blog_migrate/f81ede35a6aca6f443f947716940060c.png)

**节点类型：**

**●**  **元素节点：** 所有的标签 比如 body、 div，html 是根节点

**●** 属性节点：所有的属性 比如 href

**●** 文本节点：所有的文本

**●** 其他

#### 15.2 查找节点

**节点关系：针对的找亲戚返回的都是对象**   父节点、子节点、兄弟节点

**父节点查找：** parentNode 属性，返回最近一级的父节点 找不到返回为 null

例如：子元素.parentNode

**子节点查找：** childNodes 属性，获得所有子节点、包括文本节点（空格、换行）、注释节点等

**children 属性（重点）** 仅获得所有元素节点，返回的还是一个 伪数组， 例如：父元素.children

**兄弟关系查找：**

1. 下一个兄弟节点： nextElementSibling 属性

2. 上一个兄弟节点： previousElementSibling 属性

#### 15.3 增加节点

**1.创建节点：**创造出一个新的网页元素，再添加到网页内，一般先创建节点，然后插入节点

**创建元素节点方法：**

```javascript
document.createElement('标签名')
```

**2.追加节点：**要想在界面看到，还得插入到某个父元素中

（1） 插入到父元素的最后一个子元素： 父元素.appendChild(要插入的元素)

（2）插入到父元素中某个子元素的前面：父元素.insertBefore(要插入的元素,在哪个元素前面)

**3.克隆节点：**元素.cloneNode(布尔值)

特殊情况下我们新增节点按如下操作： 复制一个原有的节点，把复制的节点放到指定的元素内部

cloneNode会克隆出一个跟原标签一样的元素，括号内传入布尔值。

若为true，则克隆时会包含后代节点一起克隆。若为false(默认)，则克隆时不包含后代节点。

#### 15.4 删除节点

在 JavaScript 原生 DOM 操作中，要删除元素必须通过 父元素删除。

**语法：** 父元素.removeChlid(子元素)， 如不存在父子关系则删除不成功

删除节点和隐藏节点（display:none） 是有区别的：

隐藏节点还是存在的，但是删除，则从html中删除节点

### 16. M端事件

移动端也有自己独特的地方。比如 触屏事件 touch （也称触摸事件），Android 和 IOS 都有。

touch 对象代表一个触摸点。触摸点可能是一根手指，也可能是一根触摸笔。触屏事件可响应用户手指（或触控笔）对屏幕或者触控板操作。

常见的触屏事件如下： ![](https://i-blog.csdnimg.cn/blog_migrate/c2c74054d83090bc73f38a7198d9f09c.png)

### 17.插件 

**插件:** 就是别人写好的一些代码,我们只需要复制对应的代码,就可以直接实现对应的效果

**学习插件的基本过程**

1. 熟悉官网，了解这个插件可以完成什么需求   https://www.swiper.com.cn/

2. 看在线演示，找到符合自己需求的demo    https://www.swiper.com.cn/demo/index.html

3. 查看基本使用流程    https://www.swiper.com.cn/usage/index.html

4. 查看APi文档，去配置自己的插件    https://www.swiper.com.cn/api/index.html

注意：多个swiper同时使用的时候， 类名需要注意区分

### 综合案例：学生信息表

```html
<!DOCTYPE html><html lang="en"> <head>    <meta charset="UTF-8" />    <meta name="viewport" content="width=device-width, initial-scale=1.0" />    <meta http-equiv="X-UA-Compatible" content="ie=edge" />    <title>学生信息管理</title>    <link rel="stylesheet" href="css/index.css" /></head> <body>    <h1>新增学员</h1>    <form class="info" autocomplete="off">        姓名：<input type="text" class="uname" name="uname" />        年龄：<input type="text" class="age" name="age" />        性别:        <select name="gender" class="gender">            <option value="男">男</option>            <option value="女">女</option>        </select>        薪资：<input type="text" class="salary" name="salary" />        就业城市：<select name="city" class="city">            <option value="北京">北京</option>            <option value="上海">上海</option>            <option value="广州">广州</option>            <option value="深圳">深圳</option>            <option value="曹县">曹县</option>        </select>        <button class="add">录入</button>    </form>     <h1>就业榜</h1>    <table>        <thead>            <tr>                <th>学号</th>                <th>姓名</th>                <th>年龄</th>                <th>性别</th>                <th>薪资</th>                <th>就业城市</th>                <th>操作</th>            </tr>        </thead>        <tbody>            <!--         <tr>          <td>1001</td>          <td>欧阳霸天</td>          <td>19</td>          <td>男</td>          <td>15000</td>          <td>上海</td>          <td>            <a href="javascript:">删除</a>          </td>        </tr>         -->        </tbody>    </table>    <script>        // 获取元素        const uname = document.querySelector('.uname')        const age = document.querySelector('.age')        const gender = document.querySelector('.gender')        const salary = document.querySelector('.salary')        const city = document.querySelector('.city')        const tbody = document.querySelector('tbody')        // 获取所有带有name属性的元素        const items = document.querySelectorAll('[name]')        // 声明一个空的数组， 增加和删除都是对这个数组进行操作        const arr = []        // 1. 录入模块        // 1.1 表单提交事件        const info = document.querySelector('.info')        info.addEventListener('submit', function (e) {            // 阻止默认行为 不跳转            e.preventDefault()             // 这里进行表单验证  如果不通过，直接中断，不需要添加数据            // 先遍历循环            for (let i = 0; i < items.length; i++) {                if (items[i].value === '') {                    return alert('输入内容不能为空')                }            }             // 创建新的对象            const obj = {                stuId: arr.length + 1,                uname: uname.value,                age: age.value,                gender: gender.value,                salary: salary.value,                city: city.value            }            // console.log(obj)            // 追加给数组里面            arr.push(obj)            // 清空表单   reset重置            this.reset()            // 调用渲染函数            render()        })         // 2.渲染函数 因为增加和删除都需要渲染        function render() {            // 先清空tbody以前的行，把最新数组里面的数据渲染完毕            tbody.innerHTML = ''            // 遍历arr数组            for (let i = 0; i < arr.length; i++) {                // 生成tr                const tr = document.createElement('tr')                tr.innerHTML = `                    <td>${arr[i].stuId}</td>                    <td>${arr[i].uname}</td>                    <td>${arr[i].age}</td>                    <td>${arr[i].gender}</td>                    <td>${arr[i].salary}</td>                    <td>${arr[i].city}</td>                    <td>                        <a href="javascript:" date-id=${i}>删除</a>                    </td>                `                // 追加元素  父元素.appendChild(子元素)                tbody.appendChild(tr)            }        }         // 3.删除操作        // 3.1 事件委托 tbody        tbody.addEventListener('click', function (e) {            if (e.target.tagName === 'A') {                // 自己的想法 不利用自定义属性                // arr.splice(e.target.stuId - 1, 1)                // 得到当前元素的自定义属性 data-id                // 删除arr数组对应的数据                arr.splice(e.target.dataset.id, 1)                // 重新渲染                render()            }        })    </script> </body> </html>
```

### 18. 重绘和回流

1. 浏览器是如何进行界面渲染的？

a.解析（Parser）HTML，生成DOM树(DOM Tree)

b.同时解析（Parser） CSS，生成样式规则 (Style Rules)

c.根据DOM树和样式规则，生成渲染树(Render Tree)

d.进行布局 Layout(回流/重排):根据生成的渲染树，得到节点的几何信息（位置，大小）

e.进行绘制 Painting(重绘): 根据计算和获取的信息进行整个页面的绘制

f.Display: 展示在页面上

**回流(重排)**

当 Render Tree 中部分或者全部元素的尺寸、结构、布局等发生改变时，浏览器就会重新渲染部分或全部文档的过程称为 回流 。

**重绘**

由于节点(元素)的样式的改变并不影响它在文档流中的位置和文档布局时(比如：color、background-color、outline等)，称为 重绘 。

**重绘不一定引起回流，而回流一定会引起重绘。**

### **19.**Window对象

#### 19.1 BOM

BOM(Browser Object Model ) 是浏览器对象模型。

![](https://i-blog.csdnimg.cn/blog_migrate/19d7ef3d6e81894639394c40624a4749.png)

**●** window对象是一个全局对象，也可以说是JavaScript中的顶级对象

**●** 像document、alert()、console.log()这些都是window的属性,基本BOM属性和方法都是window的

**●** 所有通过var定义在全局作用域中的变量、函数都会变成window对象的属性和方法

**●** window对象下的属性和方法调用的时候可以省略window

#### 19.2 定时器-延时函数

JavaScript 内置的一个用来让代码延迟执行的函数，叫  setTimeout

**语法：** setTimeout(回调函数,等待的毫秒数)

setTimeout 仅仅只执行一次，所以可以理解为就是把一段代码延迟执行, 平时省略window

**清除延时函数** ：

```javascript
let timer = setTimeout(回调函数,等待的毫秒数)clearTimeout(timer)
```

**注意点：**

1. 延时器需要等待,所以后面的代码先执行

2. 每一次调用延时器都会产生一个新的延时器

**两种定时器对比：** 执行的次数

**●** 延时函数: 执行一次

**●** 间歇函数:每隔一段时间就执行一次，除非手动清除

案例：5秒钟之后消失的广告

```html
<body>  <img src="./images/ad.png" alt="">  <script>    // 1.获取元素    const img = document.querySelector('img')    setTimeout(function () {      img.style.display = 'none'    }, 5000)  </script></body>
```

#### 19.3 JS 执行机制

JavaScript 语言的一大特点就是单线程，也就是说，同一个时间只能做一件事。

这是因为 Javascript 这门脚本语言诞生的使命所致——JavaScript 是为处理页面中用户的交互，以及操作 DOM 而诞生的。比如我们对某个 DOM 元素进行添加和删除操作，不能同时进行。 应该先进行添加，之后再删除。

单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。这样所导致的问题是：如果 JS 执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的感觉。

为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程。于是，JS 中出现了 同步 和 异步。

**同步**

前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。

比如做饭的同步做法：我们要烧水煮饭，等水开了（10分钟之后），再去切菜，炒菜。

**异步**

你在做一件事情时，因为这件事情会花费很长时间，在做这件事时，还可以去处理其他事情。

比如做饭的异步做法，我们在烧水的同时，利用这10分钟，去切菜，炒菜。

**他们的本质区别： 这条流水线上各个流程的执行顺序不同。**

**同步任务**

同步任务都在主线程上执行，形成一个 **执行栈。**

**异步任务**

JS 的异步是通过回调函数实现的。

一般而言，异步任务有以下三种类型:

1、普通事件，如 click、resize 等

2、资源加载，如 load、error 等

3、定时器，包括 setInterval、setTimeout 等

异步任务相关添加到 **任务队列** 中（任务队列也称为消息队列）。

**JS 执行机制**

1. 先执行 执行栈中的同步任务 。

2 . 异步任务放入任务队列中。

3. 一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取 任务队列 中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行。

![](https://i-blog.csdnimg.cn/blog_migrate/de4e708ef644699d5dc2cb29e835e0a9.png)

![](https://i-blog.csdnimg.cn/blog_migrate/b8fea83be085f258eaee2b176daa4263.png)

由于主线程不断的重复获得任务、执行任务、再获取任务、再执行，所以这种机制被称为 事件循环（event loop） 。

#### 19.4 location对象

location 的数据类型是对象，它拆分并保存了 URL 地址的各个组成部分。

**常用属性和方法：**

**● href** 属性获取完整的 URL 地址，对其赋值时用于地址的跳转

![](https://i-blog.csdnimg.cn/blog_migrate/82a4d02ee24a015b4847e903c023f9a5.png)

**● search** 属性获取地址中携带的参数，符号 ？后面部分

**● hash** 属性获取地址中的啥希值，符号 # 后面部分，经常用于不刷新页面，显示不同页面，比如 网易云音乐

**● reload** 方法用来刷新当前页面，传入参数 true 时表示强制刷新，如：location.reload(true)

案例：5秒钟之后跳转的页面

```html
<body>  <a href="http://www.itcast.cn">支付成功<span>5</span>秒钟之后跳转到首页</a>  <script>    // 1. 获取元素    const a = document.querySelector('a')    // 2.开启定时器    // 3. 声明倒计时变量    let num = 5    let timerId = setInterval(function () {      num--      a.innerHTML = `支付成功<span>${num}</span>秒钟之后跳转到首页`      // 如果num === 0 则停止定时器，并且完成跳转功能      if (num === 0) {        clearInterval(timerId)        // 4. 跳转  location.href        location.href = 'http://www.itcast.cn'      }    }, 1000)  </script></body>
```

#### 19.5 navigator对象

navigator的数据类型是对象，该对象下记录了浏览器自身的相关信息

**常用属性和方法：** 通过 userAgent 检测浏览器的版本及平台

```html
// 检测 userAgent（浏览器信息）!(function () {const userAgent = navigator.userAgent// 验证是否为Android或iPhoneconst android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)const iphone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)// 如果是Android或iPhone，则跳转至移动站点if (android || iphone) {location.href = 'http://m.itcast.cn' }})()
```

#### 19.6 histroy对象

history 的数据类型是对象，主要管理历史记录， 该对象与浏览器地址栏的操作相对应，如前进、后退、历史记录等

**常用属性和方法** ![](https://i-blog.csdnimg.cn/blog_migrate/9442c2c8c2929b38bdaa635515e9df9e.png)

### 20.本地存储

#### 20.1 本地存储介绍

随着互联网的快速发展，基于网页的应用越来越普遍，同时也变的越来越复杂，为了满足各种各样的需求，会经常性在本地存储大量的数据，HTML5规范提出了相关解决方案。

1、数据存储在 用户浏览器 中

2、设置、读取方便、甚至页面刷新不丢失数据

3、容量较大，sessionStorage和localStorage约 5M 左右

常见的使用场景： https://todomvc.com/examples/vanilla-es6/ 页面刷新数据不丢失

#### 20.2 本地存储分类- localStorage

**作用:** 可以将数据永久存储在本地(用户的电脑), 除非手动删除，否则关闭页面也会存在

**特性：** 可以多窗口（页面）共享（同一浏览器可以共享）、以键值对的形式存储使用

**语法:**

存储数据： localStorage.setItem(key, value)

获取数据： localStorage.getItem(key)

删除数据：localStorage.removeItem(key)

#### 20.2 本地存储分类- sessionStorage

**特性：**

生命周期为关闭浏览器窗口

在同一个窗口(页面)下数据可以共享

以键值对的形式存储使用

用法跟 localStorage 基本相同

#### 20.3 存储复杂数据类型

本地只能存储字符串,无法存储复杂数据类型。

**解决：** 需要将复杂数据类型转换成JSON字符串,在存储到本地

**语法：JSON.stringify(复杂数据类型)** ![](https://i-blog.csdnimg.cn/blog_migrate/534dfa8d5b921796aadb74f819612f14.png)

**问题：**因为本地存储里面取出来的是字符串，不是对象，无法直接使用

**解决：** 把取出来的字符串转换为对象

**语法：JSON.parse(JSON字符串)**

![](https://i-blog.csdnimg.cn/blog_migrate/51bd7b7cecc04e9df9c1f8b318300c32.png)

### **综合案例：学生就业信息表** 

**拓展1：数组中map方法**

**作用：**迭代数组

**语法：**

```javascript
const arr = ['red', 'blue', 'green']    // map 方法也是遍历  处理数据  可以返回一个数组    const newArr = arr.map(function (item, i) {      // console.log(item)  // 数组元素  'red'      // console.log(i)  // 下标      return item + '老师'    })    console.log(newArr)  // ['red老师', 'blue老师', 'green老师']
```

**使用场景：**map 可以处理数据，并且 **返回新的数组**

**拓展2：数组中join方法**

**作用：** join() 方法用于把数组中的所有元素转换一个字符串

**语法：**

```javascript
<script>    const arr = ['red', 'blue', 'green']    // 把数组元素转换为字符串    console.log(arr.join(' '))   </script>
```

**参数：** 数组元素是通过参数里面指定的分隔符进行分隔的

```html
<!DOCTYPE html><html lang="en"> <head>    <meta charset="UTF-8" />    <meta name="viewport" content="width=device-width, initial-scale=1.0" />    <meta http-equiv="X-UA-Compatible" content="ie=edge" />    <title>学生信息管理</title>    <link rel="stylesheet" href="css/index.css" /></head> <body>    <h1>新增学员</h1>    <form class="info" autocomplete="off">        姓名：<input type="text" class="uname" name="uname" />        年龄：<input type="text" class="age" name="age" />        性别:        <select name="gender" class="gender">            <option value="男">男</option>            <option value="女">女</option>        </select>        薪资：<input type="text" class="salary" name="salary" />        就业城市：<select name="city" class="city">            <option value="北京">北京</option>            <option value="上海">上海</option>            <option value="广州">广州</option>            <option value="深圳">深圳</option>            <option value="曹县">曹县</option>        </select>        <button class="add">录入</button>    </form>     <h1>就业榜</h1>     <table>        <thead>            <tr>                <th>学号</th>                <th>姓名</th>                <th>年龄</th>                <th>性别</th>                <th>薪资</th>                <th>就业城市</th>                <th>操作</th>            </tr>        </thead>        <tbody>            <!--         <tr>          <td>1001</td>          <td>欧阳霸天</td>          <td>19</td>          <td>男</td>          <td>15000</td>          <td>上海</td>          <td>            <a href="javascript:">删除</a>          </td>        </tr>         -->        </tbody>    </table>    <script>        // 参考数据        const initData = [            {                stuId: 1001,                uname: '欧阳霸天',                age: 19,                gender: '男',                salary: '20000',                city: '上海',            }        ]        // localStorage.setItem('data', JSON.stringify(initData))        // 1.渲染业务        // 1.1 读取本地存储的数据   student-data  本地存储的命名        // (1) 本地存储有数据则记得转换为对象然后存储到变量里面，后期用于渲染页面        // (2) 如果没有数据，则用空数组来替代        const arr = JSON.parse(localStorage.getItem('data')) || []        // 1.2 利用map和join方法来渲染页面        const tbody = document.querySelector('tbody')        function render() {            // (1) 利用map遍历数组，返回对应tr的数组            const trArr = arr.map(function (ele, index) {                return `                <tr>                    <td>${ele.stuId}</td>                    <td>${ele.uname}</td>                    <td>${ele.age}</td>                    <td>${ele.gender}</td>                    <td>${ele.salary}</td>                    <td>${ele.city}</td>                    <td>                        <a href="javascript:" data-id='${index}'>删除</a>                    </td>                </tr>                 `            })            // (2) 把数组转换为字符串 join            // (3) 把生成的字符串追加给tbody            tbody.innerHTML = trArr.join('')        }        render()         // 2.新增业务        // 2.1 form表单注册提交事件，阻止默认行为        const info = document.querySelector('.info')        const uname = document.querySelector('.uname')        const age = document.querySelector('.age')        const salary = document.querySelector('.salary')        const gender = document.querySelector('.gender')        const city = document.querySelector('.city')        info.addEventListener('submit', function (e) {            e.preventDefault()            // 2.2 非空判断            if (!uname.value || !age.value || !salary.value) {                return alert('输入内容不能为空')            }            // 2.3 给arr数组追加对象，里面存储 表单获取过来的数据            arr.push({                stuId: arr.length ? arr[arr.length - 1].stuId + 1 : 1,                uname: uname.value,                age: age.value,                gender: gender.value,                salary: salary.value,                city: city.value,            })            // 2.4 渲染页面和重置表单reset()方法            render()            this.reset()            // 2.5 把数组重新存入本地存储里面，记得转换为JSON字符串存储            localStorage.setItem('data', JSON.stringify(arr))        })         // 3.删除业务        // 3.1 采用事件委托形式，给tbody注册点击事件        tbody.addEventListener('click', function (e) {            if (e.target.tagName === 'A') {                // 3.2 得到当前点击的索引号。渲染数据时，动态给a链接添加自定义属性data-id                console.log(e.target.dataset.id)                // 确认框confirm 确认是否要真的删除                if (confirm('您确定要删除这条数据吗？')) {                    // 3.3 根据索引号，利用splice删除数组这条数据                    arr.splice(e.target.dataset.id, 1)                    // 3.4 重新渲染页面                    render()                    // 3.5 把最新arr数组存入本地存储                    localStorage.setItem('data', JSON.stringify(arr))                }            }        })     </script></body> </html>
```

### 21.正则表达式

#### 21.1 什么是正则表达式

正则表达式 （Regular Expression）是用于 匹配字符串中字符组合 的模式。在 JavaScript中，正则表达式也是对象。通常用来查找、替换那些符合正则表达式的文本，许多语言都支持正则表达式。

正则表达式在 JavaScript中的**使用场景**：

1. 例如 验证表单 ：用户名表单只能输入英文字母、数字或者下划线， 昵称输入框中可以输入中文。 ( 匹配 ) ，比如用户名: /^[a-z0-9_-]{3,16}$/

2. 过滤掉页面内容中的一些 敏感词 ( 替换 )

3.从字符串中获取我们想要的特定部分( 提取 )等 。

#### 21.2 语法

**1. 定义正则表达式语法：** const 变量名 = /表达式/

其中 / / 是正则表达式字面量，比如：const reg = /前端/

**2.判断是否有符合规则的字符串：**

**test()** 方法 用来查看正则表达式与指定的字符串是否匹配

**语法：** regObj.test(被检测的字符串)  

如果正则表达式与指定的字符串匹配 ，返回true，否则false

```javascript
<script>    const str = '我们在学习前端，希望学习前端能高薪毕业'    // 正则表达式使用：    // 1. 定义规则    const reg = /前端/    // 2. 是否匹配    console.log(reg.test(str))  // true</script>
```

**3.检索（查找）符合规则的字符串：**

**exec()** 方法 在一个指定字符串中执行一个搜索匹配

**语法：** regObj.exec(被检测的字符串)  

如果匹配成功，exec() 方法返回一个数组，否则返回null

```javascript
<script>    const str = '我们在学习前端，希望学习前端能高薪毕业'    // 正则表达式使用：    // 1. 定义规则    const reg = /前端/    // 2. exec()    console.log(reg.exec(str))  // 返回数组  </script>
```

![](https://i-blog.csdnimg.cn/blog_migrate/05defb68ae3ec095bd78273c38be09d1.png)

**正则表达式检测查找 test方法和exec方法有什么区别？**

**●**  test方法 用于判断是否有符合规则的字符串，返回的是布尔值 找到返回true，否则false

**●**  exec方法用于检索（查找）符合规则的字符串，找到返回数组，否则为 null

#### 21.3 元字符

**元字符(特殊字符）:**是一些具有特殊含义的字符，可以极大提高了灵活性和强大的匹配功能。

比如，规定用户只能输入英文26个英文字母，普通字符的话 abcdefghijklm….但是换成元字符写法： [a-z]

**参考文档：**

MDN：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions

正则测试工具: http://tool.oschina.net/regex

为了方便记忆和学习，我们对众多的元字符进行了分类：

**1.边界符（表示位置，开头和结尾，必须用什么开头，用什么结尾）**

正则表达式中的边界符（位置符）用来 提示字符所处的位置 ，主要有两个字符

![](https://i-blog.csdnimg.cn/blog_migrate/8bd771256106a1f3c7018867f4bf38e0.png)

如果 ^ 和 $ 在一起，表示必须是精确匹配。 

```javascript
<script>    // 元字符    // 1. 边界符    console.log(/^哈/.test('哈')) // true    console.log(/^哈/.test('哈哈')) // true    console.log(/^哈/.test('二哈')) // false    console.log(/^哈$/.test('哈')) // true  只有这种情况为true 否则全是false    console.log(/^哈$/.test('哈哈')) // false    console.log(/^哈$/.test('二哈')) // false  </script>
```

**2.量词 （表示重复次数）**

量词用来 设定某个模式出现的次数 ![](https://i-blog.csdnimg.cn/blog_migrate/36df7ae4ccbd1c57681e33db119ac264.png)

注意： 逗号左右两侧千万不要出现空格

```javascript
<script>    // 元字符    // 量词 * 类似 >=0 次    // console.log(/^哈$/.test('哈')) // true    // console.log(/^哈*$/.test('')) // true    // console.log(/^哈*$/.test('哈')) // true    // console.log(/^哈*$/.test('哈哈')) // true    // console.log(/^哈*$/.test('二哈很傻')) //  false    // console.log(/^哈*$/.test('哈很傻')) //  false    // console.log(/^哈*$/.test('哈很哈')) // false    // console.log('------------------')     // //  量词 + 类似 >=1 次    // console.log(/^哈$/.test('哈')) // true    // console.log(/^哈+$/.test('')) // false    // console.log(/^哈+$/.test('哈')) // true    // console.log(/^哈+$/.test('哈哈')) // true    // console.log(/^哈+$/.test('二哈很傻')) //  false    // console.log(/^哈+$/.test('哈很傻')) //  false    // console.log(/^哈+$/.test('哈很哈')) // false    // console.log('------------------')     // //  量词 ? 类似  0 || 1    // console.log(/^哈?$/.test('')) // true    // console.log(/^哈?$/.test('哈')) // true    // console.log(/^哈?$/.test('哈哈')) // false    // console.log(/^哈?$/.test('二哈很傻')) //  false    // console.log(/^哈?$/.test('哈很傻')) //  false    // console.log(/^哈?$/.test('哈很哈')) // false     // 量词 {n} 写几，就必须出现几次    console.log(/^哈{4}$/.test('哈'))    console.log(/^哈{4}$/.test('哈哈'))    console.log(/^哈{4}$/.test('哈哈哈'))    console.log(/^哈{4}$/.test('哈哈哈哈'))    console.log(/^哈{4}$/.test('哈哈哈哈哈'))    console.log(/^哈{4}$/.test('哈哈哈哈哈哈'))    console.log('------------------')     // 量词 {n,}   >=n    console.log(/^哈{4,}$/.test('哈'))    console.log(/^哈{4,}$/.test('哈哈'))    console.log(/^哈{4,}$/.test('哈哈哈'))    console.log(/^哈{4,}$/.test('哈哈哈哈'))    console.log(/^哈{4,}$/.test('哈哈哈哈哈'))    console.log(/^哈{4,}$/.test('哈哈哈哈哈哈'))    console.log('------------------')     // 量词 {n,m}  逗号左右两侧千万不能有空格    >=n && <= m    console.log(/^哈{4,6}$/.test('哈'))    console.log(/^哈{4,6}$/.test('哈哈'))    console.log(/^哈{4,6}$/.test('哈哈哈'))    console.log(/^哈{4,6}$/.test('哈哈哈哈'))    console.log(/^哈{4,6}$/.test('哈哈哈哈哈'))    console.log(/^哈{4,6}$/.test('哈哈哈哈哈哈'))    console.log(/^哈{4,6}$/.test('哈哈哈哈哈哈哈'))    console.log('------------------')     </script>
```

**3.字符类 （比如 \d 表示 0~9）**

（1）  **[ ]** 匹配字符集合，后面的字符串只要包含[ ]中任意 **一个字符** ，都返回 true。

a.[ ] 里面加上 - 连字符，使用 连字符 - 表示一个范围 。

比如：

        [a-z] 表示 a 到 z 26个英文字母都可以

        [a-zA-Z] 表示大小写都可以

        [0-9] 表示 0~9 的数字都可以

b.[ ] 里面加上 ^ 取反符号

比如： [^a-z] 匹配除了小写字母以外的字符

注意要写到中括号里面

```javascript
  <script>    // 元字符    // 字符类   [abc]  只选1个    console.log(/^[abc]$/.test('a'))  // true    console.log(/^[abc]$/.test('b'))  // true    console.log(/^[abc]$/.test('c'))  // true    console.log(/^[abc]$/.test('ab'))  // false    console.log(/^[abc]{2}$/.test('ab'))  // true    console.log('------------------')     // 字符类   [a-z]  只选1个    console.log(/^[A-Z]$/.test('p'))  // false    console.log(/^[A-Z]$/.test('P'))  // true    console.log(/^[0-9]$/.test(2))  // true    console.log(/^[a-zA-Z0-9]$/.test(2))  // true    console.log(/^[a-zA-Z0-9]$/.test('p'))  // true    console.log(/^[a-zA-Z0-9]$/.test('P'))  // true    console.log('------------------')  </script>
```

（2） **.** 匹配除换行符之外的任何单个字符

（3）预定义： 指的是 某些常见模式的简写方式。 ![](https://i-blog.csdnimg.cn/blog_migrate/8fbd4a42a5598b0511188f68c78f445d.png)

案例：用户名验证案例

```html
<body>    <input type="text">    <span></span>    <script>        // 1. 准备正则        const reg = /^[a-zA-Z0-9-_]{6,16}$/        const input = document.querySelector('input')        const span = input.nextElementSibling        input.addEventListener('blur', function () {            // console.log(reg.test(this.value))            if (reg.test(this.value)) {                span.innerHTML = '输入正确'                span.className = 'right'            } else {                span.innerHTML = '请输入6~16位的英文数字下划线'                span.className = 'error'            }        })    </script></body>
```

#### 21.4 修饰符

修饰符约束正则执行的某些细节行为，如是否区分大小写、是否支持多行匹配等

**语法：**/表达式/修饰符

**i** 是单词 ignore 的缩写， **正则匹配时字母不区分大小写**

**g** 是单词 global 的缩写， **匹配所有满足正则表达式的结果**

**替换 replace**

**语法：** 字符串.replace(/正则表达式/,'替换掉文本')

案例： 过滤敏感字

```html
<body>  <textarea name="" id="" cols="30" rows="10"></textarea>  <button>发布</button>  <div></div>  <script>    const tx = document.querySelector('textarea')    const btn = document.querySelector('button')    const div = document.querySelector('div')    btn.addEventListener('click', function () {      // console.log(tx.value)      div.innerHTML = tx.value.replace(/激情|基情/g, '**')      tx.value = ''    })  </script></body>
```

### 综合案例：小兔鲜页面注册

```javascript
<script>        (function () {            // 1.发送短信验证码模块            const code = document.querySelector('.code')            let flag = true // 通过一个变量来控制   节流阀            // 1.1 点击事件            code.addEventListener('click', function () {                if (flag) {                    // flag取反，不能第二次点击                    flag = false                    let i = 5                    code.innerHTML = `${i}秒后重新获取`                    let timerId = setInterval(function () {                        i--                        // 这里不能用 this，定时器的调用者指向 window                        code.innerHTML = `${i}秒后重新获取`                        if (i === 0) {                            // 清除定时器                            clearInterval(timerId)                            // 重新获取                            code.innerHTML = `重新获取`                            // 到时间了，可以开启flag 即可以点击了                            flag = true                        }                    }, 1000)                }            })        })();         // 2. 验证的是用户名        // 2.1 获取用户名表单        const username = document.querySelector('[name=username]')        // 2.2 使用change事件  值发生变化的时候        username.addEventListener('change', verifyName)        // 2.3 封装 verifyName 函数        function verifyName() {            const span = username.nextElementSibling            // 2.4 定义规则  用户名            const reg = /^[a-zA-Z0-9-_]{6,10}$/            if (!reg.test(username.value)) {                span.innerText = '输入不合法，请输入6~10位'                return false            }            // 2.5 合法的 清空span            span.innerText = ''            return true        }         // 3. 验证的是手机号        // 3.1 获取手机表单        const phone = document.querySelector('[name=phone]')        // 3.2 使用change事件  值发生变化的时候        phone.addEventListener('change', verifyPhone)        // 3.3 封装 verifyPhone 函数        function verifyPhone() {            const span = phone.nextElementSibling            // 3.4 定义规则  手机号            const reg = /^1(3\d|4[5-9]|5[0-35-9]|6[567]|7[0-8]|8\d|9[0-35-9])\d{8}$/            if (!reg.test(phone.value)) {                span.innerText = '输入不合法，请输入正确的11位手机号'                return false            }            // 3.5 合法的 清空span            span.innerText = ''            return true        }         // 4. 验证的是验证码        // 4.1 获取验证码表单        const codeInput = document.querySelector('[name=code]')        // 4.2 使用change事件  值发生变化的时候        codeInput.addEventListener('change', verifyCode)        // 4.3 封装 verifyCode 函数        function verifyCode() {            const span = codeInput.nextElementSibling            // 4.4 定义规则  手机号            const reg = /^\d{6}$/            if (!reg.test(codeInput.value)) {                span.innerText = '输入不合法，请输入6位数字'                return false            }            // 4.5 合法的 清空span            span.innerText = ''            return true        }         // 5. 验证的是密码框        // 5.1 获取密码框表单        const password = document.querySelector('[name=password]')        // 5.2 使用change事件  值发生变化的时候        password.addEventListener('change', verifyPwd)        // 5.3 封装 verifyPwd 函数        function verifyPwd() {            const span = password.nextElementSibling            // 5.4 定义规则  手机号            const reg = /^[a-zA-Z0-9-_]{6,20}$/            if (!reg.test(password.value)) {                span.innerText = '输入不合法，请输入6~20位数字'                return false            }            // 5.5 合法的 清空span            span.innerText = ''            return true        }         // 6. 密码的再次验证        // 6.1 获取再次验证表单        const confirm = document.querySelector('[name=confirm]')        // 6.2 使用change事件  值发生变化的时候        confirm.addEventListener('change', verifyConfirm)        // 6.3 封装 verifyConfirm 函数        function verifyConfirm() {            const span = confirm.nextElementSibling            // 6.4 当前表单的值不等于密码框的值 就是错误的            if (confirm.value !== password.value) {                span.innerText = '两次密码输入不一致'                return false            }            // 6.5 合法的 清空span            span.innerText = ''            return true        }         // 7. 同意模块        const queren = document.querySelector('.icon-queren')        queren.addEventListener('click', function () {            // 切换类 toggle 原来有的就删除，没有的就添加            this.classList.toggle('icon-queren2')        })         // 8.表单提交模块        const form = document.querySelector('form')        form.addEventListener('submit', function (e) {            // 判断是否勾选同意模块 ，如果有 icon-queren2说明就勾选了，否则没勾选            if (!queren.classList.contains('icon-queren2')) {                alert('请勾选同意协议')                // return 中止程序，但不阻止提交  所以要阻止提交                e.preventDefault()            }            // 依次判断上面的每个框框是否通过，只有有一个没有通过就阻止            // 因为每一个都要判断 所以要分开写 如果用 || 只会显示第一个不通过的错误信息            if (!verifyName()) e.preventDefault()            if (!verifyPhone()) e.preventDefault()            if (!verifyCode()) e.preventDefault()            if (!verifyPwd()) e.preventDefault()            if (!verifyConfirm()) e.preventDefault()        })    </script>
```

### 阶段案例：小兔鲜登录页面

```javascript
 <script>        // 1. tab栏切换 事件委托        const tab_nav = document.querySelector('.tab-nav')        const pane = document.querySelectorAll('.tab-pane')        // 1.1 事件监听        tab_nav.addEventListener('click', function (e) {            if (e.target.tagName === 'A') {                // 取消上一个active                tab_nav.querySelector('.active').classList.remove('active')                // 当前元素添加active                e.target.classList.add('active')                 // 先干掉所有人 for循环                for (let i = 0; i < pane.length; i++) {                    pane[i].style.display = 'none'                }                // 让对应序号的 pane 显示                pane[e.target.dataset.id].style.display = 'block'            }        })         // 点击提交模块        const form = document.querySelector('form')        const agree = document.querySelector('[name=agree]')        const username = document.querySelector('[name=username]')        form.addEventListener('submit', function (e) {            e.preventDefault()            // 判断是否勾选同意协议            if (!agree.checked) {                return alert('请勾选同意按钮')            }             // 记录用户名到本地存储            localStorage.setItem('xtx-uname', username.value)            // 跳转到首页            location.href = './小兔鲜index.html'        })    </script>
```

### 阶段案例：小兔鲜首页页面

```javascript
<script>        // 1. 获取第一个小li        const li1 = document.querySelector('.xtx_navs li:first-child')        const li2 = li1.nextElementSibling        // 2.最好做个渲染函数 因为退出登录需要重新渲染        function render() {            // 2.1 读取本地存储的用户名            const uname = localStorage.getItem('xtx-uname')            // console.log(uname);            if (uname) {                li1.innerHTML = `<a href="javascript:;"><i class="iconfont icon-user"> ${uname}</i></a>`                li2.innerHTML = `<a href="javascript:;">退出登录</a>`            } else {                li1.innerHTML = `<a href="./小兔鲜login.html">请先登录</a>`                li2.innerHTML = `<a href="./小兔鲜register.html">免费注册</a>`            }        }        render()    // 调用函数         // 2.点击退出登录模块        li2.addEventListener('click', function () {            // 删除本地存储的数据            localStorage.removeItem('xtx-uname')            // 重新渲染            render()        })    </script>
```

### 实战案例：放大镜效果

```javascript
<script>        // 1. 获取三个盒子        // 2. 小盒子 图片切换效果        const small = document.querySelector('.small')        //  中盒子        const middle = document.querySelector('.middle')        //  大盒子        const large = document.querySelector('.large')        // 2. 事件委托        // mouseenter 没有冒泡，因此不能实现事件委托，需要使用 mouseover 通过事件冒泡触发 small        small.addEventListener('mouseover', function (e) {            if (e.target.tagName === 'IMG') {                // 排他思想 干掉以前的active                this.querySelector('.active').classList.remove('active')                // 当前元素的爸爸添加 active                e.target.parentNode.classList.add('active')                // 拿到当前小图片的src                // 让中等盒子里面的图片，src更换为小图片的src                middle.querySelector('img').src = e.target.src                // 大盒子更换背景图片                large.style.backgroundImage = `url(${e.target.src})`            }        })         // 3.鼠标经过中等盒子，显示隐藏大盒子        middle.addEventListener('mouseenter', show)        middle.addEventListener('mouseleave', hide)        let timeId = null        // 显示函数 显示大盒子        function show() {            // 先清除定时器            clearTimeout(timeId)            large.style.display = 'block'        }        // 隐藏函数 隐藏大盒子        function hide() {            timeId = setTimeout(function () {                large.style.display = 'none'            }, 200)        }         // 4.鼠标经过大盒子，显示隐藏大盒子        large.addEventListener('mouseenter', show)        large.addEventListener('mouseleave', hide)         // 5.鼠标经过中等盒子，显示隐藏 黑色遮罩层        const layer = document.querySelector('.layer')        middle.addEventListener('mouseenter', function () {            layer.style.display = 'block'        })        middle.addEventListener('mouseleave', function () {            layer.style.display = 'none'        })         // 6.移动黑色遮罩盒子        middle.addEventListener('mousemove', function (e) {            // 鼠标在middle 盒子里面的坐标 = 鼠标在页面中的坐标 - middle 中等盒子的坐标             // middle 中等盒子的坐标 使用 getBoundingClientRect() 来获取相当于可视区的盒子坐标，不用 offsetLeft 和 offsetTop，因为这两个属性容易被带有定位的父级影响            // 鼠标在页面中的坐标            // console.log(e.pageX);            // middle 中等盒子的坐标            // console.log(middle.getBoundingClientRect().left);            let x = e.pageX - middle.getBoundingClientRect().left - document.documentElement.scrollLeft            let y = e.pageY - middle.getBoundingClientRect().top - document.documentElement.scrollTop            // console.log(x, y);            // 黑色遮罩移动在 middle 盒子内限制移动的距离            if (x >= 0 && x <= 400 && y >= 0 && y <= 400) {                // 黑色盒子不是一直移动的                // 声明2个变量 黑色盒子移动的 mx my 变量                let mx = 0, my = 0                if (x < 100) mx = 0                if (x >= 100 && x <= 300) mx = x - 100                if (x > 300) mx = 200                 if (y < 100) my = 0                if (y >= 100 && y <= 300) my = y - 100                if (y > 300) my = 200                 layer.style.left = mx + 'px'                layer.style.top = my + 'px'                 // 大盒子的背景图片要跟随中等盒子移动 存在的关系是 2倍                large.style.backgroundPositionX = -2 * mx + 'px'                large.style.backgroundPositionY = -2 * my + 'px'            }        })    </script>
```

## 三、JS进阶

### 1.作用域

作用域（scope）规定了变量能够被访问的“范围”，离开了这个“范围”变量便不能被访问，

作用域分为： 局部作用域、 全局作用域

#### 1.1 局部作用域

局部作用域分为函数作用域和块作用域。

**1.** **函数作用域：**

在函数内部声明的变量只能在函数内部被访问，外部无法直接访问。 ![](https://i-blog.csdnimg.cn/blog_migrate/55324d5f3d2898f5d3affe4dce109253.png)

**总结：**

1. 函数内部声明的变量，在函数外部无法被访问

2. 函数的参数也是函数内部的局部变量

3. 不同函数内部声明的变量无法互相访问

4. 函数执行完毕后，函数内部的变量实际被清空了

**2. 块作用域：**

在JavaScript中使用{ }包裹的代码称为代码块，代码块内部声明的变量外部将 有可能 无法被访问。 ![](https://i-blog.csdnimg.cn/blog_migrate/3cc27a9b6853b1414329877403a71de0.png)

**总结：**

1. let 声明的变量会产生块作用域，var 不会产生块作用域

2. const 声明的常量也会产生块作用域

3. 不同代码块之间的变量无法互相访问

4. 推荐使用 let 或 const

#### 1.2 全局作用域

<script> 标签  和 .js 文件 的【最外层】就是全局作用域，在此声明的变量在函数内部也可以被访问。 全局作用域中声明的变量，任何其它作用域都可以被访问。 ![](https://i-blog.csdnimg.cn/blog_migrate/899050b3b91c184f8955ed0078bd1683.png)

**注意：**

1. 为 window 对象动态添加的属性默认也是全局的，不推荐！

2. 函数中未使用任何关键字声明的变量为全局变量，不推荐！！！

3. 尽可能少的声明全局变量，防止全局变量被污染

JavaScript 中的作用域是程序被执行时的底层机制，了解这一机制有助于规范代码书写习惯，避免因作用域导致的语法错误。

#### 1.3 作用域链

作用域链本质上是底层的 变量查找机制 。

在函数被执行时，会 优先查找当前 函数作用域中查找变量。如果当前作用域查找不到则会依次 逐级查找父级作用域 直到全局作用域。

![](https://i-blog.csdnimg.cn/blog_migrate/eafd7a57b1d66f0180b50318ccccb2cc.png) ![](https://i-blog.csdnimg.cn/blog_migrate/3c698aaa86413873bd2391ca4976e852.png)

**总结：**

1. 嵌套关系的作用域串联起来形成了作用域链

2. 相同作用域链中按着 从小到大 的规则查找变量

3. 子作用域能够访问父作用域，父级作用域无法访问子级作用域

#### 1.4 JS垃圾回收机制

**1. 什么是垃圾回收机制？**

垃圾回收机制(Garbage Collection) 简称 GC

JS中内存的分配和回收都是自动完成的，内存在不使用的时候会被垃圾回收器自动回收。

正因为垃圾回收器的存在，许多人认为JS不用太关心内存管理的问题。

但如果不了解JS的内存管理机制，我们同样非常容易成内存泄漏（内存无法被回收）的情况。

不再用到的内存，没有及时释放， 就叫做 **内存泄漏。**

**2.内存的生命周期**

JS环境中分配的内存, 一般有如下生命周期：

1. 内存分配 ：当我们声明变量、函数、对象的时候，系统会自动为他们分配内存

2. 内存使用 ：即读写内存，也就是使用变量、函数等

3. 内存回收 ：使用完毕，由垃圾回收自动回收不再使用的内存

4. 说明：全局变量一般不会回收(关闭页面回收)； 一般情况下局部变量的值不用了, 会被自动回收

#### 拓展-JS垃圾回收机制-**算法说明**

**堆栈空间分配区别：**

1. 栈 (操作系统) : 由 操作系统自动分配释放 函数的参数值、局部变量等，基本数据类型放到栈里面

2. 堆 (操作系统) : 一般 由程序员分配释放 ，若程序员不释放，由 垃圾回收机制 回收。 复杂数据类型 放到堆里面

两种常见的浏览器 垃圾回收算法 : 引用计数法 和 标记清除法

**●**  **引用计数**

IE采用的引用计数算法, 定义“ 内存不再使用 ”，就是看一个 对象 是否有指向它的引用，没有引用了就回收对象。

**算法：**

1. 跟踪记录被 引用的次数

2. 如果被引用了一次，那么就记录次数1,多次引用会 累加 ++

3. 如果减少一个引用就 减1 --

4. 如果引用次数是 0 ，则释放内存

但它却存在一个致命的问题： **嵌套引用** （循环引用）

如果两个对象 相互引用 ，尽管他们已不再使用，垃圾回收器不会进行回收，导致内存泄露。 ![](https://i-blog.csdnimg.cn/blog_migrate/7254c24489bb9ccd617f8c6f849ed291.png)

 因为他们的引用次数永远不会是0。这样的相互引用如果说很大量的存在就会导致大量的内存泄露

**●**  **标记清除法**

现代的浏览器已经不再使用引用计数算法了。

现代浏览器通用的大多是基于 标记清除算法 的某些改进算法，总体思想都是一致的。

**核心：**

1. 标记清除算法将“不再使用的对象”定义为“ 无法达到的对象 ”。

2. 就是从 根部 （在JS中就是全局对象）出发定时扫描内存中的对象。 凡是能从 根部到达 的对象，都是还 需要使用 的。

3. 那些 无法 由根部出发触及到的 对象被标记 为不再使用，稍后进行 回收 。

对于上面的例子，根部已经访问不到，所以自动清除

#### 1.5 闭包

**概念：**一个函数对周围状态的引用捆绑在一起，内层函数中访问到其外层函数的作用域

**简单理解：** **闭包 =  内层函数 + 外层函数的变量**

**闭包作用：** 封闭数据，提供操作，外部也可以访问函数内部的变量

**闭包的基本格式:**

```javascript
<script>    // 简单的写法    function outer() {      let a = 10      function fn() {        console.log(a)      }      fn()    }    outer()</script>
```

```javascript
<script>    // 常见的闭包的形式   外部可以访问使用 函数内部的变量    function outer() {      let a = 100      function fn() {        console.log(a)      }      return fn    }    // outer()   ===  fn   ===  function fn() {}    const fun = outer()    // const fun = function fn() { }    fun() // 调用函数</script>
```

```javascript
<script>    // 常见的写法2    function outer() {      let a = 100      return function () {        console.log(a)      }    }    const fun = outer()    fun() // 调用函数</script>
```

闭包应用：实现数据的私有

比如，我们要做个统计函数调用次数，函数调用一次，就++

```javascript
  <script>    // 闭包的应用    // 普通形式 统计函数调用的次数    // let i = 0    // function fn() {    //   i++    //   console.log(`函数被调用了${i}次`)    // }    //  因为 i 是全局变量，容易被修改    // 闭包形式 统计函数调用的次数    function count() {      let i = 0      function fn() {        i++        console.log(`函数被调用了${i}次`)      }      return fn    }    const fun = count()  </script>
```

![](https://i-blog.csdnimg.cn/blog_migrate/dfd2f1d23585f59ee16652ee6e4a0d47.png)

**闭包的作用：**

1.封闭数据，实现数据私有，外部也可以访问函数内部的变量

2.闭包很有用，因为它允许将函数与其所操作的某些数据（环境）关联起来

闭包可能引起的问题：**内存泄漏**

#### 1.6 变量提升

变量提升是 JavaScript 中比较“奇怪”的现象，它允许在变量声明之前即被访问（仅存在于  var  声明变量）

**注意：**

1. 变量在未声明即被访问时会报语法错误

2. 变量在var声明之前即被访问，变量的值为 undefined

3. let/const 声明的变量不存在变量提升

4. 变量提升出现在相同作用域当中

5. 实际开发中推荐先声明再访问变量

**说明：**

JS初学者经常花很多时间才能习惯变量提升，还经常出现一些意想不到的bug，正因为如此，ES6 引入了块级作用域，用let 或者 const声明变量，让代码写法更加规范和人性化。

**变量提升的流程：**

1. 先把var 变量提升到当前作用域于最前面

2. 只提升变量声明， 不提升变量赋值

3. 然后依次执行代码

不建议使用var声明变量

### 2.函数进阶

#### 2.1 函数提升

函数提升与变量提升比较类似，是指函数在声明之前即可被调用。![](https://i-blog.csdnimg.cn/blog_migrate/b165ba43fb39646ec99b3690e6192423.png)

**总结：**

1. 函数提升能够使函数的声明调用更灵活

2. 函数表达式不存在提升的现象

3. 函数提升出现在相同作用域当中

#### 2.2 函数参数

**1. 动态参数**

arguments 是函数内部内置的伪数组变量，它包含了调用函数时传入的所有实参

arguments 动态参数的**使用场景**：当不确定传递多少个实参的时候

```javascript
  <script>    function getSum() {      // arguments 动态参数 只存在于 函数里面      // 是伪数组 里面存储的是传递过来的实参      // console.log(arguments)  [2,3,4]      let sum = 0      for (let i = 0; i < arguments.length; i++) {        sum += arguments[i]      }      console.log(sum)    }    getSum(2, 3, 4)    getSum(1, 2, 3, 4, 2, 2, 3, 4)  </script>
```

**总结：**

1. arguments 是一个 伪数组 ，只存在于函数中

2. arguments 的作用是 动态获取函数的实参

3. 可以通过for循环依次得到传递过来的实参

**2. 剩余参数**

剩余参数允许我们将一个不定数量的参数表示为一个数组

剩余参数主要的**使用场景**： 用于获取多余的实参

```javascript
  <script>    function getSum(a, b, ...arr) {      console.log(arr)  // 使用的时候不需要写 ...    }    getSum(2, 3)  // []    getSum(1, 2, 3, 4, 5)  // [3,4,5]  </script>
```

**总结：**

1. ... 是语法符号，置于最末函数形参之前，用于获取 多余 的实参

2. 借助 ... 获取的剩余实参，是个 真数组

**剩余参数和动态参数区别：** 动态参数是伪数组，剩余参数是真数组

开发中，还是提倡多使用 **剩余参数**

#### 拓展-展开运算符

展开运算符(…)，将一个数组进行展开，不会修改原数组

**典型运用场景：** 求数组最大值(最小值)、合并数组等

```javascript
  <script>    const arr1 = [1, 2, 3]    // 展开运算符 可以展开数组    // console.log(...arr)    // 1,2,3     // 1 求数组最大值    console.log(Math.max(...arr1)) // 3    // console.log(Math.max(1, 2, 3))    console.log(Math.min(...arr1)) // 1    // 2. 合并数组    const arr2 = [4, 5]    const arr = [...arr1, ...arr2]    console.log(arr)    // [1,2,3,4,5]  </script>
```

**展开运算符 or 剩余参数**

**剩余参数：** 函数参数使用，得到真数组

**展开运算符：** 数组中使用， 数组展开

#### 2.3 箭头函数（重要）

**目的：** 更简短的函数写法并且不绑定this，箭头函数的语法比函数表达式更简洁

**使用场景：** 箭头函数更适用于那些本来 需要匿名函数的地方

**1. 基本语法**

**语法1：基本写法** ![](https://i-blog.csdnimg.cn/blog_migrate/3b89d74a53ad125650fcbe1ba0d4d824.png)

**语法2：只有一个参数可以省略小括号**![](https://i-blog.csdnimg.cn/blog_migrate/02417f5b5454395ed136563049718dd6.png) **语法3：如果函数体只有一行代码，可以写到一行上，并且无需写 return 直接返回值**![](https://i-blog.csdnimg.cn/blog_migrate/b889a2a9cd2344d68d6b10b6bf62a859.png) **语法4：加括号的函数体返回对象字面量表达式**![](https://i-blog.csdnimg.cn/blog_migrate/cf5025c453f76a575d67f01c42079ba0.png)

**总结：**

1. 箭头函数属于表达式函数，因此不存在函数提升

2. 箭头函数只有一个参数时可以省略圆括号 ()

3. 箭头函数函数体只有一行代码时可以省略花括号 {}，并自动做为返回值被返回

4. 加括号的函数体返回对象字面量表达式

**2. 箭头函数参数**

1. 普通函数有arguments 动态参数

2. 箭头函数 没有 arguments 动态参数，但是 有剩余参数 ..args

```javascript
  <script>    // 1. 利用箭头函数来求和    const getSum = (...arr) => {      let sum = 0      for (let i = 0; i < arr.length; i++) {        sum += arr[i]      }      return sum    }    const result = getSum(2, 3, 4)    console.log(result) // 9  </script>
```

**3. 箭头函数 this**

箭头函数不会创建自己的 this ，它只会从自己的作用域链的上一层沿用 this。

```javascript
  <script>    // 以前this的指向：  谁调用的这个函数，this 就指向谁    // console.log(this)  // window    // // 普通函数    // function fn() {    //   console.log(this)  // window    // }    // window.fn()    // // 对象方法里面的this    // const obj = {    //   name: 'andy',    //   sayHi: function () {    //     console.log(this)  // obj    //   }    // }    // obj.sayHi()     // 2. 箭头函数的this  是上一层作用域的this 指向    // const fn = () => {    //   console.log(this)  // window    // }    // fn()    // 对象方法箭头函数 this    // const obj = {    //   uname: 'pink老师',    //   sayHi: () => {    //     console.log(this)  // this 指向谁？ window    //   }    // }    // obj.sayHi()     const obj = {      uname: 'pink老师',      sayHi: function () {        console.log(this)  // obj        let i = 10        const count = () => {          console.log(this)  // obj         }        count()      }    }    obj.sayHi()   </script>
```

在开发中【使用箭头函数前需要考虑函数中 this 的值】，事件回调函数使用箭头函数时，this 为全局的 window，因此 DOM事件回调函数为了简便，还是不太推荐使用箭头函数

### 3.解构赋值

解构赋值是一种快速为变量赋值的简洁语法，本质上仍然是为变量赋值。

#### 3.1 数组解构

数组解构是将数组的单元值 快速批量赋值 给一系列变量的 简洁语法 。

**1.基本语法：**

1. 赋值运算符 = 左侧的 [] 用于批量声明变量，右侧数组的单元值将被赋值给左侧的变量

2. 变量的顺序对应数组单元值的位置依次进行赋值操作

```javascript
 <script>    // 数组解构 赋值    const [max, min, avg] = [100, 60, 80]    // // const max = arr[0]    // // const min = arr[1]    // // const avg = arr[2]    console.log(max) // 100    console.log(avg) // 80  </script>
```

**典型应用交互2个变量**

```javascript
  <script>    // 交换2个变量的值    let a = 1    let b = 2;    // 这里必须有分号    [b, a] = [a, b]    console.log(a, b)  </script>
```

#### 注意： js 前面必须加分号情况

1. 立即执行函数

![](https://i-blog.csdnimg.cn/blog_migrate/a79996c774d72b8a290dcd62206e1aff.png)

2. 数组解构![](https://i-blog.csdnimg.cn/blog_migrate/1a7773dafa337e9d27298d90579ce8dc.png)

**2.变量多 单元值少的情况** 

变量的数量大于单元值数量时，多余的变量将被赋值为 undefined

```javascript
  <script>    // 1. 变量多， 单元值少 ， undefined    const [a, b, c, d] = [1, 2, 3]    console.log(a) // 1    console.log(b) // 2    console.log(c) // 3    console.log(d) // undefined  </script>
```

**3.变量少 单元值多的情况**

```javascript
  <script>    // 2. 变量少， 单元值多    const [a, b] = [1, 2, 3]    console.log(a) // 1    console.log(b) // 2  </script>
```

**4.利用剩余参数解决变量少 单元值多的情况**

剩余参数... 获取剩余单元值，但只能置于最末位，返回的还是一个数组

```javascript
  <script>    // 3.  剩余参数 变量少， 单元值多    const [a, b, ...c] = [1, 2, 3, 4]    console.log(a) // 1    console.log(b) // 2    console.log(c) // [3, 4]  真数组  </script>
```

**5.防止有undefined传递单元值的情况，可以设置默认值**

允许初始化变量的默认值，且只有单元值为 undefined 时默认值才会生效

```javascript
  <script>    // 4.  防止 undefined 传递    const [a = 0, b = 0] = [1, 2]    const [a = 0, b = 0] = []    console.log(a) // 0    console.log(b) // 0  </script>
```

**6.按需导入，忽略某些返回值**

```javascript
  <script>    // 5.  按需导入赋值    const [a, b, , d] = [1, 2, 3, 4]    console.log(a) // 1    console.log(b) // 2    console.log(d) // 4  </script>
```

**7.支持多维数组的结构**

```javascript
  <script>    // 多维数组解构    // const [a, b, c] = [1, 2, [3, 4]]    // console.log(a) // 1    // console.log(b) // 2    // console.log(c) // [3,4]     const [a, b, [c, d]] = [1, 2, [3, 4]]    console.log(a) // 1    console.log(b) // 2    console.log(c) // 3    console.log(d) // 4  </script>
```

#### 3.2 对象解构

对象解构是将对象属性和方法快速批量赋值给一系列变量的简洁语法。

**1.** **基本语法：**

1. 赋值运算符 = 左侧的 {} 用于批量声明变量，右侧对象的属性值将被赋值给左侧的变量

2. 对象属性的值将被赋值给与属性名 相同的 变量

3. 注意 解构的变量名不要和外面的变量名冲突 否则报错

4.对象中找不到与变量名一致的属性时变量值为 undefined

```javascript
  <script>    // 对象解构    // const obj = {    //   uname: 'pink老师',    //   age: 18    // }    // 解构的语法    const { uname, age } = {age: 18, uname: 'pink老师' }    // 等价于 const uname =  obj.uname    // 要求属性名和变量名必须一直才可以    console.log(uname)    console.log(age)  </script>
```

**2. 给新的变量名赋值：**可以从一个对象中提取变量并同时修改新的变量名

```javascript
  <script>    // 1. 对象解构的变量名 可以重新改名  旧变量名: 新变量名    const { uname: username, age } = { uname: 'pink老师', age: 18 }    console.log(username)    console.log(age)  </script>
```

**3. 数组对象解构**

```javascript
  <script>    // 2. 解构数组对象    const pig = [      {        uname: '佩奇',        age: 6      }    ]    const [{ uname, age }] = pig    console.log(uname)    console.log(age)  </script>
```

**3. 多级对象解构**

```javascript
  <script>    // const pig = {    //   name: '佩奇',    //   family: {    //     mother: '猪妈妈',    //     father: '猪爸爸',    //     sister: '乔治'    //   },    //   age: 6    // }    // // 多级对象解构    // const { name, family: { mother, father, sister } } = pig    // console.log(name)    // console.log(mother)    // console.log(father)    // console.log(sister)     const person = [      {        name: '佩奇',        family: {          mother: '猪妈妈',          father: '猪爸爸',          sister: '乔治'        },        age: 6      }    ]    const [{ name, family: { mother, father, sister } }] = person    console.log(name)    console.log(mother)    console.log(father)    console.log(sister)  </script>
```

**渲染商品列表案例**

遍历数组 forEach 方法（重点）

forEach() 方法用于调用数组的每个元素，并将元素传递给回调函数

主要使用场景： **遍历数组的每个元素**

**语法：** ![](https://i-blog.csdnimg.cn/blog_migrate/4062b0915916b1c985f2f91bb87405c8.png)

**注意：**

1. forEach 主要是遍历数组

2. 参数当前数组元素是必须要写的，索引号可选。

```html
<body>  <div class="list">    <!-- <div class="item">      <img src="" alt="">      <p class="name"></p>      <p class="price"></p>    </div> -->  </div>  <script>    const goodsList = [      {        id: '4001172',        name: '称心如意手摇咖啡磨豆机咖啡豆研磨机',        price: '289.00',        picture: 'https://yanxuan-item.nosdn.127.net/84a59ff9c58a77032564e61f716846d6.jpg',      },      {        id: '4001594',        name: '日式黑陶功夫茶组双侧把茶具礼盒装',        price: '288.00',        picture: 'https://yanxuan-item.nosdn.127.net/3346b7b92f9563c7a7e24c7ead883f18.jpg',      },      {        id: '4001009',        name: '竹制干泡茶盘正方形沥水茶台品茶盘',        price: '109.00',        picture: 'https://yanxuan-item.nosdn.127.net/2d942d6bc94f1e230763e1a5a3b379e1.png',      },      {        id: '4001874',        name: '古法温酒汝瓷酒具套装白酒杯莲花温酒器',        price: '488.00',        picture: 'https://yanxuan-item.nosdn.127.net/44e51622800e4fceb6bee8e616da85fd.png',      },      {        id: '4001649',        name: '大师监制龙泉青瓷茶叶罐',        price: '139.00',        picture: 'https://yanxuan-item.nosdn.127.net/4356c9fc150753775fe56b465314f1eb.png',      },      {        id: '3997185',        name: '与众不同的口感汝瓷白酒杯套组1壶4杯',        price: '108.00',        picture: 'https://yanxuan-item.nosdn.127.net/8e21c794dfd3a4e8573273ddae50bce2.jpg',      },      {        id: '3997403',        name: '手工吹制更厚实白酒杯壶套装6壶6杯',        price: '99.00',        picture: 'https://yanxuan-item.nosdn.127.net/af2371a65f60bce152a61fc22745ff3f.jpg',      },      {        id: '3998274',        name: '德国百年工艺高端水晶玻璃红酒杯2支装',        price: '139.00',        picture: 'https://yanxuan-item.nosdn.127.net/8896b897b3ec6639bbd1134d66b9715c.jpg',      },    ]     // 1. 声明一个字符串变量    let str = ''    // 2. 遍历数据     goodsList.forEach(item => {      // console.log(item)  // 可以得到每一个数组元素  对象 {id: '4001172'}      // const {id} =  item  对象解构      const { name, price, picture } = item      str += `      <div class="item">        <img src=${picture} alt="">        <p class="name">${name}</p>        <p class="price">${price}</p>      </div>      `    })    // 3.生成的 字符串 添加给 list     document.querySelector('.list').innerHTML = str  </script></body>
```

### 综合案例：商品列表价格筛选

**筛选数组 filter 方法（重点）**

filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素

**主要使用场景：** **筛选数组符合条件的元素** **，并返回筛选之后元素的** **新数组**

**语法：** ![](https://i-blog.csdnimg.cn/blog_migrate/f5928f2f3e94ec93aa0f76952b1fa094.png)

**返回值：** 返回 数组 ，包含了符合条件的所有元素。如果没有符合条件的元素则返回空数组

**参数：** currentValue 必须写， index 可选

因为返回新数组，所以 不会影响原数组

```html
<body>    <div class="filter">        <a data-index="1" href="javascript:;">0-100元</a>        <a data-index="2" href="javascript:;">100-300元</a>        <a data-index="3" href="javascript:;">300元以上</a>        <a href="javascript:;">全部区间</a>    </div>    <div class="list">        <!-- <div class="item">      <img src="" alt="">      <p class="name"></p>      <p class="price"></p>    </div> -->    </div>    <script>        // 初始化数据        const goodsList = [            {                id: '4001172',                name: '称心如意手摇咖啡磨豆机咖啡豆研磨机',                price: '289.00',                picture: 'https://yanxuan-item.nosdn.127.net/84a59ff9c58a77032564e61f716846d6.jpg',            },            {                id: '4001594',                name: '日式黑陶功夫茶组双侧把茶具礼盒装',                price: '288.00',                picture: 'https://yanxuan-item.nosdn.127.net/3346b7b92f9563c7a7e24c7ead883f18.jpg',            },            {                id: '4001009',                name: '竹制干泡茶盘正方形沥水茶台品茶盘',                price: '109.00',                picture: 'https://yanxuan-item.nosdn.127.net/2d942d6bc94f1e230763e1a5a3b379e1.png',            },            {                id: '4001874',                name: '古法温酒汝瓷酒具套装白酒杯莲花温酒器',                price: '488.00',                picture: 'https://yanxuan-item.nosdn.127.net/44e51622800e4fceb6bee8e616da85fd.png',            },            {                id: '4001649',                name: '大师监制龙泉青瓷茶叶罐',                price: '139.00',                picture: 'https://yanxuan-item.nosdn.127.net/4356c9fc150753775fe56b465314f1eb.png',            },            {                id: '3997185',                name: '与众不同的口感汝瓷白酒杯套组1壶4杯',                price: '108.00',                picture: 'https://yanxuan-item.nosdn.127.net/8e21c794dfd3a4e8573273ddae50bce2.jpg',            },            {                id: '3997403',                name: '手工吹制更厚实白酒杯壶套装6壶6杯',                price: '100.00',                picture: 'https://yanxuan-item.nosdn.127.net/af2371a65f60bce152a61fc22745ff3f.jpg',            },            {                id: '3998274',                name: '德国百年工艺高端水晶玻璃红酒杯2支装',                price: '139.00',                picture: 'https://yanxuan-item.nosdn.127.net/8896b897b3ec6639bbd1134d66b9715c.jpg',            },        ]         // 1. 渲染函数  封装        function render(arr) {            // 声明空字符串            let str = ''            // 遍历数组            arr.forEach(item => {                // 解构                const { name, picture, price } = item                str += `                <div class="item">                    <img src=${picture} alt="">                    <p class="name">${name}</p>                    <p class="price">${price}</p>                </div>                `            })            // 追加给 List            document.querySelector('.list').innerHTML = str        }        render(goodsList)         // 2.过滤筛选        document.querySelector('.filter').addEventListener('click', e => {            const { tagName, dataset } = e.target            // 判断            if (tagName === 'A') {                // arr 返回的新数组                let arr = goodsList                if (dataset.index === '1') {                    arr = goodsList.filter(item => item.price > 0 && item.price <= 100)                } else if (dataset.index === '2') {                    arr = goodsList.filter(item => item.price >= 100 && item.price <= 300)                } else if (dataset.index === '3') {                    arr = goodsList.filter(item => item.price >= 300)                }                // 渲染函数                render(arr)            }        })    </script></body>
```

### 4.深入对象

#### 4.1创建对象三种方式

**1.** **利用对象字面量创建对象**

```javascript
const o = {    name:'字面量'}
```

**2.** **利用 new Object 创建对象**

```javascript
  <script>    // const obj = new Object()    // obj.uname = 'pink老师'    // console.log(obj)    const obj = new Object({ uname: 'pink' })    console.log(obj)  </script>
```

**3.** **利用构造函数创建对象**

#### 4.2 构造函数

**构造函数 ：**是一种特殊的函数，主要用来初始化对象

**使用场景：** 常规的 {...} 语法允许创建一个对象。比如我们创建了佩奇的对象，继续创建乔治的对象还需要重新写一遍，此时可以通过 构造函数 来 快速创建多个类似的对象 。

构造函数在技术上是常规函数。

不过有两个约定：

1. 它们的命名以 大写字母开头 。

2. 它们只能由 " new " 操作符来执行。

**构造函数语法：** 大写字母开头的函数

**创建构造函数：**

```javascript
  <script>    // 创建一个猪 构造函数     function Pig(uname, age) {      this.uname = uname      this.age = age    }     // console.log(new Pig('佩奇', 6))    // console.log(new Pig('乔治', 3))    const p = new Pig('佩奇', 6)    console.log(p)  </script>
```

**说明：**

1. 使用 new 关键字调用函数的行为被称为 实例化

2. 实例化构造函数时没有参数时可以省略 ()

3. 构造函数内部无需写return，返回值即为新创建的对象，即自动返回创建的新对象

4. 构造函数内部的 return 返回的值无效，所以不要写return

5. new Object（） new Date（） 也是实例化构造函数

**实例化执行过程**

1. 创建新对象

2. 构造函数this指向新对象

3. 执行构造函数代码，修改this，添加新的属性

4. 返回新对象

#### 4.3 实例成员&静态成员

**实例成员：**

通过构造函数创建的对象称为实例对象，实例对象中的属性和方法称为实例成员。 ![](https://i-blog.csdnimg.cn/blog_migrate/a8f6adca5d386a7bf2c338796dddf74c.png)

**说明：**

1. 实例对象的属性和方法即为实例成员

2. 为构造函数传入参数，动态创建 结构相同但值不同 的对象

3. 构造函数创建的实例对象 彼此独立互不影响 。

**静态成员：**

构造函数的属性和方法被称为静态成员

![](https://i-blog.csdnimg.cn/blog_migrate/ca3d9768b3db329876fe04600f25b534.png)

**说明：**

1. 构造函数的属性和方法被称为静态成员

2. 一般 公共特征 的属性或方法静态成员设置为静态成员

3. 静态成员方法中的 this 指向构造函数本身

### 5.内置构造函数

在 JavaScript 中 最主要 的数据类型有 6 种：

**基本数据类型：** 字符串、数值、布尔、undefined、null

**引用类型:** 对象

但是，我们会发现有些特殊情况： ![](https://i-blog.csdnimg.cn/blog_migrate/2e2f2e74f55b230b2e79eb46815ad8fd.png)

其实字符串、数值、布尔、等基本类型也都有专门的构造函数，这些我们称为 包装类型 。

JS中几乎所有的数据都可以基于构造函数创建。

**引用类型** ：Object，Array，RegExp，Date 等

**包装类型** ：String，Number，Boolean 等

#### 5.1 Object

Object 是内置的构造函数，用于创建普通对象。 ![](https://i-blog.csdnimg.cn/blog_migrate/7e6a888e62194d8b4b8a1106fde31d3c.png)

但是推荐使用字面量方式声明对象，而不是 Object 构造函数

**三个常用静态方法（静态方法就是只有构造函数Object可以调用的）**

**1.Object.keys**

**作用：** Object.keys 静态方法获取 对象中所有属性（键）

**语法：**

```javascript
  <script>    const o = { uname: 'pink', age: 18 }    // 1.获得所有的属性名    console.log(Object.keys(o))  //返回数组['uname', 'age']  </script>
```

**注意：** 返回的是一个 数组

**2.Object.values**

**作用：** Object.values 静态方法获取 对象中所有属性值

**语法：**

```javascript
  <script>    const o = { uname: 'pink', age: 18 }    // 2. 获得所有的属性值    console.log(Object.values(o))  //  ['pink', 18]  </script>
```

**注意：** 返回的是一个 数组

**3.Object. assign**

**作用：** Object. assign 静态方法常用于 对象拷贝

**使用：** 经常使用的场景给对象添加属性

**语法：**

```javascript
  <script>    const o = { uname: 'pink', age: 18 }    // 3. 对象的拷贝    // const oo = {}    // Object.assign(oo, o)    // console.log(oo)    Object.assign(o, { gender: '女' })    console.log(o)  </script>
```

#### 5.2 Array

Array 是内置的构造函数，用于创建数组。创建数组建议使用字面量创建，不用Array构造函数创建 ![](https://i-blog.csdnimg.cn/blog_migrate/aabb03b6bf1d750d2775e6ee3a4f1306.png)

**1. 数组常见实例方法-核心方法**

![](https://i-blog.csdnimg.cn/blog_migrate/fd9b17d8b1f28a90d4deb569355e260d.png)

**作用：** **reduce** 返回函数累计处理的结果，经常用于求和等

**基本语法：**arr.reduce(function(累计值, 当前元素){}, 起始值) ![](https://i-blog.csdnimg.cn/blog_migrate/69b22a014d2a7b278b9888a8797bf139.png)

**参数：** 起始值可以省略，如果写就作为第一次累计的起始值

**累计值参数：**

1. 如果有起始值，则以起始值为准开始累计， 累计值 = 起始值

2. 如果没有起始值， 则累计值以数组的第一个数组元素作为起始值开始累计

3. 后面每次遍历就会用后面的数组元素 累计到 累计值 里面 （类似求和里面的 sum ）

**使用场景：求和运算**

```javascript
  <script>    const arr = [1, 2, 3]    const re = arr.reduce((prev, item) => prev + item)    console.log(re)  </script>
```

**2. 数组常见方法-其他方法** ![](https://i-blog.csdnimg.cn/blog_migrate/8cebf3b0acb857a29ac3671edf1d0382.png)

**3. 数组常见方法- 伪数组转换为真数组**

静态方法 Array.from()

```javascript
  <script>    //  Array.from(lis) 把伪数组转换为真数组    const lis = document.querySelectorAll('ul li')    // console.log(lis)    // lis.pop() 报错    const liss = Array.from(lis)    liss.pop()    console.log(liss)  </script>
```

#### 5.3 String

在 JavaScript 中的字符串、数值、布尔具有对象的使用特征，如具有属性和方法。

之所以具有对象特征的原因是字符串、数值、布尔类型数据是 JavaScript 底层使用 Object 构造函数“包装”来的，被称为 **包装类型** 。

**1. 字符串常见实例方法** ![](https://i-blog.csdnimg.cn/blog_migrate/5d5360f9c7575896bf1956a9ab737043.png)

```javascript
  <script>    //1. split 把字符串 转换为 数组  和 join() 相反    // const str = 'pink,red'    // const arr = str.split(',')    // console.log(arr)    // const str1 = '2022-4-8'    // const arr1 = str1.split('-')    // console.log(arr1)    // 2. 字符串的截取   substring(开始的索引号[， 结束的索引号])    // 2.1 如果省略 结束的索引号，默认取到最后    // 2.2 结束的索引号不包含想要截取的部分    // const str = '今天又要做核酸了'    // console.log(str.substring(5, 7))  // [5,7)    // 3. startsWith 判断是不是以某个字符开头    // const str = 'pink老师上课中'    // console.log(str.startsWith('pink'))    // 4. includes 判断某个字符是不是包含在一个字符串里面    const str = '我是pink老师'    console.log(str.includes('pink')) // true  </script>
```

#### 显示赠品练习

```javascript
 <script>    const gift = '50g的茶叶,清洗球'    // 1. 把字符串拆分为数组    // console.log(gift.split(',')) [,]    // 2. 根据数组元素的个数，生成 对应 span标签    // const str = gift.split(',').map(function (item) {    //   return `<span>【赠品】 ${item}</span> <br>`    // }).join('')     // // console.log(str)    // document.querySelector('div').innerHTML = str    document.querySelector('div').innerHTML = gift.split(',').map(item => `<span>【赠品】 ${item}</span> <br>`).join('')  </script>
```

#### 5.4 Number

Number 是内置的构造函数，用于创建数值

**常用方法：** **toFixed()** 设置保留小数位的长度

```javascript
 <script>    // toFixed 方法可以让数字指定保留的小数位数    const num = 10.923    // console.log(num.toFixed())    console.log(num.toFixed(1))    const num1 = 10    console.log(num1.toFixed(2))  </script>
```

### 综合案例：购物车展示

```javascript
<body>    <div class="list">        <!-- <div class="item">      <img src="https://yanxuan-item.nosdn.127.net/84a59ff9c58a77032564e61f716846d6.jpg" alt="">      <p class="name">称心如意手摇咖啡磨豆机咖啡豆研磨机 <span class="tag">【赠品】10优惠券</span></p>      <p class="spec">白色/10寸</p>      <p class="price">289.90</p>      <p class="count">x2</p>      <p class="sub-total">579.80</p>    </div> -->    </div>    <div class="total">        <div>合计：<span class="amount">1000.00</span></div>    </div>    <script>        const goodsList = [            {                id: '4001172',                name: '称心如意手摇咖啡磨豆机咖啡豆研磨机',                price: 289.9,                picture: 'https://yanxuan-item.nosdn.127.net/84a59ff9c58a77032564e61f716846d6.jpg',                count: 2,                spec: { color: '白色' }            },            {                id: '4001009',                name: '竹制干泡茶盘正方形沥水茶台品茶盘',                price: 109.8,                picture: 'https://yanxuan-item.nosdn.127.net/2d942d6bc94f1e230763e1a5a3b379e1.png',                count: 3,                spec: { size: '40cm*40cm', color: '黑色' }            },            {                id: '4001874',                name: '古法温酒汝瓷酒具套装白酒杯莲花温酒器',                price: 488,                picture: 'https://yanxuan-item.nosdn.127.net/44e51622800e4fceb6bee8e616da85fd.png',                count: 1,                spec: { color: '青色', sum: '一大四小' }            },            {                id: '4001649',                name: '大师监制龙泉青瓷茶叶罐',                price: 139,                picture: 'https://yanxuan-item.nosdn.127.net/4356c9fc150753775fe56b465314f1eb.png',                count: 1,                spec: { size: '小号', color: '紫色' },                gift: '50g茶叶,清洗球,宝马, 奔驰'            }        ]         // 1. 根据数据渲染页面        document.querySelector('.list').innerHTML = goodsList.map(item => {            // console.log(item)  // 每一条对象            // 对象解构  item.price item.count            const { picture, name, count, price, spec, gift } = item            // 规格文字模块处理            const text = Object.values(spec).join('/')            // 计算小计模块 单价 * 数量  保留两位小数             // 注意精度问题，因为保留两位小数，所以乘以 100  最后除以100            const subTotal = ((price * 100 * count) / 100).toFixed(2)            // 处理赠品模块 '50g茶叶,清洗球'            const str = gift ? gift.split(',').map(item => `<span class="tag">【赠品】${item}</span> `).join('') : ''            return `        <div class="item">          <img src=${picture} alt="">          <p class="name">${name} ${str} </p>          <p class="spec">${text} </p>          <p class="price">${price.toFixed(2)}</p>          <p class="count">x${count}</p>          <p class="sub-total">${subTotal}</p>        </div>      `        }).join('')         // 3. 合计模块        const total = goodsList.reduce((prev, item) => prev + (item.price * 100 * item.count) / 100, 0)        // console.log(total)        document.querySelector('.amount').innerHTML = total.toFixed(2)    </script></body>
```

### 6.编程思想

#### 6.1 面向过程编程

**面向过程** 就是分析出解决问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用的时候再一个一个的依次调用就可以了。

面向过程，就是按照我们分析好了的步骤，按照步骤解决问题。

#### 6.2 面向对象编程 (oop)

**面向对象** 是把事务分解成为一个个对象，然后由对象之间分工与合作。

面向对象是以对象功能来划分问题，而不是步骤。

在面向对象程序开发思想中，每一个对象都是功能中心，具有明确分工。

面向对象编程具有 灵活、代码可复用、容易维护和开发 的优点，更适合多人合作的大型软件项目。

**面向对象的特性：** 封装性、继承性、多态性

#### 6.3 面向过程和面向对象的对比

![](https://i-blog.csdnimg.cn/blog_migrate/b83e2eff946e1333bd30d794fcaa4349.png)

前端不同于其他语言，面向过程更多

### 7. 构造函数（封装性）

封装是面向对象思想中比较重要的一部分，js面向对象可以通过构造函数实现的封装。

同样的将变量和函数组合到了一起并能通过 this 实现数据的共享，所不同的是借助构造函数创建出来的实例对象之间是彼此不影响的。

**总结：**

1. 构造函数体现了 面向对象的封装特性

2. 构造函数实例创建的对象彼此独立、互不影响

面向对象编程的特性：比如封装性、继承性等，可以借助于构造函数来实现

但是 存在浪费内存的问题

![](https://i-blog.csdnimg.cn/blog_migrate/6bb5ae6a3e237f5b7322fdabc3ef40a3.png)

### 8.原型

#### 8.1 原型

构造函数通过原型分配的函数是所有对象所 **共享的** 。

JavaScript 规定， 每一个构造函数都有一个 prototype 属性 ，指向另一个对象，所以我们也称为原型对象。这个对象可以挂载函数，对象实例化不会多次创建原型上函数， 节约内存 。

可以把那些不变的方法直接定义在 prototype 对象上，这样所有对象的实例都可以共享这些方法。

构造函数和原型对象中的 **this** 都指向 **实例化的对象。**

![](https://i-blog.csdnimg.cn/blog_migrate/e7502806b3b2ed4996c98ce86d34b9a5.png)

####  8.2 原型 - this指向

构造函数和原型对象中的this 都指向 **实例化的对象**

```javascript
  <script>    let that    function Star(uname) {      // that = this      // console.log(this)      this.uname = uname    }    // 原型对象里面的函数this指向的还是 实例对象 ldh    Star.prototype.sing = function () {      that = this      console.log('唱歌')    }    // 实例对象 ldh       // 构造函数里面的 this 就是  实例对象  ldh    const ldh = new Star('刘德华')    ldh.sing()    console.log(that === ldh)  </script>
```

#### 8.3 constructor 属性

每个原型对象里面都有个constructor 属性（ constructor 构造函数 ）

**作用：** 该属性 指向 该原型对象的 构造函数， 简单理解，就是指向我的爸爸（构造函数） ![](https://i-blog.csdnimg.cn/blog_migrate/3f50ec759ea65e789dba133156e9246a.png)

**使用场景：**

如果有多个对象的方法，我们可以给原型对象采取对象形式赋值。

但是这样就会覆盖构造函数原型对象原来的内容，这样修改后的原型对象 constructor 就不再指向当前构造函数了

此时，我们可以在修改后的原型对象中， 添加一个 constructor 指向原来的构造函数 。

```javascript
  <script>    // constructor  单词 构造函数     // Star.prototype.sing = function () {    //   console.log('唱歌')    // }    // Star.prototype.dance = function () {    //   console.log('跳舞')    // }    function Star() {    }    // console.log(Star.prototype)    Star.prototype = {      // 从新指回创造这个原型对象的 构造函数      constructor: Star,      sing: function () {        console.log('唱歌')      },      dance: function () {        console.log('跳舞')      },    }    console.log(Star.prototype)    // console.log(Star.prototype.constructor)     // const ldh = new Star()    // console.log(Star.prototype.constructor === Star)  </script>
```

#### 8.4 对象原型

对象都会有一个属性 **__proto__** 指向构造函数的 prototype 原型对象，之所以我们对象可以使用构造函数 prototype 原型对象的属性和方法，就是因为对象有 __proto__ 原型的存在。![](https://i-blog.csdnimg.cn/blog_migrate/7cf8d1c29ac6ec8eebf13b3d1c73e6b4.png)

**注意：**

__proto__ 是JS非标准属性

[[prototype]]和__proto__意义相同

用来表明当前实例对象指向哪个原型对象prototype

  __proto__对象原型里面也有一个 constructor属性， 指向创建该实例对象的构造函数 ![](https://i-blog.csdnimg.cn/blog_migrate/b7ec501968d3f6e7b9bf8cf3346e61f8.png)

**总结（建议反复观看）：**

1. prototype是什么？哪里来的？

        原型（原型对象）

        构造函数都自动有原型

2. constructor属性在哪里？作用干啥的？

        prototype原型和对象原型__proto__里面都有

        都 指向 创建实例对象/原型的 构造函数

3. __proto__属性在哪里？指向谁？

        在实例对象里面

        指向原型 prototype

#### **8.5 原型继承**

继承是面向对象编程的另一个特征，通过继承进一步提升代码封装的程度，JavaScript 中大多是借助原型对象实现继承的特性。

**1. 封装-** **抽取公共部分**

**2. 继承-** 让男人和女人都能**继承**人类**公共的一些属性和方法**

```javascript
  <script>    // 继续抽取   公共的部分放到原型上    // const Person1 = {    //   eyes: 2,    //   head: 1    // }    // const Person2 = {    //   eyes: 2,    //   head: 1    // }    // 构造函数  new 出来的对象 结构一样，但是对象不一样    function Person() {      this.eyes = 2      this.head = 1    }    // 女人  构造函数   继承  想要 继承 Person    function Woman() {     }    // Woman 通过原型来继承 Person    Woman.prototype = Person  // {eyes: 2, head: 1}     // 指回原来的构造函数    Woman.prototype.constructor = Woman  </script>
```

**3. 问题：** 如果我们给女人添加了一个baby的方法，发现男人自动也添加这个方法

**原因：** 男人和女人都同时使用了同一个对象，根据引用类型的特点，他们指向同一个对象，修改一个就会都影响 ![](https://i-blog.csdnimg.cn/blog_migrate/a227e0c255e66fa8b8dd9208493bf19e.png)

**4. 解决：**

需求：男人和女人不要使用同一个对象，但是不同对象里面包含相同的属性和方法

答案：构造函数    new 每次都会创建一个新的对象

**5. 继承写法完善**

```javascript
  <script>    // 继续抽取   公共的部分放到原型上    // 构造函数  new 出来的对象 结构一样，但是对象不一样    function Person() {      this.eyes = 2      this.head = 1    }    // console.log(new Person)    // 女人  构造函数   继承  想要 继承 Person    function Woman() {     }    // Woman 通过原型来继承 Person    // 父构造函数（父类）   子构造函数（子类）    // 子类的原型 =  new 父类      Woman.prototype = new Person()   // {eyes: 2, head: 1}     // 指回原来的构造函数    Woman.prototype.constructor = Woman     // 给女人添加一个方法  生孩子    Woman.prototype.baby = function () {      console.log('宝贝')    }    const red = new Woman()    console.log(red)    // console.log(Woman.prototype)    // 男人 构造函数  继承  想要 继承 Person    function Man() {     }    // 通过 原型继承 Person    Man.prototype = new Person()    Man.prototype.constructor = Man    const pink = new Man()    console.log(pink)  </script>
```

#### 8.6 原型链

基于原型对象的继承使得不同构造函数的原型对象关联在一起，并且这种关联的关系是一种链状的结构，我们将原型对象的链状结构关系称为 **原型链** ![](https://i-blog.csdnimg.cn/blog_migrate/07513e7f65a7031d453c272aa143fd3c.png)

**原型链-查找规则**

① 当访问一个对象的属性（包括方法）时，首先查找这个 对象自身 有没有该属性。

② 如果没有就查找它的原型（也就是 __proto__指向的 prototype 原型对象 ）

③ 如果还没有就查找原型对象的原型（ Object的原型对象 ）

④ 依此类推一直找到 Object 为止（ null ）

⑤ __proto__对象原型的意义就在于为对象成员查找机制提供一个方向，或者说一条路线

⑥ 可以使用 instanceof 运算符用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上

```javascript
  <script>    // function Objetc() {}    console.log(Object.prototype)    console.log(Object.prototype.__proto__)     function Person() {     }    const ldh = new Person()    // console.log(ldh.__proto__ === Person.prototype)    // console.log(Person.prototype.__proto__ === Object.prototype)    console.log(ldh instanceof Person)    console.log(ldh instanceof Object)    console.log(ldh instanceof Array)    console.log([1, 2, 3] instanceof Array)    console.log(Array instanceof Object)  </script></body>
```

### 综合案例：消息提示对象封装

```html
<body>    <button id="delete">删除</button>    <button id="login">登录</button>     <!-- <div class="modal">    <div class="header">温馨提示 <i>x</i></div>    <div class="body">您没有删除权限操作</div>  </div> -->      <script>        // 1.  模态框的构造函数        function Modal(title = '', message = '') {            // 创建 modal 模拟框盒子            // 1.1 创建 div 标签            this.modalBox = document.createElement('div')            // 1.2 给 div 标签添加类名为 modal            this.modalBox.className = 'modal'            // 1.3 modal 盒子内部填充 2个 div 标签并且修改文字内容            this.modalBox.innerHTML = `                <div class="header">${title}<i>x</i></div>                <div class="body">${message}</div>            `        }         // 2.给构造函数原型对象挂载 open 方法        Modal.prototype.open = function () {            // 先来判断页面中是否有 modal 盒子，如果有先删除，否则继续添加            const box = document.querySelector('.modal')            box && box.remove()            // 注意这个方法不要用箭头函数            // 把刚才创建的 modalBox 显示到页面 body 中            document.body.append(this.modalBox)             // 要等着盒子显示出来，就可以绑定点击事件了            this.modalBox.querySelector('i').addEventListener('click', () => {                // 这个地方需要用到箭头函数                // 这个 this 指向实例对象                this.close()            })        }         // 3. 关闭方法 挂载 到 模态框的构造函数原型身上        Modal.prototype.close = function () {            this.modalBox.remove()        }         // 4. 按钮点击        document.querySelector('#delete').addEventListener('click', () => {            const m = new Modal('温馨提示', '您没有权限删除')            // 调用 打开方法            m.open()        })         // 5. 按钮点击        document.querySelector('#login').addEventListener('click', () => {            const m = new Modal('友情提示', '您还么有注册账号')            // 调用 打开方法            m.open()        })     </script></body>
```

### 9.深浅拷贝

#### 9.1 浅拷贝

浅拷贝：拷贝的是地址

**常见方法：**

1. 拷贝对象：Object.assgin() / 展开运算符 {...obj} 拷贝对象

2.拷贝数组：Array.prototype.concat() 或者 [...arr]

```javascript
  <script>    const obj = {      uname: 'pink',      age: 18,      family: {        baby: '小pink'      }    }    // 浅拷贝    // const o = { ...obj }    // console.log(o)    // o.age = 20    // console.log(o)    // console.log(obj)    const o = {}    Object.assign(o, obj)    o.age = 20    o.family.baby = '老pink'    console.log(o)    console.log(obj)  </script>
```

如果是 简单数据类型拷贝值，引用数据类型拷贝的是地址 (简单理解： 如果是单层对象，没问题，如果有多层就有问题)

**总结：**

1. 直接赋值和浅拷贝有什么区别？

        直接赋值的方法，只要是对象，都会相互影响，因为是直接拷贝对象栈里面的地址

        浅拷贝如果是一层对象，不相互影响，如果出现多层对象拷贝还会相互影响

2. 浅拷贝怎么理解？

        拷贝对象之后，里面的属性值是简单数据类型直接拷贝值

        如果属性值是引用数据类型则拷贝的是地址

#### 9.2 深拷贝

深拷贝：拷贝的是对象，不是地址

**常见方法：**

**1.** **通过递归实现深拷贝**

**函数递归：**

如果一个函数在内部可以调用其本身，那么这个函数就是递归函数

简单理解:函数内部自己调用自己， 这个函数就是递归函数

递归函数的作用和循环效果类似

由于递归很容易发生“栈溢出”错误（stack overflow），所以 必须要加退出条件 return

**利用递归函数实现 setTimeout 模拟 setInterval效果**

```html
<body>  <div></div>  <script>    function getTime() {      document.querySelector('div').innerHTML = new Date().toLocaleString()      setTimeout(getTime, 1000)    }    getTime()  </script></body>
```

**通过递归函数实现深拷贝（简版）**

```javascript
  <script>    const obj = {      uname: 'pink',      age: 18,      hobby: ['乒乓球', '足球'],      family: {        baby: '小pink'      }    }    const o = {}    // 拷贝函数    function deepCopy(newObj, oldObj) {      debugger      for (let k in oldObj) {        // 处理数组的问题  一定先写数组再写对象 不能颠倒  因为数组属于对象        if (oldObj[k] instanceof Array) {          newObj[k] = []          //  newObj[k] 接收 []  hobby          //  oldObj[k]   ['乒乓球', '足球']          deepCopy(newObj[k], oldObj[k])        } else if (oldObj[k] instanceof Object) {          newObj[k] = {}          deepCopy(newObj[k], oldObj[k])        }        else {          //  k  属性名 uname age    oldObj[k]  属性值  18          // newObj[k]  === o.uname  给新对象添加属性          newObj[k] = oldObj[k]        }      }    }    deepCopy(o, obj) // 函数调用  两个参数 o 新对象  obj 旧对象    console.log(o)    o.age = 20    o.hobby[0] = '篮球'    o.family.baby = '老pink'    console.log(obj)    console.log([1, 23] instanceof Object)  </script>
```

**2. js库lodash里面cloneDeep内部实现了深拷贝**

**lodash官网：**[Lodash 简介 | Lodash中文文档 | Lodash中文网](https://www.lodashjs.com/ "Lodash 简介 | Lodash中文文档 | Lodash中文网")

```javascript
<body>  <!-- 先引用 -->  <script src="./lodash.min.js"></script>  <script>    const obj = {      uname: 'pink',      age: 18,      hobby: ['乒乓球', '足球'],      family: {        baby: '小pink'      }    }    const o = _.cloneDeep(obj)    console.log(o)    o.family.baby = '老pink'    console.log(obj)  </script></body>
```

**3. 通过JSON.stringify()实现**

```javascript
  <script>    const obj = {      uname: 'pink',      age: 18,      hobby: ['乒乓球', '足球'],      family: {        baby: '小pink'      }    }    // 把对象转换为 JSON 字符串    // console.log(JSON.stringify(obj))    const o = JSON.parse(JSON.stringify(obj))    console.log(o)    o.family.baby = '123'    console.log(obj)  </script>
```

**总结：**

**实现深拷贝三种方式：**

1.自己利用递归函数书写深拷贝

2.利用js库 lodash里面的 _.cloneDeep()

3.利用JSON字符串转换

### 10.异常处理

#### 10.1 throw 抛异常 

异常处理是指预估代码执行过程中可能发生的错误，然后最大程度的避免错误的发生导致整个程序无法继续运行。

![](https://i-blog.csdnimg.cn/blog_migrate/f7edac915d131b0ad574105ea89019dc.png)![](https://i-blog.csdnimg.cn/blog_migrate/cd125871e4df08f626b7cb3f72f5a129.png)

**总结：**  
1. throw 抛出异常信息，程序也会终止执行  
2. throw 后面跟的是错误提示信息  
3. Error 对象配合 throw 使用，能够设置更详细的错误信息

#### **10.2 try/catch** 捕获错误信息

我们可以通过try / catch 捕获错误信息（浏览器提供的错误信息） 

```html
<body>  <p>123</p>  <script>    function fn() {      try {        // 可能发送错误的代码 要写到 try        const p = document.querySelector('.p')        p.style.color = 'red'      } catch (err) {        // 拦截错误，提示浏览器提供的错误信息，但是不中断程序的执行        console.log(err.message)        throw new Error('你看看，选择器错误了吧')        // 需要加return 中断程序        return      }      finally {        // 不管你程序对不对，一定会执行的代码        alert('弹出对话框')      }      console.log(11)    }    fn()  </script></body>
```

**总结：**  
1. try...catch 用于捕获错误信息  
2. 将预估可能发生错误的代码写在 try 代码段中  
3. 如果 try 代码段中出现错误后，会执行 catch 代码段，并截获到错误信息，利用catch的参数可以调用错误信息  
4. finally 不管是否有错误，都会执行

#### 10.3 debugger

debugger：停止 JavaScript 的执行，相当于设置断点。![](https://i-blog.csdnimg.cn/blog_migrate/4ac899b4b544bd3b34c1d6ffd8ed92b5.png)

### 11. 处理this 

this 是 JavaScript 最具“魅惑”的知识点，不同的应用场合 this 的取值可能会有意想不到的结果，在此我们对以往学习过的关于【 this 默认的取值】情况进行归纳和总结。

#### 11.1 this指向-普通函数

普通函数的调用方式决定了 this 的值，即【谁调用 this 的值指向谁】

普通函数没有明确调用者时 this 值为 window，严格模式下没有调用者时 this 的值为 undefined

#### 11.1 this指向-箭头函数

箭头函数中的 this 与普通函数完全不同，不受调用方式的影响，事实上**箭头函数中并不存在 this**  
1. 箭头函数会默认帮我们绑定外层 this 的值，所以在箭头函数中 this 的值和外层的 this 是一样的  
2.箭头函数中的this引用的就是最近作用域中的this  
3.向外层作用域中，一层一层查找this，直到有this的定义

**注意情况1：**  
在开发中【使用箭头函数前需要考虑函数中 this 的值】，事件回调函数使用箭头函数时，this 为全局的 window，因此DOM事件回调函数如果里面需要DOM对象的this，则不推荐使用箭头函数

**注意情况2：**  
同样由于箭头函数 this 的原因，基于原型的面向对象也不推荐采用箭头函数

**总结：**  
1. 函数内不存在this，沿用上一级的。过程：向外层作用域中一层一层查找this，直到有this的定义  
2.**不适用： 构造函数，原型函数，dom事件函数**等等  
3. **适用： 需要使用上层this的地方**  
2. 使用正确的话，它会在很多地方带来方便，后面我们会大量使用慢慢体会

#### 11.2 改变this

**1. call() –了解**  
使用 call 方法调用函数，同时指定被调用函数中 this 的值  
**语法：**fun.call(thisArg, arg1, arg2, ...)   
**●** thisArg：在 fun 函数运行时指定的 this 值  
**●** arg1，arg2：传递的其他参数  
**返回值就是函数的返回值**，因为它就是调用函数

```javascript
  <script>    const obj = {      uname: 'pink'    }    function fn(x, y) {      console.log(this) // window      console.log(x + y)    }    // 1. 调用函数      // 2. 改变 this 指向    fn.call(obj, 1, 2)  </script>
```

**2. apply()-理解**  
使用 apply 方法调用函数，同时指定被调用函数中 this 的值  
**语法：**fun.apply(thisArg, [argsArray])  
**●** thisArg：在fun函数运行时指定的 this 值  
**●** argsArray：传递的值，**必须包含在数组里面**  
**返回值就是函数的返回值**，因为它就是调用函数  
因此 **apply 主要跟数组有关系**，比如使用 Math.max() 求数组的最大值

```javascript
  <script>    const obj = {      age: 18    }    function fn(x, y) {      console.log(this) // {age: 18}      console.log(x + y)    }    // 1. 调用函数    // 2. 改变this指向     //  fn.apply(this指向谁, 数组参数)    fn.apply(obj, [1, 2])    // 3. 返回值   本身就是在调用函数，所以返回值就是函数的返回值     // 使用场景： 求数组最大值    // const max = Math.max(1, 2, 3)    // console.log(max)    const arr = [100, 44, 77]    const max = Math.max.apply(Math, arr)    const min = Math.min.apply(null, arr)    console.log(max, min)    // 使用场景： 求数组最大值    console.log(Math.max(...arr))  </script>
```

**call和apply的区别：**  
**●** 都是调用函数，都能改变this指向  
**●** 参数不一样，apply传递的必须是数组

**3. bind()-重点**  
bind() 方法不会调用函数。但是能改变函数内部this 指向  
**语法：**fun.bind(thisArg, arg1, arg2, ...)  
**●**  thisArg：在 fun 函数运行时指定的 this 值  
**●**  arg1，arg2：传递的其他参数  
**返回 由指定的 this 值和初始化参数改造的 原函数拷贝 （新函数）**  
因此当我们只是想改变 this 指向，并且不想调用这个函数的时候，可以使用 bind，比如改变定时器内部的this指向

```html
<body>  <button>发送短信</button>  <script>    const obj = {      age: 18    }    function fn() {      console.log(this)    }     // 1. bind 不会调用函数     // 2. 能改变this指向    // 3. 返回值是个函数，  但是这个函数里面的this是更改过的obj    const fun = fn.bind(obj)    // console.log(fun)     fun()     // 需求，有一个按钮，点击里面就禁用，2秒钟之后开启    document.querySelector('button').addEventListener('click', function () {      // 禁用按钮      this.disabled = true      window.setTimeout(function () {        // 在这个普通函数里面，我们要this由原来的window 改为 btn        this.disabled = false      }.bind(this), 2000)   // 这里的this 和 btn 一样    })  </script></body>
```

**call apply bind 总结**  
**相同点：**都可以改变函数内部的this指向.  
**区别点：**  
**●**  call 和 apply 会调用函数, 并且改变函数内部this指向.  
**●**  call 和 apply 传递的参数不一样, call 传递参数 aru1, aru2..形式 apply 必须数组形式[arg]  
**●**  bind 不会调用函数, 可以改变函数内部this指向.  
**主要应用场景：**  
**●**  call 调用函数并且可以传递参数  
**●**  apply 经常跟数组有关系. 比如借助于数学对象实现数组最大值最小值  
**●**  bind 不调用函数,但是还想改变this指向. 比如改变定时器内部的this指向

### 12. 性能优化

#### 12.1 防抖（debounce）

**所谓防抖，就是指触发事件后在 n 秒内函数只能执行一次，如果在 n 秒内又触发了事件，则会重新计算函数执行时间。**

**开发使用场景- 搜索框防抖**  
假设输入就可以发送请求，但是不能每次输入都去发送请求，输入比较快发送请求会比较多  
我们设定一个时间，假如300ms， 当输入第一个字符时候，300ms后发送请求，但是在200ms的时候又输入了一个字符，则需要再等300ms 后发送请求

**案例：利用防抖来处理-鼠标滑过盒子显示文字**

```html
<body>  <div class="box"></div>  <script>    const box = document.querySelector('.box')    let i = 1  // 让这个变量++    // 鼠标移动函数    function mouseMove() {      box.innerHTML = ++i      // 如果里面存在大量操作 dom 的情况，可能会卡顿    }    // 防抖函数    function debounce(fn, t) {      let timeId      return function () {        // 如果有定时器就清除        if (timeId) clearTimeout(timeId)        // 开启定时器 200        timeId = setTimeout(function () {          fn()        }, t)      }    }    // box.addEventListener('mousemove', mouseMove)    box.addEventListener('mousemove', debounce(mouseMove, 200))  </script></body>
```

#### 12.2 节流（throttle）

**所谓节流，就是指连续触发事件但是在 n 秒中只执行一次函数**

**开发使用场景 – 小米轮播图点击效果 、 鼠标移动、页面尺寸缩放resize、滚动条滚动**可以加节流

**案例：利用节流来处理-鼠标滑过盒子显示文字**

```html
<body>  <div class="box"></div>  <script>    const box = document.querySelector('.box')    let i = 1  // 让这个变量++    // 鼠标移动函数    function mouseMove() {      box.innerHTML = ++i      // 如果里面存在大量操作 dom 的情况，可能会卡顿    }    // 节流函数 throttle     function throttle(fn, t) {      // 起始时间      let startTime = 0      return function () {        // 得到当前的时间        let now = Date.now()        // 判断如果大于等于 500 采取调用函数        if (now - startTime >= t) {          // 调用函数          fn()          // 起始的时间 = 现在的时间   写在调用函数的下面           startTime = now        }      }    }    box.addEventListener('mousemove', throttle(mouseMove, 500)  </script></body>
```

**总结：**

**1.节流和防抖的区别是？**  
●  节流：就是指连续触发事件但是在 n 秒中只执行一次函数,比如可以利用节流实现 1s之内 只能触发一次鼠标移动事件  
●  防抖：如果在 n 秒内又触发了事件，则会重新计算函数执行时间  
**2. 节流和防抖的使用场景是？  
●**  节流：鼠标移动，页面尺寸发生变化，滚动条滚动等开销比较大的情况下  
●  防抖：搜索框输入，设定每次输入完毕n秒后发送请求，如果期间还有输入，则从新计算时间

#### Lodash 库 实现节流和防抖

#### ![](https://i-blog.csdnimg.cn/blog_migrate/3f55b2ecb5059c6641170f64a86097b9.png)

### 节流综合案例：页面打开，可以记录上一次的视频播放位置 

**两个事件:**  
①：ontimeupdate 事件在视频/音频（audio/video）当前的播放位置发送改变时触发  
②：onloadeddata 事件在当前帧的数据加载完成且还没有足够的数据播放视频/音频（audio/video）的下一帧时触发

```html
<body>    <div class="container">        <div class="header">            <a href="http://pip.itcast.cn">                <img src="https://pip.itcast.cn/img/logo_v3.29b9ba72.png" alt="" />            </a>        </div>        <div class="video">            <video src="https://v.itheima.net/LapADhV6.mp4" controls></video>        </div>        <div class="elevator">            <a href="javascript:;" data-ref="video">视频介绍</a>            <a href="javascript:;" data-ref="intro">课程简介</a>            <a href="javascript:;" data-ref="outline">评论列表</a>        </div>    </div>    <script src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>    <script>        // 1. 获取元素  要对视频进行操作        const video = document.querySelector('video')        video.ontimeupdate = _.throttle(() => {            // console.log(video.currentTime)  获得当前的视频时间            // 把当前的时间存储到本地存储            localStorage.setItem('currentTime', video.currentTime)        }, 1000)         // 打开页面触发事件，就从本地存储里面取出记录的时间，赋值给 video.currentTime        video.onloadeddata = () => {            video.currentTime = localStorage.getItem('currentTime') || 0        }    </script></body>
```

[![](https://profile-avatar.csdnimg.cn/6c38e4e6226745daa8478665f39b8f06_weixin_59531237.jpg!1)zhuie_](https://blog.csdn.net/weixin_59531237)

关注

-