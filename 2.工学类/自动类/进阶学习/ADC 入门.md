   现在的软件无线电、数字图像采集都需要有高速的A/D采样保证有效性和精度，一般的测控系统也希望在精度上有所突破，人类数字化的浪潮推动了A/D转换器不断变革，而A/D转换器是人类实现数字化的先锋。

       以下详细介绍ADC定义、工作原理、输入输出形式、类型、工作模式和基本参数。

## 一、ADC定义

 ADC是模拟到数字转换器（Analog-to-Digital Converter）缩写，主要用于将连续传输的模拟信号转换为数字信号，便于数字系统（如中央处理器CPU、微控制器MCU等）对传输信息进行快速处理和分析。

![](https://i-blog.csdnimg.cn/blog_migrate/91d1935eed384cbf8e08fb594e31f082.jpeg)

模拟信号是指用连续变化的物理量所表达的信息，如温度、湿度、压力、电压、电流等。ADC模块所采集的模拟信号是连续变化的电压或电流信号，其数值在一定范围内连续变化，传输信号波形如图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/3252c6162f22b70a3fc9cc1154b4a7f6.png)

模拟信号传输优缺点如下：

优点：
   1）具有精确的分辨率，在理想情况下，具有无穷大的分辨率；

   2）描述物理量时，模拟信号比数字信号处理方法更简单方便；

   3）模拟信号因为没有村子量化误差，所以能准确描述物理量的真实值；

   4）模拟信号直观且更容易实现。

缺点：
   1）模拟信号的信号比较弱，易受到杂讯的影响；

   2）传输距离近，只能进行短距离运输；

   3）抗干扰能力弱，在传输过程中容易受到噪声的干扰；

   4）模拟信号保密性差，通信内容容易遭到窃听。

数字信号是由一系列离散的数字表示，只能取有限的值，一般用二进制代码0/1表示，传输信号波形如下图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/d7a536a2dd617137703292b8fe9ecb2c.png)

数字信号传输优缺点：

优点：
   1）抗干扰能力强。数字信号通过二进制表示，相比于模拟信号的连续变化，数字信号的干扰对信号质量影响比较小，在传输和处理过程中能更好的抵抗外部干扰。

   2）压缩和处理方便。数字信号通过编码和压缩算法减少数据量，从而在传输和存储过程中节省宽带和空间。同时，利用数字信号处理（DSP）技术，进行高效的算法实现和信号分析。

   3）传输损耗小。数字信号在传输过程中可以经过放大和补偿，以抵消信号损耗，提升信号质量。此外，使用纠错编码技术，通过差错检测和纠正机制保证数据准确性。

   4）兼容性强。数字信号可以通过数字接口连接不同设备和系统，实现各种数字信号之间的互联。

缺点：
   1）处理延迟高。数字信号进行数模转换（DAC）和模数转换（ADC）的过程会带来一定的延迟，对于啥要求实时性高的应用如音频传输和通信系统可能带来问题。

   2）精度受限。数字信号的精度受到采样率限制，由于数字限号只能通过离散的数值来表示，其精度不能无限增加。在高精度应用中，可能需要更高的采样率和更大的数据表示范围。

## 二、模数转换（ADC）工作原理

### 2.1 ADC理论工作原理

      ADC在模拟信号转化为数字信号需要经过采样、保持、量化和编码。采样和保持在采样保持电路中完成，而量化和编码步骤则在ADC中完成。

