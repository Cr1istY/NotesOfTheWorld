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

```java
public class Test01 {
    public static void main(String[] args) {
        int[] a = new int[10];
        for (int i = 0; i < a.length; i++) {
            a[i] = i;
        }
        for (int j : a) {
            System.out.print(j + "  ");
        }
        int min = 0;
        int max = a.length - 1;
        while (min <= max) {
            int temp = a[min];
            a[min] = a[max];
            a[max] = temp;
            min++;
            max--;
        }
        System.out.println(" ");
        for (int j : a) {
            System.out.print(j + "  ");
        }
    }
}
```

#### 2. 冒泡排序

```java
    public static void maoPao(int[] a) {
        for (int i = 0; i < a.length - 1; i++) {
            for (int j = 0; j < a.length - 1 - i; j++) {
                if (a[j] > a[j + 1]) {
                    int temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            }
        }
        for (int j : a) {
            System.out.print(j + "  ");
        }
    }
```

#### 3. 二分查找

```java
    public static void binarySearch(int[] a, int target) {
        int min = 0;
        int max = a.length - 1;
        while (min <= max) {
            int mid = (min + max) / 2;
            if (a[mid] == target) {
                System.out.println("第 " + mid + " 位");
                return;
            }
            else if (a[mid] < target) {
                min = mid + 1;
                continue;
            }
            else if (a[mid] > target) {
                max = mid - 1;
                continue;
            }
        }
    }
```

### 对象数组

数组可以用来存储对象

此时，数组中保存的是对象的地址，而不是对象的值

### 方法参数

#### 基本数据类型与引用数据类型

基本数据类型：四类八种

其他都属于引用数据类型

#### 基本数据类型作为方法参数传递

如果要修改基本数据类型的值，则必须使用引用数据类型

类似C语言中的指针

#### 引用数据类型作为方法参数传递

引用数据类型作方法参数传递时

传递的是对象的地址

#### 命令行参数

给main方法传递参数

## 案例 - 学生管理系统

### 学生类

```java
public class Student {
    private String name;
    private int age;
    private int grade;
    Student(String name, int age, int grade) {
        this.name = name;
        this.age = age;
        this.grade = grade;
    }
    Student() {}
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public int getGrade() {
        return grade;
    }
    public void setGrade(int grade) {
        this.grade = grade;
    }
}
```

---

## 下部

## 模块十 继承

重点：

1. 知道继承的好处
2. 会使用继承
3. 知道继承之后成员变量以及成员方法的访问
4. 方法的重写以及使用场景
5. 会使用this关键字调用当前对象
6. 使用super关键字调用父类对象
7. 会定义抽象方法和抽象类
8. 会重写抽象方法

### 继承

1. 定义一个父类，在其中定义重复性的代码
2. 定义一个子类，继承父类，并使用父类中非私有成员

```java
public class Teacher extends Employee{}
```

Teacher类继承了Employee类

子类不能使用父类的私有成员

#### 方法的重写

如果子类中有和父类相同的方法，则子类方法会覆盖父类方法（使用@Override注解查看）

注意事项：

1. 子类重写父类方法后，权限必须要保证大于等于父类权限（权限指的是访问权限）
   - public > protected > default > private
2. 子类重写父类方法，方法名和参数列表要一致
3. 私有方法不能被重写，构造方法不能被重写，静态方法不能被重写
4. 子类重写父类方法之后，返回值类型应该是父类方法返回值类型的子类类型

##### 使用场景

功能的升级改造

### super和this

java在处理继承的类时，在创建子类对象时，会首先创建父类对象（进行无参构造），然后再创建子类对象

每个构造方法的第一行，默认都会有一个super()，虚拟机自动提供

#### super和this的具体使用

super代表的是父类引用，可以调用父类中的成员

1. 调用父类构造方法
2. 调用父类成员方法
3. 调用父类成员变量

super需要在子类中使用

this代表的是当前对象，可以调用当前对象的成员

### 继承的特点

继承只能单继承，不能多继承（Cpp中的菱形继承）

继承支持多层继承

一个父类可以有多个子类（基类的创建）

构造方法不能继承和重写

私有方法和静态方法可以被继承，但不能被重写

### 抽象

将共有的方法抽取出来，形成父类

但抽取出来的方法无法被确定，即不用写方法体

没有方法体的方法可以被写成抽象方法

