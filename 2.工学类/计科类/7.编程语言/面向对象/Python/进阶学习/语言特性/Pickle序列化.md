## 一、pickle是什么？
[pickle —— Python 对象序列化 — Python 3.7.13 文档](https://docs.python.org/zh-cn/3.7/library/pickle.html)
在英语中 pickle 名词是**泡菜**，动词是**腌渍**的意思。可以理解为把东西腌起来保存成文件，要用的时候读出来洗洗再用。

python的pickle模块实现了基本的**数据序列化和反序列化**。

序列化对象可以在磁盘上保存对象，并在需要的时候读取出来。任何对象都可以执行序列化操作。

**pickling**是将Python对象层次结构转换为[字节流](https://so.csdn.net/so/search?q=%E5%AD%97%E8%8A%82%E6%B5%81&spm=1001.2101.3001.7020)的过程。

**unpickling**是反向操作，从而将字节流（来自二进制文件或类似字节的对象）转换回对象层次结构。  
![](https://i-blog.csdnimg.cn/blog_migrate/48456cca6fe5ceacf5dad676a9fba85b.png)

### 1.pickle的优缺点

1、优点：

pickle提供了一个简单的**持久化**功能。可以将对象以文件的形式**存放在磁盘上**。

通过pickle模块的序列化操作我们能够将程序中运行的对象信息保存到文件中去，**永久存储**。

python中**几乎所有的数据类型**（列表，字典，集合，类等）都可以用pickle来序列化。

**没有外部标准强加的限制**，例如JSON或XDR（不能代表指针共享）。

默认情况下，pickle数据格式使用**相对紧凑的二进制**表示。如果需要最佳尺寸特征，则可以有效地压缩数据。

pickle可以**表示极其庞大的Python类型**（其中许多是自动的，通过巧妙地使用Python的内省工具；复杂的案例可以通过实现特定的对象API来解决）。

通过pickle模块的[反序列化](https://so.csdn.net/so/search?q=%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96&spm=1001.2101.3001.7020)操作，我们能够从文件中创建上一次程序保存的对象。

2、缺点：

pickle模块只能在python中使用，**仅限于传输的两端都是python的情况**，且需要尽量保持两端的版本一致。  
非Python程序可能无法重建pickled Python对象。

pickle序列化后的数据，**可读性差**，人一般无法识别。  
![](https://i-blog.csdnimg.cn/blog_migrate/db3b4eb36948a915188e6837e92f7d76.png)

### 2.pickle和JSON的区别

1、JSON是一种文本序列化格式（它输出unicode文本，虽然大部分时间它被编码utf-8），而pickle是二进制序列化格式。

2、JSON是人类可读的，而pickle则不是。

3、JSON是可互操作的，并且在Python生态系统之外广泛使用，而pickle是特定于Python的。

默认情况下，JSON只能表示Python内置类型的子集，而**不能表示自定义类**；

[JSON和JSON模块详解](https://blog.csdn.net/Hardworking666/article/details/112725423)

### 3.pickle的应用总结

本地序列化的情况，应用较少。一般来说，大多数应用场景在**网络**中，将数据序列化后通过网络传输到远程结点，远程服务器上的服务接受到数据后进行反序列化，就可以使用了。

但是，需要注意的是，**远端接受端**反序列化时必须有对应的数据类型，否则就会报错，尤其是自定义类，必须远程存在。

目前，大多数项目都不是单机，不是单服务，需要通过网络将数据传送到其他结点上，这就需要大量的序列化，反序列化。

但是python程序之间还可以使用pickle解决序列化和反序列化。  
如果是跨平台，跨语言，跨协议，pickle就不适合了，就需要公共协议，如XML/Json /protocol Buffer等。

每种协议都有自己的负载，其所使用的场景都不一样，二进制的操作**不一定适用于所有的场景**。  
但越是底层的协议，越需要二进制传输。  
![](https://i-blog.csdnimg.cn/blog_migrate/262cd708f854937445cf3a161d26d79c.png)

## 二、pickle的用法

### 1. pickle接口

pickle 包主要提供了两个功能，一个是将对象转换成字节流，即**串行化**；另一个是将字节流转换成对象，即**反串行化**。

<label class="ob-comment" title="" style=""> 每个功能又分出了两个分支，一个是仅转换成字节流，另一个是转换成字节流并保存到文件中去。
 <input type="checkbox"> <span style=""> 第一行表示接收对象是打开的IO流，第二个接收对象则是字符串变量</span></label>
所以 pickle 包主要有 4 个接口，如下图所示：  
![](https://i-blog.csdnimg.cn/blog_migrate/c4e57d90427580b66a839a75a5eb996c.png)  
基本接口：

```python
pickle.dump(obj, file [,protocol])
```

注释：

obj——序列化对象，将对象obj保存到文件file中去。

file——file表示保存到的**类文件对象**，file必须有write()接口，file可以是一个以’w’打开的文件或者是一个StringIO对象，也可以是任何可以实现write()接口的对象。

protocol——序列化模式，默认是 0（ASCII协议，表示**以文本的形式**进行序列化）。  
protocol的值还可以是1和2（1和2表示**以二进制的形式**进行序列化。其中，1是老式的二进制协议；2是新二进制协议）。

1、dump（对象，文件对象）：**串行化并保存**到文件，dump 的文件对象要求是可写的。

2、load（文件对象）：从文件**读数据并恢复出对象**。load 函数从文件对象中读出一个对象，返回值就是该对象。

```python
>>> a = range(10)
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> fd = open("tmp,bin", "wb")
>>> fd
<open file 'tmp,bin', mode 'wb' at 0x000000000277E8A0>
>>> pickle.dump(a, fd)
>>> fd.close()
>>> fd2 = open("tmp,bin", "rb")
>>> a2 = pickle.load(fd2)
>>> a2
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

3、dumps（对象）：**仅串行化**。dumps 函数返回一个字节流。

4、loads（字节流）：从字节流中恢复出对象。输入应该是 dumps() 的返回值。  
注意，不要随意构造字节流，因为**并不是所有的字节流都能被解析出来**。

```python
>>> a = range(10)
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> s =  pickle.dumps(a)
>>> s
'(lp0\nI0\naI1\naI2\naI3\naI4\naI5\naI6\naI7\naI8\naI9\na.'
>>> type(s)
<type 'str'>
>>> b = pickle.loads(s)
>>> b
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 2. pickle实例

有了 pickle 这个对象, 就能对 file 以读取的形式打开：

```python
x = pickle.load(file)
```

注解：从 file 中读取一个字符串，并将它重构为原来的python对象。

序列化的时候，**只是序列化了整个序列对象**，而不是内存地址。

**file**：类文件对象，有read()和readline()接口。

举例：

一个字典a = {‘name’:‘Tom’,‘age’:18}，用pickle.dump存到本地文件，所存数据的结构就是**字典**。  
而普通的file.write写入文件的是**字符串**。读取时，pickle.load返回的是一个**字典**，file.read返回的是一个**字符串**。

如下代码：

```python
import pickle

a = {'name': 'Tom', 'age': 18}
with open('text.txt', 'wb') as file:
    pickle.dump(a, file)
with open('text.txt', 'rb') as file2:
    b = pickle.load(file2)
print(type(b))

```

运行结果：  
![](https://i-blog.csdnimg.cn/blog_migrate/a3bce648a6399e9bc65aa9de85fe5e89.png)  
得到的b的类型是字典，b和a是等价的。

也就是说pickle可以把字典、列表等结构化数据存到本地文件，读取后返回的**还是**字典、列表等结构化数据。

**而file.write、file.read存取的对象是字符串。**  
![](https://i-blog.csdnimg.cn/blog_migrate/2852a6901eb626d60eed0448886cf74c.png)  
我们再**使用zip创建字典**看看反序列化输出是不是也是字典：

zip()可以将两个可迭代对象中的对应元素打包成一个个**元组**，然后返回这些元组组成的列表。

dict()创建字典，可以传入元组列表创建字典，也可以通过zip得到元组列表后来**创建字典**。

```python
from pickle import *

d = dict(zip('mysql', range(5)))
s = dumps(d)  # 进行序列化
print(s)  # 正常情况的输出
print(loads(s))  # 进行反序列化并输出
```

运行结果如下，结果也是字典：  
![](https://i-blog.csdnimg.cn/blog_migrate/5ee186b288606b4270a61f3e91ab7c3d.png)  
![](https://i-blog.csdnimg.cn/blog_migrate/08114a2ce8215e90bc2a60d43dc36333.png)

## 结语