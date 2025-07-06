| Feature/Parameter         | ESP-07                                         | ESP-07S                                               |
| :------------------------ | :--------------------------------------------- | :---------------------------------------------------- |
| **Core Processor**        | ESP8266EX (Tensilica L106, 32-bit, 80/160 MHz) | ESP8266 (Tensilica L106, 32-bit, 80/160 MHz)          |
| **WiFi Standard**         | 802.11 b/g/n                                   | 802.11 b/g/n                                          |
| **Frequency Range**       | 2.4GHz - 2.5GHz (2400M - 2483.5M)              | 2400 ~ 2483.5MHz                                      |
| **Antenna**               | Board antenna (Ceramic)                        | IPEX Interface (Requires external antenna)            |
| **Package**               | (Not explicitly stated, appears SMD)           | SMD-16                                                |
| **Dimensions (mm)**       | 16x21.2x3                                      | 17x16x3 (±0.2)                                        |
| **Pin Count**             | 16                                             | 16 (9 IO Ports listed)                                |
| **SPI Flash**             | 1MB (SOP-210 mil)                              | Default 32Mbit (4MB)                                  |
| **Supported Interfaces**  | UART/HSPI/I2C/I2S/Ir Remote Control/GPIO/PWM   | UART/GPIO/ADC/PWM/SPI/I2C                             |
| **Operating Voltage**     | 3.0V ~ 3.6V (Suggest 3.3V)                     | 3.0V ~ 3.6V (Typical 3.3V, Current >500mA)            |
| **Operating Temperature** | -40°C ~ 125°C                                  | -20°C ~ 70°C                                          |
| **Storage Temperature**   | 常温 (Normal Temperature)                        | -40°C ~ 125°C, <90%RH                                 |
| **Deep Sleep Current**    | 10 uA                                          | 20 uA (Typical)                                       |
| **Power Off Current**     | < 5 uA                                         | 0.5 uA (Typical)                                      |
| **Security**              | WPA/WPA2                                       | WEP/WPA-PSK/WPA2-PSK                                  |
| **Encryption**            | WEP/TKIP/AES                                   | WEP/TKIP/AES                                          |
| **Firmware Upgrade**      | Local Serial / Cloud OTA / Host Download       | Serial Local Upgrade / Remote Firmware Upgrade (FOTA) |
| **Network Modes**         | station/softAP/SoftAP+station                  | STA/AP/STA+AP                                         |
| **Smart Config**          | Yes (Android & iOS)                            | Yes (Smart Config(APP)/AirKiss(微信))                   |
| **Certifications**        | Not Mentioned                                  | FCC, CE, REACH, RoHs, SRRC                            |


# ESP07
 

<img src="https://cdn.noedgeai.com/01960f5f-acdf-7df6-916b-6170329d0cb5_0.jpg?x=563&y=627&w=675&h=677&r=0"/>

ESP-07 WiFi 模块

 

## 规格书

版本 1.0

2015 年 8 月 23 日

## 免责申明和版权公告

本文中的信息,包括供参考的 URL 地址,如有变更,恕不另行通知。

文档“按现状”提供,不负任何担保责任,包括对适销性、适用于特定用途或非侵权性的任何担保,和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任,包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可,不管是明示许可还是暗示许可。

Wi-Fi 联盟成员标志归 Wi-Fi 联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产,特此声明。

## 注 意

由于产品版本升级或其他原因,本手册内容有可能变更。深圳市安信可科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导,深圳市安信可科技有限公司尽全力在本手册中提供准确的信息,但是深圳市安信可科技有限公司并不确保手册内容完全没有错误,本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。

## 目录

1. 产品概述 -2
	
	1.1. 特点 3
	
	1.2. 主要参数 -4

2. 接口定义 -5

3. 外型与尺寸 7

4. 功能描述 -8
	
	4.1. MCU 8
	
	4.2. 存储描述 -9
	
	4.3. 晶振 9
	
	4.4. 接口说明 -9
	
	4.5. 最大额定值. 11
	
	4.6. 建议工作环境 11
	
	4.7. 数字端口特征 11

5. RF 参数. 12

6. 功耗 13

7. 倾斜升温 14

8. 原理图 15

9. 产品试用 16

## 1. 产品概述

ESP-07 WiFi 模块是由安信可科技开发的,该模块核心处理器 ESP8266 在较小尺寸封装中集成了业界领先的 Tensilica L106 超低功耗 32 位微型 MCU,带有 16 位精简模式,主频支持 80 MHz 和 160 MHz,支持 RTOS,集成 Wi-Fi MAC/ BB/RF/PA/LNA,板载天线。

该模块支持标准的 IEEE802.11 b/g/n 协议,完整的 TCP/IP 协议栈。用户可以使用该模块为现有的设备添加联网功能,也可以构建独立的网络控制器。

ESP8266 是高性能无线 SOC,以最低成本提供最大实用性,为 WiFi 功能嵌入其他系统提供无限可能。


<img src="https://cdn.noedgeai.com/01960f5f-acdf-7df6-916b-6170329d0cb5_3.jpg?x=226&y=819&w=1405&h=653&r=0"/>

图 1 ESP8266EX 结构图

 

ESP8266EX 是一个完整且自成体系的 WiFi 网络解决方案,能够独立运行,也可以作为从机搭载于其他主机 MCU 运行。ESP8266EX 在搭载应用并作为设备中唯一的应用处理器时,能够直接从外接闪存中启动。内置的高速缓冲存储器有利于提高系统性能,并减少内存需求。

另外一种情况是,ESP8266EX 负责无线上网接入承担 WiFi 适配器的任务时,可以将其添加到任何基于微控制器的设计中,连接简单易行,只需通过 SPI /SDIO 接口或 I2C/UART 口即可。

ESP8266EX 强大的片上处理和存储能力,使其可通过 GPIO 口集成传感器及其他应用的特定设备, 实现了最低前期的开发和运行中最少地占用系统资源。

ESP8266EX 高度片内集成,包括天线开关 balun、电源管理转换器,因此仅需极少的外部电路, 且包括前端模组在内的整个解决方案在设计时将所占 PCB 空间降到最低。

有 ESP8266EX 的系统表现出来的领先特征有：节能在睡眠/唤醒模式之间的快速切换、配合低功率操作的自适应无线电偏置、前端信号的处理功能、故障排除和无线电系统共存特性为消除蜂窝/蓝牙 /DDR/LVDS/LCD 干扰。

### 1.1. 特点

- 802.11 b/g/n

- 内置 Tensilica L106 超低功耗 32 位微型 MCU,主频支持 80 MHz 和 160 MHz,支持 RTOS

