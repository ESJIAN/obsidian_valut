> [VHDL](https://so.csdn.net/so/search?q=VHDL&spm=1001.2101.3001.7020)是一门硬件语言，没学过硬件语言，挺感兴趣，还可以用在计组的实验中，花了点时间学习整理了一下VHDL的基本语法，方便查看。本blog所用到的所有图片都引用自[^1]
> [VHDL语言的基本语法参考文档](https://wenku.baidu.com/view/e6da0684326c1eb91a37f111f18583d048640f21.html)

[项目首页 - VHDL语言教程小白可用:本仓库提供了一份专为初学者设计的VHDL语言教程，旨在帮助小白快速入门并掌握VHDL的基本概念和使用方法。无论你是电子工程专业的学生，还是对硬件描述语言感兴趣的爱好者，这份教程都将是你学习VHDL的理想选择 - GitCode](https://gitcode.com/Open-source-documentation-tutorial/f35d5)


## 一、VHDL语言的基本语法

### 1、VHDL语言的表示符

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7b3d840208b40f90992a43704bfd9476.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d858c8e34a2869813c659123407d3f1a.png)

### 2、VHDL的数字

#### 2.1 数字型文字

156E2的意思是156× \times×1 0 2 10^2102；  
下划线可以连接数字。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/17b006663eb3ed10076600bff406dbef.png)

#### 2.2 数字基数表示的文字

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0294731835a44690f531bf4b5f34ced0.png)

#### 2.3 字符串型文字

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/fb3da99c5d32d6d92c221d4c5bbf3dc7.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e6b258ca232dc351fc256ed54a35f02b.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e4258692b9225caa987ce310655e0154.png)

#### 2.4 下标名及下标段名

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3cbaf2b3b2521f7d4297987e63bb603e.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/26541582cdf6fbd6e20c81850ad7e8c2.png)

> ==downto 和 to 有什么区别==  
> 举个例子，比如要生命一个长度位8的vector的信号  
> Signal s1: std_logic_vector(7 downto 0); 这个形成的数组下标值从右到左依次是7,6,5,4,3,2,1,0  
> Signal s2: std_logic_vector(0 to 7);这个形成的数组的下标值从右到做依次是0,1,2,3,4,5,6,7  
> 所以区别就是显示方向不同而已。

## 二、VHDL语言的数据对象

### 1、常数

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d37a41aade8fbdbcd87659f709b971df.png)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/743e008491eb0802a5adf8736bab4889.png)

### 2、变量

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1092f39449675a4628e6a0de37c0e4c3.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/bc74eade9dd61286727fb3608be54fcf.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c3c1824b71e86a8158658e48abb928c8.png)

### 3、信号(SIGNAL)

![](https://i-blog.csdnimg.cn/blog_migrate/f679e3e07ff00f25df7678bc90277025.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0527998a9af0022dccff8039271fea56.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2269826cb866b4bc7dda2b7e49bb8bbb.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cedc67cf1939a082e4ac1fc87b7a58b0.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/88527159051792286354566f2cf88023.png)

## 三、VHDL中的数据类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1ab2918dc3e322e0525a791060d2b4b3.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/209d093c7688b0dc458d322d35807834.png)

### 1、VHDL的预定义数据类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b3fc4c0b136d55d67fb8f3bc26cbf945.png)

#### 1.1 布尔(BOOLEAN)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3dba1e0f42034b0730a39de3380db3fc.png)

#### 1.2 位(BIT)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/62f408efc0aa0a65fc65fc53b3f0196a.png)

#### 1.3 位矢量(BIT_VECTOR)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0f49fcaab33e0c714e6a66011dbb19ea.png)

#### 1.4 字符(CHARACHTER)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/4816725b8a30459d679d2c87578036d4.png)

#### 1.5 整数(INTEGER)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9ec06ace16ce28771970d71475768496.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5df51768bbb6962a9ac504a9e626fad4.png)

#### 1.6 实数(REAL)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/700e2f35fa81bfc2ce77a4121dce3a19.png)

#### 1.7 字符串(STRING)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/678210abb255a361471e5626d35ae674.png)

#### 1.8 时间(TIME)数据类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2b66e82528a38505a78e3e0662eda29a.png)

#### 1.9 错误等级(SEVERITY_LEVEL)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/840bd17573441e9c03ae32d144956880.png)

### 2、IEEE预定义标准逻辑位与矢量

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7d74dc1b62e4634ba20c8bb9b6000b41.png)

