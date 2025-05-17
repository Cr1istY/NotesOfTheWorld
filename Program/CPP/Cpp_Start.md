# C++入门教程

## 一、导学，关于C++

### 面向过程和面向对象

c语言最大的缺陷，就是在于他面向过程的思维，在如今看来不够高效。

因此，面向对象的cpp语言应运而生。

#### 面向过程（POP）

- 以过程（procedure）为中心的编程范式
- 按照计算机执行命令的顺序，从上到下顺序设计程序

#### 面向对象（OOP）

- 以对象（object）为核心的编程范式
- 对象是类（class）的实例，类中包括了数据的定义和对数据的操作方法

### C++的特点

- 贴近底层、运行速度快
- 编译型语言
- 静态类型语言
- 结构化教学语言
- 面向对象语言
- 面向泛式编程语言
- 功能强大，也复杂、难以掌握

### C++的应用领域

- 桌面应用
- 系统开发
- 底层架构
- 游戏开发
- **嵌入式开发**

### C++代码运行和标准

#### 编译型语言

将整个源代码编译成机器码，再运行机器码

例如：C++、C

#### 解释型语言

由解释器将代码逐行翻译成机器码，逐行运行

例如：Python、JavaScript

#### C++运行

1. 将源代码编译成可目标代码
1. 目标代码与库文件链接，生成可执行文件
1. 运行可执行文件

#### C++标准

- C++98
- C++03
- C++11
- C++14
- C++17
- C++20

## 二、正式开始

### 1.第一个C++程序

```cpp
#include <iostream>

int main() {
	std::cout << "Hello, World!" << std::endl;
	return 0;
}
```

- std 命名空间
- :: 作用域运算符

### 2.变量和数据类型

#### 变量的声明和赋值
```cpp
// 数据类型 变量名 = 初始值;
int a = 10;
```

#### 标识符

由字母、数字、下划线组成，不能以数字开头

不能使用关键字命名

常使用驼峰命名法命名

#### 常量

- 使用`#define`定义常量，不推荐
- 使用`const + 数据类型`定义常量

#### 整形

| 类型 | 描述 | 字节数 | 范围 |
| --- | --- | --- | --- |
| int | 整数 | 4 | -2147483648 ~ 2147483647 |
| short | 短整数 | 2 | -32768 ~ 32767 |
| long | 长整数 | 4 | -2147483648 ~ 2147483647 |
| long long | 长长整数 | 8 | -9223372036854775808 ~ 9223372036854775807 |
| unsigned int | 无符号整数 | 4 | 0 ~ 4294967295 |
|char|字符|1|-128 ~ 127|
|bool|布尔|1|true/false|

使用原则：

1. int不够用，直接使用long long
1. 不能为负直接使用unsigned

#### 浮点型

| 类型 | 描述 | 字节数 | 范围 |
| --- | --- | --- | --- |
| float | 单精度浮点数 | 4 | 3.4e-38 ~ 3.4e38 |
| double | 双精度浮点数 | 8 | 1.7e-308 ~ 1.7e308 |

还可以使用科学计数法表示

5.2e2 = 5.2 * 10^2 = 520

#### new

动态分配内存，返回指针

```cpp
int *p = new int;//在堆区分配内存
*p = 10;//初始化
```

### 3.运算符

#### 优先级

乘除运算大于加减运算，平级从左往右依次计算，括号优先级最高

#### 算术运算符

|运算符|功能|
|---|---|
|+|加法、表示正数|
|-|减法、表示负数|
|*|乘法|
|/|除法|
|%|求余、取模|

#### 赋值运算符

用“=”号表示赋值

左值必须是可以修改的变量，右值可以是常量、变量、表达式

同时，在c++中，可以使用{}进行初始化赋值
```cpp
int a = {10};
int a = 10;
```
两者等效

#### 复合赋值运算符

```cpp
sum+= 10;
sum/= 10;
```
本质上都是二合一，即将运算符和赋值运算符合并

同时，还有`++a` `--b`等常见操作

值得注意的是：

`++a`前置时，先运算再进行返回

`a++`后置式，先返回再运算

#### 关系运算符

|运算符|功能|
|---|---|
|==|等于|
|!=|不等于|
|>|大于|
|<|小于|
|>=|大于等于|
|<=|小于等于|

#### 逻辑运算符

|运算符|功能|
|---|---|
|&&|与|
|\|\||或|
|!|非|