有抽象方法的类，叫做抽象类

#### 定义抽象类

使用关键字abstract定义抽象方法和抽象类

1. 抽象方法所在的类一定要是抽象类
2. 抽象类中不一定非得有抽象方法

```java
public abstract class Human {
    abstract void eat();
}
```

子类在继承抽象父类时，必须重写所有的抽象方法

同时，抽象类不能被实例化

抽象类可以被看成一类事物的标准，只要属于这类事物，都必须要拥有抽象类中的方法，必须要自我实现

注意事项：

1. 抽象类不能被实例化
2. 抽象类中不一定非得有抽象方法，但抽象方法必须属于抽象类
3. 抽象类的子类必须重写父类中的所有抽象方法，否则编译报错。（除非子类也是抽象类）
4. 抽象类可以有构造方法，给子类使用，以初始化父类中的成员

## 模块十一 - 接口和多态

### 接口

接口：一个引用数据类型，是一种标准和规范

使用：interface 关键字定义接口

`public interface InterfaceName{}`

实现接口类叫做实现类

`public class ClassName implements InterfaceName{}`

接口作为一个规范，其中的成员很单一

#### 接口的使用

1. 定义接口
2. 实现接口
3. 使用：
   1. 实现类实现接口
   2. 重写接口中的抽象方法
   3. 创建实现类对象
   4. 调用重写方法

```java
public interface USB {
    public abstract void open();
    public abstract void close();
}
```

```java
public class Mouse implements USB {
    @Override
    public void open() {
        System.out.println("Mouse open");
    }
    @Override
    public void close() {
        System.out.println("Mouse close");
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Mouse mouse = new Mouse();
        mouse.open();
        mouse.close();
    }
}
```

#### 接口中的成员

##### 1. 抽象方法

##### 2. 默认方法

默认方法应该出现在接口中，并且使用default关键字修饰

##### 3. 静态方法

默认方法和静态方法 - 作为临时加的小功能使用

##### 4. 成员变量

public static final int MAX_SPEED = 100;

final - 代表最终，被它修饰的变量不能二次赋值，可以被视为常量

接口名直接调用即可

#### 接口的特点

1. 接口可以多继承，一个接口可以继承多个接口
2. 接口可以多实现，一个类可以同时实现多个接口
3. 一个子类，可以继承父类的同时，去实现多个接口

继承也好，实现接口也罢，只要是父类中的或者接口中的抽象方法，子类必须重写，否则就会报错

当一个类实现多个接口时，接口中的方法重名，则必须重写，且只需要重写一次

##### 接口和抽象类的区别

相同：

1. 都位于继承体系的顶端，用于被其他类实现或继承
2. 都不能实例化（new）
3. 都包含抽象方法

不同：

1. 抽象类可以有成员变量，构造，成员方法，抽象方法等
2. 接口：成员单一，一般抽取接口，抽取的都是方法，视为功能的大集合
3. 类不能多继承，但是接口可以

### 多态

1. 前提：
   1. 必须要有子父类继承或者接口实现关系
   2. 必须有方法的重写（如果没有重写，多态就没有意义）
   3. new对象，父类引用指向子类对象（Fu fu = new Zi();） - 大类型接收了一个小类型的数据
2. 多态下不能直接调用子类特有功能

#### 多态下成员访问特点

`Fu fu = new Zi();`

成员变量，看等号左边是谁

成员方法，具有多态性（先调用重写的方法），看等号右边是谁

#### 多态的好处

问题：如果使用原始方式new对象，那什么都能调用；而多态却只能调用重写的方法，那为什么要使用多态呢？

##### 原始方式和多态方式的区别

原始方式，扩展性差

多态形式，扩展性强

#### 多态中的转型

##### 向上转型

父类引用指向子类对象

##### 向下转型

强制转换，将大类型强制转换为小类型

向下转型后，就可以调用子类的特有功能

##### 可能的问题

类型转换异常

在向下转型之前，需要先进行类型判断

（instanceof）

## 模块十二 - 面向对象其他

### 权限修饰符

1. public - 公有，任何地方都可以访问
2. protected - 保护，本包及其子类可以访问
3. default - 默认，本包可以访问
4. private - 私有，只有本类可以访问

|修饰符|public|protected|default|private|
|:---:|:---:|:---:|:---:|:---:|
|同类|√|√|√|√|
|同包不同类|√|√|√|No|
|不同包子父类|√|√|No|No|
|不同包非子父类|√|No|No|No|

