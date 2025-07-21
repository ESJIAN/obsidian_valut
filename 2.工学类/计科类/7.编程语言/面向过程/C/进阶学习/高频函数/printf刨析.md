Printf这个函数让大家又爱又恨，第一次接触c语言编程，基本都是调用printf打印“Hellow World！”,但当真正深入使用编程后，才发现printf并不是一个简单的函数。尤其是从事[嵌入式软件](https://so.csdn.net/so/search?q=%E5%B5%8C%E5%85%A5%E5%BC%8F%E8%BD%AF%E4%BB%B6&spm=1001.2101.3001.7020)工作的开发人员，会经常接触printf挂接驱动、printf重入的问题。

本文详细解释printf函数的工作原理，希望对大家有所帮助。

## 一、函数栈

分析printf之前首先了解函数的工作机制，程序运行前需要分配好内存空间，如图1所示(本文给出一个简图，实际编译器分配的会更加细致)：

![](https://i-blog.csdnimg.cn/blog_migrate/a512e74770d5db27e0db7ff217e6331f.png)

图1

代码、全局变量、常量内存位置固定，堆可以用于分配[动态内存](https://so.csdn.net/so/search?q=%E5%8A%A8%E6%80%81%E5%86%85%E5%AD%98&spm=1001.2101.3001.7020)，而栈区则用于程序的运行。函数调用时将形参从右向左压入栈，等函数运行完成，通过出栈，将形参的存储空间释放。不同的编译器对函数入栈、出栈的内容会有所区别，但是对于c语言，形参的格式遵循_cdedl调用规则,有以下特点：

1. 函数形参入栈顺序是从右向左
    

2. 函数形参存储空间为连续存储，且参数按照固定字节对齐；编译器根据程序运行平台的字长进行对齐，32位字长平台按照4[字节对齐](https://so.csdn.net/so/search?q=%E5%AD%97%E8%8A%82%E5%AF%B9%E9%BD%90&spm=1001.2101.3001.7020)，64位的会按照8字节对齐。
    

## 二、printf函数栈

printf 函数原型为int printf(const char *fmt, ...)，使用了可变参数的模式，我们通过图2例子来分析函数栈。

![](https://i-blog.csdnimg.cn/blog_migrate/e759db7940550096c8d48024458f320c.png)

图2

fmt：“%d,%c,%c,%f\n”为常量字符串,存储在内存的常量字段，fmt为该字符串首地址；

可变形参1：与变量a类型和数值一致，为int类型；

可变形参2：与变量b类型和数值一致, 为char类型；

可变形参3：与变量c类型和数值一致,为char类型；

可变形参4：与变量d类型和数值一致,float的可变形参会被编译器强制转换为double类型；

假设该代码运行在32位字长的平台，且栈底->栈顶为“高地址->低地址”，函数栈中所有参数的存储地址按照4字节对齐存储，设fmt存储地址为0x30000000；则其函数栈如下图：

![](https://i-blog.csdnimg.cn/blog_migrate/df9f6b006ebfc6ed8203487b91f6ca35.png)

图3

## 三、printf代码解析

### printf代码框架
    

printf代码及注释如下所示：

注：本例为32位平台，所以参数出入栈地址均为4字节对齐。

```cpp
#ifndef _VALIST#define _VALISTtypedef char *va_list;#endif                /* _VALIST */typedef int acpi_native_int;#define  _AUPBND                (sizeof (acpi_native_int) - 1)                               // 入栈4字节对齐#define  _ADNBND                (sizeof (acpi_native_int) - 1)                               // 出栈4字节对齐#define _bnd(X, bnd)            (((sizeof (X)) + (bnd)) & (~(bnd)))                          // 4字节对齐#define va_arg(ap, T)           (*(T *)(((ap) += (_bnd (T, _AUPBND))) - (_bnd (T,_ADNBND)))) // 按照4字节对齐取下一个可变参数,并且更新参数指针#define va_end(ap)              (void) 0                                                     // 与va_start成对,避免有些编译器告警#define va_start(ap, A)         (void) ((ap) = (((char *) &(A)) + (_bnd (A,_AUPBND))))       // 第一个可变形参指针#endif                /* va_arg */ static char sprint_buf[2408]; int printf(const char *fmt, ...){    va_list args;    int n;    // 第一个可变形参指针    va_start(args, fmt);    // 根据字符串fmt，将对应形参转换为字符串，并组合成新的字符串存储在sprint_buf[]缓存中，返回字符个数。    n = vsprintf(sprint_buf, fmt, args);    //c标准要求在同一个函数中va_start 和va_end 要配对的出现。    va_end(args);    // 调用相关驱动接口,将将sprintf_buf中的内容输出n个字节到设备，    // 此处可以是串口、控制台、Telnet等,在嵌入式开发中可以灵活挂接    if (console_ops.write)        console_ops.write(sprint_buf, n);    return n;}
```

### vsprintf解析模式详解
    

vsprintf采用%[flags][width][.prec][length][type]模式对各个参数进行解析各标志解析如下表：

1. 标志（flags）
    

标志（flags）用于规定输出样式，含义如下：

|   |   |   |
|---|---|---|
|flags（标志）|字符名称|描述|
|-|减号|在给定的字段宽度内左对齐，右边填充空格（默认右对齐）|
|+|加号|强制在结果之前显示加号或减号（+ 或 -），即正数前面会显示 + 号；默认情况下，只有负数前面会显示一个 - 号|
|（空格）|空格|输出值为正时加上空格，为负时加上负号|
|#|井号|specifier 是 o、x、X 时，增加前缀 0、0x、0X；<br><br>specifier 是 e、E、f、g、G 时，一定使用小数点；<br><br>specifier 是 g、G 时，尾部的 0 保留|
|0|数字零|对于所有的数字格式，使用前导零填充字段宽度（如果出现了减号标志或者指定了精度，则忽略该标志）|

2. 最小宽度（width）
    

最小宽度（width）用于控制显示字段的宽度，即打印输出的总宽度，取值和含义如下：

|   |   |   |
|---|---|---|
|width（最小宽度）|字符名称|描述|
|digit(n)|数字|字段宽度的最小值，如果输出的字段长度小于该数，结果会用前导空格填充；如果输出的字段长度大于该数，结果使用更宽的字段，不会截断输出|
|*|星号|宽度在 format 字符串中规定位置未指定，使用星号标识附加参数，指示下一个参数是width|

3. 精度（.prec）
    

精度（.precision）用于指定输出精度，即输出数据占用的宽度，取值和含义如下：

|   |   |   |
|---|---|---|
|.pre（精度）|字符名称|描述|
|.digit(n)|点+数字|对于整数说明符（d、i、o、u、x、X）：precision 指定了要打印的数字的最小位数。如果写入的值短于该数，结果会用前导零来填充。如果写入的值长于该数，结果不会被截断。精度为 0 意味着不写入任何字符；<br><br>对于 e、E 和 f 说明符：要在小数点后输出的小数位数；<br><br>对于 g 和 G 说明符：要输出的最大有效位数；<br><br>对于 s 说明符：要输出的最大字符数。默认情况下，所有字符都会被输出，直到遇到末尾的空字符；<br><br>对于 c 说明符：没有任何影响；<br><br>当未指定任何精度时，默认为 1。如果指定时只使用点而不带有一个显式值，则标识其后跟随一个 0。|
|.*|点+星号|精度在 format 字符串中规定位置未指定，使用点+星号标识附加参数，指示下一个参数是精度|

4. 类型长度（length）
    

类型长度（length）用于控制待输出数据的数据类型长度，取值和含义如下：

|   |   |
|---|---|
|length（类型长度）|描述|
|h|参数被解释为短整型或无符号短整型（仅适用于整数说明符：i、d、o、u、x 和 X）|
|l|参数被解释为长整型或无符号长整型，适用于整数说明符（i、d、o、u、x 和 X）及说明符 c（表示一个宽字符）和 s（表示宽字符字符串）|
|ll|参数被解释为超长整型或无符号超长长整型，适用于整数说明符（i、d、o、u、x 和 X）及说明符 c（表示一个宽字符）和 s（表示宽字符字符串）|

5. 说明符（type）
    

说明符（type）用于规定输出数据的类型，含义如下：

|   |   |   |
|---|---|---|
|说明符（specifier）|对应数据类型|描述|
|d / i|int|输出类型为有符号的十进制[整数](https://baike.baidu.com/item/%E6%95%B4%E6%95%B0/1293937?fromModule=lemma_inlink)，i 是老式写法|
|o|unsigned int|输出类型为无符号[八进制](https://baike.baidu.com/item/%E5%85%AB%E8%BF%9B%E5%88%B6/4230825?fromModule=lemma_inlink)整数（没有前导 0）|
|u|unsigned int|输出类型为无符号[十进制](https://baike.baidu.com/item/%E5%8D%81%E8%BF%9B%E5%88%B6/6521392?fromModule=lemma_inlink)整数|
|x / X|unsigned int|输出类型为无符号[十六进制](https://baike.baidu.com/item/%E5%8D%81%E5%85%AD%E8%BF%9B%E5%88%B6/4162457?fromModule=lemma_inlink)整数，x 对应的是 abcdef，X 对应的是 ABCDEF（没有前导 0x 或者 0X）|
|f / lf|double|输出类型为十进制表示的[浮点数](https://baike.baidu.com/item/%E6%B5%AE%E7%82%B9%E6%95%B0/23734876?fromModule=lemma_inlink)，默认精度为6（lf 在 C99 开始加入标准，意思和 f 相同）|
|e / E|double|输出类型为[科学计数法](https://baike.baidu.com/item/%E7%A7%91%E5%AD%A6%E8%AE%A1%E6%95%B0%E6%B3%95/756685?fromModule=lemma_inlink)表示的数，此处 "e" 的大小写代表在输出时用的 “e” 的大小写，默认浮点数精度为6|
|g|double|根据数值不同自动选择 %f 或 %e，%e 格式在指数小于-4或指数大于等于精度时用使用 [1]|
|G|double|根据数值不同自动选择 %f 或 %E，%E 格式在指数小于-4或指数大于等于精度时用使用|
|c|char|输出类型为[字符](https://baike.baidu.com/item/%E5%AD%97%E7%AC%A6/4768913?fromModule=lemma_inlink)型。可以把输入的数字按照[ASCII码](https://baike.baidu.com/item/ASCII%E7%A0%81?fromModule=lemma_inlink)相应转换为对应的字符|
|s|char *|输出类型为[字符串](https://baike.baidu.com/item/%E5%AD%97%E7%AC%A6%E4%B8%B2/1017763?fromModule=lemma_inlink)。输出字符串中的字符直至遇到字符串中的空字符（字符串以 '\0‘ 结尾，这个 '\0' 即空字符）或者已打印了由精度指定的字符数|
|p|void *|以16进制形式输出[指针](https://baike.baidu.com/item/%E6%8C%87%E9%92%88?fromModule=lemma_inlink)|
|q|long long|输出类型为长整型有符号的十进制[整数](https://baike.baidu.com/item/%E6%95%B4%E6%95%B0/1293937?fromModule=lemma_inlink)|
|%|不转换参数|不进行转换，输出字符‘%’（百分号）本身|
|n|int *|到此字符之前为止，一共输出的字符个数，不输出文本 [4]|

6. 转义字符
    

转义序列在字符串中会被自动转换为相应的特殊字符。printf() 使用的常见转义字符如下：

|   |   |   |
|---|---|---|
|转义序列|描述|ASCII 编码|
|\'|单引号|0x27|
|\"|双引号|0x22|
|\?|问号|0x3f|
|\\|反斜杠|0x5c|
|\a|铃声（提醒）|0x07|
|\b|退格|0x08|
|\f|换页|0x0c|
|\n|换行|0x0a|
|\r|回车|0x0d|
|\t|水平制表符|0x09|
|\v|垂直制表符|0x0b|

常见组合及输出结果

```cpp
int main(void){    int a = 10, b = 3;    printf("%*.*d\n",a,b, -100);         // 输出数字，右对齐,宽度从变量获取    printf("%10.3d\n", -100);            // 输出数字，右对齐    printf("%-10.3d\n", -100);           // 输出数字，左对齐    printf("%+10.3d\n", 100);            // 输出数字，正数带正号    printf("%0.13d\n", 100);             // 输出文本格式,如员工号    printf("%#.8x\n", 0x30ff);           // 输出8位16进制地址，小写字母    printf("%#.8X\n", 0x30ff);           // 输出8位16进制地址，大写字母    printf("%.3f\n", 3.14159267892);     // 保留浮点小数点后有效位数    printf("%llu\n", 0xffffffffffffffff);// 输出64位长整型}
```

输出结果：

![](https://i-blog.csdnimg.cn/blog_migrate/a56cc1b7464503600ab23d1346345148.png)

### vsprintf流程图
    

![](https://i-blog.csdnimg.cn/blog_migrate/2bc781c2cfd8a4bff40337ebda73be2a.png)

### vsprintf源码及注释
    

```cpp
 
#define ZEROPAD    1       /* 无数据位用0填充 */
#define SIGN       2       /* 符号位 */
#define PLUS       4       /* 符号位正数显示正号 */
#define SPACE      8       /* 符号位非负数显示空格 */
#define LEFT      16       /* 左对齐 */
#define SPECIAL   32       /* 显示其他进制的前缀,比如16进制添加前缀0x */
#define LARGE     64       /* 使用大写母 */
 
#define is_digit(c) ((c) >= '0' && (c) <= '9')
//浮点字符串缓存
#define SZ_NUM_BUF    32
static char sprint_fe[SZ_NUM_BUF+1];
 
static const char *digits = "0123456789abcdefghijklmnopqrstuvwxyz";
static const char *upper_digits = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
// 字符串长度
static size_t strnlen(const char *s, size_t count)
{
  const char *sc;
  for (sc = s; *sc != '\0' && count--; ++sc);
  return sc - s;
}
// 字符转10进制数
static int skip_atoi(const char **s)
{
  int i = 0;
  while (is_digit(**s)) i = i*10 + *((*s)++) - '0';
  return i;
}
// 
static char *number(char *str, long num, int base, int size, int precision, int type)
{
    char c, sign, tmp[66];
    const char *dig = digits;
    int i;
    // 
    if (type & LARGE)  dig = upper_digits;
    // 左对齐，去掉补0
    if (type & LEFT) type &= ~ZEROPAD;
    // 
    if (base < 2 || base > 36) return 0;
    // 补0或补空格
    c = (type & ZEROPAD) ? '0' : ' ';
    /*符号位处理,符号位占用1位-STR*/
    sign = 0;
    if (type & SIGN)
    {
        if (num < 0)
        {
            sign = '-';
            num = -num;
            size--;
        }
        // 正数打印正号
        else if (type & PLUS)
        {
            sign = '+';
            size--;
        }
        // 符号位打印空格
        else if (type & SPACE)
        {
            sign = ' ';
            size--;
        }
    }
/*符号位处理-END*/
 
/*进制转换-STR*/
    if (type & SPECIAL)
    {
        if (base == 16)
            size -= 2;
        else if (base == 8)
            size--;
    }
    i = 0;
    if (num == 0)
      tmp[i++] = '0';
    else
    {
        while (num != 0)
        {
            tmp[i++] = dig[((unsigned long) num) % (unsigned) base];
            num = ((unsigned long) num) / (unsigned) base;
        }
    }
/*进制转换-END*/
 
/*数据有效位置处理*/
    if (i > precision) precision = i;
        size -= precision;
/*非左对齐且非空余位置不补0,左侧补充空格*/
    if (!(type & (ZEROPAD | LEFT))) while (size-- > 0) *str++ = ' ';
    // 输出符号位
    if (sign) *str++ = sign;
    // 输出8进制或16进制前缀
    if (type & SPECIAL)
    {
      if (base == 8)
        *str++ = '0';//0
      else if (base == 16)
      {
        *str++ = '0';
        *str++ = digits[33];//0x
      }
    }
    /*左侧补充剩余位,如补0或者补充空格*/ 
    if (!(type & LEFT)) 
    while (size-- > 0) *str++ = c;
    /*实际数据小于有效长度,左侧补0处理*/
    while (i < precision--) *str++ = '0';
    /*复制有效字符*/ 
    while (i-- > 0) *str++ = tmp[i];
    /*左对齐,右侧补充空格*/ 
    while (size-- > 0) *str++ = ' ';
    return str;
}
// 计算浮点精度
static int ilog10(double n)    /* 在整数输出中计算log10(n) */
{
    int rv = 0;
 
    while (n >= 10)
    {    /* 右移小数位 */
        if (n >= 100000)
        {
            n /= 100000; rv += 5;
        }
        else
        {
            n /= 10; rv++;
        }
    }
    while (n < 1)
    {        /* 左移小数位 */
        if (n < 0.00001)
        {
            n *= 100000; rv -= 5;
        }
        else
        {
            n *= 10; rv--;
        }
    }
    return rv;
}
// 整数位数
static double i10x(int n)    /* 计算10^n的整数输入 */
{
    double rv = 1;
 
    while (n > 0)
    {
        if (n >= 5)
        {
            rv *= 100000; n -= 5;
        }
        else
        {
            rv *= 10; n--;
        }
    }
    while (n < 0)
    {        /* Right shift */
        if (n <= -5)
        {
            rv /= 100000; n += 5;
        }
        else
        {
            rv /= 10; n++;
        }
    }
    return rv;
}
// 浮点数据转字符串%f,%e,%E
static void ftoa(
    char* buf,    /* 字符串缓存 */
    double val,    /* 浮点数 */
    int prec,    /* 小数位数 */
    char fmt    /* 类型标识 */
)
{
    int d;
    int e = 0, m = 0;
    char sign = 0;
    double w;
    const char *er = 0;
    const char ds = '.';//FF_PRINT_FLOAT == 2 ? ',' : '.';
    unsigned int *pu=(unsigned int *)&val;
    // 阶码全1,尾数不为0，不存在的数"NaN"
    //if (isnan(val))
    if(((pu[1]&0x7ff00000)==0x7ff00000)&&(((pu[1]&0xfffff)!=0)||(pu[0]!=0)))
    {
        er = "NaN";
    }
    else
    {
        // 默认6 位小数
        if (prec < 0) prec = 6;
        // 符号处理
        if (val < 0)
        {
            val = 0 - val;
            sign = '-';
        }
        else
        {
            sign = '+';
        }
        // 阶码全1,尾数部分全0，符号位为0表示正无穷。
        // 阶码全1,尾数部分全0，符号位为1表示负无穷。
        //if (isinf(val))
        if(((pu[1]&0x7fffffff) ==0x7ff00000)&&(pu[0] == 0))
        {
            er = "INF";
        }
        //
        else
        {
            // ‘f’类型
            if (fmt == 'f')
            {
                val += i10x(0 - prec) / 2;    /*用于四舍五入,比如1.67保留1位小数为1.7 */
                m = ilog10(val);            /*整数位数*/
                if (m < 0) m = 0;
                if (m + prec + 3 >= SZ_NUM_BUF) er = "OV";    /* 最大缓存 */
            }
            else
            {    /* E类型 x.xxxxxxe+xx*/
                if (val != 0)
                {
                    val += i10x(ilog10(val) - prec) / 2;    /* 用于四舍五入,prec表示底数部分的小数位数*/
                    e = ilog10(val);                        /*整数位数*/
 
                    if (e > 99 || prec + 7 >= SZ_NUM_BUF)  //指数范围,及最大缓存,
                    {
                        er = "OV";
                    }
                    else
                    {
                        if (e < -99) e = -99;
                        val /= i10x(e);    /* 计算底数 */
                    }
                }
            }
        }
        // 有效浮点
        if (!er)
        {
            // 符号位
            if (sign == '-')
                *buf++ = sign;
 
            do
            {
                /* 进入小数部分时插入小数分隔符 */
                if (m == -1)
                    *buf++ = ds;
                //剪掉最高的数字d
                w = i10x(m);
                //
                d = (int)(val / w); val -= d * w;
 
                *buf++ = (char)('0' + d);    /* 记录10进制 */
 
            } while (--m >= -prec);
 
            if (fmt != 'f')
            {
                *buf++ = (char)fmt;
                if (e < 0) {
                    e = 0 - e; *buf++ = '-';
                }
                else {
                    *buf++ = '+';
                }
                *buf++ = (char)('0' + e / 10);
                *buf++ = (char)('0' + e % 10);
            }
        }
    }
    // 特殊值
    if (er)
    {    // 符号
        if (sign)  *buf++ = sign;
        // 数据字符串
        do
        {
            *buf++ = *er++;
        } while (*er);
    }
    *buf = 0;    /* 结束符 */
}
int vsprintf(char *buf, const char *fmt, va_list args)
{
    int len;
    unsigned long long num;
    int i, base;
    char * str;
    const char *s;/*s所指向的内存单元不可改写，但是s可以改写*/
    int flags;        /* flags to number() */
    int field_width;  /* width of output field */
    int precision;    /* min. # of digits for integers; max number of chars for from string */
    int qualifier;    /* 'h', 'l', or 'L' for integer fields */
                      /* 'z' support added 23/7/1999 S.H.    */
                      /* 'z' changed to 'Z' --davidm 1/25/99 */
    for (str=buf ; *fmt ; ++fmt)
    {
        if (*fmt != '%') /*使指针指向格式控制符'%,以方便以后处理flags'*/
        {
            *str++ = *fmt;
            continue;
        }
        /* flags */
        flags = 0;
        repeat:
            ++fmt;    
            switch (*fmt)
            {
                case '-': flags |= LEFT; goto repeat;/*左对齐-left justify*/
                case '+': flags |= PLUS; goto repeat;/*p plus with ’+‘*/
                case ' ': flags |= SPACE; goto repeat;/*p with space*/
                case '#': flags |= SPECIAL; goto repeat;/*根据其后的转义字符的不同而有不同含义*/
                case '0': flags |= ZEROPAD; goto repeat;/*当有指定参数时，无数字的参数将补上0*/
            }
 
       
        field_width = -1;
        if ('0' <= *fmt && *fmt <= '9')
            field_width = skip_atoi(&fmt);
        else if (*fmt == '*')
        {
            ++fmt;/*skip '*' */
            /* it's the next argument */
            field_width = va_arg(args, int);// 下个参数变量表述位宽
            if (field_width < 0) {
                field_width = -field_width;
                flags |= LEFT;
            }
        }
        /* get the precision-----即是处理.pre 有效位 */
        precision = -1;
        if (*fmt == '.')
        {
            ++fmt;
            if ('0' <= *fmt && *fmt <= '9')
                precision = skip_atoi(&fmt);
            else if (*fmt == '*') /*如果精度域中是字符'*'，表示下一个参数指定精度。因此调用va_arg 取精度值。若此时宽度值小于0，则将字段精度值取为0。*/
            {
                ++fmt;
                /* it's the next argument */
                precision = va_arg(args, int);
            }
            if (precision < 0)
                precision = 0;
        }
        /* get the conversion qualifier 分析长度修饰符，并将其存入qualifer 变量*/
        qualifier = -1;
        if (*fmt == 'l' && *(fmt + 1) == 'l')
        {
            qualifier = 'q';
            fmt += 2;
        }
        else if (*fmt == 'h' || *fmt == 'l' || *fmt == 'L'|| *fmt == 'Z')
        {
            qualifier = *fmt;
            ++fmt;
        }
        /* default base */
        base = 10;
        /*处理type部分*/
        switch (*fmt)
        {
            case 'c':
                /*非左对齐,左侧填充空格-Satrt*/
                if (!(flags & LEFT))
                   while (--field_width > 0)
                   *str++ = ' ';
                /*非左对齐,左侧填充空格-End*/
                *str++ = (unsigned char) va_arg(args, int);
                /*左对齐,右侧填充空格-Satrt*/
                while (--field_width > 0)
                *str++ = ' ';
                /*左对齐,右侧填充空格-End*/    
                //continue在此处是跳出本次for循环
                continue;
            case 's':
                s = va_arg(args, char *);
                if (!s)
                    s = "";
                len = strnlen(s, precision);/*取字符串的长度，最大为precision*/
                /*非左对齐,左侧填充空格-Satrt*/
                if (!(flags & LEFT))
                while (len < field_width--)
                    *str++ = ' ';
                    /*非左对齐,左侧填充空格-End*/
                for (i = 0; i < len; ++i)
                    *str++ = *s++;
                /*左对齐,右侧填充空格-Satrt*/
                while (len < field_width--)
                    *str++ = ' ';
                /*左对齐,右侧填充空格-End*/    
                continue;
            case 'p':
                /*没有设置宽度域，则默认宽度为指针变量长度,32位系统默认为8，且需要添0处理*/
                if (field_width == -1)
                {
                    field_width = 2*sizeof(void *);
                    flags |= ZEROPAD;
                }
                str = number(str,(unsigned long) va_arg(args, void *), 16,field_width, precision, flags);
                continue;
            // 形参作为指针变量,向指针变量所指向的地址写入当前转换的字符长度
            case 'n':
                // ln长整型地址
                if (qualifier == 'l')
                {
                    long * ip = va_arg(args, long *);
                    *ip = (str - buf);
                }
                // zn 字节地址
                else if (qualifier == 'Z')
                {
                    size_t * ip = va_arg(args, size_t *);
                    *ip = (str - buf);
                }
                // n 整形地址
                else
                {
                    int * ip = va_arg(args, int *);
                    *ip = (str - buf);
                }
                continue;
            // %f %e %E %lf均使用double类型
            case 'f':                    /* Floating point (decimal) */
            case 'e':                    /* Floating point (e) */
            case 'E':                    /* Floating point (E) */
                // double数据转字符串
                ftoa(sprint_fe, va_arg(args, double), precision, *fmt);    /* 浮点转字符串*/
                // 右对齐 左侧补充空格
                if (!(flags&LEFT))
                {
                    for (j = strnlen(sprint_fe, SZ_NUM_BUF); j<field_width; j++)
                    *str++= '/0';
                }
                // 数据主体
                i = 0;
                while(sprint_fe[i]) *str++ = sprint_fe[i++];    /* 主体 */
                // 左对齐 右侧补充空格
                while (j++ < field_width) *str++ = '/0';
   
                continue;
            // %%表示%
            case '%':
                *str++ = '%';
                continue;
            /* 设置进制*/
            case 'o':
                base = 8;
                break;
                /*大写*/
            case 'X':
                flags |= LARGE;
            case 'x':
                base = 16;
                break;
            /*有符号类型*/
            case 'd':
            case 'i':
                flags |= SIGN;
            /*无符号类型*/
            case 'u':
                break;
            default:
                /*非参数打印*/
                *str++ = '%';
                if (*fmt)
                *str++ = *fmt;
                else
                --fmt;
                continue;
        }
        /*同时如果flags有符号位的话，将参数转变成有符号的数*/
        if (qualifier == 'l')
        {
            num = va_arg(args, unsigned long);
            if (flags & SIGN)
                num = (signed long) num;
        }
        else if (qualifier == 'q')
        {
            num = va_arg(args, unsigned long long);
            if (flags & SIGN)
                num = (signed long long) num;
        }
        else if (qualifier == 'Z')
        {
            num = va_arg(args, size_t);
        }
        else if (qualifier == 'h')
        {
            num = (unsigned short) va_arg(args, int);
            if (flags & SIGN)
                num = (signed short) num;
        }
        else
        {
            num = va_arg(args, unsigned int);
            if (flags & SIGN)
                num = (signed int) num;
        }
        str = number(str, num, base, field_width, precision, flags);
    }
    *str = '/0';/*最后在转换好的字符串上加上NULL*/
    return str-buf;/*返回转换好的字符串的长度值*/
}
```

## 四、printf不可重入

Printf函数是不可重入的，因为vsprintf函数调用了全局变量sprint_buf[]，但是并且没有做任何边界保护，如果在多线程、或者中断程序中运行该函数，就难以避免资源重复抢占的问题。比如，线程A和线程B均调用了printf打印，线程A正在运行vsprintf函数，对sprint_buf正在操作中，此时被高优先级线程B抢占，B获取了sprint_buf的操作权，线程A生的数据就会被覆盖掉。

## 五、解决不可重入的方法

在嵌入式软件开发中经常会使用LogMsg打印，LogMsg可以自己编写，也可以借用操作系统的自带的,其根本的思想就是不同线程使用不同的sprint_buf缓存空间。主要方法有独立线程使用静态消息队列、申请动态内存、使用多组缓存空间等。