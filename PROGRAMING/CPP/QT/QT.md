# QT

## 1 Qt概述

### 1.1 Qt简介

一个跨平台的C++图形用户界面应用程序开发框架，支持Windows、Linux、Mac OS X、Android、iOS等平台。

### 1.2 Qt新建项目

1. 打开 Qt Creator IDE
2. 点击文件->新建Qt项目
3. 选择 Qt Widgets 应用程序

新建项目后，会生成一个简单的 Qt Widgets 应用程序，包含一个窗口和一个按钮。

此时，编译器会生成虚拟的文件夹，方便开发

#### 文件分类

分为

1. .pro文件：项目文件，记录了项目信息，如项目名称、源文件、头文件、库文件等。
2. .cpp文件：源文件，包含程序逻辑。
3. .h文件：头文件，包含程序接口。
4. .ui文件：用户界面文件，包含图形界面的布局。

## 2 项目一：笔记本

- 支持文本创建、打开、保存、关闭的功能
- UI样式美化
- 添加打开快捷键，添加保存快捷键
- 底部显示行列号以及文本编码
- 快捷键实现字体放大缩小

## 3 开始

### main.cpp

```cpp
#include "widget.h"

#include <QApplication>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv); // 创建一个QApplication实例
    Widget w;
    w.show();
    return a.exec(); // 启动事件循环
}
```

#### QApplication

|功能|描述|
|---|---|
|事件循环|维护事件循环，负责分发和接收各种事件|
|全局设置|处理全局的设置，如字体、颜色等|
|GUI初始化|管理窗口，负责窗口的创建、显示、隐藏等操作|
|命令行参数处理|可以处理命令行参数|

### 界面布局设计

