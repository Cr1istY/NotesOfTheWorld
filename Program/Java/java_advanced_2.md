# java 进阶2

## 模块二十一 - IO流

### File类

#### File介绍

1. 以 .jpg 结尾的一定是图片吗？不一定，也有可能是文件夹。
2. 什么是文本文档？人能看懂的文件就是文本文档。
3. 父路径与父级文件夹
4. 分隔符：
   1. 路径名称分隔符：windows: \ , linux: /
   2. 路径分隔符：一个路径和其他路径之间的分隔符 `;`

##### File类概述

An abstract representation of file and directory pathnames.

简单理解：在创建file对象时，需要传递一个路径，这个路径定位到哪个目录，我们就代表哪个对象。

`File file = new File("D:\\a.txt");`

##### File的使用

- `static String separator` - 与系统有关的默认名称分隔符
- `static String pathSeparator` - 与系统有关的路径分隔符

如何用java正确编写一个路径？

`String path = "D:" + File.separator + "a.txt";`

输出：`D:\a.txt`

##### File的构造方法

>- public File(String pathname)：通过将给定的路径名 字符串转换为抽象类路径 来创建新的实例
>- public File(String parent,String child)：从父路径字符串 和 子路径字符串创建新的File实例
>- public File(File parent,String child)：从父抽象路径名 和 子路径名字符串创建新的File实例

##### File的方法

| 序号 | 方法描述 |
|------|----------|
| 1 | `public String getName()`<br>返回由此抽象路径名表示的文件或目录的名称。 |
| 2 | `public String getParent()`<br>返回此抽象路径名的父路径名的路径名字符串，如果此路径名没有指定父目录，则返回 null。 |
| 3 | `public File getParentFile()`<br>返回此抽象路径名的父路径名的抽象路径名，如果此路径名没有指定父目录，则返回 null。 |
| 4 | `public String getPath()`<br>将此抽象路径名转换为一个路径名字符串。 |
| 5 | `public boolean isAbsolute()`<br>测试此抽象路径名是否为绝对路径名。 |
| 6 | `public String getAbsolutePath()`<br>返回抽象路径名的绝对路径名字符串。 |
| 7 | `public boolean canRead()`<br>测试应用程序是否可以读取此抽象路径名表示的文件。 |
| 8 | `public boolean canWrite()`<br>测试应用程序是否可以修改此抽象路径名表示的文件。 |
| 9 | `public boolean exists()`<br>测试此抽象路径名表示的文件或目录是否存在。 |
| 10 | `public boolean isDirectory()`<br>测试此抽象路径名表示的文件是否是一个目录。 |
| 11 | `public boolean isFile()`<br>测试此抽象路径名表示的文件是否是一个标准文件。 |
| 12 | `public long lastModified()`<br>返回此抽象路径名表示的文件最后一次被修改的时间。 |
| 13 | `public long length()`<br>返回由此抽象路径名表示的文件的长度。 |
| 14 | `public boolean createNewFile() throws IOException`<br>当且仅当不存在具有此抽象路径名指定的名称的文件时，原子地创建由此抽象路径名指定的一个新的空文件。 |
| 15 | `public boolean delete()`<br>删除此抽象路径名表示的文件或目录。 |
| 16 | `public void deleteOnExit()`<br>在虚拟机终止时，请求删除此抽象路径名表示的文件或目录。 |
| 17 | `public String[] list()`<br>返回由此抽象路径名所表示的目录中的文件和目录的名称所组成字符串数组。 |
| 18 | `public String[] list(FilenameFilter filter)`<br>返回由包含在目录中的文件和目录的名称所组成的字符串数组，这一目录是通过满足指定过滤器的抽象路径名来表示的。 |
| 19 | `public File[] listFiles()`<br>返回一个抽象路径名数组，这些路径名表示此抽象路径名所表示目录中的文件。 |
| 20 | `public File[] listFiles(FileFilter filter)`<br>返回表示此抽象路径名所表示目录中的文件和目录的抽象路径名数组，这些路径名满足特定过滤器。 |
| 21 | `public boolean mkdir()`<br>创建此抽象路径名指定的目录。 |
| 22 | `public boolean mkdirs()`<br>创建此抽象路径名指定的目录，包括创建必需但不存在的父目录。 |
| 23 | `public boolean renameTo(File dest)`<br>重新命名此抽象路径名表示的文件。 |
| 24 | `public boolean setLastModified(long time)`<br>设置由此抽象路径名所指定的文件或目录的最后一次修改时间。 |
| 25 | `public boolean setReadOnly()`<br>标记此抽象路径名指定的文件或目录，以便只可对其进行读操作。 |
| 26 | `public static File createTempFile(String prefix, String suffix, File directory) throws IOException`<br>在指定目录中创建一个新的空文件，使用给定的前缀和后缀字符串生成其名称。 |
| 27 | `public static File createTempFile(String prefix, String suffix) throws IOException`<br>在默认临时文件目录中创建一个空文件，使用给定前缀和后缀生成其名称。 |
| 28 | `public int compareTo(File pathname)`<br>按字母顺序比较两个抽象路径名。 |
| 29 | `public int compareTo(Object o)`<br>按字母顺序比较抽象路径名与给定对象。 |
| 30 | `public boolean equals(Object obj)`<br>测试此抽象路径名与给定对象是否相等。 |
| 31 | `public String toString()`<br>返回此抽象路径名的路径名字符串。 |

