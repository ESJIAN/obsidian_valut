## **1. 导言**

蓝牙™核心规范6.0（Bluetooth® Core 6.0）包含多项功能增强。本文概述了每个增强功能。注：本文为市场推广文件，无意以任何方式取代或推翻蓝牙™核心规范。

每项功能增强都有专门的章节进行描述，并以相关背景信息的描述开始。这样做的目的是为了方便那些以前可能没有接触过低功耗蓝牙某些方面的读者。尽管如此，背景部分并不完全全面，如果读者遇到不熟悉的术语或概念，建议下载并阅读《[低功耗蓝牙入门](https://www.bluetooth.com/zh-cn/bluetooth-resources/the-bluetooth-low-energy-primer/)》。

## **2.概述**

#### **2.1 蓝牙™信道探测**

蓝牙™信道探测可在两台蓝牙设备之间实现_安全的精密测距_。_测距_是指使用某些技术来测量两个物体之间的距离。

无线测距被应用于多种产品，如数字钥匙解决方案和"查找"网络等。全新蓝牙™信道探测功能旨在提供一种基于标准的技术方法，以满足此类产品通常具有的极高精度和安全性要求。

#### **2.2 基于决策的广播过滤**

蓝牙扩展广播功能可在主无线电信道和辅助无线电信道上传输一系列相关数据包。

基于决策的广播过滤允许扫描设备使用主广播信道上接收到的数据包内容来决定是否在辅助信道上扫描相关数据包。这就减少了在次要信道上扫描数据包的时间，从而提高了扫描效率，因为次要信道上的数据包可能并不包含与应用相关的PDU。

#### **2.3监视广播设备**

观察者设备的Host组件可指示低功耗蓝牙控制器过滤重复的广播数据包。当这种类型的过滤激活时，Host将只接收来自每个唯一设备的单个广播数据包（取决于核心规范在此上下文中对什么是唯一设备的定义）。这样做提高了Host的效率，但缺点是当情况决定观察者设备现在应尝试连接某设备时，Host无法知道该设备是否仍在范围内。这可能会导致观察者浪费能量，为先前发现的设备执行高占空比扫描，而该设备已不在范围内。

新的监视广播设备功能使用Host控制器接口（HCI）事件，在感兴趣的设备进入或离开范围时通知Host 。

#### **2.4 ISOAL增强**

等时适配层（ISOAL）使较大的数据帧可在较小的链路层数据包中传输，并确保接收器可以重组正确处理数据所需的相关定时信息。

ISOAL可根据某些变量生成_有帧_或_无帧_PDU。如果生成的是有帧PDU，延迟会因此增加。

在蓝牙™核心规范6.0中，ISOAL通过定义一种新的成帧模式得到了改进，该模式可减少对这一问题特别敏感的用例的延迟。该功能还提高了可靠性。

#### **2.5 LL扩展功能组**

设备能够交换各自支持的链路层功能信息。随着低功耗蓝牙的复杂性和通用性不断提高，这一功能也得到了增强，以支持更多的功能。

#### **2.6 帧间隔更新**

以前版本的蓝牙™ 核心规范为连接事件或连接等时数据流（CIS）子事件中相邻数据包传输之间的间隔时间定义了一个恒定值。该值在规范中称为_T_IFS_，固定值为150 µs。

在蓝牙™核心规范6.0 中，用于连接或连接等时数据流的帧间距现在可以协商，可以短于或长于 150 µs。

## **3.蓝牙™信道探测**

### **3.1 背景**

本节将概述低功耗蓝牙技术的各个方面，有助于更好地理解和欣赏全新的蓝牙™信道探测功能。

##### **3.1.1 设备定位和低功耗蓝牙**

自低功耗蓝牙首次在蓝牙核心规范中被指定以来，寻向等核心功能以及“查找”配置文件等一系列相关配置文件已将低功耗蓝牙打造成一种流行的位置服务技术。

_[![2405信道探测 图 2](https://www.bluetooth.com/wp-content/uploads/2024/08/2405_Channel_Sounding_Figure_2-1000x500.png "2405 Channel Sounding Figure 2")](https://www.bluetooth.com/wp-content/uploads/2024/08/2405_Channel_Sounding_Figure_2.png)图 1 - 使用方向查找到达角和出发角_

此外，在标准低功耗蓝牙广播数据包中传输的几种专有Beacon广播信息格式已被广泛采用。

许多应用都需要计算两个蓝牙设备之间的距离。在蓝牙核心规范 6.0 版发布之前，这只能通过一种称为_路径损耗计算的_方法来实现。这种方法要求接收设备测量接收到的信号强度（称为_RSSI_），并知道远程设备在距离发射器 某个参考距离（如 1 米）处发射的信号强度。此外，相关物理学表明，接收器 的信号强度与其与发射器距离的平方成反比。有了发射器参考信号强度、RSSI 和这个简单的数学关系，就可以计算出距离值。

[![2405信道探测 图 1](https://www.bluetooth.com/wp-content/uploads/2024/08/2405_Channel_Sounding_Figure_1-1000x552.png "2405 Channel Sounding Figure 1")](https://www.bluetooth.com/wp-content/uploads/2024/08/2405_Channel_Sounding_Figure_1.png)_图 2 - 距离上的反平方路径损耗_

路径损耗计算适用于对距离计算精度要求不高、一致性和可靠性要求不高的情况。当两个设备之间的距离相对较小时，由于信号强度最初会迅速下降（见图 2），因此路径损耗计算可以获得相当好的结果。但在较远距离上，信号强度的微小变化可能会对应较大的距离范围，从而使计算对微小误差非常敏感。这种方法容易受到干扰和其他环境因素的影响，而且也不安全，会使应用面临距离欺骗等攻击风险。

资产追踪、无钥匙进入和点火系统等应用的要求更具挑战性，需要采用更复杂、更安全和更标准化的方法，这样才能获得更准确、更可靠的结果。

##### **3.1.2 数据传输架构**

蓝牙核心规范定义了多个概念，它们共同构成了蓝牙数据传输架构。这些概念包括物理传输、物理信道、物理链路、逻辑链路和逻辑传输。为支持不同应用类型，定义了某些组合和配置，每种组合和配置都具有与拓扑、定时、可靠性、功率和信道使用等属性相关的特定特性。_操作模式_或_运行模式_有时被非正式地用来指各种数据传输架构配置。

[![Bluetooth 核心 6 图 3](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_3.png "Bluetooth Core 6 Figure 3")](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_3.png)_图 3 - 蓝牙数据传输架构的一部分_

图3显示了数据传输架构的一小部分，突出了两种最常用的逻辑传输及其相关的物理链路、物理信道和物理传输组件。这两种逻辑传输都与蓝牙™信道探测相关。

**3.1.2.1 LE-ACL**

LE-ACL是最常用的低功耗蓝牙逻辑传输类型之一，可在两个设备之间提供面向连接的数据通信。事实上，ACL 连接通常简称为_连接_。 

请求连接的设备称为中心设备。接收并批准该请求的设备称为外设。

当两台设备建立 ACL 连接时，它们会商定一些管理其后续通信的定时参数。这些参数中最关键的是_连接间隔_。 _连接间隔_ 参数以毫秒为单位定义了无线电为该连接提供服务的频率。

ACL 连接可以是加密的，在这种情况下，所有有效载荷都会在数据包传输前由链路层加密，并在对等设备的链路层接收时解密。

**3.1.2.2 ADVB**

ADVB即广告广播逻辑传输。它提供了一种无连接通信模式，可用于同时向一个或多个设备传输数据或指示外围设备的存在，以便其他设备发现它。

#### **3.2 关于蓝牙™信道探测**

##### **3.2.1 概述**

低功耗蓝牙的蓝牙™信道探测功能 包括两种不同的测距方法，可单独或组合使用。这两种方法分别称为基于相位的测距（PBR）和往返时间（RTT）。

与路径损耗法相比，该系统支持更精确的距离测量计算，不易受干扰和环境因素的影响，并集成了多种安全机制。

本节将介绍蓝牙™信道探测如需更深入和全面的解释，请参阅相关论文_《使用蓝牙信道探测实现安全精密测距》_ ，该论文可从蓝牙技术联盟网站获取，网址为_www.bluetooth.com_

##### **3.2.2 技术要点**

**3.2.2.1 系统结构**

蓝牙™信道探测在 1:1 拓扑中的两个互联设备之间进行。希望计算自身到另一台设备距离的设备称为启动器。另一台设备称为反射器。

在信道探测期间，启动器和反射器在预先约定的时间段内进行多次双向交流。

在蓝牙协议栈中，信道探测主要是蓝牙控制器的功能，而不是协议栈Host部分的功能。启动器控制器通过Host控制器接口（HCI）将底层测量数据传递给Host ，并最终传递给应用 。应用负责使用控制器提供的信道探测数据计算距离测量值。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_4.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_4.png)_图 4 - CS设备的作用以及Host/控制器功能分布_

使用蓝牙™信道探测的设备可能包括天线阵列。这可以提供一系列不同的通信路径，减少多径传播的影响，从而提高距离测量的准确性。

**3.2.2.2 蓝牙™信道探测和数据传输架构**

图5描述了完整数据传输架构的一个子集，并显示了为支持信道探测而新增的物理链路和物理信道类型。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_5.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_5.png)_图 5 - CS和数据传输架构_

信道探测是通过两个设备之间的ACL连接启动的。一旦信道探测启动，ACL连接将继续作为链路层控制交换的传输，并为信道探测无线电活动调度提供定时参考。信道探测使用新的信道探测物理链路和信道探测物理信道。

中心设备或外围设备可分别作为启动器和反射器。

**3.2.2.3 距离测量方法**

**3.2.2.3.1 基于相位的测距（PBR）**

PBR利用了无线电信号的一个基本属性 ，即_相位_及其与频率和波长的关系。相位可以看作是波周期的一部分，通常用 0 至 2π 弧度之间的角度表示。相位的变化有时归因于_相位旋转_。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_6.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_6.png)_图 6 - 数个波周期内的相位值示例_

图6显示了与无线电信号中的点相对应的相位值示例。请注意这些值在多个波周期内的循环重复性质。

使用PBR时，启动器以给定频率f1向反射器发射信号。反射器向发射器发回信号，发射器收到回复后，测量接收信号的相位，我们在此将其称为Pf1。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_7.png)_图 7 - 启动器发送信道探测信号，反射器发出回声_](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_7.png)

接着，发射器发射另一个无线电信号，这次频率不同，为f2。 反射器再次将接收到的信号回传给发射器。频率的改变会改变波长，因此发射器在接收到反射器回波时测量到的相位Pf2也会随之改变。

