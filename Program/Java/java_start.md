# Java - 尚硅谷教程

[尚硅谷教程](https://www.bilibili.com/video/BV1YT4y1H7YM)

## 模块一 Java入门

1. 会常用的DOS命令
2. 会按照Java的运行环境（jdk）
3. 会配置Java1的环境
4. 知道Java开发的三步骤
5. 会开发一个简单的Java程序
6. 会三种注释方式
7. 知道Java入门程序所需要注意的地方
8. 知道println与print的区别

### 1. Java相关概述

#### 课程体系介绍

1. 第一部分：计算机编程核心语法 - 数据类型、运算符、流程控制、数组、方法
2. 第二部分：面向对象核心逻辑 - 类和对象、封装、继承、多态、抽象、接口
3. 第三部分：javaSE核心高级应用 - API、集合、IO流、多线程、网络编程、反射
4. 第四部分：java新特性 - Lambda表达式、函数式接口、新日期类、jdk8-17新特性

### 2. 软件和硬件介绍

#### 硬件

硬件是看得见、摸得着的物理设施或设备。

#### 软件

软件是以文件或文档的形式所存在的，是运行在计算机上的程序。

#### 软件和硬件的关系

软件和硬件相辅相成，谁也离不开谁。

### 3. java语言介绍

计算机编程语言：就是计算机能听懂的语言。

#### 计算机语言的发展

1. 第一代：机器语言 - 0 和 1
2. 第二代：汇编语言 - 汇编指令
3. 第三代：高级语言 - 更接近人类的语言

所有的高级语言实际上都会转化为机器语言。

没有最好，只有最适合。

#### java的发展历史

java之父 - James Gosling

#### JavaSE

允许你在桌面和服务器上开发和部署Java应用程序。

java不太适合复杂的开发

#### JavaEE

页面 + 服务器开发

#### JavaME

嵌入式开发

### 4. 什么是软件开发

**需求捕捉、需求分析、设计、实现和测试**。

软件一般是使用某种程序设计语言实现的

## 模块二 Java入门前言

### 1. 字节

### 2. 常用的dos命令

## 模块三 Java环境

### 1. jvm和跨平台

#### jvm

jvm是java虚拟机，是java运行时环境

#### 跨平台

跨平台：java程序可以运行在多种操作系统上

一次编写、到处运行

### 2. jdk和jre

jdk：java开发包，java开发工具包，java开发环境

jre：java运行时环境

## 模块四 Java入门程序

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### 注释

1. 单行注释：`//`
2. 多行注释：`/* */`
3. 文档注释：`/** */`

多行注释与文档注释的区别：

文档注释：写好的类，让别人快速了解（可以通过命令生成一个API文档）

## 变量-常量-类型转换-进制转换

### 常量

#### 常量运算

如果都是整数，则运算结果是整数

### 变量

#### 数据类型

基本数据类型四类八种：

- 整形：byte、short、int、long
- 浮点型：float、double
- 字符型：char
- 布尔型：boolean

引用数据类型：类、数组、接口、枚举、注解

#### 变量声明

```java
int a;
a = 10;
// -------
int a = 10, b = 20;
// -------
int a, b;
a = 10;
b = 20;
```

#### 转义字符

转义字符：\

1. 将普通字符转成特殊字符
2. 将特殊字符转成普通字符

### 标识符

标识符，即给变量、方法、类、接口、枚举、注解、包等命名。

#### 硬性规定

不能是关键字

不能以数字开头

#### 软性规定

类：大驼峰

方法和变量：小驼峰

### 类型转换

#### 强制类型转换

```java
int a = 10;
byte b = (byte) a;
```

##### 注意事项

不要随意写出强转，会有精度损失或者数据溢出

### 位运算符

|位运算符|描述|
|:----:|:----:|
|&|按位与|
|\||按位或|
|^|按位异或|
|<<|左移|
|>>|右移|
|>>>|无符号右移|
|~|按位取反|

实际上，数据在计算机中是以二进制的形式存储的。

使用位运算符，需要先转化为二进制数。

#### 左移运算符

左移几位，就相当于乘以2的几次幂

#### 右移运算符

右移几位，就相当于除以2的几次幂

不能整除则向下取整

## IDEA

### 项目结构

项目目录下的子目录称为模块（module）

module下面的子目录称为包（package）

#### package取名规范

1. 公司域名倒着写

## 运算符

### 算术运算符

### 赋值运算符

### 比较运算符

结果是boolean类型

### 逻辑运算符

### 短路与 短路或

短路与：&& - 如果左边为false，则右边不执行

短路或：|| - 如果左边为true，则右边不执行

### 三元运算符

语法：?:

? 前面写条件

如果满足，则实现 : 左边，否则实现右边

## 流程控制语句

### Scanner键盘录入

java定义好的一个类

用来接收键盘录入的数据

#### 使用 Scanner

1. 导包：通过导包的方式找到要使用的类 - 类上引入
2. 创建对象
3. 调用方法

```java
package cn.foreveryang.scanner;
import java.util.Scanner;

public class Demon01Scanner {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        scanner.nextInt();
    }
}
```

##### nextLine 和 next 的区别

next - 遇到空格或回车就结束了

nextLine - 遇到回车才结束

### random随机数

1. 概述：java自带的一个类
2. 用途：产生一个随机整数

### switch语句

#### 1. switch基本使用

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int choice = scan.nextInt();
        switch (choice) {
            case 1:
                System.out.println("hhh");
                break;
            case 2:
                System.out.println("xxx");
                break;
            case 3:
                System.out.println("yyy");
                break;
            case 4:
                System.out.println("zzz");
                break;
            default:
                System.out.println("hh");
                break;
        }
    }
}
```

switch 能够匹配的数据类型有：

byte、short、int、char、String、enum，不能匹配浮点数（不精准）

### if语句

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int day = scan.nextInt();
        if (day == 2) {
            System.out.println("Tuesday");
        }
        else if (day == 3) {
            System.out.println("Wednesday");
        }
        else {
            System.out.println("Other");
        }
    }
}
```

