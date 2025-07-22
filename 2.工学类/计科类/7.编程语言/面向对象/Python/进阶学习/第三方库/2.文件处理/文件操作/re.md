---
title: re库
author: 
published: https://geekdaxue.co/
tags:
  - Python
  - 库函数
---




re模块主要定义了9个常量、12个函数、1个异常  
![re模块 - 图1](https://geekdaxue.co/read/guangleduo@hgl31z/4164004D79A9460A912EB261127A002C#alt=image) 

## 一、re模块简介

re模块是python处理文本的标准库

> 标准库是python内置模块，不需要额外下自，目前python内置模块大概300个，可以通过以下链接查看python所有内置模块：[https://docs.python.org/3/py-modindex.html#cap-r](https://docs.python.org/3/py-modindex.html#cap-r)

re模块官方文档：[https://docs.python.org/zh-cn/3.8/library/re.html](https://docs.python.org/zh-cn/3.8/library/re.html)  
re模块库源码：[https://github.com/python/cpython/blob/3.8/Lib/re.py](https://github.com/python/cpython/blob/3.8/Lib/re.py) 

## 二、re模块常量

re模块中有9个常量，常量的值都是 int类型 ！  
![re模块 - 图2](https://geekdaxue.co/read/guangleduo@hgl31z/908DB61E14C94C7D8175C6987A254D9C#alt=image)  
所有的常量都是在RegexFlag枚举类 来实现，这是在Python 3.6做的改版。在Python 3.6以前版本是直接将常量写在re.py中，使用枚举的好处就是方便管理和使用！  
![re模块 - 图3](https://geekdaxue.co/read/guangleduo@hgl31z/C0153D7CB39D41879538198C7D0ABF95#alt=image) 

### 1. IGNORECCAS

**语法：** re.IGNORECASE或简写为re.I  
**作用：** 进行忽略大小写匹配  
![re模块 - 图4](https://geekdaxue.co/read/guangleduo@hgl31z/DCBB987F790D4A3DB89FBD203C7F19F3#alt=image) 

### 2.ASCII

**语法：** re.ASCII 或简写为 re.A  
**作用：** 顾名思义，ASCII表示ASCII码的意思，让 \w, \W, \b, \B, \d, \D, \s 和 \S 只匹配ASCII，而不是Unicode。  
![re模块 - 图5](https://geekdaxue.co/read/guangleduo@hgl31z/9714F5F949504BD1BA93FEE9A41EF18A#alt=image)

> 注意：这只对字符串匹配模式有效，对字节匹配模式无效

### 3.DOTALL

**语法：** re.DOTALL 或简写为 re.S  
**作用：** DOT表示.，ALL表示所有，连起来就是.匹配所有，包括换行符\n。默认模式下.是不能匹配行符\n的。  
![re模块 - 图6](https://geekdaxue.co/read/guangleduo@hgl31z/64BE62726B28413D97C1915CA374367E#alt=image)

> 注意：默认匹配模式下.并不会匹配换行符\n

### 4.MULTILINE

**语法：** re.MULTILINE 或简写为 re.M  
**作用：** 多行模式，当某字符串中有换行符\n，默认模式下是不支持换行符特性的，比如：行开头 和 行结尾，而多行模式下是支持匹配行开头的。  
![re模块 - 图7](https://geekdaxue.co/read/guangleduo@hgl31z/2E74685273FE46F4AFA155486E640C7F#alt=image)  
正则表达式中^表示匹配行的开头，默认模式下它只能匹配字符串的开头；而在多行模式下，它还可以匹配 换行符\n后面的字符。

> 注意：正则语法中^匹配行开头、\A匹配字符串开头，单行模式下它两效果一致，多行模式下\A不能识别\n。

### 5.VERBOSE

**语法：** re.VERBOSE 或简写为 re.X  
**作用：** 详细模式，可以在正则表达式中加注解！  
![re模块 - 图8](https://geekdaxue.co/read/guangleduo@hgl31z/0181941E943D478381CFEBB31AADCFFF#alt=image)  
默认模式下并不能识别正则表达式中的注释，而详细模式是可以识别的。  
当一个正则表达式十分复杂的时候，详细模式或许能为你提供另一种注释方式，但它不应该成为炫技的手段，建议谨慎考虑后使用！

### 6.LOCALE

**语法：** re.LOCALE 或简写为 re.L  
**作用：** 由当前语言区域决定 \w, \W, \b, \B 和大小写敏感匹配，这个标记只能对byte样式有效。这个标记官方已经不推荐使用，因为语言区域机制很不可靠，它一次只能处理一个 “习惯”，而且只对8位字节有效。

### 7.UNICODE

**语法：** re.UNICODE 或简写为 re.U  
**作用：** 与 ASCII 模式类似，匹配unicode编码支持的字符，但是 Python 3 默认字符串已经是Unicode，所以有点冗余。

### 8.DEBUG

**语法：** re.DEBUG  
**作用：** 显示编译时的debug信息。  
![re模块 - 图9](https://geekdaxue.co/read/guangleduo@hgl31z/CEB08230A3684CABB64BF7F963D372DB#alt=image) 

### 9.TEMPLATE

**语法：** re.TEMPLATE 或简写为 re.T  
**作用：** 源码注释中写着：disable backtracking(禁用回溯)  
![re模块 - 图10](https://geekdaxue.co/read/guangleduo@hgl31z/578A8D1F6D714736B16604C589458CDE#alt=image) 

### 10.常量总结

1. 9个常量中，前5个（IGNORECASE、ASCII、DOTALL、MULTILINE、VERBOSE）有用处，两个（LOCALE、UNICODE）官方不建议使用、两个（TEMPLATE、DEBUG）试验性功能，不能依赖。
2. 常量在re常用函数中都可以使用，查看源码可得知。

![re模块 - 图11](https://geekdaxue.co/read/guangleduo@hgl31z/61920D6EDCC1458DA5A910DFCE63727B#alt=image)  
![re模块 - 图12](https://geekdaxue.co/read/guangleduo@hgl31z/2A64585A79D049668CF2446332280D6E#alt=image) 

## 三、re模块函数

>**引言**：在介绍模块函数前，前补充以下有关于通配符的介绍

![](https://ask.qcloudimg.com/http-save/yehe-9949496/e3b78396c3047aabe75f9ee67165de58.png)

![](https://ask.qcloudimg.com/http-save/yehe-9949496/36cde71e97547861638e6ded9512e0a9.png)


![](https://ask.qcloudimg.com/http-save/yehe-9949496/306a39b1f9403ab72c25e8f29a120c8a.png)

- `re.sub(r'(?<=[\u4e00-\u9fa5])|(?=[\u4e00-\u9fa5])', '', i.name)`：

### **3.1 正则表达式的表示**

（1）原生字符串类型

Re库采用raw string类型表示正则表达式，表示为：`r'text'`。

例如：`r'[1-9]\d{5}'`，`r'\d{3}-\d{8}|\d{4}-\d{7}'`

raw string是指不包含对转义符再次转义的字符串。

（2）string类型

Re库也可以采用string类型表示正则表达式，但更繁琐。

例如：`'[1-9]\\d{5}'`，`'\\d{3}-\\d{8}|\\d{4}-\\d{7}'`

**建议**：当正则表达式包含转义符时，使用raw string。

### **3.2 Re库主要功能函数**

![](https://ask.qcloudimg.com/http-save/yehe-9949496/7b73e4ae3ce8bba59ee4a7825dee2da1.png)

#### **3.2.1 re.search(pattern, string, flags=0)**

在一个字符串中搜索匹配正则表达式的第一个位置，返回match对象。

- pattern: 正则表达式的字符串或原生字符串表示；
- string: 待匹配字符串；
- flags: 正则表达式使用时的控制标记。

![](https://ask.qcloudimg.com/http-save/yehe-9949496/2a1821b3a8524171a43df7b2386ba49a.png)

```javascript
import rematch = re.search(r'[1-9]\d{5}','BIT 100081')
if match:
    print(match.group(0))
```

```javascript
100081
```

#### **3.2.2 re.match(pattern, string, flags=0)**

从一个字符串的开始位置起匹配正则表达式，返回match对象。

```javascript
import re
match = re.match(r'[1-9]\d{5}','BIT 100081')
if match:
    print(match.group(0))
type(match)
```

```javascript
NoneType
```

```javascript
import re
match = re.match(r'[1-9]\d{5}','100081 BIT')
if match:
    print(match.group(0))
```

```javascript
100081
```

#### **3.2.3 re.findall(pattern, string, flags=0)**

搜索字符串，以列表类型返回全部能匹配的子串。

```javascript
import re
ls = re.findall(r'[1-9]\d{5}','BIT100081 TSU100084')
ls
```

```javascript
['100081', '100084']
```

#### **3.2.4 re.split(pattern, string, maxsplit=0, flags=0)**

将一个字符串按照正则表达式匹配结果进行分割，返回列表类型。

- maxsplit: 最大分割数，剩余部分作为最后一个元素输出。

```javascript
import re
re.split(r'[1-9]\d{5}','BIT100081 TSU100084')
```

```javascript
['BIT', ' TSU', '']
```

```javascript
import re
re.split(r'[1-9]\d{5}', 'BIT100081 TSU100084', maxsplit=1)
```

```javascript
['BIT', ' TSU100084']
```

#### **3.2.5 re.finditer(pattern, string, flags=0)**

搜索字符串，返回一个匹配结果的迭代类型，每个迭代元素是match对象。

```javascript
import re
for m in re.finditer(r'[1-9]\d{5}', 'BIT100081 TSU100084'):
    if m:
        print(m.group(0))
```

```javascript
100081
100084
```

#### **3.2.6 re.sub(pattern, repl, string, count=0, flags=0)**

在一个字符串中替换所有匹配正则表达式的子串，返回替换后的字符串。

- repl: 替换匹配字符串的字符串；
- count: 匹配的最大替换次数。

```javascript
import re
re.sub(r'[1-9]\d{5}', ':zipcode', 'BIT100081 TSU100084')
```

```javascript
'BIT:zipcode TSU:zipcode'
```

### **3.3 Re库的另一种等价用法**

（1）函数式用法：一次性操作

```javascript
rst = re.search(r'[1-9]\d{5}','BIT 100081')
```

（2）面向对象用法：编译后的多次操作

```javascript
pat = re.compile(r'[1-9]\d{5}')
rst = pat.search('BIT 100081')
```

`regex = re.compile(pattern， flags=0)` 将正则表达式的字符串形式编译成正则表达式对象。

```javascript
regex = re.compile(r'[1-9]\d{5}')
```

![](https://ask.qcloudimg.com/http-save/yehe-9949496/c1b02d61f15e14d5a42cbb572680859a.png)

### **3.4 Re库的match对象**

Match对象是一次匹配的结果，包含匹配的很多信息。

```javascript
import re
match = re.search(r'[1-9]\d{5}','BIT 100081')
if match:
    print(match.group(0))
print(type(match))
```

```javascript
100081
<class 're.Match'>
```

Match对象的属性：

![](https://ask.qcloudimg.com/http-save/yehe-9949496/41b6b17e95f9e3e54dda868edb4926a8.png)

Match对象的方法：

![](https://ask.qcloudimg.com/http-save/yehe-9949496/402ed03db86a7e4952f73fcff88aa5ac.png)

```javascript
import re
m = re.search(r'[1-9]\d{5}','BIT100081 TSU100084')
print("String:",m.string)
print("Pattern:",m.re)
print("Pos_ini:",m.pos)
print("Pos_end:",m.endpos)

print("Acq_string:",m.group(0))
print("Acq_ini:",m.start())
print("Acq_end:",m.end())
print("Acq_span:",m.span())
```

```javascript
String: BIT100081 TSU100084
Pattern: re.compile('[1-9]\\d{5}')
Pos_ini: 0
Pos_end: 19
Acq_string: 100081
Acq_ini: 3
Acq_end: 9
Acq_span: (3, 9)
```

### **3.5 Re库的贪婪匹配与最小匹配**

```javascript
import re
m = re.search(r'PY.*N','PYANBN')
if m:
    print(m.group(0))
```

```javascript
PYANBN
```

Re库默认采用贪婪匹配，即输出匹配最长的子串。

```javascript
import re
m = re.search(r'PY.*?N','PYANBN')
if m:
    print(m.group(0))
```

```javascript
PYAN
```

最小匹配字符串：

![](https://ask.qcloudimg.com/http-save/yehe-9949496/ba2633e8951a7802ed27f4a4af5f5250.png)

只要长度输出可能不同的，都可以通过在操作符后面增加`？`变成最小匹配。

## 四、re模块异常

re模块还包含了一个正则表达式的编译错误，**当我们给出的正则表达式是一个无效的表达式**（就是表达式本身有问题）时，就会raise一个异常！  
![re模块 - 图27](https://geekdaxue.co/read/guangleduo@hgl31z/E2D9118B8D1A47068F1A2037043C9BFC#alt=image)  
上图案例中我们可以看到，在编写正则表达式中我们多写了一个后括号，这导致执行结果报错；而且是在其他所有案例执行之前，所以说明是在正则表达式编译时期就报错了。

> 注意：这个异常一定是 正则表达式 本身是无效的，与要匹配的字符串无关！

## 五、正则对象Pattern

关于re模块的常量、函数、异常我们都讲解完毕，但是完全有必要再讲讲**正则对象Pattern**。

### 1. 与re模块 函数一致

在re模块的函数中有一个重要的函数 compile函数 ，这个函数可以预编译返回一个正则对象，此正则对象拥有与re模块相同的函数，我们来看看Pattern类的源码。  
![re模块 - 图28](https://geekdaxue.co/read/guangleduo@hgl31z/D6A863DE0AFD4B1EB9B89E52D35A21A0#alt=image)  
![re模块 - 图29](https://geekdaxue.co/read/guangleduo@hgl31z/8EC5B7377CE64AC6A01C9E29FAA82534#alt=image)  
也就是说下面 两种代码写法底层实现 其实是一致的：

1. `# re函数`
2. `re.search(pattern, text)`

3. `# 正则对象函数`
4. `compile = re.compile(pattern)`
5. `compile.search(text)`

那还有必要使用compile函数 得到正则对象再去调用 search函数 吗？直接调用re.search 是不是就可以？

### 2.官方文档

关于到底该用re模块 还是 正则对象Pattern ，官方文档是否有说明呢？  
![re模块 - 图30](https://geekdaxue.co/read/guangleduo@hgl31z/33940FADF97148C084A6085EC619FF60#alt=image) 

### 3.实际测试

上面官方文档推荐我们在 **多次使用某个正则表达式时使用正则对象**，那实际情况真的是这样的吗？  
![re模块 - 图31](https://geekdaxue.co/read/guangleduo@hgl31z/C134561D62124BDA9CFEEC8F27610FE3#alt=image)  
![re模块 - 图32](https://geekdaxue.co/read/guangleduo@hgl31z/1B2BBFD24F964D4E860F975B55A3B2E1#alt=image) 

## 六、注意事项

### 2.r的作用

正则表达式使用反斜杠（’\’）来表示特殊形式，或者把特殊字符转义成普通字符。

而反斜杠在普通的 Python 字符串里也有相同的作用，所以就产生了冲突。

解决办法是对于正则表达式样式使用 Python 的原始字符串表示法；在带有 ‘r’ 前缀的字符串字面值中，反斜杠不必做任何特殊处理。

### 3.正则查找函数 返回匹配对象

查找一个匹配项（search、match、fullmatch）的函数返回值都是一个 匹配对象Match ，需要通过match.group() 获取匹配值，这个很容易忘记。  
![re模块 - 图33](https://geekdaxue.co/read/guangleduo@hgl31z/7F0AFB803D1E427C8B71F92CA77FA732#alt=image) 

### 4.重复使用某个正则

如果要重复使用某个正则表达式，推荐先使用 re.compile(pattern)函数 返回一个正则对象，然后复用这个正则对象，这样会更快！