现在，启动器可以使用频率差（f1-f2）、相位差（Pf1-Pf2）和光速公式计算两个设备之间的距离。

在实际应用中，设备通常会在两个以上的不同频率上交换两个以上的信号，因为有了更多的低电平测量值，就能提高应用所计算的距离测量值的精确度。

启动器测量到的相位值会随着设备之间距离的增加而变化，但在某一点上会重置为零，相位值开始重复。这是因为相位旋转具有周期性，如图 6 所示。在距离测量中，这种现象被称为_距离模糊_，因为相同的相位值可能在多个不同的距离上出现。 究竟何时首次出现距离模糊，取决于信道探测信号频率之间的差值。这个差值被称为_频率间隔_。一般来说，频率间隔越大，距离模糊越早出现。蓝牙信道探测使用的频率间隔为 1 MHz，距离模糊在 150 米左右才会出现。

PBR 与第二种测距方法--往返计时相结合，可以解决距离模糊的问题。

**3.2.2.3.2 往返时间（RTT）**

RTT法涉及启动器向反射器发送一个数据包，反射器再发回同样的数据包。只有在这一点上与PBR 有相似之处。

为了能够计算距离测量值，启动程序在传输其数据包时会记录一个时间戳。这个时间称为 "出发时间 "或 "ToD"。在收到反射器的回复数据包时，它会再次记录一个时间戳，这个时间称为到达时间或 ToA。

如果我们把 ToD 和 ToA 之间的时间称为TA-D，那么用TA-D乘以光速 (c)，再除以 2（因为这是双向的RTT），就可以测出所走的距离。 不过，这只是一个非常粗略的距离估计，因为它没有考虑到反射器接收数据包、处理数据包、作出回应和传输数据包所需的时间。这一处理过程所需的时间看似很短，无关紧要，但以光速（在真空中）传输的无线电波可以在一微秒内传播 300 米，因此在计算飞行时间时，很小的误差都会对计算距离产生很大影响。因此，准确确定无线电信号实际_飞行的_时间，是使用RTT 法获得精确测量距离的关键。

蓝牙™信道探测中的RTT可确保知道反射器将接收到的CS数据包转一圈并发送回启动器所需的时间，因此可在计算中使用该时间值来得出更精确的飞行时间。 

蓝牙核心规范定义了几种不同的捕捉 ToA 和 ToD 时间戳的方法。所选方法的复杂程度和精确度各不相同。最精确的时间捕捉方法被称为_分数时序估计_。尽可能准确地捕捉 ToA 和 ToD 值将获得最精确的距离测量结果。

**3.2.2.4 信道探测初始化**

在信道探测开始之前，发射器和反射器必须建立加密 ACL 连接。该连接用于安全交换与信道探测初始化程序相关的链路层控制 PDU。

蓝牙™信道探测有其独特的安全功能。要执行的第一个信道探测程序是 CS 安全启动程序。该程序为两个设备配备初始化矢量 (IV)、实例化唯一性数据 (IN) 和个性化矢量 (PV) 值，这些值随后将在信道探测过程中用作新安全功能——确定性随机比特发生器 (DRBG) 的输入。DRBG 用于许多信道探测安全功能（见 [_3.2.2.10 蓝牙™信道探测安全概述_](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#sec32210)）。加密 ACL 连接的安全性可保护这些重要数据的交换。

蓝牙™信道探测功能为开发人员提供了一系列选项，用于控制或影响所使用的距离测量方法、测量精度、程序导致的延迟、安全性和其他变量。设备不一定具有完全相同的信道探测能力，CS能力交换程序允许两个设备交换有关能力和偏好的信息。

交换功能数据后，设备参与 CS 配置程序，并就信道探测程序启动时的配置参数达成一致。

使用PBR时，反射器会以相同的频率回传从发射器接收到的信号。但是，所有设备生成的信号频率都会有一定程度的误差，即预期或_想要的_ 频率与实际测量的生成信号频率不同。频率与波长直接相关，PBR 就是基于这种关系。因此，反射器回波信号频率的不准确性会影响距离测量的准确性。因此，制造商可能会为设备配备一个名为“分数频率偏移执行误差（FAE）表”的数据表，该表针对一组参考频率，提供了生成信号的频率与预期或要求频率之间的差值，以百万分率（ppm）表示。 使用模式-0[[个人仓库/谢承旭/1.理学类/170地科类/书籍总结/1]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftn1)FAE 表请求程序，启动器可向反射器请求 FAE 表，并在进行计算时将该数据考虑在内。

完成初始化程序后，即可开始信道探测 。这包括两个设备进行一系列不同类型的交换，以获取应用 可用于距离计算的测量数据。

**3.2.2.5 时间划分**

信道探测涉及信道探测物理信道的使用，该信道来自一般的蓝牙_数据传输_架构（见_3.2.2.2信道探测和数据传输架构_）。这定义了射频活动如何细分和使用时间。

**3.2.2.5.1 事件、子事件和步骤**

信道探测在一系列程序中进行。每个程序由若干事件组成，每个事件又分为若干子事件。在这种分级方案中，时间的最终细分是步骤。启动器和反射器之间的射频交换就是在步骤中进行的。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_8.png)_图8 - 信道探测示例配置中的程序结构_](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_8.png)

各种配置参数控制着这一结构的方方面面，包括不同级别元素之间关系的心 数（例如每个子事件的步骤数）、事件的持续时间以及在步骤中发生的活动。例如，子事件中总是至少有 2 个步骤，最多 160 个步骤。每个程序最多有 256 个步骤。

**3.2.2.5.2 定时锚点**

所有信道探测程序、事件、子事件和步骤的开始时间都直接或间接锚定到相关 LE ACL 连接中的选定连接事件，在该连接上执行链路层程序以启动信道探测。

**3.2.2.6 蓝牙™信道探测步骤**

**3.2.2.6.1 数据包和音调**

在 CS 步骤期间，设备交换一系列称为 CS 同步数据包的数据包，也可选择交换称为 CS 音调的_音调_。

CS 同步数据包可使用 LE 1M 或低功耗2M PHY 传输。GFSK[[2]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftn2)调制方案，与其他低功耗蓝牙数据包一样。

CS 音调是一种使用振幅偏移键控（ASK）来创建频率固定的符号的信号。

步骤有一个相关的_模式_，其编号为 0 至 3（含 3）。模式定义了步骤中交换的细节及其目的。

- 模式 0 步骤与校准有关，允许启动器确定反射器生成的特定频率与其自身频率的差异程度。这将产生一个称为分数频率偏移（FFO）的值，用于计算补偿频率生成差异。模式 0 步骤涉及 CS 同步数据包的交换。
- 模式-1 步骤使用RTT方法应用CS同步数据包。
- 模式-2 步骤包括交换 CS 音调，以实现PBR。
- 模式-3 步骤可交换 CS 同步数据包和 CS 音调，并允许在一个步骤中收集用于RTT 和PBR 方法的数据。对模式 3 的支持是可选的。

在信道探测程序中使用哪种步骤模式取决于蓝牙核心规范 中的规则和两个设备商定的配置。这包括使用哪种或哪几种测距方法，即RTT和/或PBR。

**3.2.2.6.2 模式组合和排序**

蓝牙™信道探测允许在程序中以各种模式组合和排序步进模式，应用 可在配置过程中行使很大的控制权。应用 还可以配置要执行的信道探测程序的重复次数，以及影响数据包或音调交换次数的其他变量，并在某些方面影响它们的内容。

在确定要建立的最佳配置时，应用将考虑距离测量的精度要求、延迟容忍度和安全需求等问题。例如，一般来说，更多的交换机将提供更多的测量，可能有助于提高精确度，但代价是延迟增加。

每个子事件总是涉及至少两种不同的步骤模式。模式-0 总是启动每个子事件，同一子事件中的其他步骤可以使用一种或两种其他模式，但必须遵守某些允许的组合，这些组合在蓝牙核心规范中列出，并在表 1 中重复。

|**Main_Mode**|**Sub_Mode**|
|---|---|
|Mode-1|None|
|Mode-2|None|
|Mode-3|None|
|Mode-2|Mode-1|
|Mode-2|Mode-3|
|Mode-3|Mode-2|

表 1 - 允许的非模式 0 模式组合。

表 1 还介绍了主模式（Main_Mode）和子模式（Sub_Mode）。这些术语与通过一些配置参数创建重复步进模式的方式有关。配置过程中，1-3 模式中的一种将被指定为主模式，另一种可选为子模式。

一般来说，步进模式排序遵循这种模式：

1. 一个或多个模式 0 步骤启动子事件。
2. 随后是一连串的 n 个主要模式步骤，其中 n 是随机选择的，并在设定的范围内。
3. 按照蓝牙核心规范 所称的子模式_插入_过程，在 n 个主模式步骤的序列之后是一个子模式步骤。

除子事件必须始终以一个或多个模式 0 步开始这一一般规则外，步进模式序列与子事件边界无关。完整序列可以跨越多个子事件。

**3.2.2.7 射频信道**

**3.2.2.7.1 信道和信道过滤**

信道探测中定义了 72 个信道，每个信道的宽度为 1 兆赫，信道索引值独一无二。这些信道的安排可确保避开 LE 一级广播信道。

信道宽度为 1 兆赫，而不是通常的 2 兆赫，这就确保了使用PBR 信道PBR 信号之间的频率间隔在 150 米左右才会出现距离模糊。

一个名为 CS 信道图的特殊信道图指明了哪些信道应纳入信道选择，哪些应避免。链路层控制程序允许发起方和反射方根据本地射频条件对该表进行更新。

跳频包括从标记为可用的信道中选择一个新信道。这通常发生在每一步执行之前，除非使用的是称为 "主模式重复 "的模式功能 。

**3.2.2.7.2 信道选择**

信道探测中定义了一套新的三通道选择算法（CSA）。它们统称为 CSA #3，单独称为 CSA #3a、CSA #3b 和 CSA #3c。

CSA #3a 仅用于选择在模式-0 步骤中使用的信道。

CSA #3b 和 CSA #3c 都设计用于非模式 0 步骤，但在信道探测程序实例中只能使用其中之一。

信道探测期间保留两个通道列表。第一个仅用于 CSA #3a 和模式-0 梯级的通道选择。第二个用于 CSA #3b 或 CSA #3c 的非模式-0 步骤。

