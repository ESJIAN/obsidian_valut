# ESPF

## 5.3.4.1. 一. 产品概述[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id1 "Link to this heading")

ESP-F模块核心处理器采用高性价比芯片ESP8266EX。该芯片在较小尺寸封装中集成了业界领先的Tensilica’s L106 超低功耗32位微型MCU，带有16位精简模式，主频⽀持80 MHz和160 MHz，支持RTOS。ESP8266EX拥有完整的Wi-Fi网络功能，既能够独⽴应⽤，也可以作为从机搭载于其他主机MCU运⾏。当ESP8266EX独⽴应⽤时，能够直接从外接Flash中启动。内置的⾼速缓冲存储器有利于提⾼系统性能，并且优化存储系统。此外ESP8266EX只需通过SPI/SDIO 接⼝或I2C/UART⼝即可作为Wi-Fi适配器，应⽤到基于任何微控制器的设计中。

![ESP-F_3](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_3.png)

ESP-F模块支持标准的IEEE802.11 b/g/n/e/i协议以及完整的TCP/IP协议栈。用户可以使用该模块为现有设备添加联网功能，也可以构建独立的网络控制器。

ESP-F模块以最低成本提供最大实用性，为Wi-Fi功能嵌入其他系统提供无限可能。

![ESP-F_1](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_1.png)

<center><b>图1. 1模块结构图</b></center>

模块主要技术参数如下：





![ESP-F_13](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_13.png)

<center><b>表1. 1模块主要参数</b></center>

## 5.3.4.2. 二. 接口定义[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id2 "Link to this heading")

ESP-F接口定义如下图所示。

![ESP-F_2](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_2.png)

图2. 1模块管脚图

模块的工作模式选择和每个管脚定义如下表所示。

表2. 1引脚模式

|模式|GPIO15|GPIO0|GPIO2|
|---|---|---|---|
|UART 下载模式|低|低|高|
|FlashBoot模式|低|高|高|

表2.2 模块管脚功能定义

|序 号|Pin脚名称|类型|功能说明|
|---|---|---|---|
|1|RST|I|外部重置信号（低电平有效），复位模组|
|2|ADC|I|A/D转换管脚。输入电压范围0~1V，取值范围：0~1024|
|3|EN|I|芯⽚使能端，⾼电平：有效，芯⽚正常⼯作；低电平：芯⽚关闭，电流很⼩|
|4|IO16|I/O|深度睡眠唤醒|
|5|IO14|I/O|GPIO14; HSPI_CLK|
|6|IO12|I/O|GPIO12;HSPI_MISO|
|7|IO13|I/O|GPIO13;HSPI_MOSI;UART0_CTS|
|8|VCC|P|模块电源：3.3V|
|9|CS0|I/O|GPIO11; SD_CMD; SPI_CS0|
|10|MISO|I/O|GPIO7; SD_D0, SPI_MSIO|
|11|IO9|I/O|GPIO9; SD_D2 PIHD; HSPIHD|
|12|IO10|I/O|GPIO10; SD_D3;SPIWP; HSPIWP1|
|13|MOSI|I/O|GPIO8; SD_D1;SPI_MOSI1|
|14|SCLK|I/O|GPIO6; SD_CLK; SPI_CLK|
|15|GND|P|GND|
|16|IO15|I/O|GPIO15; MTDO;HSPICS;UART0_RTS|
|17|IO2|I/O|GPIO2; UART1_TXD|
|18|IO0|I/O|GPIO0;SPI_CS2|
|19|IO4|I/O|GPIO4|
|20|IO5|I/O|GPIO5|
|21|RXD|I/O|GPIO3; 可⽤作烧写Flash时UART Rx|
|22|TXD|I/O|GPIO1; 可⽤作烧写Flash时UART Tx|

## 5.3.4.3. 三. 外型与尺寸[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id3 "Link to this heading")

模组的外观尺寸为 16mm x 24mm x 3mm（如图所示）。该模组采用的Flash容量为32Mbits（4M Bytes）。

![ESP-F_3](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_3.png)

图3. 1 模组外观

![ESP-F_4](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_4.png)

图2.3DMP-P1尺寸图

![ESP-F_5](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_5.png)

(b) 侧视图

图3. 2模组尺寸图

表3. 1模组尺寸对照表

