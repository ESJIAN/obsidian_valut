

- # 1. 本库回忆

- ## 1.1. 最简打包步骤

- ### 1. 安装 PyInstaller

通过 pip 安装工具：


```bash
pip install pyinstaller
```

安装后可通过 `pyinstaller --version` 验证版本13。

- ### 2. 准备项目文件

确保待打包的脚本（如 `main.py`）及其依赖的资源文件（如图标、配置文件）位于同一目录。若涉及动态导入或复杂依赖，需提前处理路径问题48。

- ### 3. 执行打包命令

进入脚本所在目录，运行以下命令：

```bash
pyinstaller [选项] 脚本名.py
```

常用选项包括：

- **-F/--onefile**：生成单个可执行文件（体积较大但便于分发，默认此方式）；
- **-D/--onedir**：生成包含可执行文件和依赖库的目录（启动速度更快）；
- **-w/--windowed**：隐藏控制台窗口（适用于 GUI 程序）；
- **-i/--icon**：指定图标文件（Windows 需 `.ico`，macOS 需 `.icns`）；
- **--hidden-import**：手动指定未被自动检测到的依赖模块。

例如，将 `hello.py` 打包为无控制台的单文件程序：

```bash
pyinstaller -F -w --icon=app.ico hello.py
```

- ### 4. 查看输出结果

打包完成后，生成的文件位于 `dist` 目录：

- 单文件模式下直接包含 `hello.exe`（Windows）或无后缀文件（Linux/macOS）；
- 目录模式下包含可执行文件及依赖库文件夹15。

- ### 5. 处理资源文件

若程序依赖非代码文件（如图像、数据），需通过 `--add-data` 参数嵌入：

```bash
# Windows 格式
pyinstaller --add-data "config.ini;." --add-data "assets/;assets/" -F main.py
# Linux/macOS 格式
pyinstaller --add-data "config.ini:." --add-data "assets/:assets/" -F main.py
```

冒号（或分号）前为源路径，后为目标路径45。

- ### 6. 定制打包配置

PyInstaller 会生成同名 `.spec` 文件，可手动编辑以调整打包行为，例如修改资源路径、排除冗余模块等。

- ### 关键注意事项

- **跨平台限制**：需在目标平台上打包（如 Windows 生成 Windows 可执行文件）1011；
- **体积优化**：单文件模式因包含完整解释器体积较大，可通过 `--exclude-module` 排除不必要依赖；
- **调试建议**：首次打包建议使用 `-c/--console` 显示控制台，便于排查依赖或路径错误。

通过以上步骤，即可将 Python 脚本转换为无需 Python 环境即可运行的独立程序。对于复杂项目，可结合 `.spec` 文件或虚拟环境进一步优化打包流程911。

- # 2. 本库重点

- ## 2.1. Pytorch 打包兼容性

>**背景**：Pyinstall 在打包含 Pytorch 的项目时候，很容易因为 Pytorch 内部复杂的包依赖产生各种各样的报错，为了避免下次开相关项目仍遇到这个问题，故写下如下内容。

根据社区反馈和实际测试，以下是与 PyInstaller 兼容性较好的 PyTorch 版本对应关系（截至 2024 年 7 月），可根据项目需求选择：

---

- ### 一、推荐稳定组合（优先选择）

| PyTorch 版本         | Torchaudio版本            | Torchvision版本             | Numpy版本 | PyInstaller 版本         | 兼容性说明                                                               |
| ------------------ | ----------------------- | ------------------------- | ------- | ---------------------- | ------------------------------------------------------------------- |
| `torch==2.0.1`     | `torchaudio==2.0.1`     | `torchvision==0.15.1`     |         | `pyinstaller==5.8.0`   | 最新长期支持组合，PyTorch 2.0 优化了模块结构，PyInstaller 5.8 对动态导入支持更完善，适合需要新特性的项目。 |
| `torch==2.0.1+cpu` | `torchaudio==2.0.1+cpu` | `torchvision==0.15.1+cpu` |         |                        |                                                                     |
|  `torch==1.13.1`   |                         |                           |         |  `pyinstaller==5.4.0`  | 经典稳定组合，社区反馈问题少，适合对稳定性要求高的项目（如不依赖 PyTorch 2.x 新特性）。                  |

>**提示**：cpu 版本的 Pytorch 安装见 [[1.Pytorch基础]] 的安装章节

---

- ### 二、次优组合（特定场景适用）

| PyTorch 版本       | Torchaudio版本 | Torchvision版本 | Numpy版本 | PyInstaller 版本         | 适用场景                                                                                 |
| ---------------- | ------------ | ------------- | ------- | ---------------------- | ------------------------------------------------------------------------------------ |
| `torch==1.12.1`  |              |               |         |  `pyinstaller==5.0.0`  | 旧项目兼容，适合仅需基础功能（如张量运算、简单模型推理）的场景。                                                     |
|  `torch==2.1.0`  |              |               |         |  `pyinstaller==6.0.0`  | 尝鲜新特性（如 `torch.compile`），但需注意 PyInstaller 6.x 对动态模块的钩子可能未完全覆盖，需手动补充 `hiddenimports`。 |

---

- ### 三、注意事项

1. **CUDA 版本匹配**：若使用 GPU 版 PyTorch（如 `torch==2.0.1+cu117`），需确保：
    - 打包环境与运行环境的 CUDA 版本一致（如运行环境需安装 CUDA 11.7 运行时库）；
    - PyInstaller 需通过 `binaries` 参数打包 CUDA 相关 DLL（如 `cudart64_110.dll`）。
2. **CPU 版本优先**：若项目无需 GPU 加速，建议使用 CPU 版 PyTorch（如 `torch==2.0.1+cpu`），兼容性更稳定，打包体积更小。
3. **测试验证**：无论选择哪个版本，建议在虚拟环境中执行以下步骤验证：

    ```bash
    # 安装指定版本
    pip install torch==2.0.1 pyinstaller==5.8.0
    # 打包测试
    pyinstaller main_window.spec
    # 运行 exe 验证功能（如你的 `image_to_excel` 函数是否正常调用 PyTorch）
    ```
    

---

- ### 针对你的项目建议

你的项目中使用了 `PPStructure`（来自 PaddleOCR），需注意 PaddlePaddle 与 PyTorch 的 CUDA 版本需一致（如均为 CUDA 11.7）。推荐选择 `torch==2.0.1+cu117` + `pyinstaller==5.8.0`，并在 `main_window.spec` 中补充以下配置避免打包遗漏：

```txt
a = Analysis(
    ['main_window.py'],
    pathex=[],
    binaries=[],
    datas=[
        # 打包 PaddleOCR 模型文件（根据你的 `image_handler.py` 实际路径调整）
        ('./src/core/ocr_models', 'src/core/ocr_models'),
    ],
    hiddenimports=[
        # PyTorch 动态模块（解决之前的 `_inductor` 报错）
        'torch.distributed._shard.sharding_spec',
        'torch.distributed._shard.sharded_tensor',
        'torch.distributed.checkpoint'
    ],
    excludes=[
        # 排除无需模块（减少冲突）
        'matplotlib', 
        'torch.distributed',
        'torch._inductor'
    ],
    noarchive=False,
    optimize=0,
)
```


- # 3. 本库犯错

- ## 3.1. 虚拟环境没有安装 pyinstaller 使用主环境的 pyinstaller 进行错误的打包

- ## 3.2. 打包时候没有按照最小化打包原则进行打包

从第一性原理（即从最基本的机制和逻辑出发）分析，核心原因是：**未使用的库会引入额外的 “依赖复杂性”，这些复杂性超出了打包工具（如 PyInstaller）的解析能力，导致打包失败；而移除它们后，系统的依赖复杂度降低，工具能够正常完成解析和打包流程**。

- ### 1. 打包工具的核心工作：“依赖闭包” 的构建

PyInstaller 等打包工具的本质是做一件事：**分析代码中所有直接和间接依赖的模块 / 库，形成一个 “依赖闭包”，然后将这个闭包内的所有文件（包括 Python 解释器、库文件、资源等）打包成可执行文件**。

  

- 对于 “被使用的库”：它们的依赖是 “必要且可控的”—— 工具只需解析代码中实际调用的子模块、函数、资源，形成的依赖链是 “有用且有限的”。
- 对于 “未使用的库”：它们的依赖是 “冗余且不可控的”—— 即使代码中没有调用，工具仍会递归解析该库的所有子模块、隐藏依赖（如动态导入、条件导入）、甚至库自带的测试代码 / 示例代码，形成的依赖链可能是 “无用且无限的”（例如某些库会动态生成代码，或嵌套导入数十层子模块）。

- ### 2. 复杂依赖链的 “脆弱性”：解析容错率下降

任何工具对复杂系统的解析能力都是有限的，当依赖链的复杂度超过工具的容错阈值时，就会触发错误。未使用的库往往是 “复杂度放大器”：

  

