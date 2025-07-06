
# PyQt4
- [1.1 Qt 简介 · 零基础学 qt4 编程 · 看云](https://www.kancloud.cn/wizardforcel/wudi-qt4/111155)



# PyQt5
- https://blog.csdn.net/weixin_63716012/article/details/140332104
- https://c.biancheng.net/view/9424.html
- https://geek-docs.com/pyqt5/pyqt5-top-tutorials/1007101_pyqt5_qboxlayout_class.html
- https://github.com/feiyangqingyun/qtkaifajingyan
## 一、[PyQt5](https://so.csdn.net/so/search?q=PyQt5&spm=1001.2101.3001.7020)介绍&开发环境安装&简单案例分析

### 1-1、PyQt5的介绍

**PyQt5是一个用于创建图形用户界面（GUI）的Python库。它是基于Qt库的，Qt是一个用于创建跨平台应用程序的C++库。PyQt5允许开发人员使用Python语言创建功能强大的应用程序。使用Python开发的优点是高效**

PyQt5包括了许多工具，允许开发人员创建多种不同类型的用户界面，如对话框，下拉菜单，工具栏，按钮，文本框等。它还支持使用鼠标和键盘进行交互，以及使用图像和声音等多媒体内容。**以下为详细介绍**：

- 基础组件：PyQt5包含了一系列基础组件，如按钮，文本框，标签，菜单栏，工具栏等，可以让开发人员快速创建用户界面。
- 交互：PyQt5支持鼠标和键盘交互，可以让开发人员创建具有各种交互功能的应用程序。
- 多媒体：PyQt5允许开发人员在用户界面中使用图像，音频，视频等多媒体内容，可以创建丰富多彩的应用程序。
- 跨平台：PyQt5是基于Qt库的，Qt是跨平台的，因此PyQt5也具有跨平台的优势，可以在Windows，MacOS和Linux等操作系统上运行。
- 代码生成器：PyQt5具有高效的代码生成器，可以使用Qt Designer快速创建用户界面，并将其导出为Python代码。
- 文档和社区：PyQt5具有丰富的文档和社区支持，可以帮助开发人员解决各种问题。
- 灵活性：PyQt5是一个高度灵活的工具，可以根据开发人员的需求进行自定义和扩展，以满足不同类型的项目需

**总的来说，PyQt5是一个功能强大，易于使用的工具，可以帮助开发人员创建高质量的图形用户界面。如果您正在寻找一种用于创建图形用户界面的Python库，那么PyQt5可能是一个不错的选择。**

### 1-2、开发环境安装

```c
# 先装好IDE，推荐Pycharm,之后安装python包和PyQt5包。
pip install python
pip install PyQt5
```

### 1-3、简单案例分析

```c
import sys
from PyQt5.QtWidgets import QApplication, QWidget

if __name__ == '__main__':
    # 创建Qt应用程序实例
    app = QApplication(sys.argv)

    # 创建一个QWidget对象，作为主窗口
    w = QWidget()
    w.resize(250, 150)
    w.move(300, 300)
    w.setWindowTitle('Simple')
    w.show()

    # 运行Qt应用程序
    sys.exit(app.exec_())

```

**以下是代码的详细解释**：

- import sys：导入Python标准库中的sys模块，以便访问命令行参数。
- from PyQt5.QtWidgets import QApplication, QWidget：导入QApplication和QWidget类，这是创建窗口所必需的两个类。
- app = QApplication(sys.argv)：创建QApplication实例，并传递命令行参数，它是整个Qt应用程序的核心。
- w = QWidget()：创建一个QWidget对象，它是窗口的根节点，也是整个窗口的主部分。
- w.resize(250, 150)：设置窗口的大小为250像素宽，150像素高。
- w.move(300, 300)：设置窗口的位置为(300, 300)像素。
- w.setWindowTitle(‘Simple’)：设置窗口的标题为"Simple"。
- w.show()：显示窗口。
- sys.exit(app.exec_())：运行Qt应用程序，并通过sys.exit()函数确保应用程序在退出时正常结束。

## 二、QT Designer

### 2-1、安装和配置

- **安装PyQt5-tools**：

```c
pip install pyqt5-tools
```

**安装之后可以在python目录下找到designer.exe, 我的文件在D:\Python\Python38\Lib\site-packages\qt5_applications\Qt\bin**  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f38f759baf3e2fa32842d707dea85223.png)

- **Pycharm配置**  
    File-》Settings-》Tools-》External Tools-》新建（点击➕）-》填写配置信息，保存（Program 设置designer的执行目录，Working directory设置为工程目录）  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1c6f700f2d52d1b75762ee8869ccd4bd.png)  
    $ P r o j e c t F i l e D i r ProjectFileDirProjectFileDir $ 代表的就是当下的工程目录。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f7fb151288c940823623ecc848dcfc38.png)

之后直接可以在Tools-》External Tools中看到QT Designer  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c36bb8e952f0ba8021c9910ff5970bdc.png)

### 2-2、QT Designer基础入门

**打开QT Designer后，我们先创建一个Main Window用来存放所有组件。**  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e469de0b7e25b7efa0f731f83eea83fd.png)  
**界面的简单介绍**

- 左侧为所有组件，包括按钮、文本框等
- 中间的框为工作界面
- 右侧有属性编辑器，当将一个组件拖至中间工作界面时，可以设置该组件的大小、位置等等属性。
- 编辑完成可以在菜单栏窗体的下拉菜单中，找到预览，即最终的展现形式，以及将界面转换为python预览、或者是c++预览。
- 设计完界面后，直接点击保存即可，以ui后缀格式的文件保存。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/74d1cd3d6227ad7c68b54f2989050049.png)  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6b861a61344b9676206f332b1aa6ad66.png)

### 2-3、ui文件转换为python文件

**方法一**：直接使用命令行转换，demo.ui为保存的ui名，demo.py为ui转换为python的文件。

```c
python -m PyQt5.uic.pyuic demo.ui -o demo.py
```

**转换为python的代码如下所示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/013147720959e9b05bfb7ba619955bb5.png)

## 三、PyQt5基本窗口控件
QMain Window、Qwidget、QDialog、Qlabel、Spacers、QTextEdit、QLineEdit、菜单、工具栏、

```ad-note
title:**回忆**
1. QMainWindow 只能做顶层窗口、QWidget即可做顶层窗口也可以作为子窗口(一个应用指南开启一个应用实例，但是窗口实例可以拥有多个)

```


### 3-0、QMain Window

**QMainWindow是Qt框架中的一个主窗口类，它提供了一个应用程序的主界面，可以包含菜单栏、工具栏、状态栏、中心窗口等各种窗口部件。在QMainWindow中，中心窗口是最重要的部分，它可以是任何Qt窗口部件，如QTextEdit、QTableView、QGraphicsView等。**

QMainWindow可以通过Qt Designer进行设计和布局，也可以通过代码进行创建和配置。在使用Qt Designer时，可以拖放各种窗口部件到QMainWindow中，然后通过属性编辑器进行属性设置。在使用代码时，可以通过构造函数或者成员函数进行设置。

**QMainWindow的一些常用成员函数包括**：

- setCentralWidget()：设置中心窗口部件
- setMenuBar()：设置菜单栏
- addToolBar()：添加工具栏
- statusBar()：获取状态栏
- show()：显示主窗口

>**总结**：QMainWindow是一个非常强大的窗口部件，它可以用于创建各种类型的应用程序界面，如主窗口应用程序、多文档应用程序等。我们通常创建的是这个窗口_

### 3-1、Qwidget

**QWidget**

- 是Qt框架中所有用户界面部件的基类，包括窗口、对话框、按钮、标签、文本框、图形视图等等。QWidget提供了一些基本的用户界面功能，例如绘制、事件处理、布局等。
- 在Qt中，所有的用户界面部件都是从QWidget派生而来的，这意味着QWidget提供了一个通用的接口，以便于在不同的用户界面部件之间共享代码和实现。同时，QWidget也提供了一些常用的属性和方法，例如size()、pos()、setWindowTitle()等，以便于管理和操作界面部件。
- 在创建自定义用户界面部件时，我们可以从QWidget派生出我们自己的部件类，并通过重载其成员函数来实现自定义行为。例如，我们可以通过重载QWidget的paintEvent()函数来绘制自己的部件，或者通过重载其mousePressEvent()函数来处理鼠标点击事件。

>**总结**：QWidget是Qt框架中所有用户界面部件的基类，提供了基本的用户界面功能，包括绘制、事件处理、布局等。它是Qt框架中非常重要和常用的部件之一，对于Qt开发者来说是必须要熟练掌握的。


```ad-question
title:**QMain Window、Qwidget、QDialog的区别**
QWidget是Qt框架中所有用户界面部件的基类，包括窗口、对话框、按钮、标签、文本框、图形视图等等，它提供了基本的用户界面功能，例如绘制、事件处理、布局等。而QMainWindow是QWidget的子类，是Qt框架中的一个主窗口类，它提供了一个应用程序的主界面，可以包含菜单栏、工具栏、状态栏、中心窗口等各种窗口部件。具体来说，**QWidget与QMainWindow的区别如下**：

- **功能不同** ：QWidget提供了基本的用户界面功能，而QMainWindow提供了应用程序主窗口的各种功能，例如菜单栏、工具栏、状态栏等。
- **布局不同** ：在QWidget中，需要通过布局管理器来管理部件的布局，而在QMainWindow中，布局管理器一般用于管理中心窗口的布局，其他部件则通过设置位置和大小来进行布局。
- **层次结构不同** ：QMainWindow作为应用程序主窗口，它是顶层窗口，而QWidget可以是顶层窗口或其他窗口的子窗口。
- **创建方式不同** ：QWidget可以作为独立窗口创建，也可以作为其他窗口的子窗口创建，而QMainWindow只能作为应用程序主窗口创建。

>**总结**：QWidget和QMainWindow都是Qt框架中非常重要的用户界面部件，用于创建不同类型的界面。QWidget提供了基本的用户界面功能，适用于创建各种类型的窗口和控件，而QMainWindow则提供了应用程序主窗口的各种功能，适用于创建包含菜单栏、工具栏、状态栏等的应用程序主窗口。



**QDialog**： 是对话窗口的基类，没有菜单栏、工具栏、状态栏。  
**QMainWindow**： 可以包含菜单栏、工具栏、状态栏和标题栏，是最常见的形式。  
**QWidget**： 不确定窗口的用途，就使用Qwidget。
```



### 3-3、Spacers控件

**PyQt中的Spacer控件是一种用于布局的空白控件**。

- Spacer控件可以帮助您在布局中创建空白区域，以便在界面上分隔其他控件，或者在其他控件周围留出空白区域。 Spacer控件的大小可以通过设置其大小策略（size policy）来控制。
    
- Spacer控件有两种类型：水平（QSpacerItem）和垂直（QSpacerItem）。您可以使用QHBoxLayout或QVBoxLayout将Spacer控件添加到布局中。在添加Spacer控件时，您可以指定其最小大小、最大大小和首选大小，以及其大小策略。
    

### 3-4、Qlabel、QLineEdit

**QLabel和QLineEdit都是Qt框架中常用的用户界面控件，用于在图形用户界面（GUI）中显示文本信息和接受用户输入。以下是它们的介绍**：

#### 3-4-1、QLabel介绍

**QLabel**：

QLabel是一个显示文本或图像的控件，它通常被用于显示静态文本信息。可以通过设置其文本、字体、颜色、对齐方式等属性来自定义标签的样式和布局。可以将QLabel放置在主窗口、对话框或其他控件上，以便在应用程序中提供帮助文本、说明、状态消息等。

**方法**：

- setText(text): 设置文本内容
- setPixmap(pixmap): 设置图像内容
- setAlignment(alignment): 设置文本或图像的对齐方式
- setWordWrap( on): 当文本过长时是否自动换行
- setFixedSize(width, height): 设置控件的固定大小
- setStyleSheet(styleSheet): 设置控件的样式表

**属性**：

- text(): 返回控件的文本内容
- pixmap(): 返回控件的图像内容
- alignment(): 返回控件的对齐方式
- wordWrap(): 返回控件是否自动换行
- font(): 返回控件的字体
- color(): 返回控件的颜色

#### 3-4-2、QLabel简单案例分析

**以下是一个简单的例子，展示如何创建一个QLabel控件并设置它的一些属性**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel
from PyQt5.QtGui import QPixmap, QFont
from PyQt5.QtCore import Qt

class Example(QWidget):

    def __init__(self):
        super().__init__()

        self.initUI()

    def initUI(self):

        # 创建一个QLabel控件并设置文本内容
        label1 = QLabel('Hello, PyQt5!', self)
        label1.move(15, 10)

        # 创建一个QLabel控件并设置图像内容
        label2 = QLabel(self)
        pixmap = QPixmap('蓝色背景光柱.png')
        label2.setPixmap(pixmap)
        label2.move(15, 40)

        # 设置对齐方式
        label3 = QLabel(self)
        label3.setText('Align Center')
        label3.setAlignment(Qt.AlignCenter)
        label3.move(15, 160)

        # 设置字体和颜色
        label4 = QLabel(self)
        label4.setText('Font and Color')
        label4.setFont(QFont('Arial', 20))
        label4.setStyleSheet('color: red')
        label4.move(15, 190)

        self.setGeometry(300, 300, 250, 250)
        self.setWindowTitle('QLabel Example')
        self.show()

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())

```

#### 3-4-3、QLabel案例：使用信号（详细介绍请见第六章）

**以下是QLabel控件的常用信号**：

- linkActivated: 当控件中包含超链接时，用户单击链接时触发此信号。
- linkHovered: 当用户将鼠标悬停在超链接上时，触发此信号。
- linkPressed: 当用户按下并释放鼠标按钮时，同时鼠标位于超链接上时，触发此信号。

**以下是一个简单的例子，演示如何使用linkActivated信号**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QLabel
from PyQt5.QtGui import QDesktopServices
from PyQt5.QtCore import QUrl

class Example(QLabel):

    def __init__(self):
        super().__init__()

        self.setText('<a href="https://www.google.com">Google</a>')
        self.setOpenExternalLinks(True)
        # 绑定到指定的事件函数。
        # 点击后触发打开链接！
        self.linkActivated.connect(self.openLink)

    def openLink(self, url):
        QDesktopServices.openUrl(QUrl(url))

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    ex.show()
    sys.exit(app.exec_())

```

#### 3-4-4、QLineEdit介绍