|长|宽|高|PAD 尺寸（底部）|Pin 脚间距|
|---|---|---|---|---|
|16mm|24mm|3mm|0.9mmx1.7mm|2mm|

## 5.3.4.4. 四. 电气特性[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id4 "Link to this heading")

表4. 1电气特性

![ESP-F_14](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_14.png)

## 5.3.4.5. 五. 功耗[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id5 "Link to this heading")

表5. 1功耗

|参数|最小值|典型值|最大值|单位|
|---|---|---|---|---|
|Tx802.11b, CCK 11Mbps, POUT=+17dBm|-|170|-|mA|
|Tx802.11g, OFDM 54 Mbps, POUT =+15dBm|-|140|-|mA|
|Tx802.11n,MCS7,POUT =+13dBm|-|120|-|mA|
|Rx 802.11b，1024 Bytes包⻓，-80dBm|-|50|-|mA|
|Rx 802.11g，1024 Bytes包⻓，-70dBm|-|56|-|mA|
|Rx 802.11n，1024 Bytes包⻓，-65dBm|-|56|-|mA|
|Modem-sleep①|-|15|-|mA|
|Light-sleep②|-|0.9|-|mA|
|Deep-sleep③|-|20|-|μA|
|关闭|-|0.5|-|μA|

注①：Modem-Sleep模式用于需要CPU一直处于工作的场景，如应用于PWM或I2S应用等。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路来省电。例如在DTIM3时，保持睡眠300ms，醒来3ms间隔唤醒来接收AP的Beacon包，则电流约15mA。

注②：Light-Sleep模式用于CPU可暂停的应用，如Wi-Fi开关。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路并暂停CPU来省电。例如，在DTIM3时，保持睡眠300ms，每3ms间隔唤醒来接收AP的Beacon包，则整体平均电流约0.9mA。

注③：Deep-Sleep模式应用于不需一直保持Wi-Fi连接的场景，很长时间才发送一次数据包的应用（如每100秒测量⼀次温度的传感器），每300s 醒来后需0.3s-1s连上AP，则整体平均电流可远小于1mA。

注③：Deep-Sleep模式应用于不需一直保持Wi-Fi连接的场景，很长时间才发送一次数据包的应用（如每100秒测量⼀次温度的传感器），每300s 醒来后需0.3s-1s连上AP，则整体平均电流可远小于1mA。

## 5.3.4.6. 六. Wi-Fi射频特征[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#wi-fi "Link to this heading")

下表中数据是在室内温度下，电压为3.3V和1.1V时分别测得。

表6. 1Wi-Fi射频特征

![ESP-F_15](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_15.png)

## 5.3.4.7. 七. 推荐炉温曲线[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id6 "Link to this heading")

推荐炉温曲线如下：

![ESP-F_6](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_6.png)

图7. 1推荐炉温曲线

八. 模块内部原理图

![ESP-F_7](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_7.png)

![ESP-F_8](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_8.png)

图8. 1模块原理图

## 5.3.4.8. 九. 模块最小系统[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id7 "Link to this heading")

模块最小系统电路图如下：

![ESP-F_9](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_9.png)

图9. 1最小系统

注：

（1）模块供电电压为直流3.3V；

（2）Wi-Fi模块IO最大输出电流为12mA；

（2）Wi-Fi模块NRST管脚低电平有效；EN使能管脚高电平有效；

（4）Wi-Fi模块进入升级模式：GPIO0处于低电平，然后模块复位上电；Wi-Fi模块进入正常工作模式：GPIO0处于高电平，模块复位上电。

（5）Wi-Fi模块的RXD接外部MCU的TXD，Wi-Fi模块的TXD接外部MCU的RXD；

## 5.3.4.9. 十. 推荐PCB设计[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#pcb "Link to this heading")

Wi-Fi模块可以直接焊接到PCB板上。为了使您的终端产品获得最佳的射频性能，请注意根据本指南合理设计模块及天线在底板上的摆放位置。

针对PCB天线版本ESP-M2建议将模块沿PCB板边放置，天线在板框外或者沿板边放置且下方挖空，参考方案一及方案二；若必须将PCB天线放在底板上，则需要保证天线下方的PCB区域不可敷铜，参考方案三。

针对外置天线版本ESP-M1，由于天线外置，对模块摆放位置要求不高，可参考ESP-M2的布置建议酌情调整。