编写代码时，推荐

- 属性用private - 封装思想
- 成员方法使用public - 便于调用
- 构造public - 便于new对象

### final关键字

final：最终的，可以用于

- 修饰类：不能被继承（太监类）
- 修饰方法：不能被重写
- 修饰成员变量：不能被修改
- 修饰局部变量：保证变量的线程安全
- 修饰一个对象：不能改变对象的引用，但可以改变其中的属性

abstract不能和final同时使用

### 代码块

#### 构造代码块

构造代码块每次都会优先于构造方法执行

```java
{

}
```

每new一次，执行一次

#### 静态代码块

```java
static{

}
```

静态代码块只会执行一次，在类加载时执行，且优先于静态成员变量和静态方法执行，且优于构造代码块（最先执行）

#### 静态代码块使用场景

如果想让一些数据最先初始化，那么就可以使用静态代码块

### 内部类

在类里面定义的类

当一个事物的内部，还有一部分需要完整的结构去描述，而这个内部的完整结构又只为外部事物提供服务，那么整个内部的完成结构最好使用内部类

例如，人类中，可以添加一个心脏类

分类：

1. 成员内部类
2. 局部内部类
3. **匿名内部类**

#### 静态成员内部类

格式：直接在定义的时候，加上static关键字

```java
public class Outer {
    public static class Inner {

    }
}
```

注意：

1. 内部类可以定义属性、方法、构造等。
2. 静态内部类可以被final或者abstract修饰。
   1. 被final修饰后，不能被继承
   2. 被abstract修饰后，不能被实例化（new）
3. 静态内部类不能调用外部的非静态成员
4. 内部类还可以被四种权限修饰符修饰。

调用**静态**内部类成员：

```java
Outer.Inner inner = new Outer.Inner();
```

调用**非静态**内部类成员：

```java
Outer.Inner inner = new Outer().new Inner();
```

#### 内部类重名问题

#### 局部内部类问题

#### 内部类，接口和抽象类和普通类作为方法参数和返回值

##### 接口作为参数和返回值

接口作为参数传递，实参传进实现类对象

接口作为返回值，返回实现类对象，用接口对象接受

##### 抽象类作为参数和返回值

抽象类作为参数传递，实参传进抽象类子类对象

抽象类作为方法返回值的情况，需要返回一个实现抽象类所有抽象方法的子类对象

##### 类作为参数和返回值

会经常碰到调用的方法要接收的是一个类类型的情况，那么这时，要向方法中传入该类的对象

会经常碰到返回一个类类型的返回值，那么这时，该方法要返回一个该类的对象

#### 局部内部类实际操作

局部内部类是定义在外部类的局部位置，且一定要有类名；

#### 匿名内部类

匿名内部类可以使你的代码更加简洁，你可以在定义一个类的同时对其进行实例化。

所谓的匿名内部类，就是没有显式声明出类名的内部类

问题：单纯使用一次接口中的方法

1. 创建实现类，实现接口
2. 重写方法
3. 创建实现类对象
4. 调用方法

如果只想使用一次接口中的方法，那么就可以使用匿名内部类

将上面四步四合一

将匿名类当作一种格式

```java
new 接口/抽象类(){
    重写方法
}.重写方法();

// 上面为匿名，下面为有名

类名 对象名 = new 接口/抽象类(){
    重写方法
}
对象名.重写方法();
```

## 模块十三 - 异常_Object

### API文档

API：Application Programming Interface，**应用程序编程接口**，就是接口，就是定义了接口的类，就是接口类

说白了，API就是定义出来的类、接口，以及其中的方法

API文档，就是方便使用者使用的文档，是程序员的“字典”

### 异常

#### 异常的介绍

代码出现了不正常的现象，就叫做异常

Error ：错误 代码出现了重大错误，需要重写

Exception ：异常 代码出现了异常，可以处理，也可以不处理

1. 编译时异常：编译时出现的错误，编译器会提醒，但是不会导致程序无法运行
2. 运行时异常：运行时出现的错误，编译器不会提醒，但是会终止程序运行，导致程序崩溃

当虚拟机运行时，如果代码中出现了异常，那么虚拟机会将异常对象创建出来，并交给JVM处理

最后，抛出异常信息，终止程序

#### 创建异常对象