#### 条件运算符
```cpp
int a = 10;
int b = 20;
int max = a > b ? a : b;
```
等效于
```cpp
int max;
if (a > b) {
	max = a;
} else {
	max = b;
}
```

即 ，`?`前为判断条件，`:`前为条件为真时返回值，`:`后为条件为假时返回值

#### 位运算符

位运算符操作的是每一位（bit）上的数据

|运算符|功能|
|---|---|
|&|按位与|
|\||按位或|
|^|按位异或|
|~|按位取反|
|<<|左移|
|>>|右移|

#### 类型转换

- 隐式类型转换
> - 将长度较小的数据类型转换为长度较大的数据类型
> - 这样可以避免精度丢失

- 显式类型转换（强制类型转换）
```cpp
int a = 10;
double b = (double)a;
double c = double(a);
static_cast<double>(a);
```

(数据类型)变量 | 数据类型(变量) | 使用c++内置强制类型转换函数

### 4.流程控制语句

#### 顺序结构

程序按照代码的先后顺序执行

#### 分支结构

##### if

1. if单分支

```cpp
if (条件) {
	// 代码块
}
```

2. if双分支(也可使用条件运算符)

```cpp
if(条件) {
	// 代码块
} else {
	// 代码块
}
```

3. if多分支
```cpp
if (条件1) {
	// 代码块
} else if (条件2) {
	// 代码块
} else {
	// 代码块
}
```

##### switch
```cpp
switch (表达式) {
	case 常量1:
		// 代码块
		break;
	case 常量2:
		// 代码块
		break;
	default:
		// 代码块
}
```

用于多分支判断，`break`用于跳出`switch`语句

#### 循环（迭代）结构

##### while
```cpp
while (条件) {
	// 代码块
}
```

##### do while
```cpp
do {
	// 代码块
} while (条件);
```

先执行一次循环体，再判断条件

##### for
```cpp
for (初始化; 条件; 更新) {
	// 代码块
}
```

**范围for循环**
```cpp
int arr[5] = {1, 2, 3, 4, 5};
for (int i : arr) {
	std::cout << i << std::endl;
}
```

#### 跳转

##### break
跳出循环

##### continue
跳过本次循环

##### goto和return
跳转到指定位置
```cpp
goto label;
label:
```

goto一般不使用，会导致程序逻辑混乱

return终止函数运行，并返回值

### 5.复合数据类型

#### 数组

- 在内存中开辟一段连续的空间
- 一组相同类型的数据集合
- 通过下标访问数组元素
- 数组下标从0开始
- 元素个数不能为变量
```cpp
int arr[5] = {1, 2, 3, 4, 5};
```

##### 访问和遍历数组
```cpp
for (int i = 0; i < 5; i++) {
	std::cout << arr[i] << std::endl;
}
```

#### 多维数组

c++支持多维数组，但是不推荐使用

多维数组本质上是数组的数组

```cpp
int arr[2][3] = {
	{1, 2, 3},
	{4, 5, 6}
};
```

##### arry模板类

对于固定大小的数组，推荐使用array模板类
```cpp
#include <array>
std::array<int, 5> arr = {1, 2, 3, 4, 5};
```

#### 模板类vector

vector是c++标准库中的容器，可以动态调整大小

```cpp
#include <vector>
std::vector<int> v;
v.push_back(10);
v.push_back(20);
```

##### 添加元素

可以使用 push_back 方法向 vector 中添加元素：

```cpp
myVector.push_back(7); // 将整数 7 添加到 vector 的末尾
```

##### 访问元素

可以使用下标操作符 [] 或 at() 方法访问 vector 中的元素：

```cpp
int x = myVector[0]; // 获取第一个元素
int y = myVector.at(1); // 获取第二个元素
```

##### 获取大小

可以使用 size() 方法获取 vector 中元素的数量：

```cpp
int size = myVector.size(); // 获取 vector 中的元素数量
```

##### 迭代访问

可以使用迭代器遍历 vector 中的元素：

```cpp
for (auto it = myVector.begin(); it != myVector.end(); ++it) {
    std::cout << *it << " ";
}

```
或者使用范围循环：

```cpp
for (int element : myVector) {
    std::cout << element << " ";
}
```

##### 删除元素

可以使用 erase() 方法删除 vector 中的元素：

```cpp
myVector.erase(myVector.begin() + 2); // 删除第三个元素
```

##### 清空 Vector

可以使用 clear() 方法清空 vector 中的所有元素：