**QLineEdit**：  
QLineEdit是一个用于接收用户输入的单行文本编辑控件，它允许用户输入和编辑文本信息。可以设置QLineEdit的输入格式，例如只允许输入数字、字母或特定字符，或者限制输入的最大长度。可以使用信号和槽机制来处理用户输入的文本，以便在应用程序中执行特定的操作或验证用户输入的有效性。

_总的来说，QLabel和QLineEdit是Qt框架中非常实用的控件，它们可以为应用程序提供各种形式的文本输入和输出。_

**下图为添加了Qlabel和QLineEdit的FormLayput**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c8aca14991b8b7f84d9256088814c39c.png)  
**下面是QLineEdit控件的一些常用属性和方法**：

- text()：获取或设置控件的文本内容
- setText(text)：设置控件的文本内容
- clear()：清空控件的文本内容
- setAlignment(alignment)：设置文本的对齐方式，alignment可以是Qt.AlignLeft、Qt.AlignRight、Qt.AlignCenter等值之一
- setPlaceholderText(text)：设置控件的占位符文本，当控件没有内容时显示的文本
- setReadOnly(readOnly)：设置控件是否为只读模式
- setValidator(validator)：设置控件的输入验证器，用于限制用户输入的内容
- textChanged.connect(slot)：文本改变时的信号，连接到相应的槽函数

#### 3-4-5、QLineEdit简单案例

**下面是一个简单的例子，演示如何创建一个QLineEdit控件并将其添加到窗口中**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QLineEdit, QVBoxLayout

class Example(QWidget):

    def __init__(self):
        super().__init__()

        self.initUI()

    def initUI(self):

        # 创建QLabel控件和QLineEdit控件
        nameLabel = QLabel('Name:')
        nameEdit = QLineEdit()
		
		# QLineEdit控件有三种回显模式，用于指定文本框中的内容如何显示：
		# Normal：默认的回显模式，输入的文本会直接显示在文本框中。
		# Password：将输入的文本用星号或其他字符替代，用于密码输入等场景。可以使用setEchoChar(char)方法来指定用于替代文本的字符，默认情况下使用星号。
		# NoEcho：不显示输入的文本，用于输入敏感信息等场景。可以使用setEchoMode(QLineEdit.NoEcho)方法来指定回显模式为NoEcho。
		
		# 下边为示例：
		# 设置回显模式为密码模式
        nameEdit.setEchoMode(QLineEdit.Password)

        # 创建垂直布局，并将控件添加到布局中
        vbox = QVBoxLayout()
        vbox.addWidget(nameLabel)
        vbox.addWidget(nameEdit)

        # 设置窗口布局和大小
        self.setLayout(vbox)
        self.setGeometry(300, 300, 250, 150)
        self.setWindowTitle('QLineEdit Example')
        self.show()

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())
```

#### 3-4-6、QLineEdit案例：添加校验器

**限制输入：QlineEdit控件添加校验器**  
QLineEdit控件可以使用校验器来限制输入，常见的校验器有QIntValidator（整数校验器）、QDoubleValidator（浮点数校验器）和QRegExpValidator（正则表达式校验器）等。

**下面是一个使用QIntValidator校验器和QFormLayout表单布局的示例代码，用于限制用户只能输入整数：**

```c

import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QLineEdit, QFormLayout, QIntValidator

class Example(QWidget):

    def __init__(self):
        super().__init__()

        self.initUI()

    def initUI(self):

        # 创建QLabel控件和QLineEdit控件
        nameLabel = QLabel('Name:')
        nameEdit = QLineEdit()

        # 创建整数校验器，并将其应用于QLineEdit控件
        intValidator = QIntValidator()
        nameEdit.setValidator(intValidator)

        # 创建表单布局，并将控件添加到布局中
        formLayout = QFormLayout()
        formLayout.addRow(nameLabel, nameEdit)

        # 设置窗口布局和大小
        self.setLayout(formLayout)
        self.setGeometry(300, 300, 250, 150)
        self.setWindowTitle('QLineEdit Example')
        self.show()

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())

```

**以下为输出的图示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1f9dec67ce76b2d875cd9cdd4010f0aa.png)

_在这个例子中，我们创建了一个整数校验器，并将其应用于QLineEdit控件，这样用户只能输入整数。然后，我们使用QFormLayout表单布局来组织控件，并将控件添加到布局中。最后，设置窗口布局和大小，并显示窗口。  
使用校验器可以有效地限制用户的输入，避免非法输入导致程序崩溃或产生错误结果。同时，QFormLayout表单布局也可以方便地组织控件，使界面更加美观和易用。_

#### 3-4-7、QLineEdit综合案例

**下面是一个使用QLineEdit控件的综合案例，包含以下内容**：

- 创建一个主窗口，并在窗口中放置一个QLineEdit控件和一个按钮；
- 限制QLineEdit控件的输入为浮点数，并设置默认值；
- 点击按钮时，获取QLineEdit控件中的值，并进行简单的计算，并将结果显示在消息框中。

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QLabel, QLineEdit, QPushButton, QMessageBox, QVBoxLayout, QWidget
from PyQt5.QtGui import QDoubleValidator

class Example(QMainWindow):

    def __init__(self):
        super().__init__()

        self.initUI()

    def initUI(self):

        # 创建QLabel控件和QLineEdit控件
        self.label = QLabel('Enter a number:', self)
        self.lineedit = QLineEdit(self)

        # 设置默认值和浮点数校验器
        self.lineedit.setText('0.0')
        validator = QDoubleValidator()
        self.lineedit.setValidator(validator)

        # 创建QPushButton控件
        self.button = QPushButton('Calculate', self)
        self.button.setToolTip('Click to calculate the square of the input value')
        self.button.clicked.connect(self.calculate)

        # 设置控件布局
        vbox = QVBoxLayout()
        vbox.addWidget(self.label)
        vbox.addWidget(self.lineedit)
        vbox.addWidget(self.button)

        widget = QWidget()
        widget.setLayout(vbox)
        self.setCentralWidget(widget)

        # 设置窗口属性
        self.setGeometry(300, 300, 250, 150)
        self.setWindowTitle('QLineEdit Example')
        self.show()

    def calculate(self):

        # 获取QLineEdit控件中的值
        value = self.lineedit.text()

        # 如果值为空，则弹出警告框
        if not value:
            QMessageBox.warning(self, 'Warning', 'Please enter a number.')
            return

        # 进行计算，并显示结果
        try:
            result = float(value) ** 2
            QMessageBox.information(self, 'Result', f'The square of {value} is {result}.')
        except ValueError:
            QMessageBox.warning(self, 'Warning', 'Please enter a valid number.')

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())
```

**输出界面如下**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9f7b4cf840463d8b6e3d09c68220a577.png)

_在这个例子中，我们创建了一个主窗口，并在窗口中放置了一个QLineEdit控件和一个按钮。我们使用QDoubleValidator校验器来限制QLineEdit控件的输入为浮点数，并设置了默认值为0.0。在点击按钮时，我们获取QLineEdit控件中的值，并进行简单的计算，并将结果显示在消息框中。  
如果输入的值为空，我们会弹出一个警告框提示用户输入一个数字；如果输入的不是数字，我们也会弹出一个警告框提示用户输入一个有效的数字。_

### 3-5、添加伙伴关系Qlabel、QLineEdit

**在Qt Designer中，添加伙伴关系可以使得某些控件与标签或其他控件关联起来，从而使得用户输入更加方便和明确。以下是添加伙伴关系的步骤**：

- 打开Qt Designer并加载您的UI文件。
- 从左侧的工具栏中选择“标签”（QLabel）或“行编辑器”（QLineEdit）控件，然后将其拖放到您想要添加伙伴关系的控件旁边。
- 选中要与标签或行编辑器关联的控件。可以在属性编辑器中选择“伙伴”属性。
- 单击“伙伴”属性旁边的“…”按钮，然后选择要添加为伙伴的标签或行编辑器。
- 保存您的UI文件并重新加载应用程序以查看效果。
- 添加伙伴关系后，用户可以使用标签或行编辑器轻松地标识与控件关联的文本或标签，并且可以通过快捷键或键盘导航更轻松地访问控件。

**具体步骤**：

- 在Qlabel后加上(&B)。
- 将QLabel与后边的文本输入框添加伙伴关系
- 之后保存，即可使用alt+B访问到文本框  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5db8a1bac9c714e045bf8b13a94a92fb.png)  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e08647b09ad2599e4f84379c67f7ba88.png)  
    **代码示例**：  
    可以使用setBuddy()方法来将一个QLabel控件和一个QLineEdit控件绑定成伙伴关系。这样在用户按下Alt键并激活QLabel控件时，可以将焦点自动转移到与之关联的QLineEdit控件中。

**下面是一个简单的例子，演示如何将一个QLabel控件和一个QLineEdit控件绑定成伙伴关系，并将它们添加到一个QGridLayout布局中**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QLabel, QLineEdit, QGridLayout, QWidget

class Example(QWidget):
    
    def __init__(self):
        super().__init__()
        
        self.initUI()
        
        
    def initUI(self):
        
        # 创建QLabel和QLineEdit控件，并将它们绑定成伙伴关系
        nameLabel = QLabel('Name:')
        nameEdit = QLineEdit()
        nameLabel.setBuddy(nameEdit)

        ageLabel = QLabel('Age:')
        ageEdit = QLineEdit()
        ageLabel.setBuddy(ageEdit)
        
        # 创建QGridLayout布局，并将控件添加到其中
        grid = QGridLayout()
        grid.addWidget(nameLabel, 0, 0)
        grid.addWidget(nameEdit, 0, 1)
        grid.addWidget(ageLabel, 1, 0)
        grid.addWidget(ageEdit, 1, 1)
        
        # 设置窗口布局和大小
        self.setLayout(grid)
        self.setGeometry(300, 300, 250, 150)
        self.setWindowTitle('Buddy Example')
        self.show()
        
        
if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())
```

**如下图所示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2ea3ce58b036ff0208f3b0eaf8f43eb6.png)

_在这个例子中，我们创建了两个QLabel控件和两个QLineEdit控件，并将它们绑定成了伙伴关系。然后我们创建了一个QGridLayout布局，并将这些控件添加到布局中。最后，我们将布局设置为窗口的布局，并显示窗口。_

### 3.7. QSpinBox 介绍

```ad-note
title:**快速回忆**
- `valueChanged`时比如如果是从4变动到5，那么此时你在`slot函数`中调用`value()`方法时获取的值是5，也就是说获取的是变动之后的值
```

**QSpinBox** 是 PyQt5 中的一个计数器控件，它提供了一个可供用户编辑和选择数字的文本框，用户可以通过点击上下箭头或直接输入数字来更改文本框中的值。`QSpinBox` 常用于需要用户输入数值范围的场景，例如年龄、数量、百分比等。

**QSpinBox 控件的常用属性和方法包括：**

*   `value()`: 返回当前计数器的值。
*   `setValue(value)`: 设置计数器的值。
*   `minimum()`: 返回计数器的最小值。
*   `setMinimum(value)`: 设置计数器的最小值。
*   `maximum()`: 返回计数器的最大值。
*   `setMaximum(value)`: 设置计数器的最大值。
*   `singleStep()`: 返回计数器的单步增量。
*   `setSingleStep(value)`: 设置计数器的单步增量。
*   `prefix()`: 返回计数器的前缀。
*   `setPrefix(prefix)`: 设置计数器的前缀。
*   `suffix()`: 返回计数器的后缀。
*   `setSuffix(suffix)`: 设置计数器的后缀。
*   `valueChanged[int].connect(slot)`: 值改变时的信号，连接到相应的槽函数。

**简单案例分析：**

以下示例程序创建了一个带有计数器控件、标签和重置按钮的窗口。当计数器的值更改时，标签的文本会更新为当前计数器的值。当用户点击重置按钮时，计数器的值将重置为默认值 0。

```python
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QSpinBox, QPushButton, QVBoxLayout, QHBoxLayout
from PyQt5.QtCore import Qt

class CounterDemo(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        # 创建一个垂直布局
        vlayout = QVBoxLayout()

        # 创建一个标签和计数器控件，并添加到垂直布局中
        self.label = QLabel('Value: 0')
        self.spinbox = QSpinBox()
        self.spinbox.setMinimum(0)
        self.spinbox.setMaximum(100)
        self.spinbox.setSingleStep(1)
        self.spinbox.valueChanged[int].connect(self.onSpinBoxValueChanged)
        vlayout.addWidget(self.label)
        vlayout.addWidget(self.spinbox)

        # 创建一个水平布局，并添加一个重置按钮
        hlayout = QHBoxLayout()
        reset_btn = QPushButton('Reset')
        reset_btn.clicked.connect(self.onResetClicked)
        hlayout.addWidget(reset_btn)
        hlayout.addStretch(1)
        vlayout.addLayout(hlayout)

        # 设置窗口的布局
        self.setLayout(vlayout)

        # 设置窗口的标题和大小
        self.setWindowTitle('Counter Demo')
        self.resize(300, 200)

    def onSpinBoxValueChanged(self, newValue):
        # 当计数器的值改变时更新标签的文本
        self.label.setText(f'Value: {newValue}')

    def onResetClicked(self):
        # 点击重置按钮时将计数器的值重置为默认值0
        self.spinbox.setValue(0)

if __name__ == '__main__':
    app = QApplication(sys.argv)
    demo = CounterDemo()
    demo.show()
    sys.exit(app.exec_())
```

**输出如下图所示：**

![QSpinBox 示例](https://i-blog.csdnimg.cn/blog_migrate/d66d6874dc940bb438cdd22a126a245e.png)

在这个例子中，您可以通过点击上下箭头或直接输入数字来更改计数器的值，也可以点击重置按钮将计数器的值重置为默认值 0。

```ad-note
title:**与前文两个控件的对比**
1. **控件的性质：** `QSpinBox` 是一种用于数值输入的控件，与 `QLabel`（显示文本）、`QLineEdit`（单行文本输入）等控件属于同一层级，都是用于构建用户界面的基本元素。
2. **内容组织结构：** 笔记中，"三、PyQt5基本窗口控件" 这一部分主要介绍 PyQt5 中常用的基本控件，`QSpinBox` 显然应该归类于此。
3. **与 `QLineEdit` 的关联：** 笔记中提到了 `QLineEdit` 可以添加校验器来限制输入，而 `QSpinBox` 本身就具有数值范围限制的功能，两者在输入控制方面有一定的关联性，因此放在一起介绍更合适。

```

#### 3-6-1、QTextEdit简单介绍

**QTextEdit是一个可以用于显示和编辑富文本的多行文本编辑控件。它可以用于创建编辑器、日记、HTML文本查看器等。**

QTextEdit可以在文本中插入多媒体内容，如图像、超链接、HTML表格等，并且可以在文本中使用样式来设置字体、颜色、背景、对齐等。QTextEdit还支持拼写检查、撤销/重做、自动缩进、文本选择等基本编辑功能。

**下面是一个简单的使用QTextEdit的例子**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QAction, QTextEdit, QFileDialog
from PyQt5.QtGui import QIcon

class Example(QMainWindow):

    def __init__(self):
        super().__init__()

        self.initUI()

    def initUI(self):

        # 创建QTextEdit控件
        self.textedit = QTextEdit(self)
        self.setCentralWidget(self.textedit)

        # 创建菜单栏
        menubar = self.menuBar()

        # 创建文件菜单
        filemenu = menubar.addMenu('File')

        # 创建“打开”操作
        openact = QAction(QIcon('open.png'), 'Open', self)
        openact.setShortcut('Ctrl+O')
        openact.triggered.connect(self.openFile)
        filemenu.addAction(openact)

        # 创建“保存”操作
        saveact = QAction(QIcon('save.png'), 'Save', self)
        saveact.setShortcut('Ctrl+S')
        saveact.triggered.connect(self.saveFile)
        filemenu.addAction(saveact)

        # 设置窗口属性
        self.setGeometry(300, 300, 350, 250)
        self.setWindowTitle('QTextEdit Example')
        self.show()

    def openFile(self):

        # 打开文件对话框
        filename = QFileDialog.getOpenFileName(self, 'Open File')[0]

        # 如果选择了文件，则读取文件内容到QTextEdit控件中
        if filename:
            with open(filename, 'r') as f:
                text = f.read()
            self.textedit.setText(text)

    def saveFile(self):

        # 打开文件对话框
        filename = QFileDialog.getSaveFileName(self, 'Save File')[0]

        # 如果选择了文件，则将QTextEdit控件中的内容保存到文件中
        if filename:
            with open(filename, 'w') as f:
                f.write(self.textedit.toPlainText())

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())
```

**输出界面如下图所示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3a384be062576a3ef27303726337571c.png)