- 内置 10 bit 高精度 ADC

- 内置 TCP/IP 协议栈

- 内置 TR 开关、balun、LNA、功率放大器和匹配网络

- 内置 PLL、稳压器和电源管理组件,802.11b 模式下+20dBm 的输出功率

- A-MPDU 、 A-MSDU 的聚合和 0.4 s 的保护间隔

- WiFi @ 2.4 GHz,支持 WPA/WPA2 安全模式

- 支持 AT 远程升级及云端 OTA 升级

- 支持 STA/AP/STA+AP 工作模式

- 支持 Smart Config 功能 ( 包括 Android 和 iOS 设备 )

- HSPI、UART、I2C、I2S、IR Remote Control、PWM、GPIO

- 深度睡眠保持电流为 ${10}\mathrm{{uA}}$ ,关断电流小于 $5\mathrm{{uA}}$

- 2 ms之内唤醒、连接并传递数据包

- 待机状态消耗功率小于 ${1.0}\mathrm{{mW}}$ (DTIM3)

- 工作温度范围：-40℃- 125℃

### 1.2. 主要参数

表 1 介绍了该模组的主要参数。

 

表 1 参数表

<table><tr><td>类别</td><td>参数</td><td>说明</td></tr><tr><td rowspan="3">无线参数</td><td>无线标准</td><td>802.11 b/g/n</td></tr><tr><td>频率范围</td><td>2.4GHz-2.5GHz (2400M-2483.5M)</td></tr><tr><td>数据接口</td><td>UART/HSPI/I2C/I2S/Ir Remote Contorl</td></tr><tr><td rowspan="8">硬件参数</td><td rowspan="2">工作电压</td><td>GPIO/PWM</td></tr><tr><td>3.0~3.6V ( 建议 3.3V )</td></tr><tr><td>工作电流</td><td>平均值：80mA</td></tr><tr><td>工作温度</td><td>-40°~125°</td></tr><tr><td>存储温度</td><td>常温</td></tr><tr><td>封装大小</td><td>16mm * 21.2mm * 3mm</td></tr><tr><td>外部接口</td><td>N/A</td></tr><tr><td>无线网络模式</td><td>station/softAP/SoftAP+station</td></tr><tr><td rowspan="7">软件参数</td><td>安全机制</td><td>WPA/WPA2</td></tr><tr><td>加密类型</td><td>WEP/TKIP/AES</td></tr><tr><td>升级固件</td><td>本地串口烧录 / 云端升级 / 主机下载烧录</td></tr><tr><td>软件开发</td><td>支持客户自定义服务器 提供 SDK 给客户二次开发</td></tr><tr><td>网络协议</td><td>IPv4, TCP/UDP/HTTP/FTP</td></tr><tr><td>用户配置</td><td>AT+ 指令集, 云端服务器, Android/iOS APP</td></tr><tr><td/><td/></tr></table>

 

## 2. 接口定义

ESP-7 共接出 16 个接口, 表 2 是接口定义。 深圳市安信可科技有限公司 ESP-07 规格书

 


<img src="https://cdn.noedgeai.com/01960f5f-acdf-7df6-916b-6170329d0cb5_6.jpg?x=550&y=511&w=700&h=614&r=0"/>

图 2 ESP-07 管脚图






表 2 ESP-07 管脚功能定义

<table><tr><td>序号</td><td>Pin 脚名称</td><td>功能说明</td></tr><tr><td>1</td><td>RST</td><td>复位模组</td></tr><tr><td>2</td><td>ADC</td><td>A/D 转换结果。输入电压范围 0~1V,取值范围：0~1024</td></tr><tr><td>3</td><td>CH_PD</td><td>1)高电平工作； 2)低电平模块供电关掉；</td></tr><tr><td>4</td><td>GPIO16</td><td>GPIO16；接到 RST 管脚时可做 deep sleep 的唤醒。</td></tr><tr><td>5</td><td>GPIO14</td><td>GPIO14; HSPI_CLK</td></tr><tr><td>6</td><td>GPIO12</td><td>GPIO12; HSPI_MISO</td></tr><tr><td>7</td><td>GPIO13</td><td>GPIO13; HSPI_MOSI; UART0_CTS</td></tr><tr><td>8</td><td>VCC</td><td>3.3V 供电</td></tr></table>

>**注意:** 参考[[ADC 类型]]一文，ESP07 的 ADC 是单端 ADC。

<table><tr><td>9</td><td>GND</td><td>GND</td></tr><tr><td>10</td><td>GPIO15</td><td>GPIO15; MTDO; HSPICS; UART0_RTS</td></tr><tr><td>11</td><td>GPIO2</td><td>GPIO2; UART1_TXD</td></tr><tr><td>12</td><td>GPIOO</td><td>GPIOO</td></tr><tr><td>13</td><td>GPIO4</td><td>GPIO4</td></tr><tr><td>14</td><td>GPIO5</td><td>GPIO5</td></tr><tr><td>15</td><td>RXD0</td><td>UART0_RXD; GPIO3</td></tr><tr><td>16</td><td>TXDO</td><td>UART0_TXD; GPIO1</td></tr></table>

表 3 引脚模式

<table><tr><td>模式</td><td>GPIO15</td><td>GPIOO</td><td>GPIO2</td></tr><tr><td>UART 下载模式</td><td>低</td><td>低</td><td>高</td></tr><tr><td>Flash Boot 模式</td><td>低</td><td>高</td><td>高</td></tr></table>