```cpp
myVector.clear(); // 清空 vector
```

#### 字符串string

所谓的字符串，本质上是一个字符数组

c++中提供了string类，用于处理字符串
```cpp
#include <string>
std::string str = "Hello, World!";
```

##### 读取键盘输入
```cpp
std::string str;
std::cin >> str;
```

忽略开始的空白字符，直到遇到下一个空白字符（空格、回车、制表符）为止

##### 读取一行
```cpp
std::string str;
std::getline(std::cin, str);
```

读取一行，直到遇到回车为止

##### 使用get
```cpp
std::string str;
std::cin.get(str);
std::str = cin.get();
```

#### 读取文件
```cpp
#include <fstream>
std::ifstream ifs("test.txt");
std::string str;
ifs >> str;
```

##### 逐词读取
```cpp
std::string word;
while (ifs >> word) {
	std::cout << word << std::endl;
}
```

##### 逐行读取
```cpp
std::string line;
while (std::getline(ifs, line)) {
	std::cout << line << std::endl;
}
```

##### 逐个字符读取
```cpp
char c;
	while (ifs.get(c)) {
	std::cout << c;
}
```

#### 写入文件
```cpp
#include <fstream>
std::ofstream ofs("test.txt");
std::string str = "Hello, World!";
ofs << str;
```

## 三、进阶

### 结构体

结构体是一种自定义数据类型，用于存储不同类型的数据
```cpp
struct Student {
	std::string name;
	int age;
	double score;
};
```

#### 结构体变量
```cpp
Student stu = {"张三", 18, 99.5};
```

#### 结构体数组

```cpp
Student stus[3] = {
{"张三", 18, 99.5},
{"李四", 19, 98.5},
{"王五", 20, 97.5}
};
```

### 结构体访问

#### 结构体成员访问

```cpp
std::cout << stu.name << std::endl;
```

#### 结构体指针访问

```cpp
Student *p = &stu;
std::cout << p->name << std::endl;
```

### 枚举

枚举是一种自定义数据类型，用于定义一组具名的整数常量

```cpp
enum Season {
Spring,
Summer,
Autumn,
Winter
};
```

#### 枚举变量

```cpp
Season s = Spring;
```

```cpp
std::cout << Spring << std::endl;
```

### 指针

指针是一个变量，存储另一个变量的地址

指针是指向另一种数据类型的数据类型

#### 指针变量

```cpp
int a = 10;
int *p = &a;
```

& 取地址运算符

`*` 间接访问运算符

#### 野指针、空指针和void指针

- 野指针：指向未知内存的指针（未初始化的指针）非常危险
- 空指针：指向空地址的指针，通常用于初始化指针变量
- void指针：通用指针类型，可以指向任何类型的数据

```cpp
int *p = nullptr; // 定义空指针
void *p = nullptr; // 定义void指针
```

#### 指针的指针

指针的指针是指一个指针指向另一个指针的地址

```cpp
int a = 10;
int *p = &a;
int **pp = &p;
```

#### 指向常量的指针

指向常量的指针不能通过指针修改变量的值

```cpp
const int a = 10;
const int *p = &a;
```

#### 常量指针

常量指针不能修改指针指向的地址

```cpp
int a = 10;
int *const p = &a;
```

#### 指针和数组

指针和数组是密切相关的，数组名是数组首元素的地址

```cpp
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;
```

p指向arr的首元素

#### 指针运算

指针可以进行加减运算，但是不能进行乘除运算

```cpp
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;
p++;
```

p++表示指针向后移动一个元素

#### 指针数组和数组指针

指针数组是一个数组，数组中的元素是指针

```cpp
int a = 10;
int b = 20;
int c = 30;
int *arr[3] = {&a, &b, &c};
```

数组指针是一个指针，指向一个数组

```cpp
int arr[3] = {1, 2, 3};
int (*p)[3] = &arr;
```

### 引用

引用是一个变量的别名，引用和原变量共享同一块内存空间

一旦引用被初始化，就不能再引用其他变量

#### 引用变量

```cpp
int a = 10;
int &b = a;
```

#### 引用的引用

引用的引用是指一个引用指向另一个引用

```cpp
int a = 10;
int &b = a;
int &c = b;
```

#### 对常量的引用

对常量的引用不能通过引用修改变量的值

```cpp
const int a = 10;
const int &b = a;
```

#### 指针和引用

