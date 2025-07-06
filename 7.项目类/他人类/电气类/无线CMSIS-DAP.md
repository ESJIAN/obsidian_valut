### 目录

- - [概要](https://blog.csdn.net/windyhigh/article/details/131012597#_1)
    - [1. 一般概念](https://blog.csdn.net/windyhigh/article/details/131012597#1__5)
    - - [1.1 CMSIS—DAP的一般概念](https://blog.csdn.net/windyhigh/article/details/131012597#11_CMSISDAP_7)
        - [1.2 支持的芯片](https://blog.csdn.net/windyhigh/article/details/131012597#12__11)
        - [1.3 典型应用场景](https://blog.csdn.net/windyhigh/article/details/131012597#13__14)
    - [2. 原理图与尺寸图](https://blog.csdn.net/windyhigh/article/details/131012597#2__18)
    - - [2.1 Host端（发送端）原理图](https://blog.csdn.net/windyhigh/article/details/131012597#21_Host_20)
        - [2.2 Target（目标）端原理图](https://blog.csdn.net/windyhigh/article/details/131012597#22_Target_22)
        - [2.3 Host尺寸图](https://blog.csdn.net/windyhigh/article/details/131012597#23_Host_24)
        - [2.4 Target尺寸图](https://blog.csdn.net/windyhigh/article/details/131012597#24_Target_26)
        - [2.5 实物图](https://blog.csdn.net/windyhigh/article/details/131012597#25__28)
    - [3. 使用方法](https://blog.csdn.net/windyhigh/article/details/131012597#3__31)
    - - [3.1 连接方法](https://blog.csdn.net/windyhigh/article/details/131012597#31__32)
        - - [3.1.1 整体连接](https://blog.csdn.net/windyhigh/article/details/131012597#311__33)
            - [3.1.2 Target与Cortex-M3的ARM目标板连接](https://blog.csdn.net/windyhigh/article/details/131012597#312_TargetCortexM3ARM_39)
        - [3.2 使用步骤](https://blog.csdn.net/windyhigh/article/details/131012597#32__41)
        - - [3.2.1 HOST端准备](https://blog.csdn.net/windyhigh/article/details/131012597#321_HOST_42)
            - [3.2.2 TARGET端准备](https://blog.csdn.net/windyhigh/article/details/131012597#322_TARGET_45)
            - [3.2.3 配置调试环境（以keil MDK 5为例）](https://blog.csdn.net/windyhigh/article/details/131012597#323_keil_MDK_5_47)
        - [3.3 下载与仿真演示](https://blog.csdn.net/windyhigh/article/details/131012597#33__54)
        - - [3.3.1 下载](https://blog.csdn.net/windyhigh/article/details/131012597#331__55)
            - [3.3.2 仿真](https://blog.csdn.net/windyhigh/article/details/131012597#332__58)
    - [4. 常见问题](https://blog.csdn.net/windyhigh/article/details/131012597#4__81)
    - - [4.1 问题1](https://blog.csdn.net/windyhigh/article/details/131012597#41_1_82)
        - [4.2 问题2](https://blog.csdn.net/windyhigh/article/details/131012597#42_09_2_86)
        - [4.3 问题3](https://blog.csdn.net/windyhigh/article/details/131012597#43_09_3_90)
        - [4.4 问题4](https://blog.csdn.net/windyhigh/article/details/131012597#44_09_4_95)
        - [4.5 问题5](https://blog.csdn.net/windyhigh/article/details/131012597#45_09_5_100)
    - [5. USB转串口、无线透传功能](https://blog.csdn.net/windyhigh/article/details/131012597#5_USB_104)
    - [6. 为51单片机下载程序方法](https://blog.csdn.net/windyhigh/article/details/131012597#6_51_108)
	    - [6.1 HOST端准备](https://blog.csdn.net/windyhigh/article/details/131012597#61_HOST_109)
        - [6.2 TARGET端准备](https://blog.csdn.net/windyhigh/article/details/131012597#62_TARGET_112)
        - [6.3 51单片机和TARGET端连接](https://blog.csdn.net/windyhigh/article/details/131012597#73_51TARGET_115)
        - [6.4 下载演示（以STC-ISP软件演示）](https://blog.csdn.net/windyhigh/article/details/131012597#74_STCISP_118)


### 概要

DRG WL-CMSIS-DAP V1.0模块专用于Cortex-M内核下载、调试和仿真的开发学习。  
除此之外，还有两个附加用途：（1）可以作为[USB转ttl](https://so.csdn.net/so/search?q=USB%E8%BD%ACttl&spm=1001.2101.3001.7020)（即usb转串口）的无线透传模块使用；（2）可以为51单片机下载程序。

## 正文
### 1. 一般概念

#### 1.1 CMSIS—DAP的一般概念

CMSIS-DAP是用于将调试端口连接到USB的调试单元的接口固件。  
DRG WL-CMSIS-DAP V1.0是基于CMSIS-DAP的无线调试器，即插即用，速度快，支持虚拟串口。无线调试器包括HOST/TARGET，基于2. 4G无线通信，可对10m范围内的目标进行程序烧录和调试。

#### 1.2 支持的芯片

WL-CMSIS-DAP支持的常见Cortex-M内核的Arm芯片，如stm32、gd32等，结果合理接线配置还可以为51单片机下载程序。参考常见问题4。

#### 1.3 典型应用场景

在某些有线仿真器不便调试的场景, 例如目标始终处于移动状态(飞行器、小车、机器人等)，目标产品已经组装成产品形态，或者已安装在墙上或者高处等，此时使用无线调试器能较好的解决这些场景下的调试问题，有效提高  
研发效率。

### 2. 原理图与尺寸图

#### 2.1 Host端（发送端）原理图

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/78b726048c781a0f148837c9e57f5a76.png)

#### 2.2 Target（目标）端原理图

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9904cc33cbb985c6359b01b282e4cbc6.png)

#### 2.3 Host尺寸图

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/95991164627a92a20d2f14e599cff1f3.png)

#### 2.4 Target尺寸图

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cb4e738b0825248a6590a6b96680ef92.png)

#### 2.5 实物图

![host与target的正面图](https://i-blog.csdnimg.cn/blog_migrate/c26c949698043b6690ec0a88b9a66fd1.png)  
![host与target的背面图](https://i-blog.csdnimg.cn/blog_migrate/7d585ba07b52ed5293c9b345c4e60143.png)

### 3. 使用方法

#### 3.1 连接方法

##### 3.1.1 整体连接

无线传输模块使用WiFi模块ESP8266, PA为25DB, 功率较高,可有效保证信号稳定性(WiFi使 用扩频原理实现无线通信，带宽和稳定性是其他无线通信方式如蓝牙、GFSK通信无法比的)  
![整体连接图](https://i-blog.csdnimg.cn/blog_migrate/2ae0b828bca7bb4f049740daa72ea393.png)  
使用上和有线仿真器一样简单方便，无需使用上位机配置参数,也无需下载驱动。  
使用TCP协议进行无线数据传输，全双工通信，带数据确认,丢包重传，能有效保证传输的可靠性和稳定性。

##### 3.1.2 Target与Cortex-M3的ARM目标板连接

![TARGET端和目标板连接](https://i-blog.csdnimg.cn/blog_migrate/ec7be580ceec32491f20552bbd23c72b.png)

#### 3.2 使用步骤

##### 3.2.1 HOST端准备

HOST端接入PC的USB端口，HOST端的USB生成了CMSIS DAP设备和CDC串口设备，CMSIS DAP设备可以在keil软件中配置作为下载器，CDC串口设备可以用串口调试助手打开作为一个串口设备，插入PC后显示如下图所示，  
![图4-1 设备管理器显示](https://i-blog.csdnimg.cn/blog_migrate/841fe10741a6d4921653a2678515c5d0.png)

##### 3.2.2 TARGET端准备

当接受端和目标板连接之后，使用Type-C给接受端供电。当接受端和发射端都供电之后，3~5秒之后WiFi连接指示灯同时亮起，表示连接成功。

##### 3.2.3 配置调试环境（以keil MDK 5为例）

- 配置路径  
    启动keil5,在option→Debug栏中选择CMSIS-DAP Debugger  
    ![配置路径](https://i-blog.csdnimg.cn/blog_migrate/a5c0adfd830fde3f102b024f812a9298.png)  
    ![配置路径](https://i-blog.csdnimg.cn/blog_migrate/2d8bfe4ad73e17f0b407cc6543fceb4b.png)
- FLASH下载设置  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/df1b4c2e68d4d358518e8de6b9aa2880.png)

#### 3.3 下载与仿真演示

##### 3.3.1 下载

按照前面所述步骤配置好之后，即可点击“load”下载按钮开始下载，如下图。  
![下载图标](https://i-blog.csdnimg.cn/blog_migrate/b5c75eb2dc49c2018a54c5bf1787934d.png)

##### 3.3.2 仿真

进入调试状态：单击下图红框中的图标，可以进入或退出调试模式  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cb3f609f5fe5ef75584e5f15d1ae069e.png)  
进入调试模式后，会多一个调试的快捷工具栏，如下  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a19a2d9f222c8dd6a3b7874e3f858086.png)  
复位：使程序复位到初始位置等待重新运行。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9b9e44b22caa1bc8912bbd1cc6bf6ac5.png)  
单步调试：也就是每点一次按钮，程序运行一步。遇到函数会进入函数。点击图标按钮，或者按快捷键F11。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ebc798ad5a0773caf79144ce2348ba51.png)  
逐步调试：即逐行调试，也就是每点一次按钮，程序运行一行。遇到函数不会进入函数。点击图标按钮，或者按快捷键F10。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/50f96ec44a7ef5c01f58672c5a8112d2.png)  
跳出调试：即跳出函数调试，也就是每点一次按钮，程序跳出一个函数，直到跳出最外面的函数（main函数）。点击图标按钮，或者按快捷键Ctrl + F11。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/95ddbf57e80d0b57e5802ac1785ea9ed.png)  
运行到光标处：即将光标放在某一处，点击该按钮（或Ctrl + F11），程序执行到光标的位置就会停止下来（前提是程序能执行到光标的位置）  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2e456cab85b6b4fc6d233b9e46c645bb.png)  
跳转到当前运行到的暂停行：这个功能在程序停止运行时有效，主要的作用就是我们打开了很多文件，不知道将程序翻到哪里去了，点击改按钮即可知道我们的程序暂停在那个位置。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a5b644babd7cd74a103d46e771265ede.png)  
调试窗口：是在调试的时候可以查看的窗口，这里有别于平时编辑状态下的窗口。平时编辑时View菜单下面的选项很小，但是进入调试模式，这里就多了很多选项，这些选项就是调试时查看的窗口（见下图）  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6d8739c78b6152d06b8b809e67575f1b.png)  
内存窗口OR变量窗口：选中一个变量，鼠标右键即可选在“Add ‘变量名’ to…”添加到指定的观察窗口  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/642c4c738af559bfaad37d1000b287e8.png)  
系统外设窗口：即外设寄存器数值查看窗口  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b35a8be8eb1b9546047089349f048fa0.png)

### 4. 常见问题

#### 4.1 问题1

发射机和接收机的各种LED状态表示什么含义？  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7b76a30da28d7524a6c38b6fe72be647.png)

#### 4.2 问题2

无线通信会断开，导致调试失败如何解决?  
由于无线调试器工作在ISM 2.4G公共频段内，而蓝牙、wifi、以及部分遥控器均工作在此频段内，此频段内的电磁干扰较大，有一定可能会造通信失败。且假若您在室内进行调试，室内的物体遮挡、天线的位置，通信的径效应均有可能导致连接断开。当检测到连接断开后，发射器和接收机间会自动重新建立连接，请观察连接状态指示灯，即可重新进行调试。假若通信频繁断开，请检查接收机的供电是否稳定，适当调整位置、距离，其均有可能影响通信的稳定性。

#### 4.3 问题3

可以支持多长距离的无线通信?  
在空旷场地上，可以实现10m内的无线调试。

#### 4.4 问题4

目前支持哪些芯片的调试烧录?  
典型的使用场景为对单片机进行编程调试，理论上Cortex-M系列的内核均可以使用DAP进行烧录调试，典型的芯片如STM32全系列的芯片，GD32全系列，nRF51/52系列等，由于也支持JTAG协议，理论上可支持更多的芯片调试，如ARM Cortex-A系列，MIPS、DSP、 FPGA等。

#### 4.5 问题5

在Linux下可以使用无线仿真器进行调试吗?  
Linux下可以使用openocd配合DAP仿真器进行调试(windows下亦可使用openocd)，openocd是目前全世界流行且功能强大的开源调试器上位机，由于openocd是跨 平台的，你也可以在windows下使用openocd,通过编写适当的配置脚本，可以实现对芯片的调试、烧录等操作。由于涉及内容较多，更多说明请读者自行搜索，或者留言咨询。

### 5. [USB转串口](https://so.csdn.net/so/search?q=USB%E8%BD%AC%E4%B8%B2%E5%8F%A3&spm=1001.2101.3001.7020)、无线透传功能

按照“3.1连接方法”配置好之后，即可作为无线串口使用，注意发射端和接收端的波特率相同即可。使用方法与普通的USB转TTL模块在usb转串口的应用方法相同。串口通讯的波特率可以支持到110bps~3000000bps，如下图所示为波特率3000000时的使用效果。注意：在使用时接收端、发送端的波特率要相同。

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1a3f9283683678538aaf91b463762e71.png)

### 6. 为51单片机下载程序方法

#### 6.1 HOST端准备

HOST端接入PC的USB端口，HOST端会虚拟出一个可以使用的串口，在“计算机-设备管理”中可以看到HOST插入后识别到的COM口。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/542476c17da61fc52dd3d2ac4a2e18f8.png)

#### 6.2 TARGET端准备

当接受端和目标板连接之后，使用Type-C或杜邦线给接受端供电。当接受端和发射端都供电之后，3~5秒之后WiFi连接指示灯同时亮起，表示连接成功。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b9ec41be2aed6281559d917b131bfc19.png)

#### 6.3 51单片机和TARGET端连接

注意：51单片机的GND接到TARGET端的Ng引脚  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7aff9573128dc29f9f69ea790e66c383.png)

#### 6.4 下载演示（以STC-ISP软件演示）

启动STC-ISP(V6.88L)软件，进入到下图所示界面。  
1.选择对应的单片机型号（演示实验中以STC89C52RC单片机为例）；  
2.选择对应的串口号（这里的COM22每台电脑不一样，请以自己的为准）；  
3.选择需要下载的程序文件；  
4.点击“下载/编程”按钮，开始下载  
5.显示如下图中第五步，说明程序已经下载完成。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8d3706824f0800b437118607d1bb1a15.png)

###  7. 相关链接
[产品说明书](https://blog.csdn.net/windyhigh/article/details/131012597)  
[教学视频](https://www.bilibili.com/video/BV1NM4y1B7xA/)  
[资料下载-百度网盘](https://pan.baidu.com/s/1iPY4QQT6U7JJAImTcK4uXA?pwd=m609)