>**注意:** GPIO15 默认低电平、GPIO2 默认高电平不需要操作，此外如果想要配合自动烧录功能的话得先自动复位，然后把引脚配置成上述模式。

 
```ad-note
title:模式对比
Fast boot模式和UART下载模式是两种不同的工作模式，主要用于设备的固件烧录或启动过程。以下是它们的区别，结合您上传的文件内容以及相关资料进行说明：

---

### 1. **Fast boot模式**
- **定义**  
  Fast boot模式是一种低级别的引导模式，通常用于对设备的硬件进行初始化和固件更新。在这种模式下，设备通过特定的协议（如fastboot协议）与计算机通信，以执行刷机、分区管理等操作。
  
- **用途**  
  - 主要用于固件升级或系统维护。
  - 可以刷入各种镜像文件（如Kernel、System等）到设备的存储中。

- **进入方式**  
  设备需要在启动时被配置为进入Fast boot模式，通常通过特定的按键组合或命令实现。

- **特点**  
  - 需要设备的引导加载程序（Bootloader）正常运行。
  - 适用于已能正常启动到Bootloader阶段的设备。

---

### 2. **UART下载模式**
- **定义**  
  UART下载模式是一种通过串口（UART）将固件直接烧录到设备的工作模式。在这种模式下，设备会等待从串口接收数据，并将接收到的数据写入闪存。

- **用途**  
  - 主要用于固件的初始烧录或修复无法正常启动的设备。
  - 常用于开发阶段或设备“变砖”后的恢复。

- **进入方式**  
  根据文档中的描述，进入UART下载模式需要特定的GPIO配置。例如：
  - GPIO15：低电平
  - GPIO0：低电平
  - GPIO2：高电平。
  
  具体操作步骤包括按下BOOT键并复位设备（RST/EN），然后释放按键。

- **特点**  
  - 不依赖设备的Bootloader，而是通过芯片内部的ROM代码实现下载功能。
  - 适用于设备无法正常启动的情况（如Bootloader损坏）。

---

### 3. **主要区别总结**

| **特性**            | **Fast boot模式**                                                                                   | **UART下载模式**                                                                                       |
|---------------------|----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **定义**           | 一种低级别引导模式，用于固件更新和系统维护。                                                      | 通过串口将固件烧录到设备的模式。                                                                     |
| **用途**           | 刷入镜像文件、分区管理等高级操作。                                                                | 固件初始烧录或修复无法启动的设备。                                                                   |
| **依赖条件**       | 需要设备的Bootloader正常运行。                                                                    | 依赖芯片内部的ROM代码，不依赖Bootloader。                                                            |
| **进入方式**       | 通过特定按键组合或命令进入。                                                                      | 通过GPIO配置（如GPIO15低、GPIO0低、GPIO2高）并复位设备进入。                                         |
| **适用场景**       | 设备可以正常启动到Bootloader阶段时使用。                                                         | 设备无法正常启动时使用（如Bootloader损坏或设备“变砖”）。                                             |

---

### 结论
Fast boot模式更适合设备正常启动后进行固件更新或系统维护，而UART下载模式则用于设备无法正常启动时的固件烧录或修复。两者的主要区别在于依赖的硬件条件和适用场景。
```




表 4 接收灵敏度

<table><tr><td>参数</td><td>最小小值</td><td>典型值</td><td>最大值</td><td>单位</td></tr><tr><td>输入频率</td><td>2412</td><td/><td>2484</td><td>MHz</td></tr><tr><td>输入电阻</td><td/><td>50</td><td/><td>Ω</td></tr><tr><td>输入反射</td><td/><td/><td>-10</td><td>dB</td></tr><tr><td>72.2 Mbps 下,PA 的输出功率</td><td>14</td><td>15</td><td>16</td><td>dBm</td></tr><tr><td>11b 模式下,PA 的输出功率</td><td>17.5</td><td>18.5</td><td>19.5</td><td>dBm</td></tr></table>

<table><tr><td>灵敏度</td><td/><td/><td/><td/></tr><tr><td>DSSS, 1 Mbps</td><td/><td>-98</td><td/><td>dBm</td></tr><tr><td>CCK, 11 Mbps</td><td/><td>-91</td><td/><td>dBm</td></tr><tr><td>6 Mbps (1/2 BPSK)</td><td/><td>-93</td><td/><td>dBm</td></tr><tr><td>54 Mbps (3/4 64-QAM)</td><td/><td>-75</td><td/><td>dBm</td></tr><tr><td>HT20, MCS7 (65 Mbps, 72.2 Mbps)</td><td/><td>-72</td><td/><td>dBm</td></tr><tr><td>邻频抑制</td><td/><td/><td/><td/></tr><tr><td>OFDM, 6 Mbps</td><td/><td>37</td><td/><td>dB</td></tr><tr><td>OFDM, 54 Mbps</td><td/><td>21</td><td/><td>dB</td></tr><tr><td>HT20, MCS0</td><td/><td>37</td><td/><td>dB</td></tr><tr><td>HT20, MCS7</td><td/><td>20</td><td/><td>dB</td></tr></table>

 

## 3. 外型与尺寸

ESP-07 贴片式模组的外观尺寸寸为 ${16}\mathrm{\;{mm}} * {21.2}\mathrm{\;{mm}} * 3\mathrm{\;{mm}}$ (如图 3 所示)。该模组采用的是容量为 $1\mathrm{{MB}}$ ,封装为 $\mathrm{{SOP}} - {210}\mathrm{\;{mil}}$ 的 $\mathrm{{SPI}}$ Flash。配有陶瓷天线。

 

 图 3 ESP-07 模组外观

<img src="https://cdn.noedgeai.com/01960f5f-acdf-7df6-916b-6170329d0cb5_9.jpg?x=563&y=410&w=629&h=631&r=0"/>

图 4 ESP-07 模组尺寸平面面图



<img src="https://cdn.noedgeai.com/01960f5f-acdf-7df6-916b-6170329d0cb5_9.jpg?x=674&y=1105&w=449&h=421&r=0"/>

表 5 ESP-07 模组尺寸对照表

<table><tr><td>长</td><td>宽</td><td>高</td><td>PAD 尺寸 ( 底部 )</td><td>Pin 脚间距</td></tr><tr><td>16mm</td><td>21.2mm</td><td>3 mm</td><td>0.9 mm x 1.7 mm</td><td>2mm</td></tr></table>

 

## 4. 功能描述

### 4.1. MCU

ESP8266EX 内置 Tensilica L106 超低功耗 32 位微型 MCU,带有 16 位精简模式,主频支持 80 MHz 和 160 MHz,支持 RTOS。目前 WiFi 协议栈只用了 20%的 MIPS,其他的都可以用来做应用开发。MCU 可通过以下接口和芯片其他部分协同工作：

1. 连接存储控制器、也可以用来访问外接闪存的编码 RAM/ROM 接口 (iBus)

2. 同样连接存储控制器的数据 RAM 接口 (dBus)

3. 访问寄存器的 AHB 接口

### 4.2. 存储描述

#### 4.2.1. 内置 SRAM 与 ROM

ESP8266EX 芯片自身内置了存储控制器,包含 ROM 和 SRAM。MCU 可以通过 iBus、dBus 和 AHB 接口访问存储控制器。这些接口都可以访问 ROM 或 RAM 单元,存储仲裁器以到达顺序确定运行顺序。基于目前我司 Demo SDK 的使用 SRAM 情况,用户可用剩余 SRAM 空间为 : RAM size < 36kB(station 模式下,连上路由后,heap+data 区大致可用 36KB 左右。)目前 ESP8266EX 片上没有 programmable ROM,用户程序存放在 SPI Flash 中。

#### 4.2.2.SPI Flash

