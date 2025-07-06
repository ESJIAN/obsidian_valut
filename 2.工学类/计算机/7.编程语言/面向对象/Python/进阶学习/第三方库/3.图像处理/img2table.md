**Tesseract-OCR Windows 64-bit 5.5.0 安装与使用指南**

#### 前言

Tesseract-OCR 是一款开源的[光学字符识别](https://so.csdn.net/so/search?q=%E5%85%89%E5%AD%A6%E5%AD%97%E7%AC%A6%E8%AF%86%E5%88%AB&spm=1001.2101.3001.7020) (OCR) 引擎，支持多种语言识别，广泛用于文档扫描、图像文字提取等任务。本文将详细介绍如何在 Windows 平台上安装 Tesseract-OCR 5.5.0 版本，并进行基础配置与示例使用。

#### 一、准备工作

1. **操作系统要求**：Windows 7/8/10/11 64-bit
2. **下载地址**：访问 [Tesseract-OCR 官方发布页](https://github.com/tesseract-ocr/tesseract/releases "Tesseract-OCR 官方发布页") 下载 `tesseract-ocr-w64-setup-5.5.0.20241111.exe` 安装包。
3.  实际下载网址: [https://github.com/UB-Mannheim/tesseract/wiki](https://github.com/UB-Mannheim/tesseract/wiki "https://github.com/UB-Mannheim/tesseract/wiki")
    

#### 二、安装步骤

1. **运行安装程序**
    
    - 双击 `tesseract-ocr-w64-setup-5.5.0.20241111.exe` 文件，启动安装向导。![](https://i-blog.csdnimg.cn/direct/3129d7076d9e413cacb3f11d057223a5.png)
2. **选择语言包**
    
    - 安装向导提供了多个语言包供选择。
    - 默认情况下包含 `English (eng)` 语言包，我们下图中的四个包进行勾选
		![image.png](https://i0.hdslb.com/bfs/openplatform/b043fb5e50077896812fb78b569541c3cb06e3ed.png)
	
3. **选择安装目录**
    
    - 默认安装路径为 `C:\Program Files\Tesseract-OCR`。
    - 可以根据需要更改安装位置，但建议避免安装到系统保护的路径。
4. **完成安装**
    
    - 点击 `Install` 按钮，等待安装过程完成。
    - 完成后，点击 `Finish` 退出安装程序。

#### 三、配置环境变量

为了在命令行中直接使用 `tesseract` 命令，需要配置环境变量：

1. **打开系统环境变量配置窗口**
    - 右键点击 `此电脑` -> `属性` -> `高级系统设置` -> `环境变量`。
2. **添加路径**
    - 在 `系统变量` 中找到 `Path`，点击 `编辑`。（注意不是直接在变量配置窗口中新建变量）
    - 新增 `你安装的目标文件夹\Tesseract-OCR`，然后点击 `确定` 保存。
3. **重启IDE**
	- IDE 上的终端需要通过重启才能更新新的 PATH 变量，原因参见[[系统问题]]


#### 四、验证安装

1. 打开 `cmd` 命令提示符。
2. 输入以下命令检查 Tesseract 版本：
    
    ```sql
    tesseract --version
    ```
    
3. 如果返回版本信息，如 `tesseract v5.5.0`，说明安装成功。

#### 五、示例使用

##### 1. 基本命令

```lua
tesseract input.png output.txt
```

- `input.png` 为输入的图片文件。
- `output.txt` 为输出的文本文件。

##### 2. 多语言识别

```cobol
tesseract input.png output.txt -l chi_sim+eng
```

- `-l` 参数用于指定语言，多个语言可用 `+` 连接。

##### 3. 自定义输出格式

- 输出为 PDF 文件：
    
    ```lua
    tesseract input.png output pdf
    ```
    
- 输出为 TSV 文件：
    
    ```lua
    tesseract input.png output tsv
    ```
    

#### 六、[常见问题](https://so.csdn.net/so/search?q=%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98&spm=1001.2101.3001.7020)及解决方案

##### 1. **找不到 `tesseract` 命令**

- 检查环境变量配置是否正确。
- 重启命令提示符窗口再试。

##### 2. **中文识别不准确**

- 确保安装了 `chi_sim` 语言包。
- 图片清晰度不足会影响识别效果，建议提高分辨率或进行预处理。

##### 3. **输出乱码**

- 可以尝试将图片转换为灰度图或二值化后再识别。

#### 七、卸载方法

如果需要卸载 Tesseract-OCR：

1. 打开 `控制面板` -> `程序和功能`。
2. 找到 `Tesseract OCR`，右键点击，选择 `卸载`。
3. 删除 `C:\Program Files\Tesseract-OCR` 文件夹（如果需要）。

#### 八、总结

通过上述步骤，您可以成功在 Windows 平台上安装并使用 Tesseract-OCR 5.5.0。Tesseract 作为一款功能强大的 OCR 工具，适用于多种文字识别场景。在使用过程中可以结合图像预处理工具提升识别效果，实现高效的文本提取。