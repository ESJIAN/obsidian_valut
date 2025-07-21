
|特性|img2table+Tesseract|PaddleOCR|EasyOCR|
|---|---|---|---|
|结构化表格输出|✅（强）|✅（强）|❌（弱）|
|识别准确率|一般|高|高|
|手写体支持|弱|强|较强|
|多语言|多|多|多|
|GPU支持|❌|✅|✅|
|安装难度|需装Tesseract|需装PaddlePaddle|简单|
|适合场景|清晰印刷体表格|各类表格/文本|各类文本|

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

**结论：**

- 需要**表格结构化输出**，推荐 PaddleOCR 或 img2table+Tesseract（PaddleOCR 更强大）。
- 需要**手写体、复杂背景、速度快**，推荐 PaddleOCR。
- 只需**简单文本识别**，EasyOCR 安装最简单，支持多语言。
- 只用 CPU，且表格结构简单，img2table+Tesseract 也可用。