_在这个例子中，我们创建了一个主窗口，并在窗口中放置了一个QTextEdit控件。我们使用菜单栏来创建“打开”和“保存”操作，当用户点击对应的菜单项时，我们会打开文件对话框，让用户选择要打开或保存的文件。如果选择了文件，则会读取文件内容到QTextEdit控件中，或将QTextEdit控件中的内容保存到文件中。_

#### 3-6-2、QTextEdit综合案例

**以下是一个更综合的使用QTextEdit的例子，实现了一个简单的文本编辑器，并包括了多个功能：**

- 打开、保存文件
- 新建文件
- 剪切、复制、粘贴、撤销、重做
- 设置字体、颜色、对齐方式
- 显示当前文档中的字数和行数

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QAction, QTextEdit, QFileDialog, QFontDialog, QColorDialog
from PyQt5.QtGui import QIcon, QTextCursor, QTextCharFormat
from PyQt5.QtCore import Qt

class Example(QMainWindow):

    def __init__(self):
        super().__init__()

        self.initUI()

    def initUI(self):

        # 创建QTextEdit控件
        self.textedit = QTextEdit(self)
        self.setCentralWidget(self.textedit)

        # 创建菜单栏
        menubar = self.menuBar()

        # 创建文件菜单
        filemenu = menubar.addMenu('File')

        # 创建“新建”操作
        newact = QAction(QIcon('new.png'), 'New', self)
        newact.setShortcut('Ctrl+N')
        newact.triggered.connect(self.newFile)
        filemenu.addAction(newact)

        # 创建“打开”操作
        openact = QAction(QIcon('open.png'), 'Open', self)
        openact.setShortcut('Ctrl+O')
        openact.triggered.connect(self.openFile)
        filemenu.addAction(openact)

        # 创建“保存”操作
        saveact = QAction(QIcon('save.png'), 'Save', self)
        saveact.setShortcut('Ctrl+S')
        saveact.triggered.connect(self.saveFile)
        filemenu.addAction(saveact)

        # 创建编辑菜单
        editmenu = menubar.addMenu('Edit')

        # 创建“剪切”操作
        cutact = QAction(QIcon('cut.png'), 'Cut', self)
        cutact.setShortcut('Ctrl+X')
        cutact.triggered.connect(self.textedit.cut)
        editmenu.addAction(cutact)

        # 创建“复制”操作
        copyact = QAction(QIcon('copy.png'), 'Copy', self)
        copyact.setShortcut('Ctrl+C')
        copyact.triggered.connect(self.textedit.copy)
        editmenu.addAction(copyact)

        # 创建“粘贴”操作
        pasteact = QAction(QIcon('paste.png'), 'Paste', self)
        pasteact.setShortcut('Ctrl+V')
        pasteact.triggered.connect(self.textedit.paste)
        editmenu.addAction(pasteact)

        # 创建“撤销”操作
        undoact = QAction(QIcon('undo.png'), 'Undo', self)
        undoact.setShortcut('Ctrl+Z')
        undoact.triggered.connect(self.textedit.undo)
        editmenu.addAction(undoact)

        # 创建“重做”操作
        redoact = QAction(QIcon('redo.png'), 'Redo', self)
        redoact.setShortcut('Ctrl+Y')
        redoact.triggered.connect(self.textedit.redo)
        editmenu.addAction(redoact)

        # 创建格式菜单
        formatmenu = menubar.addMenu('Format')

        # 创建“字体”操作
        fontact = QAction(QIcon('font.png'), 'Font', self)
        fontact.setShortcut('Ctrl+F')
        fontact.triggered.connect(self.setFont)
        formatmenu.addAction(fontact)


        # 创建“颜色”
        coloract = QAction(QIcon('color.png'), 'Color', self)
        coloract.setShortcut('Ctrl+Shift+C')
        coloract.triggered.connect(self.setColor)
        formatmenu.addAction(coloract)

        # 创建“左对齐”操作
        leftact = QAction(QIcon('left.png'), 'Align Left', self)
        leftact.setShortcut('Ctrl+L')
        leftact.triggered.connect(lambda: self.setAlignment(Qt.AlignLeft))
        formatmenu.addAction(leftact)

        # 创建“居中对齐”操作
        centeract = QAction(QIcon('center.png'), 'Align Center', self)
        centeract.setShortcut('Ctrl+E')
        centeract.triggered.connect(lambda: self.setAlignment(Qt.AlignCenter))
        formatmenu.addAction(centeract)

        # 创建“右对齐”操作
        rightact = QAction(QIcon('right.png'), 'Align Right', self)
        rightact.setShortcut('Ctrl+R')
        rightact.triggered.connect(lambda: self.setAlignment(Qt.AlignRight))
        formatmenu.addAction(rightact)

        # 创建状态栏，显示行数和字数
        self.statusBar().showMessage('Lines: 1, Words: 0')
        self.textedit.textChanged.connect(self.updateStatus)

        self.setGeometry(300, 300, 800, 600)
        self.setWindowTitle('Text Editor')
        self.show()

    def newFile(self):
        # 新建文件
        self.textedit.clear()

    def openFile(self):
        # 打开文件
        filename, _ = QFileDialog.getOpenFileName(self, 'Open File', '', 'Text Files (*.txt);;All Files (*)')
        if filename:
            with open(filename, 'r') as f:
                self.textedit.setText(f.read())

    def saveFile(self):
        # 保存文件
        filename, _ = QFileDialog.getSaveFileName(self, 'Save File', '', 'Text Files (*.txt);;All Files (*)')
        if filename:
            with open(filename, 'w') as f:
                f.write(self.textedit.toPlainText())

    def setFont(self):
        # 设置字体
        font, ok = QFontDialog.getFont(self.textedit.currentFont(), self)
        if ok:
            self.textedit.setCurrentFont(font)

    def setColor(self):
        # 设置颜色
        color = QColorDialog.getColor(self.textedit.textColor(), self)
        if color.isValid():
            self.textedit.setTextColor(color)

    def setAlignment(self, alignment):
        # 设置对齐方式
        self.textedit.setAlignment(alignment)

    def updateStatus(self):
        # 更新状态栏
        cursor = self.textedit.textCursor()
        lines = self.textedit.toPlainText().count('\n') + 1
        words = len(self.textedit.toPlainText().split())
        self.statusBar().showMessage(f'Lines: {lines}, Words: {words}')


if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())
```

**生成界面如下**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c3bf53e49c999e4bdb777ad114935e7b.png)

### 3-7、QDialog介绍

#### 3-7-1、QDialog简单介绍

**QDialog是PyQt5中常用的对话框窗口，它是QWidget的子类，用于在应用程序中显示各种对话框，例如询问用户是否要保存文件，输入一些数据，或显示一些信息等。QDialog提供了一些方便的功能，使得它易于使用，例如**：

- 可以设置对话框的标题、大小、位置、模态性等属性；
- 可以添加各种控件，例如标签、按钮、文本框、列表框等；
- 可以捕获对话框关闭事件和其他事件，以便在适当的时候做出响应；
- 可以返回一些数据或响应用户的操作。

**属性**  
**以下是一些常用的QDialog属性**：

- windowTitle：对话框的标题。
- windowIcon：对话框的图标。
- sizeGripEnabled：是否显示调整大小的手柄，默认为False。
- layout：对话框的布局管理器，用于控制对话框内部控件的位置和大小。
- modal：是否将对话框设置为模态，即禁止用户与其他窗口交互，直到对话框被关闭，默认为True。
- result：对话框的返回值，通常用于表示用户的操作或输入。如果对话框是通过exec_()方法调用的，则返回值是对话框的退出码（通常是QDialog.Accepted或QDialog.Rejected）；如果对话框是通过show()方法调用的，则返回值始终是None。
- sizeHint：对话框的推荐大小。

**方法  
以下是一些常用的QDialog方法**：

- exec_()：将对话框设置为模态并运行对话框的事件循环，直到对话框被关闭。此方法通常用于从对话框中获取一些数据或响应用户的操作。
- show()：显示对话框，但不将其设置为模态。此方法通常用于显示一些信息或提供一些选项。
- done(int result)：设置对话框的返回值，并关闭对话框。此方法通常在用户进行某些操作后调用，以便通知调用方对话框的结果。
- accept()：设置对话框的返回值为QDialog.Accepted，并关闭对话框。此方法通常在用户确认某些操作后调用，以便通知调用方对话框的结果。
- reject()：设置对话框的返回值为QDialog.Rejected，并关闭对话框。此方法通常在用户取消某些操作后调用，以便通知调用方对话框的结果。  
    除了上述方法外，QDialog还提供了一些其他方法，例如resize()、move()、close()、setVisible()等，这些方法与QWidget类似，用于设置对话框的大小、位置、可见性等。

**信号  
以下是一些常用的QDialog信号**：

- finished(int result)：当对话框关闭并且返回值已经设置时发出。参数result表示对话框的返回值。
- accepted()：当用户确认某些操作并调用accept()方法时发出。
- rejected()：当用户取消某些操作并调用reject()方法时发出。

**除了基本属性、方法和信号之外，QDialog还具有以下一些特殊的属性、方法和信号：**

- acceptMode：对话框的接受模式，可以是QFileDialog.AcceptOpen（打开文件）、QFileDialog.AcceptSave（保存文件）或QFileDialog.AcceptSave（选择文件夹）。
- rejectAction：当用户按下Esc键或者点击“取消”按钮时，对话框执行的操作。默认情况下，对话框将执行reject()方法并关闭。
- setButtonLayout(list)：设置对话框底部的按钮布局。参数list应该是一个QDialogButtonBox中定义的一组按钮类型，例如QDialogButtonBox.Ok | QDialogButtonBox.Cancel。
- open()：将对话框设置为模态并运行对话框的事件循环，直到对话框被关闭。此方法与exec_()方法类似，但可以方便地打开多个对话框。
- resizeEvent(event)：当对话框的大小改变时发出。可以重写此方法来执行一些特定的操作。

#### 3-7-2、不同类型QDialog介绍

**QDialog是Qt中用于显示对话框的基类。根据对话框的用途和外观，可以将QDialog分为不同的类型，包括以下几种：**

- 普通对话框(QDialog)：最基本的对话框类型，用于显示消息、获取输入、提供选项等。它可以通过设置各种属性和使用布局管理器来控制对话框的大小、位置和内容。
- 文件对话框(QFileDialog)：用于选择文件或文件夹的对话框。可以使用QFileDialog的静态方法创建各种类型的文件对话框，例如打开文件对话框、保存文件对话框、选择文件夹对话框等。
- 字体对话框(QFontDialog)：用于选择字体和字号的对话框。可以使用QFontDialog的静态方法创建字体对话框。
- 颜色对话框(QColorDialog)：用于选择颜色的对话框。可以使用QColorDialog的静态方法创建颜色对话框。
- 输入对话框(QInputDialog)：用于获取用户输入的对话框。可以使用QInputDialog的静态方法创建各种类型的输入对话框，例如文本输入对话框、整数输入对话框、浮点数输入对话框等。
- 消息框(QMessageBox)：用于显示消息和提供选项的对话框。可以使用QMessageBox的静态方法创建各种类型的消息框，例如信息框、警告框、错误框、询问框等。
- 鼠标指针对话框(QCursor)：用于显示不同类型的鼠标指针。可以使用QCursor的静态方法创建各种类型的鼠标指针对话框，例如箭头、十字形、等待指针等。

**除了上述几种类型的QDialog之外，还可以通过自定义QDialog来创建各种特定的对话框。自定义对话框可以包含任意数量和类型的控件，可以根据具体需求进行设计和实现。在自定义对话框中，可以使用QDialog提供的属性、方法和信号，也可以使用其他Qt控件和类库中的各种功能。**

#### 3-7-3、消息框(QMessageBox)（最常用）

**消息框(QMessageBox)**：用于显示消息和提供选项的对话框。可以使用QMessageBox的静态方法创建各种类型的消息框，例如信息框、警告框、错误框、询问框等。

```c
from PyQt5.QtWidgets import QApplication, QWidget, QMessageBox, QVBoxLayout, QHBoxLayout, QPushButton