- 指针可以为空，引用不能为空
- 指针可以改变指向，引用不能改变引用对象
- 指针可以进行加减运算，引用不能进行运算
- 指针需要解引用才能访问值，引用不需要解引用
- 指针和引用的大小不同
- 指针和引用的初始化方式不同
- 指针和引用的作用域不同
- 指针和引用的用途不同
- 指针和引用的传递方式不同

### 6.函数

#### 函数的定义和调用

函数是一段具有特定功能的、可重复使用的代码块

函数的定义包括函数头和函数体

函数的调用是指在程序中使用函数的名称来执行函数中的代码

#### 生命周期和静态对象

生命周期是指对象在内存中的存在时间

自动对象：

- 是在程序执行到定义它的语句时创建，在程序执行到定义它的语句所在的代码块结束时销毁的对象

- 生命周期与代码块的生命周期相同

静态对象：

- 是在程序开始执行时创建，在程序结束时销毁的对象

- 生命周期与程序的生命周期相同

- 作用域是整个程序

- 存储位置是静态存储区

- 初始化是在程序开始执行时进行的

#### 函数的声明

函数的声明是指在程序中使用函数的名称来声明函数的存在，但是不包含函数的定义

函数的声明可以放在程序的任何位置，但是必须在函数被调用之前进行

#### 头文件与分离式编译

头文件是指包含函数声明的文件，通常以.h为后缀

使用`#include "头文件.h"`引入头文件

头文件需要使用`#pragma once`防止重复引入

#### 函数的参数

函数的参数是指调用函数时传递给函数的数据

函数的参数可以是常量、变量、表达式、数组、结构体、指针、引用等

##### 值传递

值传递是指将实参的值传递给形参

值传递是一种单向传递，实参的值传递给形参，形参的值不会传递给实参

```cpp
void swap(int a, int b) {
	int temp = a;
	a = b;
	b = temp;
}
```

##### 地址传递

地址传递是指将实参的地址传递给形参

地址传递是一种双向传递，形参的值会传递给实参

```cpp
void swap(int *a, int *b) {
	int temp = *a;
	*a = *b;
	*b = temp;
}
```

##### 引用传递

引用传递是指将实参的引用传递给形参

引用传递是一种双向传递，形参的值会传递给实参

```cpp
void swap(int &a, int &b) {
	int temp = a;
	a = b;
	b = temp;
}
```

##### 数组形参

数组形参是指将数组名传递给函数

数组形参是指针形参，传递的是数组的首地址

```cpp
void print(int arr[], int len) {
	for (int i = 0; i < len; i++) {
		std::cout << arr[i] << std::endl;
	}
}
```

#### 函数的返回值

##### 无返回值

##### 有返回值

### 7.函数的高阶应用

#### 内联函数

用函数的代码，替代函数调用

```cpp
inline int add(int a, int b) {
	return a + b;
}
```

#### 默认实参

函数的参数可以有默认值

但是只要一个参数定义了默认值，其余的参数都需要被赋值

```cpp
string stuInfo(string name = "111", string hello = "hello") {
	string info = "name:" + name "\thello" + hello;
	return info;
}
```

#### 函数重载

在c++中，同一作用域下，同一个函数名是可以被定义多次的，前提是参数列表不同。

这种，函数名相同，但实际上不同的函数被称为“重载函数”。

**主函数不能被重载**

#### 有const形参时的函数重载

常量作为形参时，跟不加const完全等价

```cpp

```

#### 函数匹配

函数匹配是指编译器根据函数调用的参数，选择合适的函数进行调用

可以根据传入的参数类型、个数、顺序等进行匹配

#### 函数指针

函数指针是指指向函数的指针

函数指针可以指向函数的地址，通过函数指针调用函数
```cpp
int add(int a, int b) {
	return a + b;
}
int (*p)(int, int) = add;
```

##### 函数指针作形参

```cpp
void print(int (*p)(int, int)) {
	std::cout << p(10, 20) << std::endl;
}
```

### 8.面向对象

#### 类和对象

##### 封装

封装是指将数据和操作数据的函数封装在一起，形成一个类

- 将属性和行为作为一个整体，表现生活中的事物
- 将属性和行为加以权限控制，提高安全性

访问权限：

- 公有权限：public - 可以在类的内部和外部访问
- 私有权限：private - 只能在类的内部访问
- 保护权限：protected - 只能在类的内部和子类中访问

##### 类的声明和定义

```cpp
class Student {
public:
	std::string name;
	int age;
	double score;
	void show();
};
```