- **嵌套导入深度超限**：例如 PyTorch、TensorFlow 等库本身有数十层嵌套子模块（如`torch.nn.modules.activation`→`torch.nn.modules.module`→...），未使用时仍会被解析，可能超过工具的递归深度限制（即使提高到 5000，极端情况下仍可能超限）。
- **特殊代码结构的解析失败**：许多库包含动态生成的代码（`exec`/`eval`）、C 扩展模块、或不符合标准字节码规范的优化代码（如 NumPy、PyTorch 的部分加速模块）。这些结构在 “被使用时” 可能只触发一小部分，但 “未被使用时” 工具可能解析到更边缘的代码路径，导致字节码解析错误（如你之前遇到的`IndexError: tuple index out of range`）。
- **钩子冲突**：PyInstaller 通过 “钩子文件（hook）” 处理特殊库的打包逻辑（如`hook-torch.py`）。未使用的库可能自带钩子，这些钩子可能与其他库的钩子冲突（例如 A 库的钩子修改了递归限制，B 库的钩子依赖原始限制），导致工具内部状态混乱。

- ### 3. “冗余依赖” 的 “蝴蝶效应”：微小问题被放大

未使用的库引入的冗余依赖，可能包含一些 “看似无害” 的小问题，但在打包工具的解析逻辑中会被放大为致命错误：

  

- 例如某个未使用的库中存在一行 “无效的类型别名”（如你之前误定义的`np.bool = bool`），在正常运行时不会被执行（因为库未被调用），但打包工具会扫描整个库的代码，解析到这行代码时触发类型错误，进而中断整个打包流程。
- 又如某个未使用的库依赖一个 “版本不兼容的子模块”（如旧版`setuptools`），正常运行时不会加载，但打包工具解析依赖时会强制检查该子模块，导致版本冲突错误。

- ### 结论：“最小依赖原则” 的必然性

从第一性原理看，**打包的本质是对 “必要依赖” 的精确捕捉**。未使用的库引入的冗余依赖，本质上是给这个 “捕捉过程” 增加了噪声和不确定性。当噪声超过工具的处理能力时，失败是必然的；而移除冗余依赖后，噪声消失，工具自然能正常工作。这也是为什么 “清理未使用的库” 是解决打包问题的通用有效手段 —— 它符合 “最小系统复杂度” 的基本工程原则。


# 1 简介