class MainWindow(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle('QMessageBox案例')
        self.setGeometry(100, 100, 400, 200)

        # 创建布局管理器和控件
        layout = QVBoxLayout()
        self.label = QLabel('请选择一种操作：')
        self.button_ok = QPushButton('确定')
        self.button_ok.clicked.connect(self.show_confirm_dialog)
        self.button_cancel = QPushButton('取消')
        self.button_cancel.clicked.connect(self.close)

        # 将控件添加到布局管理器中
        h_layout = QHBoxLayout()
        h_layout.addWidget(self.button_ok)
        h_layout.addWidget(self.button_cancel)

        layout.addWidget(self.label)
        layout.addLayout(h_layout)

        # 设置窗口的布局管理器
        self.setLayout(layout)

    def show_confirm_dialog(self):
        dialog = QMessageBox(self)
        dialog.setWindowTitle('确认对话框')
        dialog.setText('是否执行此操作？')
        dialog.setStandardButtons(QMessageBox.Yes | QMessageBox.No)
        dialog.setDefaultButton(QMessageBox.No)

        # 显示对话框并获取用户的选择
        button = dialog.exec_()
        if button == QMessageBox.Yes:
            self.label.setText('已执行此操作。')
        else:
            self.label.setText('已取消此操作。')


if __name__ == '__main__':
    app = QApplication([])
    window = MainWindow()
    window.show()
    app.exec_()

```

**输入如下图所示**：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/377893cec149c44d805064cccf9ce87d.png)

#### 3-7-4、字体对话框(QFontDialog)

**QFontDialog是一个用于选择字体和相关属性的对话框类。它允许用户选择字体、字号、粗细和斜体等属性，并返回所选字体的详细信息。在本节中，我们将详细介绍QFontDialog的用法，以及如何将其集成到PyQt5应用程序中。**

**下面是一个简单的示例程序，它演示了如何使用QFontDialog。程序创建一个窗口，该窗口包含一个标签和一个按钮。当用户单击按钮时，将显示一个QFontDialog对话框，用户可以在其中选择字体。选择字体后，标签将使用所选字体进行更新。**

```c
from PyQt5.QtWidgets import QApplication, QLabel, QPushButton, QVBoxLayout, QWidget, QFontDialog

class FontDialogExample(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.label = QLabel('Hello, World!')
        self.button = QPushButton('选择字体', self)
        self.button.clicked.connect(self.showFontDialog)

        vbox = QVBoxLayout()
        vbox.addWidget(self.label)
        vbox.addWidget(self.button)

        self.setLayout(vbox)
        self.setWindowTitle('QFontDialog示例')
        self.show()

    def showFontDialog(self):
        font, ok = QFontDialog.getFont()
        if ok:
            self.label.setFont(font)

if __name__ == '__main__':
    app = QApplication([])
    ex = FontDialogExample()
    app.exec_()

```

**输出如下所示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/969a6da159f8873542302ba7da84fd9f.png)

#### 3-7-5、输入对话框(QInputDialog)

**输入对话框(QInputDialog)**：用于获取用户输入的对话框。可以使用QInputDialog的静态方法创建各种类型的输入对话框，例如文本输入对话框、整数输入对话框、浮点数输入对话框等。

下面是一个使用QInputDialog的简单示例，用于显示一个输入对话框并将用户输入的值显示在标签控件中：

```c
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QPushButton, QVBoxLayout, QInputDialog

class MainWindow(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle('QInputDialog案例')
        self.setGeometry(100, 100, 400, 200)

        # 创建布局管理器和控件
        layout = QVBoxLayout()
        self.label = QLabel('请输入一个字符串：')
        self.button_text = QPushButton('文本输入')
        self.button_text.clicked.connect(self.get_text)
        self.button_int = QPushButton('整数输入')
        self.button_int.clicked.connect(self.get_int)
        self.button_double = QPushButton('浮点数输入')
        self.button_double.clicked.connect(self.get_double)
        self.button_combo = QPushButton('下拉列表输入')
        self.button_combo.clicked.connect(self.get_combo)

        # 将控件添加到布局管理器中
        layout.addWidget(self.label)
        layout.addWidget(self.button_text)
        layout.addWidget(self.button_int)
        layout.addWidget(self.button_double)
        layout.addWidget(self.button_combo)

        # 设置窗口的布局管理器
        self.setLayout(layout)

    def get_text(self):
        text, ok = QInputDialog.getText(self, '文本输入对话框', '请输入一个字符串:')
        if ok:
            self.label.setText('你输入的是：{}'.format(text))

    def get_int(self):
        value, ok = QInputDialog.getInt(self, '整数输入对话框', '请输入一个整数:')
        if ok:
            self.label.setText('你输入的是：{}'.format(value))

    def get_double(self):
        value, ok = QInputDialog.getDouble(self, '浮点数输入对话框', '请输入一个浮点数:')
        if ok:
            self.label.setText('你输入的是：{}'.format(value))

    def get_combo(self):
        items = ['Python', 'Java', 'C++', 'JavaScript']
        item, ok = QInputDialog.getItem(self, '下拉列表输入对话框', '请选择一种语言:', items)
        if ok and item:
            self.label.setText('你选择的是：{}'.format(item))


if __name__ == '__main__':
    app = QApplication([])
    window = MainWindow()
    window.show()
    app.exec_()
```

**输入如下**：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/63ebb14b651111e509af7b7492a20716.png)

#### 3-7-6、颜色对话框(QColorDialog)

**QColorDialog是一个用于选择颜色的标准对话框类。它允许用户选择一个颜色，包括颜色的红、绿、蓝和透明度值。在本文中，我们将介绍如何使用QColorDialog来选择颜色，并演示如何将其集成到PyQt5应用程序中**。

**要在应用程序中显示QColorDialog，可以调用其静态方法getColor()。此方法的默认参数包括**：

- initial: 初始颜色。
- parent: 所属的父级窗口，如果没有则默认为None。
- title: 对话框的标题。

**下面是一个综合的QColorDialog案例，包括了使用QColorDialog选择颜色和调整RGB值的功能：**。

```c
from PyQt5.QtWidgets import QApplication, QWidget, QPushButton, QVBoxLayout, QHBoxLayout, QLabel, QColorDialog, QSlider
from PyQt5.QtGui import QColor
from PyQt5.QtCore import Qt

class Example(QWidget):
    def __init__(self):
        super().__init__()
        self.color = QColor(255, 0, 0) # 默认为红色
        self.initUI()

    def initUI(self):
        # 创建标签
        self.lbl = QLabel('Hello, PyQt5!')
        self.lbl.setAlignment(Qt.AlignCenter)
        self.lbl.setStyleSheet('background-color: {}'.format(self.color.name()))

        # 创建按钮
        self.btn_color = QPushButton('Choose Color', self)
        self.btn_color.clicked.connect(self.show_color_dialog)

        # 创建RGB值标签和调整条
        self.lbl_r = QLabel('R:')
        self.lbl_g = QLabel('G:')
        self.lbl_b = QLabel('B:')
        self.slider_r = self.create_slider()
        self.slider_g = self.create_slider()
        self.slider_b = self.create_slider()

        # 创建布局
        hbox = QHBoxLayout()
        hbox.addWidget(self.lbl_r)
        hbox.addWidget(self.slider_r)
        hbox.addWidget(self.lbl_g)
        hbox.addWidget(self.slider_g)
        hbox.addWidget(self.lbl_b)
        hbox.addWidget(self.slider_b)

        vbox = QVBoxLayout()
        vbox.addWidget(self.lbl)
        vbox.addWidget(self.btn_color)
        vbox.addLayout(hbox)

        self.setLayout(vbox)

        self.setGeometry(300, 300, 250, 150)
        self.setWindowTitle('Color Dialog')
        self.show()

    def create_slider(self):
        slider = QSlider(Qt.Horizontal, self)
        slider.setRange(0, 255)
        slider.setSingleStep(1)
        slider.setValue(255)
        slider.valueChanged.connect(self.update_color)
        slider.setMaximumWidth(100)
        return slider

    def show_color_dialog(self):
        # 显示颜色选择器
        color = QColorDialog.getColor(self.color, self)
        if color.isValid():
            self.color = color
            self.lbl.setStyleSheet('background-color: {}'.format(self.color.name()))
            self.slider_r.setValue(self.color.red())
            self.slider_g.setValue(self.color.green())
            self.slider_b.setValue(self.color.blue())

    def update_color(self):
        # 更新RGB值和颜色
        self.color.setRed(self.slider_r.value())
        self.color.setGreen(self.slider_g.value())
        self.color.setBlue(self.slider_b.value())
        self.lbl.setStyleSheet('background-color: {}'.format(self.color.name()))

if __name__ == '__main__':
    import sys
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())
```

**下边是输出的图形**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/69a9d74743b5d505520625de17cffd2c.png)

## 四、PyQt5高级组件（QTableView、QListView、容器、多线程等）

### 4-1、容器

**PyQt是一个Python编程语言的GUI工具包，它提供了很多容器用来布置和管理GUI组件。下面是一些常见的PyQt容器**：

- **QMainWindow**：==主窗口容器==，通常包含菜单栏、工具栏、状态栏等。
- **QWidget**：==基本的用户界面元素容器==，可以作为其他容器的子容器。
- **QGroupBox**：==分组框容器==，可以将相关的组件放到一个分组框中，使它们更易于组织和查看。
- **QTabWidget**：==选项卡容器==，可以在多个选项卡中放置不同的组件，让用户轻松地在它们之间切换。
- **QStackedWidget**：==堆栈容器==，可以在同一位置上堆叠多个组件，只显示其中的一个，让用户可以轻松地在它们之间切换。
- **QScrollArea**：==滚动区域容器==，当容器中的组件太大，无法在当前视图中完全显示时，可以使用滚动区域容器。
- **QSplitter**：==拆分器容器==，可以将容器水平或垂直拆分为两个或更多子容器，让用户可以自由地调整它们的大小。
- **QToolBar**：==工具栏容器==，可以在主窗口或其他容器中放置多个工具栏，让用户可以快速访问常用功能。
- **注意**：布局和容器可以相互转换

**以下为创建QGroupBox分组容器**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2c4d1d5c23538b769ee3dcc732e9c138.png)  
**以下为将分组容器转换为栅格布局**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5d959fc2d94721364d976402d13b1034.png)

## 五、PyQt5布局管理（QBoxLayout、QGridLayout、QFormLayout、嵌套布局）

- # 1. 快速回忆
- ## 1.1. 布局组件应用步骤
好的，我来总结一下在PyQt中创建和使用布局组件的步骤：

**1. 导入必要的模块：**

首先，需要从`PyQt5.QtWidgets`（或`PyQt6.QtWidgets`，具体取决于你使用的PyQt版本）模块中导入你想要使用的布局类和其他必要的类。

```python
from PyQt5.QtWidgets import QApplication, QWidget, QVBoxLayout, QPushButton
```

**2. 创建布局对象：**

根据你的需求选择合适的布局类（例如`QVBoxLayout`、`QHBoxLayout`、`QGridLayout`、`QFormLayout`等），并创建该类的实例。

```python
layout = QVBoxLayout()
```

**3. 创建控件（Widget）：**

创建你想要添加到布局中的各种控件，例如按钮、标签、文本框等。

```python
button1 = QPushButton("Button 1")
button2 = QPushButton("Button 2")
```

**4. 将控件添加到布局中：**

使用布局对象的`addWidget()`方法（对于`QBoxLayout`和`QGridLayout`）或`addRow()`方法（对于`QFormLayout`）将控件添加到布局中。对于嵌套布局，使用`addLayout()`方法将子布局添加到父布局中。

```python
layout.addWidget(button1)
layout.addWidget(button2)
```

对于`QGridLayout`，你需要指定控件放置的行和列：

```python
layout = QGridLayout()
layout.addWidget(button1, 0, 0)  # 第0行，第0列
layout.addWidget(button2, 0, 1)  # 第0行，第1列
```

对于`QFormLayout`，你需要添加标签和控件对：

```python
layout = QFormLayout()
layout.addRow("Name:", QLineEdit())
layout.addRow("Age:", QSpinBox())
```

**5. 创建主窗口或容器Widget：**

创建一个`QWidget`（或其他容器Widget，如`QFrame`、`QGroupBox`等）作为主窗口或容器，用于容纳布局。

```python
window = QWidget()
```

或者，如果你使用的是`QMainWindow`，你可以创建一个`QWidget`作为中心部件：

```python
window = QMainWindow()
central_widget = QWidget()
```

**6. 将布局设置到主窗口或容器Widget上：**

使用`widget.setLayout(layout)`方法将布局设置到主窗口或容器Widget上。

```python
window.setLayout(layout)
```

或者，对于`QMainWindow`：

```python
central_widget.setLayout(layout)
window.setCentralWidget(central_widget)
```

**7. （可选）设置窗口属性：**

设置窗口的标题、大小等属性。

```python
window.setWindowTitle("Layout Example")
window.setGeometry(300, 300, 300, 200)
```

**8. 显示窗口：**

使用`widget.show()`方法显示窗口。

```python
window.show()
```

**9. 运行应用程序：**

创建一个`QApplication`对象，并调用`app.exec_()`方法运行应用程序。

```python
app = QApplication(sys.argv)
window.show()
sys.exit(app.exec_())
```

**总结示例代码：**

```python
import sys
from PyQt5.QtWidgets import (QApplication, QWidget, QVBoxLayout,
                             QPushButton)

app = QApplication(sys.argv)
window = QWidget()
layout = QVBoxLayout()

button1 = QPushButton("Button 1")
button2 = QPushButton("Button 2")

layout.addWidget(button1)
layout.addWidget(button2)

window.setLayout(layout)
window.setWindowTitle("Layout Example")
window.setGeometry(300, 300, 300, 200)
window.show()

sys.exit(app.exec_())
```

通过以上步骤，你就可以成功创建一个布局组件，并将控件添加到布局中，最终显示在窗口上。记住，布局管理的关键在于理解不同布局类的特性，并根据需要选择合适的布局类型，以及正确地将控件添加到布局中。

- ## 1.2. 犯错事项


```ad-note
title:**犯错事项**
在PyQt中，使用布局管理组件时，有一些常见的错误需要注意，以确保GUI的正确显示和行为：

1.  **忘记设置主布局**：
    *   **错误**：创建了布局，并将控件添加到布局中，但忘记将该布局设置到窗口或QWidget上。
    *   **后果**：控件不会显示，或者显示的位置和大小不正确。
    *   **解决方法**：使用`widget.setLayout(layout)`将布局设置到QWidget上，或者使用`mainWindow.setCentralWidget(widget)`将包含布局的QWidget设置为QMainWindow的中心部件。
2.  **控件没有添加到任何布局中**：
    *   **错误**：创建了控件，但没有使用`layout.addWidget(widget)`将其添加到任何布局中。
    *   **后果**：控件不会显示在界面上。
    *   **解决方法**：确保每个需要显示的控件都通过`addWidget()`、`addLayout()`等方法添加到布局中。
3.  **布局嵌套错误**：
    *   **错误**：在嵌套布局时，没有正确地将子布局添加到父布局中。
    *   **后果**：部分控件可能不会显示，或者布局结构混乱。
    *   **解决方法**：确保使用`parent_layout.addLayout(child_layout)`将子布局添加到父布局中。
4.  **setGeometry()与布局管理器混用**：
    *   **错误**：同时使用布局管理器和`widget.setGeometry()`来设置控件的位置和大小。
    *   **后果**：布局管理器的作用失效，控件的位置和大小可能不正确，或者在窗口大小改变时出现问题。
    *   **解决方法**：使用布局管理器后，不要再使用`setGeometry()`手动设置控件的位置和大小。让布局管理器自动管理控件的布局。
5.  **窗口大小策略（Size Policy）设置不当**：
    *   **错误**：控件的大小策略没有根据需要进行设置，导致控件在布局中占据的空间不符合预期。
    *   **后果**：控件可能过大或过小，或者在窗口大小改变时无法正确调整大小。
    *   **解决方法**：使用`widget.setSizePolicy()`方法设置控件的大小策略，例如`QSizePolicy.Expanding`、`QSizePolicy.Fixed`等。
6.  **忘记设置父对象**：
    *   **错误**：创建控件时，忘记将父对象传递给控件的构造函数。
    *   **后果**：控件可能无法正确显示，或者在程序退出时出现内存泄漏。
    *   **解决方法**：在创建控件时，始终将父对象传递给控件的构造函数，例如`QPushButton("Click", self)`。
7.  **布局方向错误**：
    *   **错误**：使用了错误的布局方向，例如在需要水平排列控件时使用了`QVBoxLayout`。
    *   **后果**：控件的排列方向不正确。
    *   **解决方法**：根据需要选择正确的布局类型，例如`QHBoxLayout`用于水平排列，`QVBoxLayout`用于垂直排列。
8.  **Stretch Factor设置不当**：
    *   **错误**：在`QBoxLayout`或`QGridLayout`中使用`addStretch()`时，没有正确设置伸缩因子（stretch factor），导致控件的比例不正确。
    *   **后果**：控件在布局中占据的空间比例不符合预期。
    *   **解决方法**：根据需要设置正确的伸缩因子，例如`layout.addWidget(widget, stretch=1)`。
9.  **在QMainWindow中使用setLayout()**：
    *   **错误**：直接在`QMainWindow`对象上调用`setLayout()`。
    *   **后果**：布局不会生效，因为`QMainWindow`有自己的布局管理方式。
    *   **解决方法**：创建一个`QWidget`对象，将布局设置到该`QWidget`上，然后使用`QMainWindow.setCentralWidget()`将该`QWidget`设置为`QMainWindow`的中心部件。
10. **在QDialog中使用setLayout()后，又添加了标准按钮**：
    *   **错误**：在`QDialog`中使用`setLayout()`设置布局后，又手动添加了标准按钮（如`Ok`和`Cancel`）。
    *   **后果**：按钮的布局可能不正确，或者出现重复的按钮。
    *   **解决方法**：使用`QDialogButtonBox`来管理标准按钮，并将其添加到布局中。

```
### 5-1、水平布局、垂直布局、栅格布局




**水平布局（Horizontal layout）：**

- 是一种在用户界面中使用的布局方式，其中控件或窗口部件（widget）沿着水平方向排列。这意味着，每个控件或窗口部件都被放置在前一个控件或窗口部件的右侧，从而形成一个水平排列。
- 水平布局常常用于在用户界面中放置多个控件或窗口部件，使它们在水平方向上对齐并占用相同的空间。水平布局在许多图形用户界面工具包中都得到了支持，例如 PyQt、Qt、JavaFX 等。
- 水平布局通常与垂直布局（Vertical layout）结合使用，以便在用户界面中实现复杂的布局。例如，您可以使用水平布局将两个按钮水平排列在一起，然后使用垂直布局将这两个按钮与其他控件组合在一起，以便在用户界面中实现更复杂的布局。

**如下图所示为将五个按钮放置在垂直布局中去**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/627560d61c7104b6e82a8996ee2b88eb.png)  
**如下图所示为垂直布局和水平布局结合的案例**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/abcef8192fc9c415016bd6782ffca5ab.png)

**栅格布局（Grid Layout）**

- 是一种基于网格的布局系统，允许开发者在页面中创建复杂的布局结构。栅格布局使用一个网格来组织页面元素，将页面划分为一系列的行和列。开发者可以通过指定网格中的单元格位置和大小来控制元素的布局。
- 栅格布局的主要特点是它可以非常灵活地定位和调整元素的位置和大小，而不需要依赖传统的文档流布局。栅格布局可以处理复杂的布局结构，并且可以自适应不同的屏幕尺寸和设备。同时，栅格布局也提供了丰富的布局调整方式，例如自适应、固定宽度、最大宽度、最小宽度等。
- 在栅格布局中，通过使用grid容器来定义网格布局，通过grid-template-rows、grid-template-columns、grid-template-areas等属性来定义网格的行列布局。开发者可以使用grid-row、grid-column等属性来指定元素所占的网格单元格位置和大小。

>总的来说，栅格布局是一种强大的布局工具，可以帮助开发者快速创建复杂的布局结构，并且可以适应不同的屏幕尺寸和设备。_

**如下图所示为一个栅格布局的案例**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/09f76aa337df182af36c6380eedc7352.png)

### 5-2、QFormLayout

**FormLayout是一种用于构建图形用户界面（GUI）中表单的布局管理器。它可以在表单中自动地安排各种控件（例如文本框、复选框、下拉框等）的位置和大小，以便它们以最优化的方式显示在表单上。**

- FormLayout的主要目的是简化表单的设计和排版工作，以及提高表单的可读性和易用性。使用FormLayout，设计人员可以轻松地创建各种不同类型的表单，例如登录表单、注册表单、数据输入表单等，而无需手动调整每个控件的位置和大小。
- FormLayout可以根据表单中控件的类型和数量，自动地生成最佳的布局。它可以根据控件之间的相对关系和层次结构，调整每个控件的位置和大小，以确保它们之间的间距和对齐方式是一致的。这样，即使用户调整了表单的大小或缩放了它，控件的位置和大小也会随之自动调整，以适应新的尺寸。
- FormLayout还提供了一些常用的功能，例如表单边距、控件间距、对齐方式、自动换行等。这些功能使得表单更加易于管理和修改，同时也提高了表单的可读性和易用性。

**总之，FormLayout是一种非常有用的表单布局工具，可以使表单设计和排版变得更加高效和方便。使用FormLayout可以减少手动工作量，提高表单的质量和用户体验。**

**如下图所示为：右边为QFormLayout，相比于Grid Layout，QFormLayout使用起来更加的灵活。**  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e3454b14fb9ff5a22f89cfc3ef60e2a7.png)

### 5-3、QGridLayout

#### 5-3-1、QGridLayout简单介绍

**GridLayout（网格布局）是一种PyQt5中的布局管理器，用于将控件以网格的形式排列在窗口中。每个单元格可以包含一个控件，且所有单元格大小相等。**

在GridLayout中，控件被按照行和列的方式排列。行和列从0开始编号。控件可以跨越多个行和列，这是通过指定控件的位置以及它在行和列中所占的单元格数量来实现的。

**以下是GridLayout的一些重要特点**：

- 创建GridLayout对象：可以通过将QWidget作为参数传递给QGridLayout构造函数来创建一个GridLayout对象。然后可以使用addWidget()方法将控件添加到布局中。
- 指定控件的位置：可以使用addWidget()方法的第二个和第三个参数来指定控件的位置。例如，addWidget(button, 0, 0)将button添加到第0行和第0列的单元格中。
- 控件的大小和跨度：可以使用addWidget()方法的第四个和第五个参数来指定控件在行和列中所占的单元格数量。例如，addWidget(label, 0, 0, 1, 2)将label添加到第0行和第0列的单元格中，并让它跨越第0列和第1列的两个单元格。
- 添加空白单元格：可以使用addSpacing()方法添加空白的单元格，从而调整控件之间的距离。
- 对齐方式：可以使用setAlignment()方法设置控件在单元格中的对齐方式。可以指定水平和垂直方向的对齐方式，也可以将对齐方式设置为水平和垂直方向的组合。
- 自动调整大小：可以使用setColumnStretch()和setRowStretch()方法来设置单元格的大小。可以使用addStretch()方法添加一个伸缩项，以便在窗口大小改变时自动调整大小。

#### 5-3-2、QGridLayout案例分析(简单计算器实现)

在这个例子中，我们创建了一个计算器窗口，并使用QGridLayout将所有控件排列成表格形式。我们使用QPushButton创建了所有数字和运算符按钮，并将它们添加到网格布局中。我们还使用QLineEdit创建了结果文本框，并将其放置在布局的顶部。  
当用户单击按钮时，我们使用on_button_clicked()方法来更新结果文本框。如果用户单击等号按钮，我们计算表达式并在文本框中显示结果。如果表达式无效，则在文本框中显示“Error”。

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QWidget, QGridLayout, QPushButton, QLineEdit


class CalculatorWindow(QMainWindow):
    def __init__(self):
        super().__init__()

        # 设置窗口属性
        self.setWindowTitle("Calculator")
        self.setFixedSize(300, 300)

        # 设置中心窗口
        central_widget = QWidget(self)
        self.setCentralWidget(central_widget)

        # 创建布局
        grid_layout = QGridLayout()
        central_widget.setLayout(grid_layout)

        # 添加文本框
        self.result_line_edit = QLineEdit()
        self.result_line_edit.setAlignment(Qt.AlignRight)
        self.result_line_edit.setReadOnly(True)
        grid_layout.addWidget(self.result_line_edit, 0, 0, 1, 4)

        # 添加按钮
        buttons = [
            "7", "8", "9", "/",
            "4", "5", "6", "*",
            "1", "2", "3", "-",
            "0", ".", "=", "+"
        ]
        positions = [(i, j) for i in range(1, 5) for j in range(4)]
        for position, button_label in zip(positions, buttons):
            button = QPushButton(button_label)
            button.setMaximumWidth(50)
            button.clicked.connect(self.on_button_clicked)
            grid_layout.addWidget(button, *position)

    def on_button_clicked(self):
        button = self.sender()
        button_label = button.text()

        if button_label == "=":
            try:
                result = str(eval(self.result_line_edit.text()))
            except (SyntaxError, ZeroDivisionError):
                result = "Error"
            self.result_line_edit.setText(result)
        else:
            self.result_line_edit.setText(self.result_line_edit.text() + button_label)


if __name__ == "__main__":
    app = QApplication(sys.argv)
    calculator = CalculatorWindow()
    calculator.show()
    sys.exit(app.exec_())
```

**输出如下**：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6e7f9d5790b7c3fa9193a18439ab8de9.png)

#### 5-3-3、QGridLayout综合案例分析

**复杂案例，感兴趣的可以自己粘贴运行看一下样式。**：

```c
import sys
from PyQt5.QtCore import Qt
from PyQt5.QtGui import QColor
from PyQt5.QtWidgets import QApplication, QWidget, QHBoxLayout, QPushButton, QLabel, QVBoxLayout, QLineEdit, QGridLayout
from pyqt5Custom import ToggleSwitch


class ColorToggleButton(QPushButton):
    def __init__(self, color, parent=None):
        super().__init__(parent)
        self.color = color
        self.setCheckable(True)
        self.setMinimumSize(50, 50)
        self.setStyleSheet(f"background-color: {self.color.name()}")

    def mousePressEvent(self, event):
        super().mousePressEvent(event)
        self.setChecked(True)


class ColorPicker(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        # 创建垂直布局
        vBox = QVBoxLayout()
        # 将垂直布局设置为主布局
        self.setLayout(vBox)

        ##################################################
        #                                                #
        #               plc_device_parm                  #
        #                                                #
        ##################################################
        self.plc_device_parm = QWidget()
        self.plc_device_lyt = QVBoxLayout()
        self.plc_device_lyt.setSpacing(5)
        self.plc_device_lyt.setAlignment(Qt.AlignTop | Qt.AlignCenter)
        self.plc_device_parm.setLayout(self.plc_device_lyt)

        # 设置背景色
        # self.plc_device_parm.setStyleSheet("background-color: #E6E6FA;")

        self.plc_device_lyt.addWidget(QLabel("<span style='font-size:30px;'>设备参数</span>"),
                                      alignment=Qt.AlignHCenter)
        self.plc_device_lyt.addWidget(QLabel(
            "<span style='font-size:15px; color:#777777;'>Detailed information of device.</span>"),
            alignment=Qt.AlignHCenter)

        self.plc_device_lyt.addSpacing(100)

        # -------------------------------
        #           添加表格
        # -------------------------------

        # 第一行标题
        labels = [QLabel('APC投入切除'), QLabel('当前运行状态'), QLabel('当前运行频率'), QLabel('手动频率'),
                  QLabel('手动频率设置'), QLabel('频率运行上限'), QLabel('频率运行下限'), QLabel('手动启停按钮'),
                  QLabel('APC运行指令'), QLabel('APC频率指令')]

        # 创建GridLayout
        self.grid_layout = QGridLayout()
        # 设置行间距为10
        self.grid_layout.setVerticalSpacing(10)
        # 所有的列都设置为固定宽度
        for i in range(10):
            self.grid_layout.setColumnMinimumWidth(i, 150)

        for i in range(11):
            if i < 7:
                self.grid_layout.addWidget(QLabel(f"{i + 1}#冷却塔风机"), i + 1, 0)
            elif i < 9:
                self.grid_layout.addWidget(QLabel(f"{i - 6}#冷却泵"), i + 1, 0)
            else:
                self.grid_layout.addWidget(QLabel(f"{i - 8}#冷冻泵"), i + 1, 0)

            # 设置第一行标题
            for j in range(10):
                self.grid_layout.addWidget(labels[j], 0, j + 1, alignment=Qt.AlignCenter)

            # 添加第二列按钮
            self.grid_layout.addWidget(ToggleSwitch(text="", style="ios", on=True), i + 1, 1, alignment=Qt.AlignCenter)
            # 添加第三列文本框
            line_edit = QLineEdit("运行")
            line_edit.setEnabled(False)
            line_edit.setStyleSheet("background-color: #00FF00; color: black")
            line_edit.setFixedWidth(60)
            line_edit.setFixedHeight(30)
            self.grid_layout.addWidget(line_edit, i + 1, 2, alignment=Qt.AlignCenter)
            # 添加第四列文本框
            line_edit = QLineEdit("45.0")
            line_edit.setEnabled(False)
            line_edit.setStyleSheet("background-color: white; color: black")
            line_edit.setFixedWidth(60)
            line_edit.setFixedHeight(30)
            self.grid_layout.addWidget(line_edit, i + 1, 3, alignment=Qt.AlignCenter)
            # 添加第五列文本框
            line_edit = QLineEdit("45.0")
            line_edit.setEnabled(False)
            line_edit.setStyleSheet("background-color: #C0C0C0; color: black")
            line_edit.setFixedWidth(60)
            line_edit.setFixedHeight(30)
            self.grid_layout.addWidget(line_edit, i + 1, 4, alignment=Qt.AlignCenter)
            # 第六列添加一组按钮
            # 因为QButtonGroup并不是QWidget的子类，所以不能直接添加到QGridLayout中。如果需要将QButtonGroup添加到布局中，
            # 需要使用一个QWidget包装一下QButtonGroup，然后将QWidget添加到布局中。
            button_widget = QWidget()
            button_layout = QHBoxLayout(button_widget)
            button_1 = QPushButton("➕")
            button_1.setFixedSize(60, 30)
            button_layout.addWidget(button_1)
            button_2 = QPushButton("➖")
            button_2.setFixedSize(60, 30)
            button_layout.addWidget(button_2)

            self.grid_layout.addWidget(button_widget, i + 1, 5, alignment=Qt.AlignCenter)

            # 第七列
            line_edit = QLineEdit("50.0")
            line_edit.setEnabled(False)
            line_edit.setStyleSheet("background-color: #C0C0C0; color: black")
            line_edit.setFixedWidth(60)
            line_edit.setFixedHeight(30)
            self.grid_layout.addWidget(line_edit, i + 1, 6, alignment=Qt.AlignCenter)

            # 第八列
            line_edit = QLineEdit("25.0")
            line_edit.setEnabled(False)
            line_edit.setStyleSheet("background-color: #C0C0C0; color: black")
            line_edit.setFixedWidth(60)
            line_edit.setFixedHeight(30)
            self.grid_layout.addWidget(line_edit, i + 1, 7, alignment=Qt.AlignCenter)

            # 第9列
            button_widget = QWidget()
            button_layout = QHBoxLayout(button_widget)
            button_1 = QPushButton("启动")
            button_1.setFixedSize(60, 30)
            button_1.setStyleSheet("background-color: lightgreen;")
            button_layout.addWidget(button_1)
            button_2 = QPushButton("停机")
            button_2.setFixedSize(60, 30)
            button_2.setStyleSheet("background-color: lightgray;")
            button_layout.addWidget(button_2)

            self.grid_layout.addWidget(button_widget, i + 1, 8, alignment=Qt.AlignCenter)

            # 第十列
            line_edit = QLineEdit("0.000")
            line_edit.setEnabled(False)
            line_edit.setStyleSheet("background-color: white; color: black")
            line_edit.setFixedWidth(60)
            line_edit.setFixedHeight(30)
            self.grid_layout.addWidget(line_edit, i + 1, 9, alignment=Qt.AlignCenter)

            # 第十一列
            line_edit = QLineEdit("0.000")
            line_edit.setEnabled(False)
            line_edit.setStyleSheet("background-color: white; color: black")
            line_edit.setFixedWidth(60)
            line_edit.setFixedHeight(30)
            self.grid_layout.addWidget(line_edit, i + 1, 10, alignment=Qt.AlignCenter)

        # 将GridLayout添加到主布局中去
        vBox.addLayout(self.grid_layout)

        # -------------------------------
        #        添加调控背景色的按钮
        # -------------------------------
        self.plc_device_lyt.addSpacing(50)
        self.color_Layout = QHBoxLayout()
        self.color_widget = QWidget()
        self.color_widget.setFixedSize(300, 100)
        self.color_widget.setLayout(self.color_Layout)
        colors = [
            QColor("#F5F5DC"),
            QColor("#E6E6FA"),
            QColor("#E4F2F2"),
            QColor("#F2E4E4"),
            QColor("#F2EEE4"),
            QColor("#E4F2E4"),
            QColor("#E4E4F2"),
            QColor("#F2F2E4")
        ]
        for color in colors:
            button = ColorToggleButton(color)
            button.setFixedSize(30, 30)
            button.clicked.connect(self.update_color)
            self.color_Layout.addWidget(button)

        # 将颜色块添加到布局中去
        self.plc_device_lyt.addWidget(self.color_widget, alignment=Qt.AlignHCenter)
        
    def update_color(self):
        # 设置背景色
        self.plc_device_parm.setStyleSheet(f"background-color: {self.sender().color.name()};")


if __name__ == '__main__':
    app = QApplication(sys.argv)
    picker = ColorPicker()
    picker.show()
    sys.exit(app.exec_())

```

## 六、PyQt5信号与槽（事件处理、数据传递等）以及关联控件QPushButton、QRadioButton、QcheckBox、QComboBox等
```ad-note
title:**快速回忆**

```


```ad-note
title:**本节注意**
  
# 槽函数若有括号，则会立即执行，而不是在信号触发时执行
**原因解释：**

在 PyQt/PySide 中，信号与槽的连接方式如下：

`self.spinBox.valueChanged.connect(self.information_edition_rollback)`

这样写是**正确的**，因为你传递的是函数对象（不带括号），只有信号触发时才会调用该函数。

如果你写成：

`self.spinBox.valueChanged.connect(self.information_edition_rollback())`

这会**立即执行** [information_edition_rollback()](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)，并把它的返回值（通常是 `None`）传递给 [connect](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)，导致信号触发时什么都不会发生。

**总结：**

- [connect(self.slot)](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)：传递函数对象，信号触发时才执行。
- [connect(self.slot())](vscode-file://vscode-app/e:/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-sandbox/workbench/workbench.html)：立即执行函数，信号触发时不会再执行。

所以，**不要在 connect 里加括号**，否则会导致槽函数在界面初始化时就被执行，而不是在信号触发时执行。
```

### 6-1、PyQt5信号与槽的介绍

**PyQt5中的信号**: 用于在对象之间传递信息的一种机制。一个信号表示了一个事件或状态的变化，当这个事件或状态变化时，信号被发射（emit）。可以将信号连接到一个或多个槽函数中，当信号被发射时，连接的槽函数会被调用执行。槽函数则是用于接收和处理信号的函数。(槽本质上就是一个函数或者方法)

**在PyQt5中，使用connect()方法来将信号连接到槽函数中。connect()方法的基本语法为**：

```c
sender.signal.connect(receiver.slot)
```

>其中，sender表示发送信号的对象，signal表示信号的名称，connect()方法将信号signal连接到receiver对象的槽函数slot中。槽函数可以是任何可调用的Python函数_。

**除了基本的信号和槽连接，PyQt5还支持一些高级的信号和槽机制，如**：

- 使用自定义信号：可以定义自己的信号，并将其连接到槽函数中。自定义信号可以通过QObject类的signal()方法定义，并使用emit()方法发射信号。
- 使用Lambda表达式：可以使用Lambda表达式作为槽函数，Lambda表达式可以简洁地表示一个函数。
- 使用信号参数：PyQt5中的信号可以带有参数，参数可以在信号发射时被传递给槽函数。
- 一个信号连接多个槽函数：可以将一个信号连接到多个槽函数中，所有的槽函数都会在信号被发射时被调用执行。

**信号和槽机制是PyQt5中非常重要的一个概念，可以用于实现各种功能，如用户界面响应、事件处理、多线程通信等。对于PyQt5的学习和使用来说，熟悉信号和槽机制是至关重要的**。

### 6-2、在Qt Designer中的操作

**以下为在Qt Designer中的编辑信号与槽**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/62857d2414586cfc915042bfc00aa776.png)  
**详细的操作步骤**：