创建异常对象，只是为了日后学习如何处理异常

关键字：`throw`

```java
throw new 异常类();
```

#### 处理异常

使用关键字：`throws`

##### 异常处理方式一 throws

```java
throw 异常;
```

```java
public class Demo01Throws {
    public static void main(String[] args) throws Exception {
        System.out.println(10/0);
        System.out.println("程序继续执行");
    }
}
```

1. 格式：在方法参数和方法体之间位置写上
2. 处理异常，将异常往上抛

如果`throws`抛出多个异常的时候呈父子类关系，可以直接抛出父类（直接`throws Exception`）

##### 异常处理方式二 try-catch-finally

```java
try{
    可能出现异常的代码
}catch(异常类名 e){
    处理有异常的代码 ->  将来会将异常信息保存到日志文件中
}
```

e是自定义的对象名

日志文件，用来保存使用程序的错误信息以及使用信息

##### 多个catch

对于不同的异常，使用不同的catch处理

把异常类名换成不同的异常类名，实现多个catch以应对不同的异常情况

#### finally关键字

代表不管是否触发异常，都会执行的代码块

**即便return也会执行finally**，除非有system.exit(0)

##### finally使用场景

1. 关闭资源
2. 释放资源，如果对象没有用了，GC会自动回收，而有一些对象是不能被GC回收的，比如数据库连接，文件流等，所以需要我们自己做释放资源操作

#### 抛异常时需要注意的事项

1. 父类中的方法抛了异常，子类可抛可不抛
2. 父类中的方法没有抛异常，子类不能抛

重写尽量形式和父类保持一致

#### try-catch 和 throws 的时机

1. 如果处理异常后，还想让虚拟机继续运行，那么使用try-catch
2. 如果方法之间是递进关系，可以先throws，再在最后进行try-catch

#### 自定义异常

定义一个类，继承自Exception或者RuntimeException，重写构造方法即可

如果继承Exception，那么这个类就是编译时异常

如果继承RuntimeException，那么这个类就是运行时异常

##### 打印异常信息的三个方法

三者皆出自Throwable类

1. String toString()：获取异常简单信息
2. String getMessage()：获取异常信息
3. void printStackTrace()：获取异常信息，同时将异常信息输出到控制台

### Object类

所有类的根类，是java中的祖宗类

#### Object toString()

返回该对象的字符串表示形式

> getClass().getName() + '@' + Integer.toHexString(hashCode())

注意：

1. 如果没有重写toString方法，那么直接输出对象名时，默认调用的是toString方法，返回的是内存地址
2. 如果重写了toString方法，返回的是对象的被重写的内容

#### Object equals

比较的是两个对象的地址

```java
public boolean equals(Object obj) {
    return (this == obj);
}
```

对于 == , 如果是基本数据类型，那么比较的是值，如果是引用数据类型，那么比较的是地址

注意：

1. 如果没有重写Object中的equals方法，那么默认调用的是Object中的equals方法，比较的是地址
2. 如果重写了Object中的equals方法，那么比较的是对象中的内容

重写equals方法需要注意。

#### Object clone

复制一个属性值一样的新对象

被克隆的对象，必须实现Cloneable接口，然后重写克隆方法

### 经典接口

#### 比较大小：java.lang.Comparable接口

引用数据类型是不能比较大小的，为了解决这个问题，java给所有引用数据类型的大小比较，指定了一个标准，就是Comparable接口

```java
package java.lang;

public interface Comparable {
    int compareTo(Object o);
}
```

第一步：哪个类的对象要比较大小，哪个类就实现java.lang.Comparable接口，并重写方法

第二步：对象比较大小时，通过对象调用compareTo方法，根据方法的返回值决定谁大谁小。

- this对象，（调用compareTo方法的对象）减 指定对象（传入compareTo()的参数对象）大于0，返回正整数
- 小于0，返回负整数
- 等于0，返回0

## 模块十四 - API

### String字符串

#### String概述

1. String类是一个字符序列，用于表示和操作字符串
2. 特点：
   1. Java中所有的字符串都是以String实例化而来的对象。（凡是带双引号的都是String类的对象）
   2. 字符串是个常量，他们的值创建后就不能更改。之后，对字符串的增删操作，实际上是创建了一个新的字符串对象，然后将新的字符串对象赋给原来的字符串变量。
   3. String对象是不可变的，所以可以被共享。

