

# **1 正则表达式的常用操作符**

![](https://ask.qcloudimg.com/http-save/yehe-9949496/e3b78396c3047aabe75f9ee67165de58.png)

![](https://ask.qcloudimg.com/http-save/yehe-9949496/36cde71e97547861638e6ded9512e0a9.png)

# **2 经典正则表达式实例**

![](https://ask.qcloudimg.com/http-save/yehe-9949496/306a39b1f9403ab72c25e8f29a120c8a.png)

# **3 Re库的基本使用**

## **3.1 正则表达式的表示类型**

（1）原生字符串类型

Re库采用raw string类型表示正则表达式，表示为：`r'text'`。

例如：`r'[1-9]\d{5}'`，`r'\d{3}-\d{8}|\d{4}-\d{7}'`

raw string是指不包含对转义符再次转义的字符串。

（2）string类型

Re库也可以采用string类型表示正则表达式，但更繁琐。

例如：`'[1-9]\\d{5}'`，`'\\d{3}-\\d{8}|\\d{4}-\\d{7}'`

**建议**：当正则表达式包含转义符时，使用raw string。

## **3.2 Re库主要功能函数**

![](https://ask.qcloudimg.com/http-save/yehe-9949496/7b73e4ae3ce8bba59ee4a7825dee2da1.png)

## **3.2.1 re.search(pattern, string, flags=0)**

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

## **3.2.2 re.match(pattern, string, flags=0)**

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

## **3.2.3 re.findall(pattern, string, flags=0)**

搜索字符串，以列表类型返回全部能匹配的子串。

```javascript
import re
ls = re.findall(r'[1-9]\d{5}','BIT100081 TSU100084')
ls
```

```javascript
['100081', '100084']
```

## **3.2.4 re.split(pattern, string, maxsplit=0, flags=0)**

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

## **3.2.5 re.finditer(pattern, string, flags=0)**

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

## **3.2.6 re.sub(pattern, repl, string, count=0, flags=0)**

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

## **3.3 Re库的另一种等价用法**

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

## **3.4 Re库的match对象**

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

## **3.5 Re库的贪婪匹配与最小匹配**

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