![](https://i-blog.csdnimg.cn/blog_migrate/5f881f808317fb54a449b294a5baa21f.png)

#### 2.1.1 ADC采样

       采样是指ADC在一定时间间隔内对连续变化的模拟信号进行取样，实现在有限采样率条件下，无失真还原信号波形信息。取样的频率决定了每秒采集的样本量，通常单位为Hz。取样电路结构如下图：

![](https://i-blog.csdnimg.cn/blog_migrate/839bfb31d8a4b5c1d290fb0b2e4420f6.png)

      取样电路中的信号波形如下：

![](https://i-blog.csdnimg.cn/blog_migrate/5d055d174bbb2500c152c73b974cb153.png)

        由图分析可知，取样信号S(t)的频率越高，所取信号经过低通滤波器后越能真实复现输入信号波形，但同时带来采样数据量过大的问题。为了有合适的采样必须满足采样样定理。

        对于ADC采样定理，必须掌握的基本知识就是奈奎斯特（Nyquist）定理。Nyquist采样定理可以理解为一个正选波每个周期最少两个点才能把正弦波还原。同时，表明采样率fs必须大于被测信号感兴趣最高频率分量(fN)的两倍，将fN定义为奈奎斯特频率。

       本文章借鉴《ADC学习系列（一）：ADC基本概念》（文章链接见参考资料）解释理解采样率为什么需要大于被测试信号最高频率分量两倍。

- 假设采样率fs=fN

        如下图所示，由于假设采样频率和被测信号频率一致，即可以理解为周期一致。也就是说，一个采样周期内，ADC只能采集一个点，将ADC采集点连接后显示波形是直线而非原始信号波形，波形出现明显失真，表示假设不成立。

![](https://i-blog.csdnimg.cn/blog_migrate/6ee780e893a91deee73462e87d7d75c8.png)

- 假设采样率fs= （4/3）*fN

       提高采样率为fN的4/3倍，可以从下图看出，在不同周期内ADC采集点数不一样，有时候采集2个点，有时候采集1个点，最后绘制图形严重失真，证明假设不成立。

![](https://i-blog.csdnimg.cn/blog_migrate/4acc15f6997ce5e7450c8441b9893ba8.png)

- 假设采样率fs=2fN

       当采样频率为2倍信号频率且ADC采集首个点位对应波形的波峰或波谷，则在一个周期内ADC可以采集幅度的最大和最小点，最后将所有采集点连接后得到三角波，经过适当函数处理可以恢复原来正弦波信号。

       但该方法前提是必须找到信号的波峰或波谷，否则也会出现波形失真现象。因此，使用Nyquist采样定理时只需要找到信号最大的频率分量，再用2倍最大频率分量的采样频率对信号进行采样，理论上可以避免信号波形失真。

       一般情况下，实际使用示波器测试波形信号时常使用5倍法则，即测试波形带宽为示波器设置带宽的1/5，这样可以使被测波形衰减≤ 2%。同时，对于中低端示波器（BW ≤ 1GHz）而言，内部的幅频响应基本等效为一个RC低通滤波，而对于高端示波器（BW ＞ 1GHz），内部通常会有补偿算法，会得到比较平坦的幅频响应曲线，此时“98%-5倍”就不一定适用了。

![](https://i-blog.csdnimg.cn/blog_migrate/a666def678bf6fdf03c504c58a1f9655.png)

- 混叠

      混叠是指在信号的采样频率低于两倍Nyquist频率时， 采样数据中出现虚假的低频成分现象。如下图所示，灰色波形表示实际测试高频信号，但由于采样率不够，会出现红色虚线所对应的波形，导致原波形频率降低，出现虚假的重建低频信号。针对这种情况，可以使用频谱仪测试信号波形，查看信号频点是否发生降低，就可以确定是否发生混叠现象。

![](https://i-blog.csdnimg.cn/blog_migrate/66ce63846840a1cccab5d63f37580e48.png)

#### 2.1.2 ADC采样保持

       ADC采样保持过程是将已经采集的模拟信号保持恒定时间不变，以便后续模拟信号向数字信号转变，这个过程所使用的电路是采集保持器（SHA）。理想SHA由简单开关SW、保持[电容](https://www.elecfans.com/tags/%E7%94%B5%E5%AE%B9/ "电容")C以及驱动电容和后级电路的高输入阻抗缓冲器组成。其中开关SW用于采样和保持模式的切换，保持电容C用于储存输入信号的瞬时值。驱动C的高输入阻抗缓冲器用于提[供电](https://m.hqchip.com/app/1720 "供电")流增益对保持电容充电，而驱动后级的高输入阻抗缓冲器是为了防止SHA在保持模式下C放电超过1 LSB。

![](https://i-blog.csdnimg.cn/blog_migrate/104f4d6a07d8211668dea48999c83672.png)

       采样ADC的[工作原理](https://www.elecfans.com/v/tag/773/ "工作原理")：采样模式下，SHA对信号进行采样；保持模式期间内保持信号恒定。调整时序，使得后级的ADC编码器在保持时间内对保持的信号进行A-to-D转换，由于保持模式下信号几乎不变，因此ADC可以处理快速变化的高频信号，处理的频率上限不由编码器决定，而是取决于SHA的孔径抖动、带宽和失真等性能。

#### 2.1.3  ADC量化编码

       在A/D转换过程中，采样保持阶段所得到的信号是离散的模拟信号，为了将模拟信号转化为数字信号，需要将采样-保持电路的输出电压按某种方式进行划分到相应的离散电平上，将这一转化过程称为数值量化，简称量化。编码过程就是将量化后的数值按照一定规则用对应代码表示模拟信号波形。

         以下图所对应的ADC量化和编码为例进行解释，具体量化编码过程如下：

- 根据CLK时钟频率划分水平方向时间单位,Ts= 1/f （f对应ADC采样时钟频率）；
- 确定ADC通道，比如3通道ADC，可以表示000-111, T=8位数据；
- 获得模拟信号的最大/小值作差，假设差值为A；
- 计算分层电平（用V表示），V=A/T，并确定000-111代码所对应的电平值；
- 通过四舍五入或只舍不入量化方式进行波形量化；
- 将量化后电平与对应代码匹配，即可完成量化编码过程。

![](https://i-blog.csdnimg.cn/blog_migrate/1e6e7c61b769d0527abb8f3796a00c0e.png)

注：1）对于3位ADC，量化数M代码可以表示为000-110（其他位数ADC类似）；

 2）分层电平q是根据模拟信号和ADC可用通道进行划分；

 3）量化过程中所取的最小数量单位称为量化单位，用D表示，是指数字信号最低位为1时所对应的模拟信号量，即1LSB；

4）信号的实际值是指模拟信号对应的数据；

5）信号的量化值是指信号经过量化过程后所对应的值；

6）量化误差是指由于模拟信号电压不一定被D整除，所以量化前后存在误差，用e表示。量化误差属原理误差，它是无法消除的。A/D 转换器的位数越多，各离散电平之间的差值越小，量化误差越小。

### 2.2  ADC芯片内部框图分析--基于STM32_AD框图分析

        如下图所示为STM32所对应的AD结构框图，主要分为参考电压、输入通道、转换序列、触发电源、转换时间、数据寄存器和中断7个模块，具体解析如下。

![](https://i-blog.csdnimg.cn/blog_migrate/12bc509bbb8255a187f2dbca0def1646.png)

#### 2.2.1 ADC参考/模拟输入电压

        参考电压是指，如下图所示为STM32中VREF+/-参考电压说明。在VREF+/-精度要求不高情况下，可以直接接入到VDDA，如果需要精准参考电压，需要外接VREF芯片或单独电路模块单独生成。

![](https://i-blog.csdnimg.cn/blog_migrate/c99891666aa746fc905ea247d7de76f2.png)

注：附3V3基准参考电压电路

![](https://i-blog.csdnimg.cn/blog_migrate/a2d10620366104fcb1b117aca5a5773d.png)

       ADC模拟输入电压范围：VREF-£VIN£ VREF+，通常VERF+电压为3V3。因此，对应输入引脚电压范围为0V~3V3，分别对应ADC分辨率的上下限。例如16位ADC采集数据，则0V~3V3对应AD值范围0~65536。

#### 2.2.2 ADC输入通道

       如图所示外部ADC输入GPIO端口为ADCx_IN0~IN15，以及 1个内部温度传感器、1个V REFIN、1个VBAT引脚共3个内部通道。ADC通道分配需要根据具体芯片规格书进行划分，下图对应STM32F407IGT6 ADC IO分配情况：

![](https://i-blog.csdnimg.cn/blog_migrate/60f7e2ebb5e5b035988fdbba93540eba.jpeg)

#### 2.2.3  ADC转换序列

        转换序列主要分为规则组和注入组，规则组最多可以有16个转换，注入组最多有4个转换，如下图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/0d2c65082361c99a43854abad877c44d.png)

       规则组：规则组通道在使用过程中按顺序进行转换，即按顺序采集完一个通道进行转换后再采集下一个通道进行转换。规则通道和所对应的转换顺序在ADC_SQRx寄存器中进行选择，规则组转换的总数应写入ADC_SQR1寄存器的L[3:0]中。

![](https://i-blog.csdnimg.cn/blog_migrate/a9a29ab3a5900c9db0c36f082eb2a7ad.png)

![](https://i-blog.csdnimg.cn/blog_migrate/707e182f66d094630ac565f5420eb6ed.png)

![](https://i-blog.csdnimg.cn/blog_migrate/35479606d313968ab5a7852c54a049af.png)

      ADC像这样的规则序列寄存器有3个，每个规则序列寄存器都能设定第n次转换的具体通道，共有16个外部通道，最多设置16次。如上图，规则序列寄存器3（ADC_SQR3）可以设定SQ1到SQ6顺序转换的通道，规则序列寄存器2（ADC_SQR2）可以设定SQ7到SQ12顺序转换的通道，规则序列寄存器1（ADC_SQR1）可以设定第SQ13到SQ16顺序转换的通道，且ADC_SQR1寄存器的L[3:0]中（对应寄存器20~23位）用来设定要顺序转换的通道个数。例如：有4个通道需要转换，即第一次转换通道2，第二次转换通道3，第三次转换通道4，第四次转换通道1，则ADC_SQR1寄存器的L[3:0]的值位0100，ADC_SQR3中SQ1的值设为2，SQ2的值设为3，SQ3的值设为4，SQ4的值设为1。

       注入组：注入，可以理解为插入，插队的意思，是一种不安分的通道，相当于中断。注入组最多4个通道。把某一通道配置位注入通道时，所对应采集信号时的优先级就比规则通道高，即暂停规则通道组的工作，优先转换注入通道组采集到的信号。注入组和所对应的转换顺序在ADC_JSQR寄存器中选择。注入组里转化的总数须写入ADC_JSQR寄存器的L[1:0]中，该通道组的配置方法于规则通道组相同。

#### 2.2.4  ADC触发源

        软件触发：ADC转换可以由ADC 控制寄存器 2: ADC_CR2的 ADON这个位来控制，写 1的时候开始转换，写 0 的时候停止转换。

       外部事件触发：触发包括内部定时器触发和外部 IO触发。触发源有很多，具体选择哪一种触发源，由 ADC控制寄存器ADC_CR2的EXTSEL[2:0]和 JEXTSEL[2:0]位来控制

#### 2.2.5  ADC转换时间

        ADC 输入[时钟](https://www.elecfans.com/tags/%E6%97%B6%E9%92%9F/ "时钟") ADC_CLK 由 PCLK2 经过分频产生，最大值是 36MHz，即最大工作时钟不能超过36MHz，典型值为30MHz。对于 STM32F407我们一般设置PCLK2=HCLK/2=84MHz，最少需要４分频。所以程序一般使用 4分频或者 6分频。

![](https://i-blog.csdnimg.cn/blog_migrate/dc6307b443a2edd9a0aa0e81a832f046.png)

     ADC 的总转换时间Tconv = 采样时间 + 12个周期（转换时间），采样时间最少不小于3个ADC_CLK，转换时间一般就是12个ADC_CLK，如果对时间没有太过苛刻的要求，应当把采样时间设置的稍长一些，这样得到的结果才会更加准确。最小采样时间：T=3+112=15个周期=0.42us(ADC时钟=36MHz下得到）。ADC采样时序如下图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/71a6af921f8e87416f5865fc0bbf573b.png)

#### 2.2.6  ADC数据寄存器

    规则数据寄存器 ADC_DR是一个32 位的寄存器且只有一个，只有低 16 位有效且只适用于独立模式存放转换完成数据。因为 ADC 的最大精度是 12 位，ADC_DR 是16 位有效，对于选择ADC存放数据时选择左对齐或者右对齐，则通过 ADC_CR2的 11 位 ALIGN设置确定。对于规则通道组来说，所有的规则通道都使用这一个数据寄存器，实际采样点时候，如果开启了多个通道，每转换完成一个通道要及时把数据从寄存器中取走。如果不及时取走，下一次转换完成的数据就会覆盖原数据。针对这种情况，可以使用直接存储器存取技术（Direct Memory Access）简称DMA进行避免丢失在下一次写入之前还未被读出的 ADC_DR 寄存器中的数据。在使能 DMA 模式的情况下（ADC_CR2 寄存器中的 DMA 位置 1），每完成规则通道组中的一个通道转换后，都会生成一个 DMA 请求。

![](https://i-blog.csdnimg.cn/blog_migrate/267f40f356ad39deba1566fac1b30f12.png)

        注：DMA用来提供在外设和存储器之间或者存储器和存储器之间的高速数据传输。无须CPU干预，数据可以通过DMA快速地移动，这就节省CPU的资源可以做其他操作。DMA传输的本质是地址到地址的操作，可以把DMA理解为CPU的“秘书”。

       注入通道虽然只有4个通道，但时每一个通道都有自己的数据寄存器，可以避免数据读取不及时出现数据被覆盖现象。

#### 2.2.7 ADC中断

       转换结束中断：规则通道和注入通道的数据转换结束后，都可以产生中断。通道转换完成后，ADC 状态寄存器 ADC_SR的EOC位会置１，可以不断轮询此位来判断是否触发中断，也可以使能中断，完成后就根据此位的状态触发中断，中断的使用是最多的。同时，可以在中断处理程序中获取我们想要采集的数据。

      模拟看门狗中断：当被 ADC 转换的模拟电压低于低阈值或者高于高阈值时，就会产生中断

      溢出中断：如果发生 DMA传输数据丢失，会置位 ADC 状态寄存器 ADC_SR的 OVR位，如果同时使能了溢出中断，那在转换结束后会产生一个溢出中断。

       DMA 请求：规则和注入通道转换结束后，除了产生中断外，还可以产生 DMA请求，把转换好的数据直接存储在内存里面。

![](https://i-blog.csdnimg.cn/blog_migrate/dfd1225e81555c2af5073a4e626844ee.png)

## 三、ADC信号输入输出形式

        ADC信号输入和输出的主要形成分为单端和差分两种方式，以输入方式进行学习。

### 3.1   单端输入

#### 3.1.1 单端输入简介

       单端信号是指只有一个信号引脚传输信号的方式。在单端信号传输中，信号源的电压或电流相对于地（或参考电压）的变化表示信号的信息。单端信号传输简单且常见，适用于短距离的数据传输。优点是简单方便，能满足大多数领域对数据采集的需求，所需pin小，设计简单；缺点是抗干扰能力相对较弱，ADC采集电压波动比较大，容易受到GND影响产生杂散和共模信号。

![](https://i-blog.csdnimg.cn/blog_migrate/d215b3b908f490aa614c7e28041ec672.png)

        如下图所示，单端输入只有一个输入引脚ADVIN，使用公共GND作为返回端，ADC的采样值=VADCIN-VGND。

![](https://i-blog.csdnimg.cn/blog_migrate/730232daefa80b6d5e6f67e003769bc6.png)

#### 3.1.2 为什么单端输入会产生共模信号？

      差分对管放大的前提是管子要开启并偏执在放大状态，就是说必须有一个电压使得基极和发射极之间的[PN结](http://m.elecfans.com/article/577144.html "PN结")导通。这个使PN结导通的电压差是共模信号与GND差值。所以单端输入指的是在一端加上差模信号，但是对管的两端仍然需要共模信号来保证偏置，只是对管不放大共模而已。

#### 3.1.3 消除共模干扰方法有那些？

       共模干扰源于共模信号和GND之间信号传输所产生，属于非对称干扰。消除共模干扰的方法包括：

1）采用屏蔽双绞线并有效接地

2）强电场的地方还要考虑采用镀锌管屏蔽

3）[布线](http://www.hqpcb.com/ "布线")时远离高压线，更不能将高压电源线和信号线捆在一起走线

4）采用浅性和稣压电原或高品质的[开关电源](http://www.elecfans.com/tags/%E5%BC%80%E5%85%B3%E7%94%B5%E6%BA%90/ "开关电源")（纹波干扰小于50mV）在一般情兄下，差模信号就是两个信号之差，共模信号是两个信号的算术平均值。

### 3.2  差分输入介绍

       差分信号传输对于远距离传输可以提供更好的抗干扰能力，因为干扰信号通常会同时影响正向信号和反向信号，而差分接收器可以通过比较两个信号的差异来减少干扰的影响。因此，差分信号传输更适用于抗干扰要求较高的应用以及长距离传输等场景。

![](https://i-blog.csdnimg.cn/blog_migrate/09a614839cbcd78868f64ca13fd896d7.png)

         差分输入ADC采样值= Vadcin+ - Vadin-，在PCB布线时通常布在一起，当其中一方受到干扰时，另一方也会受到同样的干扰。这样，在采样时能够相互抵消，从而减小干扰，增强抗干扰能力。

![](https://i-blog.csdnimg.cn/blog_migrate/c96c34e3a82834c57a4f035637f8ea9f.png)

差分信号传输的优点：

1）差分信号的总dI/dt比单端信号少，能降低EMI噪声和轨道塌陷。

2）差分信号在一对紧耦合差分传输线上传输，对返回路径的依赖没那么大。

3）使用差分线可以实现远距离差分信号的传输。

差分信号传输的缺点：

1）差分信号传输会使得收发端的电路变得复杂，系统的功耗也会随之上升。

2）如果设计不恰当，在差分信号线上有共模信号存在，会带来额外的EMI问题。

3）传输同样的数据，差分信号需要2根信号线，且差分信号一定要走两根等长、等宽、紧密靠近。这意味着电路连接更多、所需PCB面积更大。

## 四、ADC类型

### 4.1 流水线型ADC [13]

       流水线型ADC的工作流程如下图所示，在流水线ADC中，输入信号经过采样后，顺序地沿着流水线移动，一步一步进行数字转换，每步转换得到一定数量的数字输出位，最高有效位最先的得到，最低有效位最后得到。

![](https://i-blog.csdnimg.cn/blog_migrate/9d4a4b1bb33af4336ccba96adb8db55b.png)

       以12位流水线ADC结构框图进行解释。输入Vin首先被采样/保持（S&H）电路所采样，同时第一级（stage1）的闪速ADC把它量化为3位，并输出馈送到3位[DAC](https://www.elecfans.com/tags/dac/ "DAC")（具有12位精度），同时从输入模拟信号中减去已处理的模拟信号，将结果放大4倍输出给下一级（stage2）。随后，在stage2继续重复上述过程，每级提供3位，直到最后一级4位闪速ADC。每一级包含抽样保持电路、低分辨率的AD子转换电路、低分辨率的DA转换电路、减法器和级间增益放大器。

![](https://i-blog.csdnimg.cn/blog_migrate/a7fa1b1ac75496b9c8de86a22c89a586.png)

       由于每级在不同的时间得到变换结果，因此在进行数字误差校正前用移位[寄存器](https://www.elecfans.com/tags/%E5%AF%84%E5%AD%98%E5%99%A8/ "寄存器")对各级的结果先按时间对准。当一个阶段完成对样品的处理、确定位并将残余物传递到下一个阶段时，它可以开始处理从每个阶段中嵌入的采样保持接收的下一个样品。这种流水线操作是高吞吐量的原因。

       流水线型ADC对应的优点是每级都有独立的抽样保持电路，可以同时对前一级的余量进行处理，达到很高的转换速率;每一级数字输出都有冗余位，可以利用数字校正技术消除冗余，提高分辨率;与同分辨率的闪烁型AD转换电路相比，它能大大降低电路规模与功耗。同时，它对应的缺点是需要复杂的基准电路与偏置结构;输入信号必须穿过数级电路，造成流水线延迟;而各级输出必须要严格同步;要求50%的占空因数以及最小的时钟频率等。

       为了提高流水线型AD转换电路的性能，采用了多种方法。如采用开环结构、双抽样等新技术来提高速度;采用自我校正算法、背景校正算法等新的数字校正算法来提高分辨率。

### 4.2 Flash型ADC

       Flash ADC是快闪式模拟数字转换器（Flash Analog-to-Digital Converter）的缩写，其构建模式是一种高速流水线ADC。由于其内部使用多个比较器，其数据传输速度很快，内部结构如下图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/68dee01affd4b864152cae9b4b86d1a7.png)

       一个N位Flash ADC包括2N个电阻和2N-1个比较器，每个比较器均从电阻中获取基准电压，且每个基准电压比链中下一级基准电压大1LSB（图中1LSB=2/16V，LSB与2.1.3 ADC量化编码中层级电平概念类似）。对于给定电压Vin，若Vin>Max LSB（最大基准电压）时，ADC逻辑输出全“1”，而Vin<Min LSB（最小基准电压）时，ADC逻辑输出全“0”。

       以上图三位Flash ADC说明，D0~D2编码器输出000~111代表1V电压，1SLB=2/16V。若Vin = 0V5 (0.5V) =8/16V，则C1~C4输出1，C5~C7输出2， 即1111000，也就是4， 编码器输出对应100。

       Flash ADC具有转换速度快且精度高的优点，但由于采用大量电阻和比较器，在高速运转时存在相对较高的功耗。因此，Flash ADC具有明显功耗高的缺点，且因成本问题伴随芯片尺寸大，而且分辨率有限。此外，基准电阻链的电阻必须保持在较低水平，以便向快速比较器提供足够的偏置电流，因此基准电压源必须提供较大的源电流(通常大于10 mA)。

### 4.2 SAR型ADC

       SAR型ADC全称—循环渐进模拟数字转换器（Successive approximation Register ADC），主要由1个比较器、1个数模转换器、1个逐次逼近寄存器（SAR）和1个逻辑控制单元组成。它首先将采集输入信号与内部参考电压进行比较，将比较结果与参考电压一半再进行比较，然后根据比较结果确定下一步比较的阀值。通过不断重复此过程，逼近输出的精度越来越高，最终得到目标数字化结果。其中比较次数正好为ADC的量化深度，即位数。同时，1个时钟周期内完成位转换，N位则需要N个时钟周期转换完成，输出二进制数字信号。

![](https://i-blog.csdnimg.cn/blog_migrate/061a377ccfb934c4ee531b017ed02a45.png)

SAR ADC优点：

1）结构简单、转换速度快，精度高，在数字信号处理中广泛应用；

2）分辨率低于12位时，价格低，采样速率可达1MSPS；

3）与其他类型ADC相比，功耗相对较低。

SAR ADC缺点：

1）由于其需要逐步逼进，所以在处理不稳定的、干扰较大的信号时可能出现收敛慢、精度下降等问题；

2）在高于14位分辨率情况下，价格较高；

3）传感器产生的信号在进行模/数转换之前需要进行调理，包括增益级和滤波，这样会明显增加成本。

### 4.3双积分型ADC

        双积分型ADC主要可以积分环节、比较环节、计数环节。具体电路图如下。

![](https://i-blog.csdnimg.cn/blog_migrate/2fa0de08cf63e16095b919eab1c2d450.png)

参考分析理论资料：

1）[https://blog.csdn.net/ypoflyer/article/details/42609381?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170585192116800182145621%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170585192116800182145621&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-42609381-null-null.142^v99^pc_search_result_base4&utm_term=%E7%A7%AF%E5%88%86%E5%9E%8BADC%E5%8E%9F%E7%90%86&spm=1018.2226.3001.4187![icon-default.png?t=N7T8](https://i-blog.csdnimg.cn/blog_migrate/003a2ce7eb50c2e24a8c624c260c5930.png)https://blog.csdn.net/ypoflyer/article/details/42609381?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170585192116800182145621%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170585192116800182145621&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-42609381-null-null.142%5Ev99%5Epc_search_result_base4&utm_term=%E7%A7%AF%E5%88%86%E5%9E%8BADC%E5%8E%9F%E7%90%86&spm=1018.2226.3001.4187](https://blog.csdn.net/ypoflyer/article/details/42609381?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170585192116800182145621%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170585192116800182145621&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-42609381-null-null.142%5Ev99%5Epc_search_result_base4&utm_term=%E7%A7%AF%E5%88%86%E5%9E%8BADC%E5%8E%9F%E7%90%86&spm=1018.2226.3001.4187 "https://blog.csdn.net/ypoflyer/article/details/42609381?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170585192116800182145621%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170585192116800182145621&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-42609381-null-null.142^v99^pc_search_result_base4&utm_term=%E7%A7%AF%E5%88%86%E5%9E%8BADC%E5%8E%9F%E7%90%86&spm=1018.2226.3001.4187")

2）[采用A/D转换器的直接式电容采集（1）——双积分型ADC原理介绍_双积分式 ad 采样技术-CSDN博客](https://blog.csdn.net/Conan_Fate/article/details/130972047 "采用A/D转换器的直接式电容采集（1）——双积分型ADC原理介绍_双积分式 ad 采样技术-CSDN博客")

### 4.4 ∑-Δ型ADC [14-16]

       Sigma-dela ADC是 ∑-Δ型调制器模拟数字转换器（Sigma-Delta Modulator Analog-to-Digital Converter）的简称，它不是纯模拟电路，约有1/4比例的模拟单元和3/4比例的数字处理单元，依据过采样和噪声整形使输入模拟信号的带内信噪比得到极大的提高，输出的是高频数字信号。之后需要通过一个数字滤波器，对输出的高频信号进行降采样（抽取）和低通滤波，以便输出可正常处理的数字信号，其基本框架如下图。

![](https://i-blog.csdnimg.cn/blog_migrate/d95bab5d2b4906ed8f18bfcb32ad31c7.png)

       Sigma-dela ADC涉及基本概念如下图所示，其三大关键技术包括过采样、噪声整形、数字滤波和采样抽取。

![](https://i-blog.csdnimg.cn/blog_migrate/c9af6112650389a8394d974f26c48879.png)

#### 4.4.1 过采样

       给定正弦波，进入采样速率Fs的转换后，在对应频点可以看到尖峰，但存在许多量化噪声。量化噪声是由于ADC精度，决定了转换器针对输入的连续正弦波，只能采集有限数量的离散样值而导致。1bit量化电平

![q=\frac{2A}{2^{N}}](https://latex.csdn.net/eq?q%3D%5Cfrac%7B2A%7D%7B2%5E%7BN%7D%7D)

A代表幅度，信号占据范围[-A,A]，N表示信号质量化比特位数。

量化噪声

![\epsilon =\frac{\pm q}{2}=\pm A\cdot 2^{-N}](https://latex.csdn.net/eq?%5Cepsilon%20%3D%5Cfrac%7B%5Cpm%20q%7D%7B2%7D%3D%5Cpm%20A%5Ccdot%202%5E%7B-N%7D)

量化噪声功率

![P_{\epsilon }=\int_{\frac{-q}{2}}^{\frac{q}{2}}p(\epsilon )\epsilon ^{2}\approx \frac{A^{2}\cdot 2^{-2N}}{3}](https://latex.csdn.net/eq?P_%7B%5Cepsilon%20%7D%3D%5Cint_%7B%5Cfrac%7B-q%7D%7B2%7D%7D%5E%7B%5Cfrac%7Bq%7D%7B2%7D%7Dp%28%5Cepsilon%20%29%5Cepsilon%20%5E%7B2%7D%5Capprox%20%5Cfrac%7BA%5E%7B2%7D%5Ccdot%202%5E%7B-2N%7D%7D%7B3%7D)

下图a中信号功率

![P_{\delta }=\frac{A^{2}}{T}\int_{0}^{T}sinwt^{2}dt=\frac{A^{2}}{2}](https://latex.csdn.net/eq?P_%7B%5Cdelta%20%7D%3D%5Cfrac%7BA%5E%7B2%7D%7D%7BT%7D%5Cint_%7B0%7D%5E%7BT%7Dsinwt%5E%7B2%7Ddt%3D%5Cfrac%7BA%5E%7B2%7D%7D%7B2%7D)

则信号量化噪声比SQNR

![10log_{10}\frac{P_{\delta }}{P_{\epsilon }}=1.76+6.02N(dB)](https://latex.csdn.net/eq?10log_%7B10%7D%5Cfrac%7BP_%7B%5Cdelta%20%7D%7D%7BP_%7B%5Cepsilon%20%7D%7D%3D1.76&plus;6.02N%28dB%29)

![](https://i-blog.csdnimg.cn/blog_migrate/dddaf72fc49a152b13492e0acb9c283d.png)

注：（a）正弦波的量化；（b）正弦波频谱

        对于理想ADC而言，SQNR代表信噪比SNR。对于奈奎斯特速率的ADC，可通过增加采样位数，改善SNQR。对于Sigma-Delta ADC，通过K倍过采样，将量化噪声扩展至KFs/2，降低Fs/2内的噪声功率，同样改善了SNQR。

![](https://i-blog.csdnimg.cn/blog_migrate/65b00caeda0d0ad8c1aa54ffbd65ef4a.png)

注：（c）过采样对量化噪声影响；（d）奈斯特采样下的量化噪声分布；（e）过采样下的量化噪声分布。

        这样，增加至4倍采样率，SNR（信噪比，详解见ADC基本参数）可以改善6dB。

#### 4.4.2 噪声整形

       如下所示，是一个一阶Sigma-Delta 调制器结构图。主要由一个差分放大器，积分器，比较器和1bit DAC组成。

![](https://i-blog.csdnimg.cn/blog_migrate/551007067ad6b1a055470381ed64a42a.png)

       如果输入信号增加，1bit ADC，相当于简单的比较器，产生“1”；如果输入信号减小，产生“0”。这样，Sigma-Delta 调制器传递着输入信号的梯度量。

        从频域模型来看，积分器相当于低通滤波，在1bit转换过程中，量化噪声引入。其调制频域模型如下图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/3032a789963c26e055747079b4f22c69.png)

调制器的输出为

![S_{o}=\frac{S_{i}}{f+1}+\frac{qf}{f+1}](https://latex.csdn.net/eq?S_%7Bo%7D%3D%5Cfrac%7BS_%7Bi%7D%7D%7Bf&plus;1%7D&plus;%5Cfrac%7Bqf%7D%7Bf&plus;1%7D)

       式中第一项，可以看作信号，第二项，可以看作噪声项。频率趋近于0，调制器输出接近 ；频率趋向高频，噪声项趋近于q，信号项趋近于0。这样，积分器对量化噪声而言，呈现高通滤波的效果。量化噪声波形如下图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/27d3e2eaaf6064f5571175e0d18b9561.png)

      更高阶的Sigma-Delta 调制器，将能实现进一步噪声整形，从而带来SQNR的明显改善。1阶和2阶调制器性能比较如下图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/e38866c58eb8b2c26037433a261dfd0d.png)

#### 4.4.3 数字滤波和采样抽取

#####  4.4.3.1 数字滤波

       数字滤波主要由数字滤波器实现。使用数字处理器（PC或者专用DSP），在信号的样本值上进行[数值计算](https://www.zhihu.com/search?q=%E6%95%B0%E5%80%BC%E8%AE%A1%E7%AE%97&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2822918303%7D "数值计算")，实现滤波。其处理框图如下图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/4ff057f37b90949e40cc398d75378c78.png)

数字滤波相对模拟滤波，有以下优点：

1）数字滤波器是可编程的，其运算由处理器中的程序确定，在软件上容易调整，而模拟滤波器只能通过重新设计硬件电路进行调整；

2）模拟滤波器[电路元件](https://www.zhihu.com/search?q=%E7%94%B5%E8%B7%AF%E5%85%83%E4%BB%B6&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2822918303%7D "电路元件")性能受温度影响较大，而数字滤波器随时间和温度变化呈现出稳定的性能；

3）数字滤波器可以处理非常低频的信号；

4）数字滤波器可获得[线性相位](https://www.zhihu.com/search?q=%E7%BA%BF%E6%80%A7%E7%9B%B8%E4%BD%8D&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra=%7B%22sourceType%22%3A%22answer%22%2C%22sourceId%22%3A2822918303%7D "线性相位")响应。

数字滤波器对应缺点如下：

1）速度限制，数字滤波器能实时处理的信号最大带宽，比模拟滤波器低；

2）有限字长效应，数字滤波器遭受ADC噪声和截断噪声等的影响，带来不稳定性；

3）较长的设计开发周期，数字滤波器的硬件开发部分，会比模拟滤波器更久。

        数字滤波器主要分为两类——FIR和IIR。数字滤波器可由下图所示的冲激响应来表征。

![](https://i-blog.csdnimg.cn/blog_migrate/d86b97765d7a3f5c50b55aae3afbd0c5.png)

滤波器的输入和输出信号，根据FIR和IIR，分别表示为

![y(n)=\sum_{k=0}^{N-1}h(k)x(n-k)FIR](https://latex.csdn.net/eq?y%28n%29%3D%5Csum_%7Bk%3D0%7D%5E%7BN-1%7Dh%28k%29x%28n-k%29FIR)

![y(n)=\sum_{k=0}^{\bowtie }h(k)x(n-k)IIR](https://latex.csdn.net/eq?y%28n%29%3D%5Csum_%7Bk%3D0%7D%5E%7B%5Cbowtie%20%7Dh%28k%29x%28n-k%29IIR)

FIR与IIR性能对比如下：

1. ![](https://i-blog.csdnimg.cn/blog_migrate/f093edb5f4b17649cb106e1a27e0d4f3.png)
2. ##### 4.4.3.2 采样抽取[17]
    
          抽取，是采样率变换的一种，从高速采样率转换为低速采样率的过程。抽取的过程中，频谱会发生混叠，原始信号频谱需严格带限。
    

![](https://i-blog.csdnimg.cn/blog_migrate/9a7afcb83dcfc4257e2de64d6d05b36d.png)

为了防止混叠，引入低通滤波器。

![](https://i-blog.csdnimg.cn/blog_migrate/c73a17f636aeb755b6c4a2530439e917.png)

在速率转换系统中，常用的滤波器有CIC滤波器和半边带滤波器等。

- CIC滤波器

      CIC 滤波器无乘法器结构，仅由加法器和延迟元件组成，这在降低功耗方面具有很大优势。经典的单级 CIC 滤波器输出的差分方程为:

![y(n)=x(n)+x(n-1)+x(n-2)+...+x(n-D+1)](https://latex.csdn.net/eq?y%28n%29%3Dx%28n%29&plus;x%28n-1%29&plus;x%28n-2%29&plus;...&plus;x%28n-D&plus;1%29)

传递函数为：

![H(Z)=\frac{Y(z)}{X(z)}=\sum_{n=0}^{D-1}=1+z^{-1}+z^{-2}+....+z^{-D+1}](https://latex.csdn.net/eq?H%28Z%29%3D%5Cfrac%7BY%28z%29%7D%7BX%28z%29%7D%3D%5Csum_%7Bn%3D0%7D%5E%7BD-1%7D%3D1&plus;z%5E%7B-1%7D&plus;z%5E%7B-2%7D&plus;....&plus;z%5E%7B-D&plus;1%7D)

常用的递归结构的单级CIC滤波器结构如下：

![](https://i-blog.csdnimg.cn/blog_migrate/513ea51db4722025421c9fc2b0e407d2.png)

       可以看到 CIC 滤波器由积分部分和梳状部分组成，积分部分是简单的累加器，表 示当前值加上下一个采样值，梳状部分则是一种另类的差分器，表示当前值减去延时 M 个时钟周期的输入值。而且 CIC 滤波器是一种非常灵活的滤波器，它的梳状部分、积分部分和延时单元可以交换顺序，极大的降低了 CIC 滤波器的设计难度。

单级CIC频率响应：

![H(e^{jw})=\frac{1-e^{-jwM}}{1-e^{-jw}}](https://latex.csdn.net/eq?H%28e%5E%7Bjw%7D%29%3D%5Cfrac%7B1-e%5E%7B-jwM%7D%7D%7B1-e%5E%7B-jw%7D%7D)

根据欧拉公式 ![sinx=\frac{e^{jx}-e^{-jx}}{2j}](https://latex.csdn.net/eq?sinx%3D%5Cfrac%7Be%5E%7Bjx%7D-e%5E%7B-jx%7D%7D%7B2j%7D)可得

![H(e^{jw})=e^{j\frac{w}{2}}e^{-j\frac{w}{2}M}\frac{sin(\frac{wM}{2})}{sin(\frac{w}{2})}](https://latex.csdn.net/eq?H%28e%5E%7Bjw%7D%29%3De%5E%7Bj%5Cfrac%7Bw%7D%7B2%7D%7De%5E%7B-j%5Cfrac%7Bw%7D%7B2%7DM%7D%5Cfrac%7Bsin%28%5Cfrac%7BwM%7D%7B2%7D%29%7D%7Bsin%28%5Cfrac%7Bw%7D%7B2%7D%29%7D)

       CIC 滤波器是一个![\frac{sinx}{x}](https://latex.csdn.net/eq?%5Cfrac%7Bsinx%7D%7Bx%7D)类型的滤波器，以下为抽取因子M=32，采样率256MHz时，单级CIC幅频特性

![](https://i-blog.csdnimg.cn/blog_migrate/b90c8cf5514d0ed7be18eaf8f15160e9.png)

       CIC 滤波器的通带纹波并不平坦，存在一定的衰减，因此需要在后续滤波器中进行补偿，即设计CIC 补偿滤波器。

- 半带滤波器

       半带滤波器本质上是一个 FIR 滤波器，其特性属于低通特性，抽取因子通常为 2，半带滤波器的频率响应与普通滤波器有很大区别，其通带部分和阻带部分是频率对称 的，故半带滤波器系数的一半都为零，很大程度地降低了运算要求，由于滤波器系数只 有一半，所以保存系数的存储器数量也大大降低，相比其他的滤波器，能节约更多的硬件资源。

半带滤波器的表达式为：

![h(n)=h(N-1-n)](https://latex.csdn.net/eq?h%28n%29%3Dh%28N-1-n%29)

其中，N为滤波器的级数，为奇数。

半带滤波器的性质是偶数对称的，其频率响应为：

![H(e^{jw})=H(w)e^{j\theta w}](https://latex.csdn.net/eq?H%28e%5E%7Bjw%7D%29%3DH%28w%29e%5E%7Bj%5Ctheta%20w%7D)

其频率响应如下图示

![](https://i-blog.csdnimg.cn/blog_migrate/01bf55d91913fa9b0176cfeeb9f67f25.png)

       半带滤波器的通带和阻带对称，通带纹波和阻带纹波相等，也就是说它的通带截止频率和阻带截止频率关于 1/4 采样频率对称，通带容限和阻带容限相等。

### 4.5 总结

      流水线型ADC：分辨率中等（8~16bit）、速度500MHz以上，规模比并联比较型小，功耗高、精度高、价格高，通常用于视频、通讯领域。

       SAR型ADC：分辨率中等（8~18bit）、采样速率1MHz以上、功耗低、精度高、价格贵，通过DA输出电压和输入电压比较后再调整输出电压，直至相等，通常用于工控领域；

       ∑-Δ型ADC：分辨率中等（16~28bit）、采样速率低100K以上、功耗高、精度低、价格低，通常用于音频、工控领域；

       Flash型ADC：分辨率低（8~10bit）、采样率高、功耗高、精度高、价格高；

       双积分型ADC：分辨率中等（8~24bit）、采样速率中等，速度在300Hz以上，对输入模拟电压和基准电压进行两次积分。一般应用于低速数字仪表领域。

## 五、ADC工作模式

       ADC的工作模式主要包括单次转换模式、连续转换模式、扫描模式和不连续模式。以STM32进行举例说明

### 5.1  单次转换模式

      单次转换模式：在单次转换模式下，ADC只进行一次转换，转换完成后自动停止。这种模式适用于需求周期性地对单个通道进行采样的应用。

![](https://i-blog.csdnimg.cn/blog_migrate/6b2ebe03ceccf43968ab6333c984ab52.png)

### 5.2  连续转换模式

      在连续转换模式下，ADC会不断地进行转换，指导外部触发停止或软件停止。这种模式适用于需求对多个通道进行采样的应用。

![](https://i-blog.csdnimg.cn/blog_migrate/474678f4da0f83e7634efc7f427584ae.png)

### 5.3  扫描模式

       在扫描模式下，ADC会按照预设的顺序对多个通道进行采样。这种模式适用于需求对多个通道进行周期性采样应用。

![](https://i-blog.csdnimg.cn/blog_migrate/ca20415cceb717f4067e95d32945303d.png)

### 5.4  不连续模式

      在这种模式下，ADC会根据外部信号或其他条件的不连续变化来进行采样，而不是在整个采样期间持续采样。这种方式可以用于节省电源并减少噪声的影响。

![](https://i-blog.csdnimg.cn/blog_migrate/93e4dc1131d9fc96cfb3b29d6c1728e2.png)

       此外，ADC还包括双重模式、三重模式等，这些模式可以根据不同的应用需求和硬件配置来选择，以实现最佳性能和效率。

## 六、ADC基本参数

### 6.1 基本参数

#### 6.1.1 分辨率（Resolution）

       分辨率是ADC最基本的参数，可以用于表示每个模拟信号值的位数（二进制）来表示。一个4位ADC能表示16个不同的模拟信号值（2^4=16）。ADC的位数越多，转换的精度越高，分辨率也越高。

![](https://i-blog.csdnimg.cn/blog_migrate/93a7bcd9a24688426e0318e0a5828e80.png)

#### 6.1.2 采样速率（Sampling Time）

      采样速率是指；对ADC芯片而言，采样速率也就是ADC的最高采样频率，即数据手册中的Maximum Sampling Frequency。ADC的采样速率必须小于转换速率，常用单位ksps和Msps，表示每秒采样千/百万次（kilo/Milion Samples per Second）。根据2.1.1所述，ADC采样率必须大于等于被测信号频率的两倍。

![](https://i-blog.csdnimg.cn/blog_migrate/f9b752304de0c3ef284f41203065d023.png)

#### 6.1.3 转换时间（Conversion Time）

       转换时间的导数是转换速率。因为将一个模拟信号转换成一个数字量不能瞬间完成，这个过程需要一定时间。下图说明转化时间的基本概念，在t0时刻进行模拟电压值的转换，但在t1时刻才完成转换。

![](https://i-blog.csdnimg.cn/blog_migrate/28cff3c253971f53d602d92f18ff9bba.png)

       对STM32 ADC采样时间：TCONV = 采样时间+12.5周期，具体针对芯片规格书而定，也可以通过转换速率求导数获取芯片采样时间。

       积分型AD 的转换时间是毫秒级属低速 AD，逐次比较型 AD 是微秒级属中速 AD，全并行/ 串并行型 AD 可达到纳秒级。转换时间是衡量一个ADC是不是高速的主要指标，高速ADC转换时间小于1us，低俗ADC转换时间大于300us。

#### 6.1.4 量程（full-scale range, FSR）   

       对ADC芯片，量程指芯片允许输入模拟信号范围，与dBm有一定对应关系，单位一般用dBFS。在满量程之前，dBFS与dBm呈线性关系，即XdBm减小1dB，则XdBFS对应减小1dBFS。注：(1) dBFS解释

      dBFS是数字信号电平单位，简称满度相对电平。Full Scale 指0 dBFS 的位置, 0 dBFS就是最大编码电平，不同ADC的0 dBFS 实际对应值不同，它也是数字峰值表满度的参考电平。数字信号以ADC能处理的最大模拟信号的编码为最大值，即0 dBFS, 实际数字信号的幅度的编码相对于这个最大值的信号编码所代表的幅度之比，即为满度相对电平（dBFS）。因为规定最大值为0 的位置，所以，一片ADC实际处理的信号的满度相对电平都是负值。

一位12位的ADC芯片的dBFS计算方法：

dBFS = 20*log10(采样信号电平/1111 1111 1111)

(2) dBm是一个表示功率的绝对值（可以认为以1mW功率为基准的一个比值）

dBm = 10lg(P/1mW)，P：信号功率

#### 6.1.5 最低有效位（One least significant bit, LSB）

      最低有效位又称最小分辨率，满量程值除以ADC的分辨率就是LSB。例如一个4位的ADC，数字量最高16（2^4=16），满量程5V，最小的分辨率为5/16=0.31V，即 ADC最小辨认的电压是0.31V，可以用数字量0001表示0.31V这个模拟量。LSB越小表明ADC的精度越高。下图纵坐标是数字量编码，横坐标每一个台阶代表1LSB。

![](https://i-blog.csdnimg.cn/blog_migrate/c65fa42c016466bca115fb8c59b54b04.png)

### 6.2 静态参数

#### 6.2.1 微分非线性（Differential nonlineatity, DNL）

       在理想的A/D转换器传递函数中，每个代码都有一个相同的宽度，即从一个代码转换点到下一个代码转换点的模拟输入电压差是恒定的。

       微分非线性是指传递函数中任意输入代码的宽度与1SLB理想代码宽之间的偏差，主要显示局部差异细节。

![](https://i-blog.csdnimg.cn/blog_migrate/93fad5e6597f12dad11e2b69b6b3b41c.png)

      如下图所示，该ADC芯片的INL误差范围为[-12,12]LSB，表明在该误差范围内不会出现器件采集数据丢码现象。

![](https://i-blog.csdnimg.cn/blog_migrate/8a35e45fb7c532d4d08c915555ca7a12.png)

以3位ADC芯片，INL误差为[-1,1]LSB为例：

      当INL在误差范围内，ADC采集代码无丢码（如a、b所示），当INL不在误差范围内，ADC采集代码出现丢码现象（如c所示）

![](https://i-blog.csdnimg.cn/blog_migrate/7fa465169cfdb1fa79750249e3e6e052.png)

#### 6.2.2 积分非线性 （Integral nonlinearity, INL）

       积分非线性是DNL误差累积的结果，是指整个传递函数与线性响应相比偏离程度。INL又称转换器的线性度，通过INL测试表征设计时在校正系统增益误差和失调误差后转换器能够提供的最佳精度。

      测量INL方法主要包括端点法和最适宜法两种。

1、端点法

       采用端点法时，要测定转换器的第一个代码转换点和最后一个代码转换点的位置，并根据这两个端点推导出线性传递函数。通过计算推导出的线性传递函数的每个代码位置相对于理想值的偏差可以测得端点非线性度。

![](https://i-blog.csdnimg.cn/blog_migrate/7550ef6918086becec540091a7d0e12b.png)

2、最适宜法

      可通过对所测传递函数的增益和失调误差进行补偿、与线性传递函数进行比较以及对总的正负偏差进行平衡来找出最适宜的响应。

![](https://i-blog.csdnimg.cn/blog_migrate/5031977c68996e1035db10e1e7321f3e.png)

下图所示为ADC芯片规格书对应DNL参数。

![](https://i-blog.csdnimg.cn/blog_migrate/921dd00f401d983a2004287584d62f1c.png)

注：失调误差引起整个转换函数发生转移，但没有减少可用编码的数量（如下图所示）。失调误差的计算方式如下：

（1）当输入信号电平等于0.5个LSB时，第一个码字转换（从000到001）偏离理想位置的值。

（2） 查看X与Y轴之间的截距，即直线通过实际转换函数时所截取的X坐标。

![](https://i-blog.csdnimg.cn/blog_migrate/e0990edb9f5b5885e3a6b5452286709b.png)

       增益误差定义为满量程误差减去失调误差（如下图所示）。满量程误差在转换函数曲线上最后一次ADC跳变处进行测量，并和理想ADC的转换函数进行比较。增益误差可通过软件用线性函数y=(m1/m2)*x进行简单校正，其中m1是理想转换函数的斜率，m2是实际测量的转换函数的斜率。

![](https://i-blog.csdnimg.cn/blog_migrate/59abbd7d950beffbb73a34759a726595.png)

### 6.3 动态参数

      ADC动态参数主要关注SINAD、SNR、ENOB、THD、SFDR、NSD。动态参数是指在实际ADC运行过程中上述参数是在不断变化，具体计算方式如下所述。

#### 6.3.1 信纳比（SINAD）

       信纳比，又称信噪失真比（SINAD）指输入正弦波时，RMS（均方根）信号功率与总噪声功率和输出端（不含DC）的所有其他频率分量功率加所有其他谐波分量功率的RMS和的比值，即信号+噪声+谐波的功率与谐波+噪声的功率比值。

      SNDR 是用于衡量数据转换器的动态性能的关键参数之一，因为 SNDR 包含奈奎斯特带宽上的所有噪声和杂散。**SNDR** **说明的是输入信号的质量**；SNDR 越大，输入功率中的噪声和杂散比率越小。SNDR 的表达式为：

![SNDR=10lg(\frac{P_{signal}}{P_{noise}+P_{distortion}})](https://latex.csdn.net/eq?SNDR%3D10lg%28%5Cfrac%7BP_%7Bsignal%7D%7D%7BP_%7Bnoise%7D&plus;P_%7Bdistortion%7D%7D%29)

       其中，信号功率是有用信号、噪声和失真分量的平均功率是无用信号。SNDR一般使用的单位为分贝（dB）、相对于载波分贝（dBc）或满刻度分贝（dBFS）。SNDR的另一种表达式：

![SNDR=20lg(\sqrt{10^{\frac{-NSR}{10}}+10^{\frac{THD}{10}}})](https://latex.csdn.net/eq?SNDR%3D20lg%28%5Csqrt%7B10%5E%7B%5Cfrac%7B-NSR%7D%7B10%7D%7D&plus;10%5E%7B%5Cfrac%7BTHD%7D%7B10%7D%7D%7D%29)

      SNDR 是 SNR 规格和 THD 规格的综合，因此，SNDR 将所有不良频率分量与输入频率做比较，从而从总体上衡量数据转换器的动态性能。

#### 6.3.2 信噪比 （SNR）

       信噪比（SNR）一般用来量化数据转换器内部噪声的参数。它是输入信号功率与噪声功率的比值，一般使用dB作为单位。SNR是信号幅度和噪声幅度的RMS值衡量，具体计算公式如下：

       SNR=Psignal/Pnoise = (Amplitude_signal(RMS)/Amplitude_noise(RMS))^2 = 20lg(V_fs(RMS)/V_noise(RMS))

       由于采样抖动，信噪比在较高频率下一般会恶化。噪声的源头主要包括：（1）量化噪声；（2）ADC热噪声；（3）抖动或采样不确定噪声（采样时钟抖动）。

       在满刻度正弦波输入条件下，ADC的理论最高SNR从量化噪声推导获得。在奈奎斯特带宽上，信噪比的另一个表达式：

SNR=6.02N+1.76dB

       其中N为理想ADC的位数。该公式表示理想的N位数据转换器（不考虑谐波失真）的正弦波输入，整个奈奎斯特上能达到的最佳SNR。当输入信号带宽低于奈奎斯特速率时，SNR可以得到改善。

#### 6.3.3 有效位数 （ENOB）

       有效位数（ENOB）是用于衡量数据转换器相对于输入信号在奈奎斯特宽带上的转换质量（以位为单位）的参数。计算公式如下：

ENOB = (SINAD-1.76)/6.02

#### 6.3.4 总谐波失真 （THD）

       总谐波失真（THD，全称Total Harmonic Distortion）,是指输入信号（基波）与系统所有谐波的总功率比，指输出信号比输入信号多出的谐波成分。谐波失真是系统不完全线性引起的，所有附加谐波电平之和称为总谐波失真。总谐波失真与频率有关，其计算公式如下：

THD = 10lg(S/D)

      其中S表示信号功率，D表示总谐波功率。

       一般而言，1KHz频率处的总谐波失真比较小。ADC输出中的谐波失真是由ADC特性中存在的任何非线性引起的。每个实用的ADC都具有非线性特性。因此，每个实际ADC的输出中都存在谐波。DNL和INL是ADC特性非线性的量度，而THD是ADC输出中产生的谐波失真的量度。

![](https://i-blog.csdnimg.cn/blog_migrate/4a4c023047996bf339fd0cf3c8349a2b.png)

#### 6.3.5 无杂散动态范围 （SFDR）

       无杂散动态范围 (SFDR) 常用于衡量数据转换器在杂散分量干扰基本信号或导致基本信号失真之前可用的动态范围。SFDR 的定义是基本正弦波信号均方根 (RMS) 值与从 0Hz (DC) 到二分之一数据转换器采样速率(如 fs/2) 范围内测得的输出峰值杂散信号均方根值之比。峰值杂散分量可以是谐波关系，也可以是非谐波关系。

       SFDR 可以使用下列方程计算：

![SFDR_{dBc}=20lg(\frac{Funfamental Amplitude(RMS))}{Larger Spur Ampltimude(RMS))})](https://latex.csdn.net/eq?SFDR_%7BdBc%7D%3D20lg%28%5Cfrac%7BFunfamental%20Amplitude%28RMS%29%29%7D%7BLarger%20Spur%20Ampltimude%28RMS%29%29%7D%29)

或

SRDR=基本信号幅度-最大杂散幅度

       ADC的 SFDR 常常受输入信号的二次或三次谐波限制，需要通过设计滤波器和优化频率分配，避免二次谐波 (HD2) 和/或三次谐波 (HD3)，以大幅提高 SFDR。

#### 6.3.6 噪声谱密度（NSD）

        噪声谱密度是描述噪声功率谱密度随频率分布的物理量，是指ADC采样后，整个Nyquist带宽内的噪声分布在单位带宽上的噪声功率。NSD的单位是dBFS/Hz或dBm/Hz。

        如果从ADC的full-scale输入功率中减去噪声功率，就是full-scale下的信噪比，其中噪声功率则是Nyquist区间内所有1Hz bin中的NSD相加，即

![SNR_{dBc}=P_{dBm,found}-10lg(NSD_{dBm/Hz}\cdot \frac{f_{s}}{2})](https://latex.csdn.net/eq?SNR_%7BdBc%7D%3DP_%7BdBm%2Cfound%7D-10lg%28NSD_%7BdBm/Hz%7D%5Ccdot%20%5Cfrac%7Bf_%7Bs%7D%7D%7B2%7D%29)

若以dBFS为单位，令![P_{dBm,found}](https://latex.csdn.net/eq?P_%7BdBm%2Cfound%7D)=0dBFS，则

![SNR_{dBFS}=-NSD_{dBFS}-10lg\frac{f_{s}}{2}](https://latex.csdn.net/eq?SNR_%7BdBFS%7D%3D-NSD_%7BdBFS%7D-10lg%5Cfrac%7Bf_%7Bs%7D%7D%7B2%7D)

![NSD_{dBFS}=-SNR_{dBFS}-10lg\frac{f_{s}}{2}](https://latex.csdn.net/eq?NSD_%7BdBFS%7D%3D-SNR_%7BdBFS%7D-10lg%5Cfrac%7Bf_%7Bs%7D%7D%7B2%7D)

参考资料：

参考资料：[1][ADC学习系列（一）：ADC基础概念_adc基础知识-CSDN博客](https://blog.csdn.net/weixin_44786363/article/details/127382567 "ADC学习系列（一）：ADC基础概念_adc基础知识-CSDN博客")

[2][ADC学习系列（二）：ADC参数详解-CSDN博客](https://blog.csdn.net/weixin_44786363/article/details/127425612 "ADC学习系列（二）：ADC参数详解-CSDN博客")

[3][https://blog.csdn.net/m0_56694518/article/details/131337891?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170558324616800211512542%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170558324616800211512542&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-131337891-null-null.142^v99^pc_search_result_base4&utm_term=ADC&spm=1018.2226.3001.4187](https://blog.csdn.net/m0_56694518/article/details/131337891?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170558324616800211512542%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170558324616800211512542&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-131337891-null-null.142%5Ev99%5Epc_search_result_base4&utm_term=ADC&spm=1018.2226.3001.4187 "https://blog.csdn.net/m0_56694518/article/details/131337891?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170558324616800211512542%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170558324616800211512542&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-131337891-null-null.142^v99^pc_search_result_base4&utm_term=ADC&spm=1018.2226.3001.4187")

[4][ADC的单端输入、伪差分输入、差分输入区别？_差分adc-CSDN博客](https://blog.csdn.net/chenhuanqiangnihao/article/details/122086308 "ADC的单端输入、伪差分输入、差分输入区别？_差分adc-CSDN博客")

[5][一个芯片工程师的ADC学习笔记 （一） - 知乎](https://zhuanlan.zhihu.com/p/437719728?utm_id=0 "一个芯片工程师的ADC学习笔记 （一） - 知乎")

[6][STM32F103正点原子学习笔记系列——ADC - 知乎](https://zhuanlan.zhihu.com/p/623813296 "STM32F103正点原子学习笔记系列——ADC - 知乎")

[7][数字信号与模拟信号的优缺点简述-电子发烧友网](https://www.elecfans.com/d/2348117.html "数字信号与模拟信号的优缺点简述-电子发烧友网")

[8][https://blog.csdn.net/luoai_2666/article/details/116374154?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170573507816800182132204%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170573507816800182132204&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-116374154-null-null.142^v99^pc_search_result_base4&utm_term=%E5%A5%88%E5%A5%8E%E6%96%AF%E7%89%B9%E9%87%87%E6%A0%B7%E5%AE%9A%E7%90%86&spm=1018.2226.3001.4187](https://blog.csdn.net/luoai_2666/article/details/116374154?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170573507816800182132204%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170573507816800182132204&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-116374154-null-null.142%5Ev99%5Epc_search_result_base4&utm_term=%E5%A5%88%E5%A5%8E%E6%96%AF%E7%89%B9%E9%87%87%E6%A0%B7%E5%AE%9A%E7%90%86&spm=1018.2226.3001.4187 "https://blog.csdn.net/luoai_2666/article/details/116374154?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170573507816800182132204%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170573507816800182132204&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-116374154-null-null.142^v99^pc_search_result_base4&utm_term=%E5%A5%88%E5%A5%8E%E6%96%AF%E7%89%B9%E9%87%87%E6%A0%B7%E5%AE%9A%E7%90%86&spm=1018.2226.3001.4187")

[9][ADC需要采样保持器的原因及采样ADC的工作原理-电子发烧友网](https://www.elecfans.com/d/1360204.html "ADC需要采样保持器的原因及采样ADC的工作原理-电子发烧友网")

[10] [为什么单端输入有共模？分析其原因-电子发烧友网](https://m.elecfans.com/article/581918.html "为什么单端输入有共模？分析其原因-电子发烧友网")

[11][浅谈常用ADC的工作原理与选型！_1 bit adc-CSDN博客](https://blog.csdn.net/ZQ07506149/article/details/82557492?spm=1001.2014.3001.5506 "浅谈常用ADC的工作原理与选型！_1 bit adc-CSDN博客")

[12] [stm32_ADC电源、通道、工作模式_stm32 adc的模式-CSDN博客](https://blog.csdn.net/E2242/article/details/132317807 "stm32_ADC电源、通道、工作模式_stm32 adc的模式-CSDN博客")

[13][ADC也分很多类，你知道几种？](https://mp.weixin.qq.com/s?__biz=MjM5MTIwMjY1Mg==&mid=2650028575&idx=4&sn=637f5f068474b519482ff9eb68904095&chksm=beb9b62c89ce3f3a0abc11758a5a87dd2b3fba03a096fafdd0dccccd5ce8f6a88ab4d6d1e374&scene=27 "ADC也分很多类，你知道几种？")

[14] [射频基础系列|Sigma-Delta ADC的基本原理 - 知乎](https://zhuanlan.zhihu.com/p/597170084 "射频基础系列|Sigma-Delta ADC的基本原理 - 知乎")

[15] [射频基础系列|数字抽取滤波器 - 知乎](https://zhuanlan.zhihu.com/p/602910706 "射频基础系列|数字抽取滤波器 - 知乎")

[16] [滤波器基本原理是什么？ - 知乎](https://www.zhihu.com/question/437549216/answer/2822918303 "滤波器基本原理是什么？ - 知乎")

[17] https://zhuanlan.zhihu.com/p/602910706