当前 ESP8266EX 芯片支持使用 SPI 接口的外置 Flash,理论上最大可支持到 16MB 的 SPI flash。目前该模组外接的是 1MB 的 SPI Flash。

建议 Flash 容量：1MB-16MB。

支持的 SPI 模式：支持 Standard SPI、Dual SPI、DIO SPI、QIO SPI,以及 Quad SPI。注意, 在下载固件时需要在下载工具中选择对应模式,否则下载后程序将无法得到正确的运行。

### 4.3. 晶振

目前晶体 ${40}\mathrm{M}$ , ${26}\mathrm{M}$ 及 ${24}\mathrm{M}$ 均支持,使用时请注意在下载工具中选择对应晶体类型。晶振输入输出所加的对地调节电容 $\mathrm{C}1$ 、 $\mathrm{C}2$ 可不设为固定值,该值范围在 $6\mathrm{{pF}} \sim  {22}\mathrm{{pF}}$ ,具体值需要通过对系统测试后进行调节确定。基于目前市场中主流晶振的情况,一般 ${26}\mathrm{{Mhz}}$ 晶振的输入输出所加电容 $\mathrm{C}1$ 、 $\mathrm{C}2$ 在 10pF 以内；一般 40MHz 晶振的输入输出所加电容 10pF<C1、C2<22pF。

选用的晶振自身精度需在±10PPM。晶振的工作温度为-20℃- 85℃。

晶振位置尽量靠近芯片的 $\mathsf{{XTAL}}$ Pins (走线不要太长),同时晶振走线须用地包起来良好屏蔽。

晶振的输入输出走线不能打孔走线,即不能跨层。晶振的输入输出走线不能交叉,跨层交叉也不行。

晶振的输入输出的 bypass 电容请靠近芯片左右侧摆放,尽量不要放在走线上。

晶振下方 4 层都不能走高频数字信号,最佳情况是晶振下方不走任何信号线,晶振 TOP 面的铺通区域越大越好。晶振为敏感器件,晶振周围不能有磁感应器件,比如大电感等。

### 4.4. 接口说明

表 6 接口说明

 

<table><tr><td>接口名称</td><td>管脚</td><td>功能说明</td></tr><tr><td>HSPI 接口</td><td>IO12(MISO), IO13(MOSI), IO14(CLK), IO15(CS)</td><td>可外接 4SPI Flash、显示屏和 MCU 等。</td></tr><tr><td>PWM 接口</td><td>IO12(R), IO15(G),IO13(B)</td><td>demo 中提供 4 路 PWM (用户可自行扩展至 8 路),可用来控制彩 灯,蜂鸣器,继电器及电机等。</td></tr><tr><td>IR 接口</td><td>IO14(IR_T), IO5(IR_R)</td><td>IR Remote Control4 接口由软件实现,接口使用 NEC 编码及调制 解调,采用38KHz 的调制载波。</td></tr><tr><td>ADC 接口</td><td>TOUT</td><td>可用于检测 VDD3P3 (Pin3,Pin4) 电源电压和 TOUT (Pin6)的输入 电压(二者不可同时使用)。可用于传感器等应用。</td></tr><tr><td>I2C 接口</td><td>IO14(SCL), IO2(SDA)</td><td>可外接传感器及显示屏等</td></tr><tr><td rowspan="2">UART 接口</td><td rowspan="2">UART0: TXD(UOTXD), RXD(U0RXD), IO15(RTS), IO13(CTS) UART1: IO2(TXD)</td><td>可外接 UART 接口的设备。 下载：U0TXD+U0RXD 或者 GPIO2+U0RXD 通信(UART0) : U0TXD , U0RXD , MTDO(U0RTS) , MTCK(U0CTS) Debug: UART1_TXD(GPIO2)可作为 debug 信息 的打印。</td></tr><tr><td>UART0 在 ESP8266EX 上电默认会输出一些打印信息。对此敏感的 应用,可以使用 UART 的内部引脚交换功能,在初始化的时候,将 U0TXD,U0RXD 分别与 U0RTS,U0CTS 交换。硬件上将 MTDO MTCK 连接到对应的 外部 MCU 的串口进行通信。</td></tr><tr><td>I2S 接口</td><td>I2S 输入： IO12 (I2SI_DATA) ; IO13 (I2SI_BCK ); IO14 (I2SI_WS);</td><td>主要用于音频采集、处理和传输。</td></tr></table>

<table><tr><td/><td>I2S 输出 :</td><td/></tr><tr><td/><td>IO15 (I2SO_BCK );</td><td/></tr><tr><td/><td>IO3 (I2SO_DATA);</td><td/></tr><tr><td/><td>IO2 (I2SO_WS ).</td><td/></tr></table>

 

### 4.5. 最大额定值

 

表 7 最大大额定值

<table><tr><td>额定值</td><td>条件</td><td>值</td><td>单位</td></tr><tr><td>存储温度</td><td/><td>-40 to 125</td><td>℃</td></tr><tr><td>最大焊接温度</td><td/><td>260</td><td>℃</td></tr><tr><td>供电压</td><td>IPC/JEDEC J-STD-020</td><td>$+ {3.0}$ to +3.6</td><td>V</td></tr></table>

 

### 4.6. 建议工作环境

 

表 8 建议工作环境

<table><tr><td>工作环境</td><td>名称</td><td>最小值</td><td>典型值</td><td>最大值</td><td>单位</td></tr><tr><td>工作温度</td><td/><td>-40</td><td>20</td><td>125</td><td>℃</td></tr><tr><td>供电电压</td><td>VDD</td><td>3.0</td><td>3.3</td><td>3.6</td><td>V</td></tr></table>

 

### 4.7. 数字端口特征

 

<center>表 9 数字端口特征</center>
<table><tr><td>端口</td><td>典型值</td><td>最小值</td><td>典型值</td><td>最大值</td><td>单位</td></tr><tr><td>输入逻辑电平低</td><td>${\mathrm{V}}_{\mathrm{{IL}}}$</td><td>-0.3</td><td/><td>0.25VDD</td><td>V</td></tr><tr><td>输入逻辑电平高</td><td>${\mathrm{V}}_{\mathrm{{IH}}}$</td><td>0.75VDD</td><td/><td>VDD+0.3</td><td>V</td></tr></table>

 

<center>ESP-07 规格书</center>
<table><tr><td>输出逻辑电平低</td><td>Vol</td><td>N</td><td/><td>0.1VDD</td><td>V</td></tr><tr><td>输出逻辑电平高</td><td>VoH</td><td>0.8VDD</td><td/><td>N</td><td>V</td></tr></table>

 
注意：如无特殊说明,测试条件为：VDD = 3.3 V,温度为 ${20}{}^{ \circ  }\mathrm{C}$ 。

