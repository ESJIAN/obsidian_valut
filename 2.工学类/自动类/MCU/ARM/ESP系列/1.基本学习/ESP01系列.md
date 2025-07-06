# ESP01S
##  一、产品概述
[5.3.1. ESP-01S模块数据手册 — 深圳四博智能创客中心 (szsmart.readthedocs.io)](https://szsmart.readthedocs.io/en/latest/zhESPSeries/ESP8266/DOIT_ESP-01S/index.html)


ESP-01S 是由安信可科技开发的 Wi-Fi 模块, 该模块核心处理器 ESP8266 在较小尺寸封装中集成了业界领先的 Tensilica L106 超低功耗 32 位微型 MCU,带有 16 位精简模式,主频支持 80 MHz 和 160 MHz,支持 RTOS,集成 Wi-Fi MAC/ BB/RF/PA/LNA。

ESP-01S Wi-Fi 模块支持标准的 IEEE802.11 b/g/n 协议,完整的 TCP/IP 协议栈。 用户可以使用该模块为现有的设备添加联网功能,也可以构建独立的网络控制器。

ESP8266 是高性能无线 SoC,以最低成本提供最大实用性,为 Wi-Fi 功能嵌入其他系统提供无限可能。


![1742973795101.png](https://www.helloimg.com/i/2025/03/26/67e3ab308c3e4.png)



ESP8266 拥有完整的且自成体系的 Wi-Fi 网络功能,既能够独立应用,也可以作为从机搭载于其他主机 MCU 运行。当 ESP8266 独立应用时,能够直接从外接 flash 中启动。 内置的高速缓冲存储器有利于提高系统性能,并且优化存储系统。

另外一种情况是,ESP8266 只需通过 SPI/SDIO 接口或 UART 接口即可作为 Wi-Fi 适配器,应用到基于任何微控制器设计中。

ESP8266 强大的片上处理和存储能力, 使其可通过 GPIO 口集成传感器及其他应用的特定设备,大大地降低了前期开发的成本。

### 1、主要特性
- 完整的 802. 11b/g/n Wi-Fi SoC 模块

- 内置 Tensilica L106 超低功耗 32 位微型 MCU,主频支持 80 MHz 和 160 MHz,支持 RTOS

- 内置 1 路 10 bit 高精度 ADC

- 支持 UART/GPIO/PWM 接口

- 采用 DIP-8 封装

- 集成 Wi-Fi MAC/ BB/RF/PA/LNA

- 支持多种休眠模式,待机功耗低至 1.0mW

- 串口速率最高可达 4Mbps

- 内嵌 Lwip 协议栈

- 支持 STA/AP/STA+AP 工作模式

- 支持安卓、IOS 的 Smart Config(APP)/ AirKiss(微信) 一键配网

- 支持串口本地升级和远程固件升级 (FOTA)

- 通用 AT 指令可快速上手

- 支持二次开发,集成了 Windows、Linux 开发环境


### 2、主要参数


<table><tr><td>模块型号</td><td>ESP-01S</td></tr><tr><td>封装</td><td>DIP-8</td></tr><tr><td>尺寸</td><td>24.4*14.4*11.2(±0.2)MM 注：11.2mm 为排针高度</td></tr><tr><td>天线形式</td><td>板载 PCB 天线</td></tr><tr><td>频谱范围</td><td>2400 ~ 2483.5MHz</td></tr><tr><td>工作温度</td><td>-20 °C ~ 70 °C</td></tr><tr><td>存储环境</td><td>-40 °C ~ 125 °C ,〈 90%RH</td></tr><tr><td>供电范围</td><td>供电电压 3.0V ~ 3.6V,供电电流 >500mA</td></tr><tr><td>支持接口</td><td>UART/GPIO/PWM</td></tr><tr><td>I0 口数量</td><td>2</td></tr><tr><td>串口速率</td><td>支持 110 ~ 4608000 bps ,默认 115200 bps</td></tr><tr><td>安全性</td><td>WEP/WPA-PSK/WPA2-PSK</td></tr><tr><td>SPI Flash</td><td>默认 8Mbit</td></tr><tr><td>认证</td><td>RoHS</td></tr></table>

表 1 主要参数说明

##  三、电气参数

### 1、功耗特性

![img](https://szsmart.readthedocs.io/en/latest/_images/wps91.png)

|Deep Sleep|20uA|
|---|---|
|Off|0.5uA|
|正常工作（平均）|80mA|
|传送 801.11b，CCK 11Mbps，Pout=+17 dBm|170mA|
|传送 801.11g，OFDM 54Mbps，Pout=+15 dBm|140mA|
|传送 801.11n，MCS7，Pout=+13 dBm|120mA|
|接收 801.11b，包长 1024 字节，-80 dBm|50mA|
|接收 801.11g，包长 1024 字节，-70 dBm|56mA|
|接收 801.11n，包长 1024 字节，-65 dBm|56mA|

​ 注①： Modem-Sleep ⽤于需要 CPU⼀直 处于⼯作状态 如 PWM 或 I2S 应⽤等。在保持 WiFi 连接时，如

果没有数据传输，可根据 802.11 标准 (如 U-APSD)，关闭 WiFi Modem 电路来省电。例如，在 DTIM3 时，每 sleep 300mS，醒来 3mS 接收 AP 的 Beacon 包等，则整体平均电流约 15mA。

​ 注②： Light-Sleep ⽤于 CPU 可暂停的应⽤，如 WiFi 开关。在保持 WiFi 连接时，如果没有数据传输，可根据 802.11 标准 (如 U-APSD)，关闭 WiFi Modem 电路并 暂停 CPU 来省电。例如，在 DTIM3 时，每 sleep

300 ms，醒来 3ms 接收 AP 的 Beacon 包等，则整体平均电流约 0.9 mA。

注③： Deep-Sleep 不需⼀直保持 WiFi 连接，很长时间才发送⼀次数据包的应⽤，如每 100 秒测量⼀次温度的传感器。例如，每 300 s 醒来后需 0.3s - 1s 连上 AP 发送数据,则整体平均电流可远⼩于 1 mA。

以上功耗数据是基于 3.3V 的电源、25°的环境温度下，并使用内部稳压器测得：

• 所有发射数据是基于 90% 的占空比，在持续发射的模式下测得。

• 所有测量数据是基于没有 SAW 滤波器的情况，在天线接口处测试。

### 2、RF 特性


| 描述                         | 最小值  | 典型值   | 最大值    | 单位  |
| -------------------------- | ---- | ----- | ------ | --- |
| 输入频率                       | 2400 | /     | 2483.5 | MHz |
| 输入阻抗值                      | /    | 50    | /      | ohm |
| 输入反射值                      | /    | /     | -10    | dB  |
| PA 输出功率为 72.2 Mbps         | 15.5 | 16.5  | 17.5   | dBm |
| 11b 模式下 PA 输出功率            | 19.5 | 20.5  | 21.5   | dBm |
|                            |      | 接收灵敏度 |        |     |
| CCK，1Mbps                  | /    | -98   | /      | dBm |
| CCK，11Mbps                 | /    | -91   | /      | dBm |
| 6Mbps（1/2 BPSK）            | /    | -93   | /      | dBm |
| 54Mbps（3/4 64-QAM）         | /    | -75   | /      | dBm |
| HT20，MCS7（65Mbps，72.2Mbps） | /    | -72   | /      | dBm |
|                            |      | 领频抑制  |        |     |
| OFDM，6Mbps                 | /    | 37    | /      | dB  |
| OFDM，54Mbps                | /    | 21    | /      | dB  |
| HT20，MCS0                  | /    | 37    | /      | dB  |
| HT20，MCS7                  | /    | 20    | /      | dB  |

							表-4 射频参数

### 3、数字端口特征

表-5 数字端口特征


|端口|典型值|最小值| |最大值|单位|
|---|---|---|---|---|---|
|输入逻辑电平低|VIL|-0.3||0.25 VDD|V|
|输入逻辑电平高|VIH|0.75 VDD||VDD + 0.3|V|
|输出逻辑电平低|VOL|N||0.1 VDD|V|
|输出逻辑电平高|VOH|0.8 VDD||N|V|

表-6 最大额定值

| 额定值    | 条件                  | 值            | 单位  |
| ------ | ------------------- | ------------ | --- |
| 存储温度   | /                   | -40 to 125   | °C  |
| 最大焊接温度 | /                   | 260          | °C  |
| 供电电压   | IPC/JEDEC J-STD-020 | +3.0 to +3.6 | V   |

##  四、外观尺寸

<img src="https://i-blog.csdnimg.cn/blog_migrate/cade3dbef7d549af101f4057cd06e46e.png"/>

<img src="https://i-blog.csdnimg.cn/blog_migrate/af6c762c8aa45933e466ef53c232c9e2.png"/>



## 五、引脚描述
ESP-01S 模组共接出 8 个接口, 如管脚示意图, 管脚功能定义表是接口定义。

![](https://i-blog.csdnimg.cn/blog_migrate/505c57c8d427ae6f7a594e96b349b6ee.png)


ESP-01S 管脚示意图

表 管脚功能定义

<table><tr><td>脚序</td><td>名称</td><td>功能说明</td></tr><tr><td>1</td><td>GND</td><td>接地</td></tr><tr><td>2</td><td>I02</td><td>GPI02/UART1_TXD（可用IO）</td></tr><tr><td>3</td><td>I00</td><td>GPI00；下载模式：外部拉低；运行模式：悬空或者外部拉高（可用IO）</td></tr><tr><td>4</td><td>RXD</td><td>UARTO_RXD/GPI03</td></tr><tr><td>5</td><td>TXD</td><td>UARTO_TXD/GPI01</td></tr><tr><td>6</td><td>EN</td><td>芯片使能端,高电平有效</td></tr><tr><td>7</td><td>RST</td><td>复位</td></tr><tr><td>8</td><td>VCC</td><td>3.3V 供电 (VDD)；外部供电电源输出电流建议在 500mA 以 上</td></tr></table>

表 模组启动模式说明

<table><tr><td>模式</td><td>CH PD(EN)</td><td>RST</td><td>GPI015</td><td>GPI00</td><td>GPI02</td><td>TXDO</td></tr><tr><td>下载模式</td><td>高</td><td>高</td><td>低</td><td>低</td><td>高</td><td>高</td></tr><tr><td>运行模式</td><td>高</td><td>高</td><td>低</td><td>高</td><td>高</td><td>高</td></tr></table>

注意：部分引脚已经内部上拉,请参考原理图

![](https://i-blog.csdnimg.cn/blog_migrate/d2e61fde758c2633b2270c62aa61d8bb.png)
图：Non-FOTA 下载地址

![](https://i-blog.csdnimg.cn/blog_migrate/a97b07851d973a964c113a47ee9cd8ff.png)
图：FOTA 下载地址



【扩展】
- GPIO1和GPIO3可以模拟出IIC总线：[ESP-01s使用IIC串口OLED屏幕显示_esp01s i2c-CSDN博客](https://blog.csdn.net/qq_49516462/article/details/132127800)
- ESP8625与01S同体积引脚更多：[ESP-01S改进扩展IO脚适配更多传感器_esp01s可用引脚-CSDN博客](https://blog.csdn.net/honyudeng/article/details/113623781)



## 六、功能描述

### 1、MCU

ESP8266EX 内置 Tensilica L106 超低功耗 32 位微型 MCU，带有 16 位精简模式，主频支持 80MHz 和 160MHz，支持 RTOS。目前 WiFi 协议栈只用了 20%的处理能力，其余可以用来做应用开发。MCU 可通过以下接口和芯片其他部分协同工作：

• 连接存储控制器、也可以用来访问外界 Flash 的编码 RAM/ROM 接口（iBus）；

• 连接存储控制器的数据 RAM 接口（dBus）;

• 访问控制器的 AHB 接口；

### 2、存储

#### （1）内置 SRAM 与 ROM

基于 Demo SDK 的使用 SRAM 情况，用户可用剩余 SRAM 空间为：

• RAM < 50 kB（Station 模式下，连上路由后，Heap + Data 区大致可有 50kB 左右）。

• 目前 ESP8266EX 片上没有可编程 ROM，用户程序存放在 SPI Flash 中。

#### （2）SPI Flash

• ESP8266EX 芯片支持使用 SPI 接口的外置 FLASH，理论最大支持 16MB 的 SPI Flash。

• ESP-01S 模块配置了 8Mbit 的 SPI Flash，可满足一般客户的使用需求。





## 七、原理图


<img src="https://i-blog.csdnimg.cn/blog_migrate/a27a793134b0d2c0476aada96b7ff803.png"/>


##  八、设计指导
### 1、应用电路



<img src="https://i-blog.csdnimg.cn/blog_migrate/7460f6f7544787bc01ee306fd341ae0b.png"/>

 【注意】
(1)、模组外围电路,GPI00 必须上拉到 VCC,GPI015 必须下拉到 GND。

(2)、EN 脚和 RST 脚必须上拉到 VCC。

### 2、天线布局要求



(1)、在主板上的安装位置,建议以下 2 种方式：

方案一：把模组放在主板边沿,且天线区域伸出主板边沿。

方案二：把模组放在主板边沿,主板边沿在天线位置挖空一个区域。

(2)、为了满足板载天线的性能,天线周边禁止放置金属件,远离高频器件。



<img src="https://cdn.noedgeai.com/01946f76-6762-7a69-9acf-1c9771c84e21_12.jpg?x=157&y=394&w=1368&h=689&r=0"/>

<!-- Media -->

### 3、供电

(1)、推荐 3.3V 电压,峰值 500mA 以上电流

(2)、建议使用 LDO 供电；如使用 DC-DC 建议纹波控制在 30mV 以内。

(3)、DC-DC 供电电路建议预留动态响应电容的位置,可以在负载变化较大时,优化输出纹波。



<img src="https://cdn.noedgeai.com/01946f76-6762-7a69-9acf-1c9771c84e21_12.jpg?x=178&y=1422&w=1311&h=433&r=0"/>


### 4、GPIO 口的使用

(1)、模组外围引出了一些 GPIO 口,如需使用建议在 I0 口上串联 10-100 欧姆的电阻。 这样可以抑制过冲, 是两边电平更平稳。对 EMI 和 ESD 都有帮助。

(2)、特殊 IO 口的上下拉,需参考规格书的使用说明,此处会影响到模组的启动配置。

(3)、模组的 IO 口是 3.3V 如果主控与模组的 IO 电平不匹配,需要增加电平转换电路。

(4)、如果 IO 口直连到外围接口,或者排针等端子,建议在 IO 走线靠近端子处预留 ESD 器件。



<img src="https://cdn.noedgeai.com/01946f76-6762-7a69-9acf-1c9771c84e21_13.jpg?x=184&y=535&w=1305&h=425&r=0"/>

图 电平转换电路




ESP-01S 集成了高速 GPIO 和外设接口，这可能会产生严重的开关噪声。如果一些应用对于功耗和
EMI 特性要求较高，建议在数字 I/O 线上串联 10 ~ 100 欧姆的电阻。这样可以在开关电源时抑制过冲，并使信号变得平稳。串联电阻也能在一定程度上防止静电释放（ESD）。




## 九、回流焊曲线图




<img src="https://cdn.noedgeai.com/01946f76-6762-7a69-9acf-1c9771c84e21_14.jpg?x=199&y=289&w=1272&h=713&r=0"/>
升温区 - 温度：25 ~ 150℃ 时间：60 ~ 90s 升温斜率：1 ~ 3℃/s 
预热恒温区 — 温度：150 ~ 200℃ 时间：60 ~ 120s 
回流焊接区 — 温度：>217℃ 时间：60~90s；峰值温度：235~250℃ 时间：30~70s 
冷却区 - 温度：峰值温度 ~ 180℃ 降温斜率 -1 ~ -5℃/s 
焊料 — 锡银铜合金无铅焊料 (SAC305)



## 十、包装信息

如下图示,ESP-01S 的包装为托盘。(下图为示意图)



<img src="https://cdn.noedgeai.com/01946f76-6762-7a69-9acf-1c9771c84e21_15.jpg?x=271&y=333&w=1137&h=757&r=0"/>



## 十一、联系我们

官方官网： https://www.ai-thinker.com

开发 DOCS: https://docs.ai-thinker.com

官方论坛：http://bbs.ai-thinker.com

样品购买： https://anxinke.taobao.com

商务合作： sales@aithinker.com

技术支持: support@aithinker.com

公司地址：深圳市宝安区西乡固戍华丰智慧创新港Ｃ栋４１０

联系电话: 0755-29162996



# ESP01F

