# Pyside6

[课程](https://www.bilibili.com/video/BV1c84y1N7iL?spm_id_from=333.788.player.switch&vd_source=1925e38de9174c77ef2d3cfdc2dea75d&p=4)

## 环境配置

安装 PySide6

## 基础框架

```python
import sys
from PySide6.QtWidgets import QApplication, QMainWindow
class MyWindow(QMainWindow):
    def __init__(self):
        super().__init__()

if __name__ == '__main__':
    app = QApplication(sys.argv)
    window = MyWindow()
    window.show()
    app.exec_()
```

## 三种最基础的控件

所有的控件都可以通过QtDesigner来查看成员

### QpushButton

The push button, or command button, is perhaps the most commonly used widget in any graphical user interface. Push (click) a button to command the computer to perform some action, or to answer a question. Typical buttons are OK, Apply, Cancel, Close, Yes, No and Help.

### QLabel

QLabel is used for displaying text or an image. No user interaction functionality is provided. The visual appearance of the label can be configured in various ways, and it can be used for specifying a focus mnemonic key for another widget.

### QlineEdit

A line edit allows users to enter and edit a single line of plain text with useful editing functions, including undo and redo, cut and paste, and drag and drop.

## QtDesigner

### 基本布局绘制

### 界面转化

使用`pyside6-uic 文件名.ui -o 文件名.py`命令将ui文件转化为py文件

#### 使用ui文件

```python
import sys
from PySide6.QtWidgets import QApplication, QWidget
from test01 import Ui_Form

class MyWindow(QWidget):
    def __init__(self):
        super().__init__()
        self.ui = Ui_Form()
        self.ui.setupUi(self)


if __name__ == '__main__':
    app = QApplication(sys.argv)
    window = MyWindow()
    window.show()
    app.exec()

```

```python
import sys
from PySide6.QtWidgets import QApplication, QWidget
from test01 import Ui_Form


class MyWindow(QWidget, Ui_Form):
    def __init__(self):
        super().__init__()
        self.setupUi(self)


if __name__ == '__main__':
    app = QApplication(sys.argv)
    window = MyWindow()
    window.show()
    app.exec()

```

## 三种窗体介绍

三种窗体，分别适用于不同的情况

### QMainWidow

主窗口类型，比较全面

有自带的布局

适合大型项目

### QWidget

简单的窗口类型，上手简单

### QDialog

可以把窗口置顶，适用于弹窗（模态）

## 信号与槽

在Pyside6中，信号与槽是两种特殊的函数，用于实现程序间的通信。

信号是主动发出的，而槽函数是被动接收的。

以下程序是信号与槽的基本使用

```python
import sys

from PySide6.QtWidgets import QApplication, QWidget

from test01 import Ui_Form


class MyWidow(QWidget, Ui_Form):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
        self.result = ''

        self.bind()
    def bind(self):
        self.pushButton_0.clicked.connect(lambda: self.addNumber('0'))
        self.pushButton_1.clicked.connect(lambda: self.addNumber('1'))
        self.pushButton_2.clicked.connect(lambda: self.addNumber('2'))
        self.pushButton_3.clicked.connect(lambda: self.addNumber('3'))
        self.pushButton_4.clicked.connect(lambda: self.addNumber('4'))
        self.pushButton_5.clicked.connect(lambda: self.addNumber('5'))
        self.pushButton_6.clicked.connect(lambda: self.addNumber('6'))
        self.pushButton_7.clicked.connect(lambda: self.addNumber('7'))
        self.pushButton_8.clicked.connect(lambda: self.addNumber('8'))
        self.pushButton_9.clicked.connect(lambda: self.addNumber('9'))
        self.pushButton_plus.clicked.connect(lambda: self.addNumber('+'))
        self.pushButton_chu.clicked.connect(lambda: self.addNumber('/'))
        self.pushButton_jian.clicked.connect(lambda: self.addNumber('-'))
        self.pushButton_cheng.clicked.connect(lambda: self.addNumber('*'))
        self.pushButton_enter.clicked.connect(self.equal)

    def addNumber(self, number):
        self.lineEdit.clear()
        self.result += number
        self.lineEdit.setText(self.result)

    def equal(self):
        self.numberResult = eval(self.result)
        self.lineEdit.setText(str(self.numberResult))


if __name__ == '__main__':
    app = QApplication(sys.argv)
    window = MyWidow()
    window.show()
    app.exec()
```

## 常用控件-下拉框-多选框

限制用户输入

### 下拉框

QComboBox

### 多选框

QCheckBox

### 进制转换器

```python
import sys

from PySide6.QtWidgets import QApplication, QWidget
from jinzhi import Ui_Form

class MyWidow(QWidget, Ui_Form):
    def __init__(self):
        super().__init__()
        self.setupUi(self)

        self.lengthVar = {'米': 100, '千米': 100000, '厘米': 1}
        self.weightVar = {'克': 1, '千克': 1000, '斤': 500}
        self.TypeDict = {'长度': self.lengthVar, '重量': self.weightVar}
        self.comboBox.addItems(self.TypeDict.keys())
        self.comboBox_2.addItems(self.lengthVar.keys())
        self.comboBox_3.addItems(self.lengthVar.keys())
        self.bind()

    def bind(self):
        self.comboBox.currentTextChanged.connect(self.typeChange)
        self.pushButton.clicked.connect(self.cal)

    def cal(self):
        big_type = self.comboBox.currentText()

        value = self.lineEdit.text()
        if value == '':
            return
        current_type = self.comboBox_2.currentText()
        trans_type = self.comboBox_3.currentText()

        standardization = float(value) * self.TypeDict[big_type][trans_type]
        result = self.TypeDict[big_type][current_type] / standardization

        self.label.setText(f'{value} {current_type} =')
        self.label_2.setText(f'{result} {trans_type}')
        self.lineEdit_2.setText(str(result))

    def typeChange(self, text):
        self.comboBox_2.clear()
        self.comboBox_3.clear()
        self.comboBox_2.addItems(self.TypeDict[text].keys())
        self.comboBox_3.addItems(self.TypeDict[text].keys())

if __name__ == '__main__':
    app = QApplication(sys.argv)
    window = MyWidow()
    window.show()
    app.exec()
```

## 常用控件-单选框-文本框

### 单选框-QRadionButton

### 编辑框QEditText与纯文本编辑框QEditPlainText

### 项目，在线翻译

### 常用控件-滑条

## 常见布局以及布局的作用

## 内置方便控件

### 信息对话框-QMessageBox

模态：Modal

用于创建弹窗

### QinputDialog

主要用来接收用户输入

### QFileDialog

### QFontDialog

字体对话框

### QColorDialog

## 子窗口和多窗口

### 子窗口的开闭以及选择