- 创建一个按钮
- 点击菜单中的编辑信号/槽
- 拖动按钮，得到如图所示的对话框
- 左侧为信号对应的函数，即点击button发生的事件，（下边继承的信号与槽打对勾，显示右侧函数）
- 右侧为槽，即信号对应的触发事件
- 点击ok，则按钮点击之后就会触发关闭窗口事件。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/76483acb1d2687b0916c6694f7a72c55.png)

### 6-3、QPushButton介绍

**QPushButton是Qt中常用的按钮控件，可以用于在GUI中创建各种类型的按钮，如普通按钮、复选框按钮、单选框按钮等。**它继承自QAbstractButton类，因此具有QAbstractButton类的所有特性和方法。

**QpushButton的构造函数如下**：

```c
QPushButton(parent=None)
QPushButton(str, parent=None)
QPushButton(QIcon, str, parent=None)
```

_其中，第一个构造函数创建一个无标签的按钮；第二个构造函数创建一个有标签的按钮；第三个构造函数创建一个既有图标又有标签的按钮。_

**QPushButton可以通过调用**:

- setText()方法设置按钮的文本标签，
- setIcon()方法设置按钮的图标。
- setEnabled()用于设置按钮是否可用
- setFlat()用于设置按钮是否平面、setCheckable()用于设置按钮是否可选中等。

