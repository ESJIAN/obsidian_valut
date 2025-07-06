JTAG最初是用于电路板测试的标准，但后来被广泛应用于嵌入式系统调试。它是一种并行接口，通常包括四个主要线路：TCK（时钟）、TMS（模式选择）、TDI（数据输入）和TDO（数据输出）。JTAG使用状态机来控制操作序列，允许读取和写入寄存器、访问内存、执行操作指令等。
# 定义


JTAG 这个名字是由该标准的制定者 —— 联合测试行动小组（Joint Test Action Group）的名字缩写而来。其相关标准于 1990 年标准化为 IEEE Std. 1149.1-1990（该标准的全称是 Test Access Port and Boundary-Scan Architecture（测试访问端口和边界扫描架构））。  
![](https://i3.wp.com/img-blog.csdnimg.cn/8c32605133d64ca4942abf5b3b7cacc2.png)

> JTAG 是来自主要制造商的工程师团队的一个花哨的名字，他们坐在一起，提出了我们现在称为 JTAG 的标准。

## 边界扫描

_**JTAG 制定之初是采用边界扫描技术的一种测试印刷电路板或集成电路内子模块上的互连（电线）的方法。**_ 边界扫描被广泛用作观察集成电路引脚状态、测量电压或分析集成电路内部子模块的调试方法。在电路板上的很多芯片可以将他们的 JTAG 引脚通过 **Daisy Chain** 的方式连接在一起。  
![](https://i3.wp.com/img-blog.csdnimg.cn/d5d561c491cb47e69346d9c6a5b1400d.png)  
边界扫描（Boundary-Scan）技术的基本思想是在靠近芯片的输入/输出引脚上增加一个移位寄存器单元，也就是边界扫描寄存器（Boundary-Scan Register）。当芯片处于调试状态时，边界扫描寄存器可以将芯片和外围的输入/输出隔离开来。通过边界扫描寄存器单元，可以实现对芯片输入/输出信号的观察和控制。  
![](https://i3.wp.com/img-blog.csdnimg.cn/f48139f39af04b428d9b4848f0388bc4.png)  


现在，越来越多的器件采用 BGA（球栅阵列）封装。电路板上的每个 BGA 器件都对可以使用传统钉床或飞针机完成的测试施加了严格的限制。JTAG 则在球栅阵列（BGA）芯片的生产测试中提供了简单的方法，因此，边界扫描也被认为是 JTAG 的代名词。  
![](https://i3.wp.com/img-blog.csdnimg.cn/29a2cd08962849a39e1afd1c6c6e591a.png)

## 调试功能

JTAG 成立的主要目的是为了帮助电子设备的生产和测试，而不是实际上为软件调试制定标准！但随着时间的推移，芯片制造商发现 JTAG 集成到芯片内部就可以辅助芯片软件调试！如今，JTAG 被用作访问集成电路子模块的主要手段，使其成为调试嵌入式系统的基本机制。  
![](https://i3.wp.com/img-blog.csdnimg.cn/8e32d0eebd014a4ea5d8f6381c7f3546.png)  

详细的调试协议（定义如何通过 JTAG 接口读取边界扫描寄存器）由架构厂商定义，例如 ARM 在 《ARM® Debug Interface v5》规范中给出了详细介绍 DP；RISC-V 则在 《RISC-V Debug Specification》中有详细的描述 DMI。  
![](https://i3.wp.com/img-blog.csdnimg.cn/a4a0f59ebbbf437c832e7a6dd64b92b0.png)

## 烧录功能

JTAG 允许器件编程器硬件将数据传输到内部非易失性器件存储器（例如 CPLD，闪存），目前，所有 FPGA 和 CPLD 包括我们常用的 SoC、MCU 都使用 JTAG 来提供对其编程功能的访问。  


![](https://i3.wp.com/img-blog.csdnimg.cn/699a7b4ac667441190fead8f6135ba21.png)  
  注意，固件烧录可以根据存储介质分为 RAM 烧录和 ROM 烧录。其中，RAM 烧录可以直接写，而 ROM 烧录则需要特定的烧写算法（通常做法是（例如，Keil），先将烧写算法写入到 RAM，然后运行 RAM 中的程序，调试器与 RAM 中的程序通信，实现烧录）。  
![](https://i3.wp.com/img-blog.csdnimg.cn/23925f0d76504e34b81e76c9687ba1a7.png)

## TAP

最初的 JTAG 标准 IEEE 1149.1 定义了 5 个引脚，这 5 个引脚统称为 Test Access Port（TAP）。_**JTAG 本身无固定电压，由目标板和目标芯片的 IO 供电电压决定，必须保证 JTAG 信号线与连接的芯片电压相同。**_

- **TCK**： Test Clock，具有一个内部弱下拉电阻。TCK 为 TAP 的操作提供了一个独立的、基本的时钟信号，TAP 的所有操作都是通过这个时钟信号来驱动的。
- **TMS**： Test Mode Select，具有内部弱上拉电阻。TMS 信号用来控制TAP状态机的转换，在 TCK 的上升沿有效。通过 TMS 信号，可以控制 TAP 在不同的状态间相互转换。
- **TDI**： Test Data-In，具有内部弱上拉电阻。TDI 是数据输入的接口。所有要输入到特定寄存器的数据都是通过 TDI 接口一位一位串行输入的（由 TCK 驱动）。
- **TDO**： Test Data-out。TDO 是数据输出的接口。所有要从特定的寄存器中输出的数据都是通过 TDO 接口一位一位串行输出的（由 TCK 驱动）。
- **TRST**： Test Reset (Optional)，具有内部弱上拉电阻。TRST 可以用来对 TAP Controller 进行复位（初始化）。因为 TRST 是可选的，所以有四线 JTAG 与五线 JTAG 之分。

IEEE-1149.7 标准定义的 compact JTAG（cJTAG）则减少了引脚数，只定义了 2 个引脚，可以采用星形拓扑结构连接：

- **TMSC**： Test Serial Data
- **TCKS**： Test Clock

以上仅仅是信号线，除此之外还可能有一些其他引脚

- **VTREF**： 接口信号电平参考电压一般直接连接 Vsupply。这个可以用来确定 JTAG 接口使用的逻辑电平！我们常用的 J-Link、ULINK 等都可以由 5V 电压供电，然后其内部则可以转换输出 1.8V ~ 5V 从而直接给芯片供电。
- **System Reset ( nSRST)**： 可选项，与目标板上的系统复位信号相连，可以直接对目标系统复位。同时可以检测目标系统的复位情况，为了防止误触发应在目标端加上适当的上拉电阻。
- **Return Test Clock ( RTCK)**： 可选项，由目标端反馈给仿真器的时钟信号，用来同步 TCK 信号的产生，不使用时直接接地。

  JTAG 标准并没有定义 TAP 各引脚的布局方式，我们常见的调试器接口都有 20 个引脚（其源自于 ARM 给出的接口定义，详见后文），多出来的引脚都是一些电源、地等，布局基本就是如下图所示：  
![](https://i3.wp.com/img-blog.csdnimg.cn/d2482b8af5a54cab9a56498dd9451f81.png)

## TAP Controller

  TAP Controller 负责解释 TCK 和 TMS 信号，控制 JTAG 接口的行为。数据输入管脚（TDI）用于将数据加载到物理管脚与 IC 内核之间的边界单元，以及将数据加载到指令寄存器或其中一个数据寄存器中。数据输出引脚（TDO）用于从边界单元读取数据，或从指令或数据寄存器读取数据。  
![](https://i3.wp.com/img-blog.csdnimg.cn/6c77f7f9b8bd41aaba6fdf9082c3e21b.png)  
  TAP Controller 的主体是一个拥有 16 个状态的有限状态机（FSM，Finite State Machine），其状态跳变过程由 TMS 信号控制，该信号由 TCK 驱动。TAP 控制器只能在 TCK 的上升沿改变状态，FSM 接下来跳转到哪个状态（next state），由 TMS 的电平以及 FSM 当前的状态（current state）决定。  
![](https://i3.wp.com/img-blog.csdnimg.cn/befd1b585d4f45be83ce13c345c94eda.png)  
状态机只有两条“路径”，代表两种不同的模式：**指令模式**和**数据模式**。

- 数据寄存器（DR）路径：上图中以绿色显示，用于加载指令
- 指令寄存器（IR）路径：上图中以蓝色显示，用于从/向数据寄存器（包括边界扫描寄存器（BSR））读取/写入数据，

  IEEE 1149.1 标准定义了一组必须可用的指令，以使设备被认为是兼容的。这些指令是（有关每种状态的更多详细信息，请参阅 IEEE 1149.1 标准 JTAG 文档）：

- **BYPASS**：这条指令使 TDI 和 TDO 线通过一个单 BIT 直通寄存器（BYPASS 寄存器）连接。该指令允许测试 JTAG 链中的其他设备，而没有任何不必要的开销。
- **EXTEST**：该指令使 TDI 和 TDO 连接到边界扫描寄存器 (BSR)。器件的引脚状态通过 `capture dr` JTAG 状态进行采样，新值通过 `shift dr` 状态移入 BSR；然后使用 `update dr` 状态将这些值应用到设备的引脚。
- **SAMPLE/PRELOAD**：该指令使 TDI 和 TDO 连接到 BSR。但是，设备仍处于正常功能模式。在此指令期间，可以通过数据扫描操作访问 BSR，以对进入和离开设备的功能数据进行采样。该指令还用于在加载 EXTEST 指令之前将测试数据预加载到 BSR 中。

其他常用说明包括：

- **IDCODE**：该指令使 TDI 和 TDO 连接到 IDCODE 寄存器。
- **INTEST**：该指令使 TDI 和 TDO 线连接到边界扫描寄存器 (BSR)。EXTEST 指令允许用户设置和读取引脚状态，而 INTEST 指令与器件的核心逻辑信号相关。