CSA #3a 和 CSA #3b 的工作方式相同，但作用于不同的信道列表。它们使用相同的算法，对标记为_包含的_信道进行随机排序，以创建一个洗牌信道列表。洗牌信道列表中的每个条目都是唯一的，只能使用一次。当洗牌信道列表中的所有条目都被使用过之后，它就会重新生成，创建一个新的随机信道列表。

CSA #3c 算法与 CSA #3b 算法有很大不同。信道图中包含的信道子集被组织成组，并在组内生成形成形状的信道模式。CSA #3c 在某些情况下可能会在检测反射信号路径方面提供一些优势。详情请查阅蓝牙核心规范 。 CSA #3c 支持为可选项。

**3.2.2.8 LE 2M 2BT PHY**

低功耗蓝牙的物理层包括几种被称为 PHY 的允许配置的定义。PHY 的定义包括所使用的调制方案及其参数，如符号率、最小频率偏差和带宽-比特周期产品 (BT)。

在蓝牙核心规范 6.0 版之前，有三种已定义的 PHY。它们的名称分别是 LE 1M、LE-2M和LE Coded。低功耗编码 PHY 与 LE 1M 完全相同，只是数据包需要进行额外的编码，以实现错误检测和纠正。

6.0 版引入了一种名为低功耗2M 2BT 的新物理层配置。这种新的 PHY 只能与蓝牙™信道探测一起使用。

表2比较了四种PHY。

||LE 1M|LE Coded|LE 2M|LE 2M 2BT|
|---|---|---|---|---|
|Symbol Rate|1 Msym/s|1 Msym/s|2 Msym/s|2 Msym/s|
|BT|0.5|0.5|0.5|2.0|
|Min. Frequency Deviation|185 kHz|185 kHz|370 kHz|420 kHz|
|Error Detection|CRC|CRC|CRC|N/A|
|Error Correction|NONE|FEC|NONE|N/A|
|Requirement|Mandatory|Optional|Optional|Optional. Only to be used with Channel Sounding.|

表2 - PHY比较

带宽-比特周期（BT）是信号的一个属性，它提供了信号带宽与符号持续时间之间关系的信息。

BT 会影响构成符号的无线电脉冲的形状和跨度。BT 值越高，脉冲越窄、越方；BT 值越低，脉冲越宽、越圆。

BT 值为 2.0 时，信道探测在某些物理层攻击方面的安全性会提高。参见 [_3.2.2.10蓝牙™信道探测安全概述_](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#sec32210)。

**3.2.2.9信道探测 步的信噪比控制**

某些无线电发射机能够调整信噪比（SNR），使其在指定范围内。信噪比控制功能 允许发起方和反射方设备商定一个信噪比输出电平，以便在 CS 模式-1 和模式-3 步骤中用于 CS 同步数据包传输。调整 SNR 需要人为地在信号中混入一定程度的噪音。由于两台 CS 设备都知道输出 SNR，因此这种噪音的存在对两台 CS 设备来说不是问题。这种技术降低了某些类型的物理层中间主控攻击的风险。 

**3.2.2.10 蓝牙™信道探测安全概述**

距离测量解决方案所独有的安全问题通常涉及到这样一种威胁：不受信任的设备以某种方式欺骗一个受信任的设备，使其认为另一个受信任的设备距离足够近，从而允许或采取某些行动。例如，在无钥匙进入系统中，如果一个恶意设备能够欺骗门锁，使其认为相关的可信无线钥匙卡离门很近，可以自动解锁，那么未经授权的一方就可以进入系统。

安全专家认识到一系列与距离测量有关的攻击。其中一些涉及独立的恶意设备伪造来自受信任设备的通信（称为_欺骗_），另一些则是中间人（MITM）攻击类型，这些攻击转发来自受信任设备的信号，通常在此过程中操纵信号或其数字内容，导致受信任设备错误计算其与受信任设备之间的距离。此类攻击的复杂程度、实施的复杂性和成本各不相同。

蓝牙™信道探测包括一系列功能，可作为应对一系列距离测量安全威胁的对策。这些功能可分为四类：

1. 结合使用PBR 和RTT 法。

- 使用PBR和RTT法的数据计算距离，可以对数值进行交叉检验。应用应对明显的差异持怀疑态度。针对这两种方法并产生兼容的、足够相似的结果以避免被交叉检验检测到的攻击被认为是非常复杂和代价高昂的。

2. 比特流和传输模式的随机化。

- 在比特流中随机选择的位置传输随机比特值。随机比特值和位置是使用新的确定性随机比特发生器（DRBG）生成或选择的。启动器和反射器都拥有相同的 IN、IV 和 PV 值（参见[_3.2.2.4蓝牙™信道探测初始化_](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#sec3224)），因此它们各自的 DRBG 实例在调用时会产生相同的随机生成比特流。这意味着两台合法设备都知道应该期待什么样的随机比特值，以及在哪里可以找到它们。恶意设备不掌握 IN、IV 和 PV 值，因此只能猜测这些值。在每次交换中猜中比特流所有随机部分的概率非常低。此外，某些时隙会被随机用于或不用于传输，这同样由 DRBG 控制，只有合法的 CS 设备才能预测。

3. 抵御符号操纵

- 某些 MITM 攻击涉及篡改无线电符号，使目标设备错误地计算与其他合法设备的距离。这种攻击依赖于攻击者在几微秒内从潜在射频信道范围内找到传输信号，然后迅速操纵符号。
- 在使用信噪比控制功能时，传输中的噪声会增加攻击者分析信号所需的处理时间。如果需要足够的额外处理时间，攻击就会失效。
- 低功耗2M 2BT PHY 的符号跨度较短，因此符号更难被截取和操纵。

4. 射频信号分析技术，包括攻击检测。

- 蓝牙核心规范包含对蓝牙™信道探测_攻击探测器系统的_描述。其中包括一个标准化指标，用于向应用 报告正在发生攻击的概率。该指标称为_归一化攻击检测器指标_或 NADM。NADM 值由控制器根据对接收信号的评估进行分配，采用滑动量表的形式，在一定范围内显示攻击的可能性，从_攻击极不可能_开始，增加到最上限的攻击_极有可能_。表 3 包含 NADM 值定义，摘自蓝牙核心规范。

|**NADM Value**|**Description**|
|---|---|
|0x00|Attack is extremely unlikely|
|0x01|Attack is very unlikely|
|0x02|Attack is unlikely|
|0x03|Attack is possible|
|0x04|Attack is likely|
|0x05|Attack is very likely|
|0x06|Attack is extremely likely|
|0xFF|Unknown NADM.<br><br>Default value for RTT types that do not have a random sequence or sounding sequence.|

表3 - NADM值

此外，蓝牙控制器实施者和应用开发者还可根据需要，通过额外的保障措施来增强蓝牙™信道探测安全功能所提供的标准安全功能。

##### **3.2.3 关于蓝牙™信道探测的更多信息**

蓝牙™技术联盟专门编写了一篇论文，对蓝牙™信道探测功能进行了更详尽的描述。论文标题为_使用蓝牙™信道探测实现安全精密测距_，可在[蓝牙技术联盟网站](https://www.bluetooth.com/zh-cn/develop-with-bluetooth/qualification-listing/)下载这篇文章。

 [蓝牙核心规范](https://www.bluetooth.com/specifications/specs/)是实施者的唯一参考。

## **4.基于决策的广播过滤**

#### **4.1 背景**

本节将解释低功耗蓝牙技术中与基于决策的广播过滤（DBAF）功能相关的方面。

##### **4.1.1 链路层状态**

链路层是低功耗蓝牙协议栈中最复杂的部分之一。它定义了用于空中传输的数据包和 PDU，以及作为各种_逻辑传输_定义一部分的发射器和接收器行为模式。

设备拥有一个或多个链路层实例，每个实例在特定时间处于特定状态 。状态和状态之间允许的转换由链路层状态 定义。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_9.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_9.png)_图 9 - 链路层状态_

表 4 简要介绍了每个链路层状态。

|**State**|**Description**|
|---|---|
|Standby|Device neither transmits nor receives packets.|
|Initiating|Responds to advertising packets from a particular device to request a connection.|
|Advertising|Transmits advertising packets and potentially processes packets sent in response to advertising packets by other devices.|
|Connection|In a connection with another device.|
|Scanning|Listening for advertising packets from other devices.|
|Isochronous Broadcast|Broadcasts isochronous data packets.|
|Synchronization|Listens for periodic advertising belonging to a specific advertising train transmitted by a particular device.|

表 4 - 链路层状态说明

广播、扫描和启动状态与DBAF功能有关。

##### **4.1.2 过滤器策略**

过滤策略定义了链路层决定是否接受接收到的数据包并将其传递到下一阶段处理的标准。在不同状态下定义了多种过滤策略。Host可使用HCI命令选择和配置过滤策略。

扫描和启动器链路层状态中使用的过滤策略与 DBAF 有关。

在扫描状态下，链路层实例会对接收到的广播数据包应用_扫描过滤策略_。在增加 DBAF功能之前，定义了两种基本的扫描过滤策略。_未经过滤的_扫描过滤策略会接收所有收到的广播数据包。使用_过滤_扫描过滤策略时，只接受来自_过滤接受列表_（由Host填充）中标识的设备的广播数据包。扩展扫描过滤策略定义用于定向广播，其中 PDU 包括广播数据包所针对的目标设备的地址 。

_启动器过滤策略_类似于扫描过滤策略，但其目的是选择那些可连接的广播PDU。[[3]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftn3)连接请求可能会被发送到这些 PDU。在 DBAF 之前，定义了两种启动程序过滤策略。在第一种情况下，只选择来自特定设备的可连接广播数据包。第二种情况是，接受来自_过滤接受列表_中所有设备的可连接广播数据包。

在任何情况下，过滤策略的应用都会导致链路层做出接受或丢弃接收到的数据包的决定。

##### **4.1.3 扩展广播**

蓝牙核心规范定义了几种广告形式。 广告广播（ADVB）逻辑传输涉及按照略微随机化的时间安排传输广告数据包。ADVB 的基本形式称为 _传统广播_和一种更复杂的变体，称为 _扩展广播_.

传统广播只在信道索引值为 37、38 和 39 的三个_主要广播_信道上传输数据包，不涉及其他_次要广播信道_。

扩展广播使用全部40个低功耗蓝牙射频信道。标题数据在主通道上以 ADV_EXT_IND PDU 类型传输。这种PDU类型不包括 AdvData 字段，因此不携带应用数据有效载荷。相反，它通常包含一个称为 AuxPtr 的字段，该字段引用包含 AUX_ADV_IND PDU 的相关辅助数据包，该数据包在 37 个辅助广播信道之一上传输。该 PDU 包含 AdvData 有效载荷字段。

AuxPtr 包括一个信道索引值，表示辅助数据包将在哪个信道上传输、使用的 PHY 以及定时偏移量，以便接收器知道何时、何地以及如何接收。在辅助信道上传输并通过 AuxPtr 字段从主信道上的数据包引用的数据包称为辅助数据包，而引用的数据包称为上级数据包。

较大的应用数据有效载荷可能会被分割，并作为一系列链接的 PDU 发送。该系列以 AUX_ADV_IND PDU 开始，并以若干 AUX_CHAIN_IND PDU 继续。AUX_ADV_IND PDU 和每个连续的 AUX_CHAIN_IND PDU 都使用 AuxPtr 字段进行链接。图 10 显示了以 PDU 链为特征的扩展广播 示例。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_10.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_10.png)_图 10 - 带有 PDU 链的扩展广播_

扩展广播 PDU（如 ADV_EXT_IND）包括一个扩展标头。它包含一系列字段，根据蓝牙核心规范的规定，这些字段在 PDU 中的存在是强制性、可选或有条件的。

##### **4.1.4 启动状态**

在启动状态中，设备试图从扫描状态过渡到连接状态。为此，它会监听目标设备的可连接广播 PDU，并在收到后回复 CONNECT_IND PDU传统广播）或 AUX_CONNECT_REQ PDU扩展广播）。

##### **4.1.5 问题**

在使用扩展广播 的情况下，DBAF 可提高扫描设备的有效工作周期。它通过解决被称为“_分心_“的问题来实现这一目标。

**4.1.5.2 分心**

**4.1.5.2.1 什么是分心？**

在主通道上传输的 ADV_EXT_IND PDU 不包含应用数据。在某些情况下，观察者（扫描设备）必须跟踪 AuxPtr，在辅助信道上接收相关的辅助 PDU，并检查 AdvData 有效载荷字段的内容，然后才能决定是否对广播数据感兴趣。为此，它必须停止对主信道的扫描，转而对 AuxPtr 字段中指示的辅助信道进行扫描。

根据不同的情况，很多时候可能会发现广播数据并不重要。这是一个问题，因为在观察者扫描 AuxPtr 所指示的辅助信道期间，它不再扫描主信道，因此可能会错过相关的数据包。

这种跟随 AuxPtr 扫描并接收非应用目标数据包的情况被称为_分心_。

分心会降低观察者的有效占空比。分心导致主信道上的数据传输丢失，会降低使用扩展广播作为无连接数据传输 机制的设备的整体数据传输 ，并增加其他设备的延迟。

**4.1.5.2.2 广播集和重复数据**

PDU的扩展头字段包括一个名为 AdvDataInfo（ADI）的可选字段。ADI 包含两个子字段：广播数据 ID (DID) 和广播集 ID (SID)。SID 标识传输 PDU 所属的广播集。DID 包含一个随机数，只有在同一广播设备传输的属于同一广播集的 PDU 包含新数据时才会改变。

AdvDataInfo 可以包含在主信道上传输的 ADV_EXT_IND PDU 中，这些 PDU 有一个与之相关的辅助数据包。这使扫描设备有机会只选择属于相关广播集的 PDU，并识别它们已经接收到的重复数据。当上述任一条件适用时，观察者可避免在辅助信道上扫描辅助数据包。

AdvDataInfo 字段有助于避免浪费对次级信道的扫描，但对于某些情况来说，这种机制还不够完善。

#### **4.2 关于基于决策的广播过滤**

##### **4.2.1 概述**

DBAF 引入了一种新的扩展广播 PDU 类型，称为 ADV_DECISION_IND，非正式地称为_决策 PDU_。 这种 PDU 类型可用于替代 ADV_EXT_IND扩展广播 PDU，并同样在主通道上传输。

决策 PDU 包含应用数据，扫描仪可对这些数据进行评估，以做出更明智的决策，确定是否对相关的 AUX_ADV_IND 辅助数据包感兴趣，从而决定是否开始扫描其 AuxPtr 字段所引用的辅助信道。

广播设备可以配置决策 PDU 的内容，以便相关设备可以轻松检查接收到的数据包是否相关。

扫描设备可以配置其过滤策略，对接收到的决策 PDU 内容进行一系列逻辑检查，从而可靠地识别相关数据包，并扫描相关的辅助数据包，以获取其应用 有效载荷数据。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_11.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_11.png)_图 11 - DBAF 概述_

##### **4.2.2 效益**

DBAF 的优势在于应用程序可以对控制器过滤接收到的数据包进行更复杂的控制。那些未通过应用过滤检查的决策 PDU 将被丢弃，而且不会对辅助数据包进行扫描，从而避免了_分心_。

使用决策PDU代替ADV_EXT_IND扩展广播PDU有可能大幅提高有效占空比，并减少主信道上由于分心问题而漏发数据包的情况。这在有大量广播设备使用扩展广播的环境中尤为明显。

在使用数据传输作为基础承载（如作为信息传输）的情况下，数据吞吐率不会因传输而降低，否则会造成干扰。

##### **4.2.3 技术要点**

**4.2.3.1 广播**

**4.2.3.1.1 决策 PDU**

决策 PDU 正式名称为 ADV_DECISION_IND PDU，在 LE 1M 或LE Coded PHY 的链路层数据包中传输。图 12 显示了 ADV_DECISION_IND PDU 的结构以及如何通过 LE 1M（未编码）PHY 将其纳入链路层数据包。

[![图 12](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_12.png "Figure 12")](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_12.png)_图 12 - LE 未编码链路层数据包和 ADV_DECISION_IND PDU_

AdvMode和Extended Header字段出现在所有扩展广播PDU中。AdvMode 表示广播事件类型或定义的三个值。

|**AdvMode**|**Mode**|
|---|---|
|0b00|Non-connectable and non-scannable|
|0b01|Connectable and non-scannable|
|0b10|Non-connectable and scannable|
|0b11|Reserved for future use|

扩展报头字段包含各种标准字段，其存在与否取决于 PDU 类型、广播模式、PHY 和应用偏好等因素。AdvDataInfo（ADI）字段包括用于识别重复数据的 DID，是一个扩展报头字段。

AuxPtr 是唯一必须包含在决策 PDU 中的扩展报头字段。

决策 PDU 的特定字段是决策类型标志字段和决策数据字段。

扫描设备可指定对接收到的决策PDU进行检查，此类检查可能涉及扩展报头中的字段、信号强度（RSSI）或广播设备在决策数据字段中提供的特定类型的补充数据。

判定数据包含标准子字段，目前只指定了其中一个。这就是可解决标记字段。将来可能会定义其他子字段。Resolvable Tag 等标准子字段未占用的空间可用于其他_任意数据_。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_13.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_13.png)_图 13 - 决策数据字段_