QPushButton还可以通过信号与槽机制来响应用户的点击事件。当用户单击按钮时，会发出clicked()信号，可以通过连接这个信号来执行特定的操作，例如在文本框中显示一个消息或启动一个特定的函数。此外，QPushButton还支持其他一些与点击相关的信号和槽，例如pressed()和released()信号，用于在按钮被按下和释放时执行操作。

**以下是一个简单的示例，演示如何创建一个QPushButton并设置其文本标签、图标和点击事件**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QPushButton, QLabel, QHBoxLayout, QVBoxLayout, QWidget
from PyQt5.QtGui import QIcon
from PyQt5.QtCore import Qt

class MyMainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.setWindowTitle('QPushButton Demo')
        self.setGeometry(300, 300, 400, 300)

        # 创建一个QPushButton并设置文本标签和图标
        btn = QPushButton('Click me!', self)
        btn.setIcon(QIcon('icon.png'))

        # 连接按钮的clicked信号到槽函数onBtnClicked
        btn.clicked.connect(self.onBtnClicked)

        # 创建一个QLabel用于显示按钮状态
        self.label = QLabel('Button not clicked', self)

        # 创建水平布局和垂直布局，并将按钮和标签添加到布局中
        hbox = QHBoxLayout()
        hbox.addStretch(1)
        hbox.addWidget(btn)
        hbox.addStretch(1)

        vbox = QVBoxLayout()
        vbox.addStretch(1)
        vbox.addLayout(hbox)
        vbox.addStretch(1)
        vbox.addWidget(self.label, alignment=Qt.AlignCenter)

        # 创建一个QWidget，并将垂直布局添加到QWidget中
        widget = QWidget()
        widget.setLayout(vbox)
        self.setCentralWidget(widget)

    def onBtnClicked(self):
        self.label.setText('Button clicked')

if __name__ == '__main__':
    app = QApplication(sys.argv)
    win = MyMainWindow()
    win.show()
    sys.exit(app.exec_())

```

**如下图为输出示例**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8533eb865f0f7857cef23318c19c3af6.png)

### 6-3、QRadioButton介绍

**QRadioButton是一个单选按钮控件，可以用于从多个互斥的选项中选择一个选项。与QCheckBox不同，QRadioButton只允许选择一个选项。**

QRadioButton控件的基本属性和方法包括：

- setText()：设置按钮的文本。
- isChecked()：检查按钮是否被选中。
- setChecked()：设置按钮的选中状态。
- toggled()：每当按钮的选中状态发生变化时，都会发出toggled()信号。

下边是一个简单示例：

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QRadioButton


class MyMainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.setWindowTitle('QRadioButton Demo')
        self.setGeometry(300, 300, 400, 300)

        # 创建两个单选框按钮
        rb1 = QRadioButton('Option 1', self)
        rb1.move(50, 50)
        rb1.setChecked(True)

        rb2 = QRadioButton('Option 2', self)
        rb2.move(50, 80)

        # 绑定toggled()信号
        rb1.toggled.connect(self.onToggled)
        rb2.toggled.connect(self.onToggled)

    def onToggled(self, checked):
        sender = self.sender()
        if checked:
            print(sender.text() + ' is checked')


if __name__ == '__main__':
    app = QApplication(sys.argv)
    win = MyMainWindow()
    win.show()
    sys.exit(app.exec_())
```

**下图为输出图**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/61fcbffeb700039bc1a04e5d9d7cb52b.png)

### 6-4、复选框控件（QcheckBox）介绍

**QCheckBox是一个复选框控件，可以用于从多个选项中选择一个或多个选项。与QRadioButton不同，QCheckBox允许选择多个选项。**

QCheckBox控件的基本属性和方法包括：

- setText()：设置复选框的文本。
- isChecked()：检查复选框是否被选中。
- setChecked()：设置复选框的选中状态。
- stateChanged()：每当复选框的选中状态发生变化时，都会发出stateChanged()信号。

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QCheckBox

class MyMainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.setWindowTitle('QCheckBox Demo')
        self.setGeometry(300, 300, 400, 300)

        # 创建两个复选框
        cb1 = QCheckBox('Option 1', self)
        cb1.move(50, 50)

        cb2 = QCheckBox('Option 2', self)
        cb2.move(50, 80)

        # 绑定stateChanged()信号
        cb1.stateChanged.connect(self.onStateChanged)
        cb2.stateChanged.connect(self.onStateChanged)

    def onStateChanged(self, state):
        sender = self.sender()
        if state == 2:
            print(sender.text() + ' is checked')
        else:
            print(sender.text() + ' is unchecked')

if __name__ == '__main__':
    app = QApplication(sys.argv)
    win = MyMainWindow()
    win.show()
    sys.exit(app.exec_())
```

**下列为输出**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/76ec2f9461ad291f02471b60667e1749.png)

### 6-5、下拉列表控件（QComboBox）介绍

**QComboBox是一个下拉列表控件，允许用户从预定义的一组选项中选择一个或多个选项。它通常用于表示枚举类型的值或选择一组预定义的选项**。

QComboBox控件的基本属性和方法包括：

- addItem()：添加一个项到下拉列表中。
- addItems()：添加多个项到下拉列表中。
- setCurrentIndex()：设置当前选中的项的索引。
- currentText()：返回当前选中的项的文本。
- currentIndexChanged()：每当当前选中的项发生变化时，都会发出currentIndexChanged()信号。

**下面是一个简单的演示示例**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QComboBox

class MyMainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.setWindowTitle('QComboBox Demo')
        self.setGeometry(300, 300, 400, 300)

        # 创建一个下拉列表并添加几个选项
        combo = QComboBox(self)
        combo.addItem('Option 1')
        combo.addItem('Option 2')
        combo.addItem('Option 3')
        combo.move(50, 50)

        # 绑定currentIndexChanged()信号
        combo.currentIndexChanged.connect(self.onIndexChanged)

    def onIndexChanged(self, index):
    	# 选择下拉列表的某一项时，sender.currentText()对应的为数字1、2、3。
    	# 即在选择时，使用sender.currentText()来做出选择每一项对应的操作。
        sender = self.sender()
        print('Current selection is ' + sender.currentText())

if __name__ == '__main__':
    app = QApplication(sys.argv)
    win = MyMainWindow()
    win.show()
    sys.exit(app.exec_())

```

