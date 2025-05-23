# java 进阶

[尚硅谷java下](https://www.bilibili.com/video/BV1JZ421a7PX?spm_id_from=333.788.videopod.episodes&vd_source=1925e38de9174c77ef2d3cfdc2dea75d&p=96)

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

### 数学相关类 - Math

1. 数学工具类
2. 主要用于数学运算
3. 特点
   1. 构造方法私有
   2. 方法都是静态的
4. 使用：`Math.abs(int a)`

#### Math常用方法

1. int abs(int a)：绝对值
2. double ceill(double a)：向上取整
3. double floor(double a)：向下取整
4. long round(double a)：四舍五入
5. int max(int a, int b)：取最大值
6. int min(int a, int b)：取最小值

### BigInteger类

1. BigInteger类，用于处理大整数（大于long类型的整数，一般称之为**对象**）
2. 构造：BigInteger(String s) - 参数的格式必须为数字形式

#### BigInteger常用方法

1. BigInteger add(BigInteger b)：加法
2. BigInteger subtract(BigInteger b)：减法
3. BigInteger multiply(BigInteger b)：乘法
4. BigInteger divide(BigInteger b)：除法

BigInteger有上限，上限是内存扛不住的，所以，我们可以认为BigInteger无上限。

### BigDecimal类

直接使用float或者double，会有精度丢失，所以，我们使用BigDecimal类。

作用：主要用来解决精度损失问题。

构造：BigDecimal(String s)，s表示数字字符串

#### BigDecimal常用方法

1. BigDecimal valueOf(double d)：将double类型的数据转换为BigDecimal对象
2. 其他方法和BigInteger大致一样

#### 过时方法解决

过时的方法可以使用，但是不建议使用。（底层会有注解@Deprecated）

### 日期相关类 - Date

表示特定的瞬间，精确到毫秒。

1000 ms = 1 s

时间戳原点：1970年1月1日0时0分0秒0毫秒（UNIX系统起始时间、格林威治时间、位于0度时区）

一个时区相差15度，时间相差一个小时。

北京：东八区、东经116

#### Date的使用

Date类有构造方法，但是一般使用Date()，获取当前时间。

### Calendar日历类

日历类，是一个抽象类，不能直接创建对象。

月份：0表示1月，11表示12月。

#### 需要知道的字段

YEAR：年

MOUTH：月

DAY_OF_MONTH：日

等。

### SimpleDateFormat日期格式化类

按照自己想要的格式，将日期对象转换成字符串。

构造：SimpleDateFormat(String pattern)

pattern代表自己制定的日期格式：字母不能改变，但是中间的连接符可以改变。

### jdk8新日期类

#### LocalDate 本地日期

是一个不可变的日期对象，表示日期，通常为年月日

#### Period和Duration类

period用于计算时间的差值

duration也用于计算时间差

#### DataTimeFormatter日期格式化类

### 工具类 System系统相关类

1. 概述：系统相关类，是一个工具类
2. 特点：
   1. 构造私有，不能利用构造方法new对象
   2. 方法都是静态的
3. 使用：System. 类名直接调用

#### System方法

1. static long currentTimeMillis()：获取当前时间毫秒值，返回long类型
2. static void exit(int status)：退出程序，参数为状态码，返回void
3. static void arrcopy(Object src, int srcPos, Object dest, int destPos, int length)：复制数组，返回T[]

### Arrays数组工具类

1. 概述：数组工具类，是一个工具类
2. 特点：
   1. 构造私有，不能利用构造方法new对象
   2. 方法都是静态的

#### Arrays方法

1. static void sort(int[] a)：对数组进行排序，返回void
2. static String toString(int[] a)：将数组转换为字符串，返回String
3. static int binarySearch(int[] a, int key)：二分查找，返回int
4. static void copyOf(int[] original, int newLength)：数组扩容，返回int[]

### 包装类

1. 概述：包装类，将基本数据类型转换为对象，对象可以调用方法。

我们需要将基本类型转成包装类，而让基本类型有了类的特性，能够调用其中的方法。

#### Integer类

Integer是int类型的包装类

不推荐使用了，但是还得学

#### 装箱与拆箱

1. 装箱：将基本类型转化成对应的包装类
2. 拆箱：将包装类转化成对应的基本类型

使用：Integer i = 5;

自动进行拆箱和装箱。

## 模块十六 - 多线程

### 多线程基本了解

#### 线程和进程

进程：在内存中执行的应用程序叫进程

线程：进程中最小的执行单元，负责当前进程中程序的运行

一个进程中至少要有一个线程，如果一个进程中有多个线程，那么这个进程就是多线程的。

简单理解：一个功能需要一条线程。

使用场景：软件中的耗时操作，所有的聊天软件，后台服务器

一个线程可以干一件事，同时就可以做多件事情，提高了CPU的利用率

#### 并发和并行

并行：在同一时刻，有多个执行在多个CPU上（很多人做很多事）

并发：在同一个时刻，有多个指令在单个CPU上，交替执行（一个人做多个事）

单核CPU通过高速切换执行的方式，造成了同时执行多个指令的效果。

#### CPU调度

1. 分时调度：所有线程轮流获取CPU的使用权，并且平均分配每个线程占用CPU的时间片。
2. 抢占式调度：多个线程轮流抢占获取CPU的使用权，并且优先级高的线程优先获取CPU的使用权。

java程序，是抢占式调度。

#### 主线程

CPU和内存之间，专门为main方法开辟和服务的线程。

### 创建线程方式

#### 第一种方式 - 继承 Thread类

1. 定义一个类，继承Thread
2. 重写run方法，在run方法中设置线程任务（所谓的线程任务就是线程要完成的具体代码）
3. 去创建自定义线程类的对象
4. 调用Thread中的start方法，开启线程，jvm自动调用run方法

```java
package cn.foreveryang.thread;

public class Test {
    public static void main(String[] args) {
        // 创建线程对象
        MyThread t1 = new MyThread();
        t1.start();

        for (int i = 0; i < 10; i++) {
            System.out.println("Main ... " + i);
        }
    }
}
```

```java
package cn.foreveryang.thread;

public class MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("My Thread ... " + i);
        }
    }
}
```

#### 多线程原理

每创建一个线程，都会新创建一个线程栈

同一个线程对象不能连续使用start方法，如果想要再新建一个线程，需要创建新的线程对象

#### Thread中的方法

void start()：启动线程，调用当前线程的run方法

void run()：线程任务，线程要完成的具体代码（需要重写）

String getName()：获取线程名称

void setName(String name)：设置线程名称

static Thread currentThread()：获取当前线程对象

static void sleep(long millis)：让当前线程休眠，单位毫秒

在重写的run方法中有异常只能try，不能throws

因为继承的Thread类中run方法没有抛出异常，所以不能throws

#### Thread类中的其他方法

void setPriority(int newPriority)：设置线程优先级，1-10

优先级越高，越容易使用CPU

int getPriority()：获取线程优先级

void setDaemon(boolean daemon)：设置线程为守护线程，默认为用户线程

static void yield()：让当前线程释放CPU，让CPU去执行其他线程

void join()：插入线程或插队线程

##### 线程优先级

Thread.MIN_PRIORITY：1

Thread.NORM_PRIORITY：5

Thread.MAX_PRIORITY：10

#### 守护线程

当线程为守护线程时，所有用户线程执行完毕，守护线程也会执行完毕

使用场景：QQ聊天时，

#### 礼让线程

让两个线程尽可能交替运行。

注意：只是尽可能的平衡，不是绝对的交替

#### 插入线程

### 创建线程方式二 - 实现Runnable接口

1. 创建一个类，实现Runnable接口
2. 重写run方法，设置线程任务
3. 利用Thread的构造方法，Thread(Runnable target)，创建Thread对象，将自定义的类的实例作为参数传递
4. 调用Thread的start方法，开启新线程，执行run方法

### 两种实现多线程的方式区别

1. 继承Thread类：单继承，有局限
2. 实现Runnable接口：多继承，可以有多个父类

### 创建线程方式三 - 匿名内部类创建多线程

匿名多线程是在实现Runnable接口的基础上的

```java
new Thread (new Runnable() {
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("My Thread ... " + i);
        }
    }
}).start();
```

### 线程安全问题

当多个线程访问同一个资源时，导致了资源有问题

解决方法：进行上锁

#### 同步代码块

使用`synchronized`关键字

```java
synchronized (注意对象) {
    线程可能出现不安全的代码
}
```

1. 任意对象，就是我们的锁对象
2. 执行：一个线程拿到锁之后，会进入到同步代码块中执行，在此期间，其他线程拿不到锁，就进不去同步代码块，需要在同步代码块外等待排队

#### 同步方法

##### 非静态同步方法

```java
修饰符 synchronized 返回值类型 方法名(参数列表) {

}
```

非静态的同步方法，默认锁是this

### 死锁和线程状态

#### 死锁

两个或者两个以上的线程，因争夺资源而互相等待，造成线程的阻塞，最终导致所有线程都处于阻塞状态，造成系统假死

#### 线程生命周期

1. 新建New
2. 可运行Runnable
3. 锁阻塞Blocked
4. 无限等待Waiting
5. 计时等待Timed Waiting
6. 被终止Terminated

##### sleep和wait的区别

sleep：线程睡眠，在睡眠的过程中，线程不会释放锁，其他的线程无法抢占他的锁，设置的时间一到，自动醒来，继续执行

wait：线程等待，等待的过程中会释放锁，其他线程就有可能抢到锁，如果被唤醒，则会和其他线程抢锁

##### notify

notify会唤醒正在等待的线程，一次只能唤醒一条等待的线程，如果多条线程正在等待，notify就会随机唤醒一条线程

## 模块十七 - 多线程补充

### 等待唤醒

要求：一个线程生产，一个线程消费，不能连续生产，也不能连续消费

即线程之间的通讯

|方法|说明|
|:--|:--|
|void wait()|等待|
|void notify()|唤醒|
|void notifyAll()|唤醒所有|

wait和notify方法需要锁对象调用，所以需要用到同步代码块当中，并且是同一个锁对象

#### 等待唤醒案例分析

```java
package cn.foreveryang.baozipu;

public class BaoZiPu {
    private int count;
    private boolean flag;

    public BaoZiPu() {
        count = 0;
        flag = false;
    }

    public BaoZiPu(int count, boolean flag) {
        this.count = count;
        this.flag = flag;
    }

    public void getCount() {
        System.out.println("消费了---第" + count + "个包子");
    }

    public void setCount() {
        count++;
        System.out.println("生产了---第" + count + "个包子");
    }

    public boolean isFlag() {
        return flag;
    }

    public void setFlag(boolean flag) {
        this.flag = flag;
    }
}

```

```java
package cn.foreveryang.baozipu;

public class Consumer implements Runnable {
    private BaoZiPu baozipu;

    public Consumer(BaoZiPu baozipu) {
        this.baozipu = baozipu;
    }


    @Override
    public void run() {
        while (true) {

            try {
                Thread.sleep(100L);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }

            synchronized (baozipu) {
                // 1. 判断flag是否为true，如果是false，证明没有包子，消费线程等待
                if (baozipu.isFlag() == false) {
                    try {
                        baozipu.wait();
                    } catch (InterruptedException e) {
                        throw new RuntimeException(e);
                    }
                }

                // 2. 如果flag为true，证明有包子，开始消费
                baozipu.getCount();
                // 3. 改变flag为false
                baozipu.setFlag(false);
                // 4. 唤醒生产线程
                baozipu.notify();
            }
        }
    }
}

```

```java
package cn.foreveryang.baozipu;

public class Product implements Runnable {
    private BaoZiPu baozipu;

    public Product(BaoZiPu baozipu) {
        this.baozipu = baozipu;
    }


    @Override
    public void run() {
        while (true) {

            try {
                Thread.sleep(100L);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }

             synchronized (baozipu) {
                 // 1. 判断flag是否为true，如果是true，证明有包子，生产线程等待
                 if (baozipu.isFlag() == true) {
                     try {
                         baozipu.wait();
                     } catch (InterruptedException e) {
                         throw new RuntimeException(e);
                     }
                 }

                 // 2. 如果flag为false，证明没有包子，开始生产
                 baozipu.setCount();
                 // 3. 改变flag为true
                 baozipu.setFlag(true);
                 // 4. 唤醒消费线程
                 baozipu.notify();
             }
        }
    }
}
```

```java
package cn.foreveryang.baozipu;

public class Test {
    public static void main(String[] args) {
        BaoZiPu baozipu = new BaoZiPu();
        Product product = new Product(baozipu);
        Consumer consumer = new Consumer(baozipu);
        Thread t1 = new Thread(product);
        Thread t2 = new Thread(consumer);

        t1.start();
        t2.start();
    }
}

```

#### Lock锁的使用

Lock是一个接口

实现类：ReentrantLock

使用方法：lock获取锁，unlock释放锁

使用多态的方式创建对象`Lock lock = new ReentrantLock();`

syncronized和Lock锁的区别：

1. syncronized是JVM内置的线程同步机制，不管是同步代码块还是同步方法，都需要在结束{}后，释放锁对象
2. Lock是JDK提供的线程同步机制，是通过两个方法来进行上锁和解锁的，lock()和unlock()，更灵活

#### 实现多线程三 - Callable接口

`Callable<V>`是一个接口

方法：`V call()` - 设置线程任务，类似于run方法

call和run的区别：

1. 相同点：都是设置线程任务，都是需要重写
2. 不同点：call方法可以抛出异常且有返回值，run方法不可以且没有返回值

##### V 是 泛型

泛型：用于指定我们操作什么类型的数据，<> 中只能写引用数据类型，如果泛型不写，默认为Object

指定泛型是什么类型，重写的call方法，返回的就是什么类型

##### call方法返回值接收

`FutureTask<V>` 实现了`Future<V>`接口

V get() 获取call方法的返回值

### 线程池

线程池用于避免频繁的创建线程和销毁线程，将线程进行频繁使用，提高效率。

#### 线程池的创建

```java
static ExecutorService newFixedThreadPool(int nThreads)
```

1. nThreads - 线程池中线程的数量
2. 返回值 - 返回了线程池，用来管理线程对象
3. 执行线程任务，ExecutorService中的方法
   1. `Future<?> submit(Runnable task)` - 提交Runnable任务，返回一个Future对象，可以获取任务执行结果
   2. `Future<T> submit(Callable<T> task)` - 提交Callable任务，返回一个Future对象，可以获取任务执行结果
4. submit方法，返回一个Future对象，可以获取任务执行结果，Future是一个接口，用于接收call方法的返回值

### Timer定时器

1. 定时器，使用空参进行构造
2. 方法：void schedule(TimerTask task, Date firstTime, long delay)

- task - 抽象类，是Runnable的实现类
- firstTime - 第一次执行时间
- delay - 间隔时间（使用ms值）

## 模块十八 - 集合

### Collection接口

#### 单列集合框架

集合，是一个长度可变的容器

集合，只能存储引用数据类型，不能存储基本数据类型

分类：

1. 单列集合：一个元素就一个组成部分 list.add(Object o)
2. 双列集合：一个元素由两个部分组成：key和value map.put(K key, V value)

所有的单列集合都有一个顶级接口，Collection，子接口list、set继承Collection

list接口实现类：ArrayList、LinkedList、Vector

set接口实现类：HashSet、LinkedHashSet、TreeSet

##### ArrayList集合

1. 元素有序
2. 元素可重复
3. 有索引
4. 线程不安全
5. 底层数据结构是数组

##### LikedList集合

1. 元素有序
2. 元素可重复
3. 有索引
4. 线程不安全
5. 底层数据结构是双向链表

LinkedList**本质上无索引**，但是java为其提供了很多根据索引操作元素的方法

##### Vector集合

1. 不常用
2. 元素有序
3. 元素可重复
4. 有索引
5. 线程安全（慢，效率低）
6. 底层数据结构是数组

##### HashSet集合

1. 元素无序
2. 元素唯一
3. 无索引
4. 线程不安全
5. 底层数据结构是哈希表

##### LinkedHashSet集合

是HashSet的子类

1. 元素有序
2. 元素唯一
3. 无索引
4. 线程不安全
5. 底层数据结构是哈希表加双向链表

##### TreeSet集合

1. 可对元素进行排序
2. 元素唯一
3. 无索引
4. 线程不完全
5. 底层数据结构是红黑树

#### Collection

1. 概述：单列集合的顶级接口
2. 使用：
   1. 创建：`Collection<E> c = new 实现类对象<E>();`
   2. `<E>`是泛型，决定了集合中能存储的数据类型，只能写引用数据类型，不写，默认为Object

### 迭代器

1. 概述：Iterator接口，是一个迭代器，用于遍历集合
2. 主要作用：遍历集合
3. 获取：使用Collection中的方法

```java
ArrayList<String> list = new ArrayList<String>();
list.add("张三");
list.add("李四");
// 获取迭代器对象
Iterator<String> iterator = list.iterator();
while (iterator.hasNext()) {
    String next = iterator.next();
    System.out.println(next);
}
```

注意：next方法在获取时，不要连续使用多次

当迭代器遍历完所有元素后，再使用next方法，会报NoSuchElementException异常

#### 迭代器底层实现

```java
int cursor; // 下一个元素索引位置
int lastRet = -1; // 上一个元素索引位置
```

并发修改异常：

当 elements.modCount != expectedModCount 是，抛出ConcurrentModificationException异常

```java
if (modCount != expectedModCount) {
    throw new ConcurrentModificationException();
} // 修改次数不等于期望修改次数
```

最终结论：我们调用了add方法，而add方法底层只给modCount++，但是再次调用next方法时，并没有给修改后的modCount重新赋值给expectedModCount

使用迭代器或增强for迭代集合的过程中，不要随意修改集合中的元素

### 数据结构

数据结构是一种具有一定的逻辑关系，在计算机中应用某种存储结构，并且封装了相应操作的数据元素集合。

他包含三方面的内容：逻辑关系、存储关系及操作

#### 栈

#### 队列

#### 数组

#### 链表

#### 树

#### 图

### List接口

1. 是Collection的子接口
2. 常见的实现类：ArrayList、LinkedList、Vector

#### ArrayList集合的使用和源码分析

1. **概述**
     * `ArrayList` 是 Java 中一个非常常用的集合类，它位于`java.util`包下。`ArrayList` 实现了`List`接口，采用动态数组的方式存储数据，这意味着它的元素是有序的，并且可以根据需要自动调整大小。
     * 它允许对元素进行随机访问，通过索引来快速定位元素，这使得在需要频繁访问元素的场景下非常高效。但是，在中间位置插入或者删除元素可能会比较慢，因为这会导致数组中后续元素的移动。

  2. **构造方法**
     * **无参构造方法**
       * `ArrayList()`：构造一个初始容量为 10 的空列表。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         ```

     * **带初始容量的构造方法**
       * `ArrayList(int initialCapacity)`：构造一个具有指定初始容量的空列表。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>(20);
         ```

     * **从集合构造**
       * `ArrayList(Collection<? extends E> c)`：构造一个包含指定集合元素的列表，这些元素的顺序是由集合的迭代器所返回的顺序决定的。
       * 示例代码：

         ```java
         ArrayList<String> oldList = new ArrayList<>();
         oldList.add("a");
         oldList.add("b");
         ArrayList<String> newList = new ArrayList<>(oldList);
         ```

  3. **常用方法**
     * **添加元素**
       * `boolean add(E e)`：将指定的元素添加到此列表的尾部。返回值是一个布尔值，固定为`true`。因为对于`ArrayList`来说，只要不是固定大小的列表，添加元素操作总是可以成功。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         System.out.println(list); // 输出：[a, b]
         ```

       * `void add(int index, E element)`：将指定的元素插入此列表中的指定位置。在插入位置及以后的元素都向后移动一个位置。如果指定的位置索引大于等于当前列表的大小，会抛出`IndexOutOfBoundsException`异常。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("c");
         list.add(1, "b");
         System.out.println(list); // 输出：[a, b, c]
         ```

     * **删除元素**
       * `E remove(int index)`：移除此列表中指定位置的元素，并返回该元素。在指定位置之后的元素都向前移动一个位置。如果索引超出范围，会抛出`IndexOutOfBoundsException`异常。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         list.add("c");
         String removedElement = list.remove(1);
         System.out.println(removedElement); // 输出：b
         System.out.println(list); // 输出：[a, c]
         ```

       * `boolean remove(Object o)`：移除此列表中首次出现的指定元素（如果存在）。如果列表中包含该元素，则返回`true`；否则返回`false`。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         list.add("a");
         boolean isRemoved = list.remove("a");
         System.out.println(isRemoved); // 输出：true
         System.out.println(list); // 输出：[b, a]
         ```

     * **修改元素**
       * `E set(int index, E element)`：用指定的元素替换此列表中指定位置的元素，并返回被替换的元素。如果索引超出范围，会抛出`IndexOutOfBoundsException`异常。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         String oldElement = list.set(0, "c");
         System.out.println(oldElement); // 输出：a
         System.out.println(list); // 输出：[c, b]
         ```

     * **获取元素**
       * `E get(int index)`：返回此列表中指定位置的元素。如果索引超出范围，会抛出`IndexOutOfBoundsException`异常。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         String element = list.get(1);
         System.out.println(element); // 输出：b
         ```

     * **查找元素**
       * `int indexOf(Object o)`：返回此列表中首次出现的指定元素的索引，如果此列表不包含该元素，则返回 -1。从列表的开头（索引 0）开始向后搜索。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         list.add("a");
         int index = list.indexOf("a");
         System.out.println(index); // 输出：0
         ```

       * `int lastIndexOf(Object o)`：返回此列表中最后出现的指定元素的索引，如果此列表不包含该元素，则返回 -1。从列表的结尾向后搜索。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         list.add("a");
         int index = list.lastIndexOf("a");
         System.out.println(index); // 输出：2
         ```

     * **列表操作**
       * `void clear()`：移除此列表中的所有元素。操作完成后，列表将为空。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         list.clear();
         System.out.println(list.isEmpty()); // 输出：true
         ```

       * `boolean isEmpty()`：如果此列表中没有元素，则返回`true`，否则返回`false`。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         System.out.println(list.isEmpty()); // 输出：true
         list.add("a");
         System.out.println(list.isEmpty()); // 输出：false
         ```

       * `int size()`：返回此列表中的元素个数。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         System.out.println(list.size()); // 输出：2
         ```

       * `boolean contains(Object o)`：如果此列表中包含指定的元素，则返回`true`，否则返回`false`。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         System.out.println(list.contains("a")); // 输出：true
         System.out.println(list.contains("c")); // 输出：false
         ```

       * `Object clone()`：返回此`ArrayList`实例的浅表复制。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         ArrayList<String> cloneList = (ArrayList<String>) list.clone();
         System.out.println(cloneList); // 输出：[a, b]
         ```

       * `List<E> subList(int fromIndex, int toIndex)`：返回此列表从`fromIndex`（包含）到`toIndex`（不包含）的子列表视图。如果`fromIndex`大于等于`toIndex`，或者`fromIndex`或`toIndex`超出范围，会抛出`IllegalArgumentException`或`IndexOutOfBoundsException`异常。
       * 示例代码：

         ```java
         ArrayList<String> list = new ArrayList<>();
         list.add("a");
         list.add("b");
         list.add("c");
         list.add("d");
         List<String> sub = list.subList(1, 3);
         System.out.println(sub); // 输出：[b, c]
         ```

  4. **实现原理**
     * **动态数组实现**
       * `ArrayList` 底层是基于数组实现的。当添加元素时，如果当前数组的容量不足以存储新元素，它会自动扩容。扩容时，通常会将数组的大小增加到原来的 1.5 倍左右（这个倍数可能会因不同的 Java 版本而略有不同）。例如，初始容量为 10，当添加第 11 个元素时，数组会扩容为 15。
       * 这种扩容机制保证了`ArrayList`在大多数情况下能够高效地存储元素，而在元素数量增长较快时，也能通过扩容来适应存储需求。不过，扩容操作本身会带来一定的性能开销，因为需要创建新的数组并复制原有元素。

     * **线程安全**
       * `ArrayList`不是线程安全的。多个线程同时对`ArrayList`进行读写操作可能会导致数据不一致、异常等问题。如果需要在多线程环境下使用类似功能的集合，可以考虑使用`Vector`（它是线程安全的，但性能相对较低）或者通过`Collections.synchronizedList()`方法来包装`ArrayList`以实现线程安全。

     * **随机访问效率高**
       * 由于底层是数组结构，`ArrayList`的随机访问（通过索引获取元素）非常高效，时间复杂度为 O(1)。因为可以直接通过索引计算出元素在内存中的位置，而不需要像链表那样从头开始遍历。

     * **插入和删除效率低**
       * 在中间位置插入或者删除元素时，由于需要移动后续元素，时间复杂度为 O(n)。例如，在一个有 1000 个元素的`ArrayList`中，要在索引 0 处插入一个元素，后面的 999 个元素都需要向后移动一个位置，这会耗费较多时间。

#### LinkedList集合

`LinkedList` 是 Java 中的另一种常用集合类，它也实现了`List`接口，并且还实现了`Deque`（双端队列）接口。与`ArrayList`不同，`LinkedList`基于链表数据结构实现。以下是`LinkedList`的构造方法、常用方法以及实现原理的详细说明：

##### 构造方法

1. **无参构造方法**
   - `LinkedList()`：构造一个空的`LinkedList`。
   - 示例：
     ```java
     LinkedList<String> list = new LinkedList<>();
     ```

2. **从集合构造**
   - `LinkedList(Collection<? extends E> c)`：构造一个包含指定集合元素的`LinkedList`，这些元素的顺序由集合的迭代器返回。
   - 示例：
     ```java
     ArrayList<String> arrayList = new ArrayList<>();
     arrayList.add("a");
     arrayList.add("b");
     LinkedList<String> linkedList = new LinkedList<>(arrayList);
     ```

##### 常用方法

1. **添加元素**
   - `boolean add(E e)`：将指定的元素添加到此列表的尾部。
   - `void add(int index, E element)`：将指定的元素插入此列表中的指定位置。
   - `boolean addFirst(E e)`：将指定的元素插入此列表的开头。
   - `boolean addLast(E e)`：将指定的元素插入此列表的尾部（等同于`add(E e)`）。

2. **删除元素**
   - `E remove(int index)`：移除此列表中指定位置的元素，并返回被移除的元素。
   - `E removeFirst()`：移除此列表的第一个元素，并返回该元素。
   - `E removeLast()`：移除此列表的最后一个元素，并返回该元素。
   - `boolean remove(Object o)`：移除此列表中首次出现的指定元素（如果存在）。

3. **修改元素**
   - `E set(int index, E element)`：用指定的元素替换此列表中指定位置的元素。

4. **获取元素**
   - `E get(int index)`：返回此列表中指定位置的元素。
   - `E getFirst()`：返回此列表的第一个元素。
   - `E getLast()`：返回此列表的最后一个元素。

5. **查找元素**
   - `int indexOf(Object o)`：返回此列表中首次出现的指定元素的索引。
   - `int lastIndexOf(Object o)`：返回此列表中最后出现的指定元素的索引。

6. **列表操作**
   - `void clear()`：移除此列表中的所有元素。
   - `boolean isEmpty()`：如果此列表中没有元素，则返回`true`。
   - `int size()`：返回此列表中的元素个数。
   - `boolean contains(Object o)`：如果此列表中包含指定的元素，则返回`true`。
   - `List<E> subList(int fromIndex, int toIndex)`：返回此列表从`fromIndex`（包含）到`toIndex`（不包含）的子列表视图。

##### 实现原理

1. **链表结构**
   - `LinkedList`基于双向链表实现，每个元素都有一个前驱和后继节点，这使得在链表中间插入和删除元素非常高效，时间复杂度为O(1)，因为不需要移动其他元素。
   - `LinkedList`没有固定大小，可以根据需要动态增长和缩减。

2. **线程安全**
   - 和`ArrayList`一样，`LinkedList`也不是线程安全的。在多线程环境下需要额外的同步措施。

3. **随机访问效率**
   - 由于基于链表，`LinkedList`的随机访问效率较低，时间复杂度为O(n)，需要从头或尾遍历到指定位置。

4. **插入和删除效率**
   - 在链表头尾插入和删除元素的时间复杂度为O(1)，在中间插入和删除的时间复杂度为O(n)，因为需要找到指定位置。

总体来说，`LinkedList`适用于需要频繁在列表中间插入和删除元素的场景，而在需要频繁随机访问元素的场景下，`ArrayList`可能更为高效。

### 增强for与底层实现

1. 作用：遍历集合或者数组
2. 格式：for(集合/数组的数据类型 变量名 : 集合名/数组名)

注意：增强for遍历集合，底层实现为迭代器，遍历数组时，底层实现为普通for

## 模块十九 - 集合补充

### Collections工具类

1. 集合工具类
2. 特点：
   1. 构造私有
   2. 静态方法
3. 使用：类名直接调用

- `static void sort(List<T> list)`：对list集合进行排序，默认升序
- `static void sort(List<T> list, Comparator<? super T> c)`：对list集合进行排序，自定义比较器
- `static void shuffle(List<?> list)`：打乱集合
- `static <T> boolean addAll(Collection<T> c, T... elements)`：将可变参数添加到集合中

#### Comparable接口

方法：`int compareTo(T o) -> this-o(升序) o-this(降序)`

### 泛型

作用：统一数据类型，防止将来的数据装换异常

泛型中的类型必须是引用类型，不写默认为Object

为什么要使用泛型：规定数据类型，防止出现数据转换异常

定义层面：所有集合在定义的时候均使用泛型，增强灵活性

#### 如何定义泛型

##### 泛型类

```java
public class GenericClass<T> {

}
```

含有泛型的类，在new对象的时候才确定类型

```java
public class Box<T> {
   
  private T t;
 
  public void add(T t) {
    this.t = t;
  }
 
  public T get() {
    return t;
  }
 
  public static void main(String[] args) {
    Box<Integer> integerBox = new Box<Integer>();
    Box<String> stringBox = new Box<String>();
 
    integerBox.add(new Integer(10));
    stringBox.add(new String("菜鸟教程"));
 
    System.out.printf("整型值为 :%d\n\n", integerBox.get());
    System.out.printf("字符串为 :%s\n", stringBox.get());
  }
}
```

##### 泛型方法

格式：`修饰符 <T> 返回值类型 方法名(T[] arr)`

```java
public class GenericMethodTest
{
   // 泛型方法 printArray                         
   public static < E > void printArray( E[] inputArray )
   {
      // 输出数组元素            
         for ( E element : inputArray ){        
            System.out.printf( "%s ", element );
         }
         System.out.println();
    }
 
    public static void main( String args[] )
    {
        // 创建不同类型数组： Integer, Double 和 Character
        Integer[] intArray = { 1, 2, 3, 4, 5 };
        Double[] doubleArray = { 1.1, 2.2, 3.3, 4.4 };
        Character[] charArray = { 'H', 'E', 'L', 'L', 'O' };
 
        System.out.println( "整型数组元素为:" );
        printArray( intArray  ); // 传递一个整型数组
 
        System.out.println( "\n双精度型数组元素为:" );
        printArray( doubleArray ); // 传递一个双精度型数组
 
        System.out.println( "\n字符型数组元素为:" );
        printArray( charArray ); // 传递一个字符型数组
    } 
}
```

##### 泛型通配符

泛型通配符 `?` 表示未知类型，它允许你使用任意类型作为参数类型，并且可以接受任何类型作为返回值。

```java
import java.util.*;
 
public class GenericTest {
     
    public static void main(String[] args) {
        List<String> name = new ArrayList<String>();
        List<Integer> age = new ArrayList<Integer>();
        List<Number> number = new ArrayList<Number>();
        
        name.add("icon");
        age.add(18);
        number.add(314);
 
        getData(name);
        getData(age);
        getData(number);
       
   }
 
   public static void getData(List<?> data) {
      System.out.println("data :" + data.get(0));
   }
}
```

泛型的上限和下限：

1. 泛型的上限：`<? extends T>` 表示上限，表示只能接受T或者T的子类作为参数类型。
2. 泛型的下限：`<? super T>` 表示下限，表示只能接受T或者T的父类作为参数类型。

使用场景：

1. 在定义类、方法、接口的时候，如果类型不确定，我们可以考虑带泛型的类、方法、接口
2. 如果类型不确定，但是知道以后只能传递某个类的继承体系的子类或父类，我们可以考虑使用泛型

### 斗地主案例

使用集合方式实现：

```java
package cn.foreveryang.playcards;

import java.util.ArrayList;
import java.util.Collections;

public class Poker {
    public static void main(String[] args) {
        ArrayList<String> poker = getPoker();

        Collections.shuffle(poker);
        ArrayList<String> p1 = new ArrayList<>();
        ArrayList<String> p2 = new ArrayList<>();
        ArrayList<String> p3 = new ArrayList<>();
        ArrayList<String> base = new ArrayList<>();
        for (int i = 0; i < poker.size(); i++) {
            String s = poker.get(i);
            if (i >= 51) {
                base.add(s);
            } else if (i % 3 == 0) {
                p1.add(s);
            } else if (i % 3 == 1) {
                p2.add(s);
            } else {
                p3.add(s);
            }
        }

        System.out.println("3: " + p1);
        System.out.println("2: " + p2);
        System.out.println("1: " + p3);
        System.out.println("base: " + base);

    }

    private static ArrayList<String> getPoker() {
        ArrayList<String> color = new ArrayList<>();
        ArrayList<String> number = new ArrayList<>();
        ArrayList<String> poker = new ArrayList<>();
        color.add("♠");
        color.add("♥");
        color.add("♣");
        color.add("♦");

        for (int i = 2; i <= 10; i++) {
            number.add(i + "");
        }

        number.add("J");
        number.add("Q");
        number.add("K");
        number.add("A");

        for (String num : number) {
            for (String huase : color) {
                String pokerNum = num + huase;
                poker.add(pokerNum);
            }
        }

        poker.add("大王😀");
        poker.add("小王");
        return poker;
    }
}
```

### 各种树简要

#### 二叉树

#### 平衡树

#### 非平衡树

#### 排序树、查找树

#### 红黑树

集合加入红黑树的目的：增加查询效率

jdk8之前：哈希表 = 数组 + 链表

jdk8k8之后：哈希表 = 数组 + 链表 + 红黑树

### Set集合

Set接口，并没有对Collection接口进行扩展

方法实现都依靠map实现

Set和map是密切相关的

Map的遍历需要先变成单列集合，转换为Set集合

#### HashSet集合的介绍与使用

1. 概述：HashSet是Set接口的实现类，底层是哈希表结构，查询效率比数组高
2. 特点：
   1. 元素唯一
   2. 元素无序
   3. 无索引
   4. 线程不安全
3. 数据结构：哈希表结构
4. 方法：和Collection接口一样，但是HashSet集合没有removeAll()方法
5. 遍历：
   1. 使用增强for
   2. 使用迭代器

#### LinkedHashSet集合介绍与使用

1. 概述：LinkedHashSet集合是HashSet集合的子类，底层是哈希表结构，查询效率比数组高，并且元素是有序的
2. 特点：
   1. 元素唯一
   2. 元素有序
   3. 无索引
   4. 线程不安全
3. 数据结构是哈希表+双向链表
4. 使用：和HashSet集合一样

### 哈希值

1. 概述：哈希值是由计算机运算出来的十进制数，可以用来表示对象的地址，但是不能用来表示对象的内存地址
2. 获取哈希值：使用Object中的`hashCode()`方法

如果重写了HashCode方法，那么计算的就是对象内容的哈希值

1. 哈希值不一样，内容肯定不一样
2. 哈希值一样，内容不一定一样

### HashSet去重复过程说明

1. 先计算元素的哈希值（需要重写hashCode方法）
2. 再比较元素的内容（需要重写equals方法）
3. 先比较哈希值，如果哈希值一样，再比较内容
   1. 哈希值一样，内容不一样 - 仍然保存
   2. 哈希值一样，内容一样 - 去重复

## 模块二十 - 集合补充II

### Map集合

Map是双列集合的顶级接口

1. HashMap：
   1. key唯一，value可重复
   2. 无序
   3. 无索引
   4. 线程不安全
   5. 可以存null键和null值
   6. 数据结构：哈希表
   7. 子类：LinkedHashMap
      1. 是有序的
      2. 数据结构：哈希表+双向链表
2. HashTable：
   1. 线程安全
   2. 不可以存null键和null值
   3. 子类：Properties
      1. 主要和配置文件结合使用（IO流）
      2. key唯一，value可重复
      3. 无序
      4. 无索引
      5. 线程安全
      6. 不能null键和null值
      7. key和value都是字符串（String）类型
3. TreeMap：
   1. key唯一，value可重复
   2. 可以对key进行排序
   3. 无索引
   4. 线程不安全
   5. 不能存null键和null值
   6. 数据结构：红黑树

#### Map介绍

1. 概述：Map接口是双列集合的顶级接口，双列集合中存储的是键值对
2. 元素特点：
   1. 元素都是由键值对组成的

#### HashMap的介绍和使用

1. 概述：HashMap是Map接口的实现类，底层是哈希表结构，查询效率比数组高
2. 特点：
   1. key唯一，value可重复
3. 方法：
   1. V put(K key, V value) - 添加元素，返回被覆盖的value
   2. V remove(Object key) - 根据key删除元素，返回被删除的value
   3. V get(Object key) - 根据key查询value
   4. boolean containsKey(Object key) - 判断集合中是否存在指定的key
   5. `Collection<V> values()` - 获取集合中的所有value，转存到Collection集合中

#### LinkedHashMap介绍和使用

1. 概述：LinkedHashMap是HashMap的子类，底层是哈希表加上双向链表结构，查询效率比数组高，并且元素是有序的

遍历：

1. Map都需要转成Set集合，再按照key值使用get(key)方法进行遍历
2. 第二种遍历方式：
   1. 获取记录key和value的Entry对象
   2. 调用Entry对象的getKey()和getValue()方法

Map存储自定义对象时如何去重复：

重写equals方法，重写hashCode方法，确保key的唯一性

#### Map集合的练习

### 哈希表结构存储过程

1. 哈希表存储数据去重复的过程：
   1. 先比较元素的哈希值，再比较元素的内容
   2. 哈希值不一样，直接存储
   3. 哈希值一样，再比较内容
      1. 内容一样，丢弃
      2. 内容不一样，存储（使用链表或红黑树）

细节：

1. 哈希表中的数组，**默认长度为16**，但是是在第一次put的时候数组才会被初始化为16个字节
2. 哈希表中，有一个加载因子，默认为**0.75F** - 含义是，数组存储达到75%的时候，数组扩容
3. 扩容2倍
4. 如果链表长度**达到8**，数组容量**大于等于64**的时候，自动转化为红黑树
5. 如果删除元素，元素个数**小于等于6**，红黑树会转回为链表

#### 哈希表源码

#### 哈希表无索引与有序无序

哈希表中虽然有数组，但是set和map却没有索引？

这是因为哈希表在存储过程中，有可能形成链表，此时，一个索引就对应了多个元素，无法找出具体对应的元素

为什么LinkedHashMap是有序的？

LinkedHashMap底层是哈希表+双向链表，所以可以保证元素的顺序

### 红黑树相关集合

#### TreeSet

Set的实现类

1. 可以对元素进行排序
2. 无索引
3. 不能存null
4. 线程不安全
5. 元素唯一
6. 数据结构：红黑树

#### TreeMap

Map的实现类

1. 可以对Key进行排序
2. 无索引
3. key唯一
4. 线程不安全
5. 不能存null
6. 数据结构：红黑树

### Hashtable和Vector集合

#### Hashtable

Map的实现类

1. key唯一
2. value可重复
3. 无序
4. 无索引
5. 线程安全
6. 不能存null键和null值

#### Vector

1. 元素有序
2. 有索引
3. 元素可重复
4. 线程安全
5. 数据结构：数组

### Properties属性集

继承自Hashtable

1. key唯一
2. value可重复
3. 无序
4. 无索引
5. 线程安全，不能存null键和null值
6. 不需要指明泛型
7. 数据结构：哈希表结构

特有方法：

`object setProperty(String key,String value)` - 存键值对

`String getProperty(String key)` - 根据key获取value

`Set<String> stringPropertyNames()` -  获取所有的key，保存到Set集合中

`void load(InputStream inStream)` - 从流中读取键值对，存入Properties对象中

### 集合嵌套

和数组嵌套类似。
