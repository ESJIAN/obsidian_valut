## JavaScript

JavaScript 是一种轻量级的编程语言(“脚本语言”)，用于使网页具有交互性。 它可以将动态文本插入 [HTML](https://geek-docs.com/html/html-top-tutorials/1000100_html_index.html "HTML 教程")。 JavaScript 也被称为浏览器的语言。 JavaScript(JS) 与 Java 不相似或不相关。 这两种语言都具有类似 C 的语法，并广泛用于客户端和服务器端 Web 应用程序，但只有很少的相似之处。==也就是我们过去常说的脚本==

**Javascript的特点：**

- JavaScript 最初是为 DOM 操作而创建的。 早期的网站大多是静态的，在创建 JS 之后制作动态网站。
- JS中的函数是对象。它们可能像另一个对象一样具有属性和方法。 它们可以作为其他函数的参数传递。
- 可以处理日期和时间。
- 尽管表单是使用 [HTML](https://geek-docs.com/html/html-top-tutorials/1000100_html_index.html "HTML 教程") 创建的，但执行表单验证。
- 不需要编译器。

**示例：** 这是基本的 Javascript 示例。

```javascript
<script>
    console.log("Welcome to Yiibai Learning");
</script>
```



运行结果：

```java
Welcome to Yiibai Learning
```

## Java

**Java的特点：**

- 平台无关：编译器将源代码转换为字节码，然后 JVM 执行编译器生成的字节码。 这个字节码可以在任何平台上运行。
- 面向对象编程语言：按照对象集合来组织程序是面向对象编程的一种方式，每个对象代表一个类的实例。 OOP 的概念有 4 个支柱：
    - 抽象
    - 封装
    - 继承
    - 多态性
- 简单：Java 是一种简单的语言，因为它没有指针、运算符重载、多重继承、显式内存分配等复杂功能。
    
- 健壮：Java 语言健壮，这意味着可靠。 它的开发方式是尽可能早地检查错误，这就是为什么 java 编译器能够检测到其他编程语言不容易检测到的错误。
    
- 安全：在 java 中，我们没有指针，因此我们无法访问越界数组，即如果我们尝试这样做，它会显示 ArrayIndexOutOfBound 异常。
- 分布式：我们可以使用 java 编程语言创建分布式应用程序。 远程方法调用和企业 Java Bean 用于在 Java 中创建分布式应用程序。
- 多线程：Java 支持多线程。 它是一种 Java 功能，允许同时执行程序的两个或多个部分，以最大限度地利用 CPU。

**示例：** 下面是一个简单的 Java 程序。

```java
import java.io.*;

class GFG {
    public static void main(String[] args)
    {
        System.out.println(
            "Welcome to Yiibai Learning");
    }
}
```



运行结果：

```java
Welcome to Yiibai Learning
```


Java 和 JavaScript 的区别如下：

|Java|JavaScript|
|---|---|
|Java 是一种强类型语言，必须首先声明变量才能在程序中使用。在 Java 中，变量的类型是在编译时检查的。|JavaScript 是一种弱类型语言，具有更宽松的语法和规则。|
|Java 是一种面向对象的编程语言。|JavaScript 是一种基于对象的脚本语言。|
|Java 应用程序可以在任何虚拟机 (JVM) 或浏览器中运行。|JavaScript 代码过去只能在浏览器中运行，但现在它可以通过 [Node.js](https://geek-docs.com/nodejs/node-js-top-tutorials/1001100_nodejs_index.html "Node.js 教程") 在服务器上运行。|
|Java的对象是基于类的，即使我们不能在不创建类的情况下用Java编写任何程序。|JavaScript 对象是基于原型的。|
|Java程序具有文件扩展名“.Java”，并将源代码转换为由JVM(Java虚拟机)执行的字节码。|JavaScript 文件的文件扩展名为“.js”，它被解释但不被编译，每个浏览器都有 Javascript 解释器来执行 JS 代码。|
|Java 是一种独立语言。|Javascript包含在网页中并与其 HTML 内容集成。|
|Java 有一种基于线程的并发方法。|Javascript 有一种基于事件的并发方法。|
|Java 支持多线程。|Javascript 不支持多线程。|