python提供了多种方法用于将普通的*.py程序文件编译成exe文件（有时这里的“编译”也称作“打包”）。exe文件即可执行文件，打包后的*.exe应用不用依赖[python环境](https://so.csdn.net/so/search?q=python%E7%8E%AF%E5%A2%83&spm=1001.2101.3001.7020)，可以在他人的电脑上运行。

pyinstaller是一个第三方模块，专用于[python程序](https://so.csdn.net/so/search?q=python%E7%A8%8B%E5%BA%8F&spm=1001.2101.3001.7020)的exe打包。此外python还有一些别的方法进行打包，但是pyinstaller打包最强大而且好用。

pyinstaller的官网是：[https://pyinstaller.org/](https://pyinstaller.org/ "https://pyinstaller.org/")

![](https://i-blog.csdnimg.cn/blog_migrate/40b8cce16082a2f06c16675a70f16341.png)  

# 2 安装

可以通过pip进行安装。首先启动cmd，输入以下内容后回车：

```undefined
pip install pyinstaller
```

安装完成后，验证是否成功安装：

```sql
pyinstaller --version
```

>如果显示找不到“pyinstaller”，请转到最后一章“常见问题”

# 3 原理和打包效果

## 3.1 原理概述

PyInstaller 的打包过程本质上是一个 “**冻结（Freezing）**” 过程：将 Python 脚本、依赖库、解释器环境等 “冻结” 成一个或一组独立文件，使其能在没有安装 Python 的系统上运行。其核心步骤可拆解为以下 4 个阶段，每个阶段都有明确的技术逻辑：

### **3.1.1. 分析阶段（Analysis）：识别所有依赖**

PyInstaller 首先需要**递归分析脚本的所有依赖项**，确保没有遗漏任何模块、库或资源文件。具体操作包括：

- **静态分析**：通过 `modulegraph` 库解析脚本中的 `import` 语句，构建依赖树（包括标准库、第三方库、自定义模块）。

- **动态分析**：处理 “隐藏依赖”（如通过 `__import__()`、`exec()` 动态导入的模块，或通过配置文件动态加载的资源），这也是为什么复杂项目常需要手动通过 `--hidden-import` 或 `.spec` 文件指定依赖的原因。

- **资源收集**：识别脚本中用到的非代码文件（如图像、配置文件），后续会通过 `--add-data` 等参数打包到目标文件中。

### **3.1.2. 冻结阶段（Freezing）：处理代码与依赖**

分析完成后，PyInstaller 将所有依赖 “冻结” 为独立于系统 Python 环境的形式：

- **字节码转换**：将 `.py` 源码编译为 `.pyc` 字节码（避免源码泄露，同时加速加载）。

- **模块打包**：将所有依赖的 Python 模块（包括标准库如 `os`、`sys`，第三方库如 `requests` 等）收集到一个临时目录，按原目录结构整理。

- **二进制处理**：对于 C 扩展模块（如 `.pyd` 或 `.so` 文件），直接复制其二进制文件（因为它们无法被编译为字节码，需保持原生格式）。

### **3.1.3. 引导程序阶段（Bootloader）：准备启动环境**

为了让冻结的代码能在无 Python 的系统上运行，PyInstaller 会嵌入一个**引导程序（Bootloader）**—— 这是一个预编译的平台特定二进制文件（Windows 下为 `.exe`，Linux 下为 ELF 格式，macOS 下为 Mach-O）。其作用是：

- **初始化环境**：在程序运行时，创建临时目录（单文件模式下），将冻结的代码和依赖解压到该目录（多文件模式下直接使用 `dist` 目录）。

- **启动解释器**：加载一个精简的 Python 解释器（从当前环境提取，与冻结的代码绑定），确保不依赖系统安装的 Python。

- **执行用户脚本**：引导解释器定位并运行用户的入口脚本（如 `main.py`）。

### **3.1.4. 构建阶段（Building）：生成最终可执行文件**

最后，PyInstaller 将冻结的代码、依赖和引导程序组合，生成目标文件：

- **单文件模式（`-F`）**：将所有内容（引导程序 + 冻结的代码 + 依赖）压缩并打包成一个独立的可执行文件。运行时，引导程序会先将内容解压到系统临时目录（如 Windows 的 `%TEMP%`），再启动程序。

- **多文件模式（默认或 `-D`）**：生成一个 `dist` 目录，包含引导程序（可执行文件）、依赖库文件夹（如 `_internal`）、数据文件等。运行时直接从目录加载资源，无需解压，启动速度更快。

---

PyInstaller 并非 “编译” Python 代码为机器码，而是通过**打包依赖 + 嵌入精简解释器 + 引导程序启动**的方式，实现 “免 Python 环境运行”。其核心是解决两个问题：

1. 如何完整收集所有依赖（避免 “运行时找不到模块” 错误）；

2. 如何在无 Python 的系统上启动解释器并执行代码（通过引导程序和临时环境）。

这也是为什么 PyInstaller 必须在**目标平台**上打包（如 Windows 生成 `.exe`，Linux 生成 ELF）—— 因为引导程序和系统依赖（如 Windows 的 DLL、Linux 的共享库）是平台特定的。

## 3.2 搜索模块

当然，在搜索模块的时候必然会遇到一些问题。

pyinstaller只会搜索 _import_ 语句，然后根据 _import_ 得到的模块再进行搜索。如果编程者使用了一些特殊的导入方式，比如使用__import__()函数，使用 _import lib_ 里面的导入函数，那么pyinstaller很可能找不到你所需要的模块。

这时，你可以通过参数来指定你所需要的模块，也可以使用“钩子”等等（这是后话）。

这个特性会体现在打包的时，会出现相关的报错。





## 3.3 打包效果概述

pyinstaller打包后会形成一个文件夹或单个的exe（可以用参数指定）。但不论是哪一种情况，都会包含一个exe文件，用户可以双击它运行该应用程序。

假如你要打包myscript.py，那么打包完成后运行这个myscript.exe，效果就是运行myscript.py后的效果。

默认情况下，打包会形成一个黑色的控制台（cmd的样子），也可以设置隐藏这个控制台。

这个控制台用于为python提供标准输入(stdin)，标准输出(stdout)，标准错误(stderr)。也就是说，这个控制台上显示了print函数的输出，用于接收input函数的输入，还会输出python的异常。

如果你隐藏了这个控制台，程序中的print就无法显示（但是不会报错），报错信息也无法被用户直接看到（pyinstaller有一些选项来控制显示异常，后文详解）；需要注意的是，此时不能使用input，否则会报错：

```lua
RuntimeError: input(): lost sys.stdin
```

python文件有一种后缀名*.pyw，这样的程序执行时默认会隐藏控制台。如果将文件后缀命名为pyw，那么pyinstaller也会认为它隐藏了控制台，不需要通过额外的选项来指定。

当你制作GUI程序的时候，最好选择隐藏控制台，来提升用户体验。 

打包后的文件可能会被反编译（即通过exe文件得到原来的代码），可以通过一些方法进行加密（后文详解）。

## 3.4 打包成单个文件夹

下面介绍一下打包完成后形成的文件夹。

这个文件夹的名字是你提供的，一般是你要求打包的python文件的名称。文件夹中包含一个exe文件，以及其他一些依赖文件（比如一些dll文件，可能还有你的应用所需要的图片等素材）。你只需要将该文件夹压缩就能发给别人运行了。

当你运行里面的exe文件后，pyinstaller其实只是启动了解释器，然后通过解释器运行你的主程序。

- 【优点】
	
	- 打包成单个文件夹的形式便于调试，因为你可以清楚地看到pyinstaller将哪些模块文件放到了文件夹中
	
	- 单个文件夹的状态下，程序的启动速度和打包前差不多。
	
	- 当你更改代码，需要用户更新应用时，只需要让用户对于部分内容进行修改。如果你只修改了主程序，没有使用多余的模块，那么就只需要让用户替换里面的exe文件，而不用全部替换（因为更新前后使用的模块是一致的，它们都以多文件的形式放到了文件夹中）。
	

- 【缺点】打包成单个的文件夹后，文件大小可能会更大一些，因为大部分依赖文件没有进行压缩。

## 3.5 打包成单个exe

单个exe模式下，pyinstaller只会生成一个单独的exe文件，所有的依赖文件都会被压缩到exe文件中。

和上面的文件夹模式类似，exe启动后，pyinstaller也是通过调用python解释器来运行主程序的。

- 【优点】启动单个exe非常简单，用户只需要点击exe文件就能运行，而无需在一大堆的依赖文件中找到exe文件。并且在经过压缩后，这个exe文件的文件大小会大大减小。

- 【缺点】
	
	- 单个exe的启动速度比较慢（通常会慢几秒，且只是启动时的速度，不是运行后的速度），这是因为pyinstaller会在这一段时间中将一些依赖文件写入到一个临时的文件夹（后文介绍该文件夹的调用方式）。
	
	- 如果你希望添加一些附带文件（比如使用说明README），你还需要额外新建文件夹并将其放进去。

# 4 打包

在了解相关原理后，下面正式进入打包环节。

本章介绍通过命令行参数进行打包，这种方式比较初级，适用于一般的打包方式。

## 4.1 基本语法

打包需要通过cmd进行，语法和大多数工具一样。pyinstaller最简单的打包方式是：

```bash
pyinstaller myscript.py
```

其中myscript.py是你想要打包的程序。

如果这一步提示找不到myscript.py，请检查路径是否正确；如这一步提示找不到pyinstaller工具，请参考最后一章“常见问题”。

如果直接传递文件名，pyinstaller会生成一个spec文件将一些打包参数放到里面，然后进行打包。打包完成后，你会在你的目录下找到一个dist文件夹，里面存储了打包后的结果。pyinstaller还会生成一个build文件夹并写入一些日志信息。

当然，你也可以自己构建一个*.spec文件（后文介绍），然后交给pyinstaller进行处理。

## **4.2 参数总览**

本节只是列举并简要介绍常用的参数，并不过多展开，将在下面的部分对于一些重点参数举例介绍。

如有不熟悉命令行参数和命令行使用的读者可自行搜索，或者参考下面的介绍：

```bash
pyinstaller -D -i "icon.ico" myscript.py
```

调用命令时，首先给出工具名称（比如上面的 pyinstaller ），然后提供相关参数，有一些参数是可选的但不需要附带任何值（比如上面的 -D ），有一些参数是必选的（比如上面的 myscript.py ），有一些参数需要附带一个值（比如上面的 -i "icon.ico" ）。其中有一些参数可以简写（比如 -i 就是 --icon 的简写）。

## 位置参数

位置参数在打包时放在最后，而且无需指定关键字。

pyinstaller的位置参数是需要打包的文件路径，或是spec文件路径。

## 可选参数

下面只列举出比较有用的参数，读者可以自行了解，也可以跳过这部分，打包时用于参考。对于完整的参数信息，请参考[Using PyInstaller — PyInstaller 6.11.0 documentation](https://pyinstaller.org/en/stable/usage.html#options "Using PyInstaller — PyInstaller 6.11.0 documentation")

|   |   |
|---|---|
|**参数名**|**描述**|
|-D|文件夹模式。在打包完成后生成一个文件夹，其中包含一个exe文件和一个包含若干依赖文件的文件夹（详见上文）。（默认）|
|-F|单文件模式。在打包完成后只会生成一个单独的exe文件（详见上文）。|
|--add-data <SRC;DEST or SRC:DEST>|指定一个文件夹或文件（非二进制），将其嵌入到exe中。|
|--add-binary <SRC;DEST or SRC:DEST>|和--add-data类似，不过指定的文件夹或文件是二进制的|
|-p DIR<br><br>--paths DIR|提供一个路径进行搜索并且导入里面的模块（不同的路径使用路径分隔符os.pathsep分隔开，或者多次使用这个参数）。<br><br>这可以解决有时候第三方模块找不到的问题。|
|--hidden-import MODULENAME<br><br>--hiddenimport MODULENAME|需要进行额外导入的模块。当pyinstaller在程序中找不到一些模块时，需要你额外指定。这个参数可以多次使用，可以解决一些模块找不到的问题。|
|--splash IMAGE_FILE|添加一个启动画面（图片文件）路径，在程序运行前显示指定的启动图片，起到加载提示的效果。|
|-c, --console, --nowindowed|打包程序运行后出现一个黑色的控制台窗口（默认）|
|-w, --windowed, --noconsole|打包程序运行后隐藏控制台窗口|
|-i <FILE.ico or FILE.exe,ID or FILE.icns or Image or "NONE"><br><br>--icon <FILE.ico or FILE.exe,ID or FILE.icns or Image or "NONE">|设置打包后exe程序的图标（只能在Windows和macOS上使用）|
|--disable-windowed-traceback|禁用异常提示（只能在Windows和macOS上使用）|
|--uac-admin|启动打包后的程序时申请以管理员模式运行（仅Windows）|

## 4.3 单文件和文件夹模式打包/隐藏控制台窗口

下面是一个程序示例，将创建一个窗口并显示一张图片image.gif和一段提示。读者无需了解其代码细节。接下来将以这个程序为例进行一个简单的打包示范。

```python
'''
一个简单的应用
'''
 
import tkinter as tk # 导入tkinter
 
root = tk.Tk() # 创建窗口
root.title("我的应用程序") # 更改标题
 
image = tk.PhotoImage(file="assets/image.gif")
label = tk.Label(root, text="你好，用户！", image=image, compound="top")
label.pack() # 显示图片
 
root.mainloop() # 保持窗口运行
```

![](https://i-blog.csdnimg.cn/blog_migrate/9361bd838fb6401e6005c29e48a82483.png)

下面是这个应用文件夹的文件层级结构：

```python
- my_app
    - assets
        - image.gif
    - my_app_name.py
```

由于这个应用不需要进行print和input这样的控制台类操作，所以我选择隐藏控制台。打开cmd并进入程序文件所在的文件夹my_app，打包时添加-w参数：

```python
pyinstaller -w my_app_name.py
```

接下来会出现若干个INFO提示，如果没有错误，那么打包就成功了。

![](https://i-blog.csdnimg.cn/blog_migrate/e94d5fe0371b3dddf322ea8e4ab25c44.png)

完成打包后，生成了build和dist文件夹，以及一个spec文件；dist文件夹包含打包的结果，build文件夹中是一些日志信息，spec文件里面是用于打包的配置信息。

接下来是重要的一步。由于打包时没有绑定任何的资源文件，所以此时运行时会报错，提示找不到image.gif。此时，应该把程序文件夹下的assets文件夹（参见上方的文件夹层级）复制到dist文件夹中的程序文件夹，和exe文件位于同一位置。

接下来，再试一下单文件模式的打包，只需添加-F参数：

```python
pyinstaller -w -F my_app_name.py
```

![](https://i-blog.csdnimg.cn/blog_migrate/48d0c32526ebb8d2c9f272782f944e19.png)

打包后，生成了一个单个的my_app_name.exe，而没有其他文件。同样也需要将assets文件夹复制到与该exe文件的同一位置。 

## 4.4 资源嵌入exe

经常需要复制文件夹不仅麻烦，而且还无法防止里面的内容被用户修改。此时，我们可以使用pyinstaller的--add-data参数，将assets文件夹里面的资源嵌入到exe文件中。

资源嵌入exe只在单文件模式下使用。文件夹模式下，资源文件夹不会嵌入到exe中，但是会被复制到exe所在的文件夹。

使用资源嵌入后，资源文件夹的路径发生了变化，我们不能使用一般的相对路径来调用assets这样的内嵌资源文件夹。

前面已经讲过，pyinstaller单文件模式下的exe启动后，会将嵌入的资源文件放到一个临时的文件夹中，这个文件夹的名字不是固定的，叫做_MEIxxxxx，其中xxxxx是随机数。这个文件夹的路径在打包后会被放到sys._MEIPASS这个变量里面，只需要调用sys._MEIPASS就可以获得这个路径文件夹。

于是，我们通过以下函数返回正确的路径：

```python
def get_path(relative_path):
    try:
        base_path = sys._MEIPASS # pyinstaller打包后的路径
    except AttributeError:
        base_path = os.path.abspath(".") # 当前工作目录的路径
 
    return os.path.normpath(os.path.join(base_path, relative_path)) # 返回实际路径
```

这个函数通过一个相对的路径返回实际的绝对路径。

需要注意：sys._MEIPASS这个属性只有在打包成exe后才被创建，以py代码执行的时候这个属性是不存在的，所以要通过try...except...代码块捕获异常。如果不是pyinstaller模式，那么就使用py文件所在的文件夹的路径作为基本路径。我们不必担心这个函数的工作原理（虽然者不难理解），这个函数可以直接拿来用（是一位叫做[davidpendergast](https://github.com/davidpendergast "davidpendergast")的大佬写的）。

于是，我们将代码改成这样（省略了部分内容）：

```python
...
 
import sys
import os
 
def get_path(relative_path):
    try:
        base_path = sys._MEIPASS
    except AttributeError:
        base_path = os.path.abspath(".")
 
    return os.path.normpath(os.path.join(base_path, relative_path))
 
...
 
image = tk.PhotoImage(file=get_path("assets/image.gif"))
...
```

接下来进行打包：

```python
pyinstaller -w -F --add-data assets;assets my_app_name.py
```

打包完成后会生成一个包含嵌入资源的单独的exe，无需将资源文件放到同一文件夹下也能正常运行。

--add-data的参数由源文件名src和目标文件名dest组成。路径的源文件名和目标文件名用文件分隔符进行分隔，源文件名是该文件或文件夹的原本的路径，目标文件名是该文件夹嵌入到exe后的放入的文件夹名。

> 文件分隔符：在Windows系统上是分号，大部分unix系统上是冒号，可以通过os.pathsep来查看当前系统上的文件分隔符。例如：
> 

```bash
>>> import os
>>> os.pathsep
';'
```

比如--add-data "assets;assets"就表示将原本assets里面的所有文件，放入打包后的assets文件夹。再比如--add-data "assets/*.mp3;music"表示将原本assets里面的所有mp3文件，放入打包后的music文件夹。 

## 4.5 更改图标

打包完成后，默认的程序图标是一个“蛇”形，但我们也可以进行更改。（根据官方文档，该功能只能在Windows和macOS上使用）

![](https://i-blog.csdnimg.cn/blog_migrate/48d0c32526ebb8d2c9f272782f944e19.png)

--icon或-i参数用于设置图标，该参数的值默认为"NONE"，表示使用默认的图标；也可以指定为一个*.ico格式的Windows图标文件路径；*.icns的Mac图标文件路径；或者一个其他图片文件（需安装pillow模块，会通过pillow模块将其转换成标准的ico/icns格式）。

首先添加一个图标文件。图标文件在Windows上格式为*.ico，Mac上是*.icns。

```python
- my_app
    - assets
        - image.gif
    - my_app_name.py
    - icon.ico
```

这个图标文件其实放在哪里都可以，因为打包完成后其实它也相当于嵌入了exe。但为了方便，还是把它放到同一文件夹下比较好。

```python
pyinstaller -i icon.ico my_app_name.py
```

为了方便看，之前设置的-w, -F这些选项都省略了。最后生成了一个图标与icon.ico相一致的exe。

![](https://i-blog.csdnimg.cn/blog_migrate/cf7c304053fe2abff8a3ce5ff1f5098d.png)

## 4.6 启动画面（闪屏）

pyinstaller单文件模式启动速度较慢，所以可能需要一个启动画面（闪屏）进行过渡，提示用户正在进行加载。这个启动画面可以是单张图片，也可以是文本（默认情况下文本禁用，使用方式参见第5章）。

这个启动画面的实现基于Tcl/Tk（和python tkinter模块一样），打包时会附带约1.5MB的额外文件来支持这个功能。

支持闪屏，需要先准备一张图片，必须是PNG格式（如果你安装了pillow模块，可以用pillow模块支持的其他格式）。然后，在打包时加上--splash参数，并传入图片路径。

```python
pyinstaller --splash splash.png my_app_name.py
```

控制闪屏可以通过pyi_splash模块，这个模块和上一节的sys._MEIPASS属性一样，在没有通过pyinstaller打包成exe后是不起作用的，所以必须带上try...except...代码。

pyi_splash.close()方法用于关闭闪屏。一般放在程序开头即可，因为只要运行到程序开头，说明pyinstaller的加载就基本完成了。

于是，在程序开头部分添加以下代码：

```python
try:    import pyi_splash    pyi_splash.close()except ImportError:    pass
```

如果不用这段代码进行关闭，那么闪屏将一直显示。

打包后，闪屏效果如下。

![](https://i-blog.csdnimg.cn/blog_migrate/218bb06bd0b9662fe4defe0e0474dfe7.gif)

至于pyi_splash还有一个update_text方法，用于在闪屏画面上显示加载文本，将在5.7节介绍。 

## 4.7 禁用异常提示

--disable-windowed-traceback参数用于禁用异常提示。如果不添加这个参数，将会在非控制台程序出错（似乎仅限非致命的错误）时弹出一个窗口报告异常信息（注意：仅在隐藏控制台模式下弹出异常报告窗口）。为了测试，我在代码第一行添加了raise Exception，运行打包后的exe后效果如图所示。

![](https://i-blog.csdnimg.cn/blog_migrate/a09924444468b4f881aaba5f7a53f02d.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/880f32f7e5ed8ec0fd2a94bf504701addf756ee7.png)



# 5 使用Spec文件

当你调用以上的打包方式时，会在脚本的文件夹下生成一个*.spec文件。

*.spec文件包含了打包需要使用的所有配置信息。直接在命令行中将*.spec文件路径传给pyinstaller，也可以进行打包。比如：

```python
pyinstaller my_app_name.spec
```

（其中my_app_name.spec是根据my_app_name.py生成的Spec文件） 

这样，当你多次打包同一个项目时，就无需每次都传入那么多参数，只需要传入*.spec文件的路径即可。

*.spec文件也比较好处理，直接使用python编辑器或记事本就能编辑。

## 5.1 生成Spec文件

使用pyi-makespec工具可以根据pyinstaller的命令行参数生成Spec文件。用法很简单，在原先使用pyinstaller的打包命令中，把"pyinstaller"换成"pyi-makespec"就可以生成一个Spec文件。例如：

```python
pyi-makespec -w -F --add-data assets;assets my_app_name.py
```

要更改Spec文件的生成路径，可以指定参数--specpath。

如果报错提示找不到pyi-makespec，转到最后一章：常见问题。

当你使用*.spec文件进行pyinstaller打包时，大部分的打包参数都不可用，需要预先在*.spec文件中预先设定。

pyinstaller会将*.spec里面的内容当做代码执行。单文件模式和文件夹模式的*.spec文件略有不同。

下面是一个*.spec文件（单文件模式打包）的例子。

```python
# -*- mode: python ; coding: utf-8 -*-
 
 
block_cipher = None
 
 
a = Analysis(
    ['my_app_name.py'],
    pathex=[],
    binaries=[],
    datas=[('assets', 'assets')],
    hiddenimports=[],
    hookspath=[],
    hooksconfig={},
    runtime_hooks=[],
    excludes=[],
    win_no_prefer_redirects=False,
    win_private_assemblies=False,
    cipher=block_cipher,
    noarchive=False,
)
pyz = PYZ(a.pure, a.zipped_data, cipher=block_cipher)
 
exe = EXE(
    pyz,
    a.scripts,
    a.binaries,
    a.zipfiles,
    a.datas,
    [],
    name='my_app_name',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    upx_exclude=[],
    runtime_tmpdir=None,
    console=False,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
)
```

下面是一个文件夹模式的*.spec文件的例子：

```python
# -*- mode: python ; coding: utf-8 -*-
 
 
block_cipher = None
 
 
a = Analysis(
    ['my_app_name.py'],
    pathex=[],
    binaries=[],
    datas=[('assets', 'assets')],
    hiddenimports=[],
    hookspath=[],
    hooksconfig={},
    runtime_hooks=[],
    excludes=[],
    win_no_prefer_redirects=False,
    win_private_assemblies=False,
    cipher=block_cipher,
    noarchive=False,
)
pyz = PYZ(a.pure, a.zipped_data, cipher=block_cipher)
 
exe = EXE(
    pyz,
    a.scripts,
    [],
    exclude_binaries=True,
    name='my_app_name',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    console=False,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
)
coll = COLLECT(
    exe,
    a.binaries,
    a.zipfiles,
    a.datas,
    strip=False,
    upx=True,
    upx_exclude=[],
    name='my_app_name',
)
```

这里面包含一些特殊的类，比如Analysis, PYZ, EXE等，文件夹模式下还多了一个COLLECT类。只有当pyinstaller运行时才会被定义，很显然你不能在python解释器中直接调用它们。 这些类的参数与pyinstaller的命令行参数并不一样。

接下来将针对Spec文件中的这些对象进行介绍

## 5.2 Analysis对象

Analysis类包含一些分析信息，它分析模块的导入以及一些依赖文件。

这个类的常用参数介绍如下。

|   |   |   |   |
|---|---|---|---|
|**参数名**|**默认值**|**描述**|**（常用参数）示例**|
|scripts|必选参数，无默认值|需要分析的文件路径列表（一般就是需要打包的文件）|["myscript.py"]|
|pathex|None|需要额外进行分析模块导入的文件（夹）路径，包含命令行--path参数指定内容|["C:/Python310/Lib/site-packages", "C:/my_module]|
|binaries|None|需要嵌入的二进制文件列表，包含命令行--add-binary参数指定内容||
|datas|None|需要嵌入的非二进制文件（夹），包含命令行--add-data参数指定内容|[("assets", "assets"), ("music/*.mp3", "music")]|
|hiddenimport|None|需要额外导入的模块列表|["module1", "module2"]|
|hookspath|None|钩子文件路径列表（钩子文件用于配置一些模块特殊的导入，后文详解）||
|hooksconfig|None|一个字典，包含钩子的配置信息||
|excludes|None|需要被忽略，不进行导入的模块列表||
|runtime_hooks|None|运行时的钩子列表，指定为一系列文件名||
|noarchive|False|如果设为True，则不会将源代码放到一个存档中进行存储，而是作为多个单独的文件||

在完成分析后，需要将一些属性传递给PYZ类。Analysis对象包含了以下属性，你可以不必了解它们：

|   |   |
|---|---|
|**属性名**|**描述**|
|scripts|同参数中的scripts|
|pure|需要一起打包的纯python模块|
|pathex|同参数中的pathex|
|binaries|同参数中的binaries|
|datas|同参数中的datas|

## 5.3 PYZ对象

完成分析后，将Analysis对象的一些属性传递给PYZ类。PYZ相当于一个压缩包，里面储存了所有的依赖文件。

```python
pyz = PYZ(a.pure, a.zipped_data, cipher=block_cipher)
```

## 5.4 EXE对象

定义PYZ对象后，接下来需要定义EXE对象，也就是可执行文件对象。

不同打包模式（单文件或文件夹）的EXE对象参数略有不同。其中常用参数如下：

|   |   |   |   |
|---|---|---|---|
|**参数**|**默认值**|**描述**|**（常用参数）示例**|
|console|True|是否显示控制台，相当于命令行-w参数||
|disable_windowed_traceback|False|是否禁用异常提示，相当于命令行--disable-windowed-traceback参数||
|name|None|可执行文件的名称。在Windows上会自动添加".exe"后缀|"my_app_name"|
|icon|None|可执行文件的图标路径|"icon.ico"|

## 5.5 COLLECT对象（仅-D文件夹模式）

使用文件夹模式打包时还会有一个COLLECT对象，该对象用于创建文件夹。它有一个常用的关键字参数name，表示文件夹的名称。

## 5.6 Bundle对象（仅macOS系统）

如果你要在macOS上创建应用程序，且你的应用程序是无控制台的，那么在exe构建完成之后还需要添加一些代码。

```python
app = BUNDLE(exe,
             name='my_app_name.app',
             icon="icon.ico",
             bundle_identifier=None)
```

## 5.7 Splash对象

如果你想要在应用中添加启动画面（图片和文本都可以），需要在Spec文件中额外添加一个Splash对象进行控制。

在分析完代码后，创建Splash对象：

```python
a = Analysis(...)
 
splash = Splash('splash.png',
                binaries=a.binaries,
                datas=a.datas,
                text_pos=(10, 50),
                text_size=12,
                text_color='black')
```

然后在EXE中绑定splash对象。注意：单文件模式和文件夹模式方式略有不同。

以下是单文件模式绑定splash对象的方法。

```python
splash = Splash(...)
 
exe = EXE(pyz,
          a.scripts,
          splash,                   # <-- both, splash target
          splash.binaries,          # <-- and splash binaries
          ...)
```

以下是文件夹模式的方法。

```python
splash = Splash(...)
 
exe = EXE(pyz,
          splash,                   # <-- splash target
          a.scripts,
          ...)
coll = COLLECT(exe,
               splash.binaries,     # <-- splash binaries
               ...)
```

下面介绍Splash对象的一些参数。注意：由于Splash窗口基于Tcl/Tk（和python tkinter一样），所以里面有一些用法与Tcl/Tk(tkinter)的用法很像，但不重要。

|   |   |   |   |
|---|---|---|---|
|**参数**|**默认值**|**描述**|**（常用参数）示例**|
|image_file|必选参数，无默认值|图片文件路径，必须是PNG格式（如果你安装了pillow模块，可以用pillow模块支持的其他格式）|"splash.png"|
|binaries|必选参数，无默认值|Analysis对象的binaries属性||
|datas|必选参数，无默认值|Analysis对象的datas属性||
|text_pos|None|闪屏文本相对于闪屏图片的显示位置（是一个(x, y)元组，锚点为文本左下角）。如果不指定，则禁用文本显示|(500, 400)|
|text_size|12|文本大小||
|text_font|"TkDefaultFont"|文本使用的字体（必须是系统上安装了的字体），如果不指定则设为系统默认字体|"宋体"|
|text_color|"black"|文本颜色，颜色格式可以是颜色名称字符串或者十六进制颜色字符串，如"#ff00ff"（注意：不支持(r, g, b)元组形式）||
|text_default|"Initializing"|默认显示的文本（后面可以用pyi_splash.update_text来更新显示的文本）|"加载中……"|
|max_img_size|(760, 480)|最大闪屏图片尺寸。如果超出尺寸，那么闪屏图片将会被按纵横比缩放，容纳到该尺寸中。可以设为None不缩放||
|always_on_top|True|闪屏窗口是否置顶，如果置顶，其位于其他窗口之上||
|rundir|"__splash"|设置运行闪屏时，用于存放一些相关文件的文件夹名称。使用这个参数主要是为了避免命名冲突，一般不会使用||

下面就以一个示例来演示Splash的文本显示。使用的代码还是上一章节使用的。

在开头添加以下代码：

```python
try:
    import pyi_splash
    import time
 
    for i in range(100):
        text = f"加载中……进度{i}%"
        time.sleep(0.1) # 模拟一个速度比较慢的加载过程
        
        pyi_splash.update_text(text) # 更新显示的文本
 
    pyi_splash.close() # 关闭闪屏
            
except ImportError:
    pass
```

然后通过pyi-makespec生成对应的Spec文件：

```python
pyi-makespec -w -F --add-data assets;assets --splash splash.png my_app_name.py
```

由于Splash的文本显示只能在Spec文件中进行配置，所以我们先打开my_app_name.spec，将Splash对象的代码进行修改，如下所示：

```python
splash = Splash(
    'splash.png',
    binaries=a.binaries,
    datas=a.datas,
    text_pos=(30, 270),
    text_size=12,
    minify_script=True,
    always_on_top=True,
)```

然后进行打包：

```python
pyinstaller my_app_name.spec
```

运行效果如下：

![](https://i-blog.csdnimg.cn/blog_migrate/1d7a07b49b96487d68be203721ad894e.gif)

可以看到，首先显示文本被设定为加载的各个依赖文件，然后变成update_text中自己设定的加载内容。

## 5.8 多包捆绑（打包多个exe）

> 有些产品由几个不同的应用程序组成，每个应用程序可能依赖于一组通用的第三方库，或者以其他方式共享一部分代码。在打包这样的产品时，如果单独对待每个应用程序，将其与所有依赖项捆绑在一起，那就太可惜了，因为这意味着要存储代码和库的副本。
> 
> 此时，我们可以使用多包特性来捆绑一组可执行应用程序，以便它们共享库的单个副本。我们可以在单文件或单文件夹应用程序中做到这一点。

比如有两个应用都使用了tkinter模块，且这两个应用相关，需要在发布时放到一起（比如一个应用专门用于图片剪裁，另外一个专门用于图片滤镜，它们可能共用了部分功能）。如果分别打包，那么每个应用都会包含一个tkinter模块的依赖文件，而且都储存相同的内容，这就很浪费存储空间。如果用多包捆绑的话，只会有一个tkinter模块的依赖文件，两个应用都可以调用相同的依赖。

## 文件夹模式的多包捆绑

如果采用文件夹模式，想要捆绑多个应用程序，那么只需要共享一个COLLECT对象。假如有hello1.py, hello2.py，将这两个应用进行捆绑，可以将它们的Spec文件进行一些组合。

首先通过pyi-makespec分别生成hello1.py, hello2.py的Spec文件。

然后将其中的Analysis, PYZ, EXE, Splash等对象分别以不同的变量名放入同一个Spec文件，然后将它们的COLLECT对象组合起来。

```python
hello1_a = Analysis(['hello1.py'], ...)
hello1_pyz = PYZ(hello1_a.pure, hello1_a.zipped_data, ...)
hello1_exe = EXE(hello1_pyz,
          hello1_a.scripts, 
          ...)
 
hello2_a = Analysis(['hello2.py'], ...)
hello2_pyz = PYZ(hello2_a.pure, hello2_a.zipped_data, ...)
hello2_exe = EXE(hello2_pyz,
          hello2_a.scripts, 
          ...)
 
coll = COLLECT(hello1_exe,
               hello1_a.binaries,
               hello1_a.zipfiles,
               hello1_a.datas,
 
               hello2_exe,
               hello2_a.binaries,
               hello2_a.zipfiles,
               hello2_a.datas,
               ...
               name='hello')
```

这样，将会生成同一个文件夹，该文件夹下包含两个文件hello1.exe, hello2.exe。 它们共享一部分的依赖文件。

## 单文件模式的多包捆绑

单文件模式下，多包捆绑会生成多个单独的exe，其中一个exe包含它们共有的依赖文件。

比如打包hello1.py和hello2.py，设置hello1包含共有的依赖文件，最后生成hello1.exe, hello2.exe。生成的hello1.exe由于包含两个exe共有的依赖文件，其文件大小会大于hello2.exe。

运行hello1.exe时与单独打包效果相同。但是运行hello2.exe时，它会在hello1.exe中搜索它需要的依赖文件，速度会稍慢。

如果将hello2.exe移动到别的地方，或者将hello1.exe改名，那么hello2.exe将无法运行，因为它找不到hello1.exe，从而无法找到所需的依赖文件。

以下是hello1.py和hello2.py两个程序文件，将以它们为例进行打包。

```python
# hello1.py
while True:
    input("hello1")
 
# hello2.py
while True:
    input("hello2")
```

首先通过pyi-makespec生成对应的Spec文件。完成后，将两个Spec文件的Analysis类汇总到一个文件中，并进行改名。

```python
a1 = Analysis(
    ['hello1.py'],
    ...
)
 
a2 = Analysis(
    ['hello2.py'],
    ...
)
```

接下来在下面调用MERGE函数。这个函数会分析两个文件中重复的依赖项，将结果放到分析类的dependencies属性中。MERGE中位于第一个的程序将会包含共有的依赖项。

```python
MERGE((a1, "hello1", "hello1"), (a2, "hello2", "hello2"))
```

然后将两个文件的ZIP和EXE进行汇总。汇总时需要额外向EXE类传递一个参数Analysis.dependencies。

```python
pyz1 = PYZ(...)
exe1 = EXE(pyz1,
 
    a1.dependencies, ##
 
    a1.scripts, 
    a1.binaries,
    a1.zipfiles,
    a1.datas, ...)
 
pyz2 = PYZ(...)
exe2 = EXE(
    pyz2,
 
    a2.dependencies, ##
 
    a2.scripts,
    a2.binaries,
    a2.zipfiles,
    a2.datas, ...)
```

 保存文件，然后通过pyinstaller打包。

![](https://i-blog.csdnimg.cn/blog_migrate/1ea29d7aae084fd063c79a8ffa757cfb.png)

最后生成两个文件，可以看到hello1.exe的文件大小比hello2.exe大了很多，这是由于hello1.exe中包含了它们共有的依赖库。如果不使用多包捆绑，而是分别单独进行打包，那么两个文件的大小将都会超过5000KB。

# 6 钩子

有一些特殊的模块，它们存在一些特殊的依赖文件（比如ico, json等等）。而pyinstaller的导入分析无法检测到这些特殊的依赖文件，这就导致运行后出现问题。于是，pyinstaller引入了“钩子”。钩子文件其实就是一种python文件，后缀名为*.py即可（和Spec文件的实质是一样的）。钩子文件中指定了某个特殊模块所需要的所有依赖文件。通过传递钩子文件，pyinstaller就能找到那些“隐藏”的依赖文件。

虽然钩子文件的作用也可以被--hiddenimport, --datas这些命令行参数替代，但是使用钩子显然更加方便。

pyinstaller有一些内置的“钩子”，提供了一些常用模块的钩子文件，它们包含Django, pickle, pyqt, scipy等等。

钩子文件的常用命名格式是：hook-module.py（其中module是模块名）。（当然你也可以按自己喜好命名）

## 6.1 钩子文件中的全局变量

钩子文件中可以包含以下全局变量（有一些变量可以不被写在文件中）：

|   |   |   |
|---|---|---|
|**属性**|**描述**|**（常用属性）示例**|
|hiddenimports|需要额外导入的模块列表，相当于命令行--hidden-import参数|["sys", "pygame.mixer"]|
|excludedimports|需要被排除，不被自动导入的模块列表（如果有一些模块在其他地方被导入，那么仍然会导入它）|["tkinter"]|
|datas|需要被添加的非二进制文件或文件夹，相当于命令行--add-data参数|[('/usr/share/icons/education_*.png', 'assets') ]|
|binaries|需要备添加的二进制文件，相当于命令行--add-binary参数||

以下是一个钩子文件的示例：

```python
hiddenimports = ["re", "os"]datas = [("assets", "assets)]
```

## 6.2 PyInstaller.utils.hooks

pyinstaller提供了一些方法用于钩子文件的制作。这些方法位于PyInstaller.utils.hooks模块。首先需要在钩子文件导入该模块。（注意pyinstaller的P和I是大写的，这是pyinstaller作为模块时的名称）

```python
import PyInstaller.utils.hooks as hooks
```

下面介绍该模块中的常用函数。

---

**is_module_satisfies(requirements, version=None, version_attr='__version__')**

检验模块版本是否达到requirements的要求，返回一个布尔值。关于requirements的相关格式，详见[PEP 440](https://peps.python.org/pep-0440/ "PEP 440")。version_attr参数指定该模块中版本属性的名称，默认是"__version__"。

下面是一些requirements的例子：

```python
"pygame >= 2.2.1dev1" # 大于2.1.1dev1版本的pygame模块"PIL == 2.9.*"    # 版本以2.9.开头的PIL模块"sphinx >= 1.3.1; sqlalchemy != 0.6" # 同时满足两个要求
```

`collect_submodules(package, filter=<function <lambda>, on_error='warn once')`

返回一个模块的所有子模块。filter是一个筛选函数，接收模块名作为参数，返回一个布尔值表示是否要加入这个模块到返回值中。on_error表示筛选出现异常时的处理，可是："raise"（抛出异常并停止pyinstaller构建），"warn"（只抛出警告，不停止pyinstaller构建），"warn once"（只警告一次，后续与之相同的警告被忽略），"ignore"（忽略，不抛出任何警告或异常）

例如：

```python
# 收集Sphinx的所有子模块（名字中不包含test）
hiddenimports = collect_submodules(
    "Sphinx", filter=lambda name: 'test' not in name)
```

**collect_data_files(package, include_py_files=False, subdir=None, excludes=None, includes=None)** 

返回一个模块使用的所有非二进制文件。include_py_files表示返回的文件列表中是否应该含有*.py格式的文件。subdir是相对于要搜索的包的子目录。excludes, includes分别是需要被排除和被包含的文件列表，可以指定它们来判断是否要保留或移除某些格式的文件。

**collect_dynamic_libs(package, destdir=None, search_patterns=['*.dll', '*.dylib', 'lib*.so'])**

返回一个模块使用的所有二进制动态库文件。

**collect_all(package_name, include_py_files=True, filter_submodules=None, exclude_datas=None, include_datas=None, on_error='warn once')**

相当于上面的collect前缀的几个函数的综合。例如：

```python
datas, binaries, hiddenimports = collect_all('my_module_name')
```

---

使用hooks模块可以更加方便地制作钩子。

## 6.3 为自己的模块提供钩子

如果自己创建的模块需要钩子，那么可以自己定义一个文件，并储存到自己的模块中。

如果你有一个名为module_name的模块文件夹，首先在自己模块的setup.cfg中（与setuptools模块相关，可自行搜索）添加如下代码（注意里面的module_name）：

```python
[options.entry_points]
pyinstaller40 =
  hook-dirs = module_name.__pyinstaller:get_hook_dirs
  tests     = module_name.__pyinstaller:get_PyInstaller_tests
```

然后在module_name项目的文件夹中添加名字为__pyinstaller的文件夹（名称与上面hook-dirs和tests里面的命名相一致即可）。

最后可以在__pyinstaller文件夹中添加hook文件。

# 7 反编译与加密

pyinstaller制作的应用，可能会被反编译（即根据生成的exe得到这个程序的源代码）。同时，也有一些方法来预防反编译，或者增加反编译的难度。

需要注意的是，反编译代码的结果大多数时候并不准确，只能得到大概的代码，可能需要后期处理。

## 7.1 通过pyinstxtractor进行反编译

pyinstxtractor是专门针对pyinstaller的反编译工具（也就是说，其他的打包工具，比如py2exe,cx_Freeze打包的程序无法被这个工具反编译，需要通过别的反编译工具）。

## 下载工具

首先通过以下链接下载pyinstxtractor： 

[PyInstaller Extractor download | SourceForge.net](https://sourceforge.net/projects/pyinstallerextractor/ "PyInstaller Extractor download | SourceForge.net")

也可以通过github下载（推荐上面的方法，毕竟github访问较慢）：

[GitHub - extremecoders-re/pyinstxtractor: PyInstaller Extractor](https://github.com/extremecoders-re/pyinstxtractor "GitHub - extremecoders-re/pyinstxtractor: PyInstaller Extractor")

下载完成后，得到pyinstxtractor.py。

还需要下载pycdc，链接如下：

[pyinstaller/pycdc.exe · Python-ZZY/CSDN-articles - Gitee.com](https://gitee.com/python_zzy/csdn-articles/blob/master/pyinstaller/pycdc.exe "pyinstaller/pycdc.exe · Python-ZZY/CSDN-articles - Gitee.com")

想要反编译一个pyinstaller打包的应用，流程是这样的：

1. 先用pyinstxtractor将*.exe文件反编译成*.pyc文件
2. 用十六进制编辑器修改*.pyc文件中的magic number
3. 使用pycdc工具将*.pyc转换为最终的*.py文件

下面还是以这个程序为例作为演示：

```python
'''
一个简单的应用
'''
 
import tkinter as tk # 导入tkinter
 
root = tk.Tk() # 创建窗口
root.title("我的应用程序") # 更改标题
 
image = tk.PhotoImage(file="assets/image.gif")
label = tk.Label(root, text="你好，用户！", image=image, compound="top")
label.pack() # 显示图片
 
root.mainloop() # 保持窗口运行
```

为了方便演示，采用单文件模式进行打包：pyinstaller -F my_app_name.py。打包完成后，将assets文件夹放到exe所在文件夹中。

## 反编译exe

下面进入反编译环节。进入exe的文件夹，将下载的pyinstxtractor.py放到*.exe所在文件夹下。

![](https://i-blog.csdnimg.cn/blog_migrate/cdec991da412281eda276b476b9690e8.png)​

在exe所在文件夹启动cmd，并输入以下命令：

```python
python pyinstxtractor.py my_app_name.exe
```

![](https://i-blog.csdnimg.cn/blog_migrate/60c6178293df811a3b767d846627d0e2.png)​

运行完成后，可以看到生成了一个xxxx.exe_extracted的文件夹

![](https://i-blog.csdnimg.cn/blog_migrate/b406ce9e52922fd8f6a9c335b7faff02.png)​

进入此文件夹，可以找到一个文件名和应用名称相同，但是没有后缀的文件，这就是得到的*.pyc文件（虽然生成的时候没有后缀，不过这并不妨碍它本身的文件类型）。xxxx.exe_extracted文件夹中的其他文件则是一些依赖程序文件，等等。

![](https://i-blog.csdnimg.cn/blog_migrate/7f33989b4d6e3b6504cf607dea0d09cb.png)​

## 添加magic number

接下来一步很关键，需要在my_app_name这个文件中添加magic number，也就是一些python版本相关的信息。这里需要使用十六进制编辑器（有很多，不一一介绍了，sublimetext就可以用来编辑） 

magic number前面一部分与python版本有关，可以通过下面的代码查看当前python版本所对应的magic number的十六进制形式：

```python
import importlib
print(importlib.util.MAGIC_NUMBER.hex())
```

 ![](https://i-blog.csdnimg.cn/blog_migrate/5a0918d1444f013a3d40aeece2d19823.png)

如果不知道编写这个应用所使用的python版本，可能要受到一点阻碍，网上有各python版本对应的magic number表，有需要可自行搜索。

在十六进制编辑器中打开my_app_name的pyc文件。

![](https://i-blog.csdnimg.cn/blog_migrate/53da6763be330ab6d13f7c99e0fb8620.png)

然后将上面代码得到的magic number添加到此文件的最前面（表示版本信息，很重要）。

![](https://i-blog.csdnimg.cn/blog_migrate/dddc4e311a9bceb5a25c3324fdbd9dbd.png)

然后再补充24个0（这些东西代表时间、代码大小等信息，没什么用，可以全部用0填充）

![](https://i-blog.csdnimg.cn/blog_migrate/b4191d15fcd7a365c7054ae7a2dd2a42.png)

最后保存文件。

如果不进行这一步，那么下一步反编译pyc时将会报错，提示magic number有误。

## 反编译pyc

将pycdc.exe和my_app_name的pyc文件放到同一文件夹下。

![](https://i-blog.csdnimg.cn/blog_migrate/5460e0bc3a0e3c26fd365aba96e5218a.png)

在当前文件夹下启动cmd，输入：

```python
pycdc my_app_name>final_my_app_name.py
```

当前文件夹下生成了final_my_app_name.py，这就是反编译的结果。事实上，结果并不完美，存在很多错误，需要后期进行调整。

 ![](https://i-blog.csdnimg.cn/blog_migrate/894d5bdc187271b47a4537540671ea64.png)

除了pycdc，常用于反编译pyc文件的还有uncompyle6，但是目前（截至2023.12.17）不支持python3.9以上的版本。还有一个在线反编译pyc工具（有限制）：[python反编译 - 在线工具](https://tool.lu/pyc "python反编译 - 在线工具")

## 反编译依赖库

以上的方法用于反编译主文件exe，如果想要反编译这个应用依赖的python模块，可以进入xxxx.exe_extracted文件夹下的PYZ-00.pyz_extracted，里面包含了这个应用所需的依赖模块的pyc文件。按照上一节的方法即可进行反编译。

## 7.2 编译为pyd文件以防止反编译

在打包前将一些依赖的*.py文件编译成*.pyd文件，可以大大增加反编译的难度。*.pyd是动态链接库，它可以像python模块一样调用但不能直接运行。使用*.pyd不仅可以增加反编译难度，还能提升代码速度。

作者根据[python源码打包成exe、exe反编译、pyd加密防止反编译_unknown magic number 227 in-CSDN博客](https://blog.csdn.net/m0_47410750/article/details/125555120 "python源码打包成exe、exe反编译、pyd加密防止反编译_unknown magic number 227 in-CSDN博客")

的方法进行了尝试但是效果并不好，以下仅给出方法。

## 调整代码

在开始之前，我们需要先对代码进行调整。*.pyd文件只能被导入但不能直接运行，所以主程序不能进行pyd编译。所以，这样做以后依赖文件不会被反编译，但主程序还是会被反编译。我们可以进行一些改变，在主文件中留下那些不重要的代码，让反编译者看不到什么宝贵的信息，将重要的程序内容放到一个模块中，在主文件中只进行调用。

在my_app_name.py文件夹下新建一个*.py文件（命名是随意的，这里把它命名为module.py），在这个module.py文件中写入原本是my_app_name.py中的内容，不过做了一些改变，加了一个main函数用于运行。

```python
import tkinter as tk # 导入tkinter
 
def main():
    root = tk.Tk() # 创建窗口
    root.title("我的应用程序") # 更改标题
 
    image = tk.PhotoImage(file="assets/image.gif")
    label = tk.Label(root, text="你好，用户！", image=image, compound="top")
    label.pack() # 显示图片
 
    root.mainloop() # 保持窗口运行
```

再来修改my_name_app.py。这个入口程序直接从module.py（编译后就变成module.pyd了）中导入main函数，然后运行。

```python
'''
一个简单的应用
'''
 
from module import * # 这里不能写成from module import main，原因见8.1
 
if __name__ == "__main__":
    main()
```

这样一来，反编译后也只能看到几行与main相关的内容，根本无法获取有用的代码信息。 

```python
import tkinter
from module import main
 
if __name__ == "__main__":
    main()
```

## 下载工具 

先用pip下载Cython：

```python
pip install Cython
```

此外还需要配置Visual Studio的C++开发工具。

先在下方链接下载Visual Studio：

[Microsoft C++ 生成工具 - Visual Studio](https://visualstudio.microsoft.com/zh-hans/visual-cpp-build-tools/ "Microsoft C++ 生成工具 - Visual Studio")

安装生成工具时，勾选“使用C++的桌面开发”并点击右下方安装。如果你已经安装了生成工具但没有勾选这一项，可以启动安装包后，点击“修改”按钮进行更改。

![](https://i-blog.csdnimg.cn/blog_migrate/d9b788ccecc3de92abc9e7ef1f74cffd.png)

![](https://i-blog.csdnimg.cn/blog_migrate/04ab1eb04af27fc87d39dfe007afbcf1.png)

然后等待安装完成。

## 编译成pyd

在my_app_name.py的文件夹下新建setup.py，并输入以下代码：

```python
from distutils.core import setup
from Cython.Build import cythonize
 
setup(ext_modules=cythonize(["module.py", ]))
```

用ext_modules参数指定需要进行编译的文件。如果还有别的python文件需要编译，可以在列表中修改。

保存文件后，启动cmd，运行以下命令：

```python
python setup.py build_ext --inplace
```

完成编译后，文件夹中会生成一些新的文件，从中找出与模块名同名的*.pyd文件，其他没用的文件可以删掉。

![](https://i-blog.csdnimg.cn/blog_migrate/f4ef5c422d652e8961c42282dd7ca015.png)

这个文件名中有一些诸如cp310-win...的东西，表示这个python版本、系统等信息，需要手动将它们删除，只保留模块名和后缀名。

![](https://i-blog.csdnimg.cn/blog_migrate/2a767405065e86453a0afb01a5b28c04.png)

 生成pyd文件后，无需管原来的文件module.py，因为python导入时会优先选择pyd后缀的模块。

如果输入setup的命令后，出现了一些报错信息，提示需要Microsoft Visual C++，则代表上一步没有正确完成。

## 进行exe打包

完成以上步骤后，可以通过pyinstaller进行打包了。

# 8 注意事项与常见问题

## 注意事项：导入 

作者似乎发现，在导入python模块时，如果使用from xxx import func的形式，那么pyinstaller只会把导入的func包含到打包的应用里面，而不是整个xxx模块。并且这个过程中，pyinstaller不会管xxx模块中还依赖于哪些模块，这就可能导致func函数根本无法运行。

比如我有同一目录下的main.py和module.py：

```python
'''module.py'''
import tkinter
 
def main():
    tkinter.Tk()
    tkinter.mainloop()
```

```python
'''main.py'''
from module import main
 
if __name__ == "__main__":
    main() 
```

如果用pyinstaller对main.py进行编译，那么最后就会因为找不到tkinter模块而闪退。这是因为main.py中只导入了module.py中的main函数，pyinstaller会进行优化，只打包def main()函数的这一部分，而不会打包module.py中的其他内容（包括import tkinter这一重要的一句）

直接用python运行main.py时就不会出现以上问题。因为 python 解释from xxx import func这一句时，还是会先把xxx模块运行一次，但是只保留了一个func的变量名。

这里提供三种解决方案：

- 换一种导入方式，使用import xxx *（推荐）
- 在主程序中把模块所需的依赖全导进来（在上面的示例中，就是main.py中添加import tkinter这一句）
- 打包时指定--hidden-import等参数（不推荐）


## 编译时报错：Failed to collect submodules

- 【问题描述】在执行 _pyinstaller_ 打包命令时，终端发生如下报错。

```bash
4424 WARNING: Failed to collect submodules for 'torch.testing._internal.optests' because importing 'torch.testing._internal.optests' raised: ModuleNotFoundError: No module named 'expecttest'  
```

- 【问题分析】_pyinstaller_ 打包时候，会手动检查所有依赖项是否存在，这与你在终端中运行 _python_ 脚本的检查逻辑不一样，手动在终端中运行其只会在该模块被调用时却不存在才会报错，如果不存在没被调用，它是不会报错的。

- 【方案尝试】终端输入 _pip install expecttest_ 后回车

- 【方案检验】报错消失


## 编译时报错：

联系前面有关于 _pyinstaller_ 对 _from xxx import xxx_ 的处理过程，可以断定，这是由于模块内部使用了该语句造成的，这导致打包的时候打包不完整。


## 编译时报错：不是可运行的命令或程序

首先检查pyinstaller是否被成功安装。在cmd输入pip list，看安装列表中是否存在pyinstaller，如果没有则重新安装，根据安装信息进行处理。

如果显示未找到pyinstaller，则应用绝对路径指定pyinstaller。首先进入所在的文件夹，然后复制路径。打包时，将pyinstaller替换为pyinstaller.exe的绝对路径。（pyi-makespec找不到同理）

- Windows: Python目录下的Scripts文件夹
    
- GNU/Linux: /usr/bin
    
- macOS (using the default Apple-supplied Python) /usr/bin
    
- macOS (using Python installed by homebrew) /usr/local/bin
    
- macOS (using Python installed by macports) /opt/local/bin
    

例如，你想要执行pyinstaller myscript.py，但是提示找不到pyinstaller.exe。在你的电脑上，pyinstaller.exe安装在了C:\Python\Python310\Scripts这个位置，那么执行：

```python
C:\Python\Python310\Scripts\pyinstaller.exe myscript.py
```

还有一种解决方法，将pyinstaller.exe所在的文件夹添加到系统环境变量（推荐）。Windows上添加环境变量办法如下：

右击“此电脑” -> 单击“属性” -> 单击“高级系统设置” -> 单击“环境变量” -> 在用户变量的位置单击“Path” -> 单击“编辑” -> 在“编辑环境变量”的窗口单击“新建” -> 写入pyinstaller.exe的所在路径 -> 一路“确定”进行保存。

## 运行后报错：找不到某些模块或文件

如果是第三方模块找不到，有可能是pyinstaller没有搜索到储存第三方模块的文件夹。这个文件夹一般是python安装目录下的Lib/site-packages。此时，打包时可以指定-p参数，将这个文件夹路径传递给pyinstaller进行打包，这样pyinstaller就会在site-packages中搜索相关的第三方模块。

```python
pyinstaller -p .../Lib/site-packages ...
```

如果只是找不到某些模块中的部分文件，则需要为该模块添加钩子，可参见上文。

如果有些模块没有在python程序中通过import显式地导入，可以尝试修改命令行参数--hidden-import，加入找不到的模块。需要这样的原因往往是那个模块在程序中的导入位置无法被pyinstaller检测到。

例如，如果提示找不到sys, os两个模块，那么命令行参数修改为：

```bash
pyinstaller --hidden-import "sys" --hidden-import "os" ...
```

如果使用Spec打包，则应在Analysis类的hiddenimport参数的列表中添加找不到的模块。

## 运行后报错：失去标准输入

```python
RuntimeError: input(): lost sys.stdin
```

某些程序打包后出现以上报错内容。这是由于代码中使用了input这样的函数让用户进行输入，但是打包时却设置了隐藏控制台。于是，运行打包后的应用后就没有一个控制台让用户进行输入，就会报错。（失去stdout并不会报错，但是print内容不会显示）

## 运行时闪退

闪退是由于程序中出现了致命的异常，可能由多种原因导致，需要根据引发的异常进行处理。这里提供一种方法来看到造成闪退的报错信息。

在当前文件夹下启动cmd（方法：将文件资源管理器窗口上方的文件路径修改为"cmd"，然后回车），然后运行：

```python
my_app_name.exe
```

此方法通过命令行运行这个应用。如果程序闪退，命令行窗口不会关闭，上面就留下了报错信息。

如果命令行可以正常运行，但是直接运行exe会闪退，考虑下面两种情况：

- 程序只有print输出，输出结束就自动退出了，来不及看到输出内容。解决方法：在程序末尾加一行input()，这样最后输出完会停在那里
- 还有可能是受到部分杀毒软件的影响（尤其是文件夹模式下的打包，很容易出现杀毒软件误报），比如火绒、360等，参见下一节

## 运行后杀毒软件提示存在木马/无权限访问

出现运行后杀毒软件报木马可能是杀毒软件误报导致的，并不代表一定真的有木马。此外，exe直接运行时异常闪退，但是exe在命令行仍能正常运行，也有可能是受到杀毒软件的影响。

杀毒软件报错可能是因为打包后的程序显得不可信，一般可以采取以下措施：

- 使用单文件模式打包(-F)而不是文件夹模式
- 给程序指定一个图标(--icon xxx.ico)
- 如果不是命令行程序，打包时尽量把命令行隐藏（添加-w参数）
- 如果杀毒软件报错是由于对应的某个模块造成的，可以自行搜索避免的方法