**下图为输出**：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/30086b2bbfbf3185f128a80a95492d0f.png)

### 6-9、Button综合案例

**以下是一个综合案例，展示了如何使用多个QPushButton，包括普通按钮、复选框按钮、单选框按钮和菜单按钮，并演示了这些按钮的基本用法和属性。**

```c
import sys

from PyQt5.QtCore import Qt
from PyQt5.QtGui import QIcon
from PyQt5.QtWidgets import QApplication, QMainWindow, QPushButton, QCheckBox, QRadioButton, QMenu, QAction

class MyMainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        self.setWindowTitle('QPushButton Demo')
        self.setGeometry(300, 300, 400, 300)

        # 创建一个普通按钮和一个带图标的按钮
        btn1 = QPushButton('Button', self)
        btn1.move(30, 50)

        btn2 = QPushButton(self)
        btn2.setIcon(QIcon('switchicon.png'))
        btn2.move(150, 50)

        # 创建一个复选框按钮
        cb = QCheckBox('Show Title', self)
        cb.move(30, 100)
        cb.stateChanged.connect(self.toggleTitle)

        # 创建两个单选框按钮
        rb1 = QRadioButton('Button 1', self)
        rb1.move(30, 150)

        rb2 = QRadioButton('Button 2', self)
        rb2.move(150, 150)

        # 创建一个菜单按钮和一个菜单
        mb = QPushButton('Menu', self)
        mb.move(30, 200)

        menu = QMenu(self)
        menu.addAction('Action 1', self.onAction1)
        menu.addAction('Action 2', self.onAction2)

        mb.setMenu(menu)

    def toggleTitle(self, state):
        if state == Qt.Checked:
            self.setWindowTitle('QPushButton Demo - Title Visible')
        else:
            self.setWindowTitle('QPushButton Demo')

    def onAction1(self):
        print('Action 1 clicked')

    def onAction2(self):
        print('Action 2 clicked')


if __name__ == '__main__':
    app = QApplication(sys.argv)
    win = MyMainWindow()
    win.show()
    sys.exit(app.exec_())
```

**输出展示如下图所示**：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5e26e0a58c3f4241c9938d54f1c54a3a.png)

### 6-10、控件综合案例

**以下是一个使用PyQt5中的各种控件的综合案例，包括标签、按钮、文本框、列表框、进度条、滑块、单选框和复选框。**

_在这个例子中，我们创建了一个名为MyWindow的QWidget窗口，并向它添加了标签、按钮、文本框、列表框、进度条、滑块、单选框和复选框等控件。我们使用QVBoxLayout和QHBoxLayout等布局管理器将控件放置在窗口中，使用QGroupBox将单选框和复选框包含在一个控件组合框中。我们还绑定了按钮的点击事件，以便在点击按钮时执行一些操作。_

```c
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QPushButton, QLineEdit, QListWidget, QProgressBar, QSlider, QRadioButton, QCheckBox, QVBoxLayout, QHBoxLayout, QGroupBox

class MyWindow(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Widget Example")
        
        # 创建标签、按钮和文本框控件
        label = QLabel("Enter your name:")
        button = QPushButton("Submit")
        self.text_box = QLineEdit()
        
        # 创建列表框控件
        list_widget = QListWidget()
        list_widget.addItems(["Item 1", "Item 2", "Item 3"])
        
        # 创建进度条和滑块控件
        progress_bar = QProgressBar()
        slider = QSlider()
        slider.setOrientation(1)
        slider.setRange(0, 100)
        slider.setValue(50)
        slider.valueChanged.connect(progress_bar.setValue)
        
        # 创建单选框和复选框控件
        radio_button_1 = QRadioButton("Option 1")
        radio_button_2 = QRadioButton("Option 2")
        check_box = QCheckBox("Check me")
        
        # 将控件添加到布局中
        v_layout_1 = QVBoxLayout()
        v_layout_1.addWidget(label)
        v_layout_1.addWidget(self.text_box)
        v_layout_1.addWidget(button)
        v_layout_1.addWidget(list_widget)
        
        v_layout_2 = QVBoxLayout()
        v_layout_2.addWidget(progress_bar)
        v_layout_2.addWidget(slider)
        
        h_layout = QHBoxLayout()
        h_layout.addWidget(radio_button_1)
        h_layout.addWidget(radio_button_2)
        h_layout.addWidget(check_box)
        
        # 创建控件组合框
        group_box = QGroupBox("Options")
        group_box.setLayout(h_layout)
        
        # 将布局添加到主布局中
        main_layout = QVBoxLayout()
        main_layout.addLayout(v_layout_1)
        main_layout.addLayout(v_layout_2)
        main_layout.addWidget(group_box)
        
        # 设置主布局
        self.setLayout(main_layout)
        
        # 绑定按钮的点击事件
        button.clicked.connect(self.button_clicked)
    
    # 按钮的点击事件
    def button_clicked(self):
        name = self.text_box.text()
        print("Hello,", name)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = MyWindow()
    window.show()
    sys.exit(app.exec_())


```

**以下为输出图**：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a0f3a7a81f7f759fb0c654d3a380f2e0.png)

## 七、PyQt5高级控件（滑块控件、计数器控件、树控件、QtabWidget）

### 7-1、滑块控件

**滑块控件（Slider）是图形用户界面中常见的一种控件，也称为滑杆、拖动条、进度条等，用于调节数值类型的参数。用户通过拖动滑块的滑块块（Thumb）来改变滑块的值，滑块的范围和步长可以通过设置属性进行控制。在PyQt5中，QSlider是用于创建滑块控件的类。**

QSlider的常用属性和方法如下：

- value()：获取当前滑块的值。
- setValue(value)：设置当前滑块的值。
- minimum()：获取滑块的最小值。
- setMinimum(value)：设置滑块的最小值。
- maximum()：获取滑块的最大值。
- setMaximum(value)：设置滑块的最大值。
- singleStep()：获取滑块的步长。
- setSingleStep(value)：设置滑块的步长。
- sliderMoved.connect(slot)：将slot函数连接到滑块拖动事件。
- valueChanged.connect(slot)：将slot函数连接到滑块值改变事件。  
    在使用QS

**简单案例分析**：

_该综合案例创建了一个带有滑块控件的窗口，并实现了滑块值的更新和重置按钮的功能。运行该代码将显示一个带有滑块控件和重置按钮的窗口，当滑块的值改变时，标签的文本会更新为当前的滑块值。点击重置按钮将会将滑块的值重置为0，并更新标签的文本。_

```c
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QSlider, QHBoxLayout, QVBoxLayout, QPushButton
from PyQt5.QtCore import Qt


class SliderDemo(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        # 创建一个水平布局和垂直布局
        hlayout = QHBoxLayout()
        vlayout = QVBoxLayout()

        # 创建一个标签和滑块控件，并添加到水平布局中
        self.label = QLabel('Value: 0')
        self.slider = QSlider(Qt.Horizontal)
        self.slider.valueChanged[int].connect(self.onSliderValueChanged)
        hlayout.addWidget(self.label)
        hlayout.addWidget(self.slider)

        # 创建一个重置按钮，并添加到垂直布局中
        reset_btn = QPushButton('Reset')
        reset_btn.clicked.connect(self.onResetBtnClicked)
        vlayout.addLayout(hlayout)
        vlayout.addWidget(reset_btn)

        # 设置窗口的布局
        self.setLayout(vlayout)

        # 设置窗口的标题和大小
        self.setWindowTitle('Slider Demo')
        self.resize(300, 200)

    def onSliderValueChanged(self, value):
        # 当滑块的值改变时更新标签的文本
        self.label.setText(f'Value: {value}')

    def onResetBtnClicked(self):
        # 重置滑块的值为0，并更新标签的文本
        self.slider.setValue(0)
        self.label.setText('Value: 0')


if __name__ == '__main__':
    app = QApplication(sys.argv)
    demo = SliderDemo()
    demo.show()
    sys.exit(app.exec_())

```

**输出如下图所示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/db5af3dbc3842061a26494dbb4cfd9c4.png)

### 7-2、计数器（QSpinBox）控件

**QSpinBox是PyQt5中的一个计数器控件，它提供了一个可供用户编辑和选择数字的文本框，用户可以通过点击上下箭头或直接输入数字来更改文本框中的值**。

以下是一些QSpinBox控件的常用属性和方法：

- value()：返回当前计数器的值
- setValue(value)：设置计数器的值
- minimum()：返回计数器的最小值
- setMinimum(value)：设置计数器的最小值
- maximum()：返回计数器的最大值
- setMaximum(value)：设置计数器的最大值
- singleStep()：返回计数器的单步增量
- setSingleStep(value)：设置计数器的单步增量
- suffix()：返回计数器的后缀
- setSuffix(suffix)：设置计数器的后缀

**以下为简单案例分析**：

_该示例程序创建了一个带有计数器控件、标签和重置按钮的窗口。当计数器的值更改时，标签的文本会更新为当前计数器的值。当用户点击重置按钮时，计数器的值将重置为默认值0。运行该程序，将会显示一个带有计数器控件、标签和重置按钮的窗口，您可以通过点击上下箭头或直接输入数字来更改计数器的值，也可以点击重置按钮将计数器的值重置为0。_

```c
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QSpinBox, QPushButton, QVBoxLayout, QHBoxLayout
from PyQt5.QtCore import Qt


class CounterDemo(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()

    def initUI(self):
        # 创建一个垂直布局
        vlayout = QVBoxLayout()

        # 创建一个标签和计数器控件，并添加到垂直布局中
        self.label = QLabel('Value: 0')
        self.spinbox = QSpinBox()
        self.spinbox.setMinimum(0)
        self.spinbox.setMaximum(100)
        self.spinbox.setSingleStep(1)
        self.spinbox.valueChanged[int].connect(self.onSpinBoxValueChanged)
        vlayout.addWidget(self.label)
        vlayout.addWidget(self.spinbox)

        # 创建一个水平布局，并添加一个重置按钮
        hlayout = QHBoxLayout()
        reset_btn = QPushButton('Reset')
        reset_btn.clicked.connect(self.onResetClicked)
        hlayout.addWidget(reset_btn)
        hlayout.addStretch(1)
        vlayout.addLayout(hlayout)

        # 设置窗口的布局
        self.setLayout(vlayout)

        # 设置窗口的标题和大小
        self.setWindowTitle('Counter Demo')
        self.resize(300, 200)

    def onSpinBoxValueChanged(self, newValue):
        # 当计数器的值改变时更新标签的文本
        self.label.setText(f'Value: {newValue}')

    def onResetClicked(self):
        # 点击重置按钮时将计数器的值重置为默认值0
        self.spinbox.setValue(0)


if __name__ == '__main__':
    app = QApplication(sys.argv)
    demo = CounterDemo()
    demo.show()
    sys.exit(app.exec_())

```

···![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d66d6874dc940bb438cdd22a126a245e.png)

### 7-3、树（Tree Widget）控件

#### 7-3-1、树控件的简单介绍

**树控件（Tree Widget）是一种常见的用户界面控件，它可以用来展示层次化的数据结构，例如文件系统、目录结构、组织结构等等。树控件通常由多个节点（Node）组成，每个节点都可以包含多个子节点。**

**在PyQt5中，树控件是通过QTreeWidget类来实现的。下面是一些常用的树控件相关的概念**：

- 节点（Node）：树控件中的基本元素，可以包含多个子节点。每个节点通常由一个图标、一段文本和一个可选的复选框组成。节点可以通过QTreeWidgetItem类来创建和操作。
- 根节点（Root Node）：树控件中的最顶层节点，它没有父节点。一个树控件通常只有一个根节点，但也可以有多个根节点。
- 子节点（Child Node）：节点的直接下级节点。
- 父节点（Parent Node）：节点的直接上级节点。根节点没有父节点。
- 叶节点（Leaf Node）：没有子节点的节点。
- 复选框（Checkbox）：树控件中每个节点可以包含一个可选的复选框，用来表示节点的选中状态。
- 项数据（Item Data）：每个节点都可以包含多个数据项，例如文本、图标、颜色等等。这些项数据可以通过QTreeWidgetItem.setData()和QTreeWidgetItem.data()方法来设置和获取。
- 展开（Expand）：将一个节点的所有子节点显示出来。
- 折叠（Collapse）：将一个节点的所有子节点隐藏起来。

**树控件通常具有以下特点**：

- 层次化结构：树控件中的节点可以是多层次的，可以有多个父节点和多个子节点。
- 可扩展性：树控件中的节点可以被动态地添加和删除，可以根据需要展开或折叠节点。
- 交互性：用户可以通过单击节点或复选框来选择或取消选择节点，可以通过双击节点或者右键菜单来进行编辑等操作。
- 可定制性：树控件中的节点可以设置不同的图标、颜色和字体等属性，以适应不同的需求和样式。

**在PyQt5中，可以通过以下方法来操作树控件**：

- 添加节点：可以通过QTreeWidget.addTopLevelItem()方法或QTreeWidgetItem.addChild()方法来添加节点。
- 删除节点：可以通过QTreeWidget.takeTopLevelItem()方法或QTreeWidgetItem.removeChild()方法来删除节点。
- 获取节点：可以通过QTreeWidget.topLevelItem()方法或QTreeWidgetItem.child()方法来获取节点。
- 设置节点属性：可以通过QTreeWidgetItem.setText()、QTreeWidgetItem.setIcon()等方法来设置节点的文本、图标等属性。
- 选择节点：可以通过QTreeWidget.currentItem()方法获取当前选中的节点，也可以通过QTreeWidgetItem.setSelected

#### 7-3-2、树控件综合案例分析

**在这个案例中，我们创建了一个名为"组织结构图"的主窗口，并设置了固定的大小。然后，我们创建了一个树控件（QTreeWidget），并设置了树控件的列标题为"姓名"、“职位"和"部门”。**

