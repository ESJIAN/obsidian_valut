1 SWD（Serial Wire Debug）是由 ARM 公司设计的用于编程和调试 Cortex 系列微控制器的协议。由于 SWD 专门用于编程和调试，因此，它具有许多其他地方通常无法提供的特殊功能，例如通过 IO 线向计算机发送调试信息。

## 体系结构

  与将 TAP 链接在一起的 JTAG 相反，SWD 使用称为 DAP（Debug Access Port，调试访问端口）的总线。在这个 DAP 上，有一个主站（DP，Debug Port，调试端口）和一个或多个从站（AP，Access Port，接入端口），类似于 JTAG TAP。DP 使用包含 AP 地址的数据包与 AP 通信。  
![](https://i3.wp.com/img-blog.csdnimg.cn/fb2770dd733844aaa2098630241b6f93.png)

### 调试端口

调试端口是主机和 DAP 之间的接口。它还处理主机接口。有三种不同的调试端口可用于访问 DAP：

- **JTAG调试端口（JTAG-DP）**： 此端口使用标准的 JTAG 接口和协议来访问 DAP
- **串行线调试端口 （SW-DP）**： 此端口使用 SWD 协议访问 DAP。
- **串行线/JTAG调试端口（SWJ-DP）**： 此端口可以使用 JTAG 或 SWD 来访问 DAP。这是许多微控制器上的通用接口。它复用 JTAG 的 TMS 和 TCK 信号分别传输 SWDIO 和 SWDCLK 信号。必须发送特定的序列才能从一个接口切换到另一个接口。

### 访问端口

可以根据需要将多个 AP 添加到 DAP。ARM 提供了两个 AP 的规格：

- **内存访问端口 （MEM-AP）**： 此 AP 提供对核心内存和寄存器的访问。
- **JTAG接入端口（JTAG-AP）**： 此 AP 允许将 JTAG 链连接到 DAP。

## 调试

  SWD 就只是用来调试（跟踪）的，因此它相对于 JTAG 简单不少，详细的调试协议在 《ARM® Debug Interface v5》的 The Serial Wire Debug Port (SW-DP) 这个章节有介绍。  
![](https://i3.wp.com/img-blog.csdnimg.cn/51ad4b0a7c6f4487a99225b9ce8f5602.png)

## 固件烧录

  固件烧录的实现方式与 JTAG 中说的一样，就是协议走的 SWD 协议，这里就不再赘述了！

## 引脚

  SWD 协议定义了 2 个引脚，在体系结构方面支持星型拓扑。_**SWD 本身无固定电压，由目标板和目标芯片的 IO 供电电压决定，必须保证 JTAG 信号线与连接的芯片电压相同。**_：

- **SWDIO**： Serial Wire Data Input Output。主机发送的时钟信号。由于处理器时钟和 SWD 时钟之间没有关系，频率选择由主机接口决定。
- **SWCLK**： Serial Wire Clock。这是带有来自 / 送到 DP 的数据的双向信号。数据由主机在上升边缘期间设置，并在 SWDCLK 信号的下降边缘期间由 DP 采样。

  SWD 实际上只是针对 ARM 处理器的 JTAG 的一个修改/实现，ARM 在其[系统和接口设计参考](https://developer.arm.com/documentation/100893/1-0/Target-interface-connectors/Arm-JTAG-20-connector)文档中给出了常用的接口布局，成为了事实上的标准。通常它复用 JTAG 的 TMS 和 TCK 信号分别传输 SWDIO 和 SWDCLK 信号，从而允许用户使用 JTAG 或 SWD。  
![](https://i3.wp.com/img-blog.csdnimg.cn/f1adec2006ce400d9d91563a6383e112.png)  
  除了调试信号，ARM 的 SWD 接口还指定了一个专用的引脚，允许目标 CPU 通过 UART 或 Manchester 协议在专用引脚上输出特定的数据，这个引脚被称为 SWO。并非所有支持 SWD 的 ARM 架构都支持 SWO。