注意：

1. delete不走回收站，慎用
2. delete无法删除非空文件夹
3. listFiles方法底层还是list方法

#### 相对路径与绝对路径

1. 绝对路径：从盘符开始，如D:\a.txt
2. 相对路径：从当前目录（参照路径）开始，如a.txt

想象你在国外，写信，则需要学全国家 - 绝对路径

如果你在国外，只需要写城市即可 - 相对路径

针对idea中写相对路径：

哪个路径是参照路径，哪个路径就可以省略不写，剩下的就是idea中的相对路径写法

在idea中，参照路径其实就是当前project的绝对路径

总结：在idea中的相对路径，实际上就是从模块名开始写

### 字节流

#### IO流介绍以及输入输出以及流向的介绍

IO流：将一个设备上的数据传输到另一个设备上，称之为IO流技术

I：input

O：output

为什么要学IO流技术呢？

可以长期保存数据，方便下次使用

#### IO流的流向 - 针对SE阶段

以内存为参照物：

输出：将内存中的数据，写入到磁盘中

输入：将磁盘的数据，写入到内存中

不同设备的IO流：

发消息的就是输出方

收消息的就是输入方

#### IO流分类

字节流：

- 万能流 一切皆字节
- 字节输出流 - OutputStream
- 字节输入流 - InputStream

字符流：操作文本文档

- 字符输出流 - Writer
- 字符输入流 - Reader

上述四个类都是抽象类

##### 字节输出流 OutputStream

指定的文件没有，会自动创建

每次执行，默认都会创造一个新文件，覆盖旧文件

OutputStream 是 Java I/O 系统中用于输出字节数据的基础抽象类。

OutputStream 在 Java 中非常重要，因为：

1. 它是所有字节输出流的基类
2. 提供了处理二进制数据的基本方法
3. 支持多种输出目标(文件、内存、网络等)
4. 是 Java I/O 系统的核心组成部分

OutputStream 有许多重要的子类，包括：

- FileOutputStream: 用于写入文件
- ByteArrayOutputStream: 写入内存中的字节数组
- FilterOutputStream: 提供额外功能的输出流基类
- BufferedOutputStream: 提供缓冲功能的输出流
- DataOutputStream: 允许写入基本Java数据类型
- ObjectOutputStream: 用于对象序列化

OutputStream 类定义了以下关键方法：

1. write(int b)
`public abstract void write(int b) throws IOException` - 写入单个字节。参数 b 的低8位被写入，高24位被忽略。

1. write(byte[] b)
实例
`public void write(byte[] b) throws IOException` - 将字节数组 b 中的所有字节写入输出流。

1. write(byte[] b, int off, int len)
`public void write(byte[] b, int off, int len) throws IOException` - 从字节数组 b 的偏移量 off 开始，写入 len 个字节。

1. flush()
`public void flush() throws IOException` - 刷新输出流，强制写出所有缓冲的输出字节。

1. close()
`public void close() throws IOException` - 关闭输出流并释放相关系统资源。

###### 最佳实践

- 使用 try-with-resources
Java 7 引入的 try-with-resources 语句可以自动关闭资源，确保不会忘记关闭流：

    ```java
    try (OutputStream os = new FileOutputStream("file.txt")) {
        // 使用输出流
    } catch (IOException e) {
        e.printStackTrace();
    }
    ```

