## 1、IIC简介

I2C（Inter-integrated Circuit集成电路总线）总线支持设备之间的短距离通信，用于处理器和一些外围设备之间的接口，它只需要两根信号线来完成信息交换。I²C的一个特殊优势是[微控制器](https://en.wikipedia.org/wiki/Microcontroller)只需两个[通用I / O](https://en.wikipedia.org/wiki/General-purpose_I/O)引脚和软件即可控制器件芯片网络。I2C最早是飞利浦在1982年开发设计并用于自己的芯片上，一开始只允许100kHz、7-bit标准地址。1992年，I2C的第一个公共规范发行，增加了400kHz的快速模式以及10-bit扩展地址。

在I2C的基础上，1995年Intel提出了“System Management Bus” (SMBus)，用于低速设备通信，SMBus 把时钟频率限制在10kHz~100kHz，但I2C可以支持0kHz~5MHz的设备：

- **普通模式**（100kHz即100kbps）、
- **快速模式(Fm）**（400kHz）、
- **快速模式+(Fs+)**（1MHz）、
- **高速模式(Hs）**（3.4MHz）、
- **超高速模式(UFm)**（5MHz）。

注：基于IIC是Master与Slave模式，所以两者间的通信要保持时钟频率的一致。IIC是半双工。

## 2、 IIC应用

       I²C适用于外围设备，其简单性和低制造成本比速度更重要。I²C总线的常见应用包括：

- 通过小型ROM配置表描述可连接设备，以实现“ [即插即用](https://en.wikipedia.org/wiki/Plug_and_play) ”操作，例如：

1. [双列直插式内存模块](https://en.wikipedia.org/wiki/Dual_in-line_memory_module)（DIMM）上的[串行存在检测](https://en.wikipedia.org/wiki/Serial_Presence_Detect)（SPD）EEPROM
2. 通过[VGA](https://en.wikipedia.org/wiki/VGA)，[DVI](https://en.wikipedia.org/wiki/DVI)和[HDMI](https://en.wikipedia.org/wiki/HDMI)连接器为显示器提供[扩展显示识别数据](https://en.wikipedia.org/wiki/Extended_Display_Identification_Data)（EDID）。

- 通过[SMBus](https://en.wikipedia.org/wiki/SMBus)对PC系统进行系统管理;

1. SMBus引脚分配在[常规PCI](https://en.wikipedia.org/wiki/Conventional_PCI)和[PCI Express](https://en.wikipedia.org/wiki/PCI_Express)连接器中。

- 访问保持用户设置[的实时时钟](https://en.wikipedia.org/wiki/Real-time_clock)和[NVRAM](https://en.wikipedia.org/wiki/NVRAM)芯片。
- 访问低速[DAC](https://en.wikipedia.org/wiki/Digital-to-analog_converter)和[ADC](https://en.wikipedia.org/wiki/Analog-to-digital_converter)。
- 更改显示器中的对比度，色调和色彩平衡设置（通过[显示数据通道](https://en.wikipedia.org/wiki/Display_Data_Channel)）。
- 改变智能扬声器的音量。
- 控制小型（例如[功能手机](https://en.wikipedia.org/wiki/Feature_phone)）[OLED](https://en.wikipedia.org/wiki/Organic_light-emitting_diode)或[LCD](https://en.wikipedia.org/wiki/Liquid_crystal_display)显示器。
- 读取硬件监视器和诊断传感器，例如风扇的速度。
- 打开和关闭系统组件的电源

## 3、IIC协议

I2C协议把传输的消息分为两种类型的帧：

**地址帧** —— 用于master指明消息发往哪个slave；

**数据帧(单个或者连续）** —— 由master发往slave的数据（或由slave发往master），每一帧是8-bit的数据。

通常我们所说的IIC读写是相对于Master来说的。

SCL变为低电平后，数据置于SDA线上，并在SCL线变为高电平后进行采样。时钟边沿和数据读/写之间的时间由总线上的器件定义，并且在芯片与芯片之间会有所不同。

下图描述的是一个IIC完整时序图，从左往右依次看，大致总结为两类：


**IIC写寄存器的标准流程**：
1. Master发起START
2. Master发送I2C addr（7bit）和w操作0（1bit），等待ACK
3. Slave发送ACK
4. Master发送reg addr（8bit），等待ACK
5. Slave发送ACK
6. Master发送data（8bit），即要写入寄存器中的数据，等待ACK
7. Slave发送ACK第6步和第7步可以重复多次，即顺序写多个寄存器
8. Master发起STOP

**IIC读寄存器流程：**

1. Master发送I2Caddr（7bit）和 W操作1（1bit），等待ACK
2. Slave发送ACK
3. Master发送reg addr（8bit），等待ACK
4. Slave发送ACK
5. Master发起START
6. Master发送I2C addr（7bit）和 R操作1（1bit），等待ACK
7. Slave发送ACK
8. Slave发送data（8bit），即寄存器里的值
9. Master发送ACK
10. 第8步和第9步可以重复多次，即顺序读多个寄存器

![https://i-blog.csdnimg.cn/blog_migrate/b60cd4d96427ed1add73f49473daca3b.png](https://i-blog.csdnimg.cn/blog_migrate/b60cd4d96427ed1add73f49473daca3b.png)

下面会详细这些流程：

### 3.1 开始条件（Start Condition）

要启动地址帧，Master将SCL保持为高电平并将SDA拉低。也就是说，开始条件表现为：**当SCL为高电平时，SDA线上的高电平到低电平的跳变即定义了START条件。这使得所有Slave都注意到传输即将开始。如果两个Master希望一次获得总线的所有权，则无论哪个设备将SDA拉低，第一个将SDA拉低的将获得对总线的控制权。Master可以发出重复启动，启动新的通信序列而不放弃对其他Master的控制; 我们稍后再谈。**

![https://i-blog.csdnimg.cn/blog_migrate/9875837f4394d7ff57784bdd0ac512a0.png](https://i-blog.csdnimg.cn/blog_migrate/9875837f4394d7ff57784bdd0ac512a0.png)

### 3.2 地址帧(Address Frame)

在任何新的通信序列中，地址帧始终是第一个。对于7位地址，地址首先输出最高有效位（MSB），然后是R / W位，指示这是读（1）还是写（0）操作。

帧的第9位是NACK / ACK位。所有帧（数据或地址）都是这种情况。一旦发送帧的前8位，接收设备就可以控制SDA。如果接收设备在第9个时钟脉冲之前没有将SDA线拉低，则可以推断出接收设备要么没有接收到数据，要么不知道如何解析消息。在这种情况下，则由master来决定如何处理（stop或repeated start condition），也就是代码中等待超时需要做什么处理。

![](https://i-blog.csdnimg.cn/blog_migrate/75037e9328e3beecaa26a70d7700cc5c.png)

### 3.3 数据帧(Data Frame)

在发送地址帧之后，可以开始传输数据。Master将以规则的间隔继续生成时钟脉冲，数据将由Master或Slave置于SDA上，具体取决于R / W位是否指示读或写操作。数据帧的数量是任意的，并且大多数从器件将自动递增内部寄存器，这意味着后续读取或写入将来自下一个寄存器。

#### 3.3.1 写一个寄存器：

![](http://img609.ph.126.net/j7OZijBSkop1sPycnNnBfQ==/1892919218380911741.jpg)

#### 3.3.2 写多个寄存器：

![http://img535.ph.126.net/j7w9Dcj4sYiPaZA5jV1Emg==/1297318167660661668.jpg](http://img535.ph.126.net/j7w9Dcj4sYiPaZA5jV1Emg==/1297318167660661668.jpg)

#### 3.3.3 读一个寄存器：

图片缺失

#### 3.3.4读多个寄存器：

![http://img611.ph.126.net/L9QOsROhgTgCezJCVcQvRQ==/1669991036826428611.jpg](http://img611.ph.126.net/L9QOsROhgTgCezJCVcQvRQ==/1669991036826428611.jpg)

#### 3.4 停止条件(Stop Condition)

一旦发送了所有数据帧，主设备将生成停止条件。停止条件由SCL上0-> 1转换后 SDA上的0-> 1（低到高）转换定义，SCL保持高电平。在正常的数据写操作时，SDA上的值应该不会当SCL为高电平改变，以避免错误的停止条件。图如3.1小节所示。

## 4、IIC协议的高级特性

### 4.1 10-bit地址

在10-bit地址的I2C系统中，需要两个帧来传输slave的地址。第一个帧的前5个bit固定为b11110，后接slave地址的高2位，第8位仍然是R/W位，接着是一个ACK位，由于系统中可能有多个10-bit slave设备地址的高2bit相同，因此这个ACK可能由多有slave设备设置。第二个帧紧接着第一帧发送，包含slave地址的低8位（7:0），接着该地址的slave回复一个ACK（或NACK）。

注意：10-bit地址的设备和7-bit地址的设备在一个系统中是可以并存的，因为7-bit地址的高5位不可能是b11110。实际上对于7-bit的从设备地址，合法范围为b0001XXX-b1110XXX，’X’表示任意值，因此该类型地址最多有112个（其他为保留地址[1]）。

        两个地址帧传输完成后，就开始数据帧的传输了，这和7-bit地址中的数据帧传输过程相同。

![https://i-blog.csdnimg.cn/blog_migrate/a579a1701d7a927c5d351eac41c733cb.png](https://i-blog.csdnimg.cn/blog_migrate/a579a1701d7a927c5d351eac41c733cb.png)

### 4.2 重复开始条件（repeated start condition）

有时master需要在一次通信中进行多次消息交换（例如与不同的slave传输消息，或切换读写操作），并且期间不希望被其他master干扰，这时可以使用“重复开始条件”

在一次通信中，master可以产生多次start condition，来完成多次消息交换，最后再产生一个stop condition结束整个通信过程。由于期间没有stop condition，因此master一直占用总线，其他master无法切入。

为了产生一个重复的开始条件，SDA在SCL低电平时拉高，然后SCL拉高。接着master就可以产生一个开始条件继续新的消息传输（按照正常的7-bit/10-bit地址传输时序）。重复开始条件的传输时序如下图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/4e14ebd00ffe62301311c9056483e86e.png)

### 4.3 时钟拉伸

有时，低速slave可能由于上一个请求还没处理完，尚无法继续接收master的后续请求，即master的数据传输速率超过了slave的处理能力。这种情况下，slave可以进行时钟拉伸来要求master暂停传输数据。

通常时钟都是由master提供的，slave只是在SDA上放数据或读数据。而时钟拉伸则是slave在master释放SCL后，将SCL主动拉低并保持，此时要求master停止在SCL上产生脉冲以及在SDA上发送数据，直到slave释放SCL（SCL为高电平）。之后，master便可以继续正常的数据传输了。可见时钟拉伸实际上是利用了时钟同步的机制（见下文），只是时钟由slave产生。

如果系统中存在这种低速slave并且slave实现了clock stretching，则master必须实现为能够处理这种情况，实际上大部分slave设备中不包含SCL驱动器的，因此无法拉伸时钟。

       所以更完整的I2C数据传输时序图为：

![](https://i-blog.csdnimg.cn/blog_migrate/9e6a3b8f97725abec114da8530040a57.png)

### 4.4 时钟同步和仲裁

如果两个master都想在同一条空闲总线上传输，此时必须能够使用某种机制来选择将总线控制权交给哪个master，这是通过时钟同步和仲裁来完成的，而被迫让出控制权的master则需要等待总线空闲后再继续传输。在单一master的系统上无需实现时钟同步和仲裁。

### 4.5时钟同步

时钟同步是通过I2C接口和SCL之间的线“与”（wired-AND）来完成的，即如果有多个master同时产生时钟，那么只有所有master都发送高电平时，SCL上才表现为高电平，否则SCL都表现为低电平。

### 4.6总线仲裁

总线仲裁和时钟同步类似，当所有master在SDA上都写1时，SDA的数据才是1，只要有一个master写0，那此时SDA上的数据就是0。一个master每发送一个bit数据，在SCL处于高电平时，就检查看SDA的电平是否和发送的数据一致，如果不一致，这个master便知道自己输掉仲裁，然后停止向SDA写数据。也就是说，如果master一直检查到总线上数据和自己发送的数据一致，则继续传输，这样在仲裁过程中就保证了赢得仲裁的master不会丢失数据。

输掉仲裁的master在检测到自己输了之后也不再产生时钟脉冲，并且要在总线空闲时才能重新传输。

仲裁的过程可能要经过多个bit的发送和检查，实际上两个master如果发送的时序和数据完全一样，则两个master都能正常完成整个的数据传输。

维基百科参考代码：

```c
// Hardware-specific support functions that MUST be customized:
#define I2CSPEED 100
void I2C_delay(void);
bool read_SCL(void);  // Return current level of SCL line, 0 or 1
bool read_SDA(void);  // Return current level of SDA line, 0 or 1
void set_SCL(void);   // Do not drive SCL (set pin high-impedance)
void clear_SCL(void); // Actively drive SCL signal low
void set_SDA(void);   // Do not drive SDA (set pin high-impedance)
void clear_SDA(void); // Actively drive SDA signal low
void arbitration_lost(void);
 
bool started = false; // global data

void i2c_start_cond(void) 
{
  if (started) 
  { 
    // if started, do a restart condition
    // set SDA to 1
    set_SDA();
    I2C_delay();
    set_SCL();
    while (read_SCL() == 0) { // Clock stretching
      // You should add timeout to this loop
    }
 
    // Repeated start setup time, minimum 4.7us
    I2C_delay();
  }
 
  if (read_SDA() == 0) {
    arbitration_lost();
  }
 
  // SCL is high, set SDA from 1 to 0.
  clear_SDA();
  I2C_delay();
  clear_SCL();
  started = true;
}
 
void i2c_stop_cond(void) {
  // set SDA to 0
  clear_SDA();
  I2C_delay();
 
  set_SCL();
  // Clock stretching
  while (read_SCL() == 0) {
    // add timeout to this loop.
  }
 
  // Stop bit setup time, minimum 4us
  I2C_delay();
 
  // SCL is high, set SDA from 0 to 1
  set_SDA();
  I2C_delay();
 
  if (read_SDA() == 0) {
    arbitration_lost();
  }
 
  started = false;
}
 
// Write a bit to I2C bus
void i2c_write_bit(bool bit) {
  if (bit) {
    set_SDA();
  } else {
    clear_SDA();
  }
 
  // SDA change propagation delay
  I2C_delay();
 
  // Set SCL high to indicate a new valid SDA value is available
  set_SCL();
 
  // Wait for SDA value to be read by slave, minimum of 4us for standard mode
  I2C_delay();
 
  while (read_SCL() == 0) { // Clock stretching
    // You should add timeout to this loop
  }
 
  // SCL is high, now data is valid
  // If SDA is high, check that nobody else is driving SDA
  if (bit && (read_SDA() == 0)) {
    arbitration_lost();
  }
 
  // Clear the SCL to low in preparation for next change
  clear_SCL();
}
 
// Read a bit from I2C bus
bool i2c_read_bit(void) {
  bool bit;
 
  // Let the slave drive data
  set_SDA();
 
  // Wait for SDA value to be written by slave, minimum of 4us for standard mode
  I2C_delay();
 
  // Set SCL high to indicate a new valid SDA value is available
  set_SCL();
 
  while (read_SCL() == 0) { // Clock stretching
    // You should add timeout to this loop
  }
 
  // Wait for SDA value to be written by slave, minimum of 4us for standard mode
  I2C_delay();
 
  // SCL is high, read out bit
  bit = read_SDA();
 
  // Set SCL low in preparation for next operation
  clear_SCL();
 
  return bit;
}
 
// Write a byte to I2C bus. Return 0 if ack by the slave.
bool i2c_write_byte(bool send_start,
                    bool send_stop,
                    unsigned char byte) {
  unsigned bit;
  bool     nack;
 
  if (send_start) {
    i2c_start_cond();
  }
 
  for (bit = 0; bit < 8; ++bit) {
    i2c_write_bit((byte & 0x80) != 0);
    byte <<= 1;
  }
 
  nack = i2c_read_bit();
 
  if (send_stop) {
    i2c_stop_cond();
  }
 
  return nack;
}
 
// Read a byte from I2C bus
unsigned char i2c_read_byte(bool nack, bool send_stop) {
  unsigned char byte = 0;
  unsigned char bit;
 
  for (bit = 0; bit < 8; ++bit) {
    byte = (byte << 1) | i2c_read_bit();
  }
 
  i2c_write_bit(nack);
 
  if (send_stop) {
    i2c_stop_cond();
  }
 
  return byte;
}
 
void I2C_delay(void) { 
  volatile int v;
  int i;
 
  for (i = 0; i < I2CSPEED / 2; ++i) {
    v;
  }
}
```