## 5.3.4.10. 十. 推荐PCB设计[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id8 "Link to this heading")

Wi-Fi模块可以直接焊接到PCB板上。为了使您的终端产品获得最佳的射频性能，请注意根据本指南合理设计模块及天线在底板上的摆放位置。

针对PCB天线版本ESP-M2建议将模块沿PCB板边放置，天线在板框外或者沿板边放置且下方挖空，参考方案一及方案二；若必须将PCB天线放在底板上，则需要保证天线下方的PCB区域不可敷铜，参考方案三。

针对外置天线版本ESP-M1，由于天线外置，对模块摆放位置要求不高，可参考ESP-M2的布置建议酌情调整。

![ESP-F_10](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_10.png)

图10. 1方案一-天线在板框外

![ESP-F_11](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_11.png)

图10. 2方案二-天线沿板边放置且下方挖空

![ESP-F_12](https://szsmart.readthedocs.io/en/latest/_images/ESP-F_12.png)

图10. 3 方案三-天线沿板边放置且下方均不铺铜

## 5.3.4.11. 十一. 外围走线建议[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F/index.html#id9 "Link to this heading")

Wi-Fi模块集成了高速 GPIO 和外设接口，这可能会产生严重的开关噪声。如果一些应用对于功耗和EMI特性要求较高，建议在数字I/O线上串联10~100欧姆的电阻。这样可以在开关电源时抑制过冲，并使信号变得平稳，同时这种做法也能在一定程度上防止静电释放（ESD）。


# ESPF1
## 5.3.5.1. 一. 产品概述[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id1 "Link to this heading")

ESP-F1模块核心处理器采用高性价比芯片ESP8266EX。该芯片在较小尺寸封装中集成了业界领先的Tensilica’s L106 超低功耗32位微型MCU，带有16位精简模式，主频⽀持80 MHz和160 MHz，支持RTOS。ESP8266EX拥有完整的Wi-Fi网络功能，既能够独⽴应⽤，也可以作为从机搭载于其他主机MCU运⾏。当ESP8266EX独⽴应⽤时，能够直接从外接Flash中启动。内置的⾼速缓冲存储器有利于提⾼系统性能，并且优化存储系统。此外ESP8266EX只需通过SPI/SDIO 接⼝或I2C/UART⼝即可作为Wi-Fi适配器，应⽤到基于任何微控制器的设计中。

![ESP-F111](https://szsmart.readthedocs.io/en/latest/_images/ESP-F111.png)

ESP-F1模块支持标准的IEEE802.11 b/g/n/e/i协议以及完整的TCP/IP协议栈。用户可以使用该模块为现有设备添加联网功能，也可以构建独立的网络控制器。

ESP-F1模块以最低成本提供最大实用性，为Wi-Fi功能嵌入其他系统提供无限可能。

![ESP-F10](https://szsmart.readthedocs.io/en/latest/_images/ESP-F10.png)

图1. 1模块结构图

模块主要技术参数如下：

表1. 1模块主要参数

![ESP-F19](https://szsmart.readthedocs.io/en/latest/_images/ESP-F19.png)

## 5.3.5.2. 二. 接口定义[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id2 "Link to this heading")

ESP-F1接口定义如下图所示。

![ESP-F12](https://szsmart.readthedocs.io/en/latest/_images/ESP-F12.png)

图2. 1模块管脚图

模块的工作模式选择和每个管脚定义如下表所示。

表2. 1引脚模式

|模式|IO15|IO0|IO2|
|---|---|---|---|
|UART 下载模式|低|低|高|
|FlashBoot模式|低|高|高|

表2. 2模块管脚功能定义

|序 号|Pin脚名称|类型|功能说明|
|---|---|---|---|
|1|RST|I|外部重置信号（低电平有效），复位模组|
|2|ADC|I|A/D转换管脚。输入电压范围0~1V，取值范围：0~1024|
|3|EN|I|芯⽚使能端，⾼电平：有效，芯⽚正常⼯作；低电平：芯⽚关闭，电流很⼩|
|4|IO16|I/O|深度睡眠唤醒|
|5|IO14|I/O|GPIO14; HSPI_CLK|
|6|IO12|I/O|GPIO12;HSPI_MISO|
|7|IO13|I/O|GPIO13;HSPI_MOSI;UART0_CTS|
|8|VCC|P|模块电源：3.3V|
|9|GND|P|GND|
|10|IO15|I/O|GPIO15; MTDO;HSPICS;UART0_RTS|
|11|IO2|I/O|GPIO2; UART1_TXD|
|12|IO0|I/O|GPIO0;SPI_CS2|
|13|IO4|I/O|GPIO4|
|14|IO5|I/O|GPIO5|
|15|RXD|I/O|GPIO3; 可⽤作烧写Flash时UART Rx|
|16|TXD|I/O|GPIO1; 可⽤作烧写Flash时UART Tx|
|17|LNA|-|天线引脚（适用于：不使用IPEX接头时）|

## 5.3.5.3. 三. 外型与尺寸[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id3 "Link to this heading")

模组的外观尺寸为 16mm x 17mm x 3mm（如图所示）。该模组采用的Flash容量为32Mbits（4M Bytes）。

![ESP-F13](https://szsmart.readthedocs.io/en/latest/_images/ESP-F13.png)

(a) 俯视图

![ESP-F14](https://szsmart.readthedocs.io/en/latest/_images/ESP-F14.png)

(b) 俯视视图

图3. 2模组尺寸图

表3. 1模组尺寸对照表

|长|宽|高|PAD 尺寸（底部）|Pin 脚间距|
|---|---|---|---|---|
|16mm|17mm|3mm|0.9mmx1.7mm|2mm|

## 5.3.5.4. 四. 电气特性[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id4 "Link to this heading")

表4. 1电气特性

![ESP-F110](https://szsmart.readthedocs.io/en/latest/_images/ESP-F110.png)

## 5.3.5.5. 五. 功耗[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id5 "Link to this heading")

表5. 1功耗

|参数|最小值|典型值|最大值|单位|
|---|---|---|---|---|
|Tx802.11b, CCK 11Mbps, POUT=+17dBm|-|170|-|mA|
|Tx802.11g, OFDM 54 Mbps, POUT =+15dBm|-|140|-|mA|
|Tx802.11n,MCS7,POUT =+13dBm|-|120|-|mA|
|Rx 802.11b，1024 Bytes包⻓，-80dBm|-|50|-|mA|
|Rx 802.11g，1024 Bytes包⻓，-70dBm|-|56|-|mA|
|Rx 802.11n，1024 Bytes包⻓，-65dBm|-|56|-|mA|
|Modem-sleep①|-|15|-|mA|
|Light-sleep②|-|0.9|-|mA|
|Deep-sleep③|-|20|-|μA|
|关闭|-|0.5|-|μA|

注①：Modem-Sleep模式用于需要CPU一直处于工作的场景，如应用于PWM或I2S应用等。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路来省电。例如在DTIM3时，保持睡眠300ms，醒来3ms间隔唤醒来接收AP的Beacon包，则电流约15mA。

注②：Light-Sleep模式用于CPU可暂停的应用，如Wi-Fi开关。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路并暂停CPU来省电。例如，在DTIM3时，保持睡眠300ms，每3ms间隔唤醒来接收AP的Beacon包，则整体平均电流约0.9mA。

注③：Deep-Sleep模式应用于不需一直保持Wi-Fi连接的场景，很长时间才发送一次数据包的应用（如每100秒测量⼀次温度的传感器），每300s 醒来后需0.3s-1s连上AP，则整体平均电流可远小于1mA。

## 5.3.5.6. 六. Wi-Fi射频特征[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#wi-fi "Link to this heading")

下表中数据是在室内温度下，电压为3.3V和1.1V时分别测得。

表6. 1Wi-Fi射频特征

|参数|最小值|典型值|最大值|单位|
|---|---|---|---|---|
|输入频率|2412|-|2484|MHz|
|输入阻抗|-|50|-|Ω|
|输入反射|-|-|-10|dB|
|72.2Mbps下，PA的输出功耗|15.5|16.5|17.5|dBm|
|11b模式下，PA的输出功耗|19.5|20.5|21.5|dBm|
|灵敏度|-|-|-|-|
|DSSS, 1Mbps|-|-98|-|dBm|
|CCK11, Mbps|-|-91|-|dBm|
|6Mbps(1/2 BPSK)|-|-93|-|dBm|
|54Mbps(3/4 64-QAM)|-|-75|-|dBm|
|HT20, MCS7(65 Mbps, 72.2 Mbps)|-|-72|-|dBm|
|邻道抑制|||||
|OFDM, 6Mbps|-|37|-|dB|
|OFDM, 54Mbps|-|21|-|dB|
|HT20, MCS0|-|37|-|dB|
|HT20, MCS7|-|20|-|dB|

## 5.3.5.7. 七. 推荐炉温曲线[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id6 "Link to this heading")

推荐炉温曲线如下：

![ESP-F15](https://szsmart.readthedocs.io/en/latest/_images/ESP-F15.png)

图7. 1推荐炉温曲线

## 5.3.5.8. 八. 模块内部原理图[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id7 "Link to this heading")

![ESP-F16](https://szsmart.readthedocs.io/en/latest/_images/ESP-F16.png)

![ESP-F17](https://szsmart.readthedocs.io/en/latest/_images/ESP-F17.png)

图8. 1模块原理图

## 5.3.5.9. 九. 模块最小系统[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id8 "Link to this heading")

模块最小系统电路图如下：

![ESP-F18](https://szsmart.readthedocs.io/en/latest/_images/ESP-F18.png)

图9. 1最小系统

注：

（1）模块供电电压为直流3.3V；

（2）Wi-Fi模块IO最大输出电流为12mA；

（2）Wi-Fi模块NRST管脚低电平有效；EN使能管脚高电平有效；

（4）Wi-Fi模块进入升级模式：GPIO0处于低电平，然后模块复位上电；Wi-Fi模块进入正常工作模式：GPIO0处于高电平，模块复位上电。

（5）Wi-Fi模块的RXD接外部MCU的TXD，Wi-Fi模块的TXD接外部MCU的RXD。

## 5.3.5.10. 十. 推荐PCB设计[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#pcb "Link to this heading")

Wi-Fi模块可以直接焊接到PCB板上。为了使您的终端产品获得最佳的射频性能，请注意根据本指南合理设计模块及天线在底板上的摆放位置。

针对外置天线版本ESP-F1，由于天线外置，对模块摆放位置要求不高。

## 5.3.5.11. 十一. 外围走线建议[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F1/index.html#id9 "Link to this heading")

Wi-Fi模块集成了高速 GPIO 和外设接口，这可能会产生严重的开关噪声。如果一些应用对于功耗和EMI特性要求较高，建议在数字I/O线上串联10~100欧姆的电阻。这样可以在开关电源时抑制过冲，并使信号变得平稳，同时这种做法也能在一定程度上防止静电释放（ESD）。



# ESPF2
## 5.3.6.1. 一. 产品概述[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id1 "Link to this heading")

ESP-F2模块核心处理器采用高性价比芯片ESP8266EX。该芯片在较小尺寸封装中集成了业界领先的Tensilica’s L106 超低功耗32位微型MCU，带有16位精简模式，主频⽀持80 MHz和160 MHz，支持RTOS。ESP8266EX拥有完整的Wi-Fi网络功能，既能够独⽴应⽤，也可以作为从机搭载于其他主机MCU运⾏。当ESP8266EX独⽴应⽤时，能够直接从外接Flash中启动。内置的⾼速缓冲存储器有利于提⾼系统性能，并且优化存储系统。此外ESP8266EX只需通过SPI/SDIO 接⼝或I2C/UART⼝即可作为Wi-Fi适配器，应⽤到基于任何微控制器的设计中。

![ESP-F23](https://szsmart.readthedocs.io/en/latest/_images/ESP-F23.png)

ESP-F模块支持标准的IEEE802.11 b/g/n/e/i协议以及完整的TCP/IP协议栈。用户可以使用该模块为现有设备添加联网功能，也可以构建独立的网络控制器。

ESP-F模块以最低成本提供最大实用性，为Wi-Fi功能嵌入其他系统提供无限可能。

![ESP-F21](https://szsmart.readthedocs.io/en/latest/_images/ESP-F21.png)

图1. 1 模块结构图

模块主要技术参数如下：

表1. 1模块主要参数

![ESP-F214](https://szsmart.readthedocs.io/en/latest/_images/ESP-F214.png)

## 5.3.6.2. 二. 接口定义[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id2 "Link to this heading")

ESP-F接口定义如下图所示。

![ESP-F22](https://szsmart.readthedocs.io/en/latest/_images/ESP-F22.png)

图2. 1模块管脚图

模块的工作模式选择和每个管脚定义如下表所示。

表2. 1引脚模式

|模式|GPIO15|GPIO0|GPIO2|
|---|---|---|---|
|UART 下载模式|低|低|高|
|Flash Boot 模式|低|高|高|

表2. 2 模块管脚功能定义

|序 号|Pin脚名称|类型|功能说明|
|---|---|---|---|
|1|RST|I|外部重置信号（低电平有效），复位模组|
|2|ADC|I|A/D转换管脚。输入电压范围0~1V，取值范围：0~1024|
|3|EN|I|芯⽚使能端，⾼电平：有效，芯⽚正常⼯作；低电平：芯⽚关闭，电流很小|
|4|IO16|I/O|深度睡眠唤醒|
|5|IO14|I/O|GPIO14; HSPI_CLK|
|6|IO12|I/O|GPIO12;HSPI_MISO|
|7|IO13|I/O|GPIO13;HSPI_MOSI; UART0_CTS|
|8|VCC|P|模块电源：3.3V|
|9|CS0|I/O|GPIO11; SD_CMD; SPI_CS0|
|10|MISO|I/O|GPIO7; SD_D0, SPI_MSIO|
|11|IO9|I/O|GPIO9; SD_D2 PIHD; HSPIHD|
|12|IO10|I/O|GPIO10; SD_D3; SPIWP; HSPIWP1|
|13|MOSI|I/O|GPIO8; SD_D1; SPI_MOSI1|
|14|SCLK|I/O|GPIO6; SD_CLK; SPI_CLK|
|15|GND|P|GND|
|16|IO15|I/O|GPIO15; MTDO;HSPICS;UART0_RTS|
|17|IO2|I/O|GPIO2; UART1_TXD|
|18|IO0|I/O|GPIO0; SPI_CS2|
|19|IO4|I/O|GPIO4|
|20|IO5|I/O|GPIO5|
|21|RXD|I/O|GPIO3; 可用作烧写Flash时UART Rx|
|22|TXD|I/O|GPIO1; 可用作烧写Flash时UART Tx|

## 5.3.6.3. 三. 外型与尺寸[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id3 "Link to this heading")

模组的外观尺寸为 16mm x 24mm x 3mm（如图所示）。该模组采用的Flash容量为32Mbits（4M Bytes）。

![ESP-F24](https://szsmart.readthedocs.io/en/latest/_images/ESP-F24.png)

图3. 1 模组外观

![ESP-F25](https://szsmart.readthedocs.io/en/latest/_images/ESP-F25.png)

(a) 俯视图

![ESP-F26](https://szsmart.readthedocs.io/en/latest/_images/ESP-F26.png)

(b) 侧视图

图3. 2模组尺寸图

表3. 1模组尺寸对照表

|长|宽|高|PAD 尺寸（底部）|Pin 脚间距|
|---|---|---|---|---|
|16 mm|24 mm|3 mm|0.9 mm x 1.7mm|2 mm|

## 5.3.6.4. 四. 电气特性[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id4 "Link to this heading")

表4. 1电气特性

![ESP-F215](https://szsmart.readthedocs.io/en/latest/_images/ESP-F215.png)

## 5.3.6.5. 五. 功耗[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id5 "Link to this heading")

表5. 1功耗

|参数|最小值|典型值|最大值|单位|
|---|---|---|---|---|
|Tx802.11b, CCK 11Mbps, POUT=+17dBm|-|170|-|mA|
|Tx802.11g, OFDM 54 Mbps, POUT =+15dBm|-|140|-|mA|
|Tx802.11n,MCS7,POUT =+13dBm|-|120|-|mA|
|Rx 802.11b，1024 Bytes包⻓，-80dBm|-|50|-|mA|
|Rx 802.11g，1024 Bytes包⻓，-70dBm|-|56|-|mA|
|Rx 802.11n，1024 Bytes包⻓，-65dBm|-|56|-|mA|
|Modem-sleep①|-|15|-|mA|
|Light-sleep②|-|0.9|-|mA|
|Deep-sleep③|-|20|-|μA|
|关闭|-|0.5|-|μA|

注①：Modem-Sleep模式用于需要CPU一直处于工作的场景，如应用于PWM或I2S应用等。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路来省电。例如在DTIM3时，保持睡眠300ms，醒来3ms间隔唤醒来接收AP的Beacon包，则电流约15mA。

注②：Light-Sleep模式用于CPU可暂停的应用，如Wi-Fi开关。在保持Wi-Fi连接时，如果没有数据传输，可根据802.11标准(如U-APSD)，关闭Wi-Fi Modem电路并暂停CPU来省电。例如，在DTIM3时，保持睡眠300ms，每3ms间隔唤醒来接收AP的Beacon包，则整体平均电流约0.9mA。

注③：Deep-Sleep模式应用于不需一直保持Wi-Fi连接的场景，很长时间才发送一次数据包的应用（如每100秒测量⼀次温度的传感器），每300s 醒来后需0.3s-1s连上AP，则整体平均电流可远小于1mA。

## 5.3.6.6. 六. Wi-Fi射频特征[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#wi-fi "Link to this heading")

下表中数据是在室内温度下，电压为3.3V和1.1V时分别测得。

表6. 1 Wi-Fi射频特征

![ESP-F216](https://szsmart.readthedocs.io/en/latest/_images/ESP-F216.png)

## 5.3.6.7. 七. 推荐炉温曲线[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id6 "Link to this heading")

推荐炉温曲线如下：

![ESP-F27](https://szsmart.readthedocs.io/en/latest/_images/ESP-F27.png)

图7. 1 推荐炉温曲线

## 5.3.6.8. 八. 模块内部原理图[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id7 "Link to this heading")

![ESP-F28](https://szsmart.readthedocs.io/en/latest/_images/ESP-F28.png)

![ESP-F29](https://szsmart.readthedocs.io/en/latest/_images/ESP-F29.png)

图8. 1 模块原理图

## 5.3.6.9. 九. 模块最小系统[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id8 "Link to this heading")

模块最小系统电路图如下：

![ESP-F210](https://szsmart.readthedocs.io/en/latest/_images/ESP-F210.png)

图9. 1最小系统

注：

（1）模块供电电压为直流3.3V；

（2）Wi-Fi模块IO最大输出电流为12mA；

（2）Wi-Fi模块NRST管脚低电平有效；EN使能管脚高电平有效；

（4）Wi-Fi模块进入升级模式：GPIO0处于低电平，然后模块复位上电；Wi-Fi模块进入正常工作模式：GPIO0处于高电平，模块复位上电。

（5）Wi-Fi模块的RXD接外部MCU的TXD，Wi-Fi模块的TXD接外部MCU的RXD；

## 5.3.6.10. 十. 推荐PCB设计[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#pcb "Link to this heading")

Wi-Fi模块可以直接焊接到PCB板上。为了使您的终端产品获得最佳的射频性能，请注意根据本指南合理设计模块及天线在底板上的摆放位置。

针对PCB天线版本ESP-M2建议将模块沿PCB板边放置，天线在板框外或者沿板边放置且下方挖空，参考方案一及方案二；若必须将PCB天线放在底板上，则需要保证天线下方的PCB区域不可敷铜，参考方案三。

针对外置天线版本ESP-M1，由于天线外置，对模块摆放位置要求不高，可参考ESP-M2的布置建议酌情调整。

![ESP-F211](https://szsmart.readthedocs.io/en/latest/_images/ESP-F211.png)

图10. 1方案一-天线在板框外统

![ESP-F212](https://szsmart.readthedocs.io/en/latest/_images/ESP-F212.png)

图10. 2方案二-天线沿板边放置且下方挖空

![ESP-F213](https://szsmart.readthedocs.io/en/latest/_images/ESP-F213.png)

图10. 3 方案三-天线沿板边放置且下方均不铺铜

## 5.3.6.11. 十一. 外围走线建议[](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-F2/index.html#id9 "Link to this heading")

Wi-Fi模块集成了高速 GPIO 和外设接口，这可能会产生严重的开关噪声。如果一些应用对于功耗和EMI特性要求较高，建议在数字I/O线上串联10~100欧姆的电阻。这样可以在开关电源时抑制过冲，并使信号变得平稳，同时这种做法也能在一定程度上防止静电释放（ESD）。