判定类型标志字段表示判定数据字段中存在哪些子字段。被置位的比特表示蓝牙核心规范中与该字段内比特位置相关联的子字段的存在。位置 0 的位与可解决标记子字段有关。所有其他位均为保留位（RFU）。

**4.2.3.1.2 配置决策 PDU**

广播设备的Host负责使用决策PDU配置和启动广播。

判定类型标志和判定数据字段的值必须由Host提供。这可以通过 HCI 命令_LE Set Decision Data_ 来实现。该命令的参数包括标识_广播_集的_广播句柄_、_判定类型标志_、_判定数据长度_和_判定数据_。该命令可在创建广播集后的任何时间调用，包括在广播开始后。这意味着应用可以根据需要随时更改决定数据字段。

人机交互命令_LE Set扩展广播参数_用于配置广播集的主要变量，包括广播间隔等。该命令的参数之一_Advertising_Event_Properties_是一个位掩码，表示与所配置的广播集有关的各种Host要求。例如，如果设置了第 0 位，则表示Host要求控制器使用可连接的广告模式。如果设置了第 1 位，则广播应是可扫描的。

广播事件属性参数定义已更新，允许第 7、8 和 9 位与决策 PDU 结合使用。表 5 概述了这些位的含义。

|**Bit**|**Meaning**|
|---|---|
|7|Use decision PDUs when advertising|
|8|Include AdvA in the extended header of all decision PDUs|
|9|Include ADI in the extended header of all decision PDUs|

表 5 - 广播事件属性和决策PDU

如图所示，利用广播事件属性位 7，Host可指示控制器在相关广播事件中传输决策 PDU。由于扫描设备控制器可指定使用的决策 PDU 检查的复杂性，广播设备的设备地址 和/或 ADI 字段可能是不必要的，位 8 和 9 允许排除其中任何一个或两个字段，从而可能将数据包缩短 8 个八进制数，并将 LE 1M 的通话时间缩短 64 µs。

**4.2.3.2 扫描**

**4.2.3.2.1 决策扫描过滤策略模式**

如果扫描设备上的应用希望使用基于决策的广播过滤，则必须向蓝牙控制器说明。这可以通过 HCI_LE 设置扩展扫描参数_命令和_扫描过滤策略_参数的位 2 和 3 来实现。

通过这些位可以选择三种模式中的一种。

|**Value**|**Meaning**|
|---|---|
|0b00|No decisions mode. In this mode, decision PDUs are ignored.|
|0b01|All-PDUs mode. All types of advertising PDU are selected. Decision PDUs are subject to checks specified by the host. Other advertising PDUs are subject to the basic filter policy.|
|0b11|Decisions-only mode. Only decision PDUs are selected. These are subject to checks specified by the host. Those that pass are reported to the host in HCI advertising reports. Those that fail are discarded.|

**4.2.3.2.2 决策指示**

扫描设备上的应用 使用_LE 设置决策指令_命令来指定链路层在执行过滤策略时必须应用于决策 PDU 的测试。

该命令的三个数组参数允许Host配置要进行的测试。

|**Parameter**|**Meaning**|
|---|---|
|Test_Flags[i]|The first 4 bits of this field have defined meanings.<br><br>Bit 0 – Creates partitioned groups of tests. See below.<br><br>Bit 1 – The test passes if the decision data contains the _relevant field_ and the check made against its value **_passes_**.<br><br>Bit 2 – The test passes if the decision data contains the _relevant field_ and the check made against its value **_fails_**.<br><br>Bit 3 – The test passes if the decision data does not contains the _relevant field._<br><br>The value in Test_Field[i] identifies the _relevant field_. Note that the term “relevant field” applies both to fields in the advertising PDU that may be used in decision checks and values which may be measured (e.g. RSSI) or otherwise calculated (e.g. path loss) and used in decision checks.|
|Test_Field[i]|Identifies the decision data against which the check will be made. The data available for use in decision tests are:<br><br>- Resolvable Tag subfield in Decision Data<br>- AdvMode – advertising mode<br>- RSSI – received signal strength indicator<br>- Path loss calculated from the TX Power field (which must be present) and RSSI<br>- AdvA — the advertising device’s address<br>- Arbitrary Data (with various options re: minimum length of such data for the field to be regarded as present)<br>- Vendor-specific|
|Test_Parameters[i]|Values to use in checks against the relevant field. The format of this field depends on the relevant field identified in the Test_Field[i] parameter.|