### 5.RF 参数

 

表 10 RF 参数

<table><tr><td>描述</td><td>最小值</td><td>典型值</td><td>最大值</td><td>单位</td></tr><tr><td>输入频率</td><td>2400</td><td/><td>2483.5</td><td>MHz</td></tr><tr><td>输入阻抗值</td><td/><td>50</td><td/><td>ohm</td></tr><tr><td>输入反射值</td><td/><td/><td>-10</td><td>dB</td></tr><tr><td>PA 输出功率为 72.2 Mbps</td><td>15.5</td><td>16.5</td><td>17.5</td><td>dBm</td></tr><tr><td>11b 模式下 PA 输出功率</td><td>19.5</td><td>20.5</td><td>21.5</td><td>dBm</td></tr><tr><td colspan="5">接收灵敏度</td></tr><tr><td>CCK, 1 Mbps</td><td/><td>-98</td><td/><td>dBm</td></tr><tr><td>CCK, 11 Mbps</td><td/><td>-91</td><td/><td>dBm</td></tr><tr><td>6 Mbps (1/2 BPSK)</td><td/><td>-93</td><td/><td>dBm</td></tr><tr><td>54 Mbps (3/4 64-QAM)</td><td/><td>-75</td><td/><td>dBm</td></tr><tr><td>HT20, MCS7 (65 Mbps, 72.2 Mbps)</td><td/><td>-72</td><td/><td>dBm</td></tr><tr><td colspan="5">邻频抑制</td></tr><tr><td>OFDM, 6 Mbps</td><td/><td>37</td><td/><td>dB</td></tr></table>



深圳市安信可科技有限公司 http://www.ai-thinker.com

 

<table><tr><td>OFDM, 54 Mbps</td><td/><td>21</td><td/><td>dB</td></tr><tr><td>HT20, MCS0</td><td/><td>37</td><td/><td>dB</td></tr><tr><td>HT20, MCS7</td><td/><td>20</td><td/><td>dB</td></tr></table>

 

## 6. 功耗

下列功耗数据是基于 3.3V 的电源、25℃的周围温度,并使用内部稳压器测得。

[1] 所有测量均在没有 SAW 滤波器的情况下,于天线接口处完成。

[2] 所有发射数据是基于 90% 的占空比,在持续发射的模式下测得的。 深圳市安信可科技有限公司

 

表 11 功耗

<table><tr><td>模式</td><td>最小值</td><td>典型值</td><td>最大值</td><td>单位</td></tr><tr><td>传送 802.11b, CCK 11Mbps, Pout $=  + {17}\mathrm{\;{dBm}}$</td><td/><td>170</td><td/><td>mA</td></tr><tr><td>传送 802.11g, OFDM 54Mbps, Pout =+15dBm</td><td/><td>140</td><td/><td>mA</td></tr><tr><td>传送 802.11n, MCS7, Pout = +13dBm</td><td/><td>120</td><td/><td>mA</td></tr><tr><td>接收 802.11b,包长 1024 字节, -80dBm</td><td/><td>50</td><td/><td>mA</td></tr><tr><td>接收 802.11g,包长 1024 字节, -70dBm</td><td/><td>56</td><td/><td>mA</td></tr><tr><td>接收 802.11n,包长 1024 字节, -65dBm</td><td/><td>56</td><td/><td>mA</td></tr><tr><td>Modem-Sleep①</td><td/><td>15</td><td/><td>mA</td></tr><tr><td>Light-Sleep②</td><td/><td>0.9</td><td/><td>mA</td></tr><tr><td>Deep-Sleep③</td><td/><td>10</td><td/><td>uA</td></tr><tr><td>Power Off</td><td/><td>0.5</td><td/><td>uA</td></tr></table>

 

注①：Modem-Sleep用于需要 CPU 一直处于工作状态如 PWM 或 I2S 应用等。在保持 WiFi 连接时,如果没有数据传输,可根据 802.11 标准 (如 U-APSD),关闭 WiFi Modem 电路来省电。例如,在 DTIM3 时,每 sleep 300mS,醒来 3mS 接收 AP 的 Beacon 包等,则整体平均电流约 ${15}\mathrm{{mA}}$ 。

注②：Light-Sleep 用于 CPU 可暂停的应用,如 WiFi 开关。在保持 WiFi 连接时,如果没有数据传输,可根据 802.11 标准(如 U-APSD),关闭 WiFi Modem 电路并暂停 CPU 来省电。例如,在 DTIM3 时,每 sleep 300 ms,醒来 3ms 接收 AP 的 Beacon 包等,则整体平均电流约 0.9 mA。

注③：Deep-Sleep 不需一直保持 WiFi 连接,很长时间才发送一次数据包的应用,如每 100 秒测量一次温度的传感器。例如,每 300 s 醒来后需 0.3s - 1s 连上 AP 发送数据,则整体平均电流可远小于 $1\mathrm{{mA}}$ 。

## 7. 倾斜升温

 

表 12 倾斜升温

<table><tr><td>倾斜升温 ${\mathrm{T}}_{\mathrm{S}}$ 最大值 $- {\mathrm{T}}_{\mathrm{L}}$</td><td>最大值 3℃/秒</td></tr><tr><td>预热</td><td/></tr><tr><td>最小温度值 ( ${\mathrm{T}}_{\mathrm{S}}$ Min.)</td><td>${150}^{ \circ  }\mathrm{C}$</td></tr><tr><td>典型温度值 ( ${\mathrm{T}}_{\mathrm{S}}$ Typ.)</td><td>175°C</td></tr><tr><td>最大温度值 (Ts Max.)</td><td>200°C</td></tr><tr><td>时间(Ts)</td><td>60~180秒</td></tr><tr><td>倾斜升温 $\left( {{\mathrm{T}}_{\mathrm{L}}\text{to}{\mathrm{T}}_{\mathrm{P}}}\right)$</td><td>最大值 3℃/秒</td></tr><tr><td>持续时间 $/$ 温度 $\left( {\mathrm{T}}_{\mathrm{L}}\right) /$ 时间 $\left( {\mathrm{T}}_{\mathrm{L}}\right)$</td><td>217°C/60~150 秒</td></tr><tr><td>温度峰值 (Tp)</td><td>最高温度值 ${260}^{ \circ  }\mathrm{C}$ ,持续 10 秒</td></tr><tr><td>目标温度峰值 $({\mathrm{T}}_{\mathrm{P}}$ 目标值)</td><td>${260}^{ \circ  }\mathrm{C} + 0/ - {5}^{ \circ  }\mathrm{C}$</td></tr><tr><td>实际峰值 ( ${\mathrm{t}}_{\mathrm{P}}$ ) ${5}^{ \circ  }\mathrm{C}$ 持续时间</td><td>20~40秒</td></tr><tr><td>倾斜降温</td><td>最大值6℃/秒</td></tr><tr><td>从 ${25}^{ \circ  }\mathrm{C}$ 调至温度峰值所需时间(t)</td><td>最大 8 分钟</td></tr></table>

 