在struct中，成员默认是公有的，而在class中，成员默认是私有的

##### 类的成员函数

类的成员函数是指在类中定义的函数

类的成员函数可以访问类的私有成员

```cpp
void Student::show() {
	std::cout << name << "\t" << age << "\t" << score << std::endl;
}
```

一般来说，一般将类的属性设置为私有，而通过公有的成员函数来访问属性

#### 类的对象特性

##### 对象的初始化和清理

- 对象的初始化是指在创建对象时，给对象的属性赋初值
- 对象的清理是指在对象被销毁时，释放对象占用的内存

##### 构造函数和析构函数

构造函数是指在创建对象时自动调用的函数，用于初始化对象的属性

- 没有返回值
- 函数名与类名相同
- 可以重载
- 可以有默认参数

析构函数是指在对象被销毁时自动调用的函数，用于清理对象占用的内存

- 没有返回值
- 函数名与类名相同，前面加~
- 不能重载
- 没有参数

编译器提供的构造函数和析构函数是空实现

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	
	// 构造函数
	Student(string n, int a, double s) {
		name = n;
		age = a;
		score = s;
	}
	// 析构函数
	~Student() {
		cout << "析构函数被调用" << endl;
	}
};
```

##### 构造函数的分类及调用

- 默认构造函数：没有参数的构造函数
- 带参数构造函数：有参数的构造函数
- 拷贝构造函数：用一个对象初始化另一个对象的构造函数
- 隐式构造函数：编译器自动调用的构造函数

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	// 默认构造函数
	Student() {
		name = "无名";
		age = 0;
		score = 0.0;
	}
	// 带参数构造函数
	Student(string n, int a, double s) {
		name = n;
		age = a;
		score = s;
	}
	// 拷贝构造函数
	Student(const Student &s) {
		name = s.name;
		age = s.age;
		score = s.score;
	}
};
```

调用：

```cpp
Student stu1; // 默认构造函数
Student stu2("张三", 18, 99.5); // 带参数构造函数
Student stu3(stu2); // 拷贝构造函数
```

匿名对象

```cpp
Student("张三", 18, 99.5).show();
```

匿名对象在使用后会被销毁

同时，不要使用拷贝构造函数来初始化匿名对象，这会使得编译器认为你创建了一个已经创建的对象

##### 拷贝构造函数的调用时机

- 用已经创建的对象初始化另一个对象
- 值传递的方式给函数参数传值
- 值方式返回局部对象

##### 构造函数的调用规则

- 如果没有定义构造函数，编译器会提供一个默认构造函数
- 如果定义了构造函数，编译器不会提供默认构造函数，但会提供默认拷贝构造函数
- 如果定义了拷贝构造函数，编译器不会提供默认构造函数

##### 深拷贝与浅拷贝

浅拷贝：简单的赋值拷贝

但是，浅拷贝会导致内存泄漏和数据混乱

深拷贝：在堆区分配内存，拷贝数据

析构函数可以将在堆区分配的内存释放掉

如果属性有在堆区分配内存的指针，必须重写拷贝构造函数和析构函数

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	int *arr;
	
	// 带参数构造函数
	Student(string n, int a, double s) {
		name = n;
		age = a;
		score = s;
		arr = new int[10];
	}
	
	// 拷贝构造函数
	Student(const Student &s) {
		name = s.name;
		age = s.age;
		score = s.score;
		arr = new int[10];
		for (int i = 0; i < 10; i++) {
			arr[i] = s.arr[i];
		}
	}
	
	// 析构函数
	~Student() {
		delete[] arr;
		cout << "析构函数被调用" << endl;
	}
};
```

##### 初始化列表

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
	}
};
```

##### 类对象作为类成员

一个类的对象可以作为另一个类的成员

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
	}
};
class Class {
public:
	Student stu;
	
