## 一、前言

最近打算写一些单片机程序，因此买了一块51开发板，打算写几个有趣的程序。

出于将学习和娱乐分开的目的，我把编程工作放在linux下来进行。

在linux下进行单片机的软件开发，要先安装专用的交叉编译器sdcc。接下来我会阅读sdcc的man文档，再结合一些简单的实验，来了解一下这款编译器。其目的有三，一是复习一些单片机的知识，为编程做点准备。二是理清sdcc的编译选项，好用来写makefile。三是弄明白sdcc和keil编译器的不同，这样可以把keil c的代码移植过来直接使用。

## 二、sdcc的安装

### 1.1 在ubuntun下安装sdcc

由于我的系统是ubuntun，因此可以直接使用apt-get命令来进行安装  

|   |   |
|---|---|
|1|$sudo apt-get install sdcc|

### 1.2 用其他方式安装sdcc

非ubuntun环境下，可以下载sdcc源码并编译生成sdcc，这样可以得到目前的最高版本。

sdcc源码的下载地址是 [http://sdcc.sourceforge.net/snap.php](http://sdcc.sourceforge.net/snap.php) 。

|   |   |
|---|---|
|1  <br>2  <br>3  <br>4  <br>5  <br>6|$tar -xvjf sdcc-src-yyyymmdd-rrrr.tar.bz2  <br>  <br>$cd sdcc  <br>$./configure  <br>$make  <br>$make install|

**sdcc man文件下载地址** [http://sdcc.sourceforge.net/doc/sdccman.pdf](http://sdcc.sourceforge.net/doc/sdccman.pdf)

## 三、sdcc包含的内容

安装完sdcc后可以分析一下sdcc一共包含哪些组成部分。

### 2.1 头文件和库文件

sdcc的头文件和库文件在 installdir/share/sdcc目录下，除此之外的所有bin文件包含在/bin目录下。

> installdir/share/sdcc/include  
> installdir/share/sdcc/lib
> 
> installdir/bin

installdir默认的值为/usr。

### 2.2 编译程序sdcc

编译程序sdcc，最常用到的命令，它所做的其实就是轮流调用预处理器、汇编器、连接器来完成编译工作。

### 2.3 预处理程序sdccp

这个预编译程序sdccp是直接用gcc的预编译程序的源码修改而来的，它被用来在编译前处理`#include #define `这些预编译指令。

### 2.4 汇编程序和链接程序sdas, sdld

sdas用来将C源码编译成汇编指令，sdld用来链接各目标文件的符号表。顺带一提man文档上说这两个程序都是基于**Alan Baldwin**的开源代码修改的，现在用的是它的2.0版本。**Alan Baldwin**已经将它的5.0版本开源，该老兄一直致力于编译器的研发工作。

### 2.5 仿真器

sdcc集成的仿真器包含s51, sz80 shc08 and sstm8系统，由**Daniel Drotos**开发，在他的网站上有详细的说明:

[http://mazsola.iit.uni-miskolc.hu/~drdani/embedded/s51](http://mazsola.iit.uni-miskolc.hu/~drdani/embedded/s51)

### 2.6 debug工具 sdcdb

sdcc用**Daniel Drotos**的仿真器进行debug，由于我有开发板，可以直接把程序烧上去。而且该款单片机没有j-tag接口，所以等有时间再来研究这个debug工具吧。

## 总结

- 在linux下进行单片机开发可以使用交叉编译器sdcc
- sdcc包含有一个编译程序、预处理程序、汇编程序和链接程序。
- sdcc还包含有一个集成的仿真器和debug工具。