以下是`FileInputStream`类的常用方法详细说明，并附带代码演示：

1. **构造方法**：

   - `FileInputStream(String name)`：使用指定的文件名创建一个新的`FileInputStream`对象。
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         // 用 fis 读取文件内容
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

   - `FileInputStream(File file)`：使用指定的文件对象创建一个新的`FileInputStream`对象。
     ```java
     File file = new File("example.txt");
     try (FileInputStream fis = new FileInputStream(file)) {
         // 用 fis 读取文件内容
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

2. **读取数据**：

   - `int read()`：从输入流中读取下一个字节的数据，返回读取的字节数据（0 到 255 的整数值）。如果到达文件末尾，返回 -1。
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         int data;
         while ((data = fis.read()) !  = -1) {
             // 处理读取的数据
         }
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

   - `int read(byte[] b)`：从输入流中最多读取`b.length`个字节的数据，并将其存储在字节数组`b`中。返回实际读取的字节数，如果到达文件末尾，返回 -1。
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         byte[] buffer = new byte[1024];
         int bytesRead;
         while ((bytesRead = fis.read(buffer)) != -1) {
             // 处理读取的数据，存储在 buffer 中的前 bytesRead 字 节
             `System.out.print(new String(buf, 0, len))` 
             /*这句代码是 Java 中用于输出字符串的语句。让我详细解释一下：

1. `System.out`：这是 Java 中的标准输出流对象，通常用于向控制台输出信息。`System.out` 是 `java.io.PrintStream` 类的一个实例，可以通过它来执行输出操作。

2. `print` 方法：`System.out` 对象上的 `print` 方法用于打印文本而不换行。它接受不同类型的参数并将它们输出到控制台。

3. `new String(buf, 0, len)`：这是一个字符串构造方法的调用，用于将字节数组 `buf` 中的一部分数据转换为字符串。它的参数含义如下：
   - `buf`：要转换为字符串的字节数组。
   - `0`：起始索引，表示从字节数组的第一个字节开始转换。
   - `len`：要转换的字节数，表示要转换的数据长度。

4. 综合起来，`System.out.print(new String(buf, 0, len))` 的作用是将字节数组 `buf` 中从索引 `0` 开始的 `len` 个字节转换为字符串，并将该字符串输出到控制台，而不换行。这通常用于将字节数据以文本形式打印出来。

举个例子，假设 `buf` 是一个字节数组，其中包含了一些文本数据，然后通过上述代码将这些字节转换为字符串并输出到控制台。这对于读取文件或网络数据并以文本形式显示数据非常有用。**/
         }
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

   - `int read(byte[] b, int off, int len)`：从输入流中读取最多`len`个字节的数据，存储在字节数组`b`中，从偏移量`off`开始存储。返回实际读取的字节数，如果到达文件末尾，返回 -1。
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         byte[] buffer = new byte[1024];
         int bytesRead;
         int offset = 0;
         int length = 512;
         while ((bytesRead = fis.read(buffer, offset, length)) != -1) {
             // 处理读取的数据，存储在 buffer 中的前 bytesRead 字节，从 offset 开始
         }
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

3. **关闭流**：

   - `void close()`：关闭输入流，释放与之关联的系统资源。在完成文件读取后应该始终调用该方法。
     ```java
     FileInputStream fis = null;
     try {
         fis = new FileInputStream("example.txt");
         // 用 fis 读取文件内容
     } catch (IOException e) {
         e.printStackTrace();
     } finally {
         if (fis != null) {
             try {
                 fis.close();
             } catch (IOException e) {
                 e.printStackTrace();
             }
         }
     }
     ```

4. **其他方法**：

   - `int available()`：返回可以从输入流中读取而不阻塞的字节数。此方法通常用于检查输入流中是否还有可用数据。
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         int availableBytes = fis.available();
         // 处理可用数据
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

   - `long skip(long n)`：跳过并丢弃输入流中的`n`个字节。通常用于跳过不需要的数据。
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         long bytesSkipped = fis.skip(1024);
         // 跳过了 bytesSkipped 个字节的数据
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

   - `int readNBytes(byte[] b, int off, int len)`：从输入流中读取`len`个字节的数据，存储在字节数组`b`中，从偏移量`off`开始存储。返回实际读取的字节数，如果到达文件末尾，返回 -1。
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         byte[] buffer = new byte[1024];
         int bytesRead = fis.readNBytes(buffer, 0, 1024);
         // 从文件中读取了 bytesRead 字节的数据
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```