	// 带参数构造函数
	Class(string n, int a, double s) : stu(n, a, s) {
	}
};
```

当其他类的对象作为成员时，会先构造其他类的成员，再构造本类的成员

析构的顺序与构造相反

##### 静态成员

静态成员是指在类中定义的静态变量和静态函数，使用`static`关键字修饰

- 静态成员变量：属于类本身，而不是类的对象
- 静态成员函数：只能访问静态成员变量和静态成员函数，不能访问非静态成员变量和非静态成员函数

```cpp
class Student {
public:
	static int count; // 静态成员变量
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
		count++;
	}
	
	// 静态成员函数
	static void showCount() {
		cout << "学生人数：" << count << endl;
	}
};
```

- 属于整个类
- 需要在类外进行初始化

```cpp
int Student::count = 0;
```

同时，我们可以使用

- 类名来访问 Student::count
- 对象来访问 s.count

静态变量也可以设置访问权限

静态成员函数是所有对象共享的

同时，静态成员函数不能访问非静态成员变量和非静态成员函数，而只能访问静态成员变量和静态成员函数

```cpp
class Student {
public:
	static int count; // 静态成员变量
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
		count++;
	}
	
	// 静态成员函数
	static void showCount() {
		cout << "学生人数：" << count << endl;
	}
};
```

#### 对象模型和this指针

##### 成员变量和成员函数分开存储

编译器会给每个对象分配一块内存空间，存储对象的成员变量

即便是空对象，也会分配一块内存空间，是为了区分对象的地址

总而言之，创建一个类的对象时，只有非静态成员变量会被分配内存空间，成员函数不会被分配内存空间

##### this指针

this指针指向**被调用的成员函数**所在的对象

this指针不需要定义，是隐含在每一个非静态成员函数中的

- 解决名称冲突
- 返回对象本身

this指针的本质是一个指针常量，是不允许修改的

但是，this指针所指向的值是可以修改的

##### 空指针访问函数成员

空指针访问函数成员是允许的，但是会导致未定义行为

```cpp
Student *p = nullptr;
p->show();
```

##### const修饰成员函数

- 成员函数可以被声明为const，表示该函数不会修改对象的成员变量
- 成员属性声明时加上mutable，在常函数中依然可以修改
- 声明对象时前加const，表示该对象是常量对象，不能修改成员变量，只能调用常函数

#### 友元

有些私有的属性，如果需要在其他类中访问，就需要友元

##### 全局函数做友元

```cpp
class Student {
// 友元函数
	friend void show(Student s);

public:
	string name;
	int age;
	double score;
	

};
```

此时，友元函数可以访问类的私有成员

##### 类做友元

```cpp
class Student {
	friend class Class;
	public:
	string name;
	int age;
	double score;
};
class Class {
public:
	void show(Student s) {
		cout << s.name << "\t" << s.age << "\t" << s.score << endl;
	}
};
```

##### 成员函数做友元

```cpp
class Student {
	friend void Class::show(Student s);
	public:
	string name;
	int age;
	double score;
	};
class Class {
public:
	void show(Student s) {
		cout << s.name << "\t" << s.age << "\t" << s.score << endl;
	}
};
```

#### 运算符重载

运算符重载是指重新定义运算符的行为，使其适用于自定义数据类型

##### 加号运算符重载

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
	}
	
	// 运算符重载
	Student operator+(const Student &s) {
		return Student(name + s.name, age + s.age, score + s.score);
	}
};
```

##### 左移运算符重载

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
	}
	
	// 友元函数运算符重载
	friend ostream& operator<<(ostream &os, const Student &s) {
		os << s.name << "\t" << s.age << "\t" << s.score;
		return os;
	}
};
```

```cpp
int main() {
	Student s("张三", 18, 99.5);
	cout << s << endl;
	return 0;
}
```

通常不用成员函数进行重载

通常使用全局函数实现重载

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
	}
};
void operator<<(ostream &cout, const Student &s) {
	cout << s.name << "\t" << s.age << "\t" << s.score;
	return cout;
}
// cout << s;
```

##### 递增运算符重载

```cpp
student& operator++() {
	age++;
	return *this;
}
```

返回的是对象本身的引用

这是为了支持链式调用

##### 赋值运算符重载

利用深拷贝解决内存重复释放的问题

```cpp
Student& operator=(const Student &s) {
	name = s.name;
	age = s.age;
	score = s.score;
	return *this;
}
```

##### 关系运算符重载

```cpp
bool operator==(const Student &s) {
	return name == s.name && age == s.age && score == s.score;
}
```

##### 函数调用运算符重载

```cpp
class Student {
public:
	string name;
	int age;
	double score;
	
	// 带参数构造函数
	Student(string n, int a, double s) : name(n), age(a), score(s) {
	}
	
	// 函数调用运算符重载
	void operator()() {
		cout << name << "\t" << age << "\t" << score << endl;
	}
};
```

```cpp
int main() {
	Student s("张三", 18, 99.5);
	s(); // 调用函数调用运算符重载
	return 0;
}
```

#### 继承

