序：

OSI参考模型对通信中必要的功能做了很好的归纳。[网络工程师](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E7%BD%91%E7%BB%9C%E5%B7%A5%E7%A8%8B%E5%B8%88&zhida_source=entity)在讨论相关问题时也经常以OSI参考模型的分层为原型。对于[计算机网络](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C&zhida_source=entity)的初学者，学习OSI参考模型可以说是通往成功的第一步。

许多[通信协议](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E9%80%9A%E4%BF%A1%E5%8D%8F%E8%AE%AE&zhida_source=entity)，都对应了OSI参考模型7个分层中的某层。通过这一点，可以大致了解该协议在整个通信功能中的位置和地位。

不过，OSI[参考模型](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=5&q=%E5%8F%82%E8%80%83%E6%A8%A1%E5%9E%8B&zhida_source=entity)终究是个“模型”，它也只是对各层的作用做了一系列粗略的界定，并没有对协议和接口进行详细的定义。它对学习和设计协议只能起到一个引导的作用。

  

## **一、OSI[七层参考模型](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E4%B8%83%E5%B1%82%E5%8F%82%E8%80%83%E6%A8%A1%E5%9E%8B&zhida_source=entity)**

![](https://pic1.zhimg.com/80/v2-62ebb5893761668c8953599ca261ed38_720w.webp)

**0.特点**

- OSI模型每层都有自己的功能集；
- 层与层之间相互独立又相互依靠；
- 上层依赖于下层，下层为上层提供服务。

  

**1.应用层**

![](https://pica.zhimg.com/80/v2-667ca720e0832ddcd7d46288b76a2916_720w.webp)

**1.1功能：应用层是为应用程序提供服务并规定应用程序中通信相关的细节。如：文件传输（ftp）、电子邮件（pop3）、远程登陆（telnet）等协议

**1.2常见协议：http(80)、ftp(20/21)、smtp(25)、pop3(110)、[telnet](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=2&q=telnet&zhida_source=entity)(23)、dns(53)【数字为协议的端口号】

  

**2.表示层**

![](https://pic4.zhimg.com/80/v2-f0f64ebfe539a76ac61a93ba22f90f75_720w.webp)

**2.1作用：将应用处理的信息转换为合适网络传输的格式，或将下一层的数据转换为上层能处理的格式。因此它主要负责数据格式的转换。具体来说，就是将设备固有的数据格式转换为[网络标准](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E7%BD%91%E7%BB%9C%E6%A0%87%E5%87%86&zhida_source=entity)传输格式，因为不同设备对同一比特流解读的结果可能会不同。

**2.2比如：**

- 数据的解码和编码，
- 数据的加密和解密，
- 数据的压缩和[解压缩](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E8%A7%A3%E5%8E%8B%E7%BC%A9&zhida_source=entity)。

  

**3.[会话层](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E4%BC%9A%E8%AF%9D%E5%B1%82&zhida_source=entity)**

![](https://picx.zhimg.com/80/v2-c6696e464363540ba26d1a0708162f93_720w.webp)

**3.1作用：**负责建立和断开连接（数据流动的逻辑链路），以及数据的分割等数据传输相关的管理。

**3.2功能：**对话控制，同步。

  

**4.传输层**

![](https://pica.zhimg.com/80/v2-6f8dcfa3164494746aaeadb8df3e187a_720w.webp)

**4.1作用：**起着可靠传输的作用。只能在通信双方节点上进行处理，而无需在路由器上处理。

**4.2功能：**

- 服务点编址、
- 分段与重组、
- [连接控制](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E8%BF%9E%E6%8E%A5%E6%8E%A7%E5%88%B6&zhida_source=entity)、
- [流量控制](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E6%B5%81%E9%87%8F%E6%8E%A7%E5%88%B6&zhida_source=entity)、
- 差错控制。

  

**5.网络层**

![](https://pic4.zhimg.com/80/v2-5a1f0b2c110f2ee7a5854a8b7990d851_720w.webp)

**5.1作用：**将数据传输到目标地址。目标地址可以是多个网络通过路由器连接而成的某个地址。

**5.2功能：**–为[网络设备](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E7%BD%91%E7%BB%9C%E8%AE%BE%E5%A4%87&zhida_source=entity)提供[逻辑地址](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E9%80%BB%E8%BE%91%E5%9C%B0%E5%9D%80&zhida_source=entity)，–进行[路由选择](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E8%B7%AF%E7%94%B1%E9%80%89%E6%8B%A9&zhida_source=entity)、分组转发

  

**6.[数据链路层](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E6%95%B0%E6%8D%AE%E9%93%BE%E8%B7%AF%E5%B1%82&zhida_source=entity)**

![](https://picx.zhimg.com/80/v2-14e5c336a41199688021bf4be2678761_720w.webp)

**6.1作用：**负责物理层面上互连的节点之间的通信传输。将0、1序列划分成具有意义的数据帧传输给对端。

**6.2功能：**

- 组帧、
- 物理编址、
- 流量控制、
- 差错控制、
- [接入控制](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E6%8E%A5%E5%85%A5%E6%8E%A7%E5%88%B6&zhida_source=entity)。

  

**7.物理层**

![](https://pica.zhimg.com/80/v2-6b6fd13a166762ec254ed5a991cc78ac_720w.webp)

**7.1作用：**负责0、1比特流与电压高低、光的灭闪之间的转换。

**7.2功能:**

- 定义接口和媒体的物理特性,
- 定义比特的表示、数据传输速率、
- 信号的传输模（单工、半双 工、[全双工](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E5%85%A8%E5%8F%8C%E5%B7%A5&zhida_source=entity)）,
- 定义网络物理拓扑（网状、星型、环型、总线型等拓扑）

  

## **二、七层通信**

  

**0.各层之间的联系**

![](https://pic2.zhimg.com/80/v2-5cc30c96fd5aac1370ba3f31aa29546d_720w.webp)

从大体上将，OST可以分成两个部分，一个是以上三层为主体的面向用户应用的模块（在TCP/IP五层中被统一成应用层）；一个是以下四层为主题的面向数据传输的模块。

  

**1.七层通信**

![](https://pic3.zhimg.com/80/v2-cf9b427bf4421b9e6a2d8bb92d772dac_720w.webp)

如图所示，数据的传输过程主要依靠下四层的模块进行，依靠网络层对数据在漫长距离的传输中（经过很多个路由器、交换机）的寻址和选路，也在依靠传输层和数据链路层来实现对需要传输的数据准确无误地传输到对端。

就以下四层实现的功能来讲，就相当于你把U盘插入并拷贝读取电脑A上的数据，然后你手工地把U盘拔出，并插入电脑B中，读取U盘中数据。核心就是安全、准确的传输数据。

上三层主要的作用就是处理数据，将[数据处理](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86&zhida_source=entity)成你能理解的东西。

  

**2.数据传输（封装）**

封装——每一层都把上层的[协议包](https://zhida.zhihu.com/search?content_id=4910367&content_type=Article&match_order=1&q=%E5%8D%8F%E8%AE%AE%E5%8C%85&zhida_source=entity)当成数据部分，加上自己的协议头部，组成自己的协议包

![](https://pica.zhimg.com/80/v2-54a209f5fc0d72c9e737343e29ebc080_720w.webp)

封装问题对于基础弱的同学有点难，这次这篇文章暂时略过

![](https://pica.zhimg.com/80/v2-9dfd0ac3afafa511bc704c25aaaf6af6_720w.webp)

同上、略过