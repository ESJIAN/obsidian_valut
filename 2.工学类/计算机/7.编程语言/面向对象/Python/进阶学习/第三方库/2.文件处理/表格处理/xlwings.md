---
tags:
  - Lib
  - Example
  - Note
---

![](https://i-blog.csdnimg.cn/blog_migrate/89aca3b719662adf610ef92b92a9a33a.png)

![](https://i-blog.csdnimg.cn/blog_migrate/ac59a567ff22d46493d11215d5135fdf.png)


- # 1. **本库回忆**

打开 APP 对象设置了 `visible = True` 时，会先打开一张空表，然后再打开你的目标表。所以如果只是检查表的话推荐使用 `os.startfile(目标文件路径)` 去打开目标表格，这样会调用系统默认打开工具打开一张表了。



- ## 2.2. 最小操作代码

```python
import xlwings as xw

# 创建一个新的 Excel 应用实例
app = xw.App(visible=True, add_book=False)  # visible=True 显示 Excel 窗口, add_book=False 不自动创建新的工作簿

# 创建一个新的工作簿
wb = app.books.add()

# 或者打开一个已有的工作簿
wb = xw.Book('path/to/your/excel_file.xlsx')

# 保存工作簿/修改(可选)
wb.save()

# 关闭工作簿
wb.close()

# 关闭app
app.close()

```

- # 2. **本库重点**


- # 3. **本库犯错**

- ## 3.1. 提前结束进程造成工作簿对象没有保存

提前结束进程造成工作簿对象没有保存，下次程序运行时候由于上次的缓存保留机制造成进程卡死在该行（图1），此时你尝试删除这个表格的话会弹出警告(图2)，解决方法就是在任务管理器中关闭被调用的Excel进程（图3）。这个时候如果你 catch error 的话可能会得到 `(1400, 'FindWindowEx', 'Invalid window handle.')` 的报错。

![image.png](https://i0.hdslb.com/bfs/openplatform/fb436a0c0dc8c512a4c23a010a34a37f172a9078.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/13185e758a1e178cd92bc4576f2f37010183c592.png)

![image.png](https://i0.hdslb.com/bfs/openplatform/661e01dbae2621b9d8faa43dad3790d624fdcc7b.png)

>**思考**：为了防止操作资源对象时打开资源对象但是却没有及时关闭的问题的发生，请使用基于形如 `with  xw.App() as` 的自动管理区管理资源的操作。

- ## 3.2. APP对象未及时退出

一定要记得在表格操作完成后wb.close()关闭表格操作对象和app.quit()关闭工作簿，如果下次创建对象时候如果表格对象与前面重名，会造成同名对象引用的冲突，下面是代码延时

以下代码会模拟描述的故障现象：提前结束进程，导致工作簿对象没有保存，下次程序运行的时候由于上次的缓存保留机制造成进程卡死。

```python
import xlwings as xw
import time
import os
import signal

def excel_operation_incomplete_close(filename="output.xlsx"):
    """
    演示 xlwings 的基本操作，但故意不完整地关闭工作簿和 Excel 应用，
    模拟提前结束进程的情况。
    """
    app = None
    wb = None
    try:
        # 创建一个新的 Excel 应用实例
        app = xw.App(visible=True, add_book=False)

        # 创建一个新的工作簿
        wb = app.books.add()

        # 获取当前活动工作表
        sheet = wb.sheets.active

        # 写入单元格
        sheet.range('A1').value = 'Hello xlwings!'

        # 保存工作簿
        wb.save(filename)

        print(f"Excel 文件 '{filename}' 创建成功！")

        # 模拟程序提前结束，不执行 wb.close() 和 app.quit()
        print("模拟程序提前结束...")
        # os.kill(os.getpid(), signal.SIGTERM)  # 强制结束当前进程 (取消注释以启用)
        # time.sleep(5) # 模拟程序运行一段时间后崩溃
        raise Exception("模拟程序崩溃")

    except Exception as e:
        print(f"发生错误: {e}")
    finally:
        print("程序结束，但是wb.close()和app.quit()可能没有执行")
        # 注意：这里故意注释掉 wb.close() 和 app.quit()，模拟程序崩溃或提前结束
        # if wb:
        #     wb.close()  # 关闭工作簿，释放资源
        #     print("工作簿已关闭。")
        # if app:
        #     app.quit()  # 退出 Excel 应用，结束进程
        #     print("Excel 应用已退出。")

def excel_operation_next_time(filename="output.xlsx"):
    """
    演示下一次运行程序时，由于上次的缓存保留机制造成的进程卡死现象。
    """
    app = None
    wb = None
    try:
        # 创建一个新的 Excel 应用实例
        app = xw.App(visible=True, add_book=False)

        # 尝试打开之前未完整关闭的工作簿
        wb = app.books.open(filename)

        print(f"成功打开 Excel 文件 '{filename}'！")

        # 获取当前活动工作表
        sheet = wb.sheets.active

        # 写入单元格
        sheet.range('A2').value = 'Hello again!'

        # 保存工作簿
        wb.save()

    except Exception as e:
        print(f"发生错误: {e}")
    finally:
        if wb:
            wb.close()  # 关闭工作簿，释放资源
            print("工作簿已关闭。")
        if app:
            app.quit()  # 退出 Excel 应用，结束进程
            print("Excel 应用已退出。")

# 运行示例
excel_operation_incomplete_close()
print("第一次运行结束，模拟程序崩溃，没有正确关闭Excel")

print("\n第二次运行开始，尝试打开之前未完整关闭的Excel文件")
excel_operation_next_time()
print("第二次运行结束")
```

**代码解释：**

1.  **`excel_operation_incomplete_close()` 函数：**
    *   创建 Excel 应用和工作簿，并写入数据。
    *   **关键：**  注释掉了 `wb.close()` 和 `app.quit()`，模拟程序在完成操作之前崩溃或被强制结束的情况。
    *   `os.kill(os.getpid(), signal.SIGTERM)` 这行代码被注释掉了，如果取消注释，它会强制结束当前 Python 进程，更加真实地模拟程序崩溃。
    *   `raise Exception("模拟程序崩溃")` 这行代码会抛出一个异常，模拟程序运行过程中发生错误导致崩溃。
2.  **`excel_operation_next_time()` 函数：**
    *   尝试打开之前未完整关闭的工作簿 (`output.xlsx`)。
    *   如果上次的 Excel 进程没有完全退出，可能会出现以下情况：
        *   xlwings 尝试重新连接到之前的 Excel 进程，但由于状态不一致，可能导致卡死或出现其他错误。
        *   Excel 可能会显示一个警告，提示文件已被锁定或正在使用中。
3.  **运行顺序：**
    *   首先运行 `excel_operation_incomplete_close()`，模拟程序崩溃，不完整地关闭 Excel。
    *   然后运行 `excel_operation_next_time()`，尝试打开之前未完整关闭的 Excel 文件，观察是否出现卡死或错误。

**如何复现故障现象：**

1.  **运行代码：**  直接运行上面的 Python 代码。
2.  **观察现象：**
    *   第一次运行后，`output.xlsx` 文件会被创建，但 Excel 进程可能没有完全退出。
    *   第二次运行时，`excel_operation_next_time()` 可能会卡住，或者抛出异常。
    *   你可能会在任务管理器中看到 Excel 进程仍然在运行。
    *   尝试手动删除 `output.xlsx` 文件时，可能会遇到 "文件正在使用中" 的错误提示。

**解决方法：**

1.  **手动结束 Excel 进程：**  打开任务管理器，找到并结束所有 Excel 进程。
2.  **重新运行代码：**  再次运行代码，`excel_operation_next_time()` 应该能够正常打开 `output.xlsx` 文件。

**总结：**

这段代码模拟了由于程序提前结束或崩溃，导致 xlwings 工作簿和 Excel 应用没有正确关闭，从而在下次运行时出现问题的场景。通过复现这个故障，你可以更好地理解 xlwings 中正确关闭资源的重要性，以及如何处理类似的问题。

**请注意：**  强制结束进程可能会导致数据丢失或其他不可预测的问题。在实际开发中，应该尽量避免这种情况，并确保程序能够正常关闭资源。

- ## 3.3. APP 保存语句错行


- ## 3.4. 1400, 'FindWindowEx', 'Invalid window handle.' 报错

```python
    try:
        # 调用xlwings打开 excel 应用对象
        with xw.App(visible=False) as app:
            # 读取主工作表格
            try:
                # 打开主工作簿对象
                main_workbook = app.books.open(excel_file_path)
                print(f"Notice: 主工作表加载成功，文件路径: {excel_file_path}")
            except Exception as e:
                print(f"Error: {e}")
                return

            # 轮询读取暂存表格数据行
            for row_index in range(1, read_temp_storage_workbook.sheet_by_index(0).nrows):
                # 读取行数据
                row_data = read_temp_storage_workbook.sheet_by_index(0).row_values(row_index)
                # 创建一个字典，用于存储列索引和列名的对应关系
                header_index = {name: idx for idx, name in enumerate(read_temp_storage_workbook_headers)}
                try:
                    # 将日期分解为月和日
                    year, month, day = row_data[header_index["日期"]].split("-")
                    # 获取行中类别列类型单元中的类别名数据
                    category_name = row_data[header_index["类别"]]
                    # 获取行中品名列类型单元中的品名名数据
                    product_name = row_data[header_index["品名"]]
                    # 获取行中单位列类型单元中的单位名数据
                    unit_name = row_data[header_index["单位"]]
                    # 获取行中单价列类型单元中的单价名数据
                    price = row_data[header_index["单价"]]
                    # 获取行中数量列类型单元中的数量名数据
                    quantity = row_data[header_index["数量"]]
                    # 获取行中金额列单元中金额数据
                    amount = row_data[header_index["金额"]]
                    # 获取行中备注列单元中备注数据
                    remark = row_data[header_index["备注"]]
                    # 获取行中公司列单元中公司名数据
                    company_name = row_data[header_index["公司"]]
                    # 获取行中单名称列单元中单名数据
                    single_name = row_data[header_index["单名"]]
                except Exception as e:
                    __main__.SAVE_OK_SIGNAL = False
                    print(f"Error: 处理主工作簿，更新相关表格信息时拆解数据出错 {e}")

                try:
                    if not __main__.MODE:
                        print(f"\n\nNotice: {product_name}正在入库")
                        # 更新指定公司sheet中的金额数据
                        update_company_sheet(self, main_workbook, product_name, company_name, amount)  # 只在入库的时候用到
                        # 更新入库相关表中的条目信息
                        updata_import_sheet(self, main_workbook, product_name, single_name, row_data, header_index, month, day, unit_name)  # TODO:优化耗时
                        # 更新食品收发库存表中的条目信息
                        update_inventory_sheet(self, main_workbook, product_name, unit_name, quantity, price, amount, remark)
                        # 更新收发存表皮中的条目信息
                        update_receipt_storage_sheet(self, main_workbook, product_name, single_name, category_name, amount)
                        # 更新主副食明细账中的条目信息
                        update_main_food_detail_sheet(self, main_workbook, product_name, single_name, category_name, amount)
                    else:
                        print(f"\n\nNotice: 品名{product_name}正在出库")
                        # 此函数不带"export"头，没打错
                        updata_import_sheet(main_workbook, single_name, row_data, header_index, month, day, unit_name)
                        # 搞定
                        export_update_inventory_sheet(main_workbook, product_name, unit_name, quantity, price, amount, remark)
                        # 搞定
                        export_update_receipt_storage_sheet(main_workbook, single_name, category_name, amount)
                        # 搞定
                        export_update_main_food_detail_sheet(main_workbook, single_name, category_name, amount)

                except Exception as e:
                    print(f"Error: 更新主工作簿，更新相关表格信息时出错 {e}")
                    continue

            try:
                # 保存工作簿
                main_workbook.save()
                # 关闭工作簿
                main_workbook.close()
                # 关闭应用对象
                app.quit()  # Learning：切记关闭应用对象，否则会造成下次创建一个同名应用对象时候发生对象名重复的冲突造成进程卡死
            except Exception as e:
                print(f"Error: 保存主表时出错 {e}")
    except Exception as e:
        print(f"Error: 打开或处理该表 {excel_file_path} 出错,出错信息{e}")
```

- 【问题描述】终端抓取报错错误码如标题所示


- 【问题分析】使用 try 上下文的对象管理方法时候，对于资源对象的释放不需要手动进行

- 【方案尝试】删掉手动关闭应用对象的这一句

```python

# 关闭工作簿
main_workbook.close()
# 关闭应用对象
app.quit()  # Learning：切记关闭应用对象，否则会造成下次创建一个同名应用对象时候发生对象名重复的冲突造成进程卡死
except Exception as e:
print(f"Error: 保存主表时出错 {e}")

# 关闭工作簿
# main_workbook.close()  这一句删掉，这是不需要的
# 关闭应用对象
app.quit()  # Learning：切记关闭应用对象，否则会造成下次创建一个同名应用对象时候发生对象名重复的冲突造成进程卡死
except Exception as e:
print(f"Error: 保存主表时出错 {e}")

```


- ## 3.5. Debug 模式提前终止程序导致报错

- 【问题描述】在尝试 Sheet 索引时终端发生如下报错

![image.png](https://i0.hdslb.com/bfs/openplatform/743d8472a689642489d91aae6367fbd735dcf567.png)

<center><b>图：报错语句发生时的结构</b></center>

```
(-2147352567, 'Exception occurred.', (0, None, None, None, 0, -2147352565), None)
```

- 【问题分析】是**xlwings** 或 **pywin32** 操作 Excel COM 对象时的典型 COM 异常，常见原因有：

	1. **sheet名不匹配或不存在**  
	    你传入的 [sheet_name](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html) 在 workbook.sheets 里找不到，导致 [workbook.sheets[sheet_name]](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html) 抛出异常。
	    
	2. **Excel 进程未正常打开或已被关闭**  
	    比如 workbook 或 app 被提前关闭，或 Excel 进程被杀死。
	    
	3. **Excel 文件被占用或损坏**  
	    文件被其他程序占用、只读、损坏等。
	    
	4. **COM对象失效**  
	    比如 sheet、workbook、app 对象被提前释放或作用域外失效。
	    
	5. **sheet_name 有空格或特殊字符**  
	    你代码里有 [name = re.sub(r'\s+', '', name)](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)，可能导致实际 sheet 名和 Excel 里的不一致。
	

- 【方案尝试】在任务管理器中发现了未被结束的 Excel 进程，手动将其结束


- 【方案验证】




---

## 简介

xlwings 是一个 Python 库，可以方便地从 Python 中调用 Excel，也可以在 Excel 中调用 Python。它使得 Python 能够作为 Excel 的脚本语言，从而实现 Excel 的自动化，数据分析和可视化等功能。

**主要特点：**

*   **双向调用:** 可以在 Python 中调用 Excel，也可以在 Excel 中调用 Python。
*   **易于使用:** 提供了简洁的 API，易于学习和使用。
*   **强大的功能:** 支持读取、写入 Excel 数据，操作 Excel 对象（如工作表、单元格、图表等），以及自定义 Excel 函数。
*   **跨平台:** 支持 Windows, macOS, Linux 操作系统。
*   **与 Pandas 集成:** 可以方便地将 Pandas DataFrame 对象与 Excel 进行数据交换。
*   **UDFs (User Defined Functions):** 可以用 Python 编写自定义 Excel 函数 (UDFs)。

---


## 安装&卸载
像安装其他模块一样，使用pip安装即可

> pip install xlwings

如果你是在使用Anaconda也可以，使用conda安装

> conda install xlwings

请注意，官方的`conda`软件包可能落后于几个版本。但是，您可以使用`conda-forge`通道（如果已经安装了xlwings，请用`upgrade`替换安装）：

> conda install -c conda-forge xlwings

注意：在安装过程中，xlwings也是有依赖项的，但是依赖项通过`conda`或`pip`自动安装

> Windows：`pywin32`
> 
> Mac：`psutil`，`appscript`

如果原来安装过，使用如下操作更新

要更新到最新的xlwings版本，请在命令提示符中运行以下内容：

> pip install --upgrade xlwings

或者：

> conda update -c conda-forge xlwings

通过运行以下内容（确保先关闭Excel），确保您的Excel加载项版本与您的Python软件包保持同步：

> xlwings addin install

若要**卸载xlwings**，移步下面的操作

要完全**卸载xlwings**，请先卸载加载项，然后使用安装xlwings软件包时使用的相同方法（pip或conda）卸载xlwings软件包：

> xlwings addin remove

然后

> pip uninstall xlwings

或者：

> conda remove xlwings

最后，手动删除个人文件夹中的`.xlwings`目录（如果存在）
## 方法介绍
**注意：**

*   以下方法基于 xlwings 官方文档（[https://docs.xlwings.org/en/stable/index.html](https://docs.xlwings.org/en/stable/index.html)），请参考官方文档获取最准确和最新的信息。
*   由于 xlwings 的功能非常丰富，这里只列出最常用的方法。
*   以下方法的使用都需要先创建对应的对象实例。

### 1. `App` 对象

- # 1. 本节重点

- ## 1.1. 一个 APP 对象可以孵化多个 Book 对象


- # 3. 本节犯错

- ## 3.1. 手动创建 App 实例出错
创建 app 实例，并且打开了目标表却没有及时的关闭，导致调用 shutil库删除该表时发现该文件被占用的报错

```bash
Error: 将主表文件复制到 work 目录出错,错误信息为: [WinError 32] The process cannot access the file because it is being used by another process: './src/data/storage/work\\子表\\2025年主副食-三矿版主食.xls'
```

需要及时补上app.close()语句

已经用表格打开要程序操作的表，导致程序尝试打开该表时发生如下报错

```
-2147417848, 'The object invoked has disconnected from its clients.', None, None
```

需要关闭你手动打开的那张表


- ## 3.2. With 上下文管理 APP 对象时调用了 quit 方法

- 【问题描述】在使用上下文管理 APP 对象时候误用了

```python
   with xw.App(visible=False) as app:
		xxx
		xxx
		app.quit()

```



- ## 3.3. 连续两次在不同地方打开同一个工作簿

- 【问题描述】形如下描述代码，由于两行间隔较远导致忘记上面使用过一次 `open` 方法打开同一个文件，造成报错

```python
workbook = app.books.open(main_excel_file_path)
....
workbook = app.books.open(main_excel_file_path)
```

```bash
Cannot open two workbooks named '2025.4.20.xls', even if they are saved indifferent locations.
```

- 【问题分析】Excel 应用程序本身不允许打开两个具有相同名称的工作簿，即使它们位于不同的位置。

- 【方案尝试】

	**方法 1：遍历已打开的工作簿并匹配名称**
	
	*   您可以遍历 `app.books` 集合，查找名称与目标工作簿名称匹配的工作簿。
	
	```python
	import xlwings as xw
	
	def get_existing_workbook(app, workbook_name):
	    """
	    查找是否已存在指定名称的工作簿。
	    """
	    for wb in app.books:
	        if wb.name == workbook_name:
	            return wb
	    return None
	
	try:
	    app = xw.App(visible=False)
	    workbook_name = '2025.4.20.xls'
	
	    # 尝试获取已存在的工作簿
	    existing_workbook = get_existing_workbook(app, workbook_name)
	
	    if existing_workbook:
	        print(f"已找到名为 '{workbook_name}' 的工作簿。")
	        wb = existing_workbook
	        # ... 进行操作 ...
	    else:
	        print(f"未找到名为 '{workbook_name}' 的工作簿，尝试打开。")
	        wb = app.books.open(workbook_name)
	        # ... 进行操作 ...
	
	    # ... 进行操作 ...
	    wb.close()
	
	except Exception as e:
	    print(f"Error: {e}")
	finally:
	    app.quit()
	```
	
	**方法 2：使用 `try...except` 捕获异常并处理**
	
	*   尝试打开工作簿，如果抛出异常（例如 "Cannot open two workbooks named..."），则遍历已打开的工作簿并匹配名称。
	
	```python
	import xlwings as xw
	
	def get_existing_workbook(app, workbook_name):
	    """
	    查找是否已存在指定名称的工作簿。
	    """
	    for wb in app.books:
	        if wb.name == workbook_name:
	            return wb
	    return None
	
	try:
	    app = xw.App(visible=False)
	    workbook_name = '2025.4.20.xls'
	
	    try:
	        wb = app.books.open(workbook_name)
	    except Exception as e:
	        print(f"打开工作簿失败: {e}，尝试切换到已打开的工作簿。")
	        existing_workbook = get_existing_workbook(app, workbook_name)
	        if existing_workbook:
	            wb = existing_workbook
	        else:
	            raise  # 如果没有找到已打开的工作簿，则抛出异常
	
	    # ... 进行操作 ...
	    wb.close()
	
	except Exception as e:
	    print(f"Error: {e}")
	finally:
	    app.quit()
	```
	
	**方法 3：使用 `Book` 构造函数和完整路径**
	
	*   如果知道已打开工作簿的完整路径，可以直接使用 `xw.Book` 构造函数来连接到该工作簿。
	
	```python
	import xlwings as xw
	import os
	
	try:
	    app = xw.App(visible=False)
	    workbook_name = '2025.4.20.xls'
	    workbook_path = os.path.abspath(workbook_name)  # 获取完整路径
	
	    try:
	        wb = xw.Book(workbook_path)  # 尝试连接到已打开的工作簿
	    except Exception as e:
	        print(f"连接到已打开的工作簿失败: {e}，尝试打开。")
	        wb = app.books.open(workbook_name)  # 如果连接失败，则打开工作簿
	
	    # ... 进行操作 ...
	    wb.close()
	
	except Exception as e:
	    print(f"Error: {e}")
	finally:
	    app.quit()
	```
	


---

`App` 对象代表一个 Excel 应用程序实例。

*   **`__init__(self, visible=True, add_book=True)`**: 初始化 App 对象。
    *   `visible` (bool): 是否显示 Excel 应用程序窗口。默认为 `True`。
    *   `add_book` (bool): 是否自动创建一个新的工作簿。默认为 `True`。
*   **`books`**: 返回一个 `Books` 对象，用于管理工作簿集合。
*   **`display_alerts`**: 获取或设置是否显示 Excel 警告框。
*   **`screen_updating`**: 获取或设置是否更新屏幕显示。
*   **`version`**: 返回 Excel 应用程序的版本号。
*   **`quit()`**: 退出 Excel 应用程序。

**示例：**

```python
import xlwings as xw

# 创建一个 Excel 应用实例
app = xw.App(visible=True, add_book=False)

# 获取 Excel 版本
print(app.version)

# 退出 Excel 应用
app.quit()
```

>**注意**：执行 `app = xw.App(visible=True, add_book=False)` 这个操作是非常耗时的，所以不要在循环中执行这个 IO 资源对象的操作。能用一行这个语句解决的就不要在多用了！！



### 2. `Book` 对象

- ## 3. 本节犯错

- ## 3.1. 忘记调用 .save() 以及 .close() 方法

```ad-note
title:**本节犯错**

1. 忘记调用`.close()`方法导致未写入内容后未保存
2. 
```

- ## 3.3. 误在循环体中写入了 .save() 以及 .close() 方法

- 【问题描述】创建 books 对象的语句与保存、关闭语句放错位置了

```python
main_workbook = app.books.open(excel_file_path)
# 轮询读取暂存表格数据行
for row_index in range(1, read_temp_storage_workbook.sheet_by_index(0).nrows):
	XXX
	main_workbook.save()
    # 关闭工作簿
    main_workbook.close()
```


```
更新指定公司 四季常青 Sheet 失败，(-2147417848, 'The object invoked has disconnected from its clients.', None, None)
```

- 【方案尝试】



----

`Book` 对象代表一个 Excel 工作簿。

*   **`__init__(self, fullname=None, app=None, add_book=True)`**: 初始化 Book 对象。
    *   `fullname` (str, optional): 工作簿的文件路径。如果为 `None`，则创建一个新的工作簿。
    *   `app` (xw.App, optional):  `App` 对象。如果为 `None`，则使用当前活动的 Excel 应用程序。
    *   `add_book` (bool): 是否自动创建一个新的工作簿。默认为 `True`。
*   **`name`**: 返回当前选中工作簿的名称。
*   **`fullname`**: 返回工作簿的完整路径。
*   **`sheets`**: 返回一个 `Sheets` 对象，用于管理工作表集合，==包含该 Excel 工作簿中所有工作表名==。
*   `sheets[name]`: 
*   **`activate()`**: 激活工作簿。
*   **`save(path=None)`**: 保存工作簿。如果 `path` 为 `None`，则保存到原始文件路径。
*   **`close()`**: 关闭工作簿。
*    **`set_mock_caller(path)`**: 设置模拟调用者，用于调试 UDFs。

**示例：**

```python
import xlwings as xw

# 创建一个 Excel 应用实例
app = xw.App(visible=True, add_book=False)

# 创建一个新的工作簿
wb = app.books.add()

# 获取工作簿名称
print(wb.name)

# 保存工作簿
wb.save('output.xlsx')

# 关闭工作簿
wb.close()

# 退出 Excel 应用
app.quit()
```

```python
import xlwings as xw

# 创建一个 Excel 应用实例
app = xw.App(visible=True, add_book=False)

# 创建一个新的工作簿
wb = app.books.add()

# 获取工作簿中所有工作表的名字
sheet_names = [sheet.name for sheet in wb.sheets]
print(sheet_names)

# 关闭工作簿
wb.close()

# 退出 Excel 应用
app.quit()
```


### 3. `Sheet` 对象

```ad-note
title:**本节重点**
- range (cell) 的`cell`索引方法有两种，具体参考[链接](https://chatgpt.com/share/68145d1c-f3fc-8011-9a76-63aecde117c6)
	- **圆括号**（`()`）——Excel/VBA 风格，行列均以 **1** 为起点，`sheet.range((2,1))` /`sheet.range(2,1)`表示访问第二行第一个单元；`sheet.range("A2")` 表示访问A列第二行;`sheet.range("A:A")` 表示访问整个A列对象
    
	- **方括号**（`[]`）——Python 风格，行列均以 **0** 为起点，切片遵循半开区间原则。`sheet.range([1,0])` 表示访问第二行第一个单元



```

```ad-note
title:**本节犯错**

- `Sheet` 对象没有 row属性或者方法
```

`Sheet` 对象代表一个 Excel 工作表。

*   **`name`**: 返回工作表的名称。
*   **`range(cell)`**: 返回一个 `Range` 对象，用于操作单元格或单元格区域。
*   **`activate()`**: 激活工作表。
*   **`delete()`**: 删除工作表。
*   **`clear()`**: 清除工作表中的所有内容和格式。
*   **`clear_contents()`**: 清除工作表中的所有内容，但保留格式。
*   **`used_range`**: 返回一个 `Range` 对象，代表工作表中已使用的区域。
*   `index(name)`: 寻找名为 `name` 单元返回行索引（0索引制）


- # name 方法

- # range 方法

- # activate 方法

- # delete 方法

- # clear 方法

- # clear_contents 方法

- # used_range 方法

- # index 方法

**示例：**

```python
import xlwings as xw

# 创建一个 Excel 应用实例
app = xw.App(visible=True, add_book=False)

# 创建一个新的工作簿
wb = app.books.add()

# 获取当前活动工作表
sheet = wb.sheets.active

# 写入单元格
sheet.range('A1').value = 'Hello xlwings!'

# 从A1单元格从左向右写入表头
sheet.range('A1').value = ['日期', '类别', '品名', '金额', '数量', '单价', '单位', '公司', '单名']

# 获取单元格的值
value = sheet.range('A1').value
print(value)

# 清除工作表内容
sheet.clear_contents()

# 关闭工作簿
wb.close()

# 退出 Excel 应用
app.quit()
```

![image.png](https://i0.hdslb.com/bfs/openplatform/7d059b6cbf38e46fce2327d8f7a43476cfbafac2.png)

<center><b>图：写入表头的 Sheet
</b></center>






### 4. `Range` 对象


```ad-note
title:**本节重点**
- range (cell) 的`cell`索引方法有两种，具体参考[链接](https://chatgpt.com/share/68145d1c-f3fc-8011-9a76-63aecde117c6)
	- **圆括号**（`()`）——Excel/VBA 风格，行列均以 **1** 为起点，`sheet.range((2,1))`/`sheet.range(2,1)` 表示访问第二行第一个单元；`sheet.range("A2")` 表示访问A列第二行;`sheet.range("A:A")` 表示访问整个A列对象
    
	- **方括号**（`[]`）——Python 风格，行列均以 **0** 为起点，切片遵循半开区间原则。`sheet.range([1,0])` 表示访问第二行第一个单元
```

```ad-note
title:**本节犯错**
- range(cell) `cell` 使用 `sheet.range(f"{found_column_index}{found_row_index}")` 方式进行索引犯错过，因为{found_column_index}{found_row_index}返回的是数字，非VBA方式的索引字符
```

`Range` 对象代表 Excel 工作表中的一个单元格或单元格区域。

*   **`value`**: 获取或设置单元格的值。
*   **`formula`**: 获取或设置单元格的公式。
*   **`number_format`**: 获取或设置单元格的数字格式。
*   **`font`**: 返回一个 `Font` 对象，用于设置单元格字体格式。
*   **`color`**: 获取或设置单元格的背景颜色。
*   **`clear()`**: 清除区域中的所有内容和格式。
*   **`clear_contents()`**: 清除区域中的所有内容，但保留格式。
*   **`row`**: 返回区域的起始行号。
*   **`column`**: 返回区域的起始列号。
*   **`rows`**: 返回一个 `RangeRows` 对象，用于操作区域中的行。
*   **`columns`**: 返回一个 `RangeColumns` 对象，用于操作区域中的列。
*   **`address`**: 返回区域的地址。
*   **`last_cell`**: 返回区域中最后一个单元格的 `Range` 对象。
*   **`offset(row_offset=0, column_offset=0)`**: 返回一个相对于当前区域偏移后的 `Range` 对象。
*   **`resize(row_size=None, column_size=None)`**: 返回一个调整大小后的 `Range` 对象。
*   **`select()`**: 选择该区域。
*   **`copy()`**: 复制该区域。
*   **`paste()`**: 粘贴到该区域。
*   **`insert()`**: 插入单元格。
*   **`delete()`**: 删除单元格。
*   **`expand(mode='down')`**: 扩展区域以包含相邻的非空单元格。
    *   `mode`:  `'table'` (default), `'down'`, `'right'`
*   **`options(convert=DEFAULT_CONVERTER, **kwargs)`**: 配置如何从 Excel 读取数据或将数据写入 Excel。
    *   `ndim` (int):  将一维列表转换为二维数组。
    *   `header` (bool):  将第一行作为列名。
    *   `index` (bool):  将第一列作为索引。
    *   `numbers` (type):  将数字转换为指定类型。
    *   `dates` (type):  将日期转换为指定类型。
    *   `empty` (value):  将空单元格转换为指定值。
    *   `transpose` (bool):  转置数据。
    *   `pd.DataFrame` (bool):  将数据转换为 Pandas DataFrame。
    *   `np.array` (bool):  将数据转换为 NumPy 数组。
- **`value`**:
    - `index(name)`：返回名为 `name` 的单元格的行索引（0 索引制）。**注意：** 此处描述可能不准确
- **`api`**: 调用 Excel 的 api 进行相关操作的实现
    - `Find(what, after, lookIn, lookAt, searchOrder, searchDirection, matchCase, matchByte, searchFormat)`: 在区域中查找特定值。
        - `what`: 要查找的内容。
        - `after`: 查找开始的位置。
        - `lookIn`: 查找的类型，例如 `xlValues` (值) 或 `xlFormulas` (公式)。
        - `lookAt`: 查找的方式，例如 `xlPart` (部分匹配) 或 `xlWhole` (完全匹配)。
        - `searchOrder`: 搜索顺序，例如 `xlByRows` (按行) 或 `xlByColumns` (按列)。
        - `searchDirection`: 搜索方向，例如 `xlNext` (下一个) 或 `xlPrevious` (上一个)。
        - `matchCase`: 是否区分大小写。
        - `matchByte`: 是否区分全角/半角字符 (仅用于双字节字符集)。
        - `searchFormat`: 是否搜索特定格式。
        - -------------------------下面是返回的对象具有的方法
	        - `row`:  （这个方法不知道为什么经常容易卡死）
    - `ColumnWidth`: 获取或设置列宽。
    - `RowHeight`: 获取或设置行高。
    - `Interior`: 返回一个 `Interior` 对象，用于设置单元格内部属性，如颜色。
    - `Borders`: 返回一个 `Borders` 对象，用于设置单元格边框。

**示例：**

```python
import xlwings as xw

# 创建一个 Excel 应用实例
app = xw.App(visible=True, add_book=False)

# 创建一个新的工作簿
wb = app.books.add()

# 获取当前活动工作表
sheet = wb.sheets.active

# 写入单元格
sheet.range('A1').value = 'Hello xlwings!'

# 设置单元格格式
sheet.range('A1').font.bold = True
sheet.range('A1').color = (255, 0, 0)  # 红色

# 获取单元格的值
value = sheet.range('A1').value
print(value)

# 获取区域对象
rng = sheet.range('A1:C3')

# 设置区域边框
rng.api.Borders.LineStyle = 1  # 1 表示细实线

# 关闭工作簿
wb.close()

# 退出 Excel 应用
app.quit()
```

**注意：**

*   `Range` 对象还有很多其他方法，例如用于操作批注、超链接、公式等。
*   `Range` 对象的 `api` 属性可以访问 Excel COM API，用于执行更高级的操作。


<center><b>表：Excel 单元格主要的四种索引形式</b></center>

| 引用形式   | 行号是否固定 | 列号是否固定 | 描述说明               | 示例公式         | 复制公式时行为示例         |
| ------ | ------ | ------ | ------------------ | ------------ | ----------------- |
| `A1`   | ❌ 否    | ❌ 否    | 相对引用：行列都随公式的复制而变化  | `=A1+B1`     | 向下复制变为 `=A2+B2`   |
| `$A1`  | ❌ 否    | ✅ 是    | 混合引用：列固定，行随公式移动而变化 | `=$A1+B1`    | 向右复制变为 `=$A1+C1`  |
| `A$1`  | ✅ 是    | ❌ 否    | 混合引用：行固定，列随公式移动而变化 | `=A$1+B1`    | 向下复制变为 `=A$1+B2`  |
| `$A$1` | ✅ 是    | ✅ 是    | 绝对引用：行列都不随公式复制而变化  | `=$A$1+$B$1` | 无论怎么复制始终引用 `$A$1` |


## 基本用法

在我们操作之前可以先了解下，如下内容：

- **新建**：创建一个不存在的工作薄或者工作表
    
- **打开**：打开一个已经存在的工作薄
    
- **引用**：就是告诉程序，你要操作哪个对象。比如你打开了A、B、C三个工作薄，现在你想操作A工作薄，就要先引用A
    
- **激活**：我们可以同时打开多个工作薄，但是一次只能操作一个工作簿，我们正在操作的这个工作薄称为**当前活动工作薄。
    

在xlwings中

- Excel程序用App来表示，多个Excel程序集合用Apps表示；
    
- 单个工作簿用Book表示，工作簿集合用Books表示；
    
- 单个工作表用Sheet表示，工作表集合用Sheets表示；
    
- 区域用Range表示，既可以是一个单元格，也可以是一片单元格区域。
    

![](https://i-blog.csdnimg.cn/blog_migrate/601574347e1a9731c19c3f8998d78900.png)

<center><b>
图：Xlwings依次需要创建的几个操作对象</b></center>

对Excel进行操作主要使用如下三个类：

> import xlwings as xw
> 
> xw.App 打开一个excel应用
> 
> xw.Book 创建一个工作薄
> 
> xw.Sheet 创建一个工作表

### 1. 创建 Excel 应用和工作簿

显式调用 app 方法创建保存新的工作簿

```python
import xlwings as xw

# 创建一个新的 Excel 应用实例
app = xw.App(visible=True, add_book=False)  # visible=True 显示 Excel 窗口, add_book=False 不自动创建新的工作簿

# 创建一个新的工作簿
wb = app.books.add()

# 或者打开一个已有的工作簿
wb = xw.Book('path/to/your/excel_file.xlsx')

# 保存工作簿/修改(可选)
wb.save()

# 关闭工作簿
wb.close()

# 关闭app
app.close()
```

隐式的创建一个空的 `excel_file.xlsx`

```python
import xlwings as xw

# 打开空工作簿
workbook = xw.Book()      
# 保存为'path/to/your/excel_file.xlsx'
workbook.save('path/to/your/excel_file.xlsx')
# 关闭工作簿
workbook.close()
```

```ad-note
title:**第二个方法为何不需要创建 app 实例**
`xlwings` 在某些情况下可以自动处理与 Excel 应用程序的连接，因此你提供的代码片段不需要显式地创建 `xw.App` 实例。以下是一些可能的原因：

1.  **默认行为：** `xlwings` 默认情况下会自动启动 Excel 应用程序（如果尚未运行）并在后台处理连接。这意味着，当你调用 `xw.Book()` 时，`xlwings` 会自动查找或启动 Excel 实例。

2.  **配置设置：** `xlwings` 的配置可能会影响其行为。例如，你可能在 `xlwings` 的配置文件中设置了默认的 Excel 实例行为。

3.  **隐式启动：** 某些操作（如 `workbook.save()`）可能会隐式地启动 Excel 应用程序，即使你没有显式地创建 `xw.App` 实例。

尽管在你的代码片段中没有显式地创建 `xw.App` 实例，但 `xlwings` 仍然需要在后台使用 Excel 应用程序来执行操作。如果你想更明确地控制 Excel 应用程序的行为（例如，控制 Excel 是否可见，或者是否添加新的工作簿），你可以显式地创建 `xw.App` 实例。

以下是一些建议：

*   **显式创建 `xw.App` 实例：** 如果你希望更明确地控制 Excel 应用程序的行为，建议显式地创建 `xw.App` 实例。例如：

    ```python
    import xlwings as xw

    app = xw.App(visible=True, add_book=False)
    workbook = xw.Book()
    workbook.save(__main__.TEMP_SINGLE_STORAGE_EXCEL_PATH)
    workbook.close()
    app.quit()  # 确保关闭 Excel 应用程序
    ```

*   **检查 `xlwings` 配置：** 检查你的 `xlwings` 配置文件，看看是否有任何影响 Excel 应用程序行为的设置。

*   **确保 Excel 已安装：** 确保你的计算机上已安装 Excel 应用程序，并且 `xlwings` 可以找到它。

总之，虽然你的代码片段可以工作，但显式地创建 `xw.App` 实例可以让你更好地控制 Excel 应用程序的行为，并避免潜在的问题。

```

### 2. 操作工作表 (Sheet)

```python
# 获取当前活动工作表
sheet = wb.sheets.active

# 或者通过名称获取工作表
sheet = wb.sheets['Sheet1']

# 或者通过索引获取工作表
sheet = wb.sheets[0]

# 添加一个新的工作表
new_sheet = wb.sheets.add('NewSheet')

# 删除工作表
wb.sheets['Sheet1'].delete()
```

### 3. 读取和写入单元格数据

```python
# 写入单个单元格
sheet.range('A1').value = 'Hello xlwings!'

# 读取单个单元格
value = sheet.range('A1').value
print(value)

# 写入一个区域
sheet.range('A2:C2').value = [1, 2, 3]

# 读取一个区域
values = sheet.range('A2:C2').value
print(values)

# 使用列表写入多行数据
data = [['Name', 'Age', 'City'],
        ['Alice', 25, 'New York'],
        ['Bob', 30, 'London']]
sheet.range('A4').value = data
```

### 4. 使用 Pandas DataFrame

```python
import pandas as pd

# 创建一个 Pandas DataFrame
df = pd.DataFrame({'Name': ['Charlie', 'David'],
                   'Age': [28, 35],
                   'City': ['Paris', 'Tokyo']})

# 将 DataFrame 写入 Excel
sheet.range('A7').value = df

# 从 Excel 读取数据到 DataFrame
df_from_excel = sheet.range('A7').expand('table').options(pd.DataFrame).value
print(df_from_excel)
```

### 5. 操作 Excel 对象

```python
# 获取单元格对象
cell = sheet.range('A1')

# 设置单元格格式
cell.font.bold = True
cell.color = (255, 0, 0)  # 红色

# 获取区域对象
rng = sheet.range('A1:C3')

# 设置区域边框
rng.api.Borders.LineStyle = 1  # 1 表示细实线
```

### 6. 自定义 Excel 函数 (UDFs)

xlwings 允许你使用 Python 编写自定义 Excel 函数。

*   **步骤 1:**  创建一个 Python 模块（例如 `myfunctions.py`）并编写函数。

    ```python
    # myfunctions.py
    import xlwings as xw

    @xw.func
    def my_sum(x, y):
        """Adds two numbers together."""
        return x + y
    ```

*   **步骤 2:**  在 Excel 中启用 xlwings 插件，并导入 Python 模块。  (具体步骤略，请参考 xlwings 官方文档)

*   **步骤 3:**  在 Excel 单元格中使用自定义函数。

    ```excel
    =my_sum(A1, B1)
    ```

### 7. 关闭 Excel 应用

```python
# 保存工作簿
# wb.save('output.xlsx')

# 关闭工作簿
wb.close()

# 退出 Excel 应用
app.quit()
```



### 8. 使用 `with ... as ...` 语句



- # 3. 本节犯错

- ## 3.1. 把功能体写到 try .. as 外

- ### 3.1.1. 报错代码

```python
    with xw.App(visible=False) as app:
        # 读取主工作表格
        try:
            # 打开主工作簿对象
            main_workbook = app.books.open(sub_mian_food_excel_file_path)
            print(f"Notice: 子工作表加载成功，文件路径: {sub_mian_food_excel_file_path}")
            # 轮询读取暂存表格数据行
            for row_index in range(1, read_temp_storage_workbook.sheet_by_index(0).nrows):
                # 读取行数据
                row_data = read_temp_storage_workbook.sheet_by_index(0).row_values(row_index)
                # 创建一个字典，用于存储列索引和列名的对应关系
                header_index = {name: idx for idx, name in enumerate(read_temp_storage_workbook_headers)}
                # 将日期分解为月和日
                year, month, day = row_data[header_index["日期"]].split("-")
                # 获取行中类别列类型单元中的类别名数据
                category_name = row_data[header_index["类别"]]
                # 获取行中品名列类型单元中的品名名数据
                product_name = row_data[header_index["品名"]]
                # 获取行中单位列类型单元中的单位名数据
                unit_name = row_data[header_index["单位"]]
                # 获取行中单价列类型单元中的单价名数据
                price = row_data[header_index["单价"]]
                # 获取行中数量列类型单元中的数量名数据
                quantity = row_data[header_index["数量"]]
                # 获取行中金额列单元中金额数据
                amount = row_data[header_index["金额"]]
                # 获取行中备注列单元中备注数据
                remark = row_data[header_index["备注"]]
                # 获取行中公司列单元中公司名数据
                company_name = row_data[header_index["公司"]]
                # 获取行中单名称列单元中单名数据
                single_name = row_data[header_index["单名"]]  
			# 查找对应的品名的 sheet（这块的缩进出现了问题导致不在try 作用域内操作）
			if product_name in [s.name for s in main_workbook.sheets]:
				sheet = main_workbook.sheets[product_name]
			else:
				print(f"未找到品名为 {product_name} 的sheet")
				return
```

<center><b>码：报错代码</b></center>

```bash
com_error: (-2147023174, 'The RPC server is unavailable.', None, None)
```

<center><b>码：报错信息</b></center>

说明此时 [main_workbook](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html) 的 COM 连接已经失效。

---

- ### 3.1.2. 可能原因

1. **Excel进程被异常关闭或崩溃**
    - 你手动或程序外部关闭了 Excel，或者 Excel 自己崩溃了。
2. **`with xw.App(...) as app:` 作用域外访问 workbook**
    - 离开 `with` 块后，[app](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html) 和所有 workbook/sheet 的 COM 通道会自动断开，之后再访问就会报这个错。
3. **多线程/异步操作**
    - 如果你在多线程或异步环境下跨线程访问 xlwings 对象，也会导致 COM 失效。
4. **Excel 进程假死或被杀死**
    - 比如你在任务管理器里结束了 Excel 进程。
5. **长时间未操作，COM 连接超时**
    - 很少见，但如果 Excel 长时间无响应，也可能断开。

---

- ### 3.1.3. 解决方法

- **所有 Excel 操作都必须在 [with xw.App(...) as app:](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html) 作用域内完成。**
- 不要在 `with` 块外部访问任何 workbook、sheet、range。
- 避免手动关闭 Excel 进程或让 Excel 崩溃。
- 避免多线程/异步环境下跨线程访问 xlwings 对象。
- 每次调试前，确保没有残留的 Excel 进程（可用 `taskkill /f /im excel.exe`）。

---

- ### 3.1.4. 代码结构建议

```python
with xw.App(visible=False) as app:

    main_workbook = app.books.open(sub_mian_food_excel_file_path)

    # ...所有对 main_workbook 的操作...

    # 不要离开 with 块后再访问 main_workbook
```

---

**总结：**

- 你的错误本质是 Excel 的 COM 通道断开，通常是因为 Excel 进程被关闭、崩溃，或你在 `with` 作用域外访问了 workbook。
- 保证所有 Excel 操作都在 `with` 作用域内完成，并避免外部关闭 Excel，即可避免此类错误。


- # 4. 本节内容


`with ... as ...` 语句是 Python 中用于管理资源的常用方法。它可以确保在使用完资源后，自动释放资源，即使在使用过程中发生异常。对于 `xlwings` 来说，可以使用 `with` 语句来管理 `App` 和 `Book` 对象，确保 Excel 应用和工作簿在使用完毕后被正确关闭。

**示例：**

```python
import xlwings as xw

def excel_operation_with_context_manager(filename="output.xlsx"):
    """
    演示使用 with ... as ... 语句来管理 xlwings 资源，
    确保 Excel 应用和工作簿在使用完毕后被正确关闭。
    """
    try:
        with xw.App(visible=True, add_book=False) as app:
            with app.books.add() as wb:
                # 获取当前活动工作表
                sheet = wb.sheets.active

                # 写入单元格
                sheet.range('A1').value = 'Hello xlwings with context manager!'

                # 保存工作簿
                wb.save(filename)

                print(f"Excel 文件 '{filename}' 创建成功！")

    except Exception as e:
        print(f"发生错误: {e}")

# 运行示例
excel_operation_with_context_manager()
```

**代码解释：**

1.  **`with xw.App(visible=True, add_book=False) as app:`**
    *   创建一个 `App` 对象，并将其赋值给变量 `app`。
    *   当 `with` 块中的代码执行完毕后（无论是正常结束还是发生异常），`App` 对象的 `__exit__` 方法会被自动调用，该方法会调用 `app.quit()`，确保 Excel 应用被正确关闭。
2.  **`with app.books.add() as wb:`**
    *   在 `App` 对象的上下文中，创建一个新的工作簿，并将其赋值给变量 `wb`。
    *   当内部 `with` 块中的代码执行完毕后，`Book` 对象的 `__exit__` 方法会被自动调用，该方法会调用 `wb.close()`，确保工作簿被正确关闭。
3.  **异常处理：**
    *   如果在使用过程中发生异常，`with` 语句仍然会确保资源被正确释放。`try...except` 块用于捕获并处理异常，但即使没有 `except` 块，`finally` 块（由 `with` 语句隐式提供）也会被执行。

**优点：**

*   **简洁：**  使用 `with` 语句可以减少代码量，使代码更易读。
*   **安全：**  确保资源在使用完毕后被正确释放，避免资源泄漏和潜在的冲突。
*   **可靠：**  即使在使用过程中发生异常，也能保证资源被正确释放。

**总结：**

使用 `with ... as ...` 语句是管理 xlwings 资源的推荐方法。它可以确保 Excel 应用和工作簿在使用完毕后被正确关闭，避免出现之前提到的问题。在编写 xlwings 代码时，应该尽量使用 `with` 语句来管理 `App` 和 `Book` 对象。




## 高级用法

*   **事件处理:**  xlwings 允许你捕获 Excel 事件，例如工作表更改、工作簿打开等，并执行相应的 Python 代码。
*   **Array Formulas:**  可以使用 Python 创建 Excel 数组公式。
*   **Excel 模板:**  可以使用 xlwings 填充 Excel 模板，生成报告等。
*   **部署:**  可以将 xlwings 应用部署到其他机器上，无需安装 Python。

- # 1. 得行号
- ## 1.1. 从上至下寻找不为空的第一行行号


- # 2. 得列号
- ## 2.1. 从左至右寻找不为空的第一列列号





## 使用总结

xlwings 是一个功能强大的 Python 库，可以方便地与 Excel 进行交互。它提供了简洁的 API，易于学习和使用，可以用于 Excel 自动化、数据分析、可视化等多种应用场景。

建议参考 xlwings 官方文档获取更详细的信息：[https://www.xlwings.org/](https://www.xlwings.org/)


**说明：**

*   我补充了 xlwings 的简介、安装方法、基本用法（创建 Excel 应用、操作工作表、读写单元格数据、使用 Pandas DataFrame、操作 Excel 对象、自定义 Excel 函数）和高级用法。
*   每个部分都提供了代码示例，方便你理解和使用。
*   最后，我建议参考 xlwings 官方文档获取更详细的信息。


好的，根据提供的 [[xlwings]] 笔记，我将 xlwings 库中 `App` 对象、`Book` 对象和 `Sheet` 对象常用的方法整理如下。



# 7. 参考链接
- https://docs.xlwings.org/en/stable/index.html
- 