**4.2.3.2.3 测试组**

由 Test_Flags、Test_Field 和 Test_Parameters 三个参数数组代表的测试数组被划分为一个或多个_测试组_。

由 Test_Flags[0]、Test_field[0] 和 Test_Parameters[0] 表示的第一个测试是第一个测试组的成员 。遍历数组中的测试，如果 Test_Flags[i]的第一位被设置，那么它就是新测试组的成员 。如果未设置，则是数组中前一个测试组的成员，由索引值 [i - 1] 引用。表 1 显示了一个示例。

|**Index**|**Test Flags**|**Group Membership**|
|---|---|---|
|0|0b0011|Start of a new group (bit 0 = 1).|
|1|0b0010|Test is a member of same group as test[0].|
|2|0b0011|Start of a new group (bit 0 = 1).|
|3|0b0100|Test is a member of same group as test[2].|
|4|0b0010|Test is a member of same group as test[2].|

表 6 - 由 Test_Flags 位 0 控制的成员组示例

如果属于同一组的任何一项测试失败，则该组中的所有测试均被视为失败。

**4.2.3.2.4 测试评估**

请注意，在接下来的描述中，_测试_是指在 Test_Flags、Test_Field 和 Test_Parameters 参数数组的并行元素中编码的条件。_检查_是指使用从特定决策 PDU 获取或导出的特定值对测试进行评估。

链路层对每个接收到的决策 PDU 的 DBAF 测试评估如下：

对于Host指定的每个测试，首先要检查_相关字段_的可用性。这可能是指接收到的 PDU 中是否存在字段，或者是否能够计算或测量测试中使用的指定值。Test_Flags[i]（测试标志）中的第 3 位表示缺少_所需字段_是否意味着测试通过或失败。

如果存在_相关字段_，则对 Test_Field[i]（测试字段）和 Test_Parameters[i]（测试参数）中编码的检查进行评估。位 1 和 2 用于确定通过或未通过的校验是指校验通过还是未通过。

组允许指定复合条件，组中的每个测试都与同组中的其他测试有逻辑 AND 关系。换句话说，一个测试组中的所有测试都必须通过，整个测试组才算通过。

|   |
|---|
|(group 1 test 1) AND (group 1 test 2) AND (group 1 test 3)|

表 7 - 同组测试之间的逻辑关系

就整套测试指令而言，如果一组或多组测试通过，则认为整套测试通过。换句话说，每个测试组与其他测试组之间是逻辑 OR 关系。

|   |
|---|
|(group 1) OR (group 2) OR (group 3) OR (group 4)|

DBAF 能够根据决策 PDU 中的字段或其派生值制定单独的条件检查，还能根据一系列测试组编码更复杂的复合条件，这两者的结合使 DBAF 成为应用程序的强大过滤机制。

**4.2.3.2.5 处理相关字段**

具体如何进行检查，以及 Test_Parameters[i] 条目的内容如何格式化，取决于 Test_Field[i] 所指示的相关字段。蓝牙核心规范 有详细的格式和规则，在此对每种类型的相关字段进行总结。

**可解决标签**

|**Test_Parameters[i]**|**PDU Data**|**Check**|
|---|---|---|
|A 128-bit **_key_** value.|Decision Data contains a **_hash_** value and a pseudo random number (**_prand_**).|Check passes if _hash_ value equals the value obtained by evaluating ah (**key**, **prand**). ah is a hashing function defined in the core specification.|

**AdvMode**

|**Test_Parameters[i]**|**PDU Data**|**Check**|
|---|---|---|
|A 3-bit Event Type value. The three bits act as flags that map to the three possible values of the AdvMode field.|AdvMode is included in the decision PDU.|Check passes if AdvMode is any of the values indicated by an EventType flag as accepted.|

**RSSI**

|**Test_Parameters[i]**|**PDU Data**|**Check**|
|---|---|---|
|A range of RSSI values expressed as a minimum and a maximum in dBm.|Measured by the controller for each received packet.|Check passes if the measured RSSI falls within the range specified in the test.|

**路径损失**

|**Test_Parameters[i]**|**PDU Data**|**Check**|
|---|---|---|
|A range of path loss values expressed as a minimum and a maximum in dBm.|Calculated by the controller as the difference between the TX Power field in the received PDU and the RSSI for that packet.|Check passes if the calculated path loss falls within the range specified in the test.|

**AdvA**

|**Test_Parameters[i]**|**PDU Data**|**Check**|
|---|---|---|
|Contains a field called **_Check_** that indicates how to check the AdvA address field in the received decision PDU and zero, one or two test address values and types.|AdvA is a field which may be included in decision PDUs.|Depending on the **_Check_** parameter field, evaluation of the check will pass if either:<br><br>1.      AdvA in the PDU is in the controller’s Filter Accept List.<br><br>2.      AdvA in the PDU matches the first of two possible addresses in the Test_Parameters[i] field.<br><br>3.      AdvA in the PDU matches either of the  two addresses in the Test_Parameters[i] field.|

**任意数据**

|**Test_Parameters[i]**|**PDU Data**|**Check**|
|---|---|---|
|Contains an 8-octet **_Mask_** and an 8-octet **_Target_** value.|The decision PDU Decision Data field contains an Arbitrary Data subfield.|The controller performs a bitwise AND of the **_Mask_** and the Arbitrary Data value (zero-padded if necessary). If the result matches the **_Target_** parameter, the check passes.|

**特定供应商**

Test_Parameters[i] 值的解释和测试中应用的条件逻辑，顾名思义是针对特定供应商的。

**4.2.3.2.6 可重置标签和密钥共享**

可重置标签提供了一种简单的方法，将 PDU 标记为与特定应用和设备相关。为使该系统正常工作，用于哈希生成和检查的密钥值必须在适当的设备之间共享。实现的机制和程序将在未来的 GATT 属性和配置文件 规范中定义。

**4.2.3.3 启动**

Host 可将控制器的_启动过滤_ 策略配置为多种受支持的运行方式，其中一些涉及决策 PDU。当策略中涉及判定 PDU 时，接收到的 PDU 在判定指令应用 方面的处理与扫描状态相同。 

## **5.监测广播设备**

#### **5.1 背景**

本节介绍与监视广播设备功能相关的低功耗蓝牙技术的各个方面。 

##### **5.1.1 设备发现**

低功耗蓝牙中_广播_的用途之一是便于_发现设备_。通过每隔一段时间广播小数据包，设备会告知范围内的其他设备它的_存在_。同时，设备还可以表明自己愿意并能够接受其他设备的连接。

通过_扫描_可发现其他设备。扫描使设备的无线电每隔一段时间进入接收模式，并在一定时间内监听主要低功耗蓝牙信道中的传输。当广播设备在扫描设备当时正在监听的信道上广播数据包时，扫描设备就会接收到该数据包，广播设备也就被发现了。

为发现设备而发布广播是低功耗蓝牙技术的基本理念。

![](https://www.bluetooth.com/wp-content/uploads/2024/07/Bluetooth_Core_6_Figure_14.svg)_图 14 - 广播和扫描_

##### **5.1.2 连接**

发现广播设备后，下一步通常是扫描设备尝试连接广播设备，这可能是为了响应用户的操作，例如从列表中选择设备。

连接是通过发送 CONNECT_IND PDU 以回复传统广播 PDU（如 ADV_IND PDU）或发送 AUX_CONNECT_REQ PDU 以回复 AUX_ADV_IND扩展广播 PDU 来实现的。无论哪种情况，连接请求都是在与被响应 PDU 相同的信道上发送的。

互联设备必须先进行扫描，才能接收到可发送连接请求的PDU。通常情况下，最好能快速建立连接，为此将使用_高占空比扫描_。这就要求无线电在大部分时间内开启并处于接收器模式，以尽可能快地接收到所需的可连接广播数据包。一般来说，扫描是一种相对耗电的操作，而高占空比扫描则更加耗电。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_15.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_15.png)_图 15 -连接_

##### **5.1.3 范围**

扫描设备只有在广播设备和扫描设备的距离在一定范围内时，才能接收广播设备发送的数据包，并作出响应。范围取决于许多因素，如传输功率、接收器灵敏度和环境性质。设备作为发射器时的射程可能与作为接收器时的射程不同。与之通信的其他设备的范围也可能与第一个设备的范围不同。

超出范围并不一定意味着接收不到另一设备发送的信号。一个设备可能能够接收到另一个设备的传输信号，但如果接收到的信号强度与任何背景噪声的比值（即信噪比或 SNR）使接收器无法从传输中提取数据，而又不会出现过高的错误率，那么这两个设备就会被视为超出范围，因为从所有意图和目的来看，它们都是超出范围的。

如_3.1.1位置服务和低功耗蓝牙_ 中所述，RSSI 可作为距离的粗略代用指标，并用于计算路径损耗。对于某些应用而言，只有在距离足够近的情况下_，_ 连接 到另一个设备才有意义。用例可能是评估的关键部分。也许只有当用户离另一个设备很近时，连接才有意义。因此，有时会定期测量 RSSI 并进行评估，然后应用 才会认为自己与另一设备的距离足够近，有必要与其建立连接。

##### **5.1.4 筛选重复文件**

当低功耗蓝牙控制器中的链路层处于扫描状态时，低功耗蓝牙控制器中的链路层会接收广播数据包。广播设备以配置的时间间隔重复发送数据包。当用于设备发现目的时，广播数据包的内容往往不会随时间而改变。

控制器从一个或多个设备接收到的广播数据包中的数据会在人机交互事件中传达给Host 。为向Host报告广播数据定义了几种 HCI 事件类型，使用哪种类型取决于所涉及的广播类型。例如，传统广播使用低功耗广播报告事件。如果是扩展广播，则使用低功耗扩展广播报告事件。其中 _周期性广播_则使用低功耗周期性广播报告事件。

广播，尤其是来自环境中多个设备的广播，会产生大量人机交互广播报告，每个报告都通过内部传输从控制器传递到Host 。使用API注册以接收广播数据的应用程序可能会收到大量回调，但这些回调中传递的数据却一成不变，因此其价值值得怀疑。