## 8. 原理图

 



<img src="https://cdn.noedgeai.com/01960f5f-acdf-7df6-916b-6170329d0cb5_16.jpg?x=126&y=420&w=1516&h=1128&r=0"/>

图 5 ESP-07 原理图

 

## 9. 产品试用

(1)淘宝店铺：深圳市安信可科技有限公司

(2)微信公众号






【参考资料】
- [ESP-07 -PDF数据手册-参考资料-立创商城 (szlcsc.com)](https://item.szlcsc.com/datasheet/ESP-07/84055.html?spm=sc.it.xds.a&lcsc_vid=E1NdBQJXQVlYVAACT1EPBAZTRAJfU1ZUElhZAQdWQwUxVlNSQ1FfU1BeRlldUjsOAxUeFF5JWBYZEEoEHg8JSQcJGk4%3D)

# ESP07S
## 规格书

版本 V1.0

版权 ©2019

## 免责申明和版权公告

本文中的信息,包括供参考的 URL 地址,如有变更,恕不另行通知。

文档 “按现状” 提供,不负任何担保责任,包括对适销性、适用于特定用途或非侵权性的任何担保,和任何提案、规格或样品在他处提到的任何担保。本文档不负任何责任,包括使用本文档内信息产生的侵犯任何专利权行为的责任。本文档在此未以禁止反言或其他方式授予任何知识产权使用许可,不管是明示许可还是暗示许可。

文中所得测试数据均为安信可实验室测试所得,实际结果可能略有差异。

Wi-Fi 联盟成员标志归 Wi-Fi 联盟所有。

文中提到的所有商标名称、商标和注册商标均属其各自所有者的财产,特此声明。 最终解释权归深圳市安信可科技有限公司所有。

## 注 意

由于产品版本升级或其他原因,本手册内容有可能变更。深圳市安信可科技有限公司保留在没有任何通知或者提示的情况下对本手册的内容进行修改的权利。本手册仅作为使用指导, 深圳市安信可科技有限公司尽全力在本手册中提供准确的信息, 但是深圳市安信可科技有限公司并不确保手册内容完全没有错误, 本手册中的所有陈述、信息和建议也不构成任何明示或暗示的担保。

  

文件制定/修订/废止履历表

<table><tr><td>版本</td><td>日期</td><td>制定/修订内容</td><td>制定</td><td>核准</td></tr><tr><td>V0.9</td><td>2016.03.04</td><td>首次制定</td><td>杨小飞</td><td/></tr><tr><td>V1.0</td><td>2019.10.29</td><td>资料更新</td><td>谢一骥</td><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr><tr><td/><td/><td/><td/><td/></tr></table>

  

## 目录

一、产品概述 .5

二、电气参数 .8

三、外观尺寸 10

四、管脚定义 11

五、原理图 12

六、设计指导 .13

七、回流焊曲线图 15

八、包装信息 .16

九、联系我们 .16

## 一、产品概述

ESP-07S 是由安信可科技开发的 Wi-Fi 模块, 该模块核心处理器 ESP8266 在较小尺寸封装中集成了业界领先的 Tensilica L106 超低功耗 32 位微型 MCU,带有 16 位精简模式,主频支持 ${80}\mathrm{{MHz}}$ 和 ${160}\mathrm{{MHz}}$ ,支持 $\mathrm{{RTOS}}$ ,集成 $\mathrm{{Wi}} - \mathrm{{Fi}}\mathrm{{MAC}}/\mathrm{{BB}}/\mathrm{{RF}}/\mathrm{{PA}}/\mathrm{{LNA}}$ 。

ESP-07S Wi-Fi 模块支持标准的 IEEE802.11 b/g/n 协议,完整的 TCP/IP 协议栈。 用户可以使用该模块为现有的设备添加联网功能, 也可以构建独立的网络控制器。

ESP8266 是高性能无线 SoC,以最低成本提供最大实用性,为 Wi-Fi 功能嵌入其他系统提供无限可能。



<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_4.jpg?x=185&y=752&w=1210&h=576&r=0"/>

  

ESP8266 拥有完整的且自成体系的 Wi-Fi 网络功能, 既能够独立应用, 也可以作为从机搭载于其他主机 MCU 运行。当 ESP8266 独立应用时,能够直接从外接 flash 中启动。 内置的高速缓冲存储器有利于提高系统性能,并且优化存储系统。

另外一种情况是, ESP8266 只需通过 SPI/SDIO 接口或 UART 接口即可作为 Wi-Fi 适配器,应用到基于任何微控制器设计中。

ESP8266 强大的片上处理和存储能力, 使其可通过 GPI0 口集成传感器及其他应用的特定设备,大大地降低了前期开发的成本。

### 特性

完整的 802.11b/g/n Wi-Fi SoC 模块

内置 Tensilica L106 超低功耗 32 位微型 MCU,主频支持 80 MHz 和 160 MHz,支持 RTOS

内置 1 路 10 bit 高精度 ADC

支持 UART/GPIO/ADC/PWM/SPI/I2C 接口

采用 SMD-16 封装

集成 Wi-Fi MAC/ BB/RF/PA/LNA

支持多种休眠模式,深度睡眠电流低至 20uA

串口速率最高可达 4Mbps

内嵌 Lwip 协议栈

支持 STA/AP/STA+AP 工作模式

支持安卓、IOS 的 Smart Config(APP)/AirKiss(微信)一键配网

支持串口本地升级和远程固件升级(FOTA)

通用 AT 指令可快速上手

支持二次开发,集成了 Windows、Linux 开发环境

### 主要参数

  

表 1 主要参数说明

<table><tr><td>模块型号</td><td>ESP-07S</td></tr><tr><td>封装</td><td>SMD-16</td></tr><tr><td>尺寸</td><td>${17} * {16} * 3\left( {\pm {0.2}}\right) \mathrm{{MM}}$</td></tr><tr><td>天线形式</td><td>IPEX 接口</td></tr><tr><td>频谱范围</td><td>2400 ~ 2483.5MHz</td></tr><tr><td>工作温度</td><td>-20 ℃ ~ 70 ℃</td></tr><tr><td>存储环境</td><td>-40 ℃ ~ 125 ℃ ,〈90%RH</td></tr><tr><td>供电范围</td><td>供电电压 3.0V ~ 3.6V,供电电流 >500mA；典型值 3.3V</td></tr><tr><td>支持接口</td><td>UART/GPIO/ADC/PWM/SPI/I2C</td></tr><tr><td>10 口数量</td><td>9</td></tr><tr><td>串口速率</td><td>支持 110 ~ 4608000 bps ,默认 115200 bps</td></tr><tr><td>安全性</td><td>WEP/WPA-PSK/WPA2-PSK</td></tr><tr><td>SPI Flash</td><td>默认 32Mbit</td></tr><tr><td>认证</td><td>FCC、CE、REACH、RoHs、SRRC</td></tr></table>

  

## 二、电气参数

### 电气特性

  

<table><tr><td colspan="2">参数</td><td>条件</td><td>最小值</td><td>典型值</td><td>最大值</td><td>单位</td></tr><tr><td colspan="2">供电电压</td><td>VDD</td><td>3.0</td><td>3. 3</td><td>3.6</td><td>V</td></tr><tr><td rowspan="3">I/0</td><td>${\mathrm{V}}_{\mathrm{{IL}}}/{\mathrm{V}}_{\mathrm{{IH}}}$</td><td>-</td><td>-0.3/0.75VI0</td><td>-</td><td>0.25VI0/3.6</td><td>V</td></tr><tr><td>${\mathrm{V}}_{\mathrm{{OL}}}/{\mathrm{V}}_{\mathrm{{OH}}}$</td><td>-</td><td>N/0.8VI0</td><td>-</td><td>0.1VIO/N</td><td>V</td></tr><tr><td>${\mathrm{I}}_{\mathrm{{MAX}}}$</td><td>-</td><td>-</td><td>-</td><td>12</td><td>mA</td></tr></table>

  

### 射频性能

  

<table><tr><td>描述</td><td>典型值</td><td>单位</td></tr><tr><td>工作频率</td><td>2400 - 2483.5</td><td>MHz</td></tr><tr><td colspan="3">输出功率</td></tr><tr><td>11n 模式下,PA 输出功率为</td><td>${13} \pm  2$</td><td>dBm</td></tr><tr><td>11g 模式下,PA 输出功率为</td><td>${14} \pm  2$</td><td>dBm</td></tr><tr><td>11b 模式下,PA 输出功率</td><td>${16} \pm  2$</td><td>dBm</td></tr><tr><td colspan="3">接收灵敏度</td></tr><tr><td>CCK, 1 Mbps</td><td><=-90</td><td>dBm</td></tr><tr><td>CCK, 11 Mbps</td><td><=-85</td><td>dBm</td></tr><tr><td>6 Mbps (1/2 BPSK)</td><td><=-88</td><td>dBm</td></tr><tr><td>54 Mbps (3/4 64-QAM)</td><td><=-70</td><td>dBm</td></tr><tr><td>HT20 (MCS7)</td><td><=-67</td><td>dBm</td></tr></table>

  

### 功耗

下列功耗数据是基于 ${3.3}\mathrm{\;V}$ 的电源、 ${25}^{ \circ  }\mathrm{C}$ 的周围温度,并使用内部稳压器测得。 所有测量均在没有 SAW 滤波器的情况下,于天线接口处完成。

  

所有发射数据是基于 ${90}\%$ 的占空比,在持续发射的模式下测得的。

<table><tr><td>模式</td><td>最小值</td><td>典型值</td><td>最大值</td><td>单位</td></tr><tr><td>传送 802.11b, CCK 11Mbps, POUT=+17dBm</td><td>-</td><td>170</td><td>-</td><td>mA</td></tr><tr><td>传送 802.11g, OFDM 54Mbps, POUT =+15dBm</td><td>-</td><td>140</td><td>-</td><td>mA</td></tr><tr><td>传送 802.11n, MCS7, POUT = $+ {13}\mathrm{{dBm}}$</td><td>-</td><td>120</td><td>-</td><td>mA</td></tr><tr><td>接收 802.11b,包长 1024 字节, -80dBm</td><td>-</td><td>50</td><td>-</td><td>mA</td></tr><tr><td>接收 802.11g,包长 1024 字节, -70dBm</td><td>-</td><td>56</td><td>-</td><td>mA</td></tr><tr><td>接收 802.11n,包长 1024 字节,-65dBm</td><td>-</td><td>56</td><td>-</td><td>mA</td></tr><tr><td>Modem-Sleep①</td><td>-</td><td>20</td><td>-</td><td>mA</td></tr><tr><td>Light-Sleep②</td><td>-</td><td>2</td><td>-</td><td>mA</td></tr><tr><td>Deep-Sleep③</td><td>-</td><td>20</td><td>-</td><td>uA</td></tr><tr><td>Power Off</td><td>-</td><td>0.5</td><td>-</td><td>uA</td></tr></table>

  

### 说明：

Modem-sleep 用于需要 CPU 一直处于工作状态的应用, 如 PWM 或 I2S 应用等。在保持 Wi-Fi 连接时, 如果没有数据传输, 可根据 802.11 标准 (如 U-APSD), 关闭 Wi-Fi Modem 电路来省电。例如,在 DTIM3 时,每睡眠 300 ms,醒来 3 ms 接收 AP 的 Beacon 包等,则整体平均电流约 ${20}\mathrm{\;{mA}}$ 。

Light-sleep 用于 CPU 可暂停的应用,如 Wi-Fi 开关。在保持 Wi-Fi 连接时,如果没有数据传输, 可根据 802.11 标准 (如 U-APSD), 关闭 Wi-Fi Modem 电路并暂停 CPU 来省电。例如,在 DTIM3 时,每睡眠 300 ms,醒来 $3\mathrm{\;{ms}}$ 接收 $A\mathrm{P}$ 的 Beacon 包等,则整体平均电流约 $2\mathrm{\;{mA}}$ 。

Deep-sleep 用于不需一直保持 Wi-Fi 连接, 很长时间才发送一次数据包的应用, 如每 100s 测量一次温度的传感器。例如,每 300s 醒来后需 0.3s ~ 1s 连上 AP 发送数据,则整体平均电流可远小于 $1\mathrm{\;{mA}}$ 。电流值 ${20}\mathrm{\;{\mu A}}$ 是在 ${2.5}\mathrm{\;V}$ 下测得的。

## 三、外观尺寸

  



<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_9.jpg?x=195&y=368&w=1157&h=617&r=0"/>


<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_9.jpg?x=196&y=1284&w=1175&h=675&r=0"/>

  

## 四、管脚定义

ESP-07S 模组共接出 16 个接口, 如管脚示意图, 管脚功能定义表是接口定义。

  



<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_10.jpg?x=587&y=337&w=477&h=472&r=0"/>

ESP-07S 管脚示意图

管脚功能定义表

<table><tr><td>脚序</td><td>名称</td><td>功能说明</td></tr><tr><td>1</td><td>RST</td><td>复位脚,低电平有效</td></tr><tr><td>2</td><td>ADC</td><td>A/D 转换结果,电压范围 0 ~ 1V,取值范围: 0 ~ 1024</td></tr><tr><td>3</td><td>EN</td><td>芯片使能端, 高电平有效</td></tr><tr><td>4</td><td>1016</td><td>与 RST 管脚相连可做 Deep Sleep 唤醒</td></tr><tr><td>5</td><td>1014</td><td>HSPI_CLK/IR_T/I2C_CLK/I2SI_WS</td></tr><tr><td>6</td><td>I012</td><td>HSPI_MISO</td></tr><tr><td>7</td><td>I013</td><td>HSPI_MOSI/UARTO_CTS</td></tr><tr><td>8</td><td>VCC</td><td>3.3V；外部供电电源输出电流建议在 ${500}\mathrm{{mA}}$ 以上</td></tr><tr><td>9</td><td>GND</td><td>接地</td></tr><tr><td>10</td><td>1015</td><td>HSPI_CS/UO_RTS/I2SO_BCK</td></tr><tr><td>11</td><td>102</td><td>U1_TXD/I2C_SDA/I2SO_WS</td></tr><tr><td>12</td><td>100</td><td>GPI00；下载模式：外部拉低,运行模式：悬空或者外部拉高</td></tr><tr><td>13</td><td>104</td><td>GP104</td></tr><tr><td>14</td><td>105</td><td>IR_R</td></tr></table>

<table><tr><td>15</td><td>RX</td><td>RX 接收引脚</td></tr><tr><td>16</td><td>TX</td><td>TX 发送引脚</td></tr></table>

表 模组启动模式说明

<table><tr><td>模式</td><td>CH_PD (EN)</td><td>RST</td><td>GPI015</td><td>GPIOO</td><td>GPI02</td><td>TXDO</td></tr><tr><td>下载模式</td><td>高</td><td>高</td><td>低</td><td>低</td><td>高</td><td>高</td></tr><tr><td>运行模式</td><td>高</td><td>高</td><td>低</td><td>高</td><td>高</td><td>高</td></tr></table>

  

注意：部分引脚已经内部上拉,请参考原理图

## 五、原理图

  

<!-- figureText: VDD3V3 #RESET VDD3V3 VDD3V3 VDD3P3 VDD3P3 VDDD VDDA GND VDDPST SD_CMD SD_DATA_0 VDD_RIC SD_DATA_1 IPEX_3X3 GPIO0 LNA GPIO $1/$ UOTXD GPIO2/UITXD GPIO3/UORXD GPIOS GPIO9/SD_DATA_2 $\bar{\mathrm{{GND}}}$ GPIO10/SD DATA : XTAL IN XIAL_OUT Y1 26MHz/10ppr GPIO14/MTMS RES12K GPIO15/MTDO/U2TXD GPIO16/XPD_DCDC GND ESP8266EX GNI GND VCC CLK GND SLIOO VDD3V3 XX25Q32 VDD3V3 R2 MN IO4 1010 1013 IO16 -->

<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_11.jpg?x=184&y=796&w=1284&h=630&r=0"/>

  

## 六、设计指导

1、应用电路

  

<!-- figureText: VD33 VD33 R1 10K 10K TXD0 MCU_RXD RXD0 15 MCU_TXD GPIO5 14 GPIO4 GPIOO GPIO2 GPIO15 10 GND R4 NC NC GPIOA_15 RST ADC CHIP_EN CHIP_EN GPIO16 ESP8266 GPIO14 GPIO12 GPIO13 VD33 3V3 ESD C2 C1 CON801-A1 $- {10}\mathrm{{uF}} - {0.1}\mathrm{{uF}}$ ESP8266_MOUDULE-1 -->

<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_12.jpg?x=198&y=352&w=1265&h=702&r=0"/>

  

### 2、天线布局要求

(1)、ESP-07S 需要外接天线使用,模块上留有 IPEX 天线座子。

(2)、为了天线能达到最优的效果,天线装配的位置要远离金属件和高频器件。

### 3、供电

(1)、推荐 3.3V 电压,峰值 500mA 以上电流

(2)、建议使用 LDO 供电；如使用 DC-DC 建议纹波控制在 30mV 以内。

(3)、DC-DC 供电电路建议预留动态响应电容的位置,可以在负载变化较大时,优化输出纹波。

(4)、 ${3.3}\mathrm{\;V}$ 电源接口建议增加 ESD 器件。

  



<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_12.jpg?x=178&y=1605&w=1313&h=450&r=0"/>

  

### 4、GPIO 口的使用

(1)、模组外围引出了一些 GPIO 口,如需使用建议在 IO 口上串联 10-100 欧姆的电阻。 这样可以抑制过冲, 是两边电平更平稳。对 EMI 和 ESD 都有帮助。

(2)、特殊 I0 口的上下拉,需参考规格书的使用说明,此处会影响到模组的启动配置。

(3)、模组的 I0 口是 3.3V 如果主控与模组的 I0 电平不匹配,需要增加电平转换电路。

(4)、如果 I0 口直连到外围接口,或者排针等端子,建议在 I0 走线靠近端子处预留 ESD 器件。

  



<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_13.jpg?x=182&y=538&w=1303&h=422&r=0"/>

图 电平转换电路

七、回流焊曲线图



<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_14.jpg?x=189&y=288&w=1281&h=921&r=0"/>

  

## 八、包装信息

如下图示, ESP-07S 的包装为编带包装, 下图为示意图。

  

<img src="https://cdn.noedgeai.com/01960f62-599c-7d60-a659-4185d1bdd264_15.jpg?x=430&y=419&w=790&h=773&r=0"/>

  

九、联系我们

官方官网： https://www.ai-thinker.com

开发 DOCS: https://docs.ai-thinker.com

官方论坛：http://bbs.ai-thinker.com

样品购买： https://anxinke.taobao.com

商务合作： sales@aithinker.com

技术支持: support@aithinker.com

公司地址：深圳市宝安区西乡固戍华丰智慧创新港 C 栋 410

联系电话: 0755-29162996

【参考资料】 
- [esp-07s_product_specification_cn_v1.0.pdf (ai-thinker.com)](https://docs.ai-thinker.com/_media/esp8266/docs/esp-07s_product_specification_cn_v1.0.pdf)