- 正确处理异常
IO 操作可能会抛出 IOException，应该妥善处理这些异常：

    ```java
    try {
        OutputStream os = new FileOutputStream("file.txt");
        // 使用输出流
        os.close();
    } catch (IOException e) {
        System.err.println("发生IO异常: " + e.getMessage());
        e.printStackTrace();
    }
    ```

- 使用缓冲提高性能
对于大量数据写入，使用 BufferedOutputStream 可以显著提高性能：

    ```java
    OutputStream os = new BufferedOutputStream(new FileOutputStream("large_file.dat"));
    ```

- 及时刷新和关闭
确保在完成写入后调用 flush() 和 close() 方法，特别是在写入重要数据时。

##### 字节输入流 InputStream

InputStream 是 Java I/O 系统中用于读取字节数据的抽象基类，位于 java.io 包中。

InputStream 是所有字节输入流的父类，为读取字节数据提供了基本框架。

InputStream 是一个抽象类，这意味着你不能直接实例化它，但可以通过它的子类（如 FileInputStream、ByteArrayInputStream 等）来创建具体的输入流对象。

<table class="reference"><thead><tr><th data-spm-anchor-id="5176.28197581.d_app-center.i6.13015a9e24FQsC">方法名</th><th>功能说明</th></tr></thead><tbody><tr><td><code node="[object Object]">int read()</code></td><td>读取一个字节，返回值是 0~255 的 int 值，如果到达流末尾则返回 <code node="[object Object]">-1</code></td></tr><tr><td><code node="[object Object]">int read(byte[] b)</code></td><td>从流中读取最多 <code node="[object Object]">b.length</code> 个字节的数据，并存入字节数组 <code node="[object Object]">b</code></td></tr><tr><td><code node="[object Object]">int read(byte[] b, int off, int len)</code></td><td>从 <code node="[object Object]">off</code> 偏移位置开始读取最多 <code node="[object Object]">len</code> 字节到数组 <code node="[object Object]">b</code></td></tr><tr><td><code node="[object Object]">void close()</code></td><td>关闭流并释放与之相关的资源</td></tr></tbody></table>

常用子类：

- FileInputStream: 用于从文件中读取数据。
- ByteArrayInputStream: 允许内存中的字节数组作为输入流。
- FilterInputStream: 为其他输入流提供额外功能的装饰器类。
- ObjectInputStream: 用于反序列化之前使用
- ObjectOutputStream 序列化的对象。
- PipedInputStream: 与 PipedOutputStream 配合使用，实现线程间的管道通信。

##### 练习：复制文件

### 字符流

字节流是万能流，但这是针对文件复制来说的

所以，使用字节流操作文件时尽量不要边读边看

如果要实现查看操作，则需要使用字符流

>按照字符操作，则需要对文件的编码保持一致

**复制操作不要使用字符流**！

#### 字符输入流 FileReader

字符输入流：父类，Reader - 是一个抽象类

FileReader：将文本文档中的内容读取到内存中

FileReader类从InputStreamReader类继承而来。该类按字符读取流中数据。可以通过以下几种构造方法创建需要的对象。

- FileReader(File file) - 在给定从中读取数据的 File 的情况下创建一个新 FileReader。
- FileReader(FileDescriptor fd) - 在给定从中读取数据的 FileDescriptor 的情况下创建一个新 FileReader。
- FileReader(String fileName) - 在给定从中读取数据的文件名的情况下创建一个新 FileReader。

<table class="reference">
	<tbody>
		<tr>
			<th>
				序号</th>
			<th>
				文件描述</th>
		</tr>
		<tr>
			<td>
				1</td>
			<td>
				<strong>public int read() throws IOException</strong><br>
				读取单个字符，返回一个int型变量代表读取到的字符</td>
		</tr>
		<tr>
			<td>
				2</td>
			<td>
				<strong>public int read(char [] c, int offset, int len)</strong><br>
				读取字符到c数组，返回读取到字符的个数</td>
		</tr>
	</tbody>
</table>

