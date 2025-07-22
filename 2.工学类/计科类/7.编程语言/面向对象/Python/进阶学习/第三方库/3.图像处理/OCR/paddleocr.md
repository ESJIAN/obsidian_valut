# PaddleOCR

[动手学OCR - PaddleOCR 文档 (paddlepaddle.github.io)](https://paddlepaddle.github.io/PaddleOCR/latest/ppocr/blog/ocr_book.html)


| 特性       | img2table+Tesseract | PaddleOCR        | EasyOCR     |
| -------- | ------------------- | ---------------- | ----------- |
| 结构化表格输出  | ✅（强）                | ✅（强）             | ❌（弱）        |
| 识别准确率    | 一般                  | 高                | 高           |
| 手写体支持    | 弱                   | 强                | 较强          |
| 多语言      | 多                   | 多                | 多           |
| CPU多线程支持 | 弱 (Tesseract单线程)    | ✅ (PaddlePaddle) | ✅ (PyTorch) |
| GPU支持    | ❌                   | ✅                | ✅           |
| 安装难度     | 需装Tesseract         | 需装PaddlePaddle   | 简单          |
| 适合场景     | 清晰印刷体表格             | 各类表格/文本          | 各类文本        |

1.  [img2table](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html) + [TesseractOCR](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)
	- **识别能力**：依赖 Tesseract，适合结构化、印刷体、清晰表格，复杂表格和手写体效果一般。
	- **表格结构提取**：[img2table](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html) 专注于表格结构识别，能直接输出 DataFrame。
	- **语言支持**：Tesseract 支持多语言（需下载相应语言包）。
	- **硬件要求**：仅支持 CPU，不支持 GPU。
	- **速度**：较慢，单线程。
	- **易用性**：需安装 Tesseract 并配置环境变量，Python 代码简单。
	- **开源/免费**：完全开源免费。

2. PaddleOCR
	- **识别能力**：基于深度学习，支持印刷体、手写体、复杂背景、旋转文本等，表格结构识别能力强（PaddleOCR v2.6+ 支持表格结构）。
	- **表格结构提取**：支持表格结构识别，输出为 Excel、HTML 等。
	- **语言支持**：支持中、英、日、韩等多语种。
	- **硬件要求**：支持 CPU 和 GPU，GPU 下速度快。
	- **速度**：GPU 下极快，CPU 下也较快。
	- **易用性**：需安装 PaddlePaddle，配置略复杂，文档完善。
	- **开源/免费**：完全开源免费。

3. EasyOCR
	- **识别能力**：基于深度学习，适合多种字体和复杂背景，表格结构识别能力较弱（只做文本检测，不做结构还原）。
	- **表格结构提取**：不支持表格结构识别，只能识别文本内容。
	- **语言支持**：支持 80+ 种语言。
	- **硬件要求**：支持 CPU 和 GPU。
	- **速度**：GPU 下较快，CPU 下中等。
	- **易用性**：安装简单，API 友好。
	- **开源/免费**：完全开源免费。

---

**总结:**

- **Tesseract**: 开源经典，多语言支持广泛，可定制性强（训练模型），但准确率相对较低（尤其复杂场景和手写），无内置 GPU 支持，表格结构需配合其他库。
- **PaddleOCR**: 准确率高，对中文场景优化好，支持手写体和复杂背景，内置表格结构识别，支持 GPU 加速，但安装配置相对复杂。
- **EasyOCR**: 安装简单，API 友好，多语言支持好，支持 GPU，准确率高，但表格结构识别能力弱。

**选择建议:**

- 需要**表格结构化输出**且追求高准确率：**PaddleOCR**。
- 需要处理**手写体、复杂背景**或需要**高速识别 (GPU)**：**PaddleOCR** 或 **EasyOCR**。
- 优先考虑**易用性、快速集成**，且对表格结构要求不高：**EasyOCR**。
- 已有 Tesseract 基础，处理**简单印刷体表格**，可接受准确率：**img2table + Tesseract**。
- 需要识别**非常见语言**或进行**深度定制训练**：**Tesseract** 提供了基础。



- # 1. 本库回忆

- ## 1.1. 版本匹配

| Python 版本 | paddlepaddle  | paddleocr   | torch        | numpy     | opencv-python     |
| --------- | ------------- | ----------- | ------------ | --------- | ----------------- |
| 3.7       | 2.1.2 ~ 2.7.0 | 2.6.0~2.7.0 | 1.7.1~2.2.0  | 1.20~1.24 | 4.2.0.34~4.6.0.66 |
| 3.8       | 2.1.2 ~ 2.7.0 | 2.6.0~2.7.0 | 1.7.1~2.2.0  | 1.20~1.24 | 4.2.0.34~4.6.0.66 |
| 3.9       | 2.1.2 ~ 2.7.0 | 2.6.0~2.7.0 | 1.8.0~2.2.0  | 1.20~1.24 | 4.2.0.34~4.6.0.66 |
| 3.10      | 2.3.0 ~ 2.7.0 | 2.6.0~2.7.0 | 1.10.0~2.2.0 | 1.21~1.24 | 4.5.5.64~4.6.0.66 |
| 3.11      | 2.5.0 ~ 2.7.0 | 2.7.0+      | 2.0.0+       | 1.23~1.26 | 4.6.0.66+         |

<center><b>版本匹配表一览</b></center>

> 说明：
> 
> - paddleocr 2.7.0 及以上推荐 opencv-python <= 4.6.0.66
> - torch 2.2.0 支持 Python 3.10
> - numpy 1.24.4 兼容性较好
> - paddlepaddle 2.6.0/2.7.0 支持 Python 3.10/3.11
> - 具体 GPU 版本需参考各自官网

**实用建议**：

- **优先选择官方推荐的 Python 版本（如 3.8~3.10）和最新稳定包。**
- 安装顺序建议：先 numpy，再 opencv-python，再 paddlepaddle/paddleocr/torch。
- 如遇依赖冲突，优先降级 opencv-python 到 4.6.0.66 及以下。

**参考链接**：

- [PaddlePaddle 安装说明](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)
- [PaddleOCR 安装文档](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)
- [PyTorch 历史版本支持](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)
- [opencv-python PyPI](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)
- [numpy PyPI](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)







- ## 1.2. 数据结构

```
data = [
    [
        [[820.0, 34.0], [1933.0, 34.0], [1933.0, 179.0], [820.0, 179.0]], 
        ("采购验收单", 0.9970836639404297)
    ],
    [
        [[253.0, 303.0], [2221.0, 294.0], [2221.0, 397.0], [253.0, 405.0]], 
        ("购买单位第三采油厂第七作业区注采704食堂2025-04-24", 0.9800031781196594)
    ],

]

```

- 每条 OCR 结果包含一个四点边框和对应的文本及置信度：
    
    `[   [[x0, y0], [x1, y1], [x2, y2], [x3, y3]],   (text, confidence) ]`
    
- 我们关注的关键是：
    
    1. **文本内容** text
        
    2. **边框的垂直位置** y0…y3 用来判断是否同一行 [智能文档处理与工作流自动化](https://nanonets.com/blog/image-processing-and-bounding-boxes-for-ocr/?utm_source=chatgpt.com)
        
    3. **边框的水平位置** x0…x1 用来判断列顺序

### **1、前言**

Hello 大家好呀，我是小张~

本期将给大家介绍一个 Github 项目，用于OCR文本识别的；在之前的教程中，关于用 Python 实现OCR 识别，写过两篇文章：

一篇是关于 python 与 [Tesseract](https://zhida.zhihu.com/search?content_id=172606665&content_type=Article&match_order=1&q=Tesseract&zhida_source=entity) ，详情可参考：[介绍一个Python 包 ，几行代码可实现 OCR 文本识别](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzU2NTgxMjUyMQ%3D%3D%26mid%3D2247485753%26idx%3D1%26sn%3D7ee27699e6b99b3ad69870c5235eed28%26chksm%3Dfcb7457fcbc0cc6980569ae8ee362df437cc47bd286431b263bb6efd93039de52ef65db05295%26token%3D1121212502%26lang%3Dzh_CN%23rd)； tesseract 是基于传统机器学习方法实现的， 对于英文字符识别还是挺棒的，但中文字符的识别效果就差强人意了~~

  

![](https://pic3.zhimg.com/v2-ace660121f897a39c847f879e2a8d524_1440w.jpg)

  

还有一篇是介绍了一个用于文本识别的 Github 项目**[Easy-OCR](https://zhida.zhihu.com/search?content_id=172606665&content_type=Article&match_order=1&q=Easy-OCR&zhida_source=entity)**，相关用法详情可参考：[关于文本OCR检测、分享一个基于深度学习技术的Python库](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzU2NTgxMjUyMQ%3D%3D%26mid%3D2247487340%26idx%3D1%26sn%3D1cc15737a668a94f0b901f86d43ca239%26chksm%3Dfcb7432acbc0ca3cca4401cb71f609d7817f8643c4e3be13f17f50b8d53cef3b088bc2388000%26token%3D1121212502%26lang%3Dzh_CN%23rd)

Easy-OCR 是基于深度学习技术开发的，识别效果要优于 Tesserart，支持识别70+个国家语言，除了文本识别之外还能对文本块区域完成检测功能，并用线框将相关区域标注在原图上

  

![](https://pic4.zhimg.com/v2-af70fde26b975402a8f31878a5c53835_1440w.jpg)

  

但测试后发现，该库对于某些路标识别效果并不是很精确~

### **2 PaddleOCR 介绍**

这篇文章呢，将介绍一个新的 Github 项目，同样用于 OCR 识别、该项目名叫 PaddleOCR，是 Paddle 的一个分支；PaddleOCR 基于深度学习技术实现的， 所以使用时需要训练好的权重文件，但这个不需要我们担心，因为官方提供的有~

本小节是对 PaddleOCR 项目的简单介绍，如果只对使用步骤感兴趣的同学可以跳过本小节看第三节部分~~~

经测试 PaddleOCR 识别效果非常优秀，下面两张图片是从官网介绍中截取的几张图片

图一

  

![](https://pic1.zhimg.com/v2-64340005e443fc04070431c35a3e05d4_1440w.jpg)

  

图二

  

![](https://pica.zhimg.com/v2-6566e59f92ce7a735f82c12b477c3cc4_1440w.jpg)

  

为了测试该项目的识别性能、随后我在网上找了一张关于优惠卷的图片，图片中文字情况比较复杂，垂直、斜体等；还有中英文相结合，甚至还有小数点

  

![](https://pica.zhimg.com/v2-5c4b8973f11e04eed5a6898bd548a184_1440w.jpg)

  

最终测试效果如下，**无论左边图片文本复杂度有多高，图中文字基本都能识别到**，非常Nice

  

![](https://pic1.zhimg.com/v2-8d58d68d65fd34259404474f38b36558_1440w.jpg)

  

关于 PaddleOCR 模型 ,有以下几个特点

- PaddleOCR 从 2020.5.14 发布，项目迭代到现在，功能一直处于在不断完善的过程；

  

![](https://pica.zhimg.com/v2-a8f03efe6b2f80f4c28407842b56ddf8_1440w.jpg)

  

- 在 PaddleOCR 识别中，会依次完成三种任务：检测、方向分类及文本识别；
- 关于预训练权重，PaddleOCR 官网根据提供权重文件大小分为两类：  
    

- 一类为轻量级，（检测+分类+识别）三类权重加起来大小一共才 9.4 M，适用于手机端和服务器部署；
- 另一类（检测+分类+识别）三类权重内存加起来一共 143.4 MB ，适用于服务器部署；
- 无论模型是否轻量级，识别效果都能与商业效果相比，在本期教程中将选用轻量级权重用于测试；

  

- 支持多语言识别，目前能够支持 80 多种语言；
- 除了能对中文、英语、数字识别之外，还能应对字体倾斜、文本中含有小数点字符等复杂情况
- 提供有丰富的 OCR 领域相关工具供我们使用，方便我们制作自己的数据集、用于训练  
    

- 半自动数据标注工具；
- 数据合成工具；

  

- 支持 pip 安装，简单上手；

### **3 PaddleOCR 使用**

简单介绍完之后，下面将手把手教大家怎么去使用 PaddleOCR，

**3.1 环境介绍**

介绍一下本次所用的测试环境

- os：Win10；
- Python：3.7.9；

**3.2 安装 PaddlePaddle2.0**

PaddleOCR 需在 PaddlePaddle2.0 下才可以正常运行，开始之前请确保 `PaddlePaddle2.0` 已经安装，

```text
pip3 install --upgrade pip
​
​
#
python3 -m pip install paddlepaddle==2.0.0 -i https://mirror.baidu.com/pypi/simple
```

**3.2 克隆 PaddleOCR 仓库**

用 `git clone` 命令或者 `Download` 把项目仓库直接下载到本地

```text
git clone https://github.com/PaddlePaddle/PaddleOCR
```

这里我用的是 git 命令

  

![](https://pica.zhimg.com/v2-c8dcc61697320e6c0f9522e67a852e40_1440w.jpg)

  

**3.3 安装PaddleOCR 第三方依赖包**

命令行进入 `PaddleOCR` 文件夹下

```text
cd PaddleOCR
```

安装第三方依赖项

```text
pip3 install -r requirements.txt
```

这一步骤如果报错的话，建议把改项目放置在一个虚拟环境中再进行安装，如果用虚拟环境的话，记得还需要安装一下 PaddlePaddle 包

```text
python3 -m pip install paddlepaddle==2.0.0 -i https://mirror.baidu.com/pypi/simple
```

**3.4 下载权重文件**

权重链接地址分别贴在下方，需依次下载到本地；检测权重

```text
https://paddleocr.bj.bcebos.com/dygraph_v2.0/ch/ch_ppocr_mobile_v2.0_det_infer.tar
```

方向分类权重

```text
https://paddleocr.bj.bcebos.com/dygraph_v2.0/ch/ch_ppocr_mobile_v2.0_cls_infer.tar
```

识别权重

```text
https://paddleocr.bj.bcebos.com/dygraph_v2.0/ch/ch_ppocr_mobile_v2.0_rec_infer.tar
```

下载到本地之后分别进行解压，创建一个 `inference` 文件夹，把前面解压后的三个文件夹放入 inference 中，再把 `inference` 文件夹放入 PaddleOCR 中，最终树形目录结构效果如下：

  

![](https://pica.zhimg.com/v2-4cd94095aef68edb90c46b64bf80671e_1440w.jpg)

  

  

**3.5 PaddleOCR 使用**

以上环境配置好之后，就可以使用 PaddleOCR 进行识别了，在PaddleOCR 项目环境下打开终端，根据自己情况，输入下面三种类型中的一种即可完成文本识别

**1，使用 gpu，识别单张图片**

```text
python3 tools/infer/predict_system.py --image_dir="./doc/imgs/11.jpg" --det_model_dir="./inference/ch_ppocr_mobile_v2.0_det_infer/"  --rec_model_dir="./inference/ch_ppocr_mobile_v2.0_rec_infer/" --cls_model_dir="./inference/ch_ppocr_mobile_v2.0_cls_infer/" --use_angle_cls=True --use_space_char=True
```

**2，使用 gpu ，识别多张图片**

```text
python3 tools/infer/predict_system.py --image_dir="./doc/imgs/" --det_model_dir="./inference/ch_ppocr_mobile_v2.0_det_infer/"  --rec_model_dir="./inference/ch_ppocr_mobile_v2.0_rec_infer/" --cls_model_dir="./inference/ch_ppocr_mobile_v2.0_cls_infer/" --use_angle_cls=True --use_space_char=True
```

**3，不使用gpu，识别单张图片**

```text
python3 tools/infer/predict_system.py --image_dir="./doc/imgs/11.jpg" --det_model_dir="./inference/ch_ppocr_mobile_v2.0_det_infer/"  --rec_model_dir="./inference/ch_ppocr_mobile_v2.0_rec_infer/" --cls_model_dir="./inference/ch_ppocr_mobile_v2.0_cls_infer/" --use_angle_cls=True --use_space_char=True --use_gpu=False
```

里面有两个参数需要自己配置一下，参数说明：

- `image_dir` -> 为需要识别图片路径或文件夹；
- `det_model_dir` -> 存放识别后图片路径或文件夹；

PaddleOCR 识别一张图片很快，只用 CPU 的话，也只需要两三秒

  

![](https://pic2.zhimg.com/v2-730f226a88df575c1a5b199ef7515cf7_1440w.jpg)

  

### **4. 数据、源码获取**

为了方便，我已经把测试数据、项目代码都打包在一起了，下载后完成以下两个步骤即可正常使用(使用方法参考章节 3.5 部分)

- 创建虚拟环境；
- pip 工具安装依赖项；

```text
python3 -m pip install paddlepaddle==2.0.0 -i https://mirror.baidu.com/pypi/simple
​
​
# 依赖项
pip3 install -r requirements.txt
```

获取方式：

[文本OCR，这个Python库识别效果不输于商用！​mp.weixin.qq.com/s/czngLHCapJRBZ93cgE1ISg![](https://pic1.zhimg.com/v2-6a1de80f1e77549e78acfec91904ce18_180x120.jpg)](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s/czngLHCapJRBZ93cgE1ISg)

### **5 小总结**

Paddle-OCR 属于Paddle 框架其中的一个应用，Paddle 除了 OCR 之外还有许多其它好玩的模型，关键开发者提供有训练好的预权重文件、降低了使用门槛

后期呢，我也打算将从中挑一些好玩的项目，通过博文的方式手把手教大家跑起来

好了，关于 PaddleOCR 的使用就介绍到这里了，如果内容对你有帮助的话不妨点个赞来鼓励一下我~

最后感谢大家的阅读，我们下期见


## 3.3 警告解决

- `No ccache found`
    
    ```
    /opt/anaconda3/envs/paddle/lib/python3.12/site-packages/paddle/utils/cpp_extension/extension_utils.py:686: 
    UserWarning: No ccache found. Please be aware that recompiling all source files may be required. You can download and install ccache from: https://github.com/ccache/ccache/blob/master/doc/INSTALL.md
      warnings.warn(warning_message)
    ```
    
    提示在当前环境中没有找到 ccache。ccache 是一个编译缓存工具，可以显著加快重新编译的速度。如果不介意重新编译所有源文件的时间，可以选择忽略这个警告。如果希望提高编译速度，可以按照提示安装 ccache。
    
    ```
    conda install -c conda-forge ccache
    ```
    
- `Setuptools is replacing distutils`
    
    ```
    /root/miniconda3/envs/PaddleSpeech/lib/python3.9/site-packages/_distutils_hack/__init__.py:30: 
    UserWarning: Setuptools is replacing distutils. Support for replacing an already imported distutils is deprecated. In the future, this condition will fail. Register concerns at https://github.com/pypa/setuptools/issues/new?template=distutils-deprecation.yml
      warnings.warn(
    ```
    
    这个警告表示 setuptools 正在替换 distutils，并且在未来这种替换可能会失败，setuptools项目中建议通过更新 setuptools 来解决。
    
    ```
    python -m pip install --upgrade setuptools
    ```
    
- `pip is being invoked by an old script wrapper`
    
    ```
    WARNING: pip is being invoked by an old script wrapper. This will fail in a future version of pip.
    Please see https://github.com/pypa/pip/issues/5599 for advice on fixing the underlying issue.
    To avoid this problem you can invoke Python with '-m pip' instead of running pip directly.
    ```
    
    这个警告表示您正在使用的 pip 是通过一个旧的脚本包装器调用的，这在未来可能会导致问题。建议使用 python -m pip 命令来调用 pip。




# PPStructure 


- # 1. 本库回忆

- ## 1.1. 数据结构

```python
[ 
  {  
    'type': 'Text',
    'bbox': [34, 432, 345, 462],
    'res': (
      [
        [36.0, 437.0, 341.0, 437.0, 341.0, 446.0, 36.0, 447.0],
        [41.0, 454.0, 125.0, 453.0, 125.0, 459.0, 41.0, 460.0]
      ],# 每行文本的四边形坐标
      [
        ('Tigure-6. The performance of CNN and IPT models using difforen', 0.90060663), # 识别文本
        ('Tent  ', 0.465441) # 置信度
      ]
    )
  }
]
```

- **`type`**: 区域类型，如 "Text"（文本）, "Title"（标题）, "Table"（表格）, "Image"（图像）, "List"（列表）等。
- **`bbox`**: 区域外接矩形框的坐标 `[left, top, right, bottom]`。
- **`res`**: 区域内容，根据 `type` 不同而不同。对于文本区域，`res` 是一个二元组 `(boxes, rec_res)`：
    - **`boxes`**: 列表，包含每行文本的四边形坐标 `[[x1, y1, x2, y2, x3, y3, x4, y4], ...]`。
    - **`rec_res`**: 列表，包含每行文本的识别结果和置信度 `[(text, confidence), ...]`。

>**注意**：如果识别文本是HTML结构的的字符串的话，置信度项会消失（如下图）

![image.png](https://i0.hdslb.com/bfs/openplatform/1f2cabee264c003579bd7bbbab08a67c7d566b44.png)


## 1. 准备环境[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#1 "Permanent link")

### 1.1 安装PaddlePaddle[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#11-paddlepaddle "Permanent link")

> 如果您没有基础的Python运行环境，请参考[运行环境准备](https://paddlepaddle.github.io/PaddleOCR/main/ppocr/environment.html)。

- CUDA11.8 的 PaddlePaddle

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-0-1)|`python3 -m pip install paddlepaddle-gpu -i https://www.paddlepaddle.org.cn/packages/stable/cu118/`|

- CUDA12.3 的 PaddlePaddle

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-1-1)|`python3 -m pip install paddlepaddle-gpu -i https://www.paddlepaddle.org.cn/packages/stable/cu123/`|

- 您的机器是CPU，请运行以下命令安装

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-2-1)|`python3 -m pip install paddlepaddle -i https://www.paddlepaddle.org.cn/packages/stable/cpu/`|

更多的版本需求，请参照[飞桨官网安装文档](https://www.paddlepaddle.org.cn/install/quick)中的说明进行操作。

### 1.2 安装PaddleOCR whl包[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#12-paddleocr-whl "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-3-1)<br>[2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-3-2)<br>[3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-3-3)<br>[4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-3-4)|`python3 -m pip install paddleocr # 安装 图像方向分类依赖包paddleclas（如不需要图像方向分类功能，可跳过） python3 -m pip install paddleclas`|

## 2. 便捷使用[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#2 "Permanent link")

### 2.1 命令行使用[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#21 "Permanent link")

#### 2.1.1 图像方向分类+版面分析+表格识别[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#211 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-4-1)<br>[2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-4-2)<br>[3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-4-3)|`# 暂时关闭新 IR 功能 export FLAGS_enable_pir_api=0 paddleocr --image_dir=ppstructure/docs/table/1.png --type=structure --image_orientation=true`|

#### 2.1.2 版面分析+表格识别[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#212 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-5-1)|`paddleocr --image_dir=ppstructure/docs/table/1.png --type=structure`|

#### 2.1.3 版面分析[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#213 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-6-1)|`paddleocr --image_dir=ppstructure/docs/table/1.png --type=structure --table=false --ocr=false`|

#### 2.1.4 表格识别[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#214 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-7-1)|`paddleocr --image_dir=ppstructure/docs/table/table.jpg --type=structure --layout=false`|

#### 2.1.5 关键信息抽取[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#215 "Permanent link")

关键信息抽取暂不支持通过whl包调用，详细使用教程请参考：[关键信息抽取教程](https://paddlepaddle.github.io/PaddleOCR/main/ppocr/model_train/kie.html)。

#### 2.1.6 版面恢复[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#216 "Permanent link")

版面恢复分为2种方法，详细介绍请参考：[版面恢复教程](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/model_train/recovery_to_doc.html)：

- PDF解析
- OCR技术

通过PDF解析(只支持pdf格式的输入)：

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-8-1)|`paddleocr --image_dir=ppstructure/docs/recovery/UnrealText.pdf --type=structure --recovery=true --use_pdf2docx_api=true`|

通过OCR技术：

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-9-1)<br>[2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-9-2)<br>[3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-9-3)<br>[4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-9-4)<br>[5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-9-5)<br>[6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-9-6)|`# 中文测试图 paddleocr --image_dir=ppstructure/docs/table/1.png --type=structure --recovery=true # 英文测试图 paddleocr --image_dir=ppstructure/docs/table/1.png --type=structure --recovery=true --lang='en' # pdf测试文件 paddleocr --image_dir=ppstructure/docs/recovery/UnrealText.pdf --type=structure --recovery=true --lang='en'`|

#### 2.1.7 版面恢复+转换为markdown文件[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#217-markdown "Permanent link")

不使用LaTeXOCR模型进行公式识别：

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-10-1)|`paddleocr --image_dir=ppstructure/docs/recovery/UnrealText.pdf --type=structure --recovery=true --recovery_to_markdown=true --lang='en'`|

使用LaTeXOCR模型进行公式识别，其中必须使用中文layout模型：

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-11-1)|`paddleocr --image_dir=ppstructure/docs/recovery/UnrealText.pdf --type=structure --recovery=true --formula=true --recovery_to_markdown=true --lang='ch'`|

### 2.2 Python脚本使用[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#22-python "Permanent link")

#### 2.2.1 图像方向分类+版面分析+表格识别[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#221 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-15)<br>[16](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-16)<br>[17](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-17)<br>[18](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-18)<br>[19](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-19)<br>[20](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-20)<br>[21](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-21)<br>[22](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-22)<br>[23](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-12-23)|`import os import cv2 from paddleocr import PPStructure,draw_structure_result,save_structure_res table_engine = PPStructure(show_log=True, image_orientation=True) save_folder = './output' img_path = 'ppstructure/docs/table/1.png' img = cv2.imread(img_path) result = table_engine(img) save_structure_res(result, save_folder,os.path.basename(img_path).split('.')[0]) for line in result:     line.pop('img')    print(line) from PIL import Image font_path = 'doc/fonts/simfang.ttf' # PaddleOCR下提供字体包 image = Image.open(img_path).convert('RGB') im_show = draw_structure_result(image, result,font_path=font_path) im_show = Image.fromarray(im_show) im_show.save('result.jpg')`|

#### 2.2.2 版面分析+表格识别[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#222 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-15)<br>[16](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-16)<br>[17](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-17)<br>[18](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-18)<br>[19](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-19)<br>[20](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-20)<br>[21](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-21)<br>[22](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-22)<br>[23](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-13-23)|`import os import cv2 from paddleocr import PPStructure,draw_structure_result,save_structure_res table_engine = PPStructure(show_log=True) save_folder = './output' img_path = 'ppstructure/docs/table/1.png' img = cv2.imread(img_path) result = table_engine(img) save_structure_res(result, save_folder,os.path.basename(img_path).split('.')[0]) for line in result:     line.pop('img')    print(line) from PIL import Image font_path = 'doc/fonts/simfang.ttf' # PaddleOCR下提供字体包 image = Image.open(img_path).convert('RGB') im_show = draw_structure_result(image, result,font_path=font_path) im_show = Image.fromarray(im_show) im_show.save('result.jpg')`|

#### 2.2.3 版面分析[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#223 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-14-15)|`import os import cv2 from paddleocr import PPStructure,save_structure_res table_engine = PPStructure(table=False, ocr=False, show_log=True) save_folder = './output' img_path = 'ppstructure/docs/table/1.png' img = cv2.imread(img_path) result = table_engine(img) save_structure_res(result, save_folder, os.path.basename(img_path).split('.')[0]) for line in result:     line.pop('img')    print(line)`|

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-15)<br>[16](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-15-16)|`import os import cv2 from paddleocr import PPStructure,save_structure_res ocr_engine = PPStructure(table=False, ocr=True, show_log=True) save_folder = './output' img_path = 'ppstructure/docs/recovery/UnrealText.pdf' result = ocr_engine(img_path) for index, res in enumerate(result):     save_structure_res(res, save_folder, os.path.basename(img_path).split('.')[0], index) for res in result:     for line in res:        line.pop('img')        print(line)`|

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-15)<br>[16](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-16)<br>[17](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-17)<br>[18](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-18)<br>[19](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-19)<br>[20](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-20)<br>[21](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-21)<br>[22](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-22)<br>[23](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-23)<br>[24](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-24)<br>[25](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-25)<br>[26](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-26)<br>[27](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-27)<br>[28](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-28)<br>[29](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-29)<br>[30](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-30)<br>[31](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-31)<br>[32](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-32)<br>[33](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-33)<br>[34](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-16-34)|`import os import cv2 import numpy as np from paddleocr import PPStructure,save_structure_res from paddle.utils import try_import from PIL import Image ocr_engine = PPStructure(table=False, ocr=True, show_log=True) save_folder = './output' img_path = 'ppstructure/docs/recovery/UnrealText.pdf' fitz = try_import("fitz") imgs = [] with fitz.open(img_path) as pdf:     for pg in range(0, pdf.page_count):        page = pdf[pg]        mat = fitz.Matrix(2, 2)        pm = page.get_pixmap(matrix=mat, alpha=False)         # if width or height > 2000 pixels, don't enlarge the image        if pm.width > 2000 or pm.height > 2000:            pm = page.get_pixmap(matrix=fitz.Matrix(1, 1), alpha=False)         img = Image.frombytes("RGB", [pm.width, pm.height], pm.samples)        img = cv2.cvtColor(np.array(img), cv2.COLOR_RGB2BGR)        imgs.append(img) for index, img in enumerate(imgs):     result = ocr_engine(img)    save_structure_res(result, save_folder, os.path.basename(img_path).split('.')[0], index)    for line in result:        line.pop('img')        print(line)`|

#### 2.2.4 表格识别[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#224 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-17-15)|`import os import cv2 from paddleocr import PPStructure,save_structure_res table_engine = PPStructure(layout=False, show_log=True) save_folder = './output' img_path = 'ppstructure/docs/table/table.jpg' img = cv2.imread(img_path) result = table_engine(img) save_structure_res(result, save_folder, os.path.basename(img_path).split('.')[0]) for line in result:     line.pop('img')    print(line)`|

#### 2.2.5 关键信息抽取[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#225 "Permanent link")

关键信息抽取暂不支持通过whl包调用，详细使用教程请参考：[inference文档](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/infer_deploy/python_infer.html)。

#### 2.2.6 版面恢复[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#226 "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-15)<br>[16](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-16)<br>[17](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-17)<br>[18](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-18)<br>[19](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-19)<br>[20](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-20)<br>[21](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-21)<br>[22](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-22)<br>[23](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-18-23)|`import os import cv2 from paddleocr import PPStructure,save_structure_res from paddleocr.ppstructure.recovery.recovery_to_doc import sorted_layout_boxes, convert_info_docx # 中文测试图 table_engine = PPStructure(recovery=True) # 英文测试图 # table_engine = PPStructure(recovery=True, lang='en') save_folder = './output' img_path = 'ppstructure/docs/table/1.png' img = cv2.imread(img_path) result = table_engine(img) save_structure_res(result, save_folder, os.path.basename(img_path).split('.')[0]) for line in result:     line.pop('img')    print(line) h, w, _ = img.shape res = sorted_layout_boxes(result, w) convert_info_docx(img, res, save_folder, os.path.basename(img_path).split('.')[0])`|

#### 2.2.7 版面恢复+转换为markdown文件[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#227-markdown "Permanent link")

|   |   |
|---|---|
|[1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-1)<br> [2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-2)<br> [3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-3)<br> [4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-4)<br> [5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-5)<br> [6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-6)<br> [7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-7)<br> [8](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-8)<br> [9](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-9)<br>[10](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-10)<br>[11](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-11)<br>[12](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-12)<br>[13](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-13)<br>[14](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-14)<br>[15](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-15)<br>[16](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-16)<br>[17](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-17)<br>[18](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-18)<br>[19](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-19)<br>[20](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-20)<br>[21](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-21)<br>[22](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-22)<br>[23](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-23)<br>[24](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-19-24)|`import os import cv2 from paddleocr import PPStructure,save_structure_res from paddleocr.ppstructure.recovery.recovery_to_doc import sorted_layout_boxes from paddleocr.ppstructure.recovery.recovery_to_markdown import convert_info_markdown # 中文测试图 table_engine = PPStructure(recovery=True) # 英文测试图 # table_engine = PPStructure(recovery=True, lang='en') save_folder = './output' img_path = 'ppstructure/docs/table/1.png' img = cv2.imread(img_path) result = table_engine(img) save_structure_res(result, save_folder, os.path.basename(img_path).split('.')[0]) for line in result:     line.pop('img')    print(line) h, w, _ = img.shape res = sorted_layout_boxes(result, w) convert_info_markdown(res, save_folder, os.path.basename(img_path).split('.')[0])`|

### 2.3 返回结果说明[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#23 "Permanent link")

PP-Structure的返回结果为一个dict组成的list，示例如下：

#### 2.3.1 版面分析+表格识别[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#231 "Permanent link")

|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [1](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-20-1)<br>[2](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-20-2)<br>[3](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-20-3)<br>[4](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-20-4)<br>[5](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-20-5)<br>[6](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-20-6)<br>[7](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-20-7) | `[   {   'type': 'Text',      'bbox': [34, 432, 345, 462],      'res': ([[36.0, 437.0, 341.0, 437.0, 341.0, 446.0, 36.0, 447.0], [41.0, 454.0, 125.0, 453.0, 125.0, 459.0, 41.0, 460.0]],                [('Tigure-6. The performance of CNN and IPT models using difforen', 0.90060663), ('Tent  ', 0.465441)])  } ]` |

dict 里各个字段说明如下：

|字段|说明|
|---|---|
|type|图片区域的类型|
|bbox|图片区域的在原图的坐标，分别[左上角x，左上角y，右下角x，右下角y]|
|res|图片区域的OCR或表格识别结果。  <br>表格: 一个dict，字段说明如下  <br>        `html`: 表格的HTML字符串  <br>        在代码使用模式下，前向传入return_ocr_result_in_table=True可以拿到表格中每个文本的检测识别结果，对应为如下字段:  <br>        `boxes`: 文本检测坐标  <br>        `rec_res`: 文本识别结果。  <br>OCR: 一个包含各个单行文字的检测坐标和识别结果的元组|

运行完成后，每张图片会在`output`字段指定的目录下有一个同名目录，图片里的每个表格会存储为一个excel，图片区域会被裁剪之后保存下来，excel文件和图片名为表格在图片里的坐标。

`[](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-21-1)/output/table/1/   [](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-21-2)  └─ res.txt  [](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-21-3)  └─ [454, 360, 824, 658].xlsx  表格识别结果  [](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-21-4)  └─ [16, 2, 828, 305].jpg            被裁剪出的图片区域  [](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#__codelineno-21-5)  └─ [17, 361, 404, 711].xlsx        表格识别结果`

#### 2.3.2 关键信息抽取[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#232 "Permanent link")

请参考：[关键信息抽取教程](https://paddlepaddle.github.io/PaddleOCR/main/ppocr/model_train/kie.html)。

### 2.4 参数说明[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#24 "Permanent link")

' 进行合并

| 字段                      | 说明                                               | 默认值                                           |
| ----------------------- | ------------------------------------------------ | --------------------------------------------- |
| output                  | 结果保存地址                                           | ./output/table                                |
| table_max_len           | 表格结构模型预测时，图像的长边resize尺度                          | 488                                           |
| table_model_dir         | 表格结构模型 inference 模型地址                            | None                                          |
| table_char_dict_path    | 表格结构模型所用字典地址                                     | ../ppocr/utils/dict/table_structure_dict.txt  |
| merge_no_span_structure | 表格识别模型中，是否对'\|'和'\|False                         |                                               |
| formula_model_dir       | 公式识别模型 inference 模型地址                            | None                                          |
| formula_char_dict_path  | 公式识别模型所用字典地址                                     | ../ppocr/utils/dict/latex_ocr_tokenizer.json  |
| layout_model_dir        | 版面分析模型 inference 模型地址                            | None                                          |
| layout_dict_path        | 版面分析模型字典                                         | ../ppocr/utils/dict/layout_publaynet_dict.txt |
| layout_score_threshold  | 版面分析模型检测框阈值                                      | 0.5                                           |
| layout_nms_threshold    | 版面分析模型nms阈值                                      | 0.5                                           |
| kie_algorithm           | kie模型算法                                          | LayoutXLM                                     |
| ser_model_dir           | ser模型 inference 模型地址                             | None                                          |
| ser_dict_path           | ser模型字典                                          | ../train_data/XFUND/class_list_xfun.txt       |
| mode                    | structure or kie                                 | structure                                     |
| image_orientation       | 前向中是否执行图像方向分类                                    | False                                         |
| layout                  | 前向中是否执行版面分析                                      | True                                          |
| table                   | 前向中是否执行表格识别                                      | True                                          |
| formula                 | 前向中是否执行公式识别                                      | False                                         |
| ocr                     | 对于版面分析中的非表格区域，是否执行ocr。当layout为False时会被自动设置为False | True                                          |
| recovery                | 前向中是否执行版面恢复                                      | False                                         |
| recovery_to_markdown    | 是否将版面恢复结果转换为markdown文件                           | False                                         |
| save_pdf                | 版面恢复导出docx文件的同时，是否导出pdf文件                        | False                                         |
| structure_version       | 模型版本，可选 PP-structure和PP-structurev2              | PP-structure                                  |

大部分参数和PaddleOCR whl包保持一致，见 [whl包文档](https://paddlepaddle.github.io/PaddleOCR/main/ppocr/blog/whl.html)

## 3. 小结[¶](https://paddlepaddle.github.io/PaddleOCR/main/ppstructure/quick_start.html#3 "Permanent link")

通过本节内容，相信您已经熟练掌握通过PaddleOCR whl包调用PP-Structure相关功能的使用方法，您可以参考[文档教程](https://paddlepaddle.github.io/PaddleOCR/main/index.html)，获取包括模型训练、推理部署等更详细的使用教程。