#### 文章目录

- [深度学习入门之PyTorch](https://blog.csdn.net/qq_43701912/article/details/109539727#PyTorch_4)
- - [第一章 深度学习介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#__6)
    - - [1.1 人工智能](https://blog.csdn.net/qq_43701912/article/details/109539727#11__8)
        - [1.2 数据挖掘，机器学习和深度学习](https://blog.csdn.net/qq_43701912/article/details/109539727#12__16)
        - - [1.2.1 数据挖掘](https://blog.csdn.net/qq_43701912/article/details/109539727#121__18)
            - [1.2.2 机器学习](https://blog.csdn.net/qq_43701912/article/details/109539727#122__22)
            - [1.2.3 深度学习](https://blog.csdn.net/qq_43701912/article/details/109539727#123__32)
    - [第二章 深度学习框架](https://blog.csdn.net/qq_43701912/article/details/109539727#__37)
    - - [2.1 深度学习框架介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#21__39)
        - [2.2 PyTorch介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#22_PyTorch_49)
        - - [2.2.1 什么是PyTorch](https://blog.csdn.net/qq_43701912/article/details/109539727#221_PyTorch_51)
            - [2.2.2 为什么使用PyTorch](https://blog.csdn.net/qq_43701912/article/details/109539727#222_PyTorch_55)
        - [2.3 配置PyTorch深度学习环境](https://blog.csdn.net/qq_43701912/article/details/109539727#23_PyTorch_62)
        - - [2.3.1 操作系统](https://blog.csdn.net/qq_43701912/article/details/109539727#231__64)
            - [2.3.2 Python开发环境的安装](https://blog.csdn.net/qq_43701912/article/details/109539727#232_Python_68)
            - [2.3.3 PyTorch安装](https://blog.csdn.net/qq_43701912/article/details/109539727#233_PyTorch_72)
    - [第三章 多层全连接神经网络](https://blog.csdn.net/qq_43701912/article/details/109539727#__80)
    - - [3.1 PyTorch基础](https://blog.csdn.net/qq_43701912/article/details/109539727#31_PyTorch_82)
        - - [3.1.1 Tensor张量](https://blog.csdn.net/qq_43701912/article/details/109539727#311_Tensor_84)
            - [3.1.2 Variable（变量）](https://blog.csdn.net/qq_43701912/article/details/109539727#312_Variable_285)
            - [3.1.3 Dataset(数据集)](https://blog.csdn.net/qq_43701912/article/details/109539727#313_Dataset_544)
            - [3.1.4 nn.Module(模组)](https://blog.csdn.net/qq_43701912/article/details/109539727#314_nnModule_575)
            - [3.1.5 torch.optim(优化)](https://blog.csdn.net/qq_43701912/article/details/109539727#315_torchoptim_674)
            - [3.1.6 模型的保存和加载](https://blog.csdn.net/qq_43701912/article/details/109539727#316__690)
        - [3.2 线性模型](https://blog.csdn.net/qq_43701912/article/details/109539727#32__710)
        - - [3.2.1 介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#321__712)
            - [3.2.2 一维线性回归](https://blog.csdn.net/qq_43701912/article/details/109539727#322__720)
            - [3.2.3 多维线性回归](https://blog.csdn.net/qq_43701912/article/details/109539727#323__736)
            - [3.2.4 一维线性回归的代码实现](https://blog.csdn.net/qq_43701912/article/details/109539727#324__763)
            - [3.2.5 多项式回归](https://blog.csdn.net/qq_43701912/article/details/109539727#325__825)
        - [3.3 分类问题](https://blog.csdn.net/qq_43701912/article/details/109539727#33__899)
        - - [3.3.1 问题介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#331__901)
            - [3.3.2 Logistic起源](https://blog.csdn.net/qq_43701912/article/details/109539727#332_Logistic_907)
            - [3.3.3 Logistic分布](https://blog.csdn.net/qq_43701912/article/details/109539727#333_Logistic_911)
            - [3.3.4 二分类的Logistic回归](https://blog.csdn.net/qq_43701912/article/details/109539727#334_Logistic_919)
            - [3.3.5 模型的参数估计](https://blog.csdn.net/qq_43701912/article/details/109539727#335__932)
            - [3.3.6 Logistic回归的代码实现](https://blog.csdn.net/qq_43701912/article/details/109539727#336_Logistic_942)
        - [3.4 简单多层全连接前向网络](https://blog.csdn.net/qq_43701912/article/details/109539727#34__1026)
        - - [3.4.1 模拟神经元](https://blog.csdn.net/qq_43701912/article/details/109539727#341__1028)
            - [3.4.2 单层神经网络的分类器](https://blog.csdn.net/qq_43701912/article/details/109539727#342__1032)
            - [3.4.3 激活函数](https://blog.csdn.net/qq_43701912/article/details/109539727#343__1036)
            - [3.4.4 神经网络的结构](https://blog.csdn.net/qq_43701912/article/details/109539727#344__1075)
            - [3.4.5 模型的表示能力与容量](https://blog.csdn.net/qq_43701912/article/details/109539727#345__1081)
        - [3.5 深度学习的基石：反向传播算法](https://blog.csdn.net/qq_43701912/article/details/109539727#35__1088)
        - - [3.5.1 链式法则](https://blog.csdn.net/qq_43701912/article/details/109539727#351__1090)
            - [3.5.2 反向传播算法](https://blog.csdn.net/qq_43701912/article/details/109539727#352__1094)
        - [3.6 各种优化算法的变式](https://blog.csdn.net/qq_43701912/article/details/109539727#36__1100)
        - - [3.6.1 梯度下降法](https://blog.csdn.net/qq_43701912/article/details/109539727#361__1102)
            - [3.6.2 梯度下降法的变式](https://blog.csdn.net/qq_43701912/article/details/109539727#362__1107)
        - [3.7 处理数据和训练模型的技巧](https://blog.csdn.net/qq_43701912/article/details/109539727#37__1130)
        - - [3.7.1 数据预处理](https://blog.csdn.net/qq_43701912/article/details/109539727#371__1132)
            - [3.7.2 权重初始化](https://blog.csdn.net/qq_43701912/article/details/109539727#372__1146)
            - [3.7.3 防止过拟合](https://blog.csdn.net/qq_43701912/article/details/109539727#373__1160)
        - [3.8 多层全连接神经网络实现MNIST手写数字分类](https://blog.csdn.net/qq_43701912/article/details/109539727#38_MNIST_1165)
    - [第四章 卷积神经网络](https://blog.csdn.net/qq_43701912/article/details/109539727#__1265)
    - - [4.1 主要任务及起源](https://blog.csdn.net/qq_43701912/article/details/109539727#41__1269)
        - [4.2 卷积神经网络的原理和结构](https://blog.csdn.net/qq_43701912/article/details/109539727#42__1273)
        - - [4.2.1 卷积层](https://blog.csdn.net/qq_43701912/article/details/109539727#421__1297)
            - [4.2.2 池化层](https://blog.csdn.net/qq_43701912/article/details/109539727#422__1337)
            - [4.2.3 全连接层](https://blog.csdn.net/qq_43701912/article/details/109539727#423__1349)
            - [4.2.4 卷积神经网络的基本形式](https://blog.csdn.net/qq_43701912/article/details/109539727#424__1353)
        - [4.3 Pytorch卷积模块](https://blog.csdn.net/qq_43701912/article/details/109539727#43_Pytorch_1368)
        - - [4.3.1 卷积层](https://blog.csdn.net/qq_43701912/article/details/109539727#431__1370)
            - [4.3.2 池化层](https://blog.csdn.net/qq_43701912/article/details/109539727#432__1383)
            - [4.3.3 提取层结构](https://blog.csdn.net/qq_43701912/article/details/109539727#433__1442)
            - [4.3.4 提取参数及自定义初始化](https://blog.csdn.net/qq_43701912/article/details/109539727#434__1467)
        - [4.4 卷积神经网络案例分析](https://blog.csdn.net/qq_43701912/article/details/109539727#44__1492)
        - - [4.4.1 LeNet](https://blog.csdn.net/qq_43701912/article/details/109539727#441_LeNet_1494)
            - [4.4.2 AlexNet](https://blog.csdn.net/qq_43701912/article/details/109539727#442_AlexNet_1527)
            - [4.4.3 VGGNet](https://blog.csdn.net/qq_43701912/article/details/109539727#443_VGGNet_1566)
            - [4.4.4 GoogleNet](https://blog.csdn.net/qq_43701912/article/details/109539727#444_GoogleNet_1625)
            - [4.4.5 ResNet](https://blog.csdn.net/qq_43701912/article/details/109539727#445_ResNet_1674)
        - [4.5 再实现MNIST手写数字分类](https://blog.csdn.net/qq_43701912/article/details/109539727#45_MNIST_1688)
        - [4.6 图像增强的方法](https://blog.csdn.net/qq_43701912/article/details/109539727#46__1795)
        - [4.7 实现cifar10分类](https://blog.csdn.net/qq_43701912/article/details/109539727#47_cifar10_1807)
    - [第五章 循环神经网络](https://blog.csdn.net/qq_43701912/article/details/109539727#__2052)
    - - [5.1 循环神经网络](https://blog.csdn.net/qq_43701912/article/details/109539727#51__2056)
        - - [5.1.1 问题介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#511__2064)
            - [5.1.2 循环神经网络的基本结构](https://blog.csdn.net/qq_43701912/article/details/109539727#512__2073)
            - [5.1.3 存在的问题](https://blog.csdn.net/qq_43701912/article/details/109539727#513__2085)
        - [5.2 循环神经网络的变式：LSTM和GRU](https://blog.csdn.net/qq_43701912/article/details/109539727#52_LSTMGRU_2089)
        - - [5.2.1 LSTM](https://blog.csdn.net/qq_43701912/article/details/109539727#521_LSTM_2091)
            - [5.2.2 GRU](https://blog.csdn.net/qq_43701912/article/details/109539727#522_GRU_2097)
            - [5.2.3 收敛性问题](https://blog.csdn.net/qq_43701912/article/details/109539727#523__2101)
        - [5.3 循环神经网络的PyTorch实现](https://blog.csdn.net/qq_43701912/article/details/109539727#53_PyTorch_2105)
        - - [5.3.1 PyTorch的循环网络模块](https://blog.csdn.net/qq_43701912/article/details/109539727#531_PyTorch_2107)
            - [5.3.2 实例介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#532__2172)
        - [5.4 自然语言处理的应用](https://blog.csdn.net/qq_43701912/article/details/109539727#54__2283)
        - - [5.4.1 词嵌入](https://blog.csdn.net/qq_43701912/article/details/109539727#541__2285)
            - [5.4.2 词嵌入的PyTorch实现](https://blog.csdn.net/qq_43701912/article/details/109539727#542_PyTorch_2303)
            - [5.4.3 N Gram模型](https://blog.csdn.net/qq_43701912/article/details/109539727#543_N_Gram_2316)
            - [5.4.4 单词预测的PyTorch实现](https://blog.csdn.net/qq_43701912/article/details/109539727#544_PyTorch_2329)
            - [5.4.5 词性判断](https://blog.csdn.net/qq_43701912/article/details/109539727#545__2428)
            - [5.4.6 词性判断的PyTorch实现](https://blog.csdn.net/qq_43701912/article/details/109539727#546_PyTorch_2438)
        - [5.5 循环神经网络的更多应用](https://blog.csdn.net/qq_43701912/article/details/109539727#55__2546)
        - - [5.5.1 Many to one](https://blog.csdn.net/qq_43701912/article/details/109539727#551_Many_to_one_2548)
            - [5.5.2 Many to Many (shorter)](https://blog.csdn.net/qq_43701912/article/details/109539727#552_Many_to_Many_shorter_2556)
            - [5.5.3 Seq2seq](https://blog.csdn.net/qq_43701912/article/details/109539727#553_Seq2seq_2560)
            - [5.5.4 CNN+RNN](https://blog.csdn.net/qq_43701912/article/details/109539727#554_CNNRNN_2564)
    - [第6章 生成对抗网络](https://blog.csdn.net/qq_43701912/article/details/109539727#6__2568)
    - - [6.1 生成模型](https://blog.csdn.net/qq_43701912/article/details/109539727#61__2572)
        - - [6.1.1 自动编码器](https://blog.csdn.net/qq_43701912/article/details/109539727#611__2578)
            - [6.1.2 变分自动编码器](https://blog.csdn.net/qq_43701912/article/details/109539727#612__2786)
        - [6.2 生成对抗网络](https://blog.csdn.net/qq_43701912/article/details/109539727#62__2937)
        - - [6.2.1 什么是生成对抗网络](https://blog.csdn.net/qq_43701912/article/details/109539727#621__2941)
        - [6.3 Improving GAN](https://blog.csdn.net/qq_43701912/article/details/109539727#63_Improving_GAN_3423)
        - - [6.3.1 Wasserstein GAN](https://blog.csdn.net/qq_43701912/article/details/109539727#631_Wasserstein_GAN_3425)
        - [6.4 应用介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#64__3433)
        - - [6.4.1 Conditional GAN](https://blog.csdn.net/qq_43701912/article/details/109539727#641_Conditional_GAN_3435)
            - [6.4.2 Cycle GAN](https://blog.csdn.net/qq_43701912/article/details/109539727#642_Cycle_GAN_3439)
    - [第七章 深度学习实战](https://blog.csdn.net/qq_43701912/article/details/109539727#__3444)
    - - [7.1 实例一，猫狗大战：运用预训练卷积神经网络进行特征提取与预训](https://blog.csdn.net/qq_43701912/article/details/109539727#71__3446)
        - - [7.1.1 背景介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#711__3448)
            - [7.1.2 原理分析](https://blog.csdn.net/qq_43701912/article/details/109539727#712__3452)
            - [7.1.3 代码实现](https://blog.csdn.net/qq_43701912/article/details/109539727#713__3470)
        - [7.2 实例二，Deep Dream：探索卷积神经网络眼中的世界](https://blog.csdn.net/qq_43701912/article/details/109539727#72_Deep_Dream_3676)
        - - [7.2.1 原理介绍](https://blog.csdn.net/qq_43701912/article/details/109539727#721__3680)
            - [7.2.2 代码实现](https://blog.csdn.net/qq_43701912/article/details/109539727#722__3690)

> 最新内容请关注[我的博客https://blog.justlovesmile.top/](https://blog.justlovesmile.top/)

## [深度学习](https://edu.csdn.net/cloud/sd_summit?utm_source=glcblog&spm=1001.2101.3001.7020)入门之PyTorch

### 第一章 深度学习介绍

#### 1.1 人工智能

1. Artificial Intelligence，人工智能，也称机器智能。
2. 人工智能分为三大类  
    （1）弱人工智能：擅长单方面  
    （2）强人工智能：类似人类等级  
    （3）超人工智能：全方面胜过人类

#### 1.2 数据挖掘，[机器学习](https://edu.csdn.net/cloud/sd_summit?utm_source=glcblog&spm=1001.2101.3001.7020)和深度学习

##### 1.2.1 数据挖掘

KDD（knowledge discovery in database），从数据中获取有意义的信息

##### 1.2.2 机器学习

1. 机器学习是实现人工智能的一种途径，涉及多门学科
2. 大致分为五个大类  
    （1）监督学习：从给定的训练数据集中学习出一个函数，训练集中的目标是由人标注的，常见算法包括回归和分类  
    （2）无监督学习：训练集没有人为标注，常见算法如聚类  
    （3）半监督学习：介于两者之间  
    （4）迁移学习：将已经训练好的模型参数迁移到新的模型来帮助新模型训练数据集  
    （5）增强学习：通过观察周围环境来学习

##### 1.2.3 深度学习

1. 机器学习的一个分支，通过模拟人脑来实现数据特征的提取
2. 常见网络结构：DNN，CNN，RNN，GAN等等

### 第二章 深度学习框架

#### 2.1 深度学习框架介绍

1. Tensorflow  
    Google开源的基于C++开发的数学计算软件
2. Caffe
3. Theano
4. Torch  
    支持动态图
5. MXNet

#### 2.2 PyTorch介绍

##### 2.2.1 什么是PyTorch

[Python](https://so.csdn.net/so/search?q=Python&spm=1001.2101.3001.7020)优先的深度学习框架，支持GPU加速和动态神经网络

##### 2.2.2 为什么使用PyTorch

1.多学习一个框架准没错  
2.PyTorch通过一种反向自动求导的技术，可以让你零延迟地改变神经网络  
3.线性，直观，易于使用  
4.代码简洁直观，底层代码友好

#### 2.3 配置PyTorch深度学习环境

##### 2.3.1 操作系统

Windows，Linux，Mac

##### 2.3.2 Python开发环境的安装

Anaconda

##### 2.3.3 PyTorch安装

官网或者anaconda

CPU或GPU

CUDA，CuDnn

### 第三章 多层全连接神经网络

#### 3.1 PyTorch基础

##### 3.1.1 Tensor张量

Tensor相当于多维的矩阵

Tensor的数据类型有：(32位浮点型)torch.FloatTensor，（64位浮点型）torch.DoubleTensor，（16位整型）torch.ShortTensor,（32位整型）torch.IntTensor，（64位整型）torch.LongTensor

**导入pytorch**

```python
from __future__ import print_function
import torch
```

**创建一个没有初始化的5×3矩阵**

```python
x=torch.empty(5,3)
print(x)
```

**创建一个随机初始化矩阵**

```python
#均匀分布[0,1],rand
x=torch.rand(5,3)
print(x)

#正态分布，randn
x=torch.randn(5,3)
print(x)
```

**构造一个0矩阵，且数据类型为long**

```python
x=torch.zeros(5,3,dtype=torch.long)
print(x)
```

**直接根据数据构造张量**

```python
x=torch.tensor([5.5,3])
print(x)
```

**创建一个全为1的矩阵，且数据类型为double**

```python
x=torch.ones(5,3)
print(x)

x=x.new_ones(5,3,dtype=torch.double)
print(x)
```

**根据已有tensor建立新的tensor，且除非提供新值，将重用所给张量属性**

```python
x=x.new_ones(5,3,dtype=torch.double)
print(x)

x=torch.randn_like(x,dtype=torch.float)
print(x)
```

**获取张量的形状**

```python
print(x.size())
```

> **注意**  
> `torch.Size`本质上还是tuple，所以支持tuple的一切操作

**和numpy的相互转换**

```python
print(x)
numpy_x = x.numpy()
print(numpy_x)
torch_x = torch.from_numpy(numpy_x)
print(torch_x)
```

**绝对值**

```python
a=torch.randn(2,3)
print(a)

b=torch.abs(a)
print(b)
```

**运算**，例如加法

**形式一**

```python
y=torch.rand(5,3)
print(x+y)
```

**形式二**

```python
print(torch.add(x,y))
```

**形式三**

```python
result=torch.empty(5,3)
torch.add(x,y,out=result)
print(result)
```

**形式四**

```python
y.add_(x)
print(y)
```

> **注意：**  
> 任何一个in-place改变张量的操作后面都固定一个_。例如x.copy_(y)、x.t_()将更改x

**剪裁**:如果在上下边界内则不变，否则大于上边界值，则改为上边界值，小于下边界值，则改为下边界值

```python
a=torch.randn(2,3)
print(a)

b=torch.clamp(a,-0.1,0.1)
print(b)
```

**除法**

```python
a=torch.randn(2,3)
b=torch.randn(2,3)
c=torch.div(a,b)
d=torch.div(c,10)
print(a)
print(b)
print(c)
print(d)
```

> **加法**add，**乘积**mul，**除法**div，**求幂**pow，**矩阵乘法**mm，**矩阵向量乘法**mv

**改变张量形状**

```python
x=torch.randn(4,4)
y=x.view(16)
z=x.view(-1,8) # -1将会自动取值
print(x.size(),y.size(),z.size())
```

**对于只含一个元素的tensor，可以使用`.item()`来得到数值**

```python
x=torch.randn(1)
print(x)
print(x.item())
```

**使用GPU**

```python
if torch.cuda.is_available():
    device = torch.device("cuda")
    y = torch.ones_like(x, device=device)
    x = x.to(device)
    z = x+y
    print(z)
    print(z.to("CPU",torch.double))
```

##### 3.1.2 Variable（变量）

**1. Autograd：自动求导**

**创建一个张量并设置requires_grad=True用来追踪其计算历史**

```python
x=torch.ones(2,2,requires_grad=True)
print(x)
```

**对这个张量做一次运算**

```python
y=x+2
print(y)
# y是计算结果，所以他有grad_fn属性
print(y.grad_fn)
# 对y进行更多操作
z=y*y*3
out=z.mean()
print(z,out)
```

.requires_grad_(…) 改变了现有张量的 requires_grad 标志。如果没有指定的话，默认输入的这个标志是 False。

```python
a = torch.randn(2, 2)
a = ((a * 3) / (a - 1))
print(a.requires_grad)
a.requires_grad_(True)
print(a.requires_grad)
b = (a * a).sum()
print(b.grad_fn)
```

**2. 梯度**

```python
x=torch.ones(2,2,requires_grad=True)
y=x+2
z=y*y*3
out=z.mean()
# 现在开始反向传播，因为out是一个标量，则out.backward()和out.backward(torch.tensor(1.))等价
out.backward()
#输出导数d(out)/dx
print(x.grad)
```

即o u t = 1 4 ∑ i z i out=\frac{1}{4}\sum_iz_iout=41​i∑​zi​  
z i = 3 ( x i + 2 ) 2 z_i=3(x_i+2)^2zi​=3(xi​+2)2  
并且z i ∣ x i = 1 = 27 z_i|_{x_i=1}=27zi​∣xi​=1​=27，因此，有  
∂ o u t ∂ x i = 3 2 ( x i + 2 ) \frac{\partial_{out}}{\partial_{x_i}}=\frac{3}{2}(x_i+2)∂xi​​∂out​​=23​(xi​+2)，因此  
∂ o u t ∂ x i ∣ x i = 1 = 9 2 = 4.5 \frac{\partial _ {out}}{\partial_ {x_i}}|_ {x_i=1}=\frac{9}{2}=4.5∂xi​​∂out​​∣xi​=1​=29​=4.5

**雅可比矩阵**

数学上，若有向量值函数y=f(x)，那么y相当于对x的梯度是一个雅可比矩阵  
J = [ ∂ y 1 ∂ x 1 ⋯ ∂ y 1 ∂ x n ⋮ ⋱ ⋮ ∂ y m ∂ x 1 ⋯ ∂ y m ∂ x n ] J=

⎡⎣⎢⎢⎢⎢∂y1∂x1⋮∂ym∂x1⋯⋱⋯∂y1∂xn⋮∂ym∂xn⎤⎦⎥⎥⎥⎥[∂y1∂x1⋯∂y1∂xn⋮⋱⋮∂ym∂x1⋯∂ym∂xn]

J=⎣⎢⎡​∂x1​∂y1​​⋮∂x1​∂ym​​​⋯⋱⋯​∂xn​∂y1​​⋮∂xn​∂ym​​​⎦⎥⎤​  
通常来说，torch.autograd是计算雅可比向量积的一个引擎。也就是说，给定任意向量v，计算乘积v T J v^TJvTJ.如果v恰好是一个标量函数l=g(y)的导数，即v = ( ∂ l ∂ y 1 ⋯ ∂ l ∂ y m T ) v=(\frac{\partial l}{\partial y_1} \cdots \frac{\partial l}{\partial y_m}^T)v=(∂y1​∂l​⋯∂ym​∂l​T)，那么根据链式法则，雅可比向量积应该是l对x的导数  
J T ⋅ v = [ ∂ y 1 ∂ x 1 ⋯ ∂ y m ∂ x 1 ⋮ ⋱ ⋮ ∂ y 1 ∂ x n ⋯ ∂ y m ∂ x n ] [ ∂ l ∂ y 1 ⋯ ∂ l ∂ y m ] = [ ∂ l ∂ x 1 ⋯ ∂ l ∂ x n ] J^T·v=

⎡⎣⎢⎢⎢⎢∂y1∂x1⋮∂y1∂xn⋯⋱⋯∂ym∂x1⋮∂ym∂xn⎤⎦⎥⎥⎥⎥[∂y1∂x1⋯∂ym∂x1⋮⋱⋮∂y1∂xn⋯∂ym∂xn]

⎡⎣⎢⎢⎢∂l∂y1⋯∂l∂ym⎤⎦⎥⎥⎥[∂l∂y1⋯∂l∂ym]

=

⎡⎣⎢⎢∂l∂x1⋯∂l∂xn⎤⎦⎥⎥[∂l∂x1⋯∂l∂xn]

JT⋅v=⎣⎢⎡​∂x1​∂y1​​⋮∂xn​∂y1​​​⋯⋱⋯​∂x1​∂ym​​⋮∂xn​∂ym​​​⎦⎥⎤​⎣⎡​∂y1​∂l​⋯∂ym​∂l​​⎦⎤​=⎣⎡​∂x1​∂l​⋯∂xn​∂l​​⎦⎤​  
(注意：行向量的v T ⋅ J v^T⋅JvT⋅J也可以被视作列向量的J T ⋅ v J^T⋅vJT⋅v)

雅可比向量积的这一特性使得将外部梯度输入到具有非标量输出的模型中变得非常方便。

```python
x=torch.randn(3,requires_grad=True)
y=x*2
while y.data.norm() <1000:
    y=y*2

print(y)
```

在这种情况下，y 不再是标量。torch.autograd 不能直接计算完整的雅可比矩阵，但是如果我们只想要雅可比向量积，只需将这个向量作为参数传给 backward

```python
v = torch.tensor([0.1, 1.0, 0.0001], dtype=torch.float)
y.backward(v)

print(x.grad)
```

也可以通过将代码块包装在 with torch.no_grad(): 中，来阻止autograd跟踪设置了 .requires_grad=True 的张量的历史记录。

```python
print(x.requires_grad)
print((x ** 2).requires_grad)

with torch.no_grad():
    print((x ** 2).requires_grad)
```

**3. Variable**

Variable和Tensor的区别，Variable会被放入计算图中，然后进行前向传播，反向传播，自动求导

Variable是在torch.autograd.Variable中

```python
from torch.autograd import Variable

x=Variable(torch.Tensor([1]),requires_grad=True)
w=Variable(torch.Tensor([2]),requires_grad=True)
b=Variable(torch.Tensor([3]),requires_grad=True)

y=w*x+b

y.backward()

print(x.grad)
print(w.grad)
print(b.grad)
```

**搭建一个简单的神经网络**

```python
batch_n = 100 # 一个批次中输入数据的数量
hidden_layer = 100 # 经过隐藏层后保留的数据特征的个数
input_data = 1000 # 每个数据包含的数据量
output_data = 10 # 每个输出的数据包含的数据量

x=torch.randn(batch_n,input_data) #100*1000
y=torch.randn(batch_n,output_data) #100*10

w1=torch.randn(input_data,hidden_layer) #1000*100
w2=torch.randn(hidden_layer,output_data) # 100*10

epoch_n = 20 #训练的次数
learning_rate = 1e-6 #学习率

for epoch in range(epoch_n):
    h1=x.mm(w1)#100*100
    h1=h1.clamp(min=0) # if x<0 ,x=0
    y_pred=h1.mm(w2) #100*10，前向传播预测结果
    
    loss = (y_pred - y).pow(2).sum() #损失函数，即均方误差
    print("Epoch:{}, Loss:{:.4f}".format(epoch,loss))
    grad_y_pred = 2*(y_pred-y) #dloss/dy
    grad_w2 = h1.t().mm(grad_y_pred) #dloss/dy * dy/dw2
    
    grad_h = grad_y_pred.clone() #复制
    grad_h = grad_h.mm(w2.t()) #dloss/dy * dy/dh1
    grad_h.clamp_(min=0) # if x<0 ,x=0
    grad_w1 = x.t().mm(grad_h) 
    
    w1 -= learning_rate*grad_w1 #梯度下降
    w2 -= learning_rate*grad_w2
```

**使用Variable搭建一个自动计算梯度的神经网络**

```python
from torch.autograd import Variable

batch_n = 100 # 一个批次中输入数据的数量
hidden_layer = 100 # 经过隐藏层后保留的数据特征的个数
input_data = 1000 # 每个数据包含的数据量
output_data = 10 # 每个输出的数据包含的数据量

x=Variable(torch.randn(batch_n,input_data),requires_grad = False) #requires_grad = False不保留梯度
y=Variable(torch.randn(batch_n,output_data),requires_grad = False)
w1=Variable(torch.randn(input_data,hidden_layer),requires_grad = True) #requires_grad = True自动保留梯度
w2=Variable(torch.randn(hidden_layer,output_data),requires_grad = True)

epoch_n = 20
learning_rate = 1e-6

for epoch in range(epoch_n):
    y_pred = x.mm(w1).clamp(min = 0).mm(w2) #y_pred=w2*(w1*x)
    loss = (y_pred-y).pow(2).sum() #损失函数
    print("Epoch:{},Loss:{:.4f}".format(epoch,loss))
    
    loss.backward() #后向传播计算
    
    w1.data -= learning_rate*w1.grad.data
    w2.data -=learning_rate*w2.grad.data
    
    w1.grad.data.zero_() #置0
    w2.grad.data.zero_()
```

**使用nn.Module自定义传播函数来搭建神经网络**

```python
from torch.autograd import Variable

batch_n = 100
hidden_layer = 100
input_data = 1000
output_data = 10

class Model(torch.nn.Module):
    def __init__(self):
        super(Model,self).__init__()
    
    def forward(self,input_n,w1,w2):
        x = torch.mm(input_n,w1)
        x = torch.clamp(x,min=0)
        x = torch.mm(x,w2)
        return x
    
    def backward(self):
        pass
    
model = Model()

x=Variable(torch.randn(batch_n,input_data),requires_grad = False) #requires_grad = False不保留梯度
y=Variable(torch.randn(batch_n,output_data),requires_grad = False)
w1=Variable(torch.randn(input_data,hidden_layer),requires_grad = True) #requires_grad = True自动保留梯度
w2=Variable(torch.randn(hidden_layer,output_data),requires_grad = True)

epoch_n = 20
learning_rate = 1e-6

for epoch in range(epoch_n):
    y_pred = model(x,w1,w2)
    loss = (y_pred-y).pow(2).sum()
    print("Epoch:{},Loss:{:.4f}".format(epoch,loss))
    loss.backward() #后向传播计算
    
    w1.data -= learning_rate*w1.grad.data
    w2.data -=learning_rate*w2.grad.data
    
    w1.grad.data.zero_() #置0
    w2.grad.data.zero_()
```

##### 3.1.3 Dataset(数据集)

torch.utils.data.Dataset是代表这一数据的抽象类，可以自己定义数据类继承和重写这个抽象类，只需要定义`__len__`和`__getitem__`函数即可

```python
from torch.utils.data import Dataset
class myDataset(Dataset):
    def __init__(self, csv_file, txt_file, root_dir, other_file):
        self.csv_data = pd.read_csv(csv_file)
        with open(txt_file, 'r') as f:
            data_list=f.readlines()
        self.txt_data = data_list
        self.root_dir = root_dir
        
    def __len__(self):
        return len(self.csv_data)
    
    def __getitem__(self,idx):
        data = (self.csv_data[idx],self.txt_data[idx])
        return data
```

通过上面的方式，可以定义需要的数据类，可以通过迭代的方法取得每一个数据，但是这样很难实现取batch，shuffle或者多线程去读取数据，所以Pytorch中提供了torch.utils.data.DataLoader来定义一个新迭代器

```python
from torch.utils.data import DataLoader
dataiter = DataLoader(myDataset,batch_size=32)
```

##### 3.1.4 nn.Module(模组)

所有的层结构和损失函数来自torch.nn

```python
from torch import nn

class net_name(nn.Module):
    def __init__(self,other_arguments):
        super(net_name, self).__init__()
        self.conv1 = nn.Conv2d(in_channels,out_channels, kernel_size)
    
    def forward(self,x):
        x = self.conv1(x)
        return x
```

一个神经网络的典型训练过程如下：

- 定义包含一些可学习参数(或者叫权重）的神经网络
- 在输入数据集上迭代
- 通过网络处理输入
- 计算loss(输出和正确答案的距离）
- 将梯度反向传播给网络的参数
- 更新网络的权重，一般使用一个简单的规则：weight = weight - learning_rate * gradient

**使用torch.nn内的序列容器Sequential**

```python
batch_n = 100
hidden_layer = 100
input_data = 1000
output_data = 10

# 第一种方式
models_1 = torch.nn.Sequential(
    torch.nn.Linear(input_data,hidden_layer),
    torch.nn.ReLU(),
    torch.nn.Linear(hidden_layer,output_data)
)

# 第二种方式
from collections import OrderedDict
models_2 = torch.nn.Sequential(OrderedDict([
    ("Line1",torch.nn.Linear(input_data,hidden_layer)),
    ("ReLU1",torch.nn.ReLU()),
    ("Line2",torch.nn.Linear(hidden_layer,output_data))])    
)

print(models_1)
print(models_2)
```

**使用nn.Module定义一个神经网络**

```python
import torch
import torch.nn as nn
import torch.nn.functional as F


class Net(nn.Module):

    def __init__(self):
        super(Net, self).__init__()
        # 输入图像channel：1；输出channel：6；5x5卷积核
        self.conv1 = nn.Conv2d(1, 6, 5)
        self.conv2 = nn.Conv2d(6, 16, 5)
        # an affine operation: y = Wx + b
        self.fc1 = nn.Linear(16 * 5 * 5, 120)
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, 10)

    def forward(self, x):
        # 2x2 Max pooling
        x = F.max_pool2d(F.relu(self.conv1(x)), (2, 2))
        # 如果是方阵,则可以只使用一个数字进行定义
        x = F.max_pool2d(F.relu(self.conv2(x)), 2)
        x = x.view(-1, self.num_flat_features(x))
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x

    def num_flat_features(self, x):
        size = x.size()[1:]  # 除去批处理维度的其他所有维度
        num_features = 1
        for s in size:
            num_features *= s
        return num_features


net = Net()
print(net)
```

##### 3.1.5 torch.optim(优化)

优化算法分为两大类：

（1）一阶优化算法  
使用各个参数的梯度值来更新参数，最常用的是梯度下降。梯度下降的功能是通过寻找最小值，控制方差，更新模型参数，最终使模型收敛，网络的参数更新公式  
θ = θ − η × ∂ J ( θ ) ∂ θ \theta = \theta - \eta × \frac{\partial J(\theta)}{\partial \theta}θ=θ−η×∂θ∂J(θ)​  
其中η \etaη是学习率，∂ J ( θ ) ∂ θ \frac{\partial J(\theta)}{\partial \theta}∂θ∂J(θ)​是函数的梯度

（2）二阶优化算法  
二阶优化算法使用了二阶导数（Hessian方法）来最小化或最大化损失函数，主要是基于牛顿法

```python
optimizer=torch.optim.SGD(model.parameters(),lr=0.01,momentum=0.9)
```

##### 3.1.6 模型的保存和加载

1.保存

```python
#保存模型
torch.save(model,path)
#保存模型的状态
torch.save(model.state_dict(),path)
```

2.加载

```python
#加载完整的模型
load_model = torch.load(path)
#加载模型参数，需要先导入模型的结构
model.load_state_dic(torch.load(path))
```

#### 3.2 线性模型

##### 3.2.1 介绍

f(x)=wx+b

f(x)=w1x1+w2x2+…+wdxd+b

w和b都是需要学习的参数

##### 3.2.2 一维线性回归

给定数据集D={(x1,y1),(x2,y2),…,(xm,ym)}，线性回归希望得到一个f(x)=wx+b能够很好的拟合y

方法是利用L o s s = ∑ i = 1 m ( f ( x i ) − y i ) 2 Loss=\sum_{i=1}^m(f(x_i)-y_i)^2Loss=∑i=1m​(f(xi​)−yi​)2来衡量误差，即均方误差，那么  
( w ∗ , b ∗ ) = a r g min ⁡ w , b ∑ i = 1 m ( f ( x i ) − y i ) 2 = a r g min ⁡ w , b ∑ i = 1 m ( y i − w x i − b ) 2 (w^*,b^*)=arg\min_{w,b}\sum_{i=1}^m(f(x_i)-y_i)^2=arg\min_{w,b}\sum_{i=1}^m(y_i-wx_i-b)^2(w∗,b∗)=argw,bmin​i=1∑m​(f(xi​)−yi​)2=argw,bmin​i=1∑m​(yi​−wxi​−b)2

求解办法：求它的偏导数,并让其为0来估计参数  
∂ L o s s ( w , b ) ∂ w = 2 ( w ∑ i = 1 m x i 2 − ∑ i = 1 m ( y i − b ) x i ) = 0 \frac{\partial Loss_{(w,b)}}{\partial w} = 2(w\sum_{i=1}^{m}x_i^2-\sum_{i=1}^{m}(y_i-b)x_i)=0∂w∂Loss(w,b)​​=2(wi=1∑m​xi2​−i=1∑m​(yi​−b)xi​)=0  
∂ L o s s ( w , b ) ∂ b = 2 ( m b − ∑ i = 1 m ( y i − w x i ) ) = 0 \frac{\partial Loss_{(w,b)}}{\partial b} = 2(mb-\sum_{i=1}^{m}(y_i-wx_i))=0∂b∂Loss(w,b)​​=2(mb−i=1∑m​(yi​−wxi​))=0  
得到w和b的最优解  
w = ∑ i = 1 m y i ( x i − x ˉ ) ∑ i = 1 m x i 2 − 1 m ( ∑ i = 1 m x i ) 2 w=\frac{\sum_{i=1}^{m}y_i(x_i- \bar x)}{\sum_{i=1}^{m}x_i^2-\frac{1}{m}(\sum_{i=1}^{m}x_i)^2}w=∑i=1m​xi2​−m1​(∑i=1m​xi​)2∑i=1m​yi​(xi​−xˉ)​  
b = 1 m ∑ i = 1 m ( y i − w x i ) b=\frac{1}{m}\sum_{i=1}^{m}(y_i-wx_i)b=m1​i=1∑m​(yi​−wxi​)  
其中x ˉ \bar xxˉ是x的均值  
x ˉ = 1 m ∑ i = 1 m x i \bar x = \frac{1}{m}\sum_{i=1}^{m}x_ixˉ=m1​i=1∑m​xi​

##### 3.2.3 多维线性回归

f ( x i ) = w T x i + b f(x_i)=w^Tx_i+bf(xi​)=wTxi​+b  
为使得∑ i = 1 m ( f ( x i ) − y i ) 2 \sum_{i=1}^{m}(f(x_i)-y_i)^2∑i=1m​(f(xi​)−yi​)2最小，这也称为“多元线性回归”，使用最小二乘法对w和b进行估计，假设有d个属性，将w和d写入同一个矩阵，将数据集D表示成一个m×(d+1)的矩阵X，即  
X = [ x 11 x 12 ⋯ x 1 d 1 x 21 x 22 ⋯ x 2 d 1 ⋮ ⋮ ⋱ ⋮ ⋮ x m 1 x m 2 ⋯ x m d 1 ] = [ x 1 T 1 x 2 T 1 ⋮ ⋮ x m T 1 ] X=

⎡⎣⎢⎢⎢⎢⎢x11x21⋮xm1x12x22⋮xm2⋯⋯⋱⋯x1dx2d⋮xmd11⋮1⎤⎦⎥⎥⎥⎥⎥[x11x12⋯x1d1x21x22⋯x2d1⋮⋮⋱⋮⋮xm1xm2⋯xmd1]

=

⎡⎣⎢⎢⎢⎢⎢xT1xT2⋮xTm11⋮1⎤⎦⎥⎥⎥⎥⎥[x1T1x2T1⋮⋮xmT1]

X=⎣⎢⎢⎢⎡​x11​x21​⋮xm1​​x12​x22​⋮xm2​​⋯⋯⋱⋯​x1d​x2d​⋮xmd​​11⋮1​⎦⎥⎥⎥⎤​=⎣⎢⎢⎢⎡​x1T​x2T​⋮xmT​​11⋮1​⎦⎥⎥⎥⎤​  
将目标y也写成乘向量的形式y=(y1,y2,…,ym),那么可得  
w ∗ = a r g min ⁡ w ( y − X w ) T ( y − X w ) w^* = arg \min_w(y-Xw)^T(y-Xw)w∗=argwmin​(y−Xw)T(y−Xw)  
对其求导，令它为0  
∂ L o s s w ∂ w = 2 X T ( X w − y ) = 0 \frac{\partial Loss_w}{\partial w}=2X^T(Xw-y)=0∂w∂Lossw​​=2XT(Xw−y)=0

> 上面涉及到矩阵的逆运算，所以需要X T X X^TXXTX是一个满秩矩阵或者正定矩阵

可以得到:  
w ∗ = ( X T X ) − 1 X T y w ^ * =(X^TX)^{-1}X^Tyw∗=(XTX)−1XTy  
故回归模型可以写成：  
f ( x i ) = x i T ( X T X ) − 1 X T y f(x _ i)=x _ i^T(X^TX)^{-1}X^Tyf(xi​)=xiT​(XTX)−1XTy

##### 3.2.4 一维线性回归的代码实现

```python
import numpy as np
import matplotlib.pyplot as plt

x_train = np.array([[3.3],[4.4],[5.5],[6.71],[6.93],[4.168],[9.779],[6.182],[7.59],[2.167],[7.042],[10.791],[5.313],[7.997],[3.1]],dtype=np.float32)
y_train = np.array([[1.7],[2.76],[2.09],[3.19],[1.694],[1.573],[3.366],[2.596],[2.53],[1.221],[2.827],[3.465],[1.65],[2.904],[1.3]],dtype=np.float32)

x_train = torch.from_numpy(x_train)
y_train = torch.from_numpy(y_train)

class LinearRegression(nn.Module):
    def __init__(self):
        super(LinearRegression,self).__init__() #继承父类
        self.linear = nn.Linear(1,1) # 1*1
    
    def forward(self,x):
        out=self.linear(x)
        return out

if torch.cuda.is_available():
    model = LinearRegression().cuda()
else:
    model = LinearRegression()

criterion = torch.nn.MSELoss() # 均方误差
#优化函数，model.parameters()为该实例中可优化的参数，lr为参数优化的选项（学习率等）
optimizer = torch.optim.SGD(model.parameters(),lr=1e-3) #梯度下降

num_epochs = 1000

for epoch in range(num_epochs):
    if torch.cuda.is_available():
        inputs = Variable(x_train).cuda()
        target = Variable(y_train).cuda()
    else:
        inputs = Variable(x_train)
        target = Variable(y_train)
    # forward
    out = model(inputs)
    loss = criterion(out,target) #均方误差
    # backward
    optimizer.zero_grad() #置0
    loss.backward() #求梯度
    optimizer.step() #更新所有的参数，梯度下降
    
    if(epoch+1)%50==0:
        print('Epoch[{}/{}],Loss:{:.6f}'.format(epoch+1,num_epochs,loss))

model.eval() #将模型变成测试模式
predict = model(Variable(x_train))
predict = predict.data.numpy()
#画图
#plt.plot(x_train.numpy(),y_train.numpy(),'ro',label='Original data')
#plt.plot(x_train.numpy(),predict,label="Fitting Line")
#plt.show()
```

![](https://i-blog.csdnimg.cn/blog_migrate/396b69e89e7fd5f992dd377250b23885.png)

##### 3.2.5 多项式回归

对于y = b + w 1 × x + w 2 × x 2 + w 3 × x 3 y=b+w_1×x+w_2×x^2+w_3×x^3y=b+w1​×x+w2​×x2+w3​×x3，预处理数据，变成矩阵形式  
X = [ x 1 x 1 2 x 1 3 x 2 x 2 2 x 2 3 ⋮ ⋱ ⋮ x n x n 2 x n 3 ] X=

⎡⎣⎢⎢⎢⎢⎢x1x2⋮xnx21x22⋱x2nx31x32⋮x3n⎤⎦⎥⎥⎥⎥⎥[x1x12x13x2x22x23⋮⋱⋮xnxn2xn3]

X=⎣⎢⎢⎢⎡​x1​x2​⋮xn​​x12​x22​⋱xn2​​x13​x23​⋮xn3​​⎦⎥⎥⎥⎤​

```python
def make_features(x):
    x=x.unsqueeze(1)  # 在第1维（从0开始）增加一维
    return torch.cat([x ** i for i in range(1,4)],1) #1代表横着拼接x,x^2,x^3

w_target = torch.FloatTensor([0.5,3,2.4]).unsqueeze(1) # 在第1维（从0开始）加一层
b_target = torch.FloatTensor([0.9])

def f(x):
    #定义∑wix^i+b
    return x.mm(w_target) + b_target[0]

def get_batch(batch_size=32):
    #产生数据
    random = torch.randn(batch_size)
    x = make_features(random)
    y = f(x)
    if torch.cuda.is_available():
        return Variable(x).cuda(),Variable(y).cuda()
    else:
        return Variable(x),Variable(y)

class poly_model(nn.Module):
    def __init__(self):
        super(poly_model,self).__init__()
        self.poly = nn.Linear(3,1)

    def forward(self,x):
        out = self.poly(x)
        return out
    
if torch.cuda.is_available():
    model = poly_model().cuda()
else:
    model = poly_model()
    
criterion = nn.MSELoss() # 均方误差
optimizer = torch.optim.SGD(model.parameters(),lr=1e-3)#梯度下降

epoch = 0

while True:
    batch_x,batch_y = get_batch()
    #前向传播
    output = model(batch_x)
    loss = criterion(output,batch_y)
    epoch+=1
    if epoch%50 ==0:
        print("Epoch:{},Loss:{:.6f}".format(epoch,loss.data.item()))
    optimizer.zero_grad() #置0
    loss.backward() #后向传播
    optimizer.step() #优化参数
    
    if loss <1e-2:
        break
    
```

> 注意：  
> `torch.nn`只支持小批量处理`(mini-batches）`。整个`torch.nn`包只支持小批量样本的输入，不支持单个样本的输入。  
> 比如，`nn.Conv2d` 接受一个4维的张量，即`nSamples x nChannels x Height x Width`.  
> 如果是一个单独的样本，只需要使用`input.unsqueeze(0)`来添加一个“假的”批大小维度。

#### 3.3 分类问题

##### 3.3.1 问题介绍

机器学习中的监督学习主要分为回归问题和分类问题，对于回归问题，希望预测的结果是连续的，对于分类问题所预测的结果是离散的。

监督学习从数据中学习一个分类模型或者分类决策函数，被称为分类器

##### 3.3.2 Logistic起源

著名的二分类算法，Logistic回归。起源于对人口数量增长情况的研究

##### 3.3.3 Logistic分布

设x是连续的随机变量，服从Logistic分布是指X的分布函数和密度函数是如下  
F ( x ) = P ( X ≤ x ) = 1 1 + e − ( x − μ ) / γ F(x)=P(X≤x)=\frac{1}{1+e^{-(x-\mu)/\gamma}}F(x)=P(X≤x)=1+e−(x−μ)/γ1​  
f ( x ) = e − ( x − μ ) / γ γ ( 1 + e − ( x − μ ) / γ ) 2 f(x)=\frac{e^{-(x-\mu)/\gamma}}{\gamma (1+e^{-(x-\mu)/\gamma})^2}f(x)=γ(1+e−(x−μ)/γ)2e−(x−μ)/γ​  
其中μ影响中心对称点的位置，γ越小中心点附件的增长速度越快  
Sigmoid函数是Logistic分布函数中γ=1，μ=0的特殊形式，表达式如下：p ( x ) = 1 1 + e − x p(x)=\frac{1}{1+e^{-x}}p(x)=1+e−x1​

##### 3.3.4 二分类的Logistic回归

假设输入的数据的特征向量x ∈ R n x∈R^nx∈Rn，那么决策边界可以表示为∑ i = 1 n w i x i + b = 0 \sum_{i=1}^{n}w_ix_i+b=0∑i=1n​wi​xi​+b=0，建设存在一个样本点使得h w ( x ) = ∑ i = 1 n w i x i + b > 0 h_w(x)=\sum_{i=1}^{n}w_ix_i+b>0hw​(x)=∑i=1n​wi​xi​+b>0，那么判定它的类别是1，如果<0，判定其类别是0.  
Logistic回归通过找到分类概率P(Y=1)与输入变量x的直接关系，然后通过比较概率值来判断类别，简单来说就是通过计算下面两个概率分布  
P ( Y = 0 ∣ x ) = 1 1 + e w x + b P(Y=0|x)=\frac{1}{1+e^{wx+b}}P(Y=0∣x)=1+ewx+b1​  
P ( Y = 1 ∣ x ) = e w x + b 1 + e w x + b P(Y=1|x)=\frac{e^{wx+b}}{1+e^{wx+b}}P(Y=1∣x)=1+ewx+bewx+b​  
其中w是权重，b是偏置

> 一个事件发生的几率（odds）是指该事件发生的概率（p）与不发生的概率的比值（1-p），该事件的对数几率或logit函数是：l o g i t ( p ) = l o g p 1 − p logit(p)=log\frac{p}{1-p}logit(p)=log1−pp​

对于Logistic回归而言，可以得到：  
l o g P ( Y = 1 ∣ x ) 1 − P ( Y = 1 ∣ x ) = w x + b log \frac{P(Y=1|x)}{1-P(Y=1|x)}=wx+blog1−P(Y=1∣x)P(Y=1∣x)​=wx+b

##### 3.3.5 模型的参数估计

对于给定的训练集数据T={(x1,y1),(x2,y2),…,(xn,yn)}，其中$x_i \in R^n,y_i \in ${0,1}，假设P(Y=1|x)=Π(x)，那么P(Y=0|x)=1-Π(x)，所以似然函数为：  
∏ i = 1 n [ π ( x i ) ] y 1 [ 1 − π ( x i ) ] 1 − y i \prod_{i=1}^{n}[\pi (x_i)]^{y_1}[1-\pi (x_i)]^{1-y_i}i=1∏n​[π(xi​)]y1​[1−π(xi​)]1−yi​  
取对数后的对数似然函数：  
L ( w ) = ∑ i = 1 n [ y i ( w x i + b ) − l o g ( 1 + e w x i + b ) ] L(w)=\sum_{i=1}^{n}[y_i(wx_i+b)-log(1+e^{wx_i+b})]L(w)=i=1∑n​[yi​(wxi​+b)−log(1+ewxi​+b)]  
用L(w)对w求导：  
∂ L ( w ) ∂ w = ∑ i = 1 n y i x i − ∑ i = 1 n e w x i + b 1 + e w x i + b x i = ∑ i = 1 n ( y i − l o g i t ( w x i ) ) x i \frac{\partial L(w)}{\partial w}=\sum_{i=1}^{n}y_ix_i-\sum_{i=1}^{n}\frac{e^{wx_i+b}}{1+e^{wx_i+b}}x_i=\sum_{i=1}^{n}(y_i-logit(wx_i))x_i∂w∂L(w)​=i=1∑n​yi​xi​−i=1∑n​1+ewxi​+bewxi​+b​xi​=i=1∑n​(yi​−logit(wxi​))xi​  
∂ L ( w ) ∂ b = ∑ i = 1 n y i − ∑ i = 1 n e w x i + b 1 + e w x i + b = ∑ i = 1 n ( y i − l o g i t ( w x i ) ) \frac{\partial L(w)}{\partial b}=\sum_{i=1}^{n}y_i-\sum_{i=1}^{n}\frac{e^{wx_i+b}}{1+e^{wx_i+b}}=\sum_{i=1}^{n}(y_i-logit(wx_i))∂b∂L(w)​=i=1∑n​yi​−i=1∑n​1+ewxi​+bewxi​+b​=i=1∑n​(yi​−logit(wxi​))

##### 3.3.6 Logistic回归的代码实现

```python
import requests

#获取数据
url="https://cdn.jsdelivr.net/gh/Justlovesmile/code-of-learn-deep-learning-with-pytorch/chapter3_NN/logistic-regression/data.txt"
data = requests.get(url)
data_list=data.text.split('\n')[:-1]
data_list=[i.split(',') for i in data_list]
data = [(float(i[0]),float(i[1]),float(i[2])) for i in data_list]

np_data = np.array(data, dtype='float32') # 转换成 numpy array
x_data = torch.from_numpy(np_data[:, 0:2]) # 转换成 Tensor, 大小是 [100, 2]
y_data = torch.from_numpy(np_data[:, -1]).unsqueeze(1) # 转换成 Tensor，大小是 [100, 1]

#print(x_data,y_data)

#画数据的散点图
x0=list(filter(lambda x:x[-1]==0.0,data))
x1=list(filter(lambda x:x[-1]==1.0,data))
plot_x0_0 = [i[0] for i in x0]
plot_x0_1 = [i[1] for i in x0]
plot_x1_0 = [i[0] for i in x1]
plot_x1_1 = [i[1] for i in x1]

plt.plot(plot_x0_0,plot_x0_1,'ro',label="x_0") #0类用红色
plt.plot(plot_x1_0,plot_x1_1,'bo',label="x_1") #1类用蓝色
plt.legend(loc='best') #图例的位置

#分类
class LogisticRegression(nn.Module):
    def __init__(self):
        super(LogisticRegression,self).__init__() #继承
        self.lr = nn.Linear(2,1) #2*1
        self.sm = nn.Sigmoid() #sigmoid函数
        
    def forward(self,x):
        x=self.lr(x)
        x=self.sm(x)
        return x
    
logistic_model = LogisticRegression()
if torch.cuda.is_available():
    logistic_model.cuda()

criterion = nn.BCELoss() #二分类的损失函数
#随机梯度下降优化，parameters是可优化参数，lr是学习率，momentum是动量因子
optimizer = torch.optim.SGD(logistic_model.parameters(),lr=1e-3,momentum=0.9)

for epoch in range(20000):
    if torch.cuda.is_available():
        x=Variable(x_data).cuda()
        y=Variable(y_data).cuda()
    else:
        x=Variable(x_data)
        y=Variable(y_data)
    #forward
    out = logistic_model(x)
    loss = criterion(out,y)
    mask = out.ge(0.5).float() #if out>0.5,out=1,else out=0
    acc = float((mask == y_data).sum().item()) / y_data.shape[0]
    #backward
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
    if(epoch+1)%2000 ==0:
        print('*'*10)
        print('Epoch: {},Loss: {:.4f},Acc: {:.4f}'.format(epoch+1,loss,acc))

# 画线w1x+w2y+b=0
w0,w1 = logistic_model.lr.weight[0]
b = logistic_model.lr.bias.data[0]
plot_x = np.arange(30,100,0.1)
w0=w0.data
w1=w1.data
plot_y = (-w0*plot_x-b) /w1
plt.plot(plot_x,plot_y)
plt.show()
```

![](https://i-blog.csdnimg.cn/blog_migrate/f88bb57785c9d9501d5768bee055f131.png)

#### 3.4 简单多层全连接前向网络

##### 3.4.1 模拟神经元

神经网络就是受到了模拟脑神经元的启发

##### 3.4.2 单层神经网络的分类器

例如之前的Logistic回归，是使用了sigmoid函数作为激活函数的一层神经网络

##### 3.4.3 激活函数

1.Sigmoid函数

σ ( x ) = 1 1 + e − x \sigma (x)=\frac{1}{1+e^{-x}}σ(x)=1+e−x1​

缺点：  
（1）造成梯度消失。在靠近0，1两端，梯度几乎为0，导致没有信息来更新参数  
（2）输出不是以0为均值。

2.Tanh

t a n h ( x ) = 2 σ ( 2 x ) − 1 tanh(x)=2\sigma(2x)-1tanh(x)=2σ(2x)−1

Tanh激活函数是sigmoid函数的变形，将输入的数据转化到-1到1之间，解决了sigmoid函数第二个问题，但仍存在梯度消失的问题

3.ReLU

ReLU的数学表达式为f ( x ) = m a x ( 0 , x ) f(x)=max(0,x)f(x)=max(0,x)

优点：  
（1）相比较sigmoid和tanh，ReLU可以极大地加速随机梯度下降法的收敛速度，因为是线性的，不存在梯度消失  
（2）计算方法更简单

缺点：  
训练的时候很脆弱，一个很大的梯度经过ReLU激活函数，更新参数之后，会使得这个神经元不会对任何数据有激活现象，之后再经过ReLU的梯度都是0，参数无法更新。可以通过设置较小的学习率来避免这个问题

4.Leaky ReLU

ReLU的变式，为了修复ReLU脆弱的缺点，将x<0的部分变成一个很小的负的斜率，但是效果时好时不好

5.Maxout

f ( x ) = m a x ( w 1 x + b 1 , w 2 x + b 2 ) f(x)=max(w_1x+b_1,w_2x+b_2)f(x)=max(w1​x+b1​,w2​x+b2​)  
ReLU只是Maxout中w1=0，b1=0的特殊形式

优点：包含ReLU的优点，避免了ReLU的脆弱性  
缺点：参数存储变大

##### 3.4.4 神经网络的结构

神经网络是一个由神经元组成的无环图

nn.Linear(in,out，bias=False)是全连接神经网络层的函数

##### 3.4.5 模型的表示能力与容量

在实际中，我们可能发现一个三层的全连接神经网络比一个两层的全连接神经网络表现更好，但是更深的网络结构对全连接神经网络效果提升表现不大。  
我们需要注意的是，增大网络的层数和每层的节点数，相当于在增大网络的容量，容量的增大意味着网络有着更大的潜在表现能力。

但是当我们在做一个二分类问题时，更复杂的模型或许有着更复杂的形状，能将测试用例完美的分类，但是却忽略了潜在的数学关系，将噪声的干扰放大，这种效果被称为过拟合

#### 3.5 深度学习的基石：反向传播算法

##### 3.5.1 链式法则

求导的链式法则（高数知识）

##### 3.5.2 反向传播算法

是链式求导法则的应用

局部求导，不断迭代传播

#### 3.6 各种优化算法的变式

##### 3.6.1 梯度下降法

梯度下降的更新公式  
x i = x i − 1 − η ∇ L ( x i − 1 ) x^i=x^{i-1}-\eta \nabla L(x^{i-1})xi=xi−1−η∇L(xi−1)

##### 3.6.2 梯度下降法的变式

1.SGD  
随机梯度下降法，每次使用一批（batch）数据进行梯度的计算，而不是全部数据的梯度

2.Momentum  
在随机梯度下降的同时，增加动量（momentum），帮助跳出一些鞍点或局部极小值点

3.Adagrad  
自适应学习率的方法，公式是  
w t + 1 ← w t − η ∑ i = 0 t ( g i ) 2 + ε w^{t+1}←w^{t}-\frac{\eta}{\sqrt{\sum_{i=0}^{t}(g^i)^2}+\varepsilon }wt+1←wt−∑i=0t​(gi)2​+εη​

学习率在不断变小，但是在某些情况下会导致学习过早停止

4.RMSprop  
一种非常有效的自适应学习率的改进方法，公式是  
c a c h e t = α ∗ c a c h e t − 1 + ( 1 − α ) ( g t ) 2 cache^t=\alpha * cache^{t-1}+(1-\alpha)(g^t)^2cachet=α∗cachet−1+(1−α)(gt)2  
w t + 1 ← w t − η c a c h e t + ε g t w^{t+1}←w^{t}-\frac{\eta}{\sqrt{cache^t+\varepsilon}}g^twt+1←wt−cachet+ε​η​gt  
其中α是衰减率，能有效避免Adagrad学习率一直递减太多的问题，能够更快地收敛

5.Adam  
一种综合型学习方法，可以看成RMSprop加上momentum的学习方法

#### 3.7 处理数据和训练模型的技巧

##### 3.7.1 数据预处理

1.中心化  
变成0均值

2.标准化  
使得每个特征维度的最大值和最小值按比例缩放到-1到1之间

3.PCA（主成分分析）  
将数据去相关性，将其投影到一个特征空间，取一些较大的，主要的特征向量来降低数据的维度

4.白噪声  
将数据投影到一个特征空间，然后每个维度除以特征值来标准化这些数据

##### 3.7.2 权重初始化

1.全0初始化  
不应该采用这种策略

2.随机初始化  
包括了高斯随机化，均匀随机化

3.稀疏初始化

4.初始化偏置

5.批标准化

##### 3.7.3 防止过拟合

1.正则化  
2.Dropout

#### 3.8 多层全连接神经网络实现MNIST手写数字分类

```python
import torch
from torch import nn,optim
from torch.autograd import Variable
from torch.utils.data import DataLoader
from torchvision import datasets,transforms

#带有批标准化和激活函数的三层全连接神经网络
class Batch_Net(nn.Module):
    def __init__(self,in_dim,n_hidden_1,n_hidden_2,out_dim):
        super(Batch_Net,self).__init__()
        self.layer1 = nn.Sequential(nn.Linear(in_dim,n_hidden_1),nn.BatchNorm1d(n_hidden_1),nn.ReLU(True))
        self.layer2 = nn.Sequential(nn.Linear(n_hidden_1,n_hidden_2),nn.BatchNorm1d(n_hidden_2),nn.ReLU(True))
        self.layer3 = nn.Sequential(nn.Linear(n_hidden_2,out_dim))
    
    def forward(self,x):
        x=self.layer1(x)
        x=self.layer2(x)
        x=self.layer3(x)
        return x

batch_size = 64
learning_rate = 1e-2
num_epoch = 20

#transforms.ToTensor()将图片转换成PyTorch中从处理的对象，并自动将图片标准化了，即范围0到1
#transforms.Normalize(均值，方差)，处理：减均值，除以方差
#图片为灰度图，只有一个通道，如果是三通道则为transforms.Normalize([a,b,c],[d,e,f])
data_tf = transforms.Compose(
    [transforms.ToTensor(),transforms.Normalize([0.5],[0.5])]
)

# 获取数据集
train_dataset = datasets.MNIST(root="./data",train=True,transform=data_tf,download=True)
test_dataset = datasets.MNIST(root="./data",train=False,transform=data_tf)
# 数据迭代器，传入数据集和batch_size，通过shuffle=True来表示是否将数据打乱
train_loader = DataLoader(train_dataset,batch_size=batch_size,shuffle=True)
test_loader = DataLoader(test_dataset,batch_size=batch_size,shuffle=False)

model = Batch_Net(28*28,300,100,10)
if torch.cuda.is_available():
    model = model.cuda()

criterion = nn.CrossEntropyLoss() #交叉熵
# 优化
optimizer = optim.SGD(model.parameters(),lr=learning_rate)

#训练
for epoch in range(num_epoch):
    eval_loss = 0
    eval_acc = 0
    for data in train_loader:
        img,label=data
        img = img.view(img.size(0),-1)
        if torch.cuda.is_available():
            img = Variable(img).cuda()
            label = Variable(label).cuda()
        else:
            img = Variable(img)
            label = Variable(label)
        out=model(img)
        loss = criterion(out,label)
        # backward
        optimizer.zero_grad() #置0
        loss.backward() #求梯度
        optimizer.step() #更新所有的参数，梯度下降
        #acc
        eval_loss +=loss*label.size(0)
        _,pred = torch.max(out,1)
        num_correct = (pred == label).sum()
        eval_acc +=num_correct
        print('Epoch:{},Loss: {:.6f},Acc:{:.6f}'.format(epoch,eval_loss/(len(train_dataset)),float(eval_acc)/(len(train_dataset))))

        
#测试
model.eval()
eval_loss = 0
eval_acc = 0
for data in test_loader:
    img,label=data
    img = img.view(img.size(0),-1)
    if torch.cuda.is_available():
        img = Variable(img).cuda()
        label = Variable(label).cuda()
    else:
        img = Variable(img)
        label = Variable(label)
    out=model(img)
    loss = criterion(out,label)
    eval_loss +=loss.data*label.size(0)
    _,pred = torch.max(out,1)
    num_correct = (pred == label).sum()
    eval_acc +=num_correct.data

print('Test Loss: {:.6f},Acc:{:.6f}'.format(eval_loss/(len(test_dataset)),float(eval_acc)/(len(test_dataset))))
```

### 第四章 卷积神经网络

1998年由Yann Lecun提出，2012年Alex Krizhecsky凭借它赢得了ImageNet挑战赛

#### 4.1 主要任务及起源

对于[计算机视觉](https://edu.csdn.net/cloud/sd_summit?utm_source=glcblog&spm=1001.2101.3001.7020)，主要用提取图像中的特征

#### 4.2 卷积神经网络的原理和结构

一，卷积神经网络的三种思想

1.局部性

对于图片而言，需要检测图片中的特征来决定图片的类别，通常情况下这些特征都不是由整张图片决定的，而是由一些局部的区域决定的

2.相同性

对不同图片，如果具有同样的特征，这些特征会出现在不同位置，但特征检测所作的操作几乎一样

3.不变性

对于一张大图片，如果进行下采样，那么图片的性质基本保持不变

二，卷积神经网络的层结构

对于全连接神经网络，其由一系列隐藏层构成，每个隐藏层由若干个神经元构成，其中每个神经元都和前一层的所有神经元相关联，但是每一层中的神经元是相互独立的。全连接神经网络在处理图片时，比如在minist数据集上，图片大小是28×28，那么每层的单个神经元的权重数目就是28×28=784，但这知识一张小图片，且只有一个通道，如果是大图片，那么就会导致参数增长特别快，所以全连接神经网络在处理图像并不是好的选择

而卷积神经网络是一个3D容量的神经元，每个神经元由三个维度排列：宽带，高度和深度。如果输入的图片是32×32×3，那么这张图片的宽度就是32，高度也是32，深度是3

卷积神经网络的主要层结构有三个：卷积层，池化层，全连接层，通过堆叠这些层结构形成了一个完整的卷积神经网络结构，其中一些层包含参数（如：卷积层，全连接层），一些层不包含参数（如：激活层，池化层）。

##### 4.2.1 卷积层

卷积层是卷积神经网络的核心

1.概述

卷积神经网络的参数，是由一些可学习的滤波器集合构成，每个滤波器在空间上（宽度和高度）都比较小，但深度和输入数据的深度保持一致。在前向传播时，让每个滤波器都在输入数据的宽度和高度上滑动（卷积），然后计算整个滤波器和输入数据任意一处的内积。  
当滤波器沿着输入数据的宽度和高度滑动时，会生成一个二维的激活图。每个卷积层上，会有一整个集合的滤波器，这样会形成多个二维的不同的激活图，将这些激活图在深度方向堆叠起来形成卷积层的输出

2.局部连接

与神经元连接的空间大小叫做神经元的感受野，其大小是一个人为设置的超参数，其实是滤波器的宽和高

3.空间排列

卷积层的输出深度是一个超参数，与使用的滤波器数量一致，并且在滑动滤波器的时候必须指定步长

4.边界填充

可以将输入数据用0在边界进行填充，用来控制输出数据在空间上的尺寸，输出的尺寸可以用一个公式来计算，W − F + 2 P S + 1 \frac{W-F+2P}{S}+1SW−F+2P​+1，其中W是输入的数据大小，F表示卷积层中神经元的感受野尺寸，S表示步长，P表示边界填充0的数量

5.步长的限制

步长的选择是有所限制的。当输入尺寸W是10时，如果不使用0填充，即P=0，滤波器尺寸F=3，这样步长S=2就行不通，因为(10-3+0)/2+1=4.5，不是一个整数，说明神经元不能整齐对称地滑过输入数据体，这样的超参数是无效的

6.参数共享

输出体数据在深度切片上所有的权重都使用同一个权重向量，那么卷积层在向前传播的过程中每个深度切片都可以看成是神经元的权重对输入数据体做卷积，这也就是为什么把这些3D的权重集合称为滤波器或者卷积核

7.总结

卷积层的性质

- （1）输入数据体尺寸是W1×H1×D1
- （2）4个超参数：卷积核数量K，卷积核空间尺寸F，滑动步长S，零填充的数量P
- （3）输出数据体的尺寸为W2×H2×D2，其中W 2 = W 1 − F + 2 P S + 1 W_2=\frac{W_1-F+2P}{S}+1W2​=SW1​−F+2P​+1,H 2 = H 1 − F + 2 P S + 1 H_2=\frac{H_1-F+2P}{S}+1H2​=SH1​−F+2P​+1,D2=K
- （4）由于参数共享，每个卷积核包含的权重数目为F×F×D1，卷积层一共有F×F×D1×K个权重和K个偏置
- （5）在输出体数据中，第d个深度切片（空间尺寸是W2×H2），用第d个卷积器和输入数据进行有效卷积运算的结果，再加上第d个偏置

对于卷积神经网络的一些超参数，常见的设置是F=3，S=1，P=1

##### 4.2.2 池化层

通常或者卷积层之间周期性插入一个池化层，作用是逐渐减低数据体的空间尺寸，这样能减少网络中参数的数量，减少计算资源耗费，同时也能有效地控制过拟合

步骤：设定一个空间窗口，不断滑动窗口，取这些窗口中的最大值作为输出结果

池化层之所有有效，是因为之前介绍的图片特征具有不变性，也就是通过下采样不会丢失图片拥有的特征

常用的池化层形式是尺寸为2×2的窗口，滑动步长是2，对图像进行下采样，将其中75%的激活信息都丢掉，选择其中最大的保留，池化层很少引入零填充

除最大值池化外，还有平均池化，或者L2范数池化，实际证明，最大池化效果最好，平均池化一般放在卷积神经网络最后一层

##### 4.2.3 全连接层

全连接层的每个神经元与前一层所有的神经元全部连接，在这个过程中为了防止过拟合会引入`Dropout`。在进入全连接层之前，使用全局平均池化能够有效地降低过拟合

##### 4.2.4 卷积神经网络的基本形式

卷积神经网络最常见的形式就是将一些卷积层和`ReLU`层放在一起，有可能在`ReLU`层前面加上批标准化层，随后紧跟池化层，再不断重复，直到图像被缩小到一个足够小的尺寸，然后将特征图展开，连接几层全连接层，最后输出结果

1.小滤波器的有效性

2.网络的尺寸

经验  
（1）输入层：一般而言，输入层的大小应该能够被2整除很多次，常用的数字包括32，44，96，224  
（2）卷积层：卷积层应该尽可能使用小尺寸，比如3×3或5×5，滑动步长取1。7×7通常用在第一个面对原始图像的卷积层上  
（3）池化层：池化层负责对输入的数据空间维度进行下采样，常用的设置使用2×2的感受野做最大值池化，步长取2  
（4）零填充：零填充的使用可以让卷积层的输入和输出在空间上的维度保持一致

#### 4.3 Pytorch卷积模块

##### 4.3.1 卷积层

`nn.Conv2d(in_channels,out_channels,kernel_size,stride,padding,dilation,groups,bias)`  
其中

- `in_channels`对应输入数据体的深度
- `out_channels`对应输出数据体的深度
- `kernel_size`表示滤波器（卷积核）的大小，例如：`kernel_size=3`或`kernel_size=(3,2)`
- `stride`表示滑动步长，默认`1`
- `padding=0`表示四周不进行零填充，`padding=1`表示四周进行`1`个像素点的零填充，默认`0`
- `bias`是一个布尔值，默认为`True`，表示使用偏置
- `groups`表示输出数据体深度上的联系，默认`groups=1`，即所有的输出和输入都是相关联的，如果`groups=2`表示输入的深度被分割成两份，输出的深度也被分割成两份，他们之间分别对应起来，所以要求输出和输入都必须要能被`groups`整除
- `dilation`表示卷积对于输入数据体的空间间隔，默认为`1`

##### 4.3.2 池化层

`nn.MaxPool2d(kernel_size,stride,padding,dilation,return_indices,ceil_model)`  
其中

- `kernel_size`,`stride`,`padding`,`dilation`和卷积层相同
- `return_indices`表示是否返回最大值所处的下标，默认为`False`
- `ceil_mode`表示使用一些方格代替层结构，默认`False`

`nn.AvgPool2d()`表示均值池化，里面的参数和MaxPool2d类似，但多一个参数`count_include_pad`表示计算均值的时候是否包含零填充，默认为`True`

其他还有`nn.LPPool2d()`,`nn.AdaptiveMaxPool2d()`

**下面是一个简单的多层卷积神经网络**

```python
from torch import nn

class SimpleCNN(nn.Module):
    def __init__(self):
        super(SimpleCNN,self).__init__()
        layer1 = nn.Sequential()
        layer1.add_module('conv1',nn.Conv2d(3,32,3,1,padding=1))
        layer1.add_module('relu1',nn.ReLU(True))
        layer1.add_module('pool1',nn.MaxPool2d(2,2))
        self.layer1=layer1

        layer2 = nn.Sequential()
        layer2.add_module('conv2',nn.Conv2d(32,64,3,1,padding=1))
        layer2.add_module('relu2',nn.ReLU(True))
        layer2.add_module('pool2',nn.MaxPool2d(2,2))
        self.layer2=layer2
        
        layer3 = nn.Sequential()
        layer3.add_module('conv3',nn.Conv2d(64,128,3,1,padding=1))
        layer3.add_module('relu3',nn.ReLU(True))
        layer3.add_module('pool3',nn.MaxPool2d(2,2))
        self.layer3=layer3

        layer4 = nn.Sequential()
        layer4.add_module('fc1',nn.Linear(2048,512))
        layer4.add_module('fc_relu1',nn.ReLU(True))
        layer4.add_module('fc2',nn.Linear(512,64))
        layer4.add_module('fc_relu2',nn.ReLU(True))
        layer4.add_module('fc3',nn.Linear(64,10))
        self.layer4=layer4
    
    def forward(self,x):
        conv1 = self.layer1(x)
        conv2 = self.layer2(conv1)
        conv3 = self.layer3(conv2)
        fc_input = conv3.view(conv3.size(0),-1)
        fc_out = slef.layer4(fc_input)
        return fc_out

model = SimpleCNN()
print(model)
```

##### 4.3.3 提取层结构

nn.Module具有几个重要属性

- `children()`，会返回下一级模块的迭代器，比如上面这个模型，直会返回在`self.layer1`,`slef.layer2`,`slef.layer3`以及`self.layer4`上的迭代器，不会返回他们内部的东西
- `modules()`，会返回模型中所有模块的迭代器，这样就有了一个好处，即它能够访问到最内层，比如`self.layer1.conv1`这个模块
- `named_children()`和`named_modules()`不仅会返回模块的迭代器，还会返回网络层的名字

```python
#提取前面两层
print(nn.Sequential(*list(model.children())[:2]))
```

**提取所有的卷积层**

```python
conv_model = nn.Sequential()
for layer in model.named_modules():
    if isinstance(layer[1],nn.Conv2d):
        conv_model.add_module(layer[0].split('.')[-1],layer[1])

print(conv_model)
```

##### 4.3.4 提取参数及自定义初始化

`nn.Module`关于参数的属性

- `named_parameters()`，给出网络层的名字和参数的迭代器
- `parameters()`，给出一个网络的全部参数的迭代器

```python
for param in model.named_parameters():
    print(param[0])
```

**对权重初始化**，因为权重是Variable，只需要取出data属性就能处理

```python
for m in model.modules():
    if isinstance(m,nn.Conv2d):
        nn.init.normal(m.weight.data)
        nn.init.xavier_normal(m.weight.data)
        nn.init.kaiming_normal(m.weight.data)#卷积层参数初始化
        m.bias.data.fill_(0)
    elif isinstance(m,nn.Linear):
        m.weight.data.normal_()#全连接层参数初始化
```

#### 4.4 卷积神经网络案例分析

##### 4.4.1 LeNet

LeNet是整个卷积神经网络的开山之作，共有7层，其中2层卷积和2层池化层交替出现，最后输出3层全连接层得到整体的效果

```python
class Lenet(nn.Module):
    def __init__(self):
        super(Lenet,self).__init__()
        layer1 = nn.Sequential()
        layer1.add_module('conv1',nn.Conv2d(1,6,3,padding=1))
        layer1.add_module('pool1',nn.MaxPool2d(2,2))
        self.layer1 = layer1
        
        layer2 = nn.Sequential()
        layer2.add_module('conv2',nn.Conv2d(6,16,5))
        layer2.add_module('pool2',nn.MaxPool2d(2,2))
        self.layer2 = layer2
        
        layer3 = nn.Sequential()
        layer3.add_module('fc1',nn.Linear(400,120))
        layer3.add_module('fc2',nn.Linear(120,84))
        layer3.add_module('fc3',nn.Linear(84,10))
        self.layer3 = layer3
        
    def forward(self,x):
        x = self.layer1(x)
        x = self.layer2(x)
        x = x.view(x.size(0),-1) # 将第二次卷积的输出拉伸为一行
        x = self.layer3(x)
        return x
```

##### 4.4.2 AlexNet

```python
class AlexNet(nn.Module):
    def __init__(self,num_classes):
        super(AlexNet,self).__init__()
        self.features = nn.Sequential(
            nn.Conv2d(3,64,kernel_size=11,stride=4,padding=2),
            nn.ReLU(inplace=True),
            nn.MaxPool2d(kernel_size=3,stride=2),
            nn.Conv2d(64,192,kernel_size=5,padding=2),
            nn.ReLU(inplace=True),
            nn.MaxPool2d(kernel_size=3,stride=2),
            nn.Conv2d(192,384,kernel_size=3,padding=1),
            nn.ReLU(inplace=True),
            nn.Conv2d(384,256,kernel_size=3,padding=1),
            nn.ReLU(inplace=True),
            nn.Conv2d(256,256,kernel_size=3,padding=1),
            nn.ReLU(inplace=True),
            nn.MaxPool2d(kernel_size=3,stride=2),
        )
        self.classifier = nn.Sequential(
            nn.Dropout(),
            nn.Linear(256*6*6,4096),
            nn.ReLU(inplace=True),
            nn.Dropout(),
            nn.Linear(4096,4096),
            nn.ReLU(inplace=True),
            nn.Linear(4096,num_classes),
        )
        
    def forward(self,x):
        x = self.features(x)
        x = x.view(x.size(0),256*6*6)
        x = self.classifier(x)
        return x
```

##### 4.4.3 VGGNet

使用了更小的滤波器，同时使用了更深的结构

```python
class VGG(nn.Module):
    def __init__(self,num_classes):
        super(VGG,self).__init__()
        self.features = nn.Sequential(
            nn.Conv2d(3,64,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(64,64,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.MaxPool2d(kernel_size=2,stride=2),
            nn.Conv2d(64,128,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(128,128,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.MaxPool2d(kernel_size=2,stride=2),
            nn.Conv2d(128,256,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(256,256,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(256,256,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.MaxPool2d(kernel_size=2,stride=2),
            nn.Conv2d(256,512,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(512,512,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(512,512,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.MaxPool2d(kernel_size=2,stride=2),
            nn.Conv2d(512,512,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(512,512,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.Conv2d(512,512,kernel_size=3,padding=1),
            nn.ReLU(True),
            nn.MaxPool2d(kernel_size=2,stride=2),
        )
        self.classifier = nn.Sequential(
            nn.Linear(512*7*7,4096),
            nn.ReLU(True),
            nn.Dropout(),
            nn.Linear(4096,4096),
            nn.ReLU(True),
            nn.Dropout(),
            nn.Linear(4096,num_classes),
        )
        self._initialize_weights()
        
    def forward(self,x):
        x = self.features(x)
        x = x.view(x.size(0),-1)
        x = self.classifier(x)
```

##### 4.4.4 GoogleNet

也叫InceptionNet，采用了比VGG更深的网络结构，一共22层，但是参数却比AlexNet少了12倍，同时有很高的计算效率，因为它采用了一种很有效的Inception模块，而且没有全连接层。

**Inception模块**

```python
class BasicConv2d(nn.Module):
    def __init__(self,in_channels,out_channels,**kwargs):
        super(BasicConv2d,self).__init__()
        self.conv = nn.Conv2d(in_channels,out_channels,bias=False,**kwargs)
        self.bn = nn.BatchNorm2d(out_channels,eps=0.001)
    
    def forward(self,x):
        x = self.conv(x)
        x = self.bn(x)
        return F.relu(x,inplace=True)

class Inception(nn.Module):
    def __init__(self,in_channels,pool_features):
        super(Inception,self).__init__()
        self.branch1x1 = BasicConv2d(in_channels,64,kernel_size=1)
        self.branch5x5_1 = BasicConv2d(in_channels,48,kernel_size=1)
        self.branch5x5_2 = BasicConv2d(48,64,kernel_size=5,padding=2)
        
        self.branch3x3db1_1 = BasicConv2d(in_channels,64,kernel_size=1)
        self.branch3x3db1_2 = BasicConv2d(64,96,kernel_size=3,padding=1)
        self.branch3x3db1_3 = BasicConv2d(96,96,kernel_size=3,padding=1)
        
        self.branch_pool = BasicConv2d(in_channels,pool_features,kernel_size=1)
    
    def forward(self,x):
        branch1x1 = self.branch1x1(x)
        
        branch5x5 = self.branch5x5_1(x)
        branch5x5 = self.branch5x5_2(branch5x5)
        
        branch3x3db1 = self.branch3x3db1_1(x)
        branch3x3db1 = self.branch3x3db1_2(branch3x3db1)
        branch3x3db1 = self.branch3x3db1_3(branch3x3db1)
        
        branch_pool = F.avg_pool2d(x,kernel_size=3,stride=1,padding=1)
        branch_pool = self.branch_pool(branch_pool)
        
        outputs = [branch1x1,branch5x5,branch3x3db1,branch_pool]
        return torch.cat(outputs,1) #按深度拼接
```

##### 4.4.5 ResNet

由微软研究院提出，通过残差模块能够成功地训练高达152层深的神经网络

ResNet 最初的设计灵感来自这个问题:在不断加深神经网络的时候，会出现一个Degradation ，即准确率会先上升然后达到饱和，再持续增加深度则会导致模型准确率下降。

这并不是过拟合的问题，因为不仅在验证集上误差增加，训练集本身误差也会增加，假设一个比较浅的网络达到了饱和的准确率，那么在后面加上几个恒等映射层，误差不会增加，也就说更深的模型起码不会使得模型效果下降。

这里提到的使用恒等映射直接将前一层输出传到后面的思想，就是 ResNet 的灵感来源。假设某个神经网络的输入是x， 期望输出是 H(x)，如果直接把输入x传到输出作为初始结果，那么此时需要学习的目标就是 F(x) = H (x) - x  
![](https://i-blog.csdnimg.cn/blog_migrate/b3d855a4f833a82c75bbc3f56b898b0f.png)  
左边是一个普通的网络，右边是一个 ResNet 的残差学习 单元， ResNet 相当于将学习目 标改变了.不再是学习一个完整的输出H ( x ) ， 而是学习输出和输入的差别H (x) - x，即残差。

除了这些比较出名的以外还有很多。并且并不需要重复造轮子，PyTorch内为我们实现了以上网络，都在`torchvision.model`里面，并且大部分网络都有预训练好的参数

#### 4.5 再实现MNIST手写数字分类

```python
import torch
from torch import nn,optim
from torch.autograd import Variable
from torch.utils.data import DataLoader
from torchvision import datasets,transforms

class CNN(nn.Module):
    def __init__(self):
        super(CNN,self).__init__()
        self.layer1 = nn.Sequential(
            nn.Conv2d(1,16,kernel_size=3),
            nn.BatchNorm2d(16),# 归一化处理，使得数据分布一致，避免梯度消失或梯度爆炸
            nn.ReLU(inplace=True)
        )
        self.layer2 = nn.Sequential(
            nn.Conv2d(16,32,kernel_size=3),
            nn.BatchNorm2d(32),
            nn.ReLU(inplace=True),
            nn.MaxPool2d(kernel_size=2,stride=2)
        )
        
        self.layer3 = nn.Sequential(
            nn.Conv2d(32,64,kernel_size=3),
            nn.BatchNorm2d(64),
            nn.ReLU(inplace=True)
        )
        
        self.layer4 = nn.Sequential(
            nn.Conv2d(64,128,kernel_size=3),
            nn.BatchNorm2d(128),
            nn.ReLU(inplace=True),
            nn.MaxPool2d(kernel_size=2,stride=2)
        )
        
        self.fc = nn.Sequential(
            nn.Linear(128*4*4,1024),
            nn.ReLU(inplace=True),
            nn.Linear(1024,128),
            nn.ReLU(inplace=True),
            nn.Linear(128,10)
        )
        
    def forward(self,x):
        x  = self.layer1(x)
        x  = self.layer2(x)
        x  = self.layer3(x)
        x  = self.layer4(x)
        x = x.view(x.size(0),-1)
        x  = self.fc(x)
        return x
    
batch_size = 64
learning_rate = 1e-2
num_epoch = 5

data_tf = transforms.Compose(
    [transforms.ToTensor(),transforms.Normalize([0.5],[0.5])]
)

# 获取数据集
train_dataset = datasets.MNIST(root="./data",train=True,transform=data_tf,download=True)
test_dataset = datasets.MNIST(root="./data",train=False,transform=data_tf)
# 数据迭代器，传入数据集和batch_size，通过shuffle=True来表示是否将数据打乱
train_loader = DataLoader(train_dataset,batch_size=batch_size,shuffle=True)
test_loader = DataLoader(test_dataset,batch_size=batch_size,shuffle=False)

model = CNN()
if torch.cuda.is_available():
    model = model.cuda()

criterion = nn.CrossEntropyLoss()
optimizer = optim.SGD(model.parameters(),lr=learning_rate)

for epoch in range(num_epoch):
    eval_loss = 0.0
    eval_acc = 0.0
    print("Epoch {}/{}".format(epoch,num_epoch))
    print("-"*20)
    for data in train_loader:
        img,label=data
        if torch.cuda.is_available():
            img = Variable(img).cuda()
            label = Variable(label).cuda()
        else:
            img = Variable(img)
            label = Variable(label)
        out=model(img)
        loss = criterion(out,label)
        # backward
        optimizer.zero_grad() #置0
        loss.backward() #求梯度
        optimizer.step() #更新所有的参数，梯度下降
        #acc
        eval_loss += loss.data
        _,pred = torch.max(out,1)
        eval_acc += (pred == label).sum()
        print('Epoch:{},Loss: {:.4f},Acc:{:.4f}%'.format(epoch,eval_loss/(len(train_dataset)),100*float(eval_acc)/(len(train_dataset))))

        
PATH='./minist_net.pth'
print("Train finished!")
torch.save(model.state_dict(), PATH)
```

#### 4.6 图像增强的方法

torchvision.transforms包括所有图像增强的方法

- Scale，对图片的尺寸进行缩小和放大
- CenterCrop，对图像正中心进行给定大小的随机裁剪
- RandomCrop，对图片进行给定大小的随机裁剪
- RandomHorizaontalFlip，对图像进行概率为0.5的随机水平翻转
- RandomSizedCrop，首先对图片进行随机尺寸的裁剪，然后对裁剪图片进行一个随即比例的缩放，最后将图片变成给定的大小
- Pad，对图片进行边界零填充

除此之外，还可以使用OpenCV或者PIL等第三方图形库来实现

#### 4.7 实现cifar10分类

cifar10数据集中有60000张图片，每张图片的大小都是32×32的三通道彩色图

```python
import torch
import torchvision
import torchvision.transforms as transforms
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim
import os
import numpy as np
from torch.autograd import Variable

#数据处理
train_transform = transforms.Compose([
    transforms.Scale(40),
    transforms.RandomHorizontalFlip(),
    transforms.RandomCrop(32),
    transforms.ToTensor(),
    transforms.Normalize([0.5, 0.5, 0.5], [0.5, 0.5, 0.5])
])

test_transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize([0.5, 0.5, 0.5], [0.5, 0.5, 0.5])
])

#数据集获取
train_set = torchvision.datasets.CIFAR10(root='./data', train=True, download=True, transform=train_transform)
train_data = torch.utils.data.DataLoader(train_set, batch_size=32, shuffle=True)

test_set = torchvision.datasets.CIFAR10(root='./data', train=False, download=True, transform=test_transform)
test_data = torch.utils.data.DataLoader(test_set, batch_size=32, shuffle=False)

classes = ('plane', 'car', 'bird', 'cat',
           'deer', 'dog', 'frog', 'horse', 'ship', 'truck')
#3×3卷积层
def conv3x3(in_channel, out_channel, stride=1):
    return nn.Conv2d(in_channel, out_channel, 3, stride=stride, padding=1, bias=False)

class residual_block(nn.Module):
    def __init__(self, in_channel, out_channel, same_shape=True):
        super(residual_block, self).__init__()
        self.same_shape = same_shape
        stride = 1 if self.same_shape else 2
          
        self.conv1 = conv3x3(in_channel, out_channel, stride=stride)
        self.bn1 = nn.BatchNorm2d(out_channel)
          
        self.conv2 = conv3x3(out_channel, out_channel)
        self.bn2 = nn.BatchNorm2d(out_channel)
        if not self.same_shape:
            self.conv3 = nn.Conv2d(in_channel, out_channel, 1, stride=stride)
        
    def forward(self, x):
        out = self.conv1(x)
        out = F.relu(self.bn1(out), True)
        out = self.conv2(out)
        out = F.relu(self.bn2(out), True)
          
        if not self.same_shape:
            x = self.conv3(x)
        return F.relu(x+out, True)


class resnet(nn.Module):
    def __init__(self, in_channel, num_classes):
        super(resnet, self).__init__()
        self.block1 = nn.Conv2d(in_channel, 64, 7, 2,3) # 32-7+2*3/2+1=16
        self.block2 = nn.Sequential(
            nn.MaxPool2d(3, 1),
            residual_block(64, 64),
            residual_block(64, 64)
        )
        self.block3 = nn.Sequential(
            residual_block(64, 128, False),
            residual_block(128, 128)
        )
        self.block4 = nn.Sequential(
            residual_block(128, 256, False),
            residual_block(256, 256)
        )
        self.block5 = nn.Sequential(
            residual_block(256, 512, False),
            residual_block(512, 512)
        )
        self.avg_pool = nn.AvgPool2d(2)
        self.classifier = nn.Linear(512, num_classes)
          
    def forward(self, x):
        x = self.block1(x)
        #print(x.shape)
        x = self.block2(x)
        #print(x.shape)
        x = self.block3(x)
        #print(x.shape)
        x = self.block4(x)
        #print(x.shape)
        x = self.block5(x)
        #print(x.shape)
        x = self.avg_pool(x)
        x = x.view(x.size(0), -1)
        x = self.classifier(x)
        return x

PATH = './cifar_net.pth'
net = resnet(3, 10)
#if os.path.exists(PATH):
#    net.load_state_dict(torch.load(PATH))
criterion = nn.CrossEntropyLoss() #交叉熵
optimizer = optim.Adam(net.parameters(), lr=0.01) 

from datetime import datetime

#计算正确率
def get_acc(output, label):
    total = output.shape[0]
    _, pred_label = output.max(1)
    num_correct = (pred_label == label).sum().data
    return float(num_correct) / total

def train(net, train_data, valid_data, num_epochs, optimizer, criterion):
    if torch.cuda.is_available():
        net = net.cuda()
    #计时
    prev_time = datetime.now()
    for epoch in range(num_epochs):
        print("*"*10)
        train_loss = 0.0
        train_acc = 0.0
        net = net.train() #训练模式
        for data in train_data:
            im,label = data
            if torch.cuda.is_available():
                im = Variable(im.cuda())
                label = Variable(label.cuda())
            else:
                im = Variable(im)
                label = Variable(label)
            #forward
            output = net(im)
            loss = criterion(output, label)
            #forward
            optimizer.zero_grad()
            loss.backward()
            optimizer.step()
               
            train_loss += loss.data
            train_acc += get_acc(output, label)
        #计时
        cur_time = datetime.now()
        h, remainder = divmod((cur_time-prev_time).seconds, 3600)
        m, s = divmod(remainder, 60)
        time_str = "Time %02d:%02d:%02d" % (h, m, s)
        #测试
        if valid_data is not None:
            valid_loss = 0.0
            valid_acc = 0.0
            net = net.eval() # 切换测试模式
            for data in valid_data:
                im, label = data
                if torch.cuda.is_available():
                    im = Variable(im.cuda())
                    label = Variable(label.cuda())
                else:
                    im = Variable(im)
                    label = Variable(label)
                output = net(im)
                loss = criterion(output, label)
                valid_loss += loss.item()
                valid_acc += get_acc(output, label)
            epoch_str = (
                "Epoch %d. Train Loss: %f, Train Acc: %f, Valid Loss: %f, Valid Acc: %f, "
                % (epoch, train_loss / len(train_data),
                   train_acc / len(train_data), valid_loss / len(valid_data),
                   valid_acc / len(valid_data)))
        else:
            epoch_str = ("Epoch %d. Train Loss: %f, Train Acc: %f, " %
                         (epoch, train_loss / len(train_data),
                          train_acc / len(train_data)))
               
        prev_time = cur_time
        print(epoch_str + time_str)

train(net, train_data, test_data, 10, optimizer, criterion) 
print('Finished Training')

torch.save(net.state_dict(), PATH)
```

**测试**

```python
import matplotlib.pyplot as plt
import numpy as np

test_set = torchvision.datasets.CIFAR10(root='./data', train=False, download=True, transform=test_transform)
test_data = torch.utils.data.DataLoader(test_set, batch_size=4, shuffle=False)

# 输出图像的函数
def imshow(img):
    img = img / 2 + 0.5     # unnormalize
    npimg = img.numpy()
    plt.imshow(np.transpose(npimg, (1, 2, 0)))
    plt.show()

dataiter = iter(test_data)
images, labels = dataiter.next()

#print(images.shape)
# 输出图片
imshow(torchvision.utils.make_grid(images))
print('GroundTruth: ', ' '.join('%5s' % classes[labels[j]] for j in range(4)))

PATH = './cifar_net.pth'
net.load_state_dict(torch.load(PATH))

outputs = net(images)

_, predicted = torch.max(outputs, 1)

print('Predicted: ', ' '.join('%5s' % classes[predicted[j]] for j in range(4)))

class_correct = list(0. for i in range(10))
class_total = list(0. for i in range(10))
with torch.no_grad():
    for data in test_data:
        images, labels = data
        outputs = net(images)
        _, predicted = torch.max(outputs, 1)
        c = (predicted == labels).squeeze()
        for i in range(4):
            label = labels[i]
            class_correct[label] += c[i].item()
            class_total[label] += 1


for i in range(10):
    print('Accuracy of %5s : %2d %%' % (
        classes[i], 100 * class_correct[i] / class_total[i]))
```

### 第五章 循环神经网络

RNN，在序列问题和自然语言处理等领域取得很大的成功

#### 5.1 循环神经网络

卷积神经网络相当于人类的视觉，但是它没有记忆能力，所以它只能处理一种特定的视觉任务，没办法根据以前的记忆来处理新的任务。

循环神经网络的提出便是居于记忆模型的想法，期望网络能够记住前面出现的特征，并依据特征推断后面的结果，而且整体的网络结构不断循环，因而得名循环神经网络

比如：某一个单词的意思会因为上文提到的内容不同而有不同的含义，RNN可以很好的解决这类问题

##### 5.1.1 问题介绍

对于下面两句话

- arrive beijing on November 2nd
- leave beijing on November 2nd

第一句话表达到达，第二句话表示离开，如果网络能构记忆“beijing”前面的词，就会预测出不同的结果。

##### 5.1.2 循环神经网络的基本结构

将网络的输出保存在一个记忆单元中，这个记忆单元和下一次的输入一起进入神经网络中。因此，输入序列（sequences）的顺序改变，会改变网络的输出结果。

![](https://i-blog.csdnimg.cn/blog_migrate/3f57b5dbb9593171f47ff0bd6ed24097.jpeg)  
![](https://i-blog.csdnimg.cn/blog_migrate/655de5470368aa360d4b9197c79e6c9c.jpeg)

这个网络在t时刻接收到输入x t x_txt​之后，隐藏层的值是S t S_tSt​，输出值是O t O_tOt​。关键一点是，S t S_tSt​的值不仅仅取决于x t x_txt​，还取决于S t − 1 S_{t-1}St−1​。我们可以用下面的公式来表示循环神经网络的计算方法：

O t = g ( V S t ) O _ t = g(VS_t)Ot​=g(VSt​)  
S t = f ( U X t + W S t − 1 ) S _ t = f(UX_t+WS_{t-1})St​=f(UXt​+WSt−1​)

##### 5.1.3 存在的问题

循环神经网络具有很好的记忆特性，能够将记忆内容应用到当前情景下，但是记忆最大的问题在于遗忘性

#### 5.2 循环神经网络的变式：LSTM和GRU

##### 5.2.1 LSTM

LSTM是Long Short Term Memory Networks的缩写，是一种链式循环的网络结构，在网络内部有着更复杂的结构，主要为了解决长序列训练过程中的梯度下降和梯度爆炸问题。

LSTM由三个门来控制，分别是输入门，遗忘门和输出门。顾名思义，输入门控制着网络的输入，遗忘门控制着记忆单元，输出门控制着网络的输出。这其中最重要的就是遗忘门，遗忘门的作用是决定之前的哪些记忆及那个被保留，那些记忆将被去掉，正是由于遗忘门的作用，使得LSTM具有了长时记忆的功能

##### 5.2.2 GRU

GRU是Gated Recurrent Unit的缩写，由Cho于2014年提出，GRU和LSTM最大的不同在于GRU将遗忘门和输入门合成了一个“更新门”，同时网络不再额外给出记忆状态Ct，而是将输出结果ht作为记忆状态不断向后循环传递，网络的输出和出入变得简单

##### 5.2.3 收敛性问题

如果写了一个简单的LSTM网络去训练数据，会发现loss并不会按照想象的方式下降，而是在乱跳，这是因为RNN的误差曲面粗糙不平导致的，而解决方法是梯度裁剪（gradient clipping）

#### 5.3 循环神经网络的PyTorch实现

##### 5.3.1 PyTorch的循环网络模块

**1.标准RNN**

`nn.RNN()`  
**参数**

- `input_size`表示输入x t x_txt​的维度
- `hidden_size`表示输出h t h_tht​的维度
- `num_layers`表示网络层数，默认为1层
- `nonlinearity`表示非线性激活函数，默认为tanh，可选relu
- `bias`表示是否使用偏置，默认为True
- `batch_first`决定网络输入的维度顺序，默认输入顺序（seq,batch,feature），如果设置为True，则顺序为（batch，seq，feature）
- `dropout`，接受一个0到1的数值，并在除最后一层的其他输出层加上dropout层
- `bidirectional`默认是False，如果设置为True，就是双向循环神经网络的结构

**网络接受的输入**

- 序列输入x t x_txt​：x t x_txt​的维度是（seq，batch，feature），分别表示序列长度，批量和输入的特征维度
- 记忆输入h 0 h_0h0​：h 0 h_0h0​也叫隐藏状态，它的维度是（layers×direction，batch，hidden），分别表示层数乘方向（单向1，双向2），批量和输出的维度

**网络的输出**

- output，表示网络实际的输出，维度是（seq，batch，hidden×direction），分别表示序列长度，批量和输出维度乘方向
- h n h_nhn​表示记忆单元，维度是（layer×direction，batch，hidden）分别表示层数乘方向，批量，输出维度

```python
basic_rnn = nn.RNN(input_size=20,hidden_size=50,num_layers=2)

toy_input = Variable(torch.randn(100,32,20)) # seq,batch,input_size
h_0 = Variable(torch.rand(2,32,50)) # layer * direction,batch,hidden_size

toy_output,h_n = basic_rnn(toy_input,h_0)
```

**2.LSTM**

`nn.LSTM()`  
参数和标准RNN一样

LSTM与RNN不同的地方：

- LSTM的参数比标准RNN多，是标准RNN维度的4倍，但是访问的方式仍然是相同的
- LSTM的输入还多了一个C 0 C_0C0​，它们合在一起称为网络的隐藏状态，即（layer×direction，batch，hidden），当然输出也会有h 0 h_0h0​,C 0 C_0C0​

```python
lstm = nn.LSTM(input_size=20,hidden_size=50,num_layers=2)

lstm_input = Variable(torch.randn(10, 3, 20))
out, (h, c) = lstm(lstm_input)
```

**3.GRU**

GRU本质上和LSTM一样

```python
gru_seq = nn.GRU(10, 20)
gru_input = Variable(torch.randn(3, 32, 10))

out, h = gru_seq(gru_input)
```

它和LSTM不同的地方：

- 参数是标准RNN的三倍
- 网络的隐藏状态只有h0

##### 5.3.2 实例介绍

序列预测

```python
import torch
import torch.nn as nn
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from torch.autograd import Variable
%matplotlib inline

#希望通过前两个月的流量来预测当月的流量
#将前两个月的流量当做输入，当月的流量当做输出
def create_dataset(dataset,look_back=2):
    dataX,dataY = [],[]
    for i in range(len(dataset)-look_back):
        a = dataset[i:(i+look_back)]
        dataX.append(a)
        dataY.append(dataset[i+look_back])
    return np.array(dataX),np.array(dataY)

# 定义模型
class lstm_reg(nn.Module):
    def __init__(self, input_size, hidden_size, output_size=1, num_layers=2):
        super(lstm_reg, self).__init__()
        
        self.rnn = nn.LSTM(input_size, hidden_size, num_layers) # rnn
        self.reg = nn.Linear(hidden_size, output_size) # 回归
        
    def forward(self, x):
        x, _ = self.rnn(x) # (seq, batch, hidden)
        s, b, h = x.shape
        x = x.view(s*b, h) # 转换成线性层的输入格式
        x = self.reg(x)
        x = x.view(s, b, -1)
        return x

#读取数据
data_csv = pd.read_csv('./data.csv', usecols=[1])

# 预处理，将数据中na的数据去掉，然后将数据标准化到0~1之间
data_csv = data_csv.dropna()
dataset = data_csv.values
dataset = dataset.astype('float32')
max_value = np.max(dataset)
min_value = np.min(dataset)
scalar = max_value - min_value
dataset = list(map(lambda x: x / scalar, dataset))

# 创建好输入输出
data_X, data_Y = create_dataset(dataset)

# 划分训练集和测试集，70% 作为训练集
train_size = int(len(data_X) * 0.7)
test_size = len(data_X) - train_size
train_X = data_X[:train_size]
train_Y = data_Y[:train_size]
test_X = data_X[train_size:]
test_Y = data_Y[train_size:]

#将数据改变一下形状 (seq, batch, feature)
#只有一个序列，所以 batch 是 1
#输入的feature是希望依据的几个月份，这里定的是两个月份，feature=2.
train_X = train_X.reshape(-1, 1, 2)
train_Y = train_Y.reshape(-1, 1, 1)
test_X = test_X.reshape(-1, 1, 2)

train_x = torch.from_numpy(train_X)
train_y = torch.from_numpy(train_Y)
test_x = torch.from_numpy(test_X)

# 定义损失和优化
net = lstm_reg(2, 4)
criterion = nn.MSELoss()
optimizer = torch.optim.Adam(net.parameters(), lr=1e-2)

# 开始训练
for e in range(1000):
    var_x = Variable(train_x)
    var_y = Variable(train_y)
    # 前向传播
    out = net(var_x)
    loss = criterion(out, var_y)
    # 反向传播
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
    if (e + 1) % 100 == 0: # 每 100 次输出结果
        print('Epoch: {}, Loss: {:.5f}'.format(e + 1, loss.data))
        
#测试
net = net.eval() # 转换成测试模式
data_X = data_X.reshape(-1, 1, 2)
data_X = torch.from_numpy(data_X)
var_data = Variable(data_X)
pred_test = net(var_data) # 测试集的预测结果

# 改变输出的格式
pred_test = pred_test.view(-1).data.numpy()

# 画出实际结果和预测的结果
plt.plot(pred_test, 'r', label='prediction')
plt.plot(dataset, 'b', label='real')
plt.legend(loc='best')
```

![](https://i-blog.csdnimg.cn/blog_migrate/bfa6a470d6cd4c893224cdea2015a37e.png)

#### 5.4 自然语言处理的应用

##### 5.4.1 词嵌入

词嵌入（word embedding），也称为词向量，即对于每个词，可以使用一个高维向量去表示它

例如：

- (1)The cat likes playing ball
- (2)The kitty likes playing wool
- (3)The dog likes playing ball
- (4)The boy doesn’t like playing ball

对于这四句话里的四个词，cat，kitty，dog，boy，如果用one-hot编码，那么cat可以是（1，0，0，0），kitty可以是（0，1，0，0），但是cat和kitty都是小猫，所以这两个词实际语义是接近的，但是one-hot不能体现这个特点，于是可以用词嵌入的方式表示这四个词。

假设使用一个二维向量（a，b）来表示一个词，其中a代表是否喜欢玩球，b代表是否喜欢玩毛线，且数值越大代表越喜欢，那么对于cat可以表示（-1，4），对于kitty可以表示为（-2，5），对于dog可以表示为（3，-2），对于boy可以表示为（-2，-3）

![](https://i-blog.csdnimg.cn/blog_migrate/cd535ec716b32eb647347a2960fcb958.png)

可以发现kitty和cat的夹角更小，所以它们更加相似

##### 5.4.2 词嵌入的PyTorch实现

PyTorch中的词嵌入是通过函数`nn.Embedding(m,n)`来实现的，其中m表示所有的单词数目，n表示词嵌入的维度

```python
word_to_ix = {'hello':0,'world':1}
embeds = nn.Embeding(2,5)
hello_idx = torch.LongTensor([word_to_ix['hello']])
hello_idx = Variable(hello_idx)
hello_embed = embeds(hello_idx)
print(hello_embed)
```

##### 5.4.3 N Gram模型

对于一句话，单词的排列顺序是非常重要的，所以我们能否由前面的几个词来预测后面的几个单词呢，比如 'I lived in France for 10 years, I can speak _ ’ 这句话中，我们能够预测出最后一个词是 French。

对于一句话T，它由w1，w2,…,wn这n个词构成，可以得到下面的公式  
P ( T ) = P ( w 1 ) P ( w 2 ∣ w 1 ) P ( w 3 ∣ w 2 w 1 ) ⋯ P ( w n ∣ w n − 1 w n − 2 ⋯ w 2 w 1 ) P(T) = P(w_1)P(w_2 | w_1)P(w_3 |w_2 w_1) \cdots P(w_n |w_{n-1} w_{n-2}\cdots w_2w_1)P(T)=P(w1​)P(w2​∣w1​)P(w3​∣w2​w1​)⋯P(wn​∣wn−1​wn−2​⋯w2​w1​)

但是该模型存在如参数空间过大等缺陷，因此引入了马尔科夫假设，也就是说这个单词只与前面的几个词有关系。

对于这个条件概率，传统的方式是统计语料中每个单词出现的频率，据此来估计这个条件概率，这里使用词嵌入的办法，直接在语料中计算这个条件概率，然后最大化条件概率从而优化词向量，据此进行预测

##### 5.4.4 单词预测的PyTorch实现

```python
import torch
from torch import nn
import torch.nn.functional as F
from torch.autograd import Variable

CONTEXT_SIZE = 2 # 依据的单词数
EMBEDDING_DIM = 10 # 词向量的维度

# 定义模型
class n_gram(nn.Module):
    def __init__(self, vocab_size, context_size=CONTEXT_SIZE, n_dim=EMBEDDING_DIM):
        super(n_gram, self).__init__()
        
        self.embed = nn.Embedding(vocab_size, n_dim)
        self.classify = nn.Sequential(
            nn.Linear(context_size * n_dim, 128),
            nn.ReLU(True),
            nn.Linear(128, vocab_size)
        )
        
    def forward(self, x):
        voc_embed = self.embed(x) # 得到词嵌入
        voc_embed = voc_embed.view(1, -1) # 将两个词向量拼在一起
        out = self.classify(voc_embed)
        return out

# 我们使用莎士比亚的诗
test_sentence = """When forty winters shall besiege thy brow,
And dig deep trenches in thy beauty's field,
Thy youth's proud livery so gazed on now,
Will be a totter'd weed of small worth held:
Then being asked, where all thy beauty lies,
Where all the treasure of thy lusty days;
To say, within thine own deep sunken eyes,
Were an all-eating shame, and thriftless praise.
How much more praise deserv'd thy beauty's use,
If thou couldst answer 'This fair child of mine
Shall sum my count, and make my old excuse,'
Proving his beauty by succession thine!
This were to be new made when thou art old,
And see thy blood warm when thou feel'st it cold.""".split()

trigram = [((test_sentence[i], test_sentence[i+1]), test_sentence[i+2]) 
            for i in range(len(test_sentence)-2)]

# 建立每个词与数字的编码，据此构建词嵌入
vocb = set(test_sentence) # 使用 set 将重复的元素去掉
word_to_idx = {word: i for i, word in enumerate(vocb)}
idx_to_word = {word_to_idx[word]: word for word in word_to_idx}

net = n_gram(len(word_to_idx))
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.SGD(net.parameters(), lr=1e-2, weight_decay=1e-5)

# 开始训练
for e in range(100):
    train_loss = 0
    for word, label in trigram: # 使用前 100 个作为训练集
        word = Variable(torch.LongTensor([word_to_idx[i] for i in word])) # 将两个词作为输入
        label = Variable(torch.LongTensor([word_to_idx[label]]))
        # 前向传播
        out = net(word)
        loss = criterion(out, label)
        train_loss += loss.data
        # 反向传播
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
    if (e + 1) % 20 == 0:
        print('epoch: {}, Loss: {:.6f}'.format(e + 1, train_loss / len(trigram)))
        
# 测试
word, label = trigram[19]
print('input: {}'.format(word))
print('label: {}'.format(label))

word = Variable(torch.LongTensor([word_to_idx[i] for i in word]))
out = net(word)
pred_label_idx = out.max(1)[1].item()
predict_word = idx_to_word[pred_label_idx]
print('real word is {}, predicted word is {}'.format(label, predict_word))
```

```txt
epoch: 20, Loss: 0.873597
epoch: 40, Loss: 0.153170
epoch: 60, Loss: 0.090456
epoch: 80, Loss: 0.071410
epoch: 100, Loss: 0.061979
input: ('so', 'gazed')
label: on

real word is on, predicted word is on
```

##### 5.4.5 词性判断

**1.LSTM做词性判断的基本原理**

同构LSTM，根据它记忆的特性，能够通过这个单词前面记忆的一些词语来对它做一个判断，比如前面的单词如果是my，那么紧跟的词很可能是一个名词，这样就能充分利用上文来处理这个问题

**2.字符增强**

通过引入字符来增强表达，比如有些单词存在前缀或者后缀，比如`-ly`这种后缀很有可能是副词，这样我们就能在字符水平对词性进一步判断，把两种方法集成起来，能够得到一个更好的结果

##### 5.4.6 词性判断的PyTorch实现

```python
import torch
from torch import nn
from torch.autograd import Variable

training_data = [("The dog ate the apple".split(),
                  ["DET", "NN", "V", "DET", "NN"]),
                 ("Everybody read that book".split(), 
                  ["NN", "V", "DET", "NN"])]

#对单词和标签进行编码
word_to_idx = {}
tag_to_idx = {}
for context, tag in training_data:
    for word in context:
        if word.lower() not in word_to_idx:
            word_to_idx[word.lower()] = len(word_to_idx)
    for label in tag:
        if label.lower() not in tag_to_idx:
            tag_to_idx[label.lower()] = len(tag_to_idx)

#对字母编码
alphabet = 'abcdefghijklmnopqrstuvwxyz'
char_to_idx = {}
for i in range(len(alphabet)):
    char_to_idx[alphabet[i]] = i
    
def make_sequence(x, dic): # 字符编码
    idx = [dic[i.lower()] for i in x]
    idx = torch.LongTensor(idx)
    return idx

#构建单个字符的lstm模型
class char_lstm(nn.Module):
    def __init__(self, n_char, char_dim, char_hidden):
        super(char_lstm, self).__init__()
        
        self.char_embed = nn.Embedding(n_char, char_dim)
        self.lstm = nn.LSTM(char_dim, char_hidden)
        
    def forward(self, x):
        x = self.char_embed(x)
        out, _ = self.lstm(x)
        return out[-1] # (batch, hidden)

#构建词性分类的lstm模型
class lstm_tagger(nn.Module):
    def __init__(self, n_word, n_char, char_dim, word_dim, 
                 char_hidden, word_hidden, n_tag):
        super(lstm_tagger, self).__init__()
        self.word_embed = nn.Embedding(n_word, word_dim)
        self.char_lstm = char_lstm(n_char, char_dim, char_hidden)
        self.word_lstm = nn.LSTM(word_dim + char_hidden, word_hidden)
        self.classify = nn.Linear(word_hidden, n_tag)
        
    def forward(self, x, word):
        char = []
        for w in word: # 对于每个单词做字符的 lstm
            char_list = make_sequence(w, char_to_idx)
            char_list = char_list.unsqueeze(1) # (seq, batch, feature) 满足 lstm 输入条件
            char_infor = self.char_lstm(Variable(char_list)) # (batch, char_hidden)
            char.append(char_infor)
        char = torch.stack(char, dim=0) # (seq, batch, feature)
        
        x = self.word_embed(x) # (batch, seq, word_dim)
        x = x.permute(1, 0, 2) # 改变顺序
        x = torch.cat((x, char), dim=2) # 沿着特征通道将每个词的词嵌入和字符 lstm 输出的结果拼接在一起
        x, _ = self.word_lstm(x)
        
        s, b, h = x.shape
        x = x.view(-1, h) # 重新 reshape 进行分类线性层
        out = self.classify(x)
        return out

net = lstm_tagger(len(word_to_idx), len(char_to_idx), 10, 100, 50, 128, len(tag_to_idx))
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.SGD(net.parameters(), lr=1e-2)

# 开始训练
for e in range(300):
    train_loss = 0
    for word, tag in training_data:
        word_list = make_sequence(word, word_to_idx).unsqueeze(0) # 添加第一维 batch
        tag = make_sequence(tag, tag_to_idx)
        word_list = Variable(word_list)
        tag = Variable(tag)
        # 前向传播
        out = net(word_list, word)
        loss = criterion(out, tag)
        train_loss += loss.data
        # 反向传播
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
    if (e + 1) % 50 == 0:
        print('Epoch: {}, Loss: {:.5f}'.format(e + 1, train_loss / len(training_data)))

#测试
net = net.eval()
test_sent = 'Everybody ate the apple'
test = make_sequence(test_sent.split(), word_to_idx).unsqueeze(0)
out = net(Variable(test), test_sent.split())
print(out)
print(tag_to_idx)
```

#### 5.5 循环神经网络的更多应用

##### 5.5.1 Many to one

循环神经网络不仅能够输入序列，输出序列，还能后输入序列，输出单个向量。只需要再输出的序列里面取其中一个就可以，通常是取最后一个。这样的结构被称为Many to one。

Many to one的结构可以用来执行什么任务：

- 情感分析
- 关键字提取

##### 5.5.2 Many to Many (shorter)

这种结构是输入和输出都是序列，但是输出的序列比输入的序列短。这种类型的结构通常在[语音识别](https://edu.csdn.net/cloud/sd_summit?utm_source=glcblog&spm=1001.2101.3001.7020)中遇到，因为一段话如果用语言表达往往会比这段话更长。这种情况需要使用CTC算法解决重复的问题，CTC就是将输出的所有可能列举出来，然后通过去重复，去空格的方式来选择最大的概率。

##### 5.5.3 Seq2seq

这种情况是输出的长度不确定，一般是在机器翻译的任务中出现。

##### 5.5.4 CNN+RNN

RNN和CNN可以联合在一起完成图像描述任务，简而言之，就是通过预训练的卷积神经网络提取图片特征，接着通过循环网络将特征变成文字描述

### 第6章 生成对抗网络

2014年，lan Goodfellow提出的生成对抗网络（Generative Adversarial Networks，GANs）推进了整个无监督学习的发展进程，让机器实现一些创造性工作，如画画，写诗，创作歌词等成为可能…

#### 6.1 生成模型

生成模型(Generative Model)这一概念属于概率统计和机器学习,是指一系列用于随机生成可观测数据的模型.简而言之,就是"生成"的样本和"真实"的样本尽可能地相似.

生成模型的两个主要功能就是学习一个概率分布P m o d e l ( x ) P_{model}(x)Pmodel​(x)和生成数据

##### 6.1.1 自动编码器

自动编码器(AutoEncoder)最开始作为一种数据的压缩方法,其特点有:

- 和数据相关程度很高
- 压缩后数据是有损的

所以现在自动编码器主要应用在几个方面:

- 数据去噪
- 可视化降维
- 生成数据

自动编码器的一般结构

- 编码器(Encoder)
- 解码器(Decoder)

编码器和解码器可以是任意的模型,通常使用神经网络模型作为编码器和解码器.输入的数据经过神经网络降维到一个编码(code),接着又通过另一个神经网络去解码得到一个与输入原数据一模一样的生成数据,然后通过比较这两个数据,最小化它们之间的差异来训练这个网络中编码器和解码器的参数.当这个过程训练完之后,拿出这个解码器,随机传入一个编码,通过解码器能够生成一个和原数据差不多的数据

下面我们使用 mnist 数据集来说明一个如何构建一个简单的自动编码器

```python
import os
import torch
from torch.autograd import Variable
from torch import nn
from torch.utils.data import DataLoader
from torchvision.datasets import MNIST
from torchvision import transforms as tfs
from torchvision.utils import save_image

#进行数据预处理和迭代器的构建
im_tfs = tfs.Compose([
    tfs.ToTensor(),
    tfs.Normalize([0.5], [0.5]) # 标准化
])

train_set = MNIST('./data', train=True,transform=im_tfs,download=True)
train_data = DataLoader(train_set, batch_size=128, shuffle=True)

#定义网络
class autoencoder(nn.Module):
    def __init__(self):
        super(autoencoder,self).__init__()
        self.encoder = nn.Sequential(
            nn.Linear(28*28,128),
            nn.ReLU(True),
            nn.Linear(128,64),
            nn.ReLU(True),
            nn.Linear(64,12),
            nn.ReLU(True),
            nn.Linear(12,3) # 输出的 code 是 3 维，便于可视化
        )
        self.decoder = nn.Sequential(
            nn.Linear(3,12),
            nn.ReLU(True),
            nn.Linear(12,64),
            nn.ReLU(True),
            nn.Linear(64,128),
            nn.ReLU(True),
            nn.Linear(128,28*28),
            nn.Tanh()
        )
    
    def forward(self,x):
        encode = self.encoder(x)
        decode = self.decoder(encode)
        return encode,decode
"""
这里定义的编码器和解码器都是 4 层神经网络作为模型，
中间使用 relu 激活函数，最后输出的 code 是三维，
注意解码器最后我们使用tanh作为激活函数，
因为输入图片标准化在 -1 ~ 1 之间，
所以输出也要在 -1 ~ 1 这个范围内
"""
net = autoencoder()
criterion = nn.MSELoss(size_average=False)
optimizer = torch.optim.Adam(net.parameters(), lr=1e-3)

def to_img(x):
    # 定义一个函数将最后的结果转换回图片
    x = 0.5 * (x + 1.)
    x = x.clamp(0, 1)
    x = x.view(x.shape[0], 1, 28, 28)
    return x

# 开始训练自动编码器
for e in range(100):
    for im, _ in train_data:
        im = im.view(im.shape[0], -1)
        im = Variable(im)
        # 前向传播
        _, output = net(im)
        loss = criterion(output, im) / im.shape[0] # 平均
        # 反向传播
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
    
    if (e+1) % 20 == 0: # 每 20 次，将生成的图片保存一下
        print('epoch: {}, Loss: {:.4f}'.format(e + 1, loss.data))
        pic = to_img(output.cpu().data)
        if not os.path.exists('./simple_autoencoder'):
            os.mkdir('./simple_autoencoder')
        save_image(pic, './simple_autoencoder/image_{}.png'.format(e + 1))
```

训练完成之后看看效果

```python
import matplotlib.pyplot as plt
from matplotlib import cm
from mpl_toolkits.mplot3d import Axes3D
%matplotlib inline

# 可视化结果
view_data = Variable((train_set.train_data[:200].type(torch.FloatTensor).view(-1, 28*28) / 255. - 0.5) / 0.5)
encode, _ = net(view_data)    # 提取压缩的特征值
fig = plt.figure(2)
ax = Axes3D(fig)    # 3D 图
# x, y, z 的数据值
X = encode.data[:, 0].numpy()
Y = encode.data[:, 1].numpy()
Z = encode.data[:, 2].numpy()
values = train_set.train_labels[:200].numpy()  # 标签值
for x, y, z, s in zip(X, Y, Z, values):
    c = cm.rainbow(int(255*s/9))    # 上色
    ax.text(x, y, z, s, backgroundcolor=c)  # 标位子
ax.set_xlim(X.min(), X.max())
ax.set_ylim(Y.min(), Y.max())
ax.set_zlim(Z.min(), Z.max())
plt.show()
```

![](https://i-blog.csdnimg.cn/blog_migrate/9ba51db83941ced89f4b2c0f4cfcad3b.png)  
可以看到，不同种类的图片进入自动编码器之后会被编码得不同，而相同类型的图片经过自动编码之后的编码在几何示意图上距离较近，在训练好自动编码器之后，我们可以给一个随机的 code，通过 decoder 生成图片

```python
code = Variable(torch.FloatTensor([[-20.19, 10.36, -0.06]])) # 给一个 code
decode = net.decoder(code)
decode_img = to_img(decode).squeeze()
decode_img = decode_img.data.numpy() * 255
plt.imshow(decode_img.astype('uint8'), cmap='gray') 
```

![](https://i-blog.csdnimg.cn/blog_migrate/83d6dc02b1f4c98925a5da67020fbb86.png)  
这里我们仅仅使用多层神经网络定义了一个自动编码器，当然你会想到，为什么不使用效果更好的卷积神经网络呢？我们当然可以使用卷积神经网络来定义，下面我们就重新定义一个卷积神经网络来进行 autoencoder

```python
class conv_autoencoder(nn.Module):
    def __init__(self):
        super(conv_autoencoder, self).__init__()
        
        self.encoder = nn.Sequential(
            nn.Conv2d(1, 16, 3, stride=3, padding=1),  # (b, 16, 10, 10)
            nn.ReLU(True),
            nn.MaxPool2d(2, stride=2),  # (b, 16, 5, 5)
            nn.Conv2d(16, 8, 3, stride=2, padding=1),  # (b, 8, 3, 3)
            nn.ReLU(True),
            nn.MaxPool2d(2, stride=1)  # (b, 8, 2, 2)
        )
        
        self.decoder = nn.Sequential(
            nn.ConvTranspose2d(8, 16, 3, stride=2),  # (b, 16, 5, 5)
            nn.ReLU(True),
            nn.ConvTranspose2d(16, 8, 5, stride=3, padding=1),  # (b, 8, 15, 15)
            nn.ReLU(True),
            nn.ConvTranspose2d(8, 1, 2, stride=2, padding=1),  # (b, 1, 28, 28)
            nn.Tanh()
        )

    def forward(self, x):
        encode = self.encoder(x)
        decode = self.decoder(encode)
        return encode, decode

conv_net = conv_autoencoder()
if torch.cuda.is_available():
    conv_net = conv_net.cuda()
optimizer = torch.optim.Adam(conv_net.parameters(), lr=1e-3, weight_decay=1e-5)

# 开始训练自动编码器
for e in range(40):
    for im, _ in train_data:
        if torch.cuda.is_available():
            im = im.cuda()
            print(torch.device("cuda"))
        im = Variable(im)
        # 前向传播
        _, output = conv_net(im)
        loss = criterion(output, im) / im.shape[0] # 平均
        # 反向传播
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()
    
    if (e+1) % 20 == 0: # 每 20 次，将生成的图片保存一下
        print('epoch: {}, Loss: {:.4f}'.format(e+1, loss.data))
        pic = to_img(output.cpu().data)
        if not os.path.exists('./conv_autoencoder'):
            os.mkdir('./conv_autoencoder')
        save_image(pic, './conv_autoencoder/image_{}.png'.format(e+1))
```

为了时间更短，只跑 40 次，如果有条件可以再 gpu 上跑跑.这里我们展示了简单的自动编码器，也用了多层神经网络和卷积神经网络作为例子，但是自动编码器存在一个问题，我们并不能任意生成我们想要的数据，因为我们并不知道 encode 之后的编码到底是什么样的概率分布，所以有一个改进的版本变分自动编码器，其能够解决这个问题

##### 6.1.2 变分自动编码器

变分自动编码器（Variational Auto Encoder, VAE）是自动编码器的升级版本，它的结构和自动编码器相似，也是由编码器和解码器构成的。

自动编码器不能任意生成数据，因为没办法自己去构造隐藏向量，需要通过数据输入编码才知道得到的隐含向量是什么，这个时候变分自动编码器就可以解决这个问题

它的原理是，在编码过程给他增加一些限制，迫使他生成的隐含向量能够粗略地遵循一个标准正态分布。

这样我们生成一张新图片就很简单了，我们只需要给它一个标准正态分布的随机隐含向量，这样通过解码器就能够生成我们想要的图片，而不需要给它一张原始图片先编码。

一般来讲，我们通过 encoder 得到的隐含向量并不是一个标准的正态分布，为了衡量两种分布的相似程度，我们使用 KL divergence，利用其来表示隐含向量与标准正态分布之间差异的 loss，另外一个 loss 仍然使用生成图片与原图片的均方误差来表示。

KL divergence 的公式如下  
D K L ( P ∣ ∣ Q ) = ∑ i p ( i ) log ⁡ P ( i ) Q ( i ) D_{KL} (P || Q) = \sum_{i} p(i) \log \frac{P(i)}{Q(i)}DKL​(P∣∣Q)=i∑​p(i)logQ(i)P(i)​  
D K L ( P ∣ ∣ Q ) = ∫ − ∞ ∞ p ( x ) log ⁡ p ( x ) q ( x ) d x D_{KL} (P || Q) = \int_{-\infty}^{\infty} p(x) \log \frac{p(x)}{q(x)} dxDKL​(P∣∣Q)=∫−∞∞​p(x)logq(x)p(x)​dx

**重参数**

为了避免计算 KL divergence 中的积分，我们使用重参数的技巧，不是每次产生一个隐含向量，而是生成两个向量，一个表示均值，一个表示标准差，这里我们默认编码之后的隐含向量服从一个正态分布的之后，就可以用一个标准正态分布先乘上标准差再加上均值来合成这个正态分布，最后 loss 就是希望这个生成的正态分布能够符合一个标准正态分布，也就是希望均值为 0，方差为 1

[详细内容见https://arxiv.org/pdf/1606.05908.pdf](https://arxiv.org/pdf/1606.05908.pdf)

所以最后我们可以将我们的 loss 定义为下面的函数，由均方误差和 KL divergence 求和得到一个总的 loss

```python
reconstruction_funtion = nn.BCELoss(size_average=False)

def loss_function(recon_x, x, mu, logvar):
    """
    recon_x: generating images
    x: origin images
    mu: latent mean
    logvar: latent log variance
    """
    MSE = reconstruction_function(recon_x, x)
    # loss = 0.5 * sum(1 + log(sigma^2) - mu^2 - sigma^2)
    KLD_element = mu.pow(2).add_(logvar.exp()).mul_(-1).add_(1).add_(logvar)
    KLD = torch.sum(KLD_element).mul_(-0.5)
    # KL divergence
    return MSE + KLD
```

下面我们用 mnist 数据集来简单说明一下变分自动编码器

```python
import os
import torch
from torch.autograd import Variable
import torch.nn.functional as F
from torch import nn
from torch.utils.data import DataLoader
from torchvision.datasets import MNIST
from torchvision import transforms as tfs
from torchvision.utils import save_image

im_tfs = tfs.Compose([
    tfs.ToTensor(),
    tfs.Normalize([0.5], [0.5]) # 标准化
])

train_set = MNIST('./data', transform=im_tfs)
train_data = DataLoader(train_set, batch_size=128, shuffle=True)

class VAE(nn.Module):
    def __init__(self):
        super(VAE, self).__init__()
        self.fc1 = nn.Linear(784, 400)
        self.fc21 = nn.Linear(400, 20) # mean
        self.fc22 = nn.Linear(400, 20) # var
        self.fc3 = nn.Linear(20, 400)
        self.fc4 = nn.Linear(400, 784)

    def encode(self, x):
        h1 = F.relu(self.fc1(x))
        return self.fc21(h1), self.fc22(h1)

    def reparametrize(self, mu, logvar):
        std = logvar.mul(0.5).exp_()
        eps = torch.FloatTensor(std.size()).normal_()
        if torch.cuda.is_available():
            eps = Variable(eps.cuda())
        else:
            eps = Variable(eps)
        return eps.mul(std).add_(mu)

    def decode(self, z):
        h3 = F.relu(self.fc3(z))
        return F.tanh(self.fc4(h3))

    def forward(self, x):
        mu, logvar = self.encode(x) # 编码
        z = self.reparametrize(mu, logvar) # 重新参数化成正态分布
        return self.decode(z), mu, logvar # 解码，同时输出均值方差

net = VAE() # 实例化网络
if torch.cuda.is_available():
    net = net.cuda()

reconstruction_function = nn.MSELoss(size_average=False)

def loss_function(recon_x, x, mu, logvar):
    """
    recon_x: generating images
    x: origin images
    mu: latent mean
    logvar: latent log variance
    """
    MSE = reconstruction_function(recon_x, x)
    # loss = 0.5 * sum(1 + log(sigma^2) - mu^2 - sigma^2)
    KLD_element = mu.pow(2).add_(logvar.exp()).mul_(-1).add_(1).add_(logvar)
    KLD = torch.sum(KLD_element).mul_(-0.5)
    # KL divergence
    return MSE + KLD

optimizer = torch.optim.Adam(net.parameters(), lr=1e-3)

def to_img(x):
    #定义一个函数将最后的结果转换回图片
    x = 0.5 * (x + 1.)
    x = x.clamp(0, 1)
    x = x.view(x.shape[0], 1, 28, 28)
    return x

for e in range(100):
    for im, _ in train_data:
        im = im.view(im.shape[0], -1)
        im = Variable(im)
        if torch.cuda.is_available():
            im = im.cuda()
            print(torch.device("cuda"))
        recon_im, mu, logvar = net(im)
        loss = loss_function(recon_im, im, mu, logvar) / im.shape[0] # 将 loss 平均
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

    if (e + 1) % 20 == 0:
        print('epoch: {}, Loss: {:.4f}'.format(e + 1, loss.data[0]))
        save = to_img(recon_im.cpu().data)
        if not os.path.exists('./vae_img'):
            os.mkdir('./vae_img')
        save_image(save, './vae_img/image_{}.png'.format(e + 1))
```

可以看看使用变分自动编码器得到的结果，可以发现效果比一般的编码器要好很多

#### 6.2 生成对抗网络

前面我们讲了自动编码器和变分自动编码器，不管是哪一个，都是通过计算生成图像和输入图像在每个像素点的误差来生成 loss，这一点是特别不好的，因为不同的像素点可能造成不同的视觉结果，但是可能他们的 loss 是相同的，所以通过单个像素点来得到 loss 是不准确的，这个时候我们需要一种全新的 loss 定义方式，就是通过对抗进行学习。

##### 6.2.1 什么是生成对抗网络

这种训练方式定义了一种全新的网络结构，就是生成对抗网络，也就是 GANs。

根据这个名字就可以知道这个网络是由两部分组成的，第一部分是生成，第二部分是对抗。简单来说，就是有一个生成网络和一个判别网络，通过训练让两个网络相互竞争，生成网络来生成假的数据，对抗网络通过判别器去判别真伪，最后希望生成器生成的数据能够以假乱真。

**对抗：Discriminator Network**

首先我们来讲一下对抗过程，因为这个过程更加简单。

对抗过程简单来说就是一个判断真假的判别器，相当于一个二分类问题，我们输入一张真的图片希望判别器输出的结果是1，输入一张假的图片希望判别器输出的结果是0。这其实已经和原图片的 label 没有关系了，不管原图片到底是一个多少类别的图片，他们都统一称为真的图片，label 是 1 表示真实的；而生成的假的图片的 label 是 0 表示假的。

我们训练的过程就是希望这个判别器能够正确的判出真的图片和假的图片，这其实就是一个简单的二分类问题，对于这个问题可以用我们前面讲过的很多方法去处理，比如 logistic 回归，深层网络，卷积神经网络，循环神经网络都可以。

**生成：Generator Network**

接着我们看看生成网络如何生成一张假的图片。首先给出一个简单的高维的正态分布的噪声向量，这个时候我们可以通过仿射变换，也就是 xw+b 将其映射到一个更高的维度，然后将他重新排列成一个矩形，这样看着更像一张图片，接着进行一些卷积、转置卷积、池化、激活函数等进行处理，最后得到了一个与我们输入图片大小一模一样的噪音矩阵，这就是我们所说的假的图片。

这个时候我们如何去训练这个生成器呢？这就需要通过对抗学习，增大判别器判别这个结果为真的概率，通过这个步骤不断调整生成器的参数，希望生成的图片越来越像真的，而在这一步中我们不会更新判别器的参数，因为如果判别器不断被优化，可能生成器无论生成什么样的图片都无法骗过判别器。

关于生成对抗网络，出现了很多变形，比如 WGAN，LS-GAN 等等，这里我们只使用 mnist 举一些简单的例子来说明，更复杂的网络结构可以在 github 上找到相应的实现

```python
import torch
from torch import nn
from torch.autograd import Variable

import torchvision.transforms as tfs
from torch.utils.data import DataLoader, sampler
from torchvision.datasets import MNIST

import numpy as np

import matplotlib.pyplot as plt
import matplotlib.gridspec as gridspec

%matplotlib inline
plt.rcParams['figure.figsize'] = (10.0, 8.0) # 设置画图的尺寸
plt.rcParams['image.interpolation'] = 'nearest'
plt.rcParams['image.cmap'] = 'gray'

def show_images(images): # 定义画图工具
    images = np.reshape(images, [images.shape[0], -1])
    sqrtn = int(np.ceil(np.sqrt(images.shape[0])))
    sqrtimg = int(np.ceil(np.sqrt(images.shape[1])))

    fig = plt.figure(figsize=(sqrtn, sqrtn))
    gs = gridspec.GridSpec(sqrtn, sqrtn)
    gs.update(wspace=0.05, hspace=0.05)

    for i, img in enumerate(images):
        ax = plt.subplot(gs[i])
        plt.axis('off')
        ax.set_xticklabels([])
        ax.set_yticklabels([])
        ax.set_aspect('equal')
        plt.imshow(img.reshape([sqrtimg,sqrtimg]))
    return 

def preprocess_img(x):
    x = tfs.ToTensor()(x)
    return (x - 0.5) / 0.5

def deprocess_img(x):
    return (x + 1.0) / 2.0

class ChunkSampler(sampler.Sampler): # 定义一个取样的函数
    """Samples elements sequentially from some offset. 
    Arguments:
        num_samples: # of desired datapoints
        start: offset where we should start selecting from
    """
    def __init__(self, num_samples, start=0):
        self.num_samples = num_samples
        self.start = start

    def __iter__(self):
        return iter(range(self.start, self.start + self.num_samples))

    def __len__(self):
        return self.num_samples

NUM_TRAIN = 50000
NUM_VAL = 5000

NOISE_DIM = 96
batch_size = 128

train_set = MNIST('./data', train=True, download=True, transform=preprocess_img)

train_data = DataLoader(train_set, batch_size=batch_size, sampler=ChunkSampler(NUM_TRAIN, 0))

val_set = MNIST('./data', train=True, download=True, transform=preprocess_img)

val_data = DataLoader(val_set, batch_size=batch_size, sampler=ChunkSampler(NUM_VAL, NUM_TRAIN))

imgs = deprocess_img(train_data.__iter__().next()[0].view(batch_size, 784)).numpy().squeeze() # 可视化图片效果
show_images(imgs)
```

![](https://i-blog.csdnimg.cn/blog_migrate/94755f6929b7c26fd7916bff56249681.png)

**简单版本的生成对抗网络**

通过前面我们知道生成对抗网络有两个部分构成，一个是生成网络，一个是对抗网络，我们首先写一个简单版本的网络结构，生成网络和对抗网络都是简单的多层神经网络

**判别网络**

判别网络的结构非常简单，就是一个二分类器，结构如下:

- 全连接(784 -> 256)
- leakyrelu, α \alphaα 是 0.2
- 全连接(256 -> 256)
- leakyrelu, α \alphaα 是 0.2
- 全连接(256 -> 1)

其中 leakyrelu 是指 f(x) = max(α \alphaα x, x)

```python
def discriminator():
    net = nn.Sequential(        
            nn.Linear(784, 256),
            nn.LeakyReLU(0.2),
            nn.Linear(256, 256),
            nn.LeakyReLU(0.2),
            nn.Linear(256, 1)
        )
    return net
```

**生成网络**

接下来我们看看生成网络，生成网络的结构也很简单，就是根据一个随机噪声生成一个和数据维度一样的张量，结构如下：

- 全连接(噪音维度 -> 1024)
- relu
- 全连接(1024 -> 1024)
- relu
- 全连接(1024 -> 784)
- tanh 将数据裁剪到 -1 ~ 1 之间

```python
def generator(noise_dim=NOISE_DIM):   
    net = nn.Sequential(
        nn.Linear(noise_dim, 1024),
        nn.ReLU(True),
        nn.Linear(1024, 1024),
        nn.ReLU(True),
        nn.Linear(1024, 784),
        nn.Tanh()
    )
    return net
```

接下来我们需要定义生成对抗网络的 loss，通过前面的讲解我们知道，对于对抗网络，相当于二分类问题，将真的判别为真的，假的判别为假的，作为辅助，可以参考一下论文中公式

ℓ D = E x ∼ p data [ log ⁡ D ( x ) ] + E z ∼ p ( z ) [ log ⁡ ( 1 − D ( G ( z ) ) ) ] \ell_D = \mathbb{E}_{x \sim p_\text{data}}\left[\log D(x)\right] + \mathbb{E} _ {z \sim p(z)}\left[\log \left(1-D(G(z))\right)\right]ℓD​=Ex∼pdata​​[logD(x)]+Ez∼p(z)​[log(1−D(G(z)))]

而对于生成网络，需要去骗过对抗网络，也就是将假的也判断为真的，作为辅助，可以参考一下论文中公式

ℓ G = E z ∼ p ( z ) [ log ⁡ D ( G ( z ) ) ] \ell_G = \mathbb{E} _ {z \sim p(z)}\left[\log D(G(z))\right]ℓG​=Ez∼p(z)​[logD(G(z))]

如果你还记得前面的二分类 loss，那么你就会发现上面这两个公式就是二分类 loss

b c e ( s , y ) = y ∗ log ⁡ ( s ) + ( 1 − y ) ∗ log ⁡ ( 1 − s ) bce(s, y) = y * \log(s) + (1 - y) * \log(1 - s)bce(s,y)=y∗log(s)+(1−y)∗log(1−s)

如果我们把 D(x) 看成真实数据的分类得分，那么 D(G(z)) 就是假数据的分类得分，所以上面判别器的 loss 就是将真实数据的得分判断为 1，假的数据的得分判断为 0，而生成器的 loss 就是将假的数据判断为 1

下面我们来实现一下

```python
import torch
from torch import nn
from torch.autograd import Variable

import torchvision.transforms as tfs
from torch.utils.data import DataLoader, sampler
from torchvision.datasets import MNIST

import numpy as np

NUM_TRAIN = 50000
NUM_VAL = 5000

NOISE_DIM = 96
batch_size = 128

def discriminator():
    net = nn.Sequential(        
            nn.Linear(784, 256),
            nn.LeakyReLU(0.2),
            nn.Linear(256, 256),
            nn.LeakyReLU(0.2),
            nn.Linear(256, 1)
        )
    return net

def generator(noise_dim=NOISE_DIM):   
    net = nn.Sequential(
        nn.Linear(noise_dim, 1024),
        nn.ReLU(True),
        nn.Linear(1024, 1024),
        nn.ReLU(True),
        nn.Linear(1024, 784),
        nn.Tanh()
    )
    return net

bce_loss = nn.BCEWithLogitsLoss()

def discriminator_loss(logits_real, logits_fake): # 判别器的 loss
    size = logits_real.shape[0]
    true_labels = Variable(torch.ones(size, 1)).float().cuda()
    false_labels = Variable(torch.zeros(size, 1)).float().cuda()
    loss = bce_loss(logits_real, true_labels) + bce_loss(logits_fake, false_labels)
    return loss

def generator_loss(logits_fake): # 生成器的 loss  
    size = logits_fake.shape[0]
    true_labels = Variable(torch.ones(size, 1)).float().cuda()
    loss = bce_loss(logits_fake, true_labels)
    return loss

# 使用 adam 来进行训练，学习率是 3e-4, beta1 是 0.5, beta2 是 0.999
def get_optimizer(net):
    optimizer = torch.optim.Adam(net.parameters(), lr=3e-4, betas=(0.5, 0.999))
    return optimizer

def preprocess_img(x):
    x = tfs.ToTensor()(x)
    return (x - 0.5) / 0.5

def deprocess_img(x):
    return (x + 1.0) / 2.0

class ChunkSampler(sampler.Sampler): # 定义一个取样的函数
    """Samples elements sequentially from some offset. 
    Arguments:
        num_samples: # of desired datapoints
        start: offset where we should start selecting from
    """
    def __init__(self, num_samples, start=0):
        self.num_samples = num_samples
        self.start = start

    def __iter__(self):
        return iter(range(self.start, self.start + self.num_samples))

    def __len__(self):
        return self.num_samples

train_set = MNIST('./data', train=True, download=True, transform=preprocess_img)

train_data = DataLoader(train_set, batch_size=batch_size, sampler=ChunkSampler(NUM_TRAIN, 0))

val_set = MNIST('./data', train=True, download=True, transform=preprocess_img)

val_data = DataLoader(val_set, batch_size=batch_size, sampler=ChunkSampler(NUM_VAL, NUM_TRAIN))

#下面我们开始训练一个这个简单的生成对抗网络
def train_a_gan(D_net, G_net, D_optimizer, G_optimizer, discriminator_loss, generator_loss, show_every=250, 
                noise_size=96, num_epochs=10):
    iter_count = 0
    for epoch in range(num_epochs):
        for x, _ in train_data:
            bs = x.shape[0]
            # 判别网络
            real_data = Variable(x).view(bs, -1).cuda() # 真实数据
            logits_real = D_net(real_data) # 判别网络得分
            
            sample_noise = (torch.rand(bs, noise_size) - 0.5) / 0.5 # -1 ~ 1 的均匀分布
            g_fake_seed = Variable(sample_noise).cuda()
            fake_images = G_net(g_fake_seed) # 生成的假的数据
            logits_fake = D_net(fake_images) # 判别网络得分

            d_total_error = discriminator_loss(logits_real, logits_fake) # 判别器的 loss
            D_optimizer.zero_grad()
            d_total_error.backward()
            D_optimizer.step() # 优化判别网络
            
            # 生成网络
            g_fake_seed = Variable(sample_noise).cuda()
            fake_images = G_net(g_fake_seed) # 生成的假的数据

            gen_logits_fake = D_net(fake_images)
            g_error = generator_loss(gen_logits_fake) # 生成网络的 loss
            G_optimizer.zero_grad()
            g_error.backward()
            G_optimizer.step() # 优化生成网络

            if (iter_count % show_every == 0):
                print('Iter: {}, D: {:.4}, G:{:.4}'.format(iter_count, d_total_error.data, g_error.data))
                imgs_numpy = deprocess_img(fake_images.data.cpu().numpy())
                show_images(imgs_numpy[0:16])
                plt.show()
                print()
            iter_count += 1
```

```python
D = discriminator().cuda()
G = generator().cuda()

D_optim = get_optimizer(D)
G_optim = get_optimizer(G)

train_a_gan(D, G, D_optim, G_optim, discriminator_loss, generator_loss)
```

![](https://i-blog.csdnimg.cn/blog_migrate/53cac4044df2c91341d54dc575087acf.gif)

我们已经完成了一个简单的生成对抗网络，是不是非常容易呢。但是可以看到效果并不是特别好，生成的数字也不是特别完整，因为我们仅仅使用了简单的多层全连接网络。

除了这种最基本的生成对抗网络之外，还有很多生成对抗网络的变式，有结构上的变式，也有 loss 上的变式，我们先讲一讲其中一种在 loss 上的变式，Least Squares GAN

**Least Squares GAN**

[Least Squares GAN](https://arxiv.org/abs/1611.04076) 比最原始的 GANs 的 loss 更加稳定，通过名字我们也能够看出这种 GAN 是通过最小平方误差来进行估计，而不是通过二分类的损失函数，下面我们看看 loss 的计算公式

ℓ G = 1 2 E z ∼ p ( z ) [ ( D ( G ( z ) ) − 1 ) 2 ] \ell_G = \frac{1}{2}\mathbb{E} _ {z \sim p(z)}\left[\left(D(G(z))-1\right)^2\right]ℓG​=21​Ez∼p(z)​[(D(G(z))−1)2]

ℓ D = 1 2 E x ∼ p data [ ( D ( x ) − 1 ) 2 ] + 1 2 E z ∼ p ( z ) [ ( D ( G ( z ) ) ) 2 ] \ell_D = \frac{1}{2}\mathbb{E}_{x \sim p_\text{data}}\left[\left(D(x)-1\right)^2\right] + \frac{1}{2}\mathbb{E} _ {z \sim p(z)}\left[ \left(D(G(z))\right)^2\right]ℓD​=21​Ex∼pdata​​[(D(x)−1)2]+21​Ez∼p(z)​[(D(G(z)))2]

可以看到 Least Squares GAN 通过最小二乘代替了二分类的 loss，下面我们定义一下 loss 函数

```python
def ls_discriminator_loss(scores_real, scores_fake):
    loss = 0.5 * ((scores_real - 1) ** 2).mean() + 0.5 * (scores_fake ** 2).mean()
    return loss

def ls_generator_loss(scores_fake):
    loss = 0.5 * ((scores_fake - 1) ** 2).mean()
    return loss
```

```python
D = discriminator().cuda()
G = generator().cuda()

D_optim = get_optimizer(D)
G_optim = get_optimizer(G)

train_a_gan(D, G, D_optim, G_optim, ls_discriminator_loss, ls_generator_loss)
```

![](https://i-blog.csdnimg.cn/blog_migrate/a22e4431b9e414a29862d817c3039e80.gif)

上面我们讲了 最基本的 GAN 和 least squares GAN，最后我们讲一讲使用卷积网络的 GAN，叫做深度卷积生成对抗网络

**Deep Convolutional GANs**

深度卷积生成对抗网络特别简单，就是将生成网络和对抗网络都改成了卷积网络的形式，下面我们来实现一下

卷积判别网络就是一个一般的卷积网络，结构如下

- 32 Filters, 5x5, Stride 1, Leaky ReLU(alpha=0.01)
- Max Pool 2x2, Stride 2
- 64 Filters, 5x5, Stride 1, Leaky ReLU(alpha=0.01)
- Max Pool 2x2, Stride 2
- Fully Connected size 4 x 4 x 64, Leaky ReLU(alpha=0.01)
- Fully Connected size 1

```python
class build_dc_classifier(nn.Module):
    def __init__(self):
        super(build_dc_classifier, self).__init__()
        self.conv = nn.Sequential(
            nn.Conv2d(1, 32, 5, 1),
            nn.LeakyReLU(0.01),
            nn.MaxPool2d(2, 2),
            nn.Conv2d(32, 64, 5, 1),
            nn.LeakyReLU(0.01),
            nn.MaxPool2d(2, 2)
        )
        self.fc = nn.Sequential(
            nn.Linear(1024, 1024),
            nn.LeakyReLU(0.01),
            nn.Linear(1024, 1)
        )
        
    def forward(self, x):
        x = self.conv(x)
        x = x.view(x.shape[0], -1)
        x = self.fc(x)
        return x
```

卷积生成网络需要将一个低维的噪声向量变成一个图片数据，结构如下

- Fully connected of size 1024, ReLU
- BatchNorm
- Fully connected of size 7 x 7 x 128, ReLU
- BatchNorm
- Reshape into Image Tensor
- 64 conv2d^T filters of 4x4, stride 2, padding 1, ReLU
- BatchNorm
- 1 conv2d^T filter of 4x4, stride 2, padding 1, TanH

```python
class build_dc_generator(nn.Module): 
    def __init__(self, noise_dim=NOISE_DIM):
        super(build_dc_generator, self).__init__()
        self.fc = nn.Sequential(
            nn.Linear(noise_dim, 1024),
            nn.ReLU(True),
            nn.BatchNorm1d(1024),
            nn.Linear(1024, 7 * 7 * 128),
            nn.ReLU(True),
            nn.BatchNorm1d(7 * 7 * 128)
        )
        
        self.conv = nn.Sequential(
            nn.ConvTranspose2d(128, 64, 4, 2, padding=1),
            nn.ReLU(True),
            nn.BatchNorm2d(64),
            nn.ConvTranspose2d(64, 1, 4, 2, padding=1),
            nn.Tanh()
        )
        
    def forward(self, x):
        x = self.fc(x)
        x = x.view(x.shape[0], 128, 7, 7) # reshape 通道是 128，大小是 7x7
        x = self.conv(x)
        return x

def train_dc_gan(D_net, G_net, D_optimizer, G_optimizer, discriminator_loss, generator_loss, show_every=250, 
                noise_size=96, num_epochs=10):
    iter_count = 0
    for epoch in range(num_epochs):
        for x, _ in train_data:
            bs = x.shape[0]
            # 判别网络
            real_data = Variable(x).cuda() # 真实数据
            logits_real = D_net(real_data) # 判别网络得分
            
            sample_noise = (torch.rand(bs, noise_size) - 0.5) / 0.5 # -1 ~ 1 的均匀分布
            g_fake_seed = Variable(sample_noise).cuda()
            fake_images = G_net(g_fake_seed) # 生成的假的数据
            logits_fake = D_net(fake_images) # 判别网络得分

            d_total_error = discriminator_loss(logits_real, logits_fake) # 判别器的 loss
            D_optimizer.zero_grad()
            d_total_error.backward()
            D_optimizer.step() # 优化判别网络
            
            # 生成网络
            g_fake_seed = Variable(sample_noise).cuda()
            fake_images = G_net(g_fake_seed) # 生成的假的数据

            gen_logits_fake = D_net(fake_images)
            g_error = generator_loss(gen_logits_fake) # 生成网络的 loss
            G_optimizer.zero_grad()
            g_error.backward()
            G_optimizer.step() # 优化生成网络

            if (iter_count % show_every == 0):
                print('Iter: {}, D: {:.4}, G:{:.4}'.format(iter_count, d_total_error.data, g_error.data))
                imgs_numpy = deprocess_img(fake_images.data.cpu().numpy())
                show_images(imgs_numpy[0:16])
                plt.show()
                print()
            iter_count += 1

D_DC = build_dc_classifier().cuda()
G_DC = build_dc_generator().cuda()

D_DC_optim = get_optimizer(D_DC)
G_DC_optim = get_optimizer(G_DC)

train_dc_gan(D_DC, G_DC, D_DC_optim, G_DC_optim, discriminator_loss, generator_loss, num_epochs=5)
```

![](https://i-blog.csdnimg.cn/blog_migrate/98ff6fcd0e99c6612489747d2b553a75.gif)  
可以看到，通过 DCGANs 能够得到更加清楚的结果

#### 6.3 Improving GAN

##### 6.3.1 Wasserstein GAN

Wasserstein GAN是GAN的一种变式，WGAN的出现解决了下面这些难点

- 彻底解决了训练不稳定的问题
- 基本解决了coolapse mode 的问题，确保了生成样本的多样性
- 训练中有一个向交叉熵，准确率的数值指标来衡量训练的进程，数值越小代表GAN训练得越好，同时也代表着生成的图片质量越高
- 不需要精心设计网络结构也能取得较好的效果

#### 6.4 应用介绍

##### 6.4.1 Conditional GAN

Conditional GAN的一个应用是文字生成图片

##### 6.4.2 Cycle GAN

根据一个人的作品，想象他完成其他场景会是什么样

### 第七章 深度学习实战

#### 7.1 实例一，猫狗大战：运用预训练卷积神经网络进行特征提取与预训

##### 7.1.1 背景介绍

Asirra是一个图像识别机制的验证码，其有很多不同猫狗的照片（三百万张），可以用他的子集当作训练集

##### 7.1.2 原理分析

对于这个问题，简单的网络模型可能效果并不好，这个时候，使用一些成熟的模型，比如VggNet，GoogleNet，ResNet等可以帮助我们解决问题，为了节省计算资源和时间，可以通过迁移学习实现。

**迁移学习**

对于一个特定任务，如果没有来自该任务足够的数据集，传统的监督学习无法支持，而迁移学习允许通过借用已经存在的一些相关任务的标签数据来处理这些场景，把解决相关任务时获得的知识存储下来，并将它应用到我们感兴趣的目标任务中。

卷积神经网络可以理解为两个部分：前面的**卷积**部分和后面的**分类**部分，卷积部分主要用于提取图片特征，而预训练的网络对于特征提取效果已经非常好。我们可以直接用预训练的网络卷积部分来提取我们自己的图片特征，而对于自己的任务，比如猫狗二分类，就用自己的分类全连接层即可。

当然，迁移学习并不是任何时候都能使用，需要它们**完成的任务是相关的**，所以迁移学习在相似数据集上的应用效果才是良好的。

**实现方法**

1. 第一种方法：导入预训练的卷积网络，将最后的全连接层改成我们自己设计的全连接层，然后更新整个网络，最后能特别快地达到收敛
2. 第二种方法：锁定前面卷积层的参数，让网络训练只更新最后全连接层的参数，可以使训练时间大大减少
3. 第三种方法：使用多个预训练好的网络，将它们并联在一起，图片经过每个网络都会得到特征图，我们将这些特征图拼接在一起进入最后的全连接层

##### 7.1.3 代码实现

1.数据预处理

数据集可以去 [https://www.kaggle.com/c/dogs-vs-cats/data](https://www.kaggle.com/c/dogs-vs-cats/data) 下载

```python
import os
import shutil

train_root = './data/dogs-vs-cats/train/'
val_root = './data/dogs-vs-cats/val/'
data_file=os.listdir(train_root)
#print(data_file)
dog_file = list(filter(lambda x:x.split(".")[0]=='dog'and x!="dog",data_file))
cat_file = list(filter(lambda x:x.split(".")[0]=='cat'and x!="cat",data_file))

root = './data/dogs-vs-cats/'
if not os.path.exists(train_root+'dog/'):
    os.makedirs(train_root+'dog/')
if not os.path.exists(train_root+'cat/'):
    os.makedirs(train_root+'cat/')
if not os.path.exists(val_root+'dog/'):
    os.makedirs(val_root+'dog/')
if not os.path.exists(val_root+'cat/'):
    os.makedirs(val_root+'cat/')

for i in range(len(dog_file)):
    pic_path = root+'train/'+dog_file[i]
    if i < len(dog_file)*0.9:
        obj_path = train_root+'dog/'+dog_file[i]
    else:
        obj_path = val_root+'dog/'+dog_file[i]
    shutil.move(pic_path,obj_path)

for i in range(len(cat_file)):
    pic_path = root+'train/'+cat_file[i]
    if i < len(cat_file)*0.9:
        obj_path = train_root+'cat/'+cat_file[i]
    else:
        obj_path = val_root+'cat/'+cat_file[i]
    shutil.move(pic_path,obj_path)
```

上面的操作实现了，将猫狗照片分别移动到训练集和验证集，其中90%的数据作为训练集，10%的图片作为验证集，使用`shutil.move()`来移动图片

2.迁移学习模型训练

```python
import torch
import torch.nn as nn
import torchvision
from torch.autograd import Variable
from torchvision import models,transforms,datasets
from torch.utils.data import DataLoader
import numpy as np
import matplotlib.pyplot as plt
import time

img_classes=2
epoch_num = 2
path = "./data/dogs-vs-cats/"

#数据
data_transform = transforms.Compose([
    transforms.CenterCrop(224),
    transforms.ToTensor(),
    transforms.Normalize([0.5, 0.5, 0.5],[0.5, 0.5, 0.5])
])

# ImageFOLDER 返回的是一个list，这里的写法是字典的形式
data_image = {x: datasets.ImageFolder(root=os.path.join(path, x),transform=data_transform) for x in ["train", "val"]}
data_loader_image = {x: DataLoader(dataset=data_image[x],batch_size=4,shuffle=True) for x in ["train", "val"]}

# 分类
classes = data_image["train"].classes # 按文件夹名字分类
classes_index = data_image["train"].class_to_idx # 文件夹类名所对应的链值
# 打印类别
print(classes) 
print(classes_index)
# 打印训练集，验证集大小
print("train data set:", len(data_image["train"]))
print("val data set:", len(data_image["val"]))

#导入预训练的网络，并修改全连接层
model = models.resnet18(pretrained=True) # 18层的残差网络
#print(model)

for parma in model.parameters():
    parma.requires_grad = False  # 不进行梯度更新

# 改变模型的全连接层，本项目只需要输出2类
model.fc = nn.Sequential(nn.Linear(512, 256),
                                       nn.ReLU(),
                                       nn.Dropout(p=0.5),
                                       nn.Linear(256, 256),
                                       nn.ReLU(),
                                       nn.Dropout(p=0.5),
                                       nn.Linear(256, 2))

for index, parma in enumerate(model.fc.parameters()):
    parma.requires_grad = True

# 是否有GPU
use_gpu = torch.cuda.is_available()
print("Find GPU: ",use_gpu)
if use_gpu:
    model = model.cuda()
#print(model)

# 定义代价函数
cost = torch.nn.CrossEntropyLoss()
# 定义优化器
optimizer = torch.optim.Adam(model.fc.parameters(),lr=1e-4)

def train():
    for epoch in range(epoch_num):
        since = time.time()
        print("Epoch{}/{}".format(epoch+1, epoch_num))
        print("-" * 10)
        for param in ["train", "val"]:
            if param == "train":
                model.train = True
            else:
                model.train = False

            running_loss = 0.0
            running_correct = 0
            batch = 0
            for data in data_loader_image[param]:
                batch += 1
                X, y = data
                if use_gpu:
                    X, y = Variable(X.cuda()), Variable(y.cuda())
                else:
                    X, y = Variable(X), Variable(y)

                optimizer.zero_grad()
                y_pred = model(X)
                _, pred = torch.max(y_pred.data, 1)
                loss = cost(y_pred,y)
                if param == "train":
                    loss.backward()
                    optimizer.step()
                running_loss += loss.item()
                # running_loss += loss.data
                running_correct += torch.sum(pred == y.data)
                if batch % 5 == 0 and param == "train":
                    print("Batch {}, Train Loss:{:.4f}, Train ACC:{:.4f}".format(
                        batch, running_loss / (4 * batch), 100 * running_correct / (4 * batch)))

            epoch_loss = running_loss / len(data_image[param])
            epoch_correct = 100 * running_correct / len(data_image[param])

            print("{} Loss:{:.4f}, Correct:{:.4f}".format(param, epoch_loss, epoch_correct))
        now_time = time.time() - since
        print("Training time is:{:.0f}m {:.0f}s".format(now_time // 60, now_time % 60))

train()
torch.save(model, 'dogsvscats.pth')
```

测试

```python
import os
import torch
import torchvision
from torchvision import datasets, transforms, models
import numpy as np
import matplotlib.pyplot as plt
from torch.autograd import Variable
import time
model = torch.load('dogsvscats.pth')
path = "./data/dogs-vs-cats"

transform = transforms.Compose([transforms.CenterCrop(224),
                                transforms.ToTensor(),
                                transforms.Normalize([0.5, 0.5, 0.5], [0.5, 0.5, 0.5])])

data_test_img = datasets.ImageFolder(root=path+"/val/", transform = transform) 

data_loader_test_img = torch.utils.data.DataLoader(dataset=data_test_img,
                                                  batch_size = 16,shuffle=True) #载入测试数据集，并随机打乱
classes = data_test_img.classes   ##class

image, label = next(iter(data_loader_test_img))
images = Variable(image).cuda()
y_pred = model(images)
_,pred = torch.max(y_pred.data, 1)
print(pred)
print(label)

img = torchvision.utils.make_grid(image)
img = img.numpy().transpose(1,2,0)
mean = [0.5, 0.5, 0.5]
std = [0.5, 0.5, 0.5]
img = img * std + mean
print("Pred Label:", [classes[i] for i in pred])
plt.imshow(img)
plt.show()
```

#### 7.2 实例二，Deep Dream：探索卷积神经网络眼中的世界

2015年，Google发布了一个有意思的东西，叫做Deep Dream

##### 7.2.1 原理介绍

**1.反向神经网络**

我们知道经过训练之后，每一层网络足部提取越来越高级的图像特征，知道最后一层将这些特征比较做出分类的结果。比如前面几层也许在寻找边缘和拐角的特征，中间几层分析整体的轮廓特征，这样不断的增加层数就可以发展出越来越多的复杂特征，最后几层将这些特征要素组合起来形成完整的解释，这样到最后网络就会对非常复杂的东西，比如小猫，树叶等图片有所反应

**2.Deep Dream**

如果我们将算法反复地应用到自身的输出上，不断迭代，并在每次迭代后应用一些缩放，就能不断地激活特征，得到无尽的新效果。

##### 7.2.2 代码实现

```python
import torch
import torch.nn as nn
from torch.autograd import Variable
from torchvision import models
from torchvision import transforms, utils
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
# PIL.ImageFilter是Python中的图像滤波，主要对图像进行平滑、锐化、边界增强等滤波处理
# PIL.ImageChops模块包含一些算术图形操作，叫做channel operations（“chops”）。这些操作可用于诸多目的，比如图像特效，图像组合，算法绘图等等
from PIL import Image, ImageFilter, ImageChops


# 加载图像并显示
def load_image(path):
    image = Image.open(path)
    plt.imshow(image)
    plt.title("Image loaded successfully")
    return image

# 对数据集的标准化设置——减去均值再除以标准差
normalise = transforms.Normalize(
    mean=[0.485, 0.456, 0.406],
    std=[0.229, 0.224, 0.225]
    )

# 数据集的预处理，包括缩放、转换成Tensor、标准化
preprocess = transforms.Compose([
    transforms.Resize((224,224)),
    transforms.ToTensor(),
    normalise
    ])

# 逆向处理过程，逆标准化，图像乘以标准差再加上均值
def deprocess(image):
    return image * torch.Tensor([0.229, 0.224, 0.225]).cuda()  + torch.Tensor([0.485, 0.456, 0.406]).cuda()

# 下载vgg16的预训练模型，传到GPU上，输出网络结构
vgg = models.vgg16(pretrained=True)
vgg = vgg.cuda()
modulelist = list(vgg.features.modules())

# 这是deep dream的实际代码，特定层的梯度被设置为等于该层的响应，这导致了该层响应最大化。换句话说，我们正在增强一层检测到的特征，对输入图像（octaves）应用梯度上升算法。
def dd_helper(image, layer, iterations, lr):        
    # 一开始的输入是图像经过预处理、在正数第一个维度上增加一个维度以匹配神经网络的输入、传到GPU上
    input = Variable(preprocess(image).unsqueeze(0).cuda(), requires_grad=True)
    # vgg梯度清零
    vgg.zero_grad()
    # 开始迭代
    for i in range(iterations):
    	# 一层一层传递输入
        out = input
        for j in range(layer):
            out = modulelist[j+1](out)
        # 损失是输出的范数
        loss = out.norm()
        # 损失反向传播
        loss.backward()
        # 输入的数据是上次迭代时的输入数据+学习率×输入的梯度
        input.data = input.data + lr * input.grad.data
    # 将从网络结构中取出的输入数据的第一个维度去掉
    input = input.data.squeeze()
    # 矩阵转置
    input.transpose_(0,1)
    input.transpose_(1,2)
    # 将输入逆标准化后强制截断在0到1的范围内
    input = np.clip(deprocess(input), 0, 1)
    # 得到像素值为0到255的图像
    im = Image.fromarray(np.uint8(input*255))
    return im


# 这是一个递归函数，用于创建octaves，并且将由一次递归调用生成的图像与由上一级递归调用生成的图像相融合
def deep_dream_vgg(image, layer, iterations, lr, octave_scale, num_octaves):
    # 若octave序号大于0，即还未到达最底层的octave时，一层一层递归
    if num_octaves>0:
        # 对图像进行高斯滤波（高斯模糊）
        image1 = image.filter(ImageFilter.GaussianBlur(2))
        # 判断是否缩放
        if(image1.size[0]/octave_scale < 1 or image1.size[1]/octave_scale<1):
            size = image1.size
        else:
            size = (int(image1.size[0]/octave_scale), int(image1.size[1]/octave_scale))
        # 图像缩放    
        image1 = image1.resize(size,Image.ANTIALIAS)
        # 递归调用，直至num_octave==0
        image1 = deep_dream_vgg(image1, layer, iterations, lr, octave_scale, num_octaves-1)
        size = (image.size[0], image.size[1])
        # 将图像缩放到最初输入图像的大小
        image1 = image1.resize(size,Image.ANTIALIAS)
        # 将最初输入的图像与合成的相同尺寸大小的图像融合
        image = ImageChops.blend(image, image1, 0.6)
#     print("-------------- Recursive level: ", num_octaves, '--------------')
    # 按照dd_helper中的流程生成图像
    img_result = dd_helper(image, layer, iterations, lr)
    # 图像缩放并显示
    img_result = img_result.resize(image.size)
    plt.imshow(img_result)
    return img_result
    
# 加载图像(原始图像)
sky = load_image('1.jpg')

# 对于vgg16最后一个卷积层conv5_3,迭代5次，学习率为0.2,octave缩放比例为2,octave从第20层开始
sky_28 = deep_dream_vgg(sky, 28, 5, 0.2, 2, 20)
```