继承是指一个类可以从另一个类中继承属性和行为

可以极大程度上减少代码的重复，增加逼格

`class 子类名 : 继承方式 父类名`

```c++
class Base {
public:
	void show() {
		cout << "Base" << endl;
	}
};
// 继承自Base类
class Derived : public Base {
public:
};
```

**无论什么时候，子类都不能访问父类的私有成员，但是，会被继承下去**。

##### 公有继承

继承父类的公有成员和保护成员，并不更换访问权限

##### 保护继承

父类的公有成员和保护成员在子类中是保护的

##### 私有继承

父类的所有成员在子类中都是私有的

##### 继承中的对象模型

父类中的所有的非静态成员变量都会被继承到子类中

##### 继承中的构造和析构顺序

- 构造顺序：父类的构造函数先执行，子类的构造函数后执行
- 析构顺序：子类的析构函数先执行，父类的析构函数后执行

##### 继承中的同名成员处理

- 如果子类和父类有同名成员，子类的成员会覆盖父类的成员

如果想要访问父类的成员，可以使用作用域解析运算符

```cpp
Base::show();
```

子类同名成员函数会覆盖父类的同名成员函数，即便是父类的重载函数

##### 继承中同名的静态成员处理方式

调用作用域可以访问同名的父类静态成员

```cpp
Derived::Base::show();
```

##### 多继承语法

```cpp
class Derived : public Base1, public Base2 {
public:
};
```

Derived类继承了Base1类和Base2类的所有成员

但是，如果Base1类和Base2类有同名成员，编译器会报错

所以，实际开发中不建议使用多继承

##### 菱形继承

菱形继承是指一个类同时继承了两个类，而这两个类又继承了同一个父类

动物、羊、骆驼、草泥马

羊和骆驼都继承了动物类，而草泥马又继承了羊和骆驼

造成的问题：

1. 当草泥马调用动物类的成员时，编译器不知道调用哪个父类的成员（二义性）
1. 草泥马类会继承两个动物类的成员，导致内存浪费

解决：

1. 加以作用域进行区分
1. 使用虚继承

```cpp
class Animal {
public:
	void show() {
		cout << "Animal" << endl;
	}
};
class Sheep : virtual public Animal {
public:
	void show() {
		cout << "Sheep" << endl;
	}
};
class Camel : virtual public Animal {
public:
	void show() {
		cout << "Camel" << endl;
	}
};
class GrassMudHorse : public Sheep, public Camel {
public:
	void show() {
		cout << "GrassMudHorse" << endl;
	}
};
```

Animal类被称为虚基类

vbptr - 虚基类指针 - 指向vbtable - 虚基类表

#### 多态

静态多态：函数重载和运算符重载，

动态多态：运行时多态，基于虚函数实现

静态多态的函数地址是早绑定的，在编译时就确定了函数的地址

动态多态的函数地址是晚绑定的，在运行时才确定了函数的地址

##### 动态多态的基本条件

1. 有继承关系
1. 要重写父类的虚函数

##### 动态多态的实现

1. 在父类中声明虚函数
1. 父类的指针或引用指向子类对象

##### 虚函数

虚函数是指在基类中声明为虚函数的成员函数

- 在基类中使用`virtual`关键字声明

- 在子类中重写基类的虚函数

- 在基类中使用`delete`关键字声明虚函数，表示该函数不能被重写

- 在子类中使用`override`关键字声明虚函数，表示该函数重写了基类的虚函数

```cpp
class Base {
public:
	virtual void show() {
		cout << "Base" << endl;
	}
};
class Derived : public Base {
public:
	void show() override {
		cout << "Derived" << endl;
	}
};
```

```cpp
int main() {
	Base *p = new Derived();
	p->show(); // 输出Derived
	delete p;
	return 0;
}
```

##### 多态原理刨析

- 在编译时，编译器会为每个类生成一个虚函数表（vtable），表中存储了该类的虚函数的地址
- 在运行时，编译器会为每个对象生成一个虚函数指针（vptr），指向该对象所属类的虚函数表
- 当调用虚函数时，编译器会根据对象的vptr找到对应的虚函数表，然后根据虚函数表中的地址调用相应的虚函数
- 如果子类重写了父类的虚函数，虚函数表中的地址会被更新为子类的虚函数的地址
- 如果子类没有重写父类的虚函数，虚函数表中的地址会指向父类的虚函数的地址
- 如果父类的虚函数被声明为纯虚函数，子类必须重写该虚函数，否则编译器会报错