### for循环

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        int i = 10;
        for (int j = 0; j < i; j++) {
            System.out.println("我爱Python");
        }
    }
}
```

### while循环

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        int i = 10;
        int j = 0;
        while (j < i) {
            System.out.println("我爱Python");
            j++;
        }
    }
}
```

### do...while循环

先do，再循环

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        int i = 10;
        int j = 0;
        do {
            System.out.println("我爱Python");
            j++;
        } while (j < i);
    }
}
```

### break和continue

#### break

直接跳出循环

#### continue

跳出当前循环，继续下一次循环

## 模块五 数组

### 数组的定义

数组概述：数组本身是一个容器，数组本身属于引用数据类型

1. 动态初始化：只指定了长度
2. 静态初始化：给了数据

```java
// 动态初始化
public class Demon01Scanner {
    public static void main(String[] args) {
        int i[] = new int[10];
        int[] o = new int[10];
    }
}
```

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        int i[] = new int[]{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int[] o = new int[]{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int[] h ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}; // 推荐使用
    }
}
```

### 数组的操作

#### 获取数组的长度

`数组名.length`

length是数组的一个属性，不是方法，所以不用带小括号

#### 数组的索引

元素在数组中的位置，索引从0开始

#### 数组存储元素

`数组名[索引] = 元素值`

#### 数组获取元素

`数组名[索引]`

1. 直接输出数组名，会输出数组的地址

#### 数组遍历元素

