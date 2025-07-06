目录

- [前言](https://www.cnblogs.com/zjutlitao/p/14353305.html#%E5%89%8D%E8%A8%80)
- [1、芯片先关信息](https://www.cnblogs.com/zjutlitao/p/14353305.html#1%E8%8A%AF%E7%89%87%E5%85%88%E5%85%B3%E4%BF%A1%E6%81%AF)
- [2、原理图介绍](https://www.cnblogs.com/zjutlitao/p/14353305.html#2%E5%8E%9F%E7%90%86%E5%9B%BE%E4%BB%8B%E7%BB%8D)
    - [2.1 供电电路](https://www.cnblogs.com/zjutlitao/p/14353305.html#21-%E4%BE%9B%E7%94%B5%E7%94%B5%E8%B7%AF)
    - [2.2 串口电路](https://www.cnblogs.com/zjutlitao/p/14353305.html#22-%E4%B8%B2%E5%8F%A3%E7%94%B5%E8%B7%AF)
    - [2.3 自动烧写电路](https://www.cnblogs.com/zjutlitao/p/14353305.html#23-%E8%87%AA%E5%8A%A8%E7%83%A7%E5%86%99%E7%94%B5%E8%B7%AF)
- [3、PCB 效果展示](https://www.cnblogs.com/zjutlitao/p/14353305.html#3pcb-%E6%95%88%E6%9E%9C%E5%B1%95%E7%A4%BA)
- [附录](https://www.cnblogs.com/zjutlitao/p/14353305.html#%E9%99%84%E5%BD%95)

  

### 前言

ESP8266 是乐鑫公司面向物联网应用的高性价比、高度集成的 WiFi MCU。乐鑫靠这颗芯片扭转了 WiFi SOC 的市场格局，甚至加速了国内智能家居产业的爆发。也因此乐鑫上市科创板受投资者看好，目前总市值达106.04亿人民币（最近一年下跌，购买需谨慎）。本文介绍如何用 KiCad 设计一个 ESP8266 最小开发板。

  

### 1、芯片先关信息

- ESP8266EX 集成了 32 位 Tensilica 处理器、标准数字外设接口、天线开关、射频 balun、功率放大器、低噪放大器、过滤器和电源管理模块等，仅需很少的外围电路，可将所占 PCB 空间降低。
- ESP8266EX 专为移动设备、可穿戴电子产品和物联网应用而设计，通过多项专有技术实现了超低功耗。ESP8266EX 具有的省电模式适用于各种低功耗应用场景。
- ESP8266EX 内置超低功耗 Tensilica L106 32 位 RISC 处理器，CPU 时钟速度最高可达 160 MHz，支持实时操作系统 (RTOS) 和 Wi-Fi 协议栈，可将高达 80% 的处理能力留给应用编程和开发。

  

![](https://tuchuang.beautifulzzzz.com:3000/?path=/3e/27948b76e15e83ce8da4c48b2375a8.png)

  

### 2、原理图介绍

我们这里直接采用 ESP-12F 模块来设计开发板，会简单不少，原理图如下：

![](https://tuchuang.beautifulzzzz.com:3000/?path=/51/66775ec239d5f2cc18fa381a44c9f9.png)

  

#### 2.1 供电电路

供电采用 ASM1117-3.3，能够将USB的 5V 转 3.3V。除此之外，我还用了一个 ASM1117-5.0 来产生 5V 的稳压，供其他外围电路使用（如舵机、马达等）。该芯片的参数如下：

![](https://tuchuang.beautifulzzzz.com:3000/?path=/92/76106a15332c28c6f3a8ef8a424aa9.png)

常用封装：

![](https://tuchuang.beautifulzzzz.com:3000/?path=/df/4ea49a43d2c9327dd411286e369a2a.png)

  

#### 2.2 串口电路

ESP8266 烧写和调试一般都是用串口的，因此我们开发板上需要集成一个串口电路，选择一颗比较便宜的：CH340。其典型电路：

![](https://tuchuang.beautifulzzzz.com:3000/?path=/4e/c9426eee7d66d7ee7615ea7340decb.png)

典型封装为：SSOP-20

![](https://tuchuang.beautifulzzzz.com:3000/?path=/e8/44e5be1aa3079c7ecb77813d9c33c6.png)

我们使用的电路没有那么复杂，只要电源部分加个滤波，RX 和 TX 各串一个470R 的电阻（这颗芯片偏大，还有更小一些的国产串口芯片，也非常好用）。

  

#### 2.3 自动烧写电路

ESP8266工作模式

- 下载模式：芯⽚启动时，若 IO0 为低电平，芯⽚会进⼊下载模式；
- 运⾏模式：芯⽚启动时，若 IO0 为⾼电平，芯⽚会进⼊运⾏模式；

![](https://tuchuang.beautifulzzzz.com:3000/?path=/9d/e061c27b50f749240939fe9f59013a.png)

上图的逻辑关系如下：

- DTR = 0，RTS = 0，此时Q1截止，Q2截止，EN = 1，IO0 = 1；
- DTR = 0，RTS = 1，此时Q1截止，Q2导通，EN = 1，IO0 = DTR = 0；
- DTR = 1，RTS = 0，此时Q1导通，Q2截止，EN = RTS = 0，IO0 = 1；
- DTR = 1，RTS = 1，此时Q1截止，Q2截止，EN = 1，IO0 = 1；


显然，这种逻辑关系下 EN 和 IO0 不可能同时为 0  
然而，ESP8266 进入下载模式却需要如下条件：

- EN = 0，IO0 = 0，ESP8266 芯片掉电复位；
- EN = 1，IO0 = 0，保持 IO0 为低电平重新上电

此时要看下 esp8266 的下载烧录脚本(esptool.py)：

```python
def _connect_attempt(self, mode='default_reset', esp32r0_delay=False):
        """ A single connection attempt, with esp32r0 workaround options """
        # esp32r0_delay is a workaround for bugs with the most common auto reset
        # circuit and Windows, if the EN pin on the dev board does not have
        # enough capacitance.
        #
        # Newer dev boards shouldn't have this problem (higher value capacitor
        # on the EN pin), and ESP32 revision 1 can't use this workaround as it
        # relies on a silicon bug.
        #
        # Details: https://github.com/espressif/esptool/issues/136
        last_error = None

        # If we're doing no_sync, we're likely communicating as a pass through
        # with an intermediate device to the ESP32
        if mode == "no_reset_no_sync":
            return last_error

        # issue reset-to-bootloader:
        # RTS = either CH_PD/EN or nRESET (both active low = chip in reset
        # DTR = GPIO0 (active low = boot to flasher)
        #
        # DTR & RTS are active low signals,
        # ie True = pin @ 0V, False = pin @ VCC.
        if mode != 'no_reset':
            self._setDTR(False)  # IO0=HIGH
            self._setRTS(True)   # EN=LOW, chip in reset
            time.sleep(0.1)
            if esp32r0_delay:
                # Some chips are more likely to trigger the esp32r0
                # watchdog reset silicon bug if they're held with EN=LOW
                # for a longer period
                time.sleep(1.2)
            self._setDTR(True)   # IO0=LOW
            self._setRTS(False)  # EN=HIGH, chip out of reset
            if esp32r0_delay:
                # Sleep longer after reset.
                # This workaround only works on revision 0 ESP32 chips,
                # it exploits a silicon bug spurious watchdog reset.
                time.sleep(0.4)  # allow watchdog reset to occur
            time.sleep(0.05)
            self._setDTR(False)  # IO0=HIGH, done

        for _ in range(5):
            try:
                self.flush_input()
                self._port.flushOutput()
                self.sync()
                return None
            except FatalError as e:
                if esp32r0_delay:
                    print('_', end='')
                else:
                    print('.', end='')
                sys.stdout.flush()
                time.sleep(0.05)
                last_error = e
        return last_error
```

其中：

- 利用 RTS 控制 EN 或 nRST，因为它们都是低电平触发芯片复位；
- 利用 DTR 控制 IO0，低电平启动则进入下载模式；

```sql
# ie True = pin @ 0V, False = pin @ VCC.
```

注意，此处 True 为低电平，False 为高电平  
程序解析如下：

```python
self._setDTR(False)  # IO0=HIGH
self._setRTS(True)   # EN=LOW, chip in reset
```

.  
**设置 DTR = 1，RTS = 0，此时 Q1 导通，Q2 截止，EN = RTS = 0，IO0 = 1，芯片掉电复位；**

```css
time.sleep(0.1)
```

延时 100ms，为了确保 EN 为低电平，因为 EN 附近有一个 RC 电路，充放电都是需要时间的。

![](https://tuchuang.beautifulzzzz.com:3000/?path=/70/aaa3a47d9a440c6e6c44c75652e7f0.png)

例如低电平为 0.25VCC，则由高电平放电至低电平需要的时间可按如下公式计算：

![](https://tuchuang.beautifulzzzz.com:3000/?path=/86/3f52f6dc1f89d05ff2fabe90b380e0.png)

此处，t ≈ 0.29ms，延时 100ms 绰绰有余

```language
self._setDTR(True)   # IO0=LOW
self._setRTS(False)  # EN=HIGH, chip out of reset
```

.  
**设置 DTR = 0，RTS = 1，此时 Q1 截止，Q2 导通，EN = 1，IO0 = 0，芯片重新上电，由于 IO0 为低电平，芯片进入下载模式；**

```css
time.sleep(0.05)
```

延时 50ms，为了确保 EN 为高电平:(高电平认为 0.75V，用上面公式计算，t ≈ 1.39ms，延时 50ms 绰绰有余)

```language
self._setDTR(False)  # IO0=HIGH, done
```

设置 DTR = 1，RTS = 1，此时 Q1 导通，Q2 导通，EN = 1，IO0 = 1，确保下载完成后再复位芯片正常运行。  
补充一下，不点击下载按钮的话，实际测试 DTR 和 RTS 均为高电平，也就是说不会影响 ESP8266 芯片的正常运行。

  

### 3、PCB 效果展示

![](https://tuchuang.beautifulzzzz.com:3000/?path=/4b/1ee6ee382218290b4f5231a96da054.png)

![](https://tuchuang.beautifulzzzz.com:3000/?path=/6a/9c6b3bd522028aa98055d8cf65af73.png)

  

### 附录

[[1]. 乐鑫官网](https://www.espressif.com/zh-hans/products/socs/esp8266)  
[[2]. CSDN ESP8266 自动烧录原理分析](https://blog.csdn.net/wutongpro/article/details/109101063)