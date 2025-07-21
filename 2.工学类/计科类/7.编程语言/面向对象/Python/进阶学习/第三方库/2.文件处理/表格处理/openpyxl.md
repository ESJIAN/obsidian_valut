---
tags:
  - Python
  - Lib
  - template
---

[官方手册](https://openpyxl-chinese-docs.readthedocs.io/zh-cn/latest/tutorial.html)
[教程地址](https://geek-docs.com/python/python-tutorial/python-openpyxl.html)

# 简介

`openpyxl` 是一个 Python 库，专门用于读写 Excel 2010 xlsx/xlsm文件。它提供了一组丰富的API来处理Excel文件，包括创建工作簿、工作表、读取和修改单元格数据，以及设置单元格样式等。

以下是 `openpyxl` 的一些主要特性：

1. **读写支持**：可以创建新的Excel文件，也可以打开和修改现有的xlsx文件。
    
2. **工作表操作**：可以添加、删除、复制、移动工作表，以及重命名工作表。
    
3. **单元格数据**：可以读取和写入单元格的数据，包括文本、数字、日期和时间等。
    
4. **样式和格式**：支持设置单元格的字体、颜色、边框、对齐方式等样式属性。
    
5. **图表和图形**：可以在工作表中创建和编辑图表。
    
6. **公式和函数**：支持在单元格中使用Excel公式和函数。
    
7. **数据筛选和排序**：可以对工作表中的数据进行筛选和排序。
    
8. **图像和多媒体**：可以在工作表中插入图像和其他多媒体文件。
    
9. **模板**：支持将工作簿保存为模板，并在之后创建工作簿时使用这些模板。
    
10. **安全性**：可以对工作簿进行加密和解密。
    
11. **事件和宏**：虽然 `openpyxl` 不支持宏的执行，但它可以保存包含宏的工作簿。


# 安装&卸载

在本教程中，我们使用 xlsx 文件。 xlsx 是 Microsoft Excel 使用的开放 XML 电子表格文件格式的文件扩展名。 xlsm 文件支持宏。 xlsx 是专有的二进制格式，而 xlsx 是基于 Office Open XML 格式的。

```python
$ sudo pip3 install openpyxl
```


我们使用`pip3`工具安装`openpyxl`。

---

# 方法介绍

`openpyxl` 库中主要涉及以下几个对象：

1.  **Workbook（工作簿）**：
    *   是 Excel 文件的最顶层容器，代表整个 Excel 文件。
    *   通过 `openpyxl.Workbook()` 创建新的工作簿。
    *   通过 `openpyxl.load_workbook('filename.xlsx')` 加载现有的 Excel 文件。
2.  **Worksheet（工作表）**：
    *   是工作簿中的一个表格，用于组织和存储数据。
    *   通过 `book.active` 获取当前活动的工作表。
    *   通过 `book.get_sheet_by_name("SheetName")` 获取指定名称的工作表。
    *   通过 `book.create_sheet("SheetName")` 创建新的工作表。
3.  **Cell（单元格）**：
    *   是工作表中的一个矩形区域，用于存储单个数据值。
    *   通过 `sheet['A1']` 或 `sheet.cell(row=1, column=1)` 访问单元格。
    *   可以读取和写入单元格的值，例如 `cell.value = 10`。
4.  **Row（行）和 Column（列）**：
    *   虽然 `openpyxl` 没有显式的 Row 和 Column 对象，但可以通过迭代工作表来按行或按列访问单元格。
    *   `sheet.rows` 和 `sheet.columns` 属性可以用于按行或按列迭代单元格。
5.  **Chart（图表）**：
    *   用于在工作表中创建各种类型的图表，如条形图、折线图等。
    *   通过 `openpyxl.chart` 模块中的类来创建和配置图表。
6.  **Image（图像）**：
    *   用于在工作表中插入图像。
    *   通过 `openpyxl.drawing.image.Image` 类来创建图像对象，并使用 `sheet.add_image()` 方法将其添加到工作表中。
7.  **Style（样式）**：
    *   用于设置单元格的字体、颜色、对齐方式等样式属性。
    *   通过 `openpyxl.styles` 模块中的类来创建和应用样式。
8.  **Alignment（对齐）**：
    *   用于设置单元格内容的对齐方式，如水平居中、垂直居中等。
    *   通过 `openpyxl.styles.Alignment` 类来创建对齐方式对象，并将其应用于单元格。
9.  **Font（字体）**：
    *   用于设置单元格文本的字体、大小、颜色等属性。
    *   通过 `openpyxl.styles.Font` 类来创建字体对象，并将其应用于单元格。

这些对象共同构成了 `openpyxl` 库的核心，用于处理 Excel 文件的各种操作。

## workbook 对象

`Workbook` 对象是 `openpyxl` 库中最重要的对象之一，它代表一个 Excel 文件。你可以把它看作是 Excel 文件的容器，所有的工作表（Worksheet）、单元格（Cell）、样式（Style）等都包含在其中。

**创建 Workbook 对象**

*   **创建新的工作簿：**

    ```python
    from openpyxl import Workbook

    workbook = Workbook()  # 创建一个新的工作簿对象
    ```
*   **加载现有的工作簿：**

    ```python
    from openpyxl import load_workbook

    workbook = load_workbook('example.xlsx')  # 加载名为 example.xlsx 的 Excel 文件
    ```

**Workbook 对象的常用方法**

1.  **`create_sheet(title=None, index=None)`**

    *   **作用：** 创建一个新的工作表（Worksheet）并将其添加到工作簿中。
    *   **参数：**
        *   `title` (str, 可选)：新工作表的名称。如果省略，则自动生成一个名称（如 "Sheet1", "Sheet2"）。
        *   `index` (int, 可选)：新工作表在工作簿中的位置索引（从 0 开始）。如果省略，则添加到工作簿的末尾。
    *   **返回值：** 新创建的 Worksheet 对象。
    *   **示例：**

    ```python
    # 创建一个名为 "Report" 的新工作表，并将其添加到工作簿的末尾
    worksheet1 = workbook.create_sheet("Report")

    # 创建一个名为 "Summary" 的新工作表，并将其插入到工作簿的第一个位置
    worksheet2 = workbook.create_sheet("Summary", 0)
    ```

2.  **`remove(worksheet)`**

    *   **作用：** 从工作簿中移除指定的工作表。
    *   **参数：**
        *   `worksheet` (Worksheet)：要移除的 Worksheet 对象。
    *   **示例：**

    ```python
    # 获取名为 "Report" 的工作表
    worksheet = workbook["Report"]

    # 移除该工作表
    workbook.remove(worksheet)
    ```

3.  **`copy_worksheet(worksheet)`**

    *   **作用：** 复制工作簿中的指定工作表。
    *   **参数：**
        *   `worksheet` (Worksheet)：要复制的 Worksheet 对象。
    *   **返回值** 新复制的 Worksheet 对象。
    *   **示例：**

    ```python
    # 获取名为 "Report" 的工作表
    worksheet = workbook["Report"]

    # 复制该工作表
    workbook.copy_worksheet(worksheet)
    ```

4.  **`sheetnames`**

    *   **作用：** 获取工作簿中所有工作表的名称列表。
    *   **返回值：** 包含所有工作表名称的列表（list）。
    *   **示例：**

    ```python
    # 获取工作簿中所有工作表的名称
    sheet_names = workbook.sheetnames
    print(sheet_names)  # 输出：['Sheet', 'Report', 'Summary']
    ```

5.  **`active`**

    *   **作用：** 获取当前活动的工作表。
    *   **返回值：** 当前活动的 Worksheet 对象。
    *   **示例：**

    ```python
    # 获取当前活动的工作表
    active_worksheet = workbook.active
    print(active_worksheet.title)  # 输出：Sheet
    ```

6.  **`save(filename)`**

    *   **作用：** 将工作簿保存到指定的 Excel 文件。
    *   **参数：**
        *   `filename` (str)：要保存的文件名（包括路径）。
    *   **示例：**

    ```python
    # 将工作簿保存到名为 "output.xlsx" 的文件
    workbook.save('output.xlsx')
    ```

7.  **`close()`**

    *   **作用：** 关闭工作簿，释放资源。
    *   **说明：** 在处理完 Excel 文件后，建议调用 `close()` 方法来释放资源，尤其是在处理大型文件时。
    *   **示例：**

    ```python
    # 关闭工作簿
    workbook.close()
    ```

8.  **`index(worksheet)`**

    *   **作用：** 获取指定工作表在工作簿中的索引位置。
    *   **参数：**
        *   `worksheet` (Worksheet)：要查询索引的 Worksheet 对象。
    *   **返回值：** 工作表的索引位置（从 0 开始）。
    *   **示例：**

    ```python
    # 获取名为 "Report" 的工作表的索引位置
    worksheet = workbook["Report"]
    index = workbook.index(worksheet)
    print(index)  # 输出：1
    ```

9. **`get_sheet_by_name(name)`**

    *   **作用：** 通过名称获取工作表
    *   **参数：**
        *   `name` (str)：要查询的工作表名称。
    *   **返回值：** 工作表的索引位置（从 0 开始）。
    *   **示例：**

    ```python
    # 获取名为 "Report" 的工作表的索引位置
    sheet = workbook.get_sheet_by_name("January")
    ```

## worksheet 对象

`Worksheet` 对象代表 Excel 文件中的一个工作表。它是数据的载体，你可以在工作表中读取、写入、修改单元格数据，设置单元格样式，添加图表和图像等。

**获取 Worksheet 对象**

*   **通过 Workbook 的 `active` 属性获取活动工作表：**

    ```python
    from openpyxl import Workbook

    workbook = Workbook()
    worksheet = workbook.active  # 获取当前活动的工作表
    ```

*   **通过工作表名称获取工作表：**

    ```python
    from openpyxl import load_workbook

    workbook = load_workbook('example.xlsx')
    worksheet = workbook['Sheet1']  # 获取名为 "Sheet1" 的工作表
    ```

>**注意**：若 `Sheet1` 工作表不存在，则会引发 `KeyError` 异常，需要引入异常处理逻辑。

*   **通过 `create_sheet()` 方法创建新的工作表：**

    ```python
    worksheet = workbook.create_sheet('NewSheet')  # 创建名为 "NewSheet" 的工作表
    ```

**Worksheet 对象的常用方法**

1.  **`title`**

    *   **作用：** 获取或设置工作表的名称。
    *   **示例：**

    ```python
    # 获取工作表的名称
    sheet_name = worksheet.title
    print(sheet_name)  # 输出：Sheet1

    # 设置工作表的名称
    worksheet.title = 'DataSheet'
    ```

2.  **`cell(row, column, value=None)`**

    *   **作用：** 获取指定行和列的单元格对象，也可以设置单元格的值。
    *   **参数：**
        *   `row` (int)：单元格的行号（从 1 开始）。
        *   `column` (int)：单元格的列号（从 1 开始）。
        *   `value` (any, 可选)：要设置的单元格的值。如果省略，则只获取单元格对象。
    *   **返回值：** Cell 对象。
    *   **示例：**

    ```python
    # 获取第 1 行第 1 列的单元格对象
    cell = worksheet.cell(row=1, column=1)

    # 设置第 2 行第 3 列的单元格的值为 "Hello"
    worksheet.cell(row=2, column=3, value='Hello')
    ```

3.  **`[]` (单元格访问)**

    *   **作用：** 通过单元格坐标（如 "A1", "B2"）访问单元格对象。
    *   **示例：**

    ```python
    # 获取 A1 单元格对象
    cell = worksheet['A1']

    # 设置 B2 单元格的值为 100
    worksheet['B2'] = 100
    ```

4.  **`append(iterable)`**

    *   **作用：** 将一行数据（列表或元组）添加到工作表的末尾。
    *   **参数：**
        *   `iterable` (list 或 tuple)：包含单元格值的可迭代对象。
    *   **示例：**

    ```python
    # 添加一行数据
    worksheet.append(['Name', 'Age', 'City'])
    worksheet.append(['Alice', 30, 'New York'])
    worksheet.append(['Bob', 25, 'London'])
    ```

5.  **`iter_rows(min_row=None, max_row=None, min_col=None, max_col=None, values_only=False)`**

    *   **作用：** 迭代工作表中的行。
    *   **参数：**
        *   `min_row` (int, 可选)：起始行号（从 1 开始）。
        *   `max_row` (int, 可选)：结束行号。
        *   `min_col` (int, 可选)：起始列号（从 1 开始）。
        *   `max_col` (int, 可选)：结束列号。
        *   `values_only` (bool, 可选)：如果为 True，则只返回单元格的值，否则返回 Cell 对象。
    *   **返回值：** 一个生成器，每次产生一行 Cell 对象或值的元组。
    *   **示例：**

    ```python
    # 迭代工作表中的所有行，并打印每个单元格的值
    for row in worksheet.iter_rows():
        for cell in row:
            print(cell.value)

    # 迭代第 2 行到第 4 行，第 1 列到第 3 列的单元格，只获取单元格的值
    for row in worksheet.iter_rows(min_row=2, max_row=4, min_col=1, max_col=3, values_only=True):
        print(row)  # 输出：('Alice', 30, 'New York')
    ```

6.  **`iter_cols(min_row=None, max_row=None, min_col=None, max_col=None, values_only=False)`**

    *   **作用：** 迭代工作表中的列。
    *   **参数：**
        *   与 `iter_rows()` 方法类似。
    *   **返回值：** 一个生成器，每次产生一列 Cell 对象或值的元组。
    *   **示例：**

    ```python
    # 迭代工作表中的所有列，并打印每个单元格的值
    for col in worksheet.iter_cols():
        for cell in col:
            print(cell.value)
    ```

7.  **`max_row` 和 `max_column`**

    *   **作用：** 获取工作表中包含数据的最大行号和最大列号。
    *   **示例：**

    ```python
    # 获取工作表中包含数据的最大行号
    max_row = worksheet.max_row
    print(max_row)

    # 获取工作表中包含数据的最大列号
    max_column = worksheet.max_column
    print(max_column)
    ```

8.  **`merge_cells(range_string)`**

    *   **作用：** 合并指定范围内的单元格。
    *   **参数：**
        *   `range_string` (str)：要合并的单元格范围，如 "A1:B2"。
    *   **示例：**

    ```python
    # 合并 A1 到 B2 单元格
    worksheet.merge_cells('A1:B2')
    ```

9.  **`unmerge_cells(range_string)`**

    *   **作用：** 取消合并指定范围内的单元格。
    *   **参数：**
        *   `range_string` (str)：要取消合并的单元格范围，如 "A1:B2"。
    *   **示例：**

    ```python
    # 取消合并 A1 到 B2 单元格
    worksheet.unmerge_cells('A1:B2')
    ```

10. **`insert_rows(idx, amount=1)`**

    *   **作用：** 在指定行号之前插入一行或多行。
    *   **参数：**
        *   `idx` (int)：要插入行的行号（从 1 开始）。
        *   `amount` (int, 可选)：要插入的行数，默认为 1。
    *   **示例：**

    ```python
    # 在第 2 行之前插入一行
    worksheet.insert_rows(2)

    # 在第 5 行之前插入 3 行
    worksheet.insert_rows(5, 3)
    ```

11. **`insert_cols(idx, amount=1)`**

    *   **作用：** 在指定列号之前插入一列或多列。
    *   **参数：**
        *   `idx` (int)：要插入列的列号（从 1 开始）。
        *   `amount` (int, 可选)：要插入的列数，默认为 1。
    *   **示例：**

    ```python
    # 在第 2 列之前插入一列
    worksheet.insert_cols(2)

    # 在第 5 列之前插入 2 列
    worksheet.insert_cols(5, 2)
    ```

12. **`delete_rows(idx, amount=1)`**

    *   **作用：** 删除指定行号开始的一行或多行。
    *   **参数：**
        *   `idx` (int)：要删除行的起始行号（从 1 开始）。
        *   `amount` (int, 可选)：要删除的行数，默认为 1。
    *   **示例：**

    ```python
    # 删除第 3 行
    worksheet.delete_rows(3)

    # 删除从第 5 行开始的 2 行
    worksheet.delete_rows(5, 2)
    ```

13. **`delete_cols(idx, amount=1)`**

    *   **作用：** 删除指定列号开始的一列或多列。
    *   **参数：**
        *   `idx` (int)：要删除列的起始列号（从 1 开始）。
        *   `amount` (int, 可选)：要删除的列数，默认为 1。
    *   **示例：**

    ```python
    # 删除第 4 列
    worksheet.delete_cols(4)

    # 删除从第 2 列开始的 3 列
    worksheet.delete_cols(2, 3)
    ```

14. **`freeze_panes`**

    *   **作用：** 冻结窗格，使指定的行和列在滚动时保持可见。
    *   **示例：**

    ```python
    # 冻结 A2 单元格上方的行和左侧的列
    worksheet.freeze_panes = 'B2'
    ```

15. **`add_chart(chart, anchor)`**

    *   **作用：** 在工作表中添加图表。
    *   **参数：**
        *   `chart` (Chart 对象)：要添加的图表对象。
        *   `anchor` (str)：图表在工作表中的位置，如 "E10"。
    *   **示例：**

    ```python
    from openpyxl.chart import BarChart, Reference

    # 创建一个条形图
    chart = BarChart()
    data = Reference(worksheet, min_col=2, min_row=1, max_col=2, max_row=7)
    categories = Reference(worksheet, min_col=1, min_row=1, max_row=7)
    chart.add_data(data, titles_from_data=True)
    chart.set_categories(categories)

    # 将图表添加到工作表中
    worksheet.add_chart(chart, "E10")
    ```

16. **`add_image(img, anchor)`**

    *   **作用：** 在工作表中添加图像。
    *   **参数：**
        *   `img` (Image 对象)：要添加的图像对象。
        *   `anchor` (str)：图像在工作表中的位置，如 "A1"。
    *   **示例：**

    ```python
    from openpyxl.drawing.image import Image

    # 创建一个图像对象
    img = Image('image.png')

    # 将图像添加到工作表中
    worksheet.add_image(img, 'A1')
    ```

## cell 对象

`Cell` 对象代表 Excel 工作表中的一个单元格。它是存储数据的基本单位，你可以读取或修改单元格的值，设置单元格的样式，添加公式等。

**获取 Cell 对象**

*   **通过 Worksheet 的 `cell()` 方法获取：**

    ```python
    from openpyxl import Workbook

    workbook = Workbook()
    worksheet = workbook.active
    cell = worksheet.cell(row=1, column=1)  # 获取第 1 行第 1 列的单元格
    ```

*   **通过 Worksheet 的 `[]` 访问方式获取：**

    ```python
    cell = worksheet['A1']  # 获取 A1 单元格
    ```

**Cell 对象的常用属性和方法**

1.  **`value`**

    *   **作用：** 获取或设置单元格的值。
    *   **类型：** 可以是字符串、数字、日期、布尔值等。
    *   **示例：**

    ```python
    # 获取单元格的值
    cell_value = cell.value
    print(cell_value)

    # 设置单元格的值
    cell.value = 'Hello'
    cell.value = 123
    cell.value = True
    ```

2.  **`row`**

    *   **作用：** 获取单元格所在的行号（从 1 开始）。
    *   **类型：** int
    *   **示例：**

    ```python
    row_number = cell.row
    print(row_number)  # 输出：1
    ```

3.  **`column`**

    *   **作用：** 获取单元格所在的列号（从 1 开始）。
    *   **类型：** int
    *   **示例：**

    ```python
    column_number = cell.column
    print(column_number)  # 输出：1
    ```

4.  **`column_letter`**

    *   **作用：** 获取单元格所在的列的字母表示（如 "A", "B", "C"）。
    *   **类型：** str
    *   **示例：**

    ```python
    column_letter = cell.column_letter
    print(column_letter)  # 输出：A
    ```

5.  **`coordinate`**

    *   **作用：** 获取单元格的坐标（如 "A1", "B2"）。
    *   **类型：** str
    *   **示例：**

    ```python
    coordinate = cell.coordinate
    print(coordinate)  # 输出：A1
    ```

6.  **`has_style`**

    *   **作用：** 检查单元格是否应用了样式。
    *   **类型：** bool
    *   **示例：**

    ```python
    has_style = cell.has_style
    print(has_style)
    ```

7.  **`font`**

    *   **作用：** 获取或设置单元格的字体样式。
    *   **类型：** `openpyxl.styles.Font` 对象
    *   **示例：**

    ```python
    from openpyxl.styles import Font

    # 获取单元格的字体样式
    font = cell.font

    # 设置单元格的字体样式
    cell.font = Font(name='Arial', size=12, bold=True)
    ```

8.  **`fill`**

    *   **作用：** 获取或设置单元格的填充样式（背景色）。
    *   **类型：** `openpyxl.styles.PatternFill` 对象
    *   **示例：**

    ```python
    from openpyxl.styles import PatternFill

    # 获取单元格的填充样式
    fill = cell.fill

    # 设置单元格的填充样式
    cell.fill = PatternFill(fill_type='solid', fgColor='FFFF0000')  # 红色
    ```

9.  **`border`**

    *   **作用：** 获取或设置单元格的边框样式。
    *   **类型：** `openpyxl.styles.Border` 对象
    *   **示例：**

    ```python
    from openpyxl.styles import Border, Side

    # 获取单元格的边框样式
    border = cell.border

    # 设置单元格的边框样式
    side = Side(border_style='thin', color='FF000000')  # 黑色细边框
    cell.border = Border(top=side, bottom=side, left=side, right=side)
    ```

10. **`alignment`**

    *   **作用：** 获取或设置单元格的对齐方式。
    *   **类型：** `openpyxl.styles.Alignment` 对象
    *   **示例：**

    ```python
    from openpyxl.styles import Alignment

    # 获取单元格的对齐方式
    alignment = cell.alignment

    # 设置单元格的对齐方式
    cell.alignment = Alignment(horizontal='center', vertical='center')  # 水平垂直居中
    ```

11. **`number_format`**

    *   **作用：** 获取或设置单元格的数字格式。
    *   **类型：** str
    *   **示例：**

    ```python
    # 获取单元格的数字格式
    number_format = cell.number_format

    # 设置单元格的数字格式
    cell.number_format = '#,##0.00'  # 千分位分隔，保留两位小数
    cell.number_format = 'YYYY-MM-DD'  # 日期格式
    ```

12. **`protection`**

    *   **作用：** 获取或设置单元格的保护设置（锁定、隐藏公式等）。
    *   **类型：** `openpyxl.styles.Protection` 对象
    *   **示例：**

    ```python
    from openpyxl.styles import Protection

    # 获取单元格的保护设置
    protection = cell.protection

    # 设置单元格的保护设置
    cell.protection = Protection(locked=True, hidden=False)  # 锁定单元格，不隐藏公式
    ```

13. **`comment`**

    *   **作用：** 获取或设置单元格的批注。
    *   **类型：** `openpyxl.comments.Comment` 对象
    *   **示例：**

    ```python
    from openpyxl.comments import Comment

    # 获取单元格的批注
    comment = cell.comment

    # 设置单元格的批注
    cell.comment = Comment('This is a comment', 'Author')
    ```

14. **`hyperlink`**

    *   **作用：** 获取或设置单元格的超链接。
    *   **类型：** str
    *   **示例：**

    ```python
    # 获取单元格的超链接
    hyperlink = cell.hyperlink

    # 设置单元格的超链接
    cell.hyperlink = 'https://www.example.com'
    cell.value = 'Example Website'  # 建议同时设置单元格的值为链接文本
    cell.style = 'Hyperlink'  # 设置单元格样式为超链接样式
    ```

15. **`internal_value`**

    *   **作用：** 获取单元格的内部值，即 Excel 存储的原始值。
    *   **类型：** 可以是字符串、数字、日期等。
    *   **说明：** 与 `value` 属性类似，但 `internal_value` 不会进行类型转换或格式化。
    *   **示例：**

    ```python
    internal_value = cell.internal_value
    print(internal_value)
    ```

# 基本操作
## Openpyxl 创建新文件

在第一个示例中，我们使用`openpyxl`创建一个新的 xlsx 文件。

`write_xlsx.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook
import time

book = Workbook()# 创建一个新的工作簿
sheet = book.active# 获取当前活跃的工作表，默认名为Sheet

sheet['A1'] = 56
sheet['A2'] = 43

now = time.strftime("%x")
sheet['A3'] = now

book.save("sample.xlsx")
```


在示例中，我们创建一个新的 xlsx 文件。 我们将数据写入三个单元格。

```python
from openpyxl import Workbook
```



从`openpyxl`模块，我们导入`Workbook`类。 工作簿是文档所有其他部分的容器。

```python
book = Workbook()
```



我们创建一个新的工作簿。 始终使用至少一个工作表创建一个工作簿。

```python
sheet = book.active
```



我们获得对活动工作表的引用。

```python
sheet['A1'] = 56
sheet['A2'] = 43
```


我们将数值数据写入单元格 A1 和 A2。

```python
now = time.strftime("%x")
sheet['A3'] = now
```


我们将当前日期写入单元格 A3。

```python
book.save("sample.xlsx")
```


我们使用`save()`方法将内容写入`sample.xlsx`文件。

![Python OpenPyXL 教程](https://img.geek-docs.com/python/46dc21c705f99657d756ea6ced587768.jpg "Python OpenPyXL 教程")

## Openpyxl 写入单元格

写入单元格有两种基本方法：使用工作表的键（例如 A1 或 D3），或通过`cell()`方法使用行和列表示法。

`write2cell.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook

book = Workbook()
sheet = book.active

sheet['A1'] = 1
sheet.cell(row=2, column=2).value = 2

book.save('write2cell.xlsx')
```

Python

  

在示例中，我们将两个值写入两个单元格。

```python
sheet['A1'] = 1
```

Python

  

在这里，我们将数值分配给 A1 单元。

```python
sheet.cell(row=2, column=2).value = 2
```

Python

  

在这一行中，我们用行和列表示法写入单元格 B2。

## Openpyxl 附加值

使用`append()`方法，我们可以在当前工作表的底部附加一组值。

`appending_values.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook

book = Workbook()
sheet = book.active

rows = (
    (88, 46, 57),
    (89, 38, 12),
    (23, 59, 78),
    (56, 21, 98),
    (24, 18, 43),
    (34, 15, 67)
)

for row in rows:
    sheet.append(row)

book.save('appending.xlsx')
```

Python

  

在示例中，我们将三列数据附加到当前工作表中。

```python
rows = (
    (88, 46, 57),
    (89, 38, 12),
    (23, 59, 78),
    (56, 21, 98),
    (24, 18, 43),
    (34, 15, 67)
)
```

数据存储在元组的元组中。

```python
for row in rows:
    sheet.append(row)
```


我们逐行浏览容器，并使用`append()`方法插入数据行。

## OpenPyXL 读取单元格

在下面的示例中，我们从`sample.xlsx`文件中读取先前写入的数据。

`read_cells.py`

```python
#!/usr/bin/env python

import openpyxl

book = openpyxl.load_workbook('sample.xlsx')

sheet = book.active

a1 = sheet['A1']
a2 = sheet['A2']
a3 = sheet.cell(row=3, column=1)

print(a1.value)
print(a2.value) 
print(a3.value)
```

Python

  

该示例加载一个现有的 xlsx 文件并读取三个单元格。

```python
book = openpyxl.load_workbook('sample.xlsx')
```

Python

  

使用`load_workbook()`方法打开文件。

```python
a1 = sheet['A1']
a2 = sheet['A2']
a3 = sheet.cell(row=3, column=1)
```

Python

  

我们读取 A1，A2 和 A3 单元的内容。 在第三行中，我们使用`cell()`方法获取 A3 单元格的值。

```python
$ ./read_cells.py 
56
43
10/26/16
```

Python

  

这是示例的输出。

## OpenPyXL 读取多个单元格

我们有以下数据表：

![Python OpenPyXL 教程](https://img.geek-docs.com/python/0a37bb76ecebbbab395c2cfdf903d43d.jpg "Python OpenPyXL 教程")

我们使用范围运算符读取数据。

`read_cells2.py`

```python
#!/usr/bin/env python

import openpyxl

book = openpyxl.load_workbook('items.xlsx')

sheet = book.active

cells = sheet['A1': 'B6']

for c1, c2 in cells:
    print("{0:8} {1:8}".format(c1.value, c2.value))
```

Python

  

在示例中，我们使用范围运算从两列读取数据。

```python
cells = sheet['A1': 'B6']
```

Python

  

在这一行中，我们从单元格 A1-B6 中读取数据。

```python
for c1, c2 in cells:
    print("{0:8} {1:8}".format(c1.value, c2.value))
```

Python

  

`format()`功能用于在控制台上整洁地输出数据。

```python
$ ./read_cells2.py 
Items    Quantity
coins          23
chairs          3
pencils         5
bottles         8
books          30
```

Python

  

## Openpyxl 按行迭代

`iter_rows()`方法将工作表中的单元格返回为行。

`iterating_by_rows.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook

book = Workbook()
sheet = book.active

rows = (
    (88, 46, 57),
    (89, 38, 12),
    (23, 59, 78),
    (56, 21, 98),
    (24, 18, 43),
    (34, 15, 67)
)

for row in rows:
    sheet.append(row)

for row in sheet.iter_rows(min_row=1, min_col=1, max_row=6, max_col=3):
    for cell in row:
        print(cell.value, end=" ")
    print()    

book.save('iterbyrows.xlsx')
```

Python

  

该示例逐行遍历数据。

```python
for row in sheet.iter_rows(min_row=1, min_col=1, max_row=6, max_col=3):
```

Python

  

我们提供了迭代的边界。

```python
$ ./iterating_by_rows.py 
88 46 57 
89 38 12 
23 59 78 
56 21 98 
24 18 43 
34 15 67 
```

Python

  

## Openpyxl 按列迭代

`iter_cols()`方法将工作表中的单元格作为列返回。

`iterating_by_columns.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook

book = Workbook()
sheet = book.active

rows = (
    (88, 46, 57),
    (89, 38, 12),
    (23, 59, 78),
    (56, 21, 98),
    (24, 18, 43),
    (34, 15, 67)
)

for row in rows:
    sheet.append(row)

for row in sheet.iter_cols(min_row=1, min_col=1, max_row=6, max_col=3):
    for cell in row:
        print(cell.value, end=" ")
    print()    

book.save('iterbycols.xlsx')
```

Python

  

该示例逐列遍历数据。

```python
$ ./iterating_by_columns.py 
88 89 23 56 24 34 
46 38 59 21 18 15 
57 12 78 98 43 67 
```


## Openpyxl 保存表格

```ad-note
title:**本节犯错**
根据您提供的笔记内容，`openpyxl` 专门用于读写 Excel 2010 `xlsx/xlsm` 文件，并不支持 `.xls` 格式。

笔记中 `openpyxl` 的缺点也提到了这一点：

- 不支持早期版本的 Excel 文件，如 `.xls` 格式。

因此，`openpyxl` 无法直接将表格保存为 `.xls` 格式。

如果您需要处理 `.xls` 格式的文件，您可能需要考虑使用 `xlrd`（用于读取 `.xls` 文件）和 `xlwt`（用于写入 `.xls` 文件）这两个库。但请注意，`xlrd` 从 1.2.0 版本开始不再支持 `.xlsx` 文件的读取。
```


**Openpyxl 保存表格**

1.  **创建或加载工作簿：**
    *   创建新工作簿：使用 `openpyxl.Workbook()` 创建一个新的工作簿对象。
    *   加载现有工作簿：使用 `openpyxl.load_workbook('filename.xlsx')` 加载一个现有的 Excel 文件。
2.  **获取工作表：**
    *   获取活动工作表：使用 `book.active` 获取当前活动的工作表。
    *   按名称获取工作表：使用 `book.get_sheet_by_name("SheetName")` 获取指定名称的工作表。
    *   创建新工作表：使用 `book.create_sheet("SheetName")` 创建一个新工作表。
3.  **写入单元格数据：**
    *   使用单元格坐标：使用 `sheet['A1'] = value` 的方式直接写入单元格。
    *   使用行和列索引：使用 `sheet.cell(row=2, column=2).value = value` 的方式写入单元格。
    *   附加行数据：使用 `sheet.append(row)` 方法将一行数据（元组或列表）附加到工作表的末尾。
4.  **设置单元格样式（可选）：**
    *   导入 `openpyxl.styles.Alignment` 等模块来设置单元格的对齐方式、字体、颜色等样式。
    *   示例：
        ```python
        from openpyxl.styles import Alignment
        cell = sheet.cell(row=1, column=1)
        cell.alignment = Alignment(horizontal='center', vertical='center')
        ```
5.  **合并单元格（可选）：**
    *   使用 `sheet.merge_cells('A1:B2')` 合并指定范围的单元格。
6.  **冻结窗格（可选）：**
    *   使用 `sheet.freeze_panes = 'B2'` 冻结指定单元格上方的行和左侧的列。
7.  **添加公式（可选）：**
    *   将 Excel 公式作为字符串写入单元格，例如 `cell.value = "=SUM(A1:B6)"`。
8.  **插入图像（可选）：**
    *   导入 `openpyxl.drawing.image.Image` 类。
    *   创建 `Image` 对象：`img = Image("image.png")`。
    *   使用 `sheet.add_image(img, 'B2')` 添加图像到指定单元格。
9.  **创建图表（可选）：**
    *   导入 `openpyxl.chart` 模块中的相关类（如 `Reference`、`Series`、`BarChart`）。
    *   创建数据引用：`data = Reference(sheet, min_col=2, min_row=1, max_col=2, max_row=6)`。
    *   创建类别引用：`categs = Reference(sheet, min_col=1, min_row=1, max_row=6)`。
    *   创建图表对象：`chart = BarChart()`。
    *   添加数据和类别：`chart.add_data(data=data)`、`chart.set_categories(categs)`。
    *   设置图表属性（如标题、图例等）。
    *   使用 `sheet.add_chart(chart, "A8")` 将图表添加到工作表。
10. **保存工作簿：**
    *   使用 `book.save('filename.xlsx')` 将工作簿保存到指定文件。

**示例代码：**

```python
from openpyxl import Workbook
from openpyxl.styles import Alignment

# 创建一个新的工作簿
book = Workbook()
sheet = book.active

# 写入数据
sheet['A1'] = 'Name'
sheet['B1'] = 'Age'
sheet['A2'] = 'Alice'
sheet['B2'] = 30
sheet['A3'] = 'Bob'
sheet['B3'] = 25

# 设置单元格对齐方式
sheet['A1'].alignment = Alignment(horizontal='center', vertical='center')
sheet['B1'].alignment = Alignment(horizontal='center', vertical='center')

# 合并单元格
sheet.merge_cells('C1:D1')
sheet['C1'] = 'Combined Data'
sheet['C1'].alignment = Alignment(horizontal='center', vertical='center')

# 保存工作簿
book.save('output.xlsx')
```

这段代码会创建一个名为 `output.xlsx` 的 Excel 文件，其中包含一个名为 "Sheet" 的工作表，并在其中写入一些数据和样式。

# 高级操作

对于下一个示例，我们需要创建一个包含数字的 xlsx 文件。 例如，我们使用`RANDBETWEEN()`函数在 10 列中创建了 25 行数字。

`mystats.py`

```python
#!/usr/bin/env python

import openpyxl
import statistics as stats

book = openpyxl.load_workbook('numbers.xlsx', data_only=True)

sheet = book.active

rows = sheet.rows

values = []

for row in rows:
    for cell in row:
        values.append(cell.value)

print("Number of values: {0}".format(len(values)))
print("Sum of values: {0}".format(sum(values)))
print("Minimum value: {0}".format(min(values)))
print("Maximum value: {0}".format(max(values)))
print("Mean: {0}".format(stats.mean(values)))
print("Median: {0}".format(stats.median(values)))
print("Standard deviation: {0}".format(stats.stdev(values)))
print("Variance: {0}".format(stats.variance(values)))
```

Python

  

在示例中，我们从工作表中读取所有值并计算一些基本统计信息。

```python
import statistics as stats
```

Python

  

导入`statistics`模块以提供一些统计功能，例如中值和方差。

```python
book = openpyxl.load_workbook('numbers.xlsx', data_only=True)
```

Python

  

使用`data_only`选项，我们从单元格而不是公式中获取值。

```python
rows = sheet.rows
```

Python

  

我们得到所有不为空的单元格行。

```python
for row in rows:
    for cell in row:
        values.append(cell.value)
```

Python

  

在两个 for 循环中，我们从单元格中形成一个整数值列表。

```python
print("Number of values: {0}".format(len(values)))
print("Sum of values: {0}".format(sum(values)))
print("Minimum value: {0}".format(min(values)))
print("Maximum value: {0}".format(max(values)))
print("Mean: {0}".format(stats.mean(values)))
print("Median: {0}".format(stats.median(values)))
print("Standard deviation: {0}".format(stats.stdev(values)))
print("Variance: {0}".format(stats.variance(values)))
```

Python

  

我们计算并打印有关值的数学统计信息。 一些功能是内置的，其他功能是通过`statistics`模块导入的。

```python
$ ./mystats.py 
Number of values: 312
Sum of values: 15877
Minimum value: 0
Maximum value: 100
Mean: 50.88782051282051
Median: 54.0
Standard deviation: 28.459203819700967
Variance: 809.9262820512821
```

Python

  

## Openpyxl 过滤器&排序数据

图纸具有`auto_filter`属性，该属性允许设置过滤条件和排序条件。

请注意，Openpyxl 设置了条件，但是我们必须在电子表格应用中应用它们。

`filter_sort.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook

wb = Workbook()
sheet = wb.active

data = [
    ['Item', 'Colour'],
    ['pen', 'brown'],
    ['book', 'black'],
    ['plate', 'white'],
    ['chair', 'brown'],
    ['coin', 'gold'],
    ['bed', 'brown'],
    ['notebook', 'white'],
]

for r in data:
    sheet.append(r)

sheet.auto_filter.ref = 'A1:B8'
sheet.auto_filter.add_filter_column(1, ['brown', 'white'])
sheet.auto_filter.add_sort_condition('B2:B8')

wb.save('filtered.xlsx')
```

Python

  

在示例中，我们创建一个包含项目及其颜色的工作表。 我们设置一个过滤器和一个排序条件。

## Openpyxl 维度

为了获得那些实际包含数据的单元格，我们可以使用维度。

`dimensions.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook

book = Workbook()
sheet = book.active

sheet['A3'] = 39
sheet['B3'] = 19

rows = [
    (88, 46),
    (89, 38),
    (23, 59),
    (56, 21),
    (24, 18),
    (34, 15)
]

for row in rows:
    sheet.append(row)

print(sheet.dimensions)
print("Minimum row: {0}".format(sheet.min_row))
print("Maximum row: {0}".format(sheet.max_row))
print("Minimum column: {0}".format(sheet.min_column))
print("Maximum column: {0}".format(sheet.max_column))

for c1, c2 in sheet[sheet.dimensions]:
    print(c1.value, c2.value)

book.save('dimensions.xlsx')
```

Python

  

该示例计算两列数据的维数。

```python
sheet['A3'] = 39
sheet['B3'] = 19

rows = [
    (88, 46),
    (89, 38),
    (23, 59),
    (56, 21),
    (24, 18),
    (34, 15)
]

for row in rows:
    sheet.append(row)
```

Python

  

我们将数据添加到工作表。 请注意，我们从第三行开始添加。

```python
print(sheet.dimensions)
```

Python

  

`dimensions`属性返回非空单元格区域的左上角和右下角单元格。

```python
print("Minimum row: {0}".format(sheet.min_row))
print("Maximum row: {0}".format(sheet.max_row))
```

Python

  

使用`min_row`和`max_row`属性，我们可以获得包含数据的最小和最大行。

```python
print("Minimum column: {0}".format(sheet.min_column))
print("Maximum column: {0}".format(sheet.max_column))
```

Python

  

通过`min_column`和`max_column`属性，我们获得了包含数据的最小和最大列。

```python
for c1, c2 in sheet[sheet.dimensions]:
    print(c1.value, c2.value)
```

Python

  

我们遍历数据并将其打印到控制台。

```python
$ ./dimensions.py 
A3:B9
Minimum row: 3
Maximum row: 9
Minimum column: 1
Maximum column: 2
39 19
88 46
89 38
23 59
56 21
24 18
34 15
```

Python

  

## 工作表

每个工作簿可以有多个工作表。

![Python OpenPyXL 教程](https://img.geek-docs.com/python/4bf58174c38e97e6f35cd58e9c9433d1.jpg "Python OpenPyXL 教程")

Figure: Sheets

让我们有一张包含这三张纸的工作簿。

`sheets.py`

```python
#!/usr/bin/env python

import openpyxl

book = openpyxl.load_workbook('sheets.xlsx')

print(book.get_sheet_names())

active_sheet = book.active
print(type(active_sheet))

sheet = book.get_sheet_by_name("March")
print(sheet.title)
```

Python

  

该程序可用于 Excel 工作表。

```python
print(book.get_sheet_names())
```

Python

  

`get_sheet_names()`方法返回工作簿中可用工作表的名称。

```python
active_sheet = book.active
print(type(active_sheet))
```

Python

  

我们获取活动表并将其类型打印到终端。

```python
sheet = book.get_sheet_by_name("March")
```

Python

  

我们使用`get_sheet_by_name()`方法获得对工作表的引用。

```python
print(sheet.title)
```

Python

  

检索到的工作表的标题将打印到终端。

```python
$ ./sheets.py 
['January', 'February', 'March']
<class 'openpyxl.worksheet.worksheet.Worksheet'>
March
```

Python

  

这是程序的输出。

`sheets2.py`

```python
#!/usr/bin/env python

import openpyxl

book = openpyxl.load_workbook('sheets.xlsx')

book.create_sheet("April")

print(book.sheetnames)

sheet1 = book.get_sheet_by_name("January")
book.remove_sheet(sheet1)

print(book.sheetnames)

book.create_sheet("January", 0)
print(book.sheetnames)

book.save('sheets2.xlsx')
```

Python

  

在此示例中，我们创建一个新工作表。

```python
book.create_sheet("April")
```

Python

  

使用`create_sheet()`方法创建一个新图纸。

```python
print(book.sheetnames)
```

Python

  

图纸名称也可以使用`sheetnames`属性显示。

```python
book.remove_sheet(sheet1)
```

Python

  

可以使用`remove_sheet()`方法将纸张取出。

```python
book.create_sheet("January", 0)
```

Python

  

可以在指定位置创建一个新图纸。 在我们的例子中，我们在索引为 0 的位置创建一个新工作表。

```python
$ ./sheets2.py 
['January', 'February', 'March', 'April']
['February', 'March', 'April']
['January', 'February', 'March', 'April']
```

Python

  

可以更改工作表的背景颜色。

`sheets3.py`

```python
#!/usr/bin/env python

import openpyxl

book = openpyxl.load_workbook('sheets.xlsx')

sheet = book.get_sheet_by_name("March")
sheet.sheet_properties.tabColor = "0072BA"

book.save('sheets3.xlsx')
```

Python

  

该示例修改了标题为“ March”的工作表的背景颜色。

```python
sheet.sheet_properties.tabColor = "0072BA"
```

Python

  

我们将`tabColor`属性更改为新颜色。

![Python OpenPyXL 教程](https://img.geek-docs.com/python/267940254c695254cc2b315f33c1d587.jpg "Python OpenPyXL 教程")

第三工作表的背景色已更改为某种蓝色。

## 合并单元格

单元格可以使用`merge_cells()`方法合并，而可以不使用`unmerge_cells()`方法合并。 当我们合并单元格时，除了左上角的所有单元格都将从工作​​表中删除。

`merging_cells.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook
from openpyxl.styles import Alignment

book = Workbook()
sheet = book.active

sheet.merge_cells('A1:B2')

cell = sheet.cell(row=1, column=1)
cell.value = 'Sunny day'
cell.alignment = Alignment(horizontal='center', vertical='center')

book.save('merging.xlsx')
```

Python

  

在该示例中，我们合并了四个单元格：A1，B1，A2 和 B2。 最后一个单元格中的文本居中。

```python
from openpyxl.styles import Alignment
```

Python

  

为了使文本在最后一个单元格中居中，我们使用了`openpyxl.styles`模块中的`Alignment`类。

```python
sheet.merge_cells('A1:B2')
```

Python

  

我们用`merge_cells()`方法合并四个单元格。

```python
cell = sheet.cell(row=1, column=1)
```

我们得到了最后一个单元格。

```python
cell.value = 'Sunny day'
cell.alignment = Alignment(horizontal='center', vertical='center')
```

我们将文本设置为合并的单元格并更新其对齐方式。

![Python OpenPyXL 教程](https://img.geek-docs.com/python/7b00cc20b247e6eabdfd52d679384005.jpg "Python OpenPyXL 教程")

## Openpyxl 冻结窗格

冻结窗格时，在滚动到工作表的另一个区域时，我们会保持工作表的某个区域可见。

`freezing.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook
from openpyxl.styles import Alignment

book = Workbook()
sheet = book.active

sheet.freeze_panes = 'B2'

book.save('freezing.xlsx')
```

该示例通过单元格 B2 冻结窗格。

```python
sheet.freeze_panes = 'B2'
```

要冻结窗格，我们使用`freeze_panes`属性。

## Openpyxl 公式

下一个示例显示如何使用公式。 `openpyxl`不进行计算； 它将公式写入单元格。

`formulas.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook

book = Workbook()
sheet = book.active

rows = (
    (34, 26),
    (88, 36),
    (24, 29),
    (15, 22),
    (56, 13),
    (76, 18)
)

for row in rows:
    sheet.append(row)

cell = sheet.cell(row=7, column=2)
cell.value = "=SUM(A1:B6)"
cell.font = cell.font.  (bold=True)

book.save('formulas.xlsx')
```

在示例中，我们使用`SUM()`函数计算所有值的总和，并以粗体显示输出样式。

```python
rows = (
    (34, 26),
    (88, 36),
    (24, 29),
    (15, 22),
    (56, 13),
    (76, 18)
)

for row in rows:
    sheet.append(row)
```

我们创建两列数据。

```python
cell = sheet.cell(row=7, column=2)
```

我们得到显示计算结果的单元格。

```python
cell.value = "=SUM(A1:B6)"
```

我们将一个公式写入单元格。

```python
cell.font = cell.font.  (bold=True)
```

我们更改字体样式。

![Python OpenPyXL 教程](https://img.geek-docs.com/python/330dc2c6f5e65fc37e8ed308b4c9405f.jpg "Python OpenPyXL 教程")

## OpenPyXL 图像

在下面的示例中，我们显示了如何将图像插入到工作表中。

`write_image.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook
from openpyxl.drawing.image import Image

book = Workbook()
sheet = book.active

img = Image("icesid.png")
sheet['A1'] = 'This is Sid'

sheet.add_image(img, 'B2')

book.save("sheet_image.xlsx")
```

在示例中，我们将图像写到一张纸上。

```python
from openpyxl.drawing.image import Image
```

我们使用`openpyxl.drawing.image`模块中的`Image`类。

```python
img = Image("icesid.png")
```

创建一个新的`Image`类。 `icesid.png`图像位于当前工作目录中。

```python
sheet.add_image(img, 'B2')
```

我们使用`add_image()`方法添加新图像。

## Openpyxl 图表

`openpyxl`库支持创建各种图表，包括条形图，折线图，面积图，气泡图，散点图和饼图。

根据文档，`openpyxl`仅支持在工作表中创建图表。 现有工作簿中的图表将丢失。

`create_bar_chart.py`

```python
#!/usr/bin/env python

from openpyxl import Workbook
from openpyxl.chart import (
    Reference,
    Series,
    BarChart
)

book = Workbook()
sheet = book.active

rows = [
    ("USA", 46),
    ("China", 38),
    ("UK", 29),
    ("Russia", 22),
    ("South Korea", 13),
    ("Germany", 11)
]

for row in rows:
    sheet.append(row)

data = Reference(sheet, min_col=2, min_row=1, max_col=2, max_row=6)
categs = Reference(sheet, min_col=1, min_row=1, max_row=6)

chart = BarChart()
chart.add_data(data=data)
chart.set_categories(categs)

chart.legend = None
chart.y_axis.majorGridlines = None
chart.varyColors = True
chart.title = "Olympic Gold medals in London"

sheet.add_chart(chart, "A8")    

book.save("bar_chart.xlsx")
```

在此示例中，我们创建了一个条形图，以显示 2012 年伦敦每个国家/地区的奥运金牌数量。

```python
from openpyxl.chart import (
    Reference,
    Series,
    BarChart
)
```

`openpyxl.chart`模块具有使用图表的工具。

```python
book = Workbook()
sheet = book.active
```

创建一个新的工作簿。

```python
rows = [
    ("USA", 46),
    ("China", 38),
    ("UK", 29),
    ("Russia", 22),
    ("South Korea", 13),
    ("Germany", 11)
]

for row in rows:
    sheet.append(row)
```

我们创建一些数据并将其添加到活动工作表的单元格中。

```python
data = Reference(sheet, min_col=2, min_row=1, max_col=2, max_row=6)
```

对于`Reference`类，我们引用表中代表数据的行。 在我们的案例中，这些是奥运金牌的数量。

```python
categs = Reference(sheet, min_col=1, min_row=1, max_row=6)
```

我们创建一个类别轴。 类别轴是将数据视为一系列非数字文本标签的轴。 在我们的案例中，我们有代表国家名称的文本标签。

```python
chart = BarChart()
chart.add_data(data=data)
chart.set_categories(categs)
```

我们创建一个条形图并为其设置数据和类别。

```python
chart.legend = None
chart.y_axis.majorGridlines = None
```

使用`legend`和`majorGridlines`属性，可以关闭图例和主要网格线。

```python
chart.varyColors = True
```

将`varyColors`设置为`True`，每个条形都有不同的颜色。

```python
chart.title = "Olympic Gold medals in London"
```

为图表设置标题。

```python
sheet.add_chart(chart, "A8")   
```

Python

  

使用`add_chart()`方法将创建的图表添加到工作表中。

![Python OpenPyXL 教程](https://img.geek-docs.com/python/3bf54c368a46a154e45200cfe08e019d.jpg "Python OpenPyXL 教程")

在本教程中，我们使用了 openpyxl 库。 我们已经从 Excel 文件中读取数据，并将数据写入 Excel 文件中。

---

# 实战例程

**读取操作xlsx分为以下步骤**

1. **安装 `openpyxl` 库**： 如果还没有安装 `openpyxl`，首先需要通过 pip 安装它。
    
2. **导入 `openpyxl` 模块**： 在 Python 脚本中导入 `openpyxl` 库。
    
3. **加载 Excel 文件**： 使用 `load_workbook` 函数加载需要读取的 Excel 文件。
    
4. **选择工作表**： 可以通过工作表的名称或索引来选择特定的工作表。
    
5. **读取单元格数据**： 通过指定单元格的位置（如 'A1'）或行列索引（如 `cell(row=1, column=1)`）来读取单个单元格的值。
    
6. **读取多个单元格**： 可以使用切片语法或迭代器来读取一行、一列或一个特定区域的多个单元格数据。
    
7. **处理数据**： 对读取的数据进行所需的处理，例如打印输出、数据分析或转换。
    
8. **关闭工作簿**： 完成数据读取后，可以选择关闭工作簿以释放资源。
    
9. **（可选）保存修改**： 如果对 Excel 文件进行了修改，可以使用 `save` 方法保存更改




```python
from openpyxl import load_workbook

# 1. 加载 Excel 文件
wb = load_workbook('example.xlsx')

# 2. 选择工作表
ws = wb['Sheet1']

# 3. 读取单个单元格数据
value = ws['A1'].value
print(value)

# 4. 读取多个单元格
row = ws['A1:C1']  # 读取第一行的A到C列
col = ws['A1:A10']  # 读取A列的前10行
range_data = ws['A1:C10']  # 读取A1到C10的区域

# 5. 迭代读取行或列
for cell in ws['A1:A10']:
    print(cell.value)

# 6. 关闭工作簿
wb.close()


```