```java
import java.io.*;
 
public class FileRead {
    public static void main(String args[]) throws IOException {
        File file = new File("Hello1.txt");
        // 创建文件
        file.createNewFile();
        // creates a FileWriter Object
        FileWriter writer = new FileWriter(file);
        // 向文件写入内容
        writer.write("This\n is\n an\n example\n");
        writer.flush();
        writer.close();
        // 创建 FileReader 对象
        FileReader fr = new FileReader(file);
        char[] a = new char[50];
        fr.read(a); // 读取数组中的内容
        for (char c : a)
            System.out.print(c); // 一个一个打印字符
        fr.close();
    }
}
```

#### 字符输出流 FileWriter

字符输出流：父类，Writer - 抽象类

FileWriter：将内存中的数据写入到文本文档中

`FileWriter` 主要用于将字符数据写入到文件中。如果文件不存在，它会自动创建；如果文件已存在，默认情况下会覆盖文件的内容。与字节流相比，`FileWriter` 更加适合处理文本文件，使用起来也更加高效。

基本构造函数：

```java
FileWriter writer = new FileWriter("filename.txt");
```

- filename.txt：目标文件路径。如果文件不存在，FileWriter 会自动创建。

使用追加模式：

```java
FileWriter writer = new FileWriter("filename.txt", true);
```

- 其中` true `表示以追加模式打开文件，数据会被追加到文件末尾，不会覆盖现有内容。