- 在populateTreeWidget()方法中，我们首先创建了根节点，并将其添加到树控件中。然后，我们创建了两个部门节点（department1和department2）作为根节点的子节点，以及每个部门节点下的员工节点。
    
- 每个节点的数据由一个字符串列表表示，其中包括员工的姓名、职位和部门信息。我们使用QTreeWidgetItem类来创建节点，并将其添加为父节点的子节点。
    
- 最后，我们展开了根节点，以便在组织结构图中显示默认的部门和员工关系。
    

```c

import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QTreeWidget, QTreeWidgetItem

class OrganizationChart(QMainWindow):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("组织结构图")
        self.resize(500, 400)

        self.treeWidget = QTreeWidget()
        self.treeWidget.setHeaderLabels(["姓名", "职位", "部门"])

        self.populateTreeWidget()

        self.setCentralWidget(self.treeWidget)

    def populateTreeWidget(self):
        # 创建根节点
        root = QTreeWidgetItem(self.treeWidget, ["总经理", "总经理", ""])

        # 创建部门节点1
        department1 = QTreeWidgetItem(root, ["市场部", "部门经理", ""])
        employee1 = QTreeWidgetItem(department1, ["张三", "销售经理", "市场部"])
        employee2 = QTreeWidgetItem(department1, ["李四", "市场专员", "市场部"])

        # 创建部门节点2
        department2 = QTreeWidgetItem(root, ["技术部", "部门经理", ""])
        employee3 = QTreeWidgetItem(department2, ["王五", "技术总监", "技术部"])
        employee4 = QTreeWidgetItem(department2, ["赵六", "开发工程师", "技术部"])

        # 展开根节点
        self.treeWidget.expandItem(root)

if __name__ == "__main__":
    app = QApplication(sys.argv)

    organizationChart = OrganizationChart()
    organizationChart.show()

    sys.exit(app.exec_())

```

**输出如下图所示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/57c123b8a213b5c5ecf87d974cf23223.png)

### 7-4、QTabWidget控件

**QTabWidget是Qt框架中的一个控件，用于创建和管理标签页（Tab）界面。它提供了一个选项卡式的布局，允许用户在不同的标签页之间切换，并且可以在每个标签页中显示不同的内容**。

QTabWidget具有以下特点和功能：

- 标签页切换：QTabWidget通过标签栏（TabBar）显示不同的标签页，并且允许用户通过点击标签来切换当前显示的标签页。用户可以通过鼠标点击或者键盘快捷键进行切换。
- 多个标签页：QTabWidget支持创建多个标签页，每个标签页可以显示不同的内容。可以根据需要动态添加或移除标签页。
- 自定义标签：每个标签页可以自定义显示的标签文本、图标等，以便更好地表示内容。标签页的样式和外观也可以通过样式表进行自定义。
- 嵌套布局：在每个标签页中，可以使用其他布局和控件来构建复杂的界面。例如，可以在每个标签页中放置表单、列表、按钮等控件。
- 信号与槽：QTabWidget提供了一些信号和槽函数，用于处理标签页切换事件、关闭标签页等操作。通过连接信号和槽，可以实现与标签页相关的自定义逻辑和交互。

**QTabWidget在用户界面设计中经常被用于组织和管理复杂的界面结构。它适用于需要在不同的标签页中显示不同内容的场景，如选项卡式的设置界面、多标签文档编辑器、多标签浏览器等。使用QTabWidget，开发者可以方便地创建交互式、易于导航的界面，提升用户体验和操作效率。**

**以下是一个简单案例**：

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QWidget, QVBoxLayout, QLabel, QTabWidget

if __name__ == "__main__":
    app = QApplication(sys.argv)

    # 创建主窗口
    mainWindow = QMainWindow()

    # 创建QTabWidget
    tabWidget = QTabWidget(mainWindow)

    # 创建标签页1
    tab1 = QWidget()
    layout1 = QVBoxLayout(tab1)
    label1 = QLabel("这是标签页1")
    layout1.addWidget(label1)

    # 创建标签页2
    tab2 = QWidget()
    layout2 = QVBoxLayout(tab2)
    label2 = QLabel("这是标签页2")
    layout2.addWidget(label2)

    # 将标签页添加到QTabWidget中
    tabWidget.addTab(tab1, "标签页1")
    tabWidget.addTab(tab2, "标签页2")

    # 设置主窗口的中央部件为QTabWidget
    mainWindow.setCentralWidget(tabWidget)
    mainWindow.resize(400, 300)
    mainWindow.show()

    sys.exit(app.exec_())

```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cc2f4ec07259d9b7195e1a415c5c965e.png)

### 7-5、堆栈窗口控件（QStackedWidget）

**堆栈窗口控件（QStackedWidget）是Qt框架提供的一种用于管理多个页面或窗口的容器控件。它可以显示多个子窗口，但每次只能显示其中的一个，其它子窗口则被隐藏。通过切换可见的子窗口，堆栈窗口控件允许用户在不同的页面之间进行导航和切换。**

以下是堆栈窗口控件的一些特性和使用方法：

页面管理：堆栈窗口控件可以管理多个页面或窗口，每个页面都可以是一个QWidget或其子类。可以通过添加、插入和删除页面来动态管理堆栈中的子窗口。

导航和切换：通过在堆栈窗口控件中的子窗口之间进行切换，可以实现页面导航。可以使用setCurrentIndex()方法或setCurrentWidget()方法来设置当前可见的子窗口，从而切换页面。

信号和槽机制：堆栈窗口控件提供了一些信号，例如currentChanged信号，可以在当前页面发生变化时触发。可以使用这些信号与槽连接来处理页面切换时的逻辑。

堆栈管理：堆栈窗口控件维护一个内部的堆栈，用于跟踪页面的顺序。可以使用堆栈管理方法，如addWidget()、insertWidget()和removeWidget()来管理堆栈中的页面。

堆栈窗口控件适用于需要在不同页面之间进行切换或导航的应用程序场景，例如设置向导、多页表单、步骤流程等。通过使用堆栈窗口控件，可以方便地管理和显示多个页面，并实现简单而直观 的界面切换和导航效果。

### 7-6、停靠控件

**停靠控件（Dock Widget）是一种常用的界面布局控件，它允许用户在主窗口中创建可停靠的面板或工具栏，以便对应用程序进行灵活的布局和组织。停靠控件提供了一种便捷的方式来管理和切换应用程序的功能模块，使用户可以根据自己的需求动态调整界面布局。**

**在 PyQt 中，停靠控件由 QDockWidget 类实现。它可以与 QMainWindow 或 QMainWindows 的派生类一起使用，使得应用程序的主窗口可以容纳多个停靠控件，并支持拖动、停靠和浮动等操作。**

停靠控件通常具有以下特点和用途：

- 可停靠性：停靠控件可以通过拖拽的方式在主窗口中进行停靠，用户可以将其放置在合适的位置，如顶部、底部、左侧或右侧，也可以在主窗口之外浮动显示。这样，用户可以根据需要自定义界面的布局，使得工作区域更加整洁和高效。
    
- 提供附加功能：停靠控件通常用于承载应用程序的附加功能模块，如工具栏、属性面板、输出窗口等。通过将相关的功能模块组织在不同的停靠控件中，用户可以方便地切换和使用这些功能，提高工作效率。
    
- 用户自定义：停靠控件通常提供了用户自定义的能力，允许用户根据自己的喜好和工作流程调整界面布局。用户可以自由地调整停靠控件的大小、位置和停靠方式，以适应不同的工作环境和任务需求。
    

**在使用停靠控件时，可以通过以下步骤实现**：

- 创建停靠控件对象：使用 QDockWidget 类创建一个停靠控件对象，并将需要承载的内容设置为其子部件。
    
- 设置停靠属性：可以设置停靠控件的标题、图标、位置等属性，以及允许的停靠区域和停靠方式。
    
- 将停靠控件添加到主窗口：使用 QMainWindow 或 QMainWindows 的派生类将停靠控件添加到主窗口中的合适位置，通常使用 addDockWidget() 方法来完成。
    

通过使用停靠控件，用户可以轻松实现界面的灵活布局和组织，以适应不同的任务和工作流程。停靠控件的可停靠性、自定义性和附加功能使得应用程序更加可扩展和易用，提供了良停靠控件（Dock Widget）是一种常用的界面布局控件，它允许用户在主窗口中创建可停靠的面板或工具栏，以便对应用程序进行灵活的布局和组织。停靠控件提供了一种便捷的方式来管理和切换应用程序的功能模块，使用户可以根据自己的需求动态调整界面布局。

**在 PyQt 中，停靠控件由 QDockWidget 类实现。它可以与 QMainWindow 或 QMainWindow 的派生类一起使用，使得应用程序的主窗口可以容纳多个停靠控件，并支持拖动、停靠和浮动等操作。**

**停靠控件的主要特点和用途如下**：

- 可停靠性：停靠控件可以通过拖拽的方式在主窗口中进行停靠。用户可以将其放置在合适的位置，如顶部、底部、左侧或右侧，也可以在主窗口之外浮动显示。这种灵活性使得用户可以根据实际需求自定义界面布局，提高工作效率。
    
- 提供附加功能：停靠控件通常用于承载应用程序的附加功能模块，如工具栏、属性面板、输出窗口等。通过将相关的功能模块组织在不同的停靠控件中，用户可以方便地切换和使用这些功能，提高工作效率。
    
- 用户自定义：停靠控件通常提供了用户自定义的能力，允许用户根据自己的喜好和工作流程调整界面布局。用户可以自由地调整停靠控件的大小、位置和停靠方式，以适应不同的工作环境和任务需求。
    
- 在使用停靠控件时，可以按照以下步骤进行：
    
- 创建停靠控件对象：使用 QDockWidget 类创建一个停靠控件对象，并将需要承载的内容设置为其子部件。
    
- 设置停靠属性：可以设置停靠控件的标题、图标、位置等属性，以及允许的停靠区域和停靠方式。
    
- 将停靠控件添加到主窗口：使用 QMainWindow 或 QMainWindow 的派生类将停靠控件添加到主窗口中的合适位置，通常使用 addDockWidget() 方法来完成。
    

通过使用停靠控件，用户可以轻松实现界面的灵活布局和组织，以适应不同的任务和工作流程。停靠控件的可停靠性、自定义性和附加功能使得应用程序更加可扩展和易用，提供了良好的用户体验。

**综合案例实现：**

```c
import sys
from PyQt5.QtWidgets import QApplication, QMainWindow, QDockWidget, QTextEdit, QAction, QFileDialog, QMessageBox, QVBoxLayout, QWidget, QLabel, QPushButton, QTreeWidget, QTreeWidgetItem

class NotePad(QMainWindow):
    def __init__(self):
        super().__init__()

        self.initUI()

    def initUI(self):
        self.setWindowTitle("NotePad")
        self.setGeometry(100, 100, 800, 600)

        # 创建文本编辑区域
        self.textEdit = QTextEdit()
        self.setCentralWidget(self.textEdit)

        # 创建停靠控件
        dock = QDockWidget("File Actions", self)
        dock.setAllowedAreas(Qt.LeftDockWidgetArea)

        # 创建停靠控件中的内容，包括打开文件按钮和保存文件按钮
        openButton = QPushButton("Open File")
        openButton.clicked.connect(self.openFile)

        saveButton = QPushButton("Save File")
        saveButton.clicked.connect(self.saveFile)

        layout = QVBoxLayout()
        layout.addWidget(openButton)
        layout.addWidget(saveButton)

        widget = QWidget()
        widget.setLayout(layout)
        dock.setWidget(widget)

        # 将停靠控件添加到主窗口的左侧停靠区域
        self.addDockWidget(Qt.LeftDockWidgetArea, dock)

        # 创建菜单和动作
        self.createActions()
        self.createMenus()

        # 创建侧边栏
        self.createSidebar()

        self.show()

    def createActions(self):
        self.openAction = QAction("Open File", self)
        self.openAction.triggered.connect(self.openFile)

        self.saveAction = QAction("Save File", self)
        self.saveAction.triggered.connect(self.saveFile)

    def createMenus(self):
        self.fileMenu = self.menuBar().addMenu("File")
        self.fileMenu.addAction(self.openAction)
        self.fileMenu.addAction(self.saveAction)

    def createSidebar(self):
        # 创建侧边栏
        sidebarDock = QDockWidget("Notes", self)
        sidebarDock.setAllowedAreas(Qt.LeftDockWidgetArea)

        # 创建树控件
        treeWidget = QTreeWidget()
        treeWidget.setHeaderLabels(["Notes"])

        # 添加示例笔记
        root = QTreeWidgetItem(treeWidget)
        root.setText(0, "Notebook")

        note1 = QTreeWidgetItem(root)
        note1.setText(0, "Note 1")

        note2 = QTreeWidgetItem(root)
        note2.setText(0, "Note 2")

        # 将树控件添加到侧边栏
        sidebarDock.setWidget(treeWidget)
        self.addDockWidget(Qt.LeftDockWidgetArea, sidebarDock)

    def openFile(self):
        fileName, _ = QFileDialog.getOpenFileName(self, "Open File")
        if fileName:
            try:
                with open(fileName, 'r') as file:
                    content = file.read()
                self.textEdit.setPlainText(content)
            except Exception as e:
                QMessageBox.critical(self, "Error", str(e))

    def saveFile(self):
        fileName, _ = QFileDialog.getSaveFileName(self, "Save File")
        if fileName:
            try:
                with open(fileName, 'w') as file:
                    content = self.textEdit.toPlainText()
                    file.write(content)
                QMessageBox.information(self, "Success", "File saved successfully.")
            except Exception as e:
                QMessageBox.critical(self, "Error", str(e))

if __name__ == '__main__':
    app = QApplication(sys.argv)
    notepad = NotePad()
    sys.exit(app.exec_())


```

**输出界面如下所示**：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9935b0cdae7fb7af4c730688730116f1.png)

## 八、PyQt5图形与特效（定制窗口风格、绘图、QSS与UI美化、不规则窗口、设置样式等）

## 九、PyQt5扩展应用（制作PyQt5安装程序、数据处理、第三方图绘图库在PyQt5中的应用、UI自动化测试等）

---

## 总结

```pyhton
# 1. 头部信息和导入区

  

class Ui_Form(object):

    # 2. UI 类定义

  

    def setupUi(self, Form):

        # 3. 创建控件、布局、设置属性

  

    def retranslateUi(self, Form):

        # 4. 设置界面文本，支持国际化

  

    # 5. 槽函数（可选）

  

if __name__ == "__main__":

    # 6. 主程序入口
```




# PyQt6