#### 2.1 标准逻辑位STD_LOGIN数据类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1e566ff27bc4946fb928c69fd2fd918a.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5380d8f4a2353fa787db7aad8deb7cdd.png)

#### 2.2 标准逻辑矢量(STD_LOGIC_VECTOR)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c08b8675530fc2e21f04a4c1e80751b5.png)

#### 2.3 其他预定义标准数据类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/32ca0fd81d534e66f8386eecc586c9bd.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9f0e3a6c171d2a500d85a50b5237452c.png)

##### (1) 无符号数据类型（UNSIGNED TYPE)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cd761c0b1408774b46bf051d910f9d03.png)

##### (2) 有符号数据类型(SIGNED TYPE)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8f632ee640649b886b12ce7233d905d4.png)

#### 2.4 用户自定义数据类型方式

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5be8c32eaa27ecb58f1add55ba03db5f.png)

##### (1) TYPE语句用法

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/50c660b2f9c5250f6f31cad01de0e5a4.png)

##### (2) SUBTYPE语句的用法

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7c7b5bfa10054e6ed0188d41e49c36f0.png)

##### (3) 枚举类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2d2aa08dbfd4a5e8cbbbce8b4173d60e.png)

##### (4) 数组类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0d84f50454a37f3d4e0df55952ed5bee.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3be3e68c3731b26ae1fe271ecdabd092.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e1382b507cd8abfb72cf2a2f954635fa.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/81fe0821f0a1e50062479b7e738d12a3.png)

##### (5) 记录类型

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2de72578ea011fca006d7db23a1ac21b.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/37d234f502e597c5e74ba3b560bdbcbe.png)

##### (6) 数据类型转换

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e3750ffe60653d5589383771d80ab3de.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9c6136dd0a0d06bdc2ae9def2b3a6a80.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7b0395bcfc18e100bb60e457a7ed6356.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9d061913dccbbd43c0c15827463b9930.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/4cba4ddf801f0d71314af5f92454f5a0.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a8411acd76916070012ab2a71c0625ae.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1da7ae2491eff60314da5ac960908b42.png)

## 四、VHDL In Quartus Ⅱ

> 这章里边部分参考一位旁友**hayroc**的笔记，一起放上来方便看。

### 1、VHDL入门

#### （1）vhdl设计组成：

库和程序包(libary, package)  
实体(entity)  
结构体(architecture)  
配置(configuration)

通俗来讲：  
库和包 -> 材料，工具箱  
实体 -> 硬件外部的接口  
结构体 -> 硬件内部的具体实现

#### （2）语法

**实体**：

```ruby
entity 实体名 is  
    generic(常数名：数据类型：初值)  
    port(端口信号名：数据类型)  
end 实体名  
```

**结构体**：通过vhdl语句描述实体的具体行为和逻辑功能

```ruby
architecture 结构体名 of 实体名 is  
    说明部分（可选，如数据类型type 常数constand 信号signal 元件component 过程pocedure 变量variable和进程process等）  
begin  
    功能描述部分  
end 结构体名  
```

**逻辑**

```ruby
if 条件 then  
    --do something;
else if 条件 then 
    --do something;
else 
    --do something;
end if; 
```

**循环**

```ruby
for x in 0 to n loop
    --do something;
end loop;
```

**运算符**

> **赋值运算**：  
> <= 信号赋值  
> := 变量赋值  
> => 数组内部分元素赋值

> **逻辑运算**：  
> not 非  
> and 与  
> or 或  
> nand 与非  
> nor 或非  
> xor 异或  
> 注意：对数组类型，参与运算的数组位数要相等，运算为对应位进行

