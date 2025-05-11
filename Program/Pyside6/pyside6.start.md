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
