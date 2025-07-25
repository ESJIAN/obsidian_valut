
## 1 Linux入门

### 1.1 概述

​ [Linux内核](https://so.csdn.net/so/search?q=Linux%E5%86%85%E6%A0%B8&spm=1001.2101.3001.7020)最初只是芬兰人Linux Torvalds在赫尔辛基大学上学时处于个人爱好而编写的。

​ Linux是一套免费使用和自 由传播的类[Unix操作系统](https://so.csdn.net/so/search?q=Unix%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F&spm=1001.2101.3001.7020)，是一个基于POSIX和UNIX的多用户、多任务、支持多线程和多CPU的操作系统。Linux能运行主要的UNIX工具软件、应用程序和网络协议。它支持32位和64位[硬件](https://marketing.csdn.net/p/3127db09a98e0723b83b2914d9256174?pId=2782&utm_source=glcblog&spm=1001.2101.3001.7020)。Linux继承 了Unix以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统。

​ 目前市面上较指明的发行版有：Ubunta、RedHat、CentOS，Debain、Fedora、SuSE、OpenSUSE。

### 1.2 Linux和Windows区别

![image-20220924195820555](https://i-blog.csdnimg.cn/blog_migrate/2d9e71344f8f2ef56766866789a24fcc.png)

#### 1.3 CentOs下载地址

网易镜像：https://mirrors.163.com/centos/7/isos/

搜狐镜像：https://mirrors.sohu.com/centos/7/isos/

## 2 VM与Linux的安装

具体安装步骤参考其他文章

## 3 Linux文件与目录

### 3.1 Linux文件

[Linux系统](https://so.csdn.net/so/search?q=Linux%E7%B3%BB%E7%BB%9F&spm=1001.2101.3001.7020)中一切皆文件

### 3.2 Linux目录结构

![image-20220924200453503](https://i-blog.csdnimg.cn/blog_migrate/2691ec2cf91f5a66959cd5b777eb0378.png)

|目录|含义|
|---|---|
|/bin|Binary的缩写，用来存二进制可执行文件，并且比较特殊的是/bin存放的是所有一般用户都能使用的可执行文件，如：cat、chmod、mv、mkdir、cd等常用指令|
|/sbin|Super User的意思，存放一些只有root用户才有权限执行的可执行文件，如init,ip,mount等命令|
|/boot|主要存放开机时用到的引导文件，如linux内核文件和开机菜单与开机所有需要的配置文件|
|/dev|device,任何设备都以文件的形式存放再这个目录中。例如硬盘、键盘、鼠标、光驱等各种设备文件。只要通过访问该目录的某个文件就相当于访问了对应的设备|
|/etc|配置文件、启动脚本等（etc)包含所有程序所需的配置文件以及系统的配置文件，如用户的账号密码文件，各个服务的起始文件等。也包含了用于启动/停止单个程序的启动和关闭shell脚本。一般来说，该目录下的文件属性是可以让用户查阅，但只有root管理员有权利修改|
|/home|系统默认的用户的家目录，每当新建一个用户系统都会在这个目录下创建以该用户名为名称的目录作为该用户的家目录。|
|/lib|library,存放着系统开机时所需的函数库以及/bin和/sbin目录下的命令会调用的函数库|
|/lib64|存放相对于/lib中支持64位格式的函数库|
|/media|存放可移除的媒体设备、如光盘，DVD等|
|/mnt|mount，临时挂载的设备文件，临时安装目录，系统管理员可以挂载文件系统。时系统管理员临时安装文件的系统安装点。|
|/opt|optional，可选的软件包，即第三方文件软件。我们可以将除了系统自带软件之外的其他软件安装到这个目录。|
|/proc|特殊的动态目录，用以 维护系统的信息和状态，包括当前运行中进程（processes)信息。包含系统进程的相关信息，是一个虚拟的文件系统，包含有关正在运行的进程的信息，系统资源以文本信息形式存在。|
|/root|系统管理员root的主目录|
|/run|最近一次开机后所产生的各项信息，如当前的用户和正在运行中的守护进程等。|
|/srv|service,存放一些服务启动后所需的数据|
|/sys|system,与/proc类似也是虚拟文件系统，存放系统核心与硬件相关信息管理设备文件。不占用硬件容量。|
|/tmp|temporary, 存放系统运行过程中使用的一些临时文件，可以被所有就用户访问，系统重启时会清空该目录。|
|/usr|包含绝大部分所有用户（users)都能访问的应用程序和文件包含二进制文件，库文件。文档和二级程序的源代码。|
|/var|经常变化的（variable)文件，诸如日志或数据库等代表变量文件。在这个目录下可以找到内容可能增长的文件|

## 4.VI/VIM 编辑器

### 4.1 VIM是什么

​ VI是Unix操作系统和类Unix操作系统中最通用的文本编辑器。

​ VIM编辑器是从V1从发展出来的一个[性能](https://marketing.csdn.net/p/3127db09a98e0723b83b2914d9256174?pId=2782&utm_source=glcblog&spm=1001.2101.3001.7020)更强大的文本编辑器。可以主动的以文字颜色辨别语法的正确性，方便程序设计。VIM与VI编辑器完全兼容。

### 4.2 模式转换

vim的界面分为一般模式（快速编辑、光标跳转）、插入模式（编辑文本）、指令模式（搜索、替换）

### 4.3 一般模式

|语法|功能描述|
|---|---|
|yy|复制光标当前一行|
|y数字y|复制一段（从第几行到第几行）|
|y (shift + 4)|复制当前光标到结尾的字符串|
|p|箭头移动到目的行粘贴|
|u|撤销上一步|
|dd|删除光标当前行|
|d数字d|删除光标（含）后多少行|
|x|剪切一个字母，相当于del|
|X|剪切一个字母，相当于Backspace|
|w|切换到下一个词|
|e|快速到下一个词尾|
|d|跳转到上一个词|
|yw|复制一个词|
|dw|删除一个词|
|shift+6|移动到行头|
|shift+4|移动到行尾|
|gg|移动到页头|
|G/L|移动到页尾|
|数字+shift+g|移动到目标行|
|b|跳转到上一个词|
|数字b|跳转到上n个词|

**显示行号** :set nu

不显示行号 :set nonu

### 4.4 插入模式

​ 在一般模式中可以进行删除、复制、粘贴等的动作，但是却无法编辑文件内容的！要 等到你按下『i, I, o, O, a, A』等任何一个字母之后才会进入编辑模式。

​ 注意了！通常在Linux中，按下这些按键时，在画面的左下方会出现『INSERT或 REPLACE』的字样，此时才可以进行编辑。而如果要回到一般模式时， 则必须要按下 『Esc』这个按键即可退出编辑模式。

**1）进入编辑模式**

|按钮|功能|
|---|---|
|i|当前光标前|
|a|当前光标后|
|o|当前光标行的下一行|
|I|光标所在行最前|
|A|光标所在行租后|
|O|当前光标行的上一行|

2）退出编辑

​ 按【ESC】键退出编辑弄湿，之后所在的模式为一般模式

### 4.5 指令模式

​ 在一般模式当中，输入【`:/?`】3个中的任何一个按钮，就可以将光标移动到最底下的一行

​ 在这个模式当中，可以提供【搜索】资料的动作，读取、淳朴、大量取代字符、离开vi、显示行号等动作是在此模式中达成的。

#### 1）基本语法

|命令|功能|
|---|---|
|:w|保存|
|:q|退出|
|:wq|保存并退出|
|:q!|不保存强制退出|
|/要查找的词|n查找下一个，N往上查找|
|:noh|取消高亮显示|
|:set nu|显示行号|
|:set nonu|关闭显示行号|
|`:s /old/new`|替换当前行匹配到第一个old为new|
|`:s /lod/new/g`|替换当前行匹配到所有old为new|
|:%s/old/new|替换文档中每一行匹配到的第一个old为new|
|:%s/old/new/g|替换文档中的所有的old为new 比较常用|

![image-20220512234008290](https://i-blog.csdnimg.cn/blog_migrate/6625ee204a27b95b2fe45f52500d6742.png)

### 4.6 模式之间转换

![image-20220512160155965](https://i-blog.csdnimg.cn/blog_migrate/303a1101fda7c2a64975e2cfb29232c2.png)

## 5. 网络配置和系统管理操作

### 5.1 查看网络IP和网关

#### 1）查看虚拟网络编辑

windows查看ip

```
ipconfig
```

#### 2）虚拟机网卡配置

##### 桥接模式

​ 虚拟机直接连接外部物理网络的模式，主机起到了网桥的作用。这个模式下直接访问外部网络，并且对外部网络是可见的。（同一个路由器内都可见，占用局域网的ip）

##### NAT模式（Network Address Translation）

​ 虚拟机和主机构建一个专用网络，并通过虚拟网络地址转换（NAT）设备对IP进行转换。虚拟机通过该共享IP可以访问外部网络，但外部网络无法访问虚拟机。

##### 仅主机模式

​ 虚拟机只与主机共享一个专用网络，与外部网络无法通信。

#### 3）查看网关

```
ifconfig
```

### 5.2 配置网络ip

修改为静态IP

```bash
 cd /etc/sysconfig/network-scripts
 vim ifcfg-#按tab键补充
```

> 说明：`ifcfg-`前缀的文件的可能会有好几种情况，例如：`ifcfg-eth0`、`ifcfg-ens33`、`ifcfg-ens192`

```bash
BOOTPROTO="dhcp"
修改为 
BOOTPROTO="static"
#IP地址
IPADDR=192.162.202.100
# 网关
GATEWAY=192.168.202.2
# 域名解析器
DBS1=192.168.202.2
```

重启网络服务

```重启网卡
server network restart
```

![image-20220513234505448](https://i-blog.csdnimg.cn/blog_migrate/48bc0cc29c4050bbf567586016b16f2c.png)

### 5.3 配置主机名

#### 5.3.1 修改主机名称

```bash
# 查看主机名
hostname

vim /ect/hostname  
修改里面的值
# 重启服务器

# 查看主机相关信息
hostnamectl
# 修改主机名为lys
hostnamectl set-hostname lys
```

#### 5.3.2 修改hosts映射文件

1）修改linux的主机映射文件（hosts文件）

​ 说明：后续在虚拟机多的情况时，配置时通畅会采用主机名的方式配置

```bash
vim /etc/hosts
```

windows

```
C:\Windows\System32\drivers\etc\hosts
```

## 6. 远程登录

windows 命令行连接

```bash
ssh root@11.212.33.44 
# 或
ssh zhangsan@11.212.33.44 -p Port
```

或者使用Xshell

## 7. 系统管理

### 7.1 Linux中的进程和服务

​ 计算机中，一个正在执行的程序或命令，被叫做"进程"（process）

​ 启动之后一直存在、常驻内存的进程，一般被称做“服务”（service）

### 7.2 service 服务管理 （CentOS 6 版本了解）

```
ls /usr/sbin/ | grep service
```

1） 基本语法

​ service 服务名 start | stop | restart | status

2）经验技巧

​ 查看服务的方法：`ls /etc/init.d/`

3）案例实操

（1）查看网络服务的状态

```bash
service network status
```

（2）停止网络服务

```bash
service network stop
```

（3）启动网络服务

```bash
service network start
```

（4）重启网络服务

```bash
service network restart
```

### 7.3 chkconfig 设置后台服务的自启配置（CentOS 6版本）

1） 基本语法

```
chkconfig （功能描述：查看所有服务器自启配置） 

chkconfig 服务名 off （功能描述：关掉指定服务的自动启动） 

chkconfig 服务名 on （功能描述：开启指定服务的自动启动） 

chkconfig 服务名 --list （功能描述：查看服务开机启动状态）
```

2）案例实操

（1）开启/关闭 network(网络)服务的自动启动

```bash
chkconfig network on
chkconfig network off
```

（2）开启/关闭 network 服务指定级别的自动启动

```
chkconfig --level 指定级别 network on
chkconfig --level 指定级别 network off
```

### 7.4 systemctl CentOS 7 版本-重点掌握）

1） 基本语法

​ systemctl start | stop | restart | status 服务名

2） 经验技巧

​ 查看服务的方法：`ls - al /usr/lib/systemd/system`

3）案例实操

（1）查看防火墙服务的状态

```bash
systemctl status firewalld
```

（2）停止防火墙服务

```bash
systemctl stop firewalld
```

（3）启动防火墙服务

```bash
systemctl start firewalld
```

（4）重启防火墙服务

```bash
systemctl restart firewalld
```

### 7.5 systemctl设置后台服务的自启配置

1）基本语法

systemctl list-unit-files （功能描述：查看服务开机启动状态）

systemctl disable service_name （功能描述：关掉指定服务的自动启动）

systemctl enable service_name （功能描述：开启指定服务的自动启动）

2）案例实操

（1）开启/关闭iptables（防火墙）服务的自动启动

```bash
systemctl enable firewalld.service
systemctl disable firewalld.service
```

### 7.6 系统运行级别

#### 1. linux运行级别

![image-20220515153151877](https://i-blog.csdnimg.cn/blog_migrate/39ead9dcc19c1fd85563b91187b07e8d.png)

Linux系统有7种运行级别（runlevel) 常用的级别3和5

- 0：系统停机状态，系统默认运行级别不能设为0，否则不能正常启动
- 1：单用户工作状态，root权限，用于系统维护，禁止远程登录
- 2：多用户状态（没有NFS），不支持网络
- 3：安全的多用户状态（有NFS），登录后进入控制台命令行模式
- 4：系统未使用，保留
- 5：X11控制台，登陆后进入图形GUI模式
- 6：系统正常关闭并重启，默认运行级别不能设为6，否则不能正常启动

#### 2. CentOS7的运行级别简化为：

multi-user.target 等价于原运行级别3（多用户有网，无图形界面）

graphical.target 等价于原运行级别5（多用户有网，有图形界面）

#### 3. 查看当前运行级别：

systemctl get-default

vim /etc/inittab

#### 4. 修改当前运行级别：

system set-default TARGET.target (这里的TARGET取 multi-user 或者graphical)

### 7.7 关闭防火墙

#### 1. 临时关闭防火墙

```bash
# 查看防火墙状态
systemctl status firewalld
systemctl stop firewalld
```

#### 2. 开机启动时关闭防火墙

```bash
# 查看防火墙开机启动状态
systemctl enable firewalld.service
# 设置开机时关闭防火墙
systemctl disable firewalld.service
```

查看服务是否开机自启动

```bash
systemctl list-unit-files
```

### 7.8 关机重启命令

```bash
# 一分钟后关机
shutdown
# 三分钟后关机
shutdown 3
# 某个时间关机
shutdown 15:00
# 取消关机
shutdown -c 
# 立刻关机
shutdown now
```

1. 基本语法
    
    1. sync 将数据由内存同步到硬盘中
    2. halt 停机，关闭系统，但不断电
    3. poweroff 关机，断电
    4. reboot 重启，等同于 shutdown-r now
    5. shutdown 【选项】 时间
2. 经验技巧
    

> Linux系统中为了提高磁盘的读写效率，对磁盘采取了 “预读迟写’'操作方式。当用户 保存文件时，Linux核心并不一定立即将保存数据写入物理磁盘中，而是将数据保存在缓 冲区中，等缓冲区满时再写入磁盘，这种方式可以极大的提高磁盘写入数据的效率。但是， 也带来了安全隐患，如果数据还未写入磁盘时，系统掉电或者其他严重问题出现，则将导 致数据丢失。使用sync指令可以立即将缓冲区的数据写入磁盘。

3. 案例实操
    
4. 将数据由内存同步到硬盘中
    

```bash
sync
```

2. 重启

```bash
reboot
```

3. 停机（不断电）

```bash
halt
```

4. 计算机在1分钟后关机，并且会显示在登录用户的当前屏幕中

```bash
shutdown -h 1
```

5. 立马关机

```bash
shutdown -h now
```

6. 系统立马重启（等同于reboot）

```bash
shutdown -r now
```

## 8 常用基本命令

​ Shell可以看做是一个命令解释器，为我们提供了交互式的文本控制台界面，我们可以通过终端控制台来输入命令，由shell进行解释并最终交给内核执行

### 8.1 帮助命令

#### 8.1.1 man 获取帮助信息

1. 基本语法
    
    man [命令或配置文件] 获取帮助信息
    
    ```bash
    man -f cd
    cd (1)               - bash built-in commands, see bash(1)
    cd (n)               - Change working directory
    [root@lys ~]# man 1 cd # 1为上面的括号显示
    ```
    
2. 显示说明
    

|信息|功能|
|---|---|
|NAME|命令的名称和单行描述|
|SYNOPSIS|怎样使用命令|
|DESCRIPTION|命令功能的深入讨论|
|EXAMPLES|怎样使用命令的例子|
|SEE ALSO|相关主题（通常是手册页）|

#### 8.1.2 help 获取shell内置命令的帮助信息

​ 一部门基础功能的系统命令是直接内嵌在shell中，系统加载启动之后会随着shell一起加载，常驻系统内存中。这部门命令被称为“内置（built-in）命令”；相应的其他命令被称为“外部命令”

判断是否内置命令

```bash
type cd
cd is a shell builtin
```

1. 基本语法
    
    help 命令 获得shell内置命令的帮助信息
    
2. 案例实操
    
    - 查看cd命令的帮助信息 `help cd`

#### 8.1.3 常用快捷键

|常用快捷键|功能|
|---|---|
|ctrl + c|停止进程|
|ctrl + l|清屏，等同于clear;彻底清屏是： reset|
|tab|提示（更重要的是可以防止敲错）|
|上下键|查找执行过的命令|

### 8.2 文件目录类

#### 8.2.1 pwd显示当前工作目录的绝对路径

pwd: print working directory 打印工作目录

##### 1. 基本语法

​ pwd 显示当前工作目录的绝对路径

#### 8.2.2 ls 列出目录的内容

ls: list 列出目录内容

1）基本语法

​ ls [选项] [文件或目录]

2. 选项说明

|选项|功能|
|---|---|
|-a|全部的文件，连同隐藏文档（开头为.的文件） 一起|
|-l|长数据串列出，包含文件的属性与权限等等数据（常用）等价于“ll”|
|-lh|文件大小比较好看|

3）显示说明

​ 每行列出的信息依次是：文件类型与权限 链接户 文件属性 文件大小用byte来标识 建立或最近修改的时间 名字

#### 8.2.3 cd 切换目录

cd Change Directory 切换目录

|参数|功能|
|---|---|
|cd 绝对路径|切换路径|
|cd 相对路径|切换路径|
|cd ~ 或 cd|回到自己的家目录|
|cd -|回到上一次所在目录|
|cd …|回到当前沐浴露的上一级目录|
|cd -P|跳转到实际物理路径，而非快捷方式路径|

#### 8.2.4 mkdir创建一个新的目录

```bash
# 创建目录
mkdir a 

# 一次创建多级
mkdir a a/b a/b/c
mkdir -p a/b/c
```

#### 8.2.5 rmdir删除一个空的目录

```bash
# 删除目录
rmdir a

# 删除多级目录
rmdir a/b/c
```

#### 8.2.6 创建空文件

1） 基本语法

​ touch 文件名称

#### 8.2.7 cp复制文件或目录

```bash
cp [选项] source dest

cp nginx.conf nginx.conf2

# 递归复制整个文件夹

cp -r logs logs2

# 不强制覆盖使用  
\cp

# 查看别名
alias
```

#### 8.2.8 rm 删除文件或目录

rm [选项] deleteFile [递归](https://edu.csdn.net/course/detail/40020?utm_source=glcblog&spm=1001.2101.3001.7020)删除目录中所有内从

|选项|功能|
|---|---|
|-r|递归删除目录中所有内容|
|-f|强制执行删除操作，而不提示用于进行确认|
|-v|显示指令的详细执行过程|

```bash
#删除文件
rm test.txt
# 递归删除
rm -r dir
# 强制删除
rm -f dir
```

>**提示**：可以配合[[2. 语法]]

#### 8.2.9 mv 移动文件或目录或重命名

`mv oldNameFile newNameFile `重命名

`mv /tmp/moveFile /targerFolder `移动文件

#### 8.2.10 cat 查看文件内容

cat [选项] 要查看的文件

cat -n 文件名 显示所有行的行号，包括空行

#### 8.2.11 more 文件内容分屏查看器

​ more指令是一个基于VI编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容，more指令中内置若干快捷键

|操作|功能说|
|---|---|
|空白键（space）|代表向下翻一页|
|Enter|代表向下翻一行|
|q|立刻离开 more|
|ctrl + F|向下滚动一屏|
|ctrl + B|返回上一屏|
|=|输出当前行的行号|
|:f|输出文件名和当前行行号|

#### 8.2.12 less 分屏显示文件内容 （查看大文件）

​ less指令永爱分屏查看文件内容，它的功能与more指令类似，但是比more指令更加强大，支持各种显示终端。less指令在显示文件内容时，不是一次将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示大型文件具有较高的效率。

```
less 文件名
```

|操作|功能说明|
|---|---|
|空白键|向下翻动一页|
|pagedown|向下翻动一页|
|pageup|向上翻动一页|
|/字符串|向下搜寻【字符串】的功能：n:向下查找 N：向上查找|
|？字符串|向上搜寻【字符串】的功能：n 向上查找 N 向下查找|
|q|离开less这个程序|

#### 8.2.13 echo

​ echo 输出内容到控制台

​ echo 【选项】【输出内容】

​ -e: 支持反斜线控制的字符转换

|控制字符|作业|
|---|---|
|\|输出\本身|
|\n|换行符|
|\t|制表符，也就是Tab键|

查看系统环境变量

```bash
echo $ + Tab键
```

#### 8.2.14 head 显示文件头部内容

head用于显示文件的开头部门内容，默认情况下 head指令显示文件的前10行内容。

1）基本语法

​ head 文件名 查看文件头10行内容

​ head -n 5 文件 查看文件头5行内容

#### 8.2.15 tail 输出文件尾部

tail -n 5 文件名

tail -f 文件

- 按Ctrl + S 可以暂停监听
    
- 按Ctrl + Q 可以继续监听
    

查看文件索引

ls -i web.log

#### 8.2.16 输出重定向和 >> 追加

- ls -l > a.txt （功能描述：列表的内容写入文件 a.txt 中（**覆盖写**））
- ls -al >> aa.txt （功能描述：列表的内容**追加**到文件 aa.txt 的末尾）
- cat 文件 1 > 文件 2 （功能描述：将文件 1 的内容覆盖到文件 2）
- echo “内容” >> 文件

#### 8.2.17 ln 软连接

​ 软连接（link）也称为符号链接，类似于windows里的快捷方式，有自己的数据块，主要存放了连接其他文件的路径

创建软连接

```bash
[root@lys logs]# ln -s web.log web
[root@lys logs]# ll
total 7988
-rw-r--r-- 1 root root  115498 May 13 11:04 gateway.log
lrwxrwxrwx 1 root root       7 May 16 00:36 web -> web.log # 软连接的前缀为l
-rw-r--r-- 1 root root 8048944 May 16 00:36 web.log
```

直接进入软连接对应的地址

```bash
cd -P 软连接 
```

删除软连接: rm -rf 软连接名，而不是rm -rf 软连接名/

**!!! 如果使用rm -rf 软连接/ 删除，会把软连接对应的真实目录下内容删掉**

硬连接 （相当于）

```bash
ln 文件名 链接名
```

#### 8.2.18 history 查看已经执行过历史命令

```bash
# 查看历史命令
history
# 情况历史命令
history -c
```

### 8.3 时间日期类

1. 基本语法

date [option] + [format]

date -s 日期时间 设置日期时间

date + “日期时间格式” 指定显示时使用的日期

#### 8.3.1 date显示当前时间

- date
- date + %Y
- date + %m
- date + %d
- date “+%Y-%m-%d %H:%m:%S”
- date +%Y-%m-%d %H:%m:%S
- date +%s 查看时间戳
- date -d “-1 hours ago” 一个小时后的时间

设置系统当前时间

```bash
date -s "2022-06-19 20:52:22"
```

同步时间

```bash
ntpdate -u ntp1.aliyun.com
```

#### 8.3.4 cal查看日历

cal [选项] 不加选项，显示本月日历

- cal -3 查看3个月的时间
- cal -m 周一放在第一天
- cal 2022 查看2022年日历
- cal 查看本年度日历

### 8.4 用户管理命令

```bash
# useradd 用户名 添加新用户
useradd lys
# 可以在home目录看到创建的用户文件夹
cd /home
# 创建时修改主文件夹名称
useradd -d /home/dave david
# 设置密码
passwd lys

# 查看用户信息,可以验证是否存在
id lys
uid=1005(lys) gid=1005(lys) groups=1005(lys)

# 查看系统用户
less /etc/passwd

# 切换用户 su: switch user
su lys
# 在lys用户退出可回到root用户
exit

# 查看当前用户
who am i

# 删除用户
userdel lys
# 删除用户以及文件夹
userdel -r lys

# sudo设置普通用户具有root权限
vim /etc/sudoers
# 添加
lys     ALL=(ALL)       ALL
# 使用超级管理员权限
sudo lys
# 将用户添加入某个组
usermod -g 组名 用户名
```

### 8.5 用户组管理命令

​ 每个用户都有一个用户组，系统可以对一个用户组中的所有用户进行集中管理。不同Linux系统对用户组的规则有所不同，

​ 如Linux下的用户属于与它同名的用户组，这个用户在和创建用户时同时创建。

​ 用户组的管理设计用户组的添加、删除和修改。组的增加、删除和修改实际上就是对/etc/group文件的更新

```bash
# 新增组
groupadd 组名

# 修改组名
groupmod -n 新组名 旧组名

# 删除用户组
groupdel 组名
```

### 8.6 文件权限类

#### 7.6.1 文件属性

​ Linux系统是一种典型的多用户系统，不同的用户处于不同的地位，拥有不同的权限。为了保护系统的安全性，Linux系统对不同的用户访问同一文件（包括目录文件）的权限做了不同的规定。在Linux中我们可以使用ll 或者ls -l来显示一个文件的属性以及文件所属的用户和组

1. 从左到有的10个字符标识

![image-20220517231040047](https://i-blog.csdnimg.cn/blog_migrate/d29ddbff29b4ed5c76c7b2c97be35def.png)

如果没有权限，就会出现减号[-]而已，从左至右用0-9这些数字赖标师

(1)0首位表示类型

​ 在Linux中第一个字符代表这个文件是目录、文件或链接文件

```
-  - 代表文件
-  d 代表目录
- l  链接文档 （link file）
```

(2) 第1-3位确定属主（该文件的所有者）拥有该文件的权限。User

(3)第4-6位确定属组（所有者的同组用户）拥有该文件的权限。Group

(4) 第7-9位确定其他用户拥有该文件的权限 Other

2. rwx作用文件和目录的不同解释
    
    作用到文件：
    
    【r】: 代表可读（read) 可以读取，查看
    
    【w】：代表可写（write) 可以修改，但是不代表可以删除该文件，删除一个文件的前提条件是对该文件所在的目录有写权限，才能删除该文件
    
    【x】：代表可执行(execute) 可以被系统执行
    
    作用到目录:
    
    【r】: 代表可读（read) 可以读取，ls查看目录内容
    
    【w】：代表可写（write) 可以修改，目录内创建+删除+重命名目录
    
    【x】：代表可执行(execute) 可以进入该目录
    

文件基本属性介绍

![image-20220517232953855](https://i-blog.csdnimg.cn/blog_migrate/6ad69e1cc12db4ee1bc5563a8d97aa97.png)

（1）如果查看到是文件：链接数指的是硬链接个数。

（2）如果查看的是文件夹：链接数指的是子文件夹个数。

#### 8.6.2 chmod 改变权限

![image-20220517233623454](https://i-blog.csdnimg.cn/blog_migrate/e9c03c812fc61820c3c7519cf2058a8f.png)

示例

```bash
# 增加执行权限
chmod +x nginx.conf

# chmod [u|g|o|a] +-= {rwx} 文件或目录
chmod u+x nginx.conf
chmod u-x nginx.conf
chmod u=x nginx.conf
chmod a+x nginx.conf
chmod a=rwx nginx.conf

# r=4 w=2 x=1
# 直接用数字修改权限
chmod 777 nginx.conf

# 修改整个文件夹的所有这，所属组，其他用户都具有可读可写可执行权限
chmod -R 777 nginx.conf
```

#### 8.6.3 chown 改变所有者

chown 改变所有者

chown [选项] [最终用户] [文件或目录]

```bash
chown lys a.txt
# 获取递归改变文件所有者和所有组
chown -R lys dir
```

#### 8.6.4 charp 改变所有组

chgrp [最终用户组] [文件或目录]

chgrp root a.txt

### 8.7 搜索查找类

#### 8.7.1 find 查找文件或目录

​ find 指令将从指定目录向下递归地遍历其各个子目录

find [搜索范围] [选项]

|选项|功能|
|---|---|
|-name 查询方式|按照指定文件名查找模式查找文件|
|-user 用户名|查找属于指定用户名所有文件|
|-size 文件大小|按照指定文件大小查找文件，单位为 b-块 （512字节） c- 字节 w-字 2字节 k - 千字节 M -兆字节 G-吉字节|

```bash
# 按名称查找
find -name nginx.conf

# 按路径加名称查找
find /root -name nginx.conf

# 按照后缀查找
# "*"匹配多个字段,"?"匹配单个字符
find -name "*.txt"

# 按用户查找
find -user lys

# 按大小查找 +大于 -小于
find -size +1M
find -size +1M
```

#### 8.7.2 locate 快速定位文件路径

​ local指令利用事先简历的系统中所有文件名称及路径的locate数据库事先快速定位给定的文件。Locate指令无需遍历整个文件系统，查询速度较快。为了保证查询结果的准确度，管理员必须定期更新locate时时刻。

​ locate 搜索文件

​ 由于locate指令基于数据库进行查询，所以第一此运行前，必须使用updatedb指令创建locate数据库

```bash
updatedb
locate nginx.conf
# 查看指令所在位置
which ls
whereis locate
```

#### 8.7.3 grep过滤查找及"|"管道符

​ 管道符，|，表示将前一个命令的处理结果输出传递给后面的命令处理

grep 选项 查找内容 源文件

- -n 显示匹配行及行号

```bash
# 显示location在nginx.conf的哪几行
grep -n location nginx.conf 
# 查找某文件在该目录的第一个
ls | grep -n test
```

wc 查看单词数量

```
wc nginx.conf
136  302 3022 nginx.conf
行数  单词数量 字节数
```

### 8.8 压缩和压缩类

#### 8.8.1 gzip/gunip 压缩

gzip 文件

gunzip 文件.gz (解压缩文件命令)

- 只能压缩文件不能压缩目录
- 不保留原来的文件
- 同时多个文件会产生多个压缩包

示例

```bash
gzip nginx.conf
gunzip nginx.conf
gzip nginx.conf nginx.conf2
```

#### 8.8.2 zip/unzip压缩

​ zip压缩命令在window/linux都通用，可以压缩目录且保留源文件

zip [选项] XXX.zip 压缩文件和目录命令

unzip [选项] XXX.zip 解压缩文件

- zip -r 压缩目录
- unzip -d 指定解压后文件的存放目录

```bash
# 将logs压缩成logs.zip
zip -r logs.zip logs/

# 解压logs.zip
unzip -d ./tmp logs.zip 
```

#### 8.8.3 tar打包

tar [选项] XXX.tar.gz 打包目录，压缩后的文件格式 .tar.gz

|选项|功能|
|---|---|
|-c|产生.tar打包文件|
|-v|显示详细信息|
|-f|执行压缩后的文件名|
|-z|打包同时压缩|
|-x|解压.tar文件|
|-C|解压到指定目录|

```bash
# 压缩单个文件
tar -zcvf nginx.tar.gz nginx.conf
# 压缩多个文件
tar -zcvf nginx.tar.gz nginx.conf nginx.conf2
# 解压文件
mkdir tmp
tar -zxvf nginx.tar.gz -C tmp/
```

### 8.9 磁盘查看和分区类

![](https://i0.hdslb.com/bfs/openplatform/34be318744e3688c35ad6997b76bfeaf648ecf34.png)

>**解读**：先将设备挂载到设备点下（形如 sda ），而分区挂载类似设备挂在，只不过在字母名后面会跟上数字序号（形如sda1），然后再把设备点与文件挂载点（形如/mnt/sata1-1）设置好映射关系。


#### 8.9.1 du 查看文件和目录占用的磁盘空间

​ du: disk usage 磁盘占用情况

du 目录/文件 显示目录下每个子目录的磁盘使用情况

|选项|功能|
|---|---|
|-h|以人们较易预读的G,M、k等格式自行显示|
|-a|不进查看子目录大小，还要包括文件|
|-c|显示所有的文件和子目录大小后，显示总和|
|-s|只显示总和|
|-max-depth=n|指定统计子目录的深度为第nc层|

tree 工具

示例

查看当前用户主目录占用的磁盘空间大小

```bash
du -sh # 查看当前路径文件大小
# 子查看一级子目录
du --max-depth=1 -ah

```

#### 8.9.2 df查看磁盘空间使用情况

df: disk free 空余磁盘

df 选项 列出文件系统的整体磁盘使用量，检查文件系统的磁盘空间占用情况

df -h 以人们较阅读的格式自行显示

#### 8.9.3 lsblk 查看设备挂载情况

- lsblk
    
- lsblk -f 查看详细的设备故障情况，显示文件系统信息
    

#### 8.9.4 **mount/umount** 挂载/卸载

​ 对于Linux用户来讲，不论有几个分区，分别分给哪一个目录使用，它总归就是一个根目录、一个独立且唯一的文件结构。

​ Linux中每个分区都是用来组成整个文件系统的一部门，它在用一种叫挂载的处理方法，它整个文件系统中包含了一整套的文件和目录，并将一个分区和一个目录联系起来，要载入的那个文件将它的存储空间在这个目录获得,

mount [-t vfstype] [-o options] device dir （功能描述：挂载设备）

umount 设备文件名或挂载点 （功能描述：卸载设备）

|参数|功能|
|---|---|
|-t vfstype|指定文件系统的类型，通常不必指定。mount会自动选择类型。常用类型有：光盘或光盘镜像 DOS Windows9x fat32文件系统：vfat Windows NT ntfs 文件系统： ntfs Mount Windows 文件网络共享：smbfs UNIX(LINUX)文件共享：nfs|
|-o options|主要用来描述设备或档案的挂接方式。常用的参数有: loop 用来把一个文件当成硬盘分区挂接上系统 ro:采用只读方式挂接设备 rw:采用读写方式挂接设备 iocharset: 指定访问系统所用字符集|
|device|要挂接的设备|
|dir|设备在系统上的挂载点|

设置开机自启动

vi /etc/fstab

![image-20220522152433537](https://i-blog.csdnimg.cn/blog_migrate/f971ef17b5bfbd3eb861d562d06c33db.png)

#### 8.9.5 fdisk分区

fdisk -l 查看磁盘分区详情

fdisk 硬盘设备名 （显示所有硬盘的分区列表）

（1）Linux 分区

Device：分区序列

Boot：引导

Start：从X磁柱开始

End：到Y磁柱结束

Blocks：容量

Id：分区类型ID

System：分区类型

（2）分区操作按键说明

m：显示命令列表

p：显示当前磁盘分区

n：新增分区

w：写入分区信息并退出

q：不保存分区信息直接退出

### 8.10 进程管理类

​ 进程是正在执行的一个程序或命令，每一个进程都是一个运行的实体，都有自己的地址空间，并占用着一定的系统资源

#### 8.10.1 ps 查看当前系统进程状态

​ ps: process status 进程状态

- ps aux | grep XXX 查看系统中带XXX的进程
- ps -ef | grep XXX 可以查看子父今后进程之间的关系

|选项|功能|
|---|---|
|a|列出带有终端的所有用户的进程|
|x|列出当前用户的所有今后进程，包括没有终端的进程|
|u|面向用户友好的显示风格|
|-e|列出所有进程|
|-u|列出某个用户关联的所有进程|
|-f|显示完整格式的进程列表|

```bash
ls /usr/lib/systemd/system
# 带d.service的为守护进程
ls /usr/lib/systemd/system | grep d.service
```

```bash
ps aux | less
ps -ef | less
```

##### 1. ps aux显示信息说明

USER：该进程是由哪个用户产生的

PID: 进程的ID号

%CPU: 该进程占用CPU资源的百分比，占用越高，进程越耗费资源；

%MEM: 该进程占用物理内存的百分比，占用越高，进程越耗费资源；

VSZ: 该进程占用虚拟内存的大小，单位KB;

RSS: 该进程占用实际物理内存的大小，单位KB;

TTY: 该进程是哪个终端中运行的。对于CentOS来说，tty1是图形化终端，tty2-tty5是本地的字符界面终端。pts/0-255代表虚拟终端。

STAT: 进程状态。常见的状态有：

​ R:运行状态 S:睡眠状态 T: 暂停状态 Z:僵尸状态 s:包含子进程 l: 多线程 +:前台显示 <：高优先级 N:低优先级

START: 该进程的启动时间

TIME：该进程占用CPU的运算时间，注意不是系统时间

COMMAND：产生此进程的命令名

##### 2. ps -ef 显示信息说明

UID: 用户ID

PID: 进程ID

PPID: 父进程ID

C: CPU用于计算执行优先级的因子。数字越大，表明进程是CPU密集型运算，执行优先级会降低；数字越小，表明进程是I/O密级型运算，执行优先级会提高

STIME：进程启动的时间

TIY:完成的终端名称

TIME: CPU时间

CMD: 启动进程所用的命令和参数

> 如果是想查看进程CPU占用率和内存占用率，可以使用aux
> 
> 如果想查看进程的父进程ID可以使用ef;

#### 8.10.2 kill 终止进程

kill [选项] 进程号 通过进程号杀死进程

killall 进程名称 通过进程名称杀死进程，也支持通配符，这在系统因负载过大而变得很慢时很有用

|选项|功能|
|---|---|
|-9|表示强迫进程立即停止|

kill -l 查看各个号码代表的意思

#### 8.10.3 pstree 查看进程树

pstree [选项]

|选项|功能|
|---|---|
|-p|显示进程PID|
|-u|显示进程的所属用户|

- pstree
- pstree -p
- pstree -u

#### 8.10.4 top实施监控系统进程状态

top [选项]

|选项|功能|
|---|---|
|-d 秒数|指定top命令每隔几秒更新。默认是3秒在top命令的交互模式当中可以执行|
|-i|使top不显示任何闲置或者僵死进程。|
|-p|通过指定进程ID来仅仅监控某个进程的状态|

|操作|功能|
|---|---|
|P|以CPU使用率排序，默认就是此项|
|M|以内存的使用率排序|
|N|以PID排序|
|q|退出top|
|u|根据指定用户进行过滤|
|k|直接杀死|

> top详细内容，参考文章[Linux之top命令详解](https://blog.csdn.net/weixin_43811294/article/details/130002316)

#### 8.10.5 netstat 显示网络状态和端口占用信息

|选项|功能|
|---|---|
|-a|显示所有正在监听（listen）和未监听的套接字（socket)|
|-n|拒绝显示别名，能显示数字的全部转化为数字|
|-l|仅列出在监听的服务状态|
|-p|表示显示哪个进程在调用|

- netstat -anp | grep 进程号 查看该进程网络信息
- netstat -nlp | grep 端口号 查看网络端口号占用情况
- netstat -atnp 查看连接

根据端口号查进程ID

```bash
netstat -tlnp | grep <端口号>
# 示例
netstat -tlnp | grep 3658
tcp6       0      0 127.0.0.1:3658          :::*                    LISTEN      20753/java  
# 20753就为进程id
```

根据进程id查占用端口

```bash
netstat -nlp | grep <pid>  | grep LISTEN
# 示例
netstat -nlp | grep 12564 | grep LISTEN
tcp6       0      0 :::49999                :::*                    LISTEN      12564/java          
unix  2      [ ACC ]     STREAM     LISTENING     572295240 12564/java           /tmp/.java_pid12564.tmp
# 说明该进程占用的端口号为49999
```

### 8.11 crontab 系统定时任务

#### 8.11.1 crontab服务管理

重启cornd服务管理

```bash
systemctl restart crond
```

选项说明

|选项|功能|
|---|---|
|-e|编辑crontab定时任务|
|-l|查询crontab任务|
|-r|删除当前用户所有的crontab任务|

进入编辑界面

```bash
crontab -e
# 小例子 每分钟往hello文件追加一个"hello world"
*/1 * * * * echo "hello world" >> /root/hello
```

|项目|含义|范围|
|---|---|---|
|第1个“*"|一个小时当中的第几分钟|0-59|
|第2个“*"|一天当中的第几个小时|0-23|
|第3个“*"|一个月当中的第几天|1-31|
|第4个“*"|一年当中的第几月|1-12|
|第5个“*"|一周当中的星期几|0-7 （0和7都代表星期日）|

符号说明

|特殊符号|含义|
|---|---|
|*|代表任何时间，比如第一个“*”就代表一小时中每分钟都执行一次的意思|
|，|代表不连续的时间。比如“0 8,12,16 * * *” 就代表在每天的8点0分，，12点0分，16点0分都执行一次命令|
|-|代表连续的时间访问。比如“0 5 * * 1-6" 代表在周一到周六的凌晨5点0分执行命令|
|*/n|代表每隔多久执行一次，比如”*/10 * * * *" 命令，代表每隔10分钟就执行一边命令|
|||

示例

|45 22 * * *|每天22点45分执行命令|
|---|---|
|0 17 * * 1|每周1的17点0分执行命令|
|0 5 1,15 * *|每月1号 15号的凌晨5点0分执行命令|
|40 4 * * 1-5 命令|每周一到周五 4点40分执行命令|
|*/10 4 * * *|每天的凌晨4点，每隔10分钟执行一次命令|
|0 0 1,15 * 1 命令|每月1号和15号，每周1的0点0分都会执行命令。注意：星期几和几号最好不要同事出现，因为他们定义的都是天。非常容易让管理员混乱|

## 9 软件包管理

### 9.1 RPM

#### 9.1.1 RPM概述

​ RPM(RedHat Package Manager),RedHat软件包管理工具，类似于windows里面的setup.exe，是Linux这系列操作系统的打包安装工具，它虽然是RedHat的标志，但理念是通用的。

​ RPM包的名称格式

​ Apache-1.3.23-11.i386.rpm

​ “apache” 软件名称

​ “1.3.23-11”软件的版本号，主版本和此版本

​ “i386”是软件所运行的硬件平台，Intel 32位处理器的统称

​ “rpm”文件扩展名，代表RPM包

#### 9.1.2 RPM查询命令 （rpm -qa)

rpm -qa 查询所安装的所有rpm软件包

由于软件包比较多，一般都会才去过滤 rpm -qa | grep 名称

查询具体信息

```
rpm -qi unzip-6.0-24.el7_9.x86_64
```

#### 9.1.3 RPM 卸载命令 （rpm -e)

rpm -e 名称 卸载软件包

rpm -e --nodeps 名称 卸载软件时，不检查依赖。这样的话，那些使用该软件包的软件在此之后可能就不能正常工作

卸载firefox

```bash
rpm -e firefox
```

#### 9.1.4 安装命令 (rpm -ivh)

rpm -ivh 包全名

|选项|功能|
|---|---|
|-i|install 安装|
|-v|–verbose 显示详细信息|
|-h|–hase，进度条|
|–nodeps|安装前不检查依赖|

安装firefox

```bash
rpm -ivh firefox-45.0.1-1.el6.centos.x86_64.rpm
```

### 9.2 仓库配置

#### 9.2.1 YUM概述

​ YUM(全称为 Yellow dog Updater, Modified)是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次 安装所有依赖的软件包，无须繁琐地一次一次下载，安装。

#### 9.2.2 YUM的常用命令

yum [选项] [参数]

|选项|功能|
|---|---|
|-y|对所有提问都回答“yes"|

|参数|功能|
|---|---|
|install|安装rpm 软件包|
|update|更新rpm软件包|
|check-update|检查是否有可用的更新rpm软件包|
|remove|删除指定的rpm软件包|
|list|显示软件包信息|
|clean|清楚yum过期的缓存|
|deplist|显示yum软件包的所有依赖关系|

yum方式安装firefox

```bash
yum list | grep firefox
# 卸载老版本
yum remove firefox
yum -y install firefox
```

#### 9.2.3 修改网络YUM源 (默认会自己搜索最近的)

​ 默认的系统 YUM 源，需要连接国外 apache 网站，网速比较慢，可以修改关联的网络 YUM 源为国内镜像的网站，比如网易 163,aliyun 等

(1)安装 wget, wget 用来从指定的 URL 下载文件

```bash
yum install wget
```

(2)在/etc/yum.repos.d/目录下，备份默认的 repos 文件

```bash
cd /etc/yum.repos.d
cp CentOS-Base.repo CentOS-Base.repo.backup
```

（3）下载网易 163 或者是 aliyun 的 repos 文件,任选其一

```bash
wget http://mirrors.aliyun.com/repo/Centos-7.repo # 阿里云
wget http://mirrors.163.com/.help/CentOS7-Base-163.repo # 网易
```

（4）使用下载好的 repos 文件替换默认的 repos 文件 例如:用 CentOS7-Base-163.repo 替换 CentOS-Base.repo

```bash
mv CentOS7-Base-163.repo CentOS-Base.repo
```

（5）清理旧缓存数据，缓存新数据

```bash
yum clean all
yum makecache
```

yum makecache 就是把服务器的包信息下载到本地电脑缓存起来

(6)测试

```bash
yum list | grep firefox
yum -y install firefox
```

## 10 克隆虚拟机 （略）

![image-20220523004204902](https://i-blog.csdnimg.cn/blog_migrate/c7af463b8b647b8eb74689f2415305cb.png)

下