#### String原理

1. jdk8：String是一个被final修饰的char数组。
2. jdk9开始：是一个被final修饰的byte数组。

一个char占两个字节，而一个byte占一个字节

优化了内存

#### String的创建

```java
String();
String(String s)
String(char[] value)
String(byte[] bytes)
```

简化形式：`String s = "abc";`

#### String面试题说明

```java
String s1 = "abc";
String s2 = "abc";
String s3 = new String("abc");
System.out.println(s1 == s2); // true
System.out.println(s1 == s3); // false
System.out.println(s2 == s3); // false
```

引用数据类型，比较的是地址，s1和s2是共享地址的，所以s1和s2比较时，返回true

1. String s1 = new String("abc"); 共有两个对象，一个是new本身，一个是"abc'
2. String s2 = new String("abc"); 共创建了一个或两个，要看abc有没有提前创建出来

```java
String s1 = "hello";
String s2 = "world";
String s3 = "helloworld"
String s4 = "hello" + "world";
String s5 = s1 + "world";
String s6 = s1 + s2;

System.out.println(s3 == s4); // true
System.out.println(s3 == s5); // false
System.out.println(s3 == s6); // false
```

#### String的常用方法

1. 判断方法，`boolean equals(String s)`|`boolean equalsIgnoreCase(String s)`
    - 实际开发中，为了防止出现空指针，一般会把**确切的值**作为对象，然后调用方法。
    - 或者使用`Objects.equals(String s1, String s2)`，该方法会自动判断空指针。
2. 获取功能：
   1. 获取字符串长度，调用`s.length()`。返回`int`
   2. 字符串拼接，调用`s.concat(String s)`。返回`String`
   3. 根据索引获取对应字符，调用`s.charAt(int index)`。返回`char`
   4. 获取指定字符串在大字符串中第一次出现的位置，调用`s.indexOf(String s)`。返回`int`
   5. 截取字符串，从指定索引开始截取到末尾，调用`s.substring(int index)`。返回`String`
   6. 截取字符串，从指定索引开始截取到指定索引结束，调用`s.substring(int start, int end)`。返回`String`（含头不含尾）
3. 转换功能：
   1. 将字符串转换为字符数组，调用`s.toCharArray()`。返回`char[]`
   2. 将字符串转换为字节数组，调用`s.getBytes()`。返回`byte[]`
   3. 替换字符，调用`s.replace(char oldChar, char newChar)`。返回`String`
4. 分割功能：
   1. `String[] split(String regex)`；regex表示正则表达式，返回`String[]`
5. 其他方法：
   1. `boolean isEmpty()`：判断字符串是否为空，返回`boolean`
   2. `String toLowerCase()`：将字符串转换为小写，返回`String`
   3. `String toUpperCase()`：将字符串转换为大写，返回`String`
   4. `boolean contains(String s)`：判断字符串是否包含指定字符串，返回`boolean`
   5. `boolean endsWith(String s)`：判断字符串是否以指定字符串结束，返回`boolean`
   6. `boolean startsWith(String s)`：判断字符串是否以指定字符串开始，返回`boolean`
   7. `String trim()`：去除字符串两端的空格，返回`String`

### StringBuilder

#### stringBuilder概述

一个可变的字符序列，此类提供了一个与StringBuffer兼容的API，但性能更好，但不保证同步（线程不安全）

作用：主要用于拼接字符串

为什么要使用？

1. String拼接字符有缺点：会不断产生新字符串对象。
2. StringBuilder自带一个缓存区，字符串可以改变。拼接字符串后，都会在缓存区中保存，不会产生新对象。

#### StringBuilder的特点

1. 底部自带缓存区，此缓存区是没有被final修饰的byte数组，默认长度为15
2. 如果超出了数组长度，数组会自动扩容，创建一个新长度的数组，然后将新数组的地址值重新赋值给老数组
3. 默认每次扩容老数组的2倍+2，如果超出了这个数组，会按照实际扩容为主。

#### StringBuilder的使用

1. 创建对象：`StringBuilder s = new StringBuilder()`
2. 常用方法：
   1. append(String s)：添加字符串，返回`StringBuilder`（是自己）
   2. reverse()：反转字符串，返回`StringBuilder`（是自己）
   3. toString()：将`StringBuilder`转换为`String`，返回`String`

## 模块十五 - API