```java
import java.io.FileWriter;
import java.io.IOException;

public class FileWriterExample {
    public static void main(String[] args) {
        try (FileWriter writer = new FileWriter("E:/software/test/text.txt")) {
            writer.write("Hello, FileWriter!\n");
            writer.write("This is a new line.\n");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

- write() 方法：用于将字符串写入文件。可以写入任意的字符数据。
- try-with-resources：自动管理资源，确保文件写入完成后流能够自动关闭，无需手动调用 close()。
- 如果不指定具体的路径，生成文件与src在同级目录

### IO流异常处理

try-catch-finally

```java
FileWriter fw = null;
try{
    fw = new FileWriter("d:/a.txt");
    fw.write("hello world");

}catch (IOException e) {
    e.printStackTrace();
}finally{
    try{
        if (fw != null) {
            try{
                fw.close();
            }catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
 } 
```

jdk7：

```java
try(IO对象){
    可能出现异常的代码;
}catch(异常类型 对象名){
    处理异常
}
```

以上处理异常方式会自动关闭IO流

## 模块二十二 - IO流补充

### 缓冲流

上述的四个IO流类，都是使用基本类，方法都是有native修饰的本地方法

本地方法是和系统与硬盘打交道的，即读和写都是在硬盘之间进行的，效率不高。

而使用缓冲流，则先将数据读入缓冲区，再从缓冲区中读取数据，从而提高效率。

>本地方法：使用native修饰，由c语言编写，不开源，和硬件打交道

#### 字节缓冲流

使用之前，需要将基本流包装成缓冲流。

1. BufferedOutputStream：将输出流包装成带缓冲区的输出流。
2. BufferedInputStream：将输入流包装成带缓冲区的输入流。

使用和创建基本流一样，使用带缓冲区的输出流

细节：

1. 使用缓冲流，为什么不需要关闭基本流 - 缓冲流内部会自动关闭基本流。
2. 缓冲流读写过程：将缓冲区中的数据写入到基本流中，基本流中写入数据，缓冲区中清空。

#### 字符缓冲流

字符流的基本流，底层是有缓冲区的，效率不是特别明显。

1. BufferedReader
2. BufferedWriter

特有方法：

- newLine() - 换行
- readLine() - 一次只读取一行，遇到行结束字符返回null

### 字符编码

编码：将自然字符串编码为字节序列的过程。

解码：将字节序列解码为自然字符串的过程。

如果存和取使用的是一样的规则，数据就不会出错。

最常见：utf-8

#### 转换流 InputSteamReader

字节流在操作的过程中，尽量不要边读边看，可能会出现乱码。

字符流在读取的过程中，编码一致，不会出现乱码问题

转换流，帮助我们指定读取的编码 - 字节流与字符流之间的桥梁

#### 转换流 OutputSteamWriter

### 序列化流

#### 序列化流与反序列化流

1. 作用：读写对象
2. 两个对象：
   1. ObjectOutputStream - 序列化流，写对象
   2. ObjectInputStream - 反序列化流，读对象

注意：

我们将对象序列化到文件中，此时文件中的内容是看不懂的，我们只需要使用java读回来即可。

##### ObjectOutputStream

作用：将java对象序列化到文件中

writeObject(Object obj) - 将对象写入文件

注意：

想要将对象序列化到文件中，不能随便序列化。 - 必须实现Serializable接口

##### ObjectInputStream

作用：将文件中的序列化对象读出

readObject() - 读取对象

注意：

读取对象时，必须保证对象是可序列化的。

##### 不想被序列化

transit - 将字段标记为瞬时字段，不能被序列化。

##### 序列号冲突问题

序列化之后，修改源码，修改完之后没有重新进行序列化，直接反序列化了，就会出现序列号冲突问题。

对于一个实现序列化接口的类，编译之后，在文件中会自动生成一个序列号。

反序列化时，会将序列号与反序列化对象中的序列号进行比较，如果相同，则认为两个对象是同一个对象，否则会抛出异常。

解决方法：

使用`public static final long serialVersionUID = 42L;`

直接给类设置一个静态的序列号，解决序列号冲突问题。

循环读取的次数和存储对象的个数不一致，就会出现异常。

### IO流 打印流

System.out.println() - 输出到控制台

System.out 实际上是一个静态对象，是PrintStream类型。

#### 改变流向

1. 什么叫改变流向：可以让输出语句从控制台上输出改变到在文件中进行输出。
2. System中的`static PrintStream setOut(PrintStream out)`让语句从控制台输出转移到文件输出。

使用场景：可以将输出的内容以及详细信息保存到日志文件中，永久保存。

### Properties集合

Properties是唯一一种能和文件流兼容的集合。

1. 无序、无索引
2. key唯一，value可重复
3. 线程安全
4. key和value都是字符串类型

特有方法：

- setProperty(String key, String value) - 存键值对
- getProperty(String key) - 取值
- stringPropertyNames() - 获取所有的key，存放到set集合中
- load(InputStream inStream) - 将流中的数据加载到Properties集合中

使用场景：配合配置文件使用

注意：

- 将来不能将很多的硬数据放到源码中

创建配置文件：

1. 在模块下右键 - file - 取名为 xxx.properties
2. 在 xxx.properties 文件中写配置数据
   1. key和value使用=分隔（key=value）
   2. key和value不用加双引号
   3. 每个键值对写完之后，需要换行再写下一对
   4. 键值对之间最好不要有空格
   5. 键值对不建议写中文

### Commons-io 工具包

IO技术开发中，代码量很大，而且代码的重复率较高，如果我们要遍历目录，拷贝目录就需要使用方法的递归调用，也增大了程序的复杂度。

使用'commons-io’工具包，可以解决这个问题。

#### 添加第三方jar包

jar包：本身是一个压缩包，里面存放着开发好的类文件。

需要将jar包解压到我们的项目下。

1. 创建一个libs文件夹，将jar包放入libs文件夹中
2. 将准备好的jar包放到此文件夹下
3. 对着jar包 - 右键 - add as library（如果我们想将libs下的所有jar包全部解压，直接邮件lib）
4. level可以选择moudle

### 快速记忆IO流对象

## 模块二十三 - 网络编程、正则表达式、设计模式

概述：在网络通信协议下，不同计算机上运行的程序，进行数据传输

### 软件结构

- C/S架构：客户端/服务端，常见：QQ
- B/S架构：浏览器/服务器，常见：百度

两种架构各有优缺，但是都离不开网络编程的支持。

### 服务器

服务器：安装了服务器软件的计算机，用于处理网络请求，返回响应。

常见的服务器软件：tomcat

两台计算机之间要想进行通讯，必须使用相应的规则

### 通信三要素

Ip地址、协议、端口号

> 详见计算机网络

### UDP协议编程

1. DatagramSocket对象，指定端口，创建发送端
2. DatagramPacket对象，封装数据，指定端口和ip地址

#### 发送端

1. 创建DatagramSocket对象（快递公司）
   1. 空参：端口号从可用的端口号中随机一个使用
   2. 有参：自己制定端口
2. 创建DatagramPacket对象（快递单），打包数据
   1. 要发送的数据 - 字节数组
   2. 指定接收端的ip
   3. 指定接收端的端口号
3. 发送数据
4. 释放资源

#### 服务端

1. 创建DatagramSocket对象，指定服务端的端口号
2. 接收数据包
3. 解析数据包
4. 释放资源

### TCP协议编程

面向连接，必须要先打开服务端

#### TCP客户端

Socket对象，指定ip和端口，创建客户端

1. 创建Socket对象，指定服务端ip和端口
2. 调用Socket对象中的getOutputStream()方法，获取网络输出流，发送请求
3. 调用Socket中的getInputStream()方法，获取网络输入流，读取响应数据
4. 关流

#### TCP服务端

1. 创建ServerSocket对象，指定端口
2. 调用ServerSocket对象的accept()方法，等待客户端连接，该方法返回的是连接服务端的socket对象
3. 调用Socket对象中的getInputStream()方法，获取网络输入流，读取数据
4. 调用Socket对象中的getOutputStream()方法，用于给客户端写响应
5. 关流

#### 文件上传练习

```java
package cn.foreveryang.tcp;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;

public class Client {
    public static void main(String[] args) throws Exception {
        // 1. 创建Socket对象
        Socket socket = new Socket("127.0.0.1", 6666);
        // 2. 创建FileInputStream用于读取本地文件
        FileInputStream fis = new FileInputStream("E:\\ceshi\\ceshi.png");
        // 3. 调用getOutputStream，用于将读取过来的图片写给服务端
        OutputStream os = socket.getOutputStream();
        // 4. 边读边写
        byte[] buf = new byte[1024];
        int len;
        while ((len = fis.read(buf)) != -1) {
            os.write(buf, 0, len);
        }

        System.out.println("==========");
        socket.shutdownOutput();
        // 5. 调用getInputStream，读取响应结果
        InputStream is = socket.getInputStream();
        byte[] buf1 = new byte[1024];
        int len1 = is.read(buf1);
        System.out.println(new String(buf1, 0, len1));
        is.close();
        os.close();
        socket.close();
        fis.close();
    }
}
```

```java
package cn.foreveryang.tcp;

import java.io.FileOutputStream;
import java.io.OutputStream;
import java.net.ServerSocket;
import java.net.Socket;
import java.io.InputStream;


public class Server {
    public static void main(String[] args) throws Exception {
        // 1. 创建ServerSocket对象
        ServerSocket ss = new ServerSocket(6666);
        // 2. 调用accept方法，等待客户端连接
        Socket s = ss.accept();
        // 3. 调用socket中的getInputSteam，读取客户端的发送过来的图片
        InputStream is = s.getInputStream();
        // 4. 创建FileOutputSteam，将读取过来的图片写在硬盘上
        FileOutputStream fos = new FileOutputStream("E:\\test1.png");
        // 5. 边读边写
        byte[] buffer = new byte[1024];
        int len;
        while ((len = is.read(buffer)) != -1) {
            fos.write(buffer, 0, len);
        }

        System.out.println("=====");

        // 6. 调用socket中的getOutputSteam，给客户端响应结果

        OutputStream os = s.getOutputStream();
        os.write("上传成功".getBytes());

        // 7，关流

        os.close();
        fos.close();
        is.close();
        s.close();
        ss.close();


    }
}
```

### 正则表达式

正则表达式是一个具有特殊规则的字符串，用于匹配字符串。

使用：用于检验手机号、邮箱、身份证号、邮政编码、IP地址、URL地址、日期、时间、金额等。

#### 正则表达式具体使用

##### 正则表达式字符类

### 设计模式

设计模式，是一套被反复使用，经过分类编目的代码设计经验的总结。

使用正则表达式，是为了可重用代码，保证代码的可靠性、程序的重用性、稳定性。

#### 模板方法设计模式

模板方法设计模式：定义一个操作中的算法的骨架，而将一些步骤延迟到子类中。明确了一部分功能，而另一部分功能不明确，需要延迟到子类中实现。

例如：饭店吃饭，需要经过点菜、吃菜、买单三个步骤，其中，点菜和买单是固定步骤，吃菜是变化的步骤，所以，点菜和买单是模板方法，而吃菜是变化的步骤，所以，吃菜是子类实现。

#### 单例模式

1. 目的：单-一个，例-实例
2. 让一个类只产生一个对象，给外界使用。

分类：

1. 饿汉式：我好饥饿呀，迫不及待要这个对象，感觉new出来
2. 懒汉式：我懒，等我需要时才去创建对象

##### 饿汉式

```java
public class GiantDragon {

    //私有化构造方法使得该类无法在外部通过new 进行实例化
    private GiantDragon(){
        System.out.println("私有化构造方法");
    }

    //准备一个类属性，指向一个实例化对象。 因为是类属性，所以只有一个

    private static GiantDragon instance = new GiantDragon();

    //public static 方法，提供给调用者获取12行定义的对象
    public static GiantDragon getInstance(){
        return instance;
    }
}
```

##### 懒汉式

```java
public class GiantDragon2 {

    //GiantDragon2 进行实例化
    private GiantDragon2(){
        System.out.println("私有化构造方法");
    }

    //准备一个类属性，用于指向一个实例化对象，但是暂时指向null
    private static GiantDragon2 instance;

    //public static 方法，返回实例对象 （非线程安全的，不推荐使用该写法）
    public static GiantDragon2 getInstance(){
        //第一次访问的时候，发现instance没有指向任何对象，这时实例化一个对象
        if(null==instance){
            instance = new GiantDragon2();
        }
        //返回 instance指向的对象
        return instance;
    }
    // 线程安全的，并且通过非空判断提升性能（因为如果只上锁，那么每次调用的时候都会上锁，事实上只有第一次创建对象的时候才需要加锁）
    public static GiantDragon2 getInstance(){
        if(instance == null){
            synchronized(instance){
                //第一次访问的时候，发现instance没有指向任何对象，这时实例化一个对象
                if(null==instance){
                    instance = new GiantDragon2();
                }
            }
        }
        //返回 instance指向的对象
        return instance;
    }
    //以上线程安全的写法在java单例设计模式中并非完美的写法，因为在JVM执行过程中可能会存在问题，感兴趣的小伙伴可以去找一下相关的资料。

}
```

### Lombok的使用

简化javabean开发

之前：

1. 提供属性
2. 提供构造方法

如果使用lombok：只需要提供属性

## 模块二十四 - JDK新特性

### Lambda表达式

1. 面向对象思想：是java的核心编程思想
2. 强调的是找对象，帮我们去做事情

而jdk8开始，引入了函数式编程思想

强调的是结果，不强调过程

Lambda表达式：

```java
() -> {}
```

() : 重写方法的参数列表

-> ：将参数传递给重写的方法体

{} : 重写的方法体

必须是函数式接口（有且只有一个抽象方法的接口，用@FunctionalInterface注解去检测）做方法传递

#### 怎么写Lambda表达式

1. 先观察后改造
   1. 先观察是否是函数式接口做方法参数传递
   2. 如果是，则使用Lambda表达式
   3. 调用方法，以匿名内部类的形式传递实参
   4. 从new接口开始到重写方法的方法名结束，选择，删除
   5. 在重写方法的参数后面，方法体的前面加上`() -> {}`
2. 省略规则：
   1. 重写方法的参数类型可以删掉
   2. 如果重写方法只有一个参数，则参数括号可以省略
   3. 如果方法体只有一句话，那么所在的大括号以及分号可以干掉
   4. 如果方法体只有一句话，且方法体只有一句话，那么大括号可以省略

### 函数式接口

有且仅有一个抽象方法的接口叫做函数式接口

使用@FunctionalInterface注解去检测

#### jdk自带函数式接口

单独使用很不好用，实际上是用于Stream流操作

##### 1. Suppier

##### 2. Consumer

##### 3. Function

##### 4. Predicate

### Stream流

Stream流中的流，是指流式编程，可以被看成是流水线。

#### Stream流的获取

1. 集合：`Stream<T> stream()`
2. 数组：`static <T> Stream<T> of (T... values)`

#### Stream流中的常用方法

1. forEach - 是一个终结方法
2. count - 一个终结方法，统计元素个数

### 方法引用

使用场景：

1. 被引用的方法要写在重写方法中。
2. 被引用的方法从参数上，返回值上要和所在重写方法一致。
3. 而且引用方法最好是操作重写方法的参数值的。

怎么使用：

`::`

### jdk8之后的新特性

主要是对性能的优化。

## 模块二十五 - 单元测试_反射_注解

### Junit单元测试

Junit是一个开源的测试框架，用于测试java应用程序。

可以代替main方法去执行其他的方法。

可以单独执行一个方法，然后测试方法能否跑通。

注意：junit需要导包

#### Junit的基本使用

### 类的加载时机

1. new对象
2. new子类对象
3. 执行main方法
4. 调用静态成员
5. 反射，创建class类对象