不过，重复接收来自同一设备的不变广播数据包确实有一定价值。它允许扫描设备跟踪其他设备当前是否在范围内。

幸运的是，允许Host启用扫描的 HCI 命令_（LE Set Scan Enable_和_LE Set Extended Scan Enable_）都有一个名为 Filter_Duplicates 的参数。这允许Host向控制器指出是否应向其发送重复广播报告。

图 16 显示host 在未启用重复过滤的情况下启用了扫描。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_16.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_16.png)_图 16 - 广播数据包和报告_

图 17 显示了启用扫描并打开重复过滤的情况。请注意，只有收到的第一个广播数据包才会向Host发送广播报告。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_17.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_17.png)_图 17 - 过滤重复的广播PDU_

Filter_Duplicates 选项作用于来自所有设备的所有广播数据包，因此无法将其仅应用于特定设备，而不过滤来自其他设备的所有广播数据包。

因此，应用程序可以做出选择。第一种选择是接收所有广播报告，并保持对另一个设备是否在范围内的最新感知，但这将产生大量的人机交互流量和应用代码回调。另一种选择是抑制重复广播报告的报告，但会立即失去对相关设备是否继续保持在范围内的跟踪。这两种方案都不理想

##### **5.1.5 蓝牙低功耗音频和接收器可用性**

在通用音频配置文件 (CAP) 术语中，"接受器"（Acceptor）是指可以接受来自另一设备（称为 "启动器"）的音频串流的设备。建议启动器不要使用过滤接受列表（见_4.1.2 过滤策略_），因为该列表中通常填有发起方已绑定的设备地址。个人音频设备很可能已经绑定，但低功耗音频涉及的不仅仅是个人音频。

为了获得最佳的用户体验，当需要建立音频流时，应尽可能减少延迟。因此，跟踪候选接收器是否在范围内是可取的。扫描音频设备只是为了检查它是否仍在范围内，然后再扫描，这样做是浪费时间和精力，会对延迟和用户体验产生不利影响。

低功耗音频使用案例是设计监测广播设备功能的关键场景之一。

#### **5.2 关于监测广播设备**

##### **5.2.1 概述**

使用Filter_Duplicates禁止报告与已报告给Host的广播数据包相同的数据包，会使Host在连接时无法确定广播设备是否仍在范围内。连接之前通常会进行昂贵的高占空比扫描，如果目标设备已不在范围内，那么这一活动就完全是在浪费能量。 监测广播设备功能解决了这一问题。

使用监测广播设备功能时，Host 会指示控制器跟踪一个或多个广播设备的存在。监测广播功能不会在每个接收到的广播数据包中都向Host 发送一份广播报告，而是在被监测设备离开监测范围时通知Host 一次，在其返回监测范围时再通知Host 一次。这为应用跟踪它可能想连接的设备提供了一种有效的方法。它还考虑了应用对信号强度的要求。

当应用在收到设备在范围内的通知后决定连接到某个受监测设备时，连接前的扫描就不可能是白费力气了。目标设备应该就在附近，因此扫描会产生一个广播数据包，可以发送连接请求作为回应。

监测广播设备的操作独立于过滤接受列表（见_4.1.2 过滤策略_），因此可以方便地将过滤接受列表仅用于绑定设备，而将监测广播设备用于所有设备，无论这些设备是否已与扫描设备绑定。

通过提高能效和改善用户体验，有许多情况和类型的产品都将从监测广播设备功能中受益。启动音频流的低功耗音频设备_（CAP 启动器_）是本功能所定义的一类产品 。

##### **5.2.2 技术要点**

**5.2.2.1 受监测的广播设备名单**

蓝牙核心规范定义了监视广播设备列表。这是控制器中的一个数据结构，包含Host希望跟踪的广播设备列表。

列表中的每个设备都有几个参数，每个条目都可以看作是一个相关的定时器。此外，每个条目都有一个名为 "_等待 RSSI 高值_"的状态 ，该状态由执行系统维护。该状态 表示被监测设备是否在范围内。如果 "等待 RSSI High "为 true，则表示设备不在范围内。 

通过了解监测广播设备列表中的参数，可以了解控制器如何进行监测。

|**Parameter(s)**|**Description**|
|---|---|
|Address and Address Type|The address and address type of the device to be monitored. These two parameters allow the controller to identify and monitor the device.|
|RSSI Threshold Low|If the RSSI of all advertising packets from this monitored device stays at or below this value for the period of time indicated by the Time Out parameter then it is said that a _loss-of-signal_ has occurred. When this happens, the controller notifies the host using an HCI LE Monitor Advertisers Report event. The state of this device set to _Awaiting RSSI High._|
|RSSI Threshold High|If the RSSI of an advertising packet received from this monitored device is greater than or equal to this value, and the device state is _Awaiting RSSI High_ then the controller sends a HCI LE Monitor Advertisers Report event to the host to inform it that the device is in range. The state for this device is cleared or set to indicate that it is no longer awaiting an RSSI above the high threshold and the timer that is used to monitor for loss of signal is reset.|
|Time Out|A time in seconds used to monitor for signal loss. If no RSSI measurement exceeds the RSSI Threshold Low parameter in this period then loss-of-signal is said to have occurred.|

**5.2.2.2 Host控制器接口**

Host配置监测广播设备列表，并通过Host控制器接口 (HCI) 接收与受监测广播设备相关的事件。定义了三条命令和一个事件。

|**HCI Command or Event**|**Description**|
|---|---|
|LE Monitored Advertisers List command|Used by the host to add or remove an entry from the Monitored Advertisers List or to clear the list completely. An array of one or more devices to be monitored plus their associated RSSI thresholds and timeout parameter are provided in this command.|
|LE Monitored Advertisers Enable command|Allows the host to enable or disable advertiser monitoring in the controller.|
|LE Read Monitored Advertisers List Size command|Allows the host to determine the total number of entries the controller can currently accommodate in its Monitored Advertisers list. Note that this value may change at any time.|
|LE Monitored Advertisers Report event|Generated by the controller whenever for a monitored device there is a loss-of-signal or the device comes back into range. The _Condition_ parameter indicates which of these two conditions is responsible for the event having been generated.|

**5.2.2.3 示例**

图 18 展示了监测广播设备的运行情况。插图的左半部分是一个信息序列图。广播设备被描绘成一个整体，而扫描设备则被分为控制器和Host两部分，以便查看两部分之间的人机交互通信。  

图的右半部分显示 RSSI 值、已设置的 RSSI 低阈值和高阈值，以及计时器和_等待 RSSI 高_ 状态 信息。

时间从图表的顶部流向底部。关注点按字母顺序标注在左侧时间轴上。表 8 汇总了以下内容。

|**Point**||
|---|---|
|A|The scanner’s host starts by asking the controller how many advertising devices it can monitor.  The host then adds a device to the list along with RSSI low, RSSI high and timeout values (not shown). Finally, the host tells the controller to enable advertiser monitoring.|
|B|At this point the illustration starts to show advertising packets transmitted by the first device. Note that the device could have been advertising prior to this point but the packets are only shown from here. Received packets have an RSSI that is greater than the configured low threshold and so the timer for the monitored device is reset as each packet is received.|
|C|The next few packets received after point C have an RSSI that is lower than the low RSSI threshold and so it is at point C that the timer is last reset and the timer runs from that point.|
|D|A series of low RSSI packets are now received and at point D, a timeout occurs. The controller indicates the loss of signal condition to the host by sending a LE Monitor Advertisers Report event with condition == 0x00. The device is now in the Awaiting High RSSI state in the monitoring advertisers list.|
|E|At point E, the first of a series of packets whose RSSI is above the low threshold is received. For each such packet, the timer is reset.|
|F|At point F, the RSSI value exceeds the RSSI High threshold. The host is informed that the monitored device is back in range with a sufficiently strong signal via a LE Monitor Advertisers Report event with condition == 0x01 sent by the controller. The device is no longer in the Awaiting High RSSI state.|

表 8 -监测广播设备示例：兴趣点

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_18.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_18.png)_图 18 - 使用中的监测广播设备示例_

## **6.ISOAL增强**

#### **6.1 背景**

本节将解释低功耗蓝牙技术中与低功耗蓝牙协议栈等时适配层 (ISOAL) 增强相关的方面。

##### **6.1.1 等时通信**

低功耗蓝牙数据传输架构包括 LE CIS 和 LE BIS 逻辑传输，其中 CIS 表示连接异步流，BIS 表示广播异步流。这些逻辑传输由 LE 等速物理链路和 LE 等速物理通道支持。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_19.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_19.png)_图 19 - 等时通信和数据传输架构_

当设备间传输的数据有_时间限制时_，就会使用等时通信。这意味着，当接收器处理传输的数据时，必须遵守严格的时间关系。

蓝牙低功耗音频 使用等时通信，这确保了多个相关数据流将在同一时间由各自的接收器呈现。更具体地说，举例来说，这意味着左立体声声道的音频数据和右立体声声道的音频数据可由音频源设备在不同时间传输，但将由两个独立的音频接收设备（如左和右耳塞）以用户期望的方式同时呈现两个立体声声道。

CIS 为等时通信提供了一种面向连接的方法。CIS 通常涉及小型设备群，例如一部智能手机和一对助听器。不过，通信可以是双向的，因此助听器可以包括一个麦克风，同时充当音频源和音频汇。

BIS 涉及等时数据广播，用于向一大批设备传送音频等等时数据。不过，通信是单向的。

异步通信，尤其是在处理音频数据时，会遇到许多挑战。

首先是在多个完全独立的设备上正确同步_呈现_数据（这里指的是音频播放）。这正是等时通信所要地址的问题。

延迟有时是一个问题，有时则不是。只有当用户有其他参照物来比较音频设备中声音的预期时间和他们所体验到的声音的实际时间时，他们才有可能意识到延迟。例如，如果助听器用户既能听到周围的声音，也能听到传输到助听器 的声音，那么如果存在明显的延迟，用户就会感觉到周围的声音和放大的声音之间存在延迟。蓝牙等时通信允许选择低延迟配置，以帮助满足此类设备的要求。

可靠性非常重要，因为在许多音频场景中，对数据丢失的容忍度是有限的。CIS 和 BIS 都包含提高可靠性的机制。

##### **6.1.2 数字音频**

等时通信并非仅用于音频应用，但却是其最初设计的主要用途。数字音频数据的生成方式带来了一些挑战，低功耗蓝牙协议栈中的等时适配层（ISOAL）可以解决这些问题。