> **算术运算**：  
> + 加  
> - 减  
> * 乘  
> / 除  
> mod 模  
> rem 取余  
> ** 指数  
> abs 绝对值  
> 注意：尽量只使用加减

> **关系运算**：  
> => 大于等于  
> <= 小于等于  
> 大于  
> < 小于  
> /= 不等于  
> = 等于

> **连接运算**：  
> & 连接运算结果为同类型构成的数组

==注意==：从本质上讲，VHDL代码是并发执行的。只有PROCESS，FUNCTION或者PROCEDURE内部的代码才是顺序执行的。值得注意的是，尽管这些模块中的代码是顺序执行的，但是当它们作为一个整体是，与其他模块之间又是并发的。IF，WAIT,CASE,LOOP语句都是顺序代码，用在PROCESS,FUNCTION和PROCEDURE内部。

### 2、代码实例

#### （1）半加器

```ruby
--halfadder
library ieee;
use ieee.std_logic_1164.all;
use ieee.std_logic_unsigned.all;

entity halfadder is
    port(a, b : in std_logic;
         s, c : out std_logic
         --s -> sum, c -> carry
        );
end halfadder;

architecture f_halfadder of halfadder is 
begin
    s <= a xor b;
    c <= a and b;
end f_halfadder;
```

#### （2）一位全加器

```ruby
--fulladder
library ieee;
use ieee.std_logic_1164.all;
use ieee.std_logic_unsigned.all;

entity fulladder is 
    port(a, b, c0 : in std_logic;
            s, c1 : out std_logic
        );
end fulladder;

architecture f_fulladder of fulladder is 
begin 
    s  <= a xor b xor c0;
    c1 <= (a and b) or (c0 and (a xor b)); 
end f_fulladder;
```

#### （3）四位加法器

```ruby
--add4
library ieee;
use ieee.std_logic_1164.all;
use ieee.std_logic_unsigned.all;

entity add4 is 
    port(a, b : in std_logic_vector(3 downto 0); 
            s : out std_logic_vector(3 downto 0);
           c0 : in std_logic;
           c1 : out std_logic
        );
end add4;

architecture f_add4 of add4 is 
begin 
    --模拟手算加法
    process(a, b, c0)
    variable t : std_logic;
    begin
        t := c0;
        for x in 0 to 3 loop
            s(x) <= a(x) xor b(x) xor t;
               t := (a(x) and b(x)) or (t and (a(x) xor b(x)));
        end loop;
        c1 <= t;
    end process;
end f_add4;
```

#### （4）四位不带符号乘法器

直接使用 ”+“ 号要结果的存储要多加一位。

```ruby
---mul4
library ieee;
use ieee.std_logic_1164.all;
use ieee.std_logic_unsigned.all;

entity mul4 is 
    port(n0, n1 : in std_logic_vector(3 downto 0);
             a0 : out  std_logic_vector(7 downto 0)
        ); 
end mul4;

architecture f_mul4 of mul4 is 
signal t0, t1, t2, t3 : std_logic_vector(3 downto 0);

begin  
    process(n0, n1, t0, t1, t2, t3) 
    begin
        --模拟手算乘法
        if n1(0) = '1' then
            t0 <= n0;
        else 
            t0 <= "0000";
        end if;
        
        if n1(1) = '1' then
            t1 <= n0;
        else 
            t1 <= "0000";
        end if;
        
        if n1(2) = '1' then
            t2 <= n0;
        else 
            t2 <= "0000";
        end if;
        
        if n1(3) = '1' then
            t3 <= n0;
        else 
            t3 <= "0000";
        end if;
        
        a0 <= ("0000" & t0) + ("000" & t1 & '0') + ("00" & t2 & "00") + ('0' & t3 & "000");
    end process;
end f_mul4;
```

#### （5）五位带符号数的补码阵列乘法器

最后的原理图。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/06e08f92ea3033949a0d9a1bce1946b8.png)  
**comp4（四位求补器）**

