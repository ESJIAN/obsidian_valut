---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
温
度
物
理
量 ^volXHOBv

0℃ ^PlnW9Kwk

200℃ ^8fZpPMJP

传
感
器
输
出
电
流
信
号 ^xaOomhSp

20ma ^si0lf42K

4ma ^tnM2DQM2

800 ^mG6YZaIF

4000 ^oTQDImeL

P
L
C
模
拟
量
输
入
通
道
对
应
的
数
字
量 ^G9yG46tX

首先第一条要求：量程的首末得对齐
    最低点对齐：
        1. 温度物理量的最低点0℃对齐传感器输出电流信号的最低点4ma
        2. 传感器输出电流信号的最低点4ma对齐PLC模拟量输入通道对应的数字量最低点800
    最高点对齐：
        1. 温度物理量的最高点200℃对齐传感器输出电流信号的最高点20ma
        2. 传感器输出电流信号的最高点20ma对齐PLC模拟量输入通道对应的数字量最高点4000

然后就是第二条要求：求解线性映射关系 ^NgvwHBQv

映射f1 ^YF5D5dYg

映射f2 ^QiNYV9im

映射f3 ^LXfwift1

映射f3 ^yi55S2kQ

%%
## Drawing
```compressed-json
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

ggAA
```
%%