音频通过_采样_转换成数字格式。采样包括以固定的时间间隔测量和记录信号的振幅，这将产生大量数据，在蓝牙低功耗音频 中，这些数据最终需要被传输。

蓝牙低功耗音频使用一种名为编解码器的编解码器[[4]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftn4)编解码器是一种压缩算法，可对样本数据进行压缩，从而大幅缩小样本数据的大小。编解码器一般通过识别和利用一系列连续样本中发现的模式来工作。因此，编解码器需要同时分析一系列样本才能工作。

编解码器一次分析的样本集合称为一帧。帧有固定的持续时间，通常以毫秒为单位，包含的样本数由采样率决定。例如，如果采样率为 44.1 KHz，10 毫秒的帧包含 441 个样本。

##### **6.1.3 ISOAL**

**6.1.3.1 蓝牙架构中的 ISOAL**

数字音频等数据由系统的应用 产生。它位于蓝牙堆栈的Host 部分，通常是操作系统（OS）服务 或在操作系统上运行的用户应用 。在蓝牙核心规范中，为等时通信提供数据的层简称为_上层_。

蓝牙链路层使用一种等时逻辑传输方式与一个或多个其他设备进行数据通信。链路层在蓝牙控制器中实现，蓝牙控制器通常是一个芯片上的系统。

ISOAL 以_服务数据单元_（SDU）与 ISOAL 交换等时数据，ISOAL 则与链路层交换协议数据单元（PDU）。图 20 显示了蓝牙系统这三个部分之间的关系。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_20.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_20.png)_图 20 - 蓝牙架构中的 ISOAL_

Host和控制器是典型的独立组件，通过 USB 或 UART 等支持的传输方式之一，使用Host控制器接口相互通信。

**6.1.3.2 ISOAL 解决的问题**

在两个重要领域，上层数据生产者的运行参数与链路层的运行参数之间的差异可能会导致问题的复杂化。

首先是上层产生的 SDU 的大小。通常情况下，SDU 要比链路层支持的最大 PDU 大得多。

_ISOAL 使上层能够生成比链路层在单个 PDU 中所能处理的 SDU 更大的 SDU。_

第二个问题与时间有关。链路层的数据传输是在间隔时间发生的事件中进行的。这个时间间隔可取一系列值，一般称为_ISO_ 时间间隔。上层也会以一定的时间间隔产生帧，并以 SDU（SDU代表服务数据单元）的形式向下传递。上层产生 SDU 的时间间隔称为_SDU间隔_ 。

控制器链路层使用的 ISO 间隔通常与 Host 上层使用的 SDU 间隔不同，而且这两个间隔值也不是整数倍。此外，这两层的活动不同步也很常见，因此数据通过系统时可能会出现等待延迟。需要注意的是，如果链路层在事件发生期间没有来自上层的数据要传输，则会传输一个空 PDU。

图 21 显示了 SDU 和 PDU 生产不同步的影响。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_21.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_21.png)_图 21 - 非同步 SDU 和 PDU 的生成_

要传输的数据与时间紧密相关，接收器必须能够还原这种时间关系，并确保在处理数据时达到预期结果。这始终是一个问题，但当上层和传输层之间没有同步时，问题就更加复杂了。

_ISOAL 允许上层生成 SDU 的速率不同于链路层传输等时 PDU 的速率，并允许它们的运行不同步。_

**6.1.3.3 ISOAL 处理路径**

等时数据通过 ISOAL 有两种可能的路径，图 22 用不同的颜色表示了这两种路径。

如果 SDU 间隔是 ISO 间隔的整数倍，并且上层和传输层的操作同步，那么就会通过一个称为_分片_的过程产生_非成帧 PDU_。 否则，将生成_有帧 P_DU，并应用称为_分段_的过程。

[![图 22](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_22-1000x803.png "Figure 22")](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_22.png)_图 22- ISOAL_

**6.1.3.4 无框架和有框架 PDU**

如果使用的是非成帧 PDU 路径，那么大于链路层允许的最大 PDU 大小的 SDU 会被一个称为_片段_的过程分割成更小的部分。片头指示片段是整个 SDU，还是 SDU 的开始、继续或结束。

在反方向上，SDU 由从链路层接收到的较小的未成帧 PDU_重新组合而成_。

如果使用有帧 PDU 路径，就会对 SDU 进行称为_分段_的处理。与分片一样，这也是将 SDU 分割成带有报头的较小部分，但表示 SDU 开始的报头还包含定时偏移信息，这样接收器 就能_重新组装_并保留这些关键的定时信息。

SDU 在一个或多个链路层 PDU 中传输，具体取决于分片或分段过程的结果。

**6.1.3.5 成帧模式**

蓝牙核心规范中定义了_成帧模式_。在 6.0 版之前，只定义了两种成帧模式，分别对应有帧或无帧情况。

**6.1.3.6 ISOAL 分段的问题**

ISOAL 成帧过程处理上层传给它的数据的两个方面。它将较大的 SDU 分割成较小的 PDU，从而使其得以传输；它还确保数据与时间的关系得以保留并可以重建。

分段有两个问题，视应用而定，可能重要，也可能不重要。

首先是可靠性。在任何无线通信系统中，数据包丢失的概率总是存在的。如果一个包含音频数据的 SDU 被分割成多个 PDU，通过一系列相应的链路层数据包在空中传输，那么其中任何一个或多个数据包丢失的概率就会增加，从而导致整个 SDU 丢失。

第二个问题是延迟。如果采用分段，那么接收设备的上层必须等到收到 SDU 的所有分段后才能重新组合和处理。就音频而言，这意味着要重新创建一个音频帧，并使用编解码器对其进行解码。[[5]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftn5)在进入音频渲染阶段之前，音频编解码器需要等待一段时间。这个等待时间就是延迟。

#### **6.2 关于ISOAL增强**

异步适配层有一种新的成帧模式，称为 "_未分段成帧模式_"。主机可通过在 HCI LE 设置 CIG 参数命令或 LE 创建 BIG 命令的成帧参数中指定 0x02 的值来选择该模式。

非分段成帧模式允许使用成帧 PDU，并保留每个 SDU 的定时信息，但不需要应用 分段。这种新的成帧模式有两个好处。首先，消除了分段过程造成的延迟。其次，降低了因数据包丢失而导致 SDU 丢失的风险。

##### **6.2.1 减少延迟**

通过消除成帧过程中的分段，每个链路层数据包实际上都包含了一个完整的 SDU。在低功耗音频 的情况下，这相当于一个完整的音频帧，上层无需等待收到一系列数据包后才能对收到的音频数据进行解码和处理。

##### **6.2.2 提高可靠性**

应用分段时，单个 SDU 作为多个数据包的有效载荷进行传输。假设数据包丢失的概率不变，则传输整个 SDU 所需的数据包越多，丢失一个或多个 SDU 部分的概率就越大。

使用非分段成帧模式时，最大 PDU 大小总是足以包含整个 SDU，而无需分段。因此，上层的 SDU 与链路层传输的 PDU 之间是一一对应的关系。因此，数据包丢失的风险不会像分段为每个 SDU 产生多个 PDU 那样增加。

## **7.LL 扩展功能**

#### **7.1 背景**

链路层（LL）是低功耗蓝牙协议栈的一个复杂层。该层定义了许多被称为_功能_的能力。

对功能 的支持通常是可选的。在使用功能 或执行与这些功能有关或依赖于这些功能的 LL 程序之前，设备需要确定其自身的蓝牙控制器和远程设备的控制器是否支持功能 。为此，蓝牙核心规范 定义了一个名为_FeatureSet 的_8 八位位掩码和一个功能 交换程序。

FeatureSet 的定义为其 64 位中的每一位赋予了意义。位值为 1 表示支持相关功能 ，位值为 0 表示不支持相关功能 。

功能交换链路层控制过程涉及在连接中由中心设备启动时交换 LL_FEATURE_REQ 和 LL_FEATURE_RSP PDU。外设也可以启动该过程，但要发送 LL_PERIPHERAL_FEATURE_REQ PDU，而中心设备则回复 LL_FEATURE_RSP。所有这三种 PDU 类型都包含 FeatureSet 位掩码，该掩码表示发送设备支持的功能。图 23 显示了由中心设备（此处描述为设备 A）启动的功能 交换链路层控制流程。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_23.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_23.png)_图 23 - 中央启动的 LL功能 交换程序_

随着时间的推移，蓝牙变得越来越复杂，其功能也越来越多。FeatureSet 位掩码的 64 位已不足以涵盖蓝牙核心规范 6.0 版本及其未来版本所定义的大量功能。 

图 24 显示了蓝牙核心规范 5.4 版中定义 FeatureSet 字段位含义的表格末尾。这里只有 63 位未分配。

![](https://www.bluetooth.com/wp-content/uploads/2024/07/Bluetooth_Core_6_Figure_24.svg)_图 24 -蓝牙核心规范版本{亚特兰大版本号}的 FeatureSet 字段_

#### **7.2 关于 LL 扩展功能**

##### **7.2.1 概述**

_LL 扩展功能_ 提供了一种方法，可将功能集字段中已分配位的功能以外的其他功能指示为设备支持或不支持。它的设计旨在支持蓝牙技术在未来的发展，其容量足以容纳 1984 个支持指示位。

##### **7.2.2 技术要点**

_LL 扩展功能集_ 本身是一种链路层功能 ，设备要么支持，要么不支持。这由 FeatureSet 字段中的第 63 位的值表示。

FeatureSet 位掩码已被放大并划分为可寻址页。第 0 页包含前 64 位，这些位是根据蓝牙核心规范 6.0 版之前的字段规范定义的。然后是 10 个页面，从 1 开始依次编号，每个页面大小为 192 位（24 个八位字节）。

支持 LL 扩展功能 集功能 的设备可使用_功能 页面交换_程序发现彼此的扩展功能 集。该程序可由中心设备或外围设备启动。

已定义两条新的人机交互命令和一个新的人机交互事件，供 LL 扩展功能 使用。它们分别是_LE 读取所有本地支持功能命令_、_LE 读取所有远程功能命令_和_LE 读取所有远程功能完成事件_。

调用 LE Read All Remote Features 命令会传输一系列 LL_FEATURE_EXT_REQ PDU，远程设备会用 LL_FEATURE_EXT_RSP PDU 对每个 PDU 作出回应。当检索到所有远程 FeatureSet 页面时，将在 LE 读取所有远程特性完成事件中向启动host 报告详细信息。请参见图 25。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_25.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_25.png)_图 25 - LL 扩展功能设置交换_

LL_FEATURE_EXT_REQ 和 LL_FEATURE_EXT_RSP PDU 具有相同的结构，链路层数据 PDU CtrData 字段中有三个字段。表 9 显示了这些 PDU 类型中的字段。

