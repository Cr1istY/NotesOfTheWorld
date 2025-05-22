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