使用 for 循环，遍历数组中的所有元素。

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        int[] h ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        for (int j : h) {
            System.out.println(j);
        }
    }
}
```

#### 数组常见异常

1. ArrayIndexOutOfBoundsException - 数组索引越界异常
2. NullPointerException - 空指针异常

### 数组的高级操作

#### 数组复制

使用 for 循环，复制数组中的元素。

#### 数组扩容

申请一个新的比原数组空间大的数组，将原数组中的元素复制过去。

### 内存图

在java的世界中，将内存划分成了五块

1. stack  - 栈
   - 主要运行方法，方法的运行都会进栈内存运行，运行完毕之后，需要“弹栈”，释放内存。
2. heap   - 堆
   - 保存的是对象，数组，每new一次，都会在堆内存中开辟空间，并为这个空间分配一个地址值。
   - 堆内存中的元素，都有其默认值。
3. method area - 方法区
   - 代码的“预备区”，记录了类的信息及其方法的信息。
   - 方法区中，主要保存class文件及其中的信息。
4. native method stack - 本地方法栈
   - 本地方法可以理解为堆对java功能的扩充。
   - 很多功能，是java语言实现不了的，就需要依靠本地方法。
5. pc register - 寄存器

### 二维数组

```java
public class Demon01Scanner {
    public static void main(String[] args) {
        int[][] i = new int[10][5];
    }
}
```

## 模块六 方法

### 方法

#### 1. 方法的介绍和基本使用

问题：

之前，我们将所有功能都放在main方法中

造成了不好维护的局面

因此，我们要将功能封装成方法，方便以后调用和维护

方法：即拥有功能性功能的代码块

```java
修饰符 返回值类型 方法名(参数列表) {  
    方法体;
    return 返回值;
}
```

#### 2. 方法的重载

方法名相同，参数列表不相同的方法，才叫重载方法。

## 模块七 面向对象

封装、继承、多态

### 类和对象

1. 测试类：带main方法的类，用于测试运行代码的
2. 实体类：一类事物的抽象表现形式

#### 组成部分

1. 属性
2. 行为（方法）

#### 对象的理解

对象，一类事物的具体表现形式

1. 导包
   1. 同一个包下，不需要导包
   2. 特殊包：对于java.lang包下的类，不需要导包
2. 创建对象：想使用谁，就new谁
3. 调用方法

#### 匿名对象

匿名对象：没有名字的对象，直接使用new出来的对象，没有变量名，直接使用。

注意：涉及到赋值，不要使用匿名对象。

## 模块八 封装

### 什么是封装

封装：将属性和行为封装在一起，对外隐藏内部细节，对外提供统一的接口。（提高安全性）

### 关于private

私有化权限，将类的成员设置为私有的，外部无法直接访问，只能通过本对象的方法访问。

### get 和 set 方法

将成员封装起来并私有化后，我们还需要提供一个公共的接口（get set）方法。

set：设置成员属性值

get：获取成员属性值

### this关键字的基本使用

this：代表当前对象，this.属性名，this.方法名

用来区分重名的成员变量和局部变量

### 构造方法的定义和格式

构造方法：类名和方法名一致，并且能初始化对象的方法，叫做构造方法

无参构造：没有参数，每个类默认包含

有参构造：指定参数，需要自己创建

定义一个有参构造之后，虚拟机不会再创建无参构造

特点：

1. 构造方法没有返回值，不能使用return语句
2. 不能有返回值属性

### JavaBean

JavaBean：JavaBean是一种Java语言写成的类，用于封装数据。

要求：

1. 类必须是具体的和公共的。
2. 并且有无参数的构造，和有参数的构造
3. 成员必须私有化，有get set方法

#### 包分层

1. com.foreveryang.controller -> 放和页面打交道的类（表现层）
2. com.foreveryang.service -> 放和业务处理相关的类（业务层）
3. com.foreveryang.dao -> 放和数据库打交道的类（持久层）
4. com.foreveryang.pojo -> 专门放JavaBean类
5. com.foreveryang.util -> 放工具类（工具类）

#### 在IDE中使用快捷键快速构造JavaBean类

alt + insert

### 封装扩展

将来的JavaBean，会和数据库中的表相对应

1. 类名 - 表名
2. 属性名 - 列名
3. 对象 - 每一行的数据
4. 属性值 - 表中每格的元素

## 模块九 面向对象补全

### static关键字

在类中，使用static修饰的成员变量，称为静态成员。

还能修饰一个方法。

静态成员**属于类**，而不是对象。

调用静态成员，直接使用`类名.成员名`

静态成员会随着类的加载而加载

#### static修饰成员的访问问题

1. 在静态方法中不能访问非静态成员（想要调用，需要new一个对象）
2. 在非静态方法中，可以访问静态成员和非静态成员
3. 在静态方法中能直接调用静态成员

同一类中，可以直接调用函数名

### 可变参数

方法参数位置，只明确了方法类型，没有明确方法个数

定义可变参数：参数类型...参数名

可变参数的本质是一个数组

参数位置不能连续写多个可变参数，而且当可变参数一起使用时，可变参数需要放到参数列表最后

```java
public class hello {
    public static void main(String[] args) {
        int sum = sum(1, 2, 3, 4, 6);
        System.out.println(sum);
    }

    public static int sum(int...nums) {
        int sum = 0;
        for (int i : nums) {
            sum += i;
        }
        return sum;
    }
}
```

### 递归

直接递归和间接递归

同时，递归必须要有出口，否则栈内存会溢出

### 数组常用算法

#### 1. 数组翻转