|**CtrData**|   |   |
|---|---|---|
|**MaxPage**<br><br>(1 octet)|**PageNumber**<br><br>(1 octet)|**FeaturePage**<br><br>(24 octets)|

表 9 - LL_FEATURE_EXT_REQ 和 LL_FEATURE_EXT_RSP PDU 的内容

MaxPage 字段用于表示存在非零位的最高页码。

PageNumber 字段用于标识扩展 FeatureSet 中 24 八位字节页面的编号，其值被请求或报告。

FeaturePage 包含由 PageNumber 标识的页面中的 192 位值。

功能页面交换程序可由Host 启动，也可由链路层自主启动。现有 HCI 命令和事件的新版本已经定义，以便Host使用扩展功能 集功能 。 

## **8.帧间隔更新**

#### **8.1 背景**

本节将解释低功耗蓝牙技术与帧间隔更新增强功能相关的方面。

##### 8.1.1 帧间空间

链路层定义_空中接口协议_，其中包括定义称为帧间空间（IFS）的时间间隔。

IFS 必须包含在同一信道上发送的两个连续数据包之间。在蓝牙核心规范 6.0 版之前，该时间段使用符号标识符 T_IFS，固定值为 150 µs。

各种传输类型还规定了事件或子事件中传输的最后一个数据包结束与下一个事件或子事件开始之间必须存在的最短持续时间。 

##### 8.1.2 连接状态

图 9 描述了链路层状态 。连接状态中可运行两种逻辑传输类型。它们是面向连接的异步逻辑传输（ACL）和连接的等时流（CIS）。

ACL 传输允许一台扮演中心角色的设备在_连接事件_期间与另一台扮演外设角色的设备交换数据包。

图 26 显示了蓝牙核心规范 6.0 版之前定义的 ACL 连接示例，固定值 T_IFS 定义了同一连接事件中从中心向外设或从外设向中心发送的数据包之间必须存在的时间间隔。此外，在一个连接事件结束和下一个连接事件开始之间，必须_至少_有一段 T_IFS 的时间间隔。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_26.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_26.png)_图 26 -通过 ACL 连接交换的数据包_

CIS 采用子事件系统，在子事件中交换数据包。在 6.0 版之前，同一子事件中数据包之间的时隙也被定义为固定值 T_IFS，如图 27 所示。此外，还定义了一个称为最小子事件空间（Minimum Subevent Space）的时间段，其符号名称为 T_MSS。 在一个 CIS 子事件结束和下一个 CIS 子事件开始之间，必须_至少_有一个 T_MSS 的时间段。在 6.0 版之前的蓝牙核心规范 中，T_MSS 与 T_IFS 具有相同的 150 µs 固定值。需要注意的是，CIS 有一个相关的 ACL 连接，用于建立 CIS 和交换影响 CIS 的链路层控制 PDU。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_27.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_27.png)_图 27 - 通过连接的等时数据流（CIS）交换的数据包_

#### **8.2 关于帧间隔更新**

##### **8.2.1 概述**

蓝牙核心规范 6.0 版对帧间距做了以下更改： 

- 为适用于 ACL 连接和 CIS 的时间间隔分配了五个不同的符号名称。
- 数值不再固定为 150 µs。
- 五种帧间距类型的默认值均为 150 µs，但中央和外围设备可在建立连接后协商新值。

帧空间值可以比默认的 150 µs 短或长。

这一变化仅适用于 ACL 连接和连接的等时数据流。其他传输类型继续使用 150 µs 的固定帧间距，现在使用符号名称 T_IFS_150。

较短的帧空间值可提高总体吞吐量。可从更短的帧空间和更高的数据吞吐率中获益的应用举例如下：

- 健身追踪器必须一次性将所有累积数据传输到互联设备 ，如智能手机或笔记本电脑。
- 固件更新。
- 蓝牙低功耗音频。通过连接的等时串流发送的音频数据包可以更快、更短地发送。这就降低了其他设备发生碰撞的可能性。
- 将无线电用于 Wi-Fi 等其他用途的设备有更多时间进行这些活动。

较长的帧空间值可能有利于处理能力相对较低的控制器，使控制器有更多时间处理较长的数据包。

##### **8.2.2 技术亮点**

**8.2.2.1 间距类型**

ACL 连接定义了三种间距类型。表 10 总结了 ACL 连接的新间距类型。

|**Spacing Type Symbolic Identifier**|**Definition**|
|---|---|
|T_IFS_ACL_CP|The duration of the required spacing time which must exist from the end of a packet transmission by the Central device and the start of the following slot in the same connection event, which may potentially be used by the Peripheral.|
|T_IFS_ACL_PC|The duration of the required spacing time from the end of a packet transmission by the Peripheral device in a connection and the start of the following slot to potentially be used by the Central in the same connection event.|
|T_IFS_END|The minimum time to elapse between the end of a connection event and the start of the next one.|

表 10 - ACL 连接的新帧间距类型和标识符

图 28 描述了 ACL 连接中的连接事件和数据包传输，新的间隔类型用符号标识符表示。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_28.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_28.png)_图 28 - ACL 连接中的新帧间距类型_

为连接的等时数据流定义了两种间隔类型。表 11 概述了 CIS 的新间隔类型。 

|**Spacing Type Symbolic Identifier**|**Definition**|
|---|---|
|T_IFS_CIS|The duration of the required spacing time from the end of a packet transmission by the Central device in a CIS and the start of the following transmission by the Peripheral.|
|T_MSS_CIS|The minimum subevent space which is the minimum time that must elapse between the end of a packet transmitted in one subevent and the start of the next subevent.|

表 11 - CIS 的新帧间距类型和标识符

图 29 描述了连接的等时数据流中的子事件和数据包传输，新的间隔类型用符号标识符表示。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_29.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_29.png)_图 29 - 连接的等时数据流 (CIS) 中的新帧间距类型_

控制器可配置为对每个低功耗蓝牙PHY（LE 1M、LE 2M 和LE Coded）的每种间距类型使用不同的值。

在任何情况下，间距参数的默认值都是 150 µs，间距参数的允许设置值范围是 0 至 10,000 µs。

在所有情况下，允许误差为 ±2 µs。

**8.2.2.2 帧间隔更新**

链路层规范定义了一个新过程，称为帧间隔更新 。通过使用该程序，设备可为某些或所有支持的 PHY 协商每个适用间隔类型的值。

中央设备或外围设备均可启动帧间隔更新 程序。这可通过在连接上发送 LL_FRAME_SPACE_REQ 来实现。作为回应，其他设备必须发送一个 LL_FRAME_SPACE_RSP PDU。

LL_FRAME_SPACE_REQ PDU 包括以下字段：

|**Field**|**Meaning**|
|---|---|
|FS_MIN|The minimum requested frame spacing in microseconds.|
|FS_MAX|The maximum requested frame spacing in microseconds.|
|PHYs|A single octet bit mask where bit 0 indicates the LE 1M PHY, bit 1 indicates the LE 2M PHY and bit 2 indicates the LE Coded PHY. One or more of these bits may be set to indicate the PHYs for which the frame spacing update is being requested.|
|Spacing Type|A 2-octet bit mask which indicates the spacing parameters for which new values are being requested. Bit 0 indicates T_IFS_ACL_CP, bit 1  indicates T_IFS_ACL_PC, bit 2 indicates T_IFS_END, bit 3 indicates T_IFS_CIS and bit 4 indicates T_MSS_CIS.|

响应设备应用蓝牙核心规范中的规则验证请求。如果请求有效并且可以满足，则返回一个 LL_FRAME_SPACE_RSP PDU，其中包含要使用的帧空间值。这将是设备能够支持的请求范围内的最低值。两个设备都采用新值，并将变化通知主机。

如果请求无法满足，则返回一个 LL_REJECT_EXT_IND PDU，错误代码设为 Unsupported功能或参数值，并且使用中的帧间距参数保持不变。

**8.2.2.3 Host控制器接口**

Host 控制器接口已更新，以支持新的帧间隔更新 程序。

该程序由Host向其控制器发送新的 HCI_LE_Frame_Space_Update 命令启动。该命令包含要求提供新帧空间值的间隔类型和时间范围，以及新值应适用的 PHY。

帧间隔更新完成后，将通过新的 LE帧间隔更新完成事件通知Host 。

图 30 显示了当帧间隔更新 程序启动时，Host和控制器之间以及设备之间发生的交互。

[![](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_30.png)](https://www.bluetooth.com/wp-content/uploads/2024/08/Bluetooth_Core_6_Figure_30.png)_图 30 - 帧间隔更新 HCI 和链路层交互_

## **9.结论**

蓝牙核心规范 6.0 版本延续了蓝牙技术定期更新、增加新功能和改进技术的趋势。

信道探测将为可靠和精确的距离测量提供一种基于标准的安全方法，许多类型的产品都将从中受益。

基于决策的广播过滤将提高使用蓝牙扩展广播进行无连接数据传输时的吞吐量和可靠性。

监测广播设备将对应用 开发人员非常有用，能够提供更好的用户界面和更好的用户体验。

对 ISOAL 所做的改进将有利于那些用户认为低延迟非常重要的音频应用。

LL 扩展功能集功能可为当今和未来最先进、功能的设备提供发现功能支持。

## **10.参考文献**

|Item|Location|
|---|---|
|Bluetooth Core Specification version 6.0|[https://www.bluetooth.com/specifications/specs/](https://www.bluetooth.com/specifications/specs/)|
|The Bluetooth LE Security Study Guide|[https://www.bluetooth.com/bluetooth-resources/le-security-study-guide/](https://www.bluetooth.com/zh-cn/bluetooth-resources/le-security-study-guide/)|
|Bluetooth® Channel Sounding Technical Overview paper|[https://www.bluetooth.com/channel-sounding-tech-overview/](https://www.bluetooth.com/zh-cn/channel-sounding-tech-overview/)|

**注释**

---

_[[个人仓库/谢承旭/1.理学类/170地科类/书籍总结/1]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftnref1)模式-0 将在 3.2.2.5.1 事件、子事件和步骤中解释。  
[[2]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftnref2)高斯移频键  
[[3]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftnref3)可连接的广播PDU是允许将连接请求作为响应的PDU  
[[4]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftnref4)低复杂度通信编解码器  
[[5]](https://www.bluetooth.com/zh-cn/core-specification-6-feature-overview/#_ftnref5)低复杂度通信编解码器 - 蓝牙使用的音频编解码器低功耗音频音频_