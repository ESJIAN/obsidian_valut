![Excel入门到精通（第一章：认识Excel；第二章：Excel的基本操作）](https://picx.zhimg.com/v2-d6a4be3e8e7e643f55851ccb5879f5e0_720w.jpg?source=d16d100b)

大家好，欢迎大家收看2019Excel表格入门到精通系列课程，每周二、四进行更新。整套课程一共十六章，我将会由浅入深的讲解Excel表格全部的操作功能，希望通过系统的学习会让你的知识体系更加牢固。同时有任何问题可以在下方留言，看到后会及时回复。

今天是我们第一章的学习，学习完后希望你可以在评论区输入“今日学习完毕”，我们一起打卡，坚持学完整套课程。

如果课程对你有帮助，希望可以多多支持。

## **目录预览**

**第一章：认识Excel**

1. Excel界面介绍
2. Excel常用功能设置
3. 工作表的编辑和移动

**第二章：Excel的基本操作**

1. 制作表格
2. 制作斜线表头
3. 格式刷
4. 行列的移动复制
5. 行列的插入删除
6. 行列的隐藏显示
7. 行高与列宽
8. 冻结窗格

**第三章：Excel高效办公**

1. 25个常用快捷键
2. 数据变图片
3. 图片转Excel
4. PDF转Excel
5. 屏幕截图
6. 清除命令
7. 选择性粘贴
8. 双击鼠标小技巧

**第四章：表格的样式与编辑**

1. 条件格式的用法
2. 排序与筛选
3. 查找替换与定位

**第五章：数据的处理**

1. 分列
2. 下拉菜单的制作
3. 删除重复值
4. 多表合并

**第六章：公式介绍**

1. 公式输入
2. 单元格引用

**第七章：基础函数**

1. ROW函数（行位置）
2. COLUMN函数（列位置）
3. RANDBETWEEN函数（随机整数）
4. RAND函数（随机小数）
5. MOD函数（求余）
6. REPT函数（重复内容）
7. MAX函数（最大值）
8. MIN函数（最小值）

**第八章：统计函数**

1. SUM函数（求和）
2. SUMIF函数（单条件求和）
3. SUMIFS函数（多条件求和）
4. AVERAGE函数（求平均）
5. AVERAGEIF函数（单条件求平均）
6. AVERAGEIFS函数（多条件求平均）
7. COUNT函数（统计数字个数）
8. COUNTA函数（统计非空单元格个数）
9. COUNTBLANK函数（统计空白单元格个数）

**第九章：逻辑函数**

1. IF函数（条件判断）
2. IFS函数（多条件判断）
3. AND函数
4. OR函数
5. ISODD函数（奇数判断）
6. ISEVEN函（偶数判断）

**第十章：日期与时间函数**

1. YEAR函数（提取年）
2. MONTH函数（提取月）
3. DAY函数（提取天）
4. HOUR函数
5. MINUTE函数
6. DAY函数
7. TODAY函数（当前日期）
8. NOW函数（当前时间）
9. DATE函数（生成日期）
10. DATEDIF函数（计算日期差）
11. WEEKDAY函数（日期转星期）
12. EDATE函数（计算N个月之前或之后的日期）
13. WORKDAY函数（计算N个工作日之前或之后的日期）
14. NETWORKDAYS函数（计算两日期之间的工作日天数）

**第十一章：文本函数**

1. TEXT函数
2. LEN函数（计算字符串长度）
3. LEFT函数（从左提取字符串）
4. RIGHT函数（从右提取字符串）
5. MID函数（从中间提取字符串）
6. CONCAT函数（文本连接）
7. TEXTJOIN函数（文本连接）

**第十二章：查找函数与Subtotal函数**

1. VLOOKUP函数
2. MATCH函数
3. Find与FINDB函数
4. SEARCH与SEARCHB函数
5. Subtotal函数

**第十三章：超级表**

1. 认识超级表
2. 创建超级表
3. 超级表的用法

**第十四章：图表的使用**

1. 簇状柱形图
2. 堆积柱形图
3. 折线图
4. 条形图
5. 组合图
6. 迷你图

**第十五章：数据透视表**

1. 认识数据透视表
2. 创建数据透视表
3. 数据透视表字段
4. 数据透视表的删除
5. 数据透视的内容清除
6. 数据更新
7. 字段的隐藏和显示
8. 制作简单的数据看板
9. 切片器与报表链接

**第十六章：打印和保护**

1. 保护工作表
2. 保护工作簿
3. 打印设置
4. 页眉和页脚的设置



- # 1. 笔记回忆


- # 2. 笔记重点

- # 3. 笔记犯错

- 表格是0索引的访问模式，所以访问地址数要在实际行/列数上取减一位


- 合并单元格的实体单元格访问通常是**左上角**作为实际访问的单元格。这意味着，如果你合并了A8、A2、B1和B2这四个单元格，那么在代码中，你应该使用A1来访问这个合并后的单元格，在下图所示的实际情况中就是访问D8单元格来获取这个合并单元格的值或者是对象。

![image.png](https://i0.hdslb.com/bfs/new_dyn/648df44a85f5f6339e29a7959422fe94394687087.png)


# **第一章：认识Excel**

## 1. **Excel介绍**

- ## 1.1. **认识操作界面**

打开一个新的Excel空白工作簿，主要分为以下**六大板块**：

![](https://pica.zhimg.com/v2-f31463b491609bf7879027a507a8c75e_1440w.jpg)

<center><b>图：Excel 打开文件后的默认视图</b></center>

![](https://pic2.zhimg.com/v2-6c43d763bc80524833c324e427e180f1_1440w.jpg)

<center><b>图：六大板块同图对比</b></center>

- ### **1.1.1. [快速访问工具栏](https://zhida.zhihu.com/search?content_id=171340849&content_type=Article&match_order=1&q=%E5%BF%AB%E9%80%9F%E8%AE%BF%E9%97%AE%E5%B7%A5%E5%85%B7%E6%A0%8F&zhida_source=entity)**

快速访问工具栏位于界面的左上角。用于放置**用户经常使用到的功能**，默认有保存，撤消，恢复三个按钮；

可以点击右侧的自定义快速访问工具栏按钮，添加其它按钮，或者在任意功能区，选中一个功能，右键选择“**添加到快速访问工具栏**”，也可以从工具栏删除某功能。

![动图封面](https://pic2.zhimg.com/v2-4fbc32086ab0046f53c170c1ee254ca3_b.jpg)

像是某些**高频使用**的功能如保存、筛选、升降序等我们可以将之添加到快速访问工具栏，这样在用到的时候，就不用再去某个功能区寻找。  

- ### **1.1.2. 功能区**

接着是功能区，默认存在 **文件、开始、插入、页面布局、公式、数据、审阅、视图**八大功能区；

每个功能区内 存在多种功能，下面的章节里逐一向大家介绍各功能区的主要内容，及**高频使用功能**，重点掌握！这里先不介绍。

![动图封面](https://pic2.zhimg.com/v2-dce49e488d7f61ecf97a9e0d33d1d1bb_b.jpg)

- ### **1.1.3. [编辑栏](https://zhida.zhihu.com/search?content_id=171340849&content_type=Article&match_order=1&q=%E7%BC%96%E8%BE%91%E6%A0%8F&zhida_source=entity)**

功能区下面是编辑栏，编辑栏最左侧有一个显示框，**显示当前鼠标选中单元格的位置**，如单元格选中A1单元格，这显示框中显示“A1”。

显示框后面依次是**取消（×）、确定插入（√）、插入函数（fx）**，点击fx,会出现各种类型的函数，查找选择需要的函数即可。

![](https://pica.zhimg.com/v2-c05899650daf6e9d238112971a2e95ba_1440w.jpg)

- ### **1.1.4. [单元格区域](https://zhida.zhihu.com/search?content_id=171340849&content_type=Article&match_order=1&q=%E5%8D%95%E5%85%83%E6%A0%BC%E5%8C%BA%E5%9F%9F&zhida_source=entity)**

编辑栏下方是单元格区域，也就是日常我们操作的区域（输入、修改、删除数据），单元格区域是由行与列组成的电子表格，存储数据的载体；

在Excel2016版本中，**Excel共有1048576行（2的20次方）、16384列（2的14次方）**，行标签用阿拉伯数字1-1048576表示，点击一个数字，即可选中一整行，列标签用过大写字母A-XFD表示，点击一个字母，即可选中一整列。

![](https://pic4.zhimg.com/v2-da96c89180c48f62c25caa46e26cf933_1440w.jpg)

但这并不意味着单个Excel表格可以存储这么多的数据，当数据量达到几十万条之后，处理过程中，工作表将会出现卡顿，数据量越大、公式越多，卡顿越严重（其实是程序运算的时间越长，日常工作中**并不建议在工作表中保存大量的公式**）。

欣慰的是，大部分日常工作的数据量并不会很大，Excel足以应付。

- ### **1.1.5. [工作表标签](https://zhida.zhihu.com/search?content_id=171340849&content_type=Article&match_order=1&q=%E5%B7%A5%E4%BD%9C%E8%A1%A8%E6%A0%87%E7%AD%BE&zhida_source=entity)**

单元格区域下方是工作表标签，左侧是各个工作表的名字（一般**一个Excel文件叫工作簿，里面的每个插页（sheet）叫工作表**），点击加号（+）按钮，可以新增工作表，双击工作表的名字，可以重命名。

右侧是**水平滚动条**，左右拖动，可以查看不同列数据的内容（Excel**界面最右侧是垂直滚动条**，查看不同行的数据，也可以用鼠标滚轮上下滚动）

![动图封面](https://pic1.zhimg.com/v2-f9128455225e5176cab181a4295c6d86_b.jpg)

- ### **1.1.6. [状态栏](https://zhida.zhihu.com/search?content_id=171340849&content_type=Article&match_order=1&q=%E7%8A%B6%E6%80%81%E6%A0%8F&zhida_source=entity)**

最底下是状态栏，当在**选中单元格数据时，状态栏会显示相应的信息**，比如平均值，计数，求和。状态栏右侧是常用的视图功能，有**普通、页面布局，分页预览、缩放比例设置**。

![动图封面](https://pic1.zhimg.com/v2-0d4ea6135d4b943178a469e678f74628_b.jpg)

状态栏有很多实用的的小功能往往被人忽略，如计数，打开任意一张表，想知道这张表一共有多少行或列，不用拉到表格最底部，**直接选中一列或一行，然后观看状态栏的数字即可**，同样求和，不用sum公式，直接选中要求和的单元格，观看底部状态栏即可，十分的方便。

![](https://pic1.zhimg.com/v2-425704bbb4d7640ef16536e10d5f1164_1440w.jpg)

  

如果你的状态栏没有计数、求和等功能，**右键状态栏**，你会发现意外的惊喜。

本节主要讲述Excel界面各个模块的功能，对**Excel有个宏观的认识**，下面的章节进入正文，结合案例讲解重要功能键的主要作用与应用场景。

- ## 1.2. 认识Excel文件

1. **工作簿（Workbook）**
    
    - 一个Excel文件即一个工作簿，默认包含 **3个工作表**（可自定义数量），如 `Sheet1`、`Sheet2`、`Sheet3`。
2. **工作表（Worksheet）**
    
    - 由 **行（Row）** 和 **列（Column）** 组成的表格，行号为数字（1, 2, 3…，最大行号：1048576），列标为字母（A, B, C…，最大列数：16384）。
    - 工作表标签位于底部，可重命名、插入、删除或隐藏。
3. **单元格（Cell）**
    
    - 行与列的交点，通过 **单元格地址** 定位（如 `A1`、`C5`）。
    - 单元格可存储 **数据**（文本、数值、日期等）、**公式** 或 **函数**。


## 2. **Excel常用功能设置**

**背景与主题设置：文件—更多—账户—选择喜欢的背景和主题

![](https://picx.zhimg.com/v2-d6f94a76a119bd1eba9c876a8006a175_1440w.jpg)

**自动保存设置：文件—更多—选项—保存—可以更改文件自动保存的时间

![](https://pica.zhimg.com/v2-5086c10b8b297b6eef3d5c9401435386_1440w.jpg)

  
**恢复工作表：文件—更多—选项—保存—复制文件位置路径—粘贴到计算机选框—敲击enter键—选择要恢复的文件

![](https://pica.zhimg.com/v2-b0a56cea8e40f2c874f582e0eb996c04_1440w.jpg)

![](https://pic3.zhimg.com/v2-e18108f6733992b83b140415401f50a2_1440w.jpg)

**产品更新设置：文件—更多—账户—根据自己的需求选择立即更新或者禁用更新

![](https://pic4.zhimg.com/v2-302b905c790de934ef03d30cb0e114f3_1440w.jpg)

**自定义快速访问工具栏设置：把保存、打印预览、撤销、重做添加到自定义快速访问工具栏，只需要点击三角符号—选中对应的命令即可完成添加。

![](https://pic2.zhimg.com/v2-bb5147ecbf29035fa7954c68914cedf1_1440w.jpg)

或者点击三角符号—选择其他命令—跳转到快速访问工具栏—选择对应的命令添加到右边的自定义快速访问工具栏区域—点击确定即可完成添加。（不需要可以删除，并且可以通过旁边的三角符号调整顺序）

![](https://pica.zhimg.com/v2-3d42a8b7381e0b8318fcaba3189a5f10_1440w.jpg)

添加完成后的效果

![](https://pic3.zhimg.com/v2-5a3ef9f192442cf9f4cd0a6f8f6092f6_1440w.jpg)

**界面常见问题处理：**

**标题栏/名称框/编辑栏/网格线不见了如何恢复？**

点击视图—勾选编辑栏、网格线、标题可以恢复—取消勾选则隐藏

![](https://pica.zhimg.com/v2-c1df6c14e7f292e49c25e9ab2eef8d6a_1440w.jpg)

**工作标签/滚动条不见了如何恢复？**

![](https://pic4.zhimg.com/v2-74d71364778fbdc01179f7c66ef23817_1440w.jpg)

点击文件—更多—选项—高级—勾选上工作标签和滚动条即可

![](https://pica.zhimg.com/v2-d3f1eec90bb7e45b51f0f28bf1f40282_1440w.jpg)

## 3. **工作表的编辑和移动**

新建工作表/工作表删除/隐藏/添加颜色等操作（单击鼠标右键）

![](https://pic3.zhimg.com/v2-024a5764b8d6d20de7011091f0cec240_1440w.jpg)

**工作表的移动复制**

案例：

把《Excel实战讲解》工作簿中的9.3（数据看板）工作表移动到《Excel入门到精通》工作簿。

<center><b>首先打开2个工作簿</b></center>

![](https://pic4.zhimg.com/v2-22a412e64cc1eb2b5bf8e99a81dc825f_1440w.jpg)

<center><b>选中9.3工作表—鼠标单击右键—选择移动或复制</b></center>

![](https://pic3.zhimg.com/v2-09580c885838ab489863bb7a7400ad42_1440w.jpg)

<center><b>点击下拉按钮—选择《Excel入门到精通》工作簿—勾选建立副本</b></center>

![](https://pica.zhimg.com/v2-1aaf82635fb0e22874bc6aa008eb58e8_1440w.jpg)

<center><b>选择移动到最后—点击确定。这样就把《Excel实战讲解》工作簿中的9.3（数据看板）工作表移动到《Excel入门到精通》工作簿中了。</b></center>

![](https://picx.zhimg.com/v2-7a6bb7cc59a48d151ebd9c13115e9939_1440w.jpg)

![](https://pic3.zhimg.com/v2-c8e3f8a63fe024fa5c5bdf70f30d76a2_1440w.jpg)

---

# **第二章：Excel的基本操作**

## 1. **制作表格**

![](https://pic3.zhimg.com/v2-5f576ff7a19c2b2e06b0b02bdda1b87e_1440w.jpg)

## 2.**制作斜线表头**

Ctrl+1设置单元格格式—点击边框—选择样式—选择斜线。

![](https://picx.zhimg.com/v2-e45e9d28077bcc4514f9b3a286980c03_1440w.jpg)

## **3.格式刷**

格式刷是指把相同格式（例如，颜色、字体样式和大小，以及边框样式）快速应用到多个文本或图形。 格式刷可从一个对象复制所有格式，并将其应用到另一个对象上，可以将其理解为格式的复制和粘贴。

选择要复制格式的文本或图形。

在“开始”选项卡上，单击“格式刷”，单击只能刷一次，双击刷多次。

若要更改文档中多个选定内容的格式，必须先双击"格式刷"。

要停止设置格式，请按 Esc。

## **4.行列的移动复制**

行移动（列同理）

选中行—移动光标—当光标变成黑色十字箭头时按住鼠标左键进行拖动

![](https://pic1.zhimg.com/v2-aa21bd7e3ab2c00f9ab4b50ebefca34a_1440w.jpg)

行复制（列同理）

选中行—移动光标—当光标变成黑色十字箭头时按住ctrl键不放和再按住鼠标左键进行拖动

![](https://picx.zhimg.com/v2-84a747b2afc74b828c062ef84b6cb825_1440w.jpg)

## **5.行列的插入删除**

列的插入

我们需要在序号后插入3列，选中序号后3列—单击鼠标右键—点击插入（行同理）

![](https://pic2.zhimg.com/v2-0fef7f6a9dfab246681dc75940b848ef_1440w.jpg)

列的删除

选中需要删除的列—单击鼠标右键—点击删除（行同理）

![](https://pic1.zhimg.com/v2-b5bc28823747a0fc3acbe81f7543df62_1440w.jpg)

## **6.行列的隐藏显示**

隐藏列

选中需要隐藏的列—单击鼠标右键—点击隐藏（行同理）

![](https://pic3.zhimg.com/v2-e8952fb5d1b3b304364e7e7dfe9da6ea_1440w.jpg)

取消隐藏列

选中隐藏的列的旁边2列—单击鼠标右键—点击取消隐藏（行同理）

![](https://pic2.zhimg.com/v2-cee8581c865b6b31e34844a37ade9c7d_1440w.jpg)

## **7.行高与列宽**

设置指定列宽

选中需要设置列宽的列—单击鼠标右键—点击列宽—输入数字（行高同理）

![](https://pica.zhimg.com/v2-052cce0afab5a5fbc6f6f627a2673ba0_1440w.jpg)

也可以移动光标—当光标变成黑色十字箭头时进行拖动

![](https://pica.zhimg.com/v2-d5b9fd17f7c30aee085ff714a600c886_1440w.jpg)

## **8.冻结窗格**

冻结首行——选中首行——点击视图——冻结首行

![](https://pic2.zhimg.com/v2-7a23281616b6c2b52650c9f76d229551_1440w.jpg)

首行冻结后的效果，方便浏览（冻结首列同理）

![](https://pic2.zhimg.com/v2-51a8c5f3abc62a244f24f46c3d1b3629_1440w.jpg)

现在冻结前2行前2列（多行多列），选中C3单元格——点击冻结窗格（如果之前有设置，需要先取消）

![](https://pica.zhimg.com/v2-6ad5af4a101ac00c4922817d75e6fb9e_1440w.jpg)

效果如下

![](https://picx.zhimg.com/v2-8416931fa83383cc23099e52c9077705_1440w.jpg)







# **第三章：Excel高效办公**

## **1.25个常用快捷键**

Ctrl+C 复制

Ctrl+X 剪切

Ctrl+V 粘贴

Ctrl+Z 撤销上一步操作

Ctrl+S 保存文件

Ctrl+A 全选

Ctrl+1 设置单元格格式

Ctrl+Y 恢复上一步操作

Ctrl+F 查找

Ctrl+G 定位

Ctrl+H 替换

Ctrl+N 新建工作簿

Alt+Tab 切换浏览窗口

Alt+Enter 强制换行

![动图封面](https://picx.zhimg.com/v2-dc45dac0c7352c36501f1bf9f420c857_b.jpg)

Alt+= 求和

![动图封面](https://picx.zhimg.com/v2-39e31c903ce94e09b4d0c45aa6ff4dff_b.jpg)

Ctrl+P 打印设置

鼠标左键（快速移动单元格）

鼠标变成十字箭头，点击鼠标左键不放进行拖动

![动图封面](https://pic4.zhimg.com/v2-288fefa8059ce2752bca3b4d6c322df1_b.jpg)

Ctrl+鼠标左键（快速复制单元格）

鼠标变成十字箭头，按住ctrl键不放，然后点击鼠标左键不放进行拖动

![动图封面](https://pic4.zhimg.com/v2-e7b8e9e7d5c9ece7e141ef2db124613d_b.jpg)

Ctrl+Enter 一次性填充所选择的单元格

![动图封面](https://pic4.zhimg.com/v2-430a7b753339e597fc8f78a8cf35688f_b.jpg)

F4 循环改变单元格引用的类型（函数常用）

![动图封面](https://pica.zhimg.com/v2-81a2e6993ed47c57fdee5c0f0f40118c_b.jpg)

Ctrl+-(减号) 快速删除行/列

![动图封面](https://pica.zhimg.com/v2-ee9b6298ffe808d41c17a8c7b7bfac8a_b.jpg)

Alt + ; (分号) 只选取显示的行，隐藏行不选取，常搭配ctrl+c一起使用

![动图封面](https://pic4.zhimg.com/v2-c29ccc39f5eca1bc1b68ead700526091_b.jpg)

Ctr+E 智能填充

![动图封面](https://pic3.zhimg.com/v2-f61550128d6717bdb6edf05862037442_b.jpg)

Ctrl+PageDown / PageUp 快速浏览工作表

![动图封面](https://pic3.zhimg.com/v2-842d58ac7895798d84a1d2658e43d766_b.jpg)

Ctrl+Shift+方向键 （选中整行/整列）

![动图封面](https://pica.zhimg.com/v2-e33d38c52125f28ad196a9bf399a4b48_b.jpg)

## **2.数据变图片**

选中需要生成图片的区域—点击复制为图片—选中如屏幕所示和图片—点击确定—最后进行粘贴

![](https://pic3.zhimg.com/v2-f3ecd79a209f5b2a5b92376e434f01b2_1440w.jpg)

## **3.图片转Excel**

在工作中有时候会遇到需要把图片中的数据录入到表格中，如果手动的录入不仅效率低而且还容易出错，这时候我们就可以借助QQ截图功能来帮我们去识别图片中的信息，然后一键复制到表格中。

当然网上也有很多其它的工具可以实现这个功能，但是他们的缺点也很明显，比如要你注册账号、限制次数、限制文件大小、识别率低、收费等等。

我们以下图为例：

我们需要把下图中的数据导入到Excel表中

![](https://pic3.zhimg.com/v2-9d4f08291fe56703b83cf13f3e76edfe_1440w.jpg)

第一步：先把图片导入到Excel表中

![](https://pica.zhimg.com/v2-8d2ce920c4a2e3551e0b1c1c1394083a_1440w.jpg)

第二步：登陆QQ，同时按alt+ctrl+o键进行屏幕内容识别

![](https://pic2.zhimg.com/v2-1f73b6a63ed37912d941b46fa5ca1b51_1440w.jpg)

或者先截图，再点击屏幕识图（2种方法都可以）

![](https://pic3.zhimg.com/v2-94f6975f9a39c86d7ecdfd2e7ce83a8c_1440w.jpg)

![](https://pica.zhimg.com/v2-9fcbf2aeb06a0067a41731a1a6143a32_1440w.jpg)

数据识别出来之后可以进行核对并修改，然后点击转为在线文档（其实就是我们经常用的腾讯文档，如果没有登陆，需要提前登陆/如果之前没有用过，直接在微信小程序搜索腾讯文档，登陆即可，非常方便）。

![](https://picx.zhimg.com/v2-dc2af6b0c80be956248a347d99d49b4d_1440w.jpg)

需要等待几秒钟

![](https://picx.zhimg.com/v2-4db5bf25ef83834341c468b11d9611ed_1440w.jpg)

图片和数据清晰的情况下，识别正确率可以达到99%，然后把在线文档的内容复制粘贴到线下文档，格式进行微调就可以啦。我讲得比较细，实际操作非常快捷和方便。重点是免费、不限次数。

![](https://pic1.zhimg.com/v2-4e1a06351302252be41fb29499867e5a_1440w.jpg)

## **4.PDF转Excel**

PDF转Excel——免费在线PDF转换成Excel转换器 ([http://pdfdo.com](https://link.zhihu.com/?target=http%3A//pdfdo.com))

![](https://pica.zhimg.com/v2-fac408b9eaab17f2584f7703f4a1ced0_1440w.jpg)

直接选择需要转换的文件，上传结束后点击PDF转excel按钮就可以快速的转换，这个网站比其它网站的转化速度更快，而且不需要登陆和注册。

如果需要使用更高级的功能才需要付费，一般使用都是免费的。

![](https://pic2.zhimg.com/v2-4d92ba86eb2d20b1c2e93383df9a7113_1440w.jpg)

## **5.屏幕截图**

点击插入—插图—屏幕截图

![](https://pic2.zhimg.com/v2-d4504c88766eeaa6a761fe378ca58393_1440w.jpg)

## **6.清除命令**

一键清除内容和格式

点击开始—在编辑功能区找到全部清除

![动图封面](https://pica.zhimg.com/v2-78574c44fdf1733e9f43f4130b9c4f60_b.jpg)

仅清除格式

![动图封面](https://picx.zhimg.com/v2-dd4d77d1b2967918e8174d73fccc5429_b.jpg)

仅清除内容（delete键可代替）

![动图封面](https://pica.zhimg.com/v2-a0a4b77688ec6417c37cc94a16c864ac_b.jpg)

清除批

![动图封面](https://pica.zhimg.com/v2-32e0436adebe9ee30f55b40550654f58_b.jpg)

清除超链接

![动图封面](https://pic3.zhimg.com/v2-abc31d1523e403198df9c137c717390a_b.jpg)

## **7.选择性粘贴**

转置（行转列）

复制内容—选择一个空白单元格—单击鼠标右键—点击转置

![](https://pic4.zhimg.com/v2-074f091eb7944edee146292af62ed387_1440w.jpg)

![](https://pic4.zhimg.com/v2-86f00e27201b68c674e9bd7d2d26705f_1440w.jpg)

也可以点击选择性粘贴—勾选转置

![](https://pic4.zhimg.com/v2-b2b48c1248b603c7899581172d507cfb_1440w.jpg)

跳过空白单元格粘贴

把员工新电话更新到通讯录

![](https://picx.zhimg.com/v2-e61124c1f22ab783af8c91ad53a4f9d3_1440w.jpg)

![](https://picx.zhimg.com/v2-c3cc2c1e747bc430ce7b03c84d45f963_1440w.jpg)

运算

所有员工职级增加1级

复制数字1—选中职级区域—单击鼠标右键—选择性粘贴—勾选“加”—点击确定（加减乘除同理）

![](https://pic1.zhimg.com/v2-a4ca6ed5aa9e98c08e3360dab393f4f2_1440w.jpg)

## **8.双击鼠标小技巧**

[知乎视频7853 播放 · 9 赞同视频![点击可播放视频](https://pic1.zhimg.com/v2-d8c4c3a46ddc9a581800217c09dafe55_r.jpg?source=2231c908)​](https://www.zhihu.com/zvideo/1446914735342415872)

  

---

  

# **第四章：表格的样式与编辑**

## 1. **条件格式的用法**

第一种用法：突出单元格规则，我们可以在选中区域内标记出我们想要的数字，如下图，我们标记出大于80的数据。

选中数据—选择条件格式—突出显示单元格规则—点击大于—在选框中输入80—更改颜色—点击确定。

突出显示单元格规则中另外6个命令，方法同理，特别是最后一项标记重复值是经常使用的，可以快速标记出数据中重复的内容。

![](https://pic2.zhimg.com/v2-1e592a59cde3304b98510d2ddf6ec2ff_1440w.jpg)

![](https://pic1.zhimg.com/v2-3f985ad47a4c80a71b3e124cc59ab6ae_1440w.jpg)

第二种用法：最前/最后规则，用法和突出显示单元格规则一样。我们可以在选中区域内标记出前10项（数字和颜色可以修改），如下图

![](https://pica.zhimg.com/v2-571ca6fd14f777460d21c355711ea27a_1440w.jpg)

![](https://pic3.zhimg.com/v2-4123dcc414baac47d2f0fc7b277efa1a_1440w.jpg)

第三种：数据条即数据可视化，非常实用的一个功能。如果只想显示数据条，不显示数字，可以在其它规则中关闭。色阶和图标集的用法和前面3项规则相似，实际操作几次就会了。

![](https://pic2.zhimg.com/v2-4f1372053138a05d0b0171cb5c4a7f3b_1440w.jpg)

## **2.排序与筛选**

筛选的使用

选中标题—点击筛选（快捷键ctrl+shift+L）—标题会生成筛选下拉按钮

![](https://pic2.zhimg.com/v2-cf7f8bc6fcb3d54f1bd1e5d23c92dddb_1440w.jpg)

我们可以点击下拉按钮进行筛选，如果有不同的颜色，也可以按颜色进行筛选

![](https://pic1.zhimg.com/v2-36d3e88189fae864aa21a0e4836f7872_1440w.jpg)

如果我们想要把年龄从小到大排序，我们可以点击升序

![](https://pic1.zhimg.com/v2-b9cfa3fc41e1d03773b20423f96191a0_1440w.jpg)

![](https://pic1.zhimg.com/v2-1a31d6046d9e7a62a75e3b4e9335a7ec_1440w.jpg)

## **3.查找替换与定位**

按内容查找

开始—查找—输入查找的内容

范围：工作表是指只查找当前工作表的内容；工作簿是指在整个工作簿里进行查找。

单元格匹配：如果勾选单元格匹配，那么只能查找到和你输入内容一模一样的单元格。举个例子：我们查找“彭万里”，如果我们不勾选单元格匹配，我们就会查找出2个单元格，“彭万里”和“张彭万里”。

如果勾选上单元格匹配，就只能查找到“彭万里”这个单元格。

![](https://pic3.zhimg.com/v2-ebf5dca60e9a2a938db09f42bf50551c_1440w.jpg)

如果我们想知道姓“李”的员工有多少人，我们可以在查找内容里输入“李*”，下方就会出现姓“李”的员工数量，如果只输入“李”，没有*，那么单元格带李字的都会被查找到。

![](https://pic2.zhimg.com/v2-3a222e5e3ff6d797876395ea64c4ee2f_1440w.jpg)

按格式查找

按格式查找之前，先清空查找内容，然后点击格式按钮，会出现3个选项。如果之前有按格式查找过单元格，我们就先清除格式；我们点击格式会出现一个弹窗让我们自己去设置格式查找，一般很少用；基本都是点击从单元格选择格式，这时候会出现一个吸管，我们去吸一下标题栏，预览这里就会出现标题栏的格式。

![](https://pica.zhimg.com/v2-7002801b31c50c670d981b1401e330e8_1440w.jpg)

最后我们点击查找全部，就会查找出6个单元格。

![](https://pic3.zhimg.com/v2-d4c283f027ccee5e0e9836ad3ad65ec4_1440w.jpg)

# **第五章：数据的处理**

## 1. **分列**

固定宽度分列

选中需要进行分列的文本—点击数据—点击分列—选择固定宽度—点击下一步

![](https://pic4.zhimg.com/v2-12baf82d4ab4ff063efecbda8e62f067_1440w.jpg)

建立分隔线，我们把出生年月提取出来，然后点击下一步

![](https://pic1.zhimg.com/v2-8cbf85ba96045009d3a7ef8862f48ab6_1440w.jpg)

第1列和第3列我们不需要，选中后会变黑色，我们点击不导入此列。

我们再选中我们需要保留的列，点击日期（根据具体情况选择日期或者常规或者文本）。

目标区域可以自己选择位置。

![](https://pic2.zhimg.com/v2-6afc8a35cc9840ab179c3574800c21df_1440w.jpg)

点击完成，日期就被我们提取出来了

![](https://pic3.zhimg.com/v2-2a1a39251b5a0ed92a156fe43f2f8012_1440w.jpg)

分隔符号分列

前面几步操作相同—然后选择分隔符号

这里我们可以选择分号，逗号，空格。如果都没有，可以选择其它，自己手动输入。

然后会出现数据预览，没有问题就直接点击下一步

![](https://picx.zhimg.com/v2-4ea5098d12bfe5ed8cd9c948dfe21ddf_1440w.jpg)

因为这次我们所有内容都要保留，所以我们直接选择目标区域

![](https://pica.zhimg.com/v2-55cd820cf448edb734e27e159e2cf544_1440w.jpg)

点击完成

![](https://pica.zhimg.com/v2-83ca04b0860b87ccf6126bf3fdca71fa_1440w.jpg)

## **2.下拉菜单的制作**

[知乎视频2857 播放 · 14 赞同视频![点击可播放视频](https://pic3.zhimg.com/v2-485d02ad6c62bc25cee3802c526e21d0_r.jpg?source=2231c908)​](https://www.zhihu.com/zvideo/1447971385968205824)

## **3.删除重复值**

当我们需要对一列数据保留唯一值时，我们就要使用删除重复值

选中数据区域—点击数据—点击删除重复值—如果有标题就勾选数据包含标题，我们这里没有标题，所以不勾选

![](https://pic2.zhimg.com/v2-be867b98433b13e2c88dda48311d7db5_1440w.jpg)

点击确定

![](https://pica.zhimg.com/v2-a769403780a8314066f8250b18677740_1440w.jpg)

## **4.多表合并**

同一个工作簿的多个表格合并

以下图为例

工作簿的名称我们命名为：《多表合并演示》，现在工作簿里面有5张表，对应了不同部门的人员信息，我们需要把所有人员信息合并到一张表格里。

![](https://pic1.zhimg.com/v2-56fb2a69efc1a17e6df1864b67d1df82_1440w.jpg)

我们在工作簿里面新建一张表格，命名为：《信息汇总》。然后选择数据——获取数据——自文件——从工作簿

![](https://pic4.zhimg.com/v2-8ede22afe7f9aeed4fa6a8041fb5d627_1440w.jpg)

找到《多表合并演示》工作簿，选中并打开

![](https://pic3.zhimg.com/v2-6df0bd5c6393859b0d2cb042451f94f4_1440w.jpg)

这时候会弹出一个导航器，勾选选择多项，勾选需要合并数据的表格，点击转换数据

![](https://picx.zhimg.com/v2-8cb1fe048bdc8f872c42a4c4a6ee3cb7_1440w.jpg)

数据会加载几秒钟

![](https://pica.zhimg.com/v2-179cf62f27297f2d77f3bbdde32840a0_1440w.jpg)

我们点击追加查询的下拉按钮，选择将查询追加为新查询

![](https://pic4.zhimg.com/v2-db40e21887b6f1392265901634ac1935_1440w.jpg)

接下来选择三个或更多表，把可用表的信息添加到要追加的表，点击确

![](https://pic2.zhimg.com/v2-e461b8b18fd74092818a9689d73c41fb_1440w.jpg)

这时候会出现一个新的表格：追加1

![](https://pic3.zhimg.com/v2-c3193a7b6ec9364709ae69e18060f41c_1440w.jpg)

选择关闭并上载下拉按钮——点击关闭并上载至

![](https://pic2.zhimg.com/v2-73f398f8266cedefb3a5f13a02376ca5_1440w.jpg)

这时候会弹出一个选框，我们选择仅创建链接，点击确定

![](https://pic2.zhimg.com/v2-721094ff9b5ac2f145cadef0ace47047_1440w.jpg)

接下来选中追加1——单击鼠标右键——加载到

![](https://pica.zhimg.com/v2-51f2f2657767b29858c9e089ff1293d4_1440w.jpg)

选择表——现有工作表——确定

![](https://pic3.zhimg.com/v2-3ee1d2dbc43b6b34986185e79c7d03e8_1440w.jpg)

这时候所有数据都合并到了一张表格

![](https://picx.zhimg.com/v2-fa0730ec5bb8a8117159c899a44e1659_1440w.jpg)

**第二种：不同工作簿里的多个表格合并**

以下图为例

与上个案例有所不同的是，现在每个部门的人员信息都在不同的工作簿里面，现在有5个工作簿的数据需要合并到一张表格。

![](https://pic2.zhimg.com/v2-cf336b8b5d5505da5c43fbd9b4c3ef8f_1440w.jpg)

首先我们新建一个文件夹，命名：《各部门人员信息表》，然后把上面5个工作簿放到《各部门人员信息表》这个文件夹里。

![](https://pica.zhimg.com/v2-7ffc70e883eba647fa4fad352473fd1e_1440w.jpg)

接下来我们再新建一个工作表命名：公司人员信息汇总表，打开表格——点击数据——获取数据——自文件——从文件夹

![](https://pica.zhimg.com/v2-a7af6213a299239c7a66f9d494a87430_1440w.jpg)

找到《各部门人员信息表》这个文件夹并打开

![](https://pic4.zhimg.com/v2-0fc29b612d600f1396f94c44f0602703_1440w.jpg)

点击转换数

![](https://pic1.zhimg.com/v2-598c879fdda352b4e42df0427a9a9bea_1440w.jpg)

选中content，单击鼠标右键——删除其他列

![](https://pic3.zhimg.com/v2-b4dbbaff69248086c457c52a4642e3dc_1440w.jpg)

选择添加列——自定义列，输入固定的公式：Excel.Workbook([content],true)，注意：[content]不是手写的，是点击插入按钮，插入到公式里面的。最后点击确定。

![](https://picx.zhimg.com/v2-004b4d320323feea7a9b36f125faa7f5_1440w.jpg)

选择自定义列旁边的拉伸按钮——取消勾选使用原始列名作为前缀——点击确定

![](https://pica.zhimg.com/v2-dc8dce917aa6bae1d463a1c5700496c0_1440w.jpg)

选择Data——单击鼠标右键——删除其他列

![](https://pica.zhimg.com/v2-e47a8eb93ee91325257deaaf371cb164_1440w.jpg)

选择Data旁边的拉伸按钮——取消勾选使用原始列名作为前缀——点击确定

![](https://pic3.zhimg.com/v2-bbf0a99e07f81d8250346205357ef4b0_1440w.jpg)

回到主页——点击关闭并上载下拉按钮——选择关闭并上载至...

![](https://pic4.zhimg.com/v2-771869d26ef39456580323a6de0898ef_1440w.jpg)

这时候会弹出导入数据——选择表——现有工作表——确定

![](https://pic2.zhimg.com/v2-b52e2154d997a7036e0fe1d3b018e63f_1440w.jpg)

所有数据都加载到了《公司人员信息汇总表》

![](https://pic1.zhimg.com/v2-fcfbacade40264ff1b181c5460d25cd4_1440w.jpg)

---

#  第六章：公式介绍

- # 1. 本章回忆

- # 2. 本章重点

- # 3. 本章犯错

- # 4. 本章思考


## 1. **公式输入**

公式的介绍：所有公式都是以"="开头，结束可以点击enter键或者点击编辑栏的✓结束

![](https://pica.zhimg.com/v2-907afd1d71f3a3e28a5c8de7cee2f6e6_1440w.jpg)

## **2.单元格引用**

| A8   | 相对引用 | 允许行、列都相对引用       |
| ---- | ---- | ---------------- |
| A$8  | 混合引用 | 锁定引用行为8行，允许列相对引用 |
| $A$8 | 绝对引用 | 锁定引用行为8行，引用列为8列  |


EXCEL单元格的引用包括绝对引用、相对引用和混合引用三种。

以下图为例，B8单元格相对引用A8单元格的值，这时候下拉单元格选框就会得到`B9=A9,B10=A10,B11=A11,B12=A12`，这就是**相对引用**

![](https://pic4.zhimg.com/v2-db132795701135a5841dd65152f609a5_1440w.jpg)

以下图为例，**C8单元格列相对引用行绝对引用A8单元格的值**，这时候下拉单元格选框就会得到`C9=A$8,C10=A$8,C11=A$8,C12=A$8`，因为**把行锁定**了，这就是**混合引用**。

![](https://picx.zhimg.com/v2-9eede55bfaf7d15552cf21867874e43d_1440w.jpg)

以下图为例，B17单元格绝对引用B1单元格，这时候无论是下拉单元格还是左右拉动单元格得到都是=$B$1，因为把行列都锁定了，没有办法变化，这就是**绝对引用**。

![](https://pic2.zhimg.com/v2-77edee3a8f90429223b683ef3de830e3_1440w.jpg)

我们可以通过点击公式—显示公式，查看所有单元格中的公式。

![](https://pic3.zhimg.com/v2-08f15d79ecdb56aaaff875386f2a175c_1440w.jpg)

# **第七章：基础函数**

1. **ROW函数（行位置）**

ROW函数是用来确定光标的当前行位置或者指定单元格行位置的函数。

语法：=row()

案例：求C14单元格所在的行位置

![](https://pica.zhimg.com/v2-cc22d8deb82877adf736e79c5fc69342_720w.jpg?source=d16d100b)

**2.COLUMN函数（列位置）**

COLUMN函数是用来确定光标的当前列位置或者指定单元格列位置的函数。

语法：=COLUMN()

案例：求C14单元格所在的列位置

![](https://picx.zhimg.com/v2-d0543483d619c7762562d069a7130c76_720w.jpg?source=d16d100b)

**3.RANDBETWEEN函数（随机整数）**

RANDBETWEEN函数是返回指定的最小值和指定最大值之间的一个随机整数。

语法：RANDBETWEEN（bottom,top）

Bottom参数： 指定的最小整数。

Top参数： 指定的最大整数。

案例

![动图封面](https://picx.zhimg.com/v2-3758cd55abe347e5c34e7637193b6b8d_720w.jpg?source=d16d100b)

**4.RAND函数（随机小数）**

随机小数

Rand函数是返回一个大于等于 0 及小于 1随机实数。

语法：RAND()

案例

![动图封面](https://pica.zhimg.com/v2-0e99ce57305ed043f2d119a1b87db125_720w.jpg?source=d16d100b)

**5.MOD函数（求余）**

求余函数

mod函数是一个求余函数,是用于返回两数相除的余数，返回结果的符号与除数的符号相同。

语法：=MOD(被除数,除数)

案例

![动图封面](https://pic1.zhimg.com/v2-68f6e14055b0a73c8c97579c7edb099f_720w.jpg?source=d16d100b)

**6.REPT函数（重复内容）**

REPT函数是按照给定的次数重复显示文本的函数。

语法：=rept(需要重复显示的文本,重复显示的次数)

案例

![动图封面](https://pica.zhimg.com/v2-aa8e3f867a9e9c9bd4513dcae23b53c7_720w.jpg?source=d16d100b)

**7.MAX函数（最大值）**

MAX函数是求最大值函数。

案例

![](https://picx.zhimg.com/v2-79efe37a54b9d8c76bca8a07b764b08e_720w.jpg?source=d16d100b)

**8.MIN函数（最小值）**

MIN函数是求最小值函数。

案例

![](https://picx.zhimg.com/v2-5a7ed10e6b0fce7d87489224acce0d68_720w.jpg?source=d16d100b)

---

# 第八章：统计函数

1. **SUM函数（求和）**

SUM函数是一个求和函数，以将单个值、单元格引用或是区域相加，或者将三者的组合相加。

语法：SUM(number1,[number2],...)

number1 （必需参数）要相加的第一个数字。 可以是具体数字，也可以是单元格引用或者单元格区域。

number2，这是要相加的第二个数字。

![](https://picx.zhimg.com/v2-9bdeceab1a4c34036a4b101d820ee64e_720w.jpg?source=d16d100b)

**2.SUMIF函数（单条件求和）**

SUMIF函数是对选中范围内符合指定条件的值求和。

sumif函数语法是：=SUMIF(range，criteria，sum_range)

sumif函数的参数如下：

第一个参数：Range为条件区域，用于条件判断的单元格区域。

第二个参数：Criteria是求和条件，由数字、逻辑表达式等组成的判定条件。

第三个参数：Sum_range 为实际求和区域，需要求和的单元格、区域或引用。

案例

![](https://pica.zhimg.com/v2-d437dcec2ef8d956fce69b9ab28e9804_720w.jpg?source=d16d100b)

**3.SUMIFS函数（多条件求和）**

SUMIFS函数，快速对多条件单元格求和。

SUMIFS函数语法是：SUMIFS(sum_range, criteria_range1, criteria1, [criteria_range2, criteria2], ...)

sumifs函数的参数如下：

第一个参数：sum_range 是需要求和的实际单元格。

第二个参数：criteria_range1为计算关联条件的第一个区域。

第三个参数：criteria1为条件1，条件的形式为数字、表达式、单元格引用或者文本

第四个参数：criteria_range2为计算关联条件的第二个区域。

第五个参数：criteria2为条件2。

实际案例

![](https://picx.zhimg.com/v2-106158cb56d5c15ab3da11097588d9c0_720w.jpg?source=d16d100b)

**4.AVERAGE函数（求平均）**

AVERAGE函数是计算平均值的函数。

语法：AVERAGE( number, number2,……)

案例

![](https://picx.zhimg.com/v2-bf1b11fcd76bf0a53c2bdf01f1076143_720w.jpg?source=d16d100b)

**5.AVERAGEIF函数（单条件求平均）**

AVERAGEIF函数是计算某个区域内满足给定条件的所有单元格的平均值。

语法：AVERAGEIF(range, criteria, [average_range])

使用方法可参考SUMIF函数

![](https://picx.zhimg.com/v2-20ca876dcdd6655c957e1a9bb0e8656f_720w.jpg?source=d16d100b)

**6.AVERAGEIFS函数（多条件求平均）**

AVERAGEIFS函数是求多重条件所有单元格的平均值。使用方法可参考SUMIFS函数

语法：=averageifs(average_range,criteria_range1,criteria1,criteria_range2,criteria2,...)

案例

![](https://pic1.zhimg.com/v2-bb493550990edf808ee7148a110714a5_720w.jpg?source=d16d100b)

**7.COUNT函数（统计数字个数）**

COUNT函数给定数据集合或者单元格区域中数据的个数进行计数，COUNT函数只能对数字数据进行统计，对于空单元格、逻辑值或者文本数据将不统计。

案例

![](https://pic1.zhimg.com/v2-68a6a1c83a3e9d992e724e694a067448_720w.jpg?source=d16d100b)

**8.COUNTA函数（统计非空单元格个数）**

COUNTA函数是计算区域内非空单元格的个数。

案例

![](https://pic1.zhimg.com/v2-a37293768ff27129686c3f83bdf6dd17_720w.jpg?source=d16d100b)

**9.COUNTBLANK函数（统计空白单元格个数）**

COUNTBLANK函数是计算区域内空白单元格的个数。

案例

![](https://pica.zhimg.com/v2-9d427ca0e023bb21dbd4e89322bc8380_720w.jpg?source=d16d100b)

# 第九章：逻辑函数

1. **IF函数（条件判断）**

IF函数是条件判断函数：如果指定条件的计算结果为 TRUE，IF函数将返回某个值；如果该条件的计算结果为 FALSE，则返回另一个值。

语法：IF(logical_test,value_if_true,value_if_false)

logical_test：测试条件

value_if_true：满足条件返回的结果

value_if_false：不满足条件返回的结果

案例

![](https://pic1.zhimg.com/v2-b4648e00a6d784fcd8e14a535a5b20d4_720w.jpg?source=d16d100b)

**2.IFS函数（多条件判断）**

IFS函数是多条件判断函数，检查是否满足一个或多个条件并返回与第一个TRUE条件对应的值

=IFS(条件1,值1,条件2,值2……条件N,值N)。

案例

![](https://picx.zhimg.com/v2-cd49101dc8c521733cf26d9dd7a857c5_720w.jpg?source=d16d100b)

**3.AND函数**

AND函数是指所有参数的逻辑值为真时，返回TRUE；只要有一个参数的逻辑值为假，即返回 FALSE。

案例

![](https://pic1.zhimg.com/v2-02afaf232abb743960e77ba4c18d73ac_720w.jpg?source=d16d100b)

**4.OR函数**

OR函数是指任何一个参数逻辑值为 TRUE，即返回 TRUE；所有参数的逻辑值为 FALSE，才返回 FALSE

案例

![](https://pic1.zhimg.com/v2-0b62bd16bb108321f11213e776720f6b_720w.jpg?source=d16d100b)

**5.ISODD函数（奇数判断）**

ISODD函数是一个奇数判断函数，如果数字为奇数则返回TRUE。

![动图封面](https://pic1.zhimg.com/v2-9f5dabc18c081ba0d65f42a1ea14ecbe_720w.jpg?source=d16d100b)

**6.ISEVEN函（偶数判断）**

ISEVEN函数是一个偶数判断函数，如果数字为偶数则返回TRUE。

![动图封面](https://picx.zhimg.com/v2-889bec5290502b4ebe4cefcaf3826116_720w.jpg?source=d16d100b)

---

# 第十章：日期与时间函数

1. **YEAR函数（提取年）**

YEAR函数是从日期中提取年

![](https://pic1.zhimg.com/v2-b10abff63e4016a7489f19bebce707a8_720w.jpg?source=d16d100b)

**2.MONTH函数（提取月）**

MONTH函数是从日期中提取月

![](https://pic1.zhimg.com/v2-a426346dfd31b89699265746addbbd9f_720w.jpg?source=d16d100b)

**3.DAY函数（提取天）**

DAY函数是从日期中提取日

![](https://picx.zhimg.com/v2-9d75031a22e98850234059ad7e1e35d8_720w.jpg?source=d16d100b)

**4.HOUR函数**

Hour函数是从指定时间获取小时。

返回0和 23 之间（包括0和23）的整数（表示一天中某个小时）。

![](https://pic1.zhimg.com/v2-0e8438d1195df4956bd5746b9acb1cd8_720w.jpg?source=d16d100b)

**5.MINUTE函数**

返回时间值中的分钟，分钟是一个介于 0 到 59 之间的整数。

![](https://pic1.zhimg.com/v2-5028d3546da9c6c2625c35624486292d_720w.jpg?source=d16d100b)

6.DAY函数

返回某日期的天数，天数是介于 1 到 31 之间的整数。

![](https://picx.zhimg.com/v2-69d894cbe5ff49f1126a858566144349_720w.jpg?source=d16d100b)

**7.TODAY函数（当前日期）**

TODAY函数是返回当前日期的函数，固定公式：=today()，是一个跟随时间变化而变化的函数。

![动图封面](https://picx.zhimg.com/v2-5a1f3c4df30de0349a82a07df02f57df_720w.jpg?source=d16d100b)

**8.NOW函数（当前时间）**

NOW函数是返回当前时间的函数，固定公式：=now()，每分钟都会变化，按键盘上的F9键可以刷新，一般都是配合其它函数一起使用。

![动图封面](https://pica.zhimg.com/v2-fed61e2102fc71d3c8201feba6d41d43_720w.jpg?source=d16d100b)

**9.DATE函数（生成日期）**

DATE函数是指输入指定的参数生成日期

语法：=date（year,month,day）

![](https://pic1.zhimg.com/v2-f9d0e8d00ca482002da7831df93bb885_720w.jpg?source=d16d100b)

**10.DATEDIF函数（计算日期差）**

DATEDIF函数是计算两日期之差，返回两个日期之间的年\月\日间隔数。

语法：DATEDIF(start_date,end_date,unit)

Start_date 起始日期

End_date 结束日期

Unit 为所需信息的返回类型：Y" 时间段中的整年数；"M" 时间段中的整月数；"D" 时间段中的天数；"MD" 起始日期与结束日期的同月间隔天数；"YD" 起始日期与结束日期的同年间隔天数；"YM" 起始日期与结束日期的同年间隔月数。

案例

![](https://picx.zhimg.com/v2-f2b24a975226b1a5cafbcb6127055af7_720w.jpg?source=d16d100b)

![](https://picx.zhimg.com/v2-24683affaf365e02446952c1e36710eb_720w.jpg?source=d16d100b)

![](https://picx.zhimg.com/v2-916f95e3de4cfba1983d93df016f918d_720w.jpg?source=d16d100b)

**11.WEEKDAY函数（日期转星期）**

WEEKDAY函数是返回某日期的星期数。

语法：WEEKDAY(serial_number，return_type)

serial_number 指日期

return_type指返回类型，一般都选择2

![](https://picx.zhimg.com/v2-5ca2001c46231dc24af6f48c1d804c12_720w.jpg?source=d16d100b)

案例

![](https://pica.zhimg.com/v2-4c02e7861e08d17596384eeed75ba435_720w.jpg?source=d16d100b)

**12.EDATE函数**

EDATE函数是用于计算指定日期之前或之后N个月的具体日期。

语法：EDATE(start_date,months)

start_date：表示起始日期的日期。

months：表示start_date 之前或之后的月份数。（之后是正数，之前是负数）

案例：当前日期是2021/12/10，8个月之后的具体日期是多少？这个函数常用于商品过期时间、还款日期、工期完工日期等。

![](https://pica.zhimg.com/v2-8ad6e5351ed731012e8c7e254905a63c_720w.jpg?source=d16d100b)

**13.WORKDAY函数**

返回在某日期（起始日期）之前或之后N个工作日的具体日期。 工作日不包括周末和专门指定的假日。 在计算发票到期日、预期交货时间或工作天数时，可以使用函数 WORKDAY 来扣除周末或假日。

语法：=WORKDAY(start_date, days, [holidays])

Start_date必需参数。 代表开始日期。

Days必需参数。开始日期之前或之后不含周末及节假日的天数。 Days 为正值将生成未来日期；为负值生成过去日期。

Holidays可选参数。 一个可选列表，其中包含需要从工作日历中排除的一个或多个日期，例如各种省/市/自治区和国家/地区的法定假日及非法定假日。 该列表可以是包含日期的单元格区域，也可以是由代表日期的序列号所构成的数组常量。

案例：当前日期是2020/5/1，25个工作日之后的日期是？

![](https://pic1.zhimg.com/v2-c485fcdd12b46ea1e0043396d5f07db4_720w.jpg?source=d16d100b)

**14.NETWORKDAYS函数**

计算2个日期之间的工作日天数，工作日不包括周末和专门指定的假期。

语法：NETWORKDAYS(start_date, end_date, [holidays])

Start_date必需参数。开始日期。

End_date必需参数。结束日期。

Holidays可选参数。休息日，例如：省/市/自治区和国家/地区的法定假日以及其他非法定假日。 该列表可以是包含日期的单元格区域，或是表示日期的序列号的数组常量。

案例：2020/5/1到2020/10/1有多少个工作日？

![](https://picx.zhimg.com/v2-b216f1aa5e10c06e10ed19000e13f97a_720w.jpg?source=d16d100b)

# **第十二章：查找函数**

1. **VLOOKUP函数**

VLOOKUP函数是一个运用非常广的纵向查找函数。

语法：VLOOKUP(lookup_value,table_array,col_index_num,[range_lookup])

lookup_value：要查找的值

table_array：要查找的区域

col_index_num：返回数据在查找区域的第几列数

range_lookup：精确匹配/近似匹配

案例：精确查找

![](https://picx.zhimg.com/v2-9b13e0435eb34aaba0b2bc9e81a865c1_720w.jpg?source=d16d100b)

案例：模糊查找

![](https://picx.zhimg.com/v2-dbdb8283e0c8ad48ab580398ad30ca76_720w.jpg?source=d16d100b)

案例：反向查找

![](https://picx.zhimg.com/v2-d622d3465257cb42c11b4a468fbef494_720w.jpg?source=d16d100b)

**2.MATCH函数**

MATCH函数返回指定数值在指定数组区域中的位置。

语法：MATCH(lookup_value, lookup_array, [match_type])

lookup_value：查找的值

lookup_array：查找的区域

match_type：可选参数（1、0、-1）

![](https://pic1.zhimg.com/v2-40b540a98ddfe56e550aad073e8ffafc_720w.jpg?source=d16d100b)

案例：查找冯兴国在B列的位置

![](https://picx.zhimg.com/v2-a534cce7c88ed5f8c24a071f6f7eee19_720w.jpg?source=d16d100b)

**3.Find与FINDB函数**

Find函数是从文本字符串中查找特定的字符位置，区分大小写

语法：=FIND(要查找的字符串、被查找的字符串、[开始位置])

案例：查找天在文本中的位置，查找C在文本中的位置，find区分大小写，所以最后一个会错误

![](https://picx.zhimg.com/v2-ea77bcc3f66f960fb85327552ae0ed44_720w.jpg?source=d16d100b)

FindB函数是从文本字符串中查找特定的字节位置，区分大小写

语法：=findb(要查找的字节、被查找的字节、[开始位置])

一个汉字算1个字符，2个字节；数字和英文字母算1个字符，1个字节

案例：

查找天在文本中的位置，查找C在文本中的位置，findb区分大小写，所以最后一个会错误

![](https://picx.zhimg.com/v2-dc48084e6d87f227f9a404bc9dbba7a9_720w.jpg?source=d16d100b)

**4.SEARCH与SEARCHB函数**

SEARCH函数是从文本字符串中查找特定的字符位置，不区分大小写，可以使用通配符进行查找

语法：=search (要查找的字符串、被查找的字符串、[开始位置])

![](https://pica.zhimg.com/v2-e4fa4b9d5dd30e598a6676fff9c39e30_720w.jpg?source=d16d100b)

SEARCHB是从文本字符串中查找特定的字节位置，不区分大小写，可以使用通配符进行查找

语法：=searchb(要查找的字节、被查找的字节、[开始位置])

![](https://picx.zhimg.com/v2-cbd1cb20ea1c9b3f33600bb891bc0e3f_720w.jpg?source=d16d100b)

**5. SUBTOTAL函数**

以一抵十的Subtotal函数，在计算隐藏数据时，有着无法替代的作用。

语法：=SUBTOTAL(选择函数类型,ref1,[ref2],...)

选择函数类型：1到11（计算隐藏值），101到111（不计算隐藏值）

![](https://picx.zhimg.com/v2-3359beb734bec1155803e1c68d0ca826_720w.jpg?source=d16d100b)

![](https://picx.zhimg.com/v2-aed674169843f9149bb9891572a45bf9_720w.jpg?source=d16d100b)

案例1

无隐藏数据时求和，sum函数和subtotal函数功能一样，公式：=SUBTOTAL(9,E1:E5)。公式中第一个参数是9，因为1到11（计算隐藏值）

![](https://pic1.zhimg.com/v2-7622913735e21d447243d64709444b02_720w.jpg?source=d16d100b)

当隐藏2、3、4行时，subtotal就只计算显示的行数据，公式：=SUBTOTAL(109,E1:E5)。

公式中第一个参数是109，因为101到111（不计算隐藏值）

![](https://picx.zhimg.com/v2-842aa8c22558c0d9b2f791114386ab48_720w.jpg?source=d16d100b)

案例2

![](https://picx.zhimg.com/v2-bd10955146f7600b6826502c98ad2ffa_720w.jpg?source=d16d100b)

案例3

让你的表格生成永远连续的序号，用这个公式生成的序号，无论是删除行还是筛选行序号都会连续。

![](https://picx.zhimg.com/v2-b6a360ad416acbe416ba9546edea16c7_720w.jpg?source=d16d100b)

# **第十三章：超级表**

1. **认识超级表**

超级表与普通表格相比，可以帮助我们更好的分析数据、美化表格。通过超级表可以更方便的对数据进行筛选、排序、设置格式、套用表格样式等功能。

![](https://pic4.zhimg.com/v2-ffaf8bb76876a01209a28ada384a43a3_1440w.jpg)

**2.创建超级表**

点击插入—选择表格—创建超级表（快捷键ctrl+T）

![](https://pic4.zhimg.com/v2-010e827880dd25e12eb5b4dfa660e39d_1440w.jpg)

点击开始—套用表格样式，也可以快速创建超级表

![](https://pic2.zhimg.com/v2-ddee0da2d8923a62b01105b73cfe75e3_1440w.jpg)

恢复普通表

表设计—转换为区域

![](https://pic1.zhimg.com/v2-7e6fff757f499d47a3aaf29cc58ef136_1440w.jpg)

**3.超级表的用法**

数据分析

表设计—汇总行

![](https://picx.zhimg.com/v2-fd04ba2a2a6083e3e5ad51aace50a043_1440w.jpg)

删除重复值

表设计—删除重复值—选择需要删除重复值的列

![](https://pic1.zhimg.com/v2-f3db23e6eb8dc65649dfd4665e55bce6_1440w.jpg)

插入切片器快速筛选

表设计—插入切片器—选择筛选项—点击确定

![](https://pic4.zhimg.com/v2-97fb41d4647a32137f3caa5419680a45_1440w.jpg)

![](https://pic4.zhimg.com/v2-891c25ef30503959159d66ae7cd10281_1440w.jpg)

![动图封面](https://pic3.zhimg.com/v2-70e16087805a120b38b1c8e6904b436e_b.jpg)

如果想删除切片器，选中之后单击鼠标右键进行删除

![](https://pica.zhimg.com/v2-ab0b521d9e391630f672b5f89f12fb1e_1440w.jpg)

增加数据自动关联样式

![动图封面](https://pic1.zhimg.com/v2-665288a946ff0e289880b9c330aa4a1e_b.jpg)
# **第十四章：图表的使用**

1. **簇状柱形图**

类别顺序不重要，主要进行类别的比较，可以选择簇状柱形图

选中数据—点击插入—二维柱形图—选择簇状柱形图

![](https://pic1.zhimg.com/v2-4c85fbf21410c0bb7bda452019780eaa_1440w.jpg)

进入到图表界面后，可以选择图表样式，可以更改图表的布局。

图表名选中之后可以修改和删除，网格线和坐标轴都可以选中后删除。

![](https://pic4.zhimg.com/v2-b9d474cb86f8da75926a89cae0033a05_1440w.jpg)

图表的美化

双击图表或者选中图表后单击鼠标右键，选择设置图表区域格式

![](https://picx.zhimg.com/v2-9492f666715cd278bb1c80612a13bde3_1440w.jpg)

选择无填充—无边框

![](https://pica.zhimg.com/v2-aa529d2a3227c1e75244d7668fb022de_1440w.jpg)

选中条形图分别更改色彩（单击1次，系统会选中所有条形图，双击，会选中1个图形）

然后再双击选中的条形图或单击鼠标右键，选择设置数据点格式，进行色彩填充

![](https://pic4.zhimg.com/v2-e6a2d10920ef7f874455a7f20025bc8f_1440w.jpg)

![](https://picx.zhimg.com/v2-37a3dc5f32bd3b94222741ba5cd87c9b_1440w.jpg)

添加数据标签

![](https://pic3.zhimg.com/v2-bb37f399cdaebb1208ecc6116cda2e66_1440w.jpg)

通过图表的美化和排版，我们可以制作数据看板

![](https://pic3.zhimg.com/v2-54648a6a642ae725c95181147b8d8b60_1440w.jpg)

**2.堆积柱形图**

比较整体的各个部分，可以用堆积柱形图。

![](https://pic4.zhimg.com/v2-15a55406b037470ddc079264b11e2383_1440w.jpg)

美化后的堆积柱形图

![](https://pic3.zhimg.com/v2-e8f61a0b1e6fd7b6247954a971cb5b7a_1440w.jpg)

**3.折线图**

观察数据的走向和变化趋势可以用折线图。

![](https://pica.zhimg.com/v2-85a33a13d3433a856eca3ce07b66634c_1440w.jpg)

最高点和最低点的标记

鼠标选中最高点—添加数据标签（用于突出显示数据）

![](https://pic4.zhimg.com/v2-36dc4bdbc4f0cd4a221a44fe82c1342b_1440w.jpg)

**4.条形图**

类别之间的比较且类别名称比较长的时候可以用条形图。

![](https://pica.zhimg.com/v2-489a0bf6ee304d5108bcf50c21be0c2c_1440w.jpg)

调整一下布局

![](https://pic4.zhimg.com/v2-f0e82c3073f61ef52120b3aa3ae4d271_1440w.jpg)

进行配色

![](https://pic1.zhimg.com/v2-7b8ea01f835f3dd1b46e04e277b27bc4_1440w.jpg)

  
5.**组合图**

直观的看出季度销售额的走向，同时也能反应出线上和线下销售额的对比

![](https://pic4.zhimg.com/v2-e6522f5018a3b972ec62d5396e3c44df_1440w.jpg)

**6.迷你图**

迷你图是放入单个单元格中的小型图，每个迷你图代表所选内容中的一行数据。

插入—选择想要的迷你图

![](https://pic3.zhimg.com/v2-43fb9cf29df9ef43a9637eca0728a296_1440w.jpg)

选择数据（选择同类型的数据，只选月份，不要选合计）—选择放置迷你图的位置

![](https://pic2.zhimg.com/v2-853fdfa918d1699d854fff12e551ad37_1440w.jpg)

迷你图做好后，可以进行高点的标记，也可以更改颜色

![](https://pic3.zhimg.com/v2-2983b822bf590221b09c83b81be5e98e_1440w.jpg)

# **第十五章：数据透视表**

1. **认识数据透视表**

数据透视表是计算、汇总和分析数据的强大工具，可以从复杂的数据库中快速提取想要的信息。

![](https://picx.zhimg.com/v2-586746077395fcdd57eab4488510d332_720w.jpg?source=d16d100b)

**2 .数据透视表的创建**

在创建数据透视表之前需要对数据源进行规范，数据源不应有任何空行或空列，它必须只有一行标题，不能有合并单元格，不能有空白单元格。

第一步：Ctrl+T把数据源变成超级表，如果数据源有删减，数据透视表可以直接刷新进行数据更新。

![](https://pica.zhimg.com/v2-b6db112d74fcbba5b039edcf2ad272a1_720w.jpg?source=d16d100b)

插入—数据透视表—选择表区域—选择新工作表

![](https://picx.zhimg.com/v2-668e0d5c8879b91d06ed28f5d6dba86e_720w.jpg?source=d16d100b)

点击确定之后会生成一个新工作表

![](https://picx.zhimg.com/v2-de1a84daab314c55c9aeb7170d58c731_720w.jpg?source=d16d100b)

**3.数据透视表字段**

我们创建月度简历量透视表

我们把月份拖到行，总简历数拖到数值，这时候就会生成月度简历量透视表

![](https://pic1.zhimg.com/v2-5027eb22c044f703a3bf69d6d06d12dc_720w.jpg?source=d16d100b)

我们再创建渠道入职人数透视表

选中月度简历量透视表进行复制，然后粘贴在下方，取消勾选月份和总简历数

![](https://picx.zhimg.com/v2-abb63d121ca87e2c4fe8a0ade3c76f6c_720w.jpg?source=d16d100b)

把渠道拖到行，入职人数拖到值

![](https://picx.zhimg.com/v2-e22083b12a535d9addf437198821e449_720w.jpg?source=d16d100b)

**4 .数据透视表的删除**

如果想要删除数据透视表，直接选中数据透视表，按delete键

![动图封面](https://picx.zhimg.com/v2-2f700f8e71378039ebbf30f96c7c2dff_720w.jpg?source=d16d100b)

**5.数据透视的内容清除**

如果想要清空数据透视表内容，选中数据透视表之后，点击全部清除。这时候只是清除了内容，但是数据透视表还在。如果想要移动数据透视表，可以用复制粘贴的方式，也可以点击移动数据透视表进行移动。

![](https://pic1.zhimg.com/v2-431d531eb8fad0b15eb94bc650c95b89_720w.jpg?source=d16d100b)

**6.数据更新**

如果数据源有更新，我们选中其中一个数据透视表，单击鼠标右键，选择刷新，数据透视表数据就会同步更新。

![](https://picx.zhimg.com/v2-0735e978914b889cd8f8e635b2fd7f76_720w.jpg?source=d16d100b)

**7.字段的隐藏和显示**

字段列表按钮是控制数据透视表字段的显示和隐藏

![](https://picx.zhimg.com/v2-b71e597e7a6dfd664b9e605844194f87_720w.jpg?source=d16d100b)

**8.制作简单的数据看板**

选择数据透视表中任意单元格—点击插入—插入簇状柱形图

![](https://picx.zhimg.com/v2-796aea8bcd23a8d4fc839deb5db08ec0_720w.jpg?source=d16d100b)

图表的美化（十四章图表的使用有详细的讲解）

点击字段按钮可以进行字段的隐藏和显示

![](https://picx.zhimg.com/v2-193f9fcd5de11e3c114d552a97cdab5a_720w.jpg?source=d16d100b)

然后我们删除不需要的部分，背景和边框进行无填充，再对数据条进行配色（十四章图表的使用有详细的讲解）

![](https://pic1.zhimg.com/v2-4708ca28ba65ded48551c1c6d78f9aac_720w.jpg?source=d16d100b)

制作多个数据透视表和图表

![](https://picx.zhimg.com/v2-47fd46db2d3658d9423454440af93a36_720w.jpg?source=d16d100b)

最后把所有图表复制粘贴到一张新工作表，进行颜色填充和排版，生成一张简单的数据看板。

![](https://picx.zhimg.com/v2-54648a6a642ae725c95181147b8d8b60_720w.jpg?source=d16d100b)

[知乎视频7.5 万播放 · 35 赞同视频![点击可播放视频](https://pic3.zhimg.com/v2-cf450c4ef54dfe09814889c76c928638_r.jpg?source=2231c908)​](https://www.zhihu.com/zvideo/1451974180039847936)

**9 切片器与报表链接**

插入切片器进行数据筛选

![](https://picx.zhimg.com/v2-9878ac98d817ba0f432bb12b15ad44c0_720w.jpg?source=d16d100b)

报表链接，关联数据透视表和图表，这样切片器就可以控制所有数据透视表，实现动态数据的展现。

选中切片器—点击切片器选项卡—报表链接—勾选要关联的数据透视表—点击确定

![](https://pic1.zhimg.com/v2-5d08d1875db2a691189237b8eed5af66_720w.jpg?source=d16d100b)

---

# **第十六章：打印和保护**

1. **保护工作表**

选中表格—点击审阅—点击保护工作表—输入密码

![](https://picx.zhimg.com/v2-99c6511d75184a25fd1a703bbe7b4cc6_720w.jpg?source=d16d100b)

**2.保护工作簿**

选择文件—另存为—点击工具—常规选项—设置密码选择文件—另存为—点击工具—常规选项—设置密码

![](https://picx.zhimg.com/v2-ba60567f193e58200b2945c60fc97dd4_720w.jpg?source=d16d100b)

**3.打印设置**

选择视图—页面布局—调整页面布局

![](https://picx.zhimg.com/v2-2d33d46967d6c3966fa389693bdcaf14_720w.jpg?source=d16d100b)

选择分页预览—拖动下方的蓝线—改变分页的位置

![](https://picx.zhimg.com/v2-baedcdcb098dfa20f5302fb754840819_720w.jpg?source=d16d100b)

缩放大小查看是否调整到合适的布局

![](https://pic1.zhimg.com/v2-9a35dd56b3e7c6bd88ef1bf1990c1e6c_720w.jpg?source=d16d100b)

点击文件——打印——打印设置（页数、单双面、页边距）——打印预览

![](https://picx.zhimg.com/v2-03dda9a3fb507391bee717b41f81134a_720w.jpg?source=d16d100b)

点击页面设置——居中方式

![](https://picx.zhimg.com/v2-fe5531944b15a6518c611e0ad813fb71_720w.jpg?source=d16d100b)

如果每页都要打印标题，则选择页面布局—打印标题—工作表—选择标题行—查看打印预览

![](https://picx.zhimg.com/v2-b0956728a3772410e5447b9361d2a44f_720w.jpg?source=d16d100b)

[知乎视频5779 播放 · 5 赞同视频![点击可播放视频](https://pic2.zhimg.com/v2-6a3bbf8c87e68eca57b03d149e5368c4_r.jpg?source=2231c908)​](https://www.zhihu.com/zvideo/1448345861437218816)

**4.页眉和页脚的设置**

[知乎视频2080 播放 · 0 赞同视频![点击可播放视频](https://pic3.zhimg.com/v2-416856cbeac5c638512335a87b02b86c_r.jpg?source=2231c908)](https://www.zhihu.com/zvideo/1449803902892281856)