#### SB TypeC & USB-PD & USB接口类型

- [24P USB-TypeC 引脚定义](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#24P_USBTypeC__1)
- - - [母头/母座](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#_18)
        - [公头/插头](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#_22)
        - [引脚功能定义](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#_29)
        - [引脚功能分布情况](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#_50)
- [16/12P USB-TypeC 引脚定义](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#1612P_USBTypeC__59)
- - - [16Pin和12Pin其实是同一种接口](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#16Pin12Pin_73)
- [6P USB-TypeC 引脚定义](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#6P_USBTypeC__80)
- [CC1、CC2的作用 - 设备识别、PD快充](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#CC1CC2__PD_94)
- - [PD及各厂商快充协议区分 - 扫盲链接](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#PD___107)
- [USB-PD](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#USBPD_120)
- [USB传输速率](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#USB_139)
- [USB2.0/3.0 接口类型一览](https://blog.csdn.net/Mark_md/article/details/114578359?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-0&spm=1001.2101.3001.4242#USB2030__144)

## 24P USB-TypeC 引脚定义

---

- USB TypeC 拥有诸多优点：双面可插不担心正反、可做`USB/雷电`高速传输载体，支持 `PD快充`、`音频设备`、`HDMI传输`、`调试模式`等诸多功能。
    
- 市面上的其他`USB接口`和`充电接口`在逐步被`TypeC`替代，可以预见的是，`TypeC`作为一种多兼容性接口，其未来会具有非常长的生命周期。
    
- 本文主要介绍 24P、16P、6P `USB-TypeC`接口的引脚定义，和`USB-PD`、`USB接口类型`，方便大家作`硬件设计`时的参考。
    

==本文介绍的内容非常之全，望各位耐心观看，有深度的信息已经给出原链接。==

（wikipedia好是真的好，可惜国内看不到，图片大多为搬运，技术交流用。[原链接：wiki百科TypeC](https://zh.wikipedia.org/wiki/USB_Type-C)）  
[AN1953 - USB TypeC的介绍 - MicroChip](https://ww1.microchip.com/downloads/en/appnotes/00001953a.pdf)  
[MicroChip TypeC 文档](https://microchipdeveloper.com/usb:type-c)  
[USB-IF官网 - USBType-C®电缆和连接器规格](https://www.usb.org/usb-type-cr-cable-and-connector-specification)  
[识别您的USB连接器或USB电缆类型](https://www.cmd-ltd.com/advice-centre/usb-chargers-and-power-modules/usb-and-power-module-product-help/identifying-usb-connector/)

---

#### 母头/母座

---

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/caada1e3ba9cc3450f14a35f529478fb.png)

---

#### 公头/插头

---

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f6b7ee46d631108918f06cd8656e4f7e.png)  
   可以很明显看出，插口内的Pin功能相对于`中心对称`。公头插入母头，无论正反插，引脚功能都完美契合。而且`电源VBUS/GND`都拥有4个Pin，最大支持`5A`电流，在保证高速数据传输的同时也提高了电流承载能力。  
  

---

#### 引脚功能定义

---

|Pin|名称|功能描述|Pin|名称|功能描述|
|---|---|---|---|---|---|
|A1|GND|接地|B12|GND|接地|
|A2|SSTXp1|SuperSpeed差分信号#1，TX，正|B11|SSRXp1|SuperSpeed差分信号#1，RX，正|
|A3|SSTXn1|SuperSpeed差分信号#1，TX，负|B10|SSRXn1|SuperSpeed差分信号#1，RX，负|
|A4|VBUS|总线电源|B9|VBUS|总线电源|
|A5|CC1|Configuration channel|B8|SBU2|Sideband use (SBU)|
|A6|Dp1|USB 2.0差分信号，position 1，正|B7|Dn2|USB 2.0差分信号，position 2，负|
|A7|Dn1|USB 2.0差分信号，position 1，负|B6|Dp2|USB 2.0差分信号，position 2，正|
|A8|SBU1|Sideband use (SBU)|B5|CC2|Configuration channel|
|A9|VBUS|总线电源|B4|VBUS|总线电源|
|A10|SSRXn2|SuperSpeed差分信号#2，RX，负|B3|SSTXn2|SuperSpeed差分信号#2，TX，负|
|A11|SSRXp2|SuperSpeed差分信号#2，RX，正|B2|SSTXp2|SuperSpeed差分信号#2，TX，正|
|A12|GND|接地|B1|GND|接地|
|`USB 2.0差分信号只会连接其中一边。因USB Type-c 插头 无B6、B7。`||||||
|||||||

---

#### 引脚功能分布情况

---

[出处：TI](https://www.ti.com/lit/wp/slly021/slly021.pdf?ts=1619083224857&ref_url=https%253A%252F%252Fwww.google.com%252F)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e7255553c1b5f8180e82781a70d94372.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/393346ea8625cad58d14aab2b67db935.png)

  

---

## 16/12P USB-TypeC 引脚定义

---
24Pin全功能的`TypeC`好用是好用，但接口的采购成本比较高。况且小家电使用的`MCU`就没有`USB3.0`，`USB2.0`就足够一般设备的使用，于是就有了`16Pin`的`TypeC`。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0e799ba4d78d1a88e2b4fe01f9712006.png)  

`16Pin TypeC`在`24Pin`的基础上阉割了`USB3.0`的`TX1/2、RX1/2`，保留了`SBU1/2`、`CC1/2`、`USB2.0的D+D-`，除了没有`USB3.0/3.1`高速传输外，其他别无二致，同样支持 `PD快充`、`音频设备`、`HDMI传输`、`调试模式`等功能。

鉴于生产厂家的不同，引脚定义可能与上图略有差异。例如TB上购买到的`16P-TypeC`，引脚定义大多如下图所示。[TYPE-C母座 16PIN板上贴片L=7.35mm](http://www.goodconn.cn/OrderProduct.aspx?classid=13&id=270)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/22cd03346016264177b89cbfbc53d54b.png)

  

---

12Pin和16Pin其实是同一种接口

---
 `16Pin`一般为接口厂家、封装的正式名称，而日常生活中习惯称呼为`12Pin`。这是因为接口设计时，将`TypeC母座`两端的两个`Vbus`和`GND`出线都并拢了起来，实际是16条出线，但焊接的焊盘只要12个。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/38717e941dc6ca0f3c67c93bf9cd08f5.png)  
  

---

## 6P USB-TypeC 引脚定义

---
对于玩具、牙刷等生活用品，产品定位上没有`USB通信`的需求，只需要`USB取电充电`。那么连`USB2.0`都可以省掉了。`6Pin TypeC`正式出道。

`6Pin TypeC`仅仅保留`Vbus`、`GND`、`CC1`、`CC2`。接口两侧对称分布着两组`GND`、`Vbus`，使得防反插功能保留，粗线也让其更为方便的传输大电流。

 `CC1`、`CC2`用于`PD设备识别`，承载`USB-PD`的通信，以向供电端请求电源供给。在传输电力的同时，USB数据传输不会受到影响。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/21d51f50fc0ea8f19dd3fcefd718fccc.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d4947827d17af4a2f08b471f673df08f.png)
![Pin解释](https://i-blog.csdnimg.cn/blog_migrate/6714ffe42724e7f5cb99ab50b7cff672.png#pic_center)
  

```ad-note
title:使用注意
1. 不使用数据传输功能CC1，CC2可以留空或者接5.1K电阻
```









---

## CC1、CC2的作用

---

### PD快充
 
这里不得不提一下`CC1`、`CC2`引脚的作用，大家最早认识快充应该是从`高通CPU的QC`开始的。通过提高输电电压，来提高输送功率。但`QC协议`中，通信使用的是`USB的DP、DM`，这就导致充电的时候会对USB通信造成影响。

而`USB-PD`对电源设备的识别依靠`CC1、CC2`引脚，避免了QC标准与`DP、DM`的冲突。使得`USB-PD`在传输电力的同时，数据传输不会受到影响。


**注意：** 由于 `USB-PD` 的输电与`CC1、CC2`引脚密切相关，小家电这些无内置`PD协议芯片`的小产品，如果想从 `USB-PD` 供给端取电，需要在 `CC1、CC2`引脚配置`Ra/Rd下拉电阻`。无下拉电阻可能影响受电。（详见上文）  


### 设备识别

  
#### 1.插入检测

**DFP**（下行端口）为主机端口，**UFP**（上行端口）为设备端口。如图所示，在DFP中的CC通道上有上拉电阻，相应的在UFP中有对应的下拉电阻。在DFP与UFP连接之前，VBUS没有输出，当两者连接之后，**DFP检测到CC引脚的电平被拉低，DFP则识别到UFP设备已连接并打开VBUS上的MOSFET，为UFP设备供电**。

![](https://upload-images.jianshu.io/upload_images/2993706-94e12344f4fb76cb.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/929/format/webp)

在DFP上有两个CC引脚，DFP通过检测三种不同形式的UFP端下拉电阻（Open开路、Ra=0.8-1.2K、Rd=5.1K）来识别各种配置模式。

![](https://upload-images.jianshu.io/upload_images/2993706-a5c43932bc3bff87.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/771/format/webp)

![](https://upload-images.jianshu.io/upload_images/2993706-a3a2dfab8f807b13.PNG?imageMogr2/auto-orient/strip|imageView2/2/w/596/format/webp)

#### 2.识别电缆方向来建立信号路由

连接Type-C电缆可以不区分正反方向，当DFP检测到CC1被下拉，则UFP是向上接入，同样地当检测到CC2被下拉则UFP是向下接入（参考上表）。下图展示了使用高速MUX进行信号路径切换。USB3.1数据速率高达10 Gbps，需要使用MUX来避免传输线分叉和冗余。

![](https://upload-images.jianshu.io/upload_images/2993706-4ad8e851e0bf19e6.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/927/format/webp)

#### 3.在两个端口间协商建立DFP和UFP身份

Type-C除了DFP与UFP，还有一种是DRP（双模式端口），可以在DFP与UFP间切换，当DRP端口与DFP设备相连，DRP则切换为UFP设备；同样地也可以切换为DFP设备。当两个DRP设备连接时，DFP与UFP身份是随机的。

![](https://upload-images.jianshu.io/upload_images/2993706-2fbb64e9b9b725fb.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/590/format/webp)

#### 4.了解VBUS配置方式：电流模式与USB PD

下表展示了每个USB标准所能提供的供电能力。纯Type-C端口可以提供5V/3A的供电能力。如果使用Type-C端口配合USB PD协议，供电能力则高达20V/5A。USB PD协议通过CC通道传输。

![](https://upload-images.jianshu.io/upload_images/2993706-911e0dfa98a70ee8.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/867/format/webp)

Type-C有 1.5A 和 3A 两种电流模式，取决于DFP的输出能力。DFP通过CC引脚上的电压告知UFP供电能力。UFP端的下拉电阻Rd=5.1K，DFP就可以通过其上拉电阻或者电流源在CC引脚上产生电压。

![](https://upload-images.jianshu.io/upload_images/2993706-07948f0d7bcf9e12.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/803/format/webp)

Type-C给出了不同输出模式下上拉电阻或电流源的规格：

![](https://upload-images.jianshu.io/upload_images/2993706-5cde6206a2938a96.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/805/format/webp)

举例来说，当DFP给CC引脚提供330uA的电流时，CC引脚上电压则为330uA * 5.1kOhms = 1.683V。根据下表，DFP则被识别为vRd-3.0标准。当DFP用10k电阻把CC引脚上拉至4.75~5.5V时，CC引脚上的电压则为1.688V，DFP也会被识别为vRd-3.0标准。

![](https://upload-images.jianshu.io/upload_images/2993706-43e9866b469677e5.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/958/format/webp)

BMC PD控制器通过CC引脚发送USB PD协议。

![](https://upload-images.jianshu.io/upload_images/2993706-c14760a693f1bc4d.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/632/format/webp)

#### 5.配置VCONN

Type-C规范定义了内部有电路需要供电的主动电缆。Type-C电缆上一共有两个CC引脚，如果其中一个用来识别DFP与UFP，那么另外一个就可以用来作为VCONN为主动电缆提供电源。当DFP检测到下拉电阻为Ra=800~1200Ohms时，这个CC引脚将切换至VCONN对外输出4.75~5.5V，功率最大1W。

![](https://upload-images.jianshu.io/upload_images/2993706-9267e19089eb32cc.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/696/format/webp)

#### 6.配置使用其他外设模式

Type-C规范定义了替代（Alt）模式与外设（Accessory）模式。主机、设备与线缆可以发送格式化的厂商自定义信息（VDM）来交换信息和发现USB ID。当主机通过VDM与设备交换信息厚进入 Alt 模式后，Type-C接口中的引脚定义将会改变以支持PCIe或者DisplayPort。下面的例子是一个Type-C扩展坞，它使用MUX切换PCIe或USB 3.1信号通至Type-C端口。

![](https://upload-images.jianshu.io/upload_images/2993706-cb32e8ba87ef5a9f.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/969/format/webp)

当CC1和CC2引脚同时使用Ra下拉时，主机将把设备识别成音频设备，然后从USB信号切换至音频信号。

![](https://upload-images.jianshu.io/upload_images/2993706-ba1ee47b17afee4b.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/870/format/webp)



## PD及各厂商快充协议区分 

（PD、QC、AFC、FCP/SCP、VOOC、PE）

---

[一文看懂存在于手机端的那些快充协议](https://www.chongdiantou.com/archives/60814.html)

[手机快充协议科普 | 细数那些让人抓狂的手机快充协议](https://zhuanlan.zhihu.com/p/353361232)

[一篇文章带你了解常见快充协议](https://zhuanlan.zhihu.com/p/196757396)

  

---

## USB-PD

---

   如果说`TypeC`的意义只在于整合了`USB串行通信设备接口`的话，那就大错特错了，借助`USB-PD协议`，用电端可以方便的从供电端取电。输出电压可调，最大传输`5A-20V`共`100W`的功率。

   USB-PD（USB Power Delivery），是USB标准化组织`USB-IF`推出的一个`USB电力输送`标准。已经发展出 1.0、2.0、3.0 三个版本。

   2017年，USB-IF 又在`USB-PD 3.0` 上增加了 `可编程电源 PPS`(Programmable Power Supply)。PPS作为PD 3.0的重大升级，旨在为当今的快速充电解决方案提供统一的规范。目前其已经实现对`高通QC 3.0/4.0`、`联发科PE 2.0/3.0`、`OPPO VOOC`、`华为SuperCharge` 等标准的收录。

- USB-PD的输出电压范围，从5V扩展到`3.0V~21V`。
- PPS可调整电压的分辨率为`20mV`
- PPS有脉动保护机制，大电流传输下，每10s要在负载和适配器之间保持一次脉动沟通，避免充电过程失控。
- 可传输 5A-20V（100W）的功率。（3A以上需要线缆内置`E-Marker芯片`）
- 支持`DFU/UFP设备身份转换`，可用同一接口完成`供电、取电`两种功能。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3a305bfb4919b31b7b8add871bfbc836.png)

新汇总的`USB-PD/QC`快充解决方案：  
[锂电快充方案：TypeC-PD/QC诱骗芯片的常用型号，升降压（充电）芯片选型](https://blog.csdn.net/Mark_md/article/details/119458578?spm=1001.2014.3001.5501)

---

## USB传输速率

---

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/94d7b20a6461e5340ea44cf900d96ebc.png)

---

## USB2.0/3.0 接口类型一览

---

[识别您的USB连接器或USB电缆类型](https://www.cmd-ltd.com/advice-centre/usb-chargers-and-power-modules/usb-and-power-module-product-help/identifying-usb-connector/)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/dcdccb73e7fc6500d46b5d289547bd58.png)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/62c2472f005466ffea9a920985ca0308.png)