在实际开发中，为了维护和拓展代码，通常会使用开闭原则开发

开闭原则：对扩展开放，对修改关闭

##### 多态的好处

1. 组织结构清晰，易于维护
1. 可读性强
1. 可扩展性强

##### 纯虚函数和抽象类

在基类中声明纯虚函数，表示该函数没有实现，必须在子类中实现

- 纯虚函数的声明方式：`virtual void show() = 0;`

当一个类中有纯虚函数时，该类被称为抽象类

抽象类不能被实例化，只能被继承

子类必须重写纯虚函数，否则编译器会报错

##### 虚析构和纯虚析构

多态使用中，如果子类中有属性开辟到堆区，那么父类指针在释放时无法调用到子类的析构代码

必须将父类的析构函数声明为虚析构或纯虚析构

如果子类中没有堆区数据，可以不写父类的虚析构函数

### 9.文件处理

程序中的数据通常存储在内存中，内存中的数据在程序结束后会被销毁

但是，有些数据需要在程序结束后仍然保留，这时就需要将数据存储到文件中

C++对文件的操作是通过流来实现的，通过导入`fstream`头文件

文件类型分为两种

- 文本文件：以字符为单位存储数据，通常以.txt为后缀
- 二进制文件：以字节为单位存储数据，通常以.bin为后缀

#### 1. 文本文件

##### 读写文本文件

1. 包含头文件
1. 创建流对象
1. 打开文件
1. 写数据
1. 关闭文件

|打开方式|解释|
|---|---|
|ios::in|以读的方式打开文件|
|ios::out|以写的方式打开文件|
|ios::app|以追加的方式打开文件|
|ios::ate|以读写的方式打开文件，指针指向文件末尾|
|ios::trunc|以写的方式打开文件，清空文件内容|
|ios::binary|以二进制的方式打开文件|

打开方式可以组合使用

使用`|`符号连接

```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;
int main() {
	ofstream ofs("test.txt", ios::out | ios::app);	//同时以写和追加的方式打开文件
	if (!ofs) {
		cout << "打开文件失败" << endl;
		return 0;
	}
	ofs << "hello world" << endl;	//写入数据
	ofs.close();
	return 0;
}
```

#### 2. 二进制文件

使用`ostream& write(const char * buffer, int len);`函数来读取二进制文件

## 综合案例：职工管理系统

## 四、提高

### 1. 模板

#### 1.1 模板的概念

模板是一种泛型编程的机制，它允许我们编写通用的代码，而不需要为每种数据类型都编写一份代码。

模板可以用于函数和类，它们可以接受任意类型的参数，并且可以在编译时进行类型检查。

#### 1.2 函数模板

使用`template <typename T>`或`template <class T>`来定义函数模板

```cpp
template <typename T>
void swap(T &a, T &b) {
	T temp = a;
	a = b;
	b = temp;	
}
```

#### 1.3 函数模板注意事项

1. 自动类型推导，必须推导出一致的数据类型T，才可以使用
2. 模板必须要确定出T的数据类型，才可以使用

#### 1.4 普通函数与函数模板的区别

1. 普通函数可以发生隐式类型转换，函数模板不能
2. 普通函数可以发生重载，函数模板不能
3. 函数模板可以发生重载，普通函数不能

#### 1.5 普通函数与函数模板的调用规则

1. 如果函数模板和普通函数都可以调用，优先调用普通函数
2. 如果函数模板可以产生更好的匹配，优先调用函数模板
3. 如果函数模板和普通函数都不能调用，编译器会报错
4. 函数模板也可以发生重载 

#### 1.6 模板的局限性

1. 模板的通用性并不是万能的
2. 有些特定数据类型，需要用具体化方式做特殊实现

学习模板并不是为了写模板，而是在STL能够运用系统提供的模板

### 2. 类模板

建立一个通用类，类中的成员数据类型可以不具体指定，用一个虚拟的类型来代表

#### 2.1 类模板语法

使用`template <typename T>`或`template <class T>`来定义类模板

```cpp
template <typename T>
class MyArray {
public:
	T arr[10];
	void show() {
		for (int i = 0; i < 10; i++) {
			cout << arr[i] << " ";
		}
	}	
}
int main() {
	MyArray<int> myArray;	
}
```

#### 2.2 类模板与函数模板区别

1. 类模板没有自动类型推导使用方式
2. 类模板在模板参数列表中，可以又默认参数