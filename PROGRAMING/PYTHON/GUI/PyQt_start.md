# Python Qt

## PyQt简介

### 几种方案

1. Tkinter：小但控件少
2. wxPython：稳定性差，文档少，用户少
3. PySide2\PyQt5：基于Qt的python图形界面开发，但是比较大

### 安装PySide5

python高版本只能按照PySide6

## 开始

### 基础框架

```python
from PySide6.QtWidgets import QApplication, QWidget

class MainWindow(QWidget):
    def __init__(self):
        super().__init__()

if __name__ == '__main__':
    app = QApplication([])
    window = MainWindow()
    window.show()
    app.exec()
```

### 三种最基础的控件

#### QPushButton

最基础的按钮控件

#### QLabel

标签

#### QLineEdit

输入框

### 三个窗体界面

#### QMainWindow

有自己的布局，自带控件多

但是使用复杂

#### QWidegt

窗体简单

#### QDialog

没有自带布局

和QWidegt最大的区别是可以把窗口置顶

做对话框 - 模态窗口

### 信号与槽

每个控件主动发出信号

而槽接收到信号之后进行对应的操作

### 常用控件

#### 下拉框 QComboBox