```ruby
library ieee;
use ieee.std_logic_1164.all;
use ieee.std_logic_unsigned.all;
entity comp4 is 
	port (c0 : in std_logic;
			flag1: in std_logic;
			num1 : in std_logic_vector (3 downto 0);
			flag2: in std_logic;
			num2 : in std_logic_vector (3 downto 0);
			res1 : out std_logic_vector(3 downto 0);
			res2 : out std_logic_vector(3 downto 0));
end comp4;
architecture f_comp4 of comp4 is
begin
process(num1,flag1,num2,flag2,c0)
	Variable tmp_ci:std_logic;
	begin
		res1<="0000";
		res2<="0000";
		tmp_ci:='0';
		for i in 0 to 3 loop
			res1(i)<=(num1(i) xor (tmp_ci and flag1));
			tmp_ci:=num1(i) or tmp_ci;
		end loop;
		tmp_ci:='0';
		for i in 0 to 3 loop
			res2(i)<=(num2(i) xor (tmp_ci and flag2));
			tmp_ci:=num2(i) or tmp_ci;
		end loop;
end process;
end f_comp4;
```

**mult_array（四位乘法阵列）**

```ruby
--这里实现的是没有符号的乘法阵列
library ieee;
use ieee.std_logic_1164.all;
use ieee.std_logic_unsigned.all;
entity mult_array is
	port(num1, num2: in std_logic_vector(3 downto 0); -- num1是被乘数，舗um2是成乘数
			   res : out std_logic_vector(7 downto 0);
			   test: out std_logic_vector(7 downto 0));
end mult_array;
architecture f_mult_array of mult_array is
TYPE mult_array is Array(3 downto 0) of std_logic_vector(6 downto 0);
Signal m: mult_array;
begin
	process(m,num1,num2)
	Variable tmp_num2:std_logic_vector(3 downto 0);
	begin
		for i in 0 to 3 loop
			m(i)<="0000000";
			if num2(i)='1' then 
				m(i)(3+i downto i)<=num1(3 downto 0);
			end if;
		end loop;
		--test(7 downto 4 ) <= num2(3 downto 0);
		res<=('0' & m(0)) + ('0' & m(1)) + ('0' & m(2)) + ('0' & m(3));
	end process;
end f_mult_array;
```

**comp8（八位求补器）**

```ruby
library ieee;
use ieee.std_logic_1164.all;
use ieee.std_logic_unsigned.all;
entity comp8 is 
	port (e, c0 : in std_logic;
			num : in std_logic_vector (7 downto 0);
			result : out std_logic_vector(7 downto 0));
end comp8;
architecture f_comp8 of comp8 is
begin
process(num,e,c0)
	Variable tmp_ci:std_logic;
	begin
		tmp_ci:='0';
		for i in 0 to 7 loop
			result(i)<=(num(i) xor (tmp_ci and e));
			tmp_ci:=num(i) or tmp_ci;
		end loop;
end process;
end f_comp8;
```

### 3、Debug日志

> 1、同一个项目文件有两个vhd文件时，如果要对不同的vhd文件进行仿真的话需要对先把要仿真的文件置于top entity，然后把这个文件**编译**一遍，这样才能在node finder里边找到对应的引脚。
> 
> 2、信号的赋值操作只有在进程结束后才会进行，所以如果信号在进程内被多次赋值的话，只有最后一次赋值操作才会起作用，所以在进程内写算法一般都是用variable，signal和variable的区别具体可以看这篇blog => [VHDL中信号与变量的区别及赋值的讨论](https://blog.csdn.net/qijitao/article/details/50629305)  
> 3、当自己制作的组件的某一个接口是一个数组，这时候要用总线连接，具体的连法可以看这篇blog[quartus总线怎样连接](https://blog.csdn.net/deniece1/article/details/100998077)  
> 4、在用vhdl写组件的的时候，在定义process的时候，一定要把用到的input的端口写进porcess定义时的括号里边，否则可能导致的后果就是你把你写好的这个组件生成出来之后，结果永远对不上！

错误请指出，不定时更新，ths！  
==May you give me a like?==

[^1]: [VHDL语言基础教程：语法、数据对象与类型-CSDN博客](https://blog.csdn.net/messyking/article/details/115559198)
