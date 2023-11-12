Java中的InputStream有很多子类，以下是一些常见的InputStream子类的详细介绍以及相应的代码演示：

1. **FileInputStream**（文件字节输入流）：
   - 用途：从文件中读取字节数据。
   - 代码演示：
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt")) {
         int data;
         while ((data = fis.read()) != -1) {
             System.out.print((char) data);
         }
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

2. **ByteArrayInputStream**（字节数组输入流）：
   - 用途：从字节数组中读取数据。
   - 代码演示：
     ```java
     byte[] byteArray = { 65, 66, 67, 68, 69 };
     try (ByteArrayInputStream bais = new ByteArrayInputStream(byteArray)) {
         int data;
         while ((data = bais.read()) != -1) {
             System.out.print((char) data);
         }
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

3. **FileReader**（文件字符输入流）：
   - 用途：从字符文件中读取字符数据。
   - 代码演示：
     ```java
     try (FileReader reader = new FileReader("example.txt")) {
         int data;
         while ((data = reader.read()) != -1) {
             System.out.print((char) data);
         }
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

4. **PipedInputStream**（管道输入流）：
   - 用途：用于从其他线程中读取数据。
   - 代码演示：
     ```java
     PipedInputStream in = new PipedInputStream();
     PipedOutputStream out = new PipedOutputStream();

     try {
         in.connect(out);

         Thread writerThread = new Thread(() -> {
             try {
                 out.write("Hello, PipedInputStream!".getBytes());
                 out.close();
             } catch (IOException e) {
                 e.printStackTrace();
             }
         });

         Thread readerThread = new Thread(() -> {
             try {
                 int data;
                 while ((data = in.read()) != -1) {
                     System.out.print((char) data);
                 }
                 in.close();
             } catch (IOException e) {
                 e.printStackTrace();
             }
         });

         writerThread.start();
         readerThread.start();
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

5. **BufferedInputStream**（缓冲输入流）：
   - 用途：提供缓冲功能，提高读取效率。
   - 代码演示：
     ```java
     try (FileInputStream fis = new FileInputStream("example.txt");
          BufferedInputStream bis = new BufferedInputStream(fis)) {
         int data;
         while ((data = bis.read()) != -1) {
             System.out.print((char) data);
         }
     } catch (IOException e) {
         e.printStackTrace();
     }
     ```

这些是Java中InputStream的一些常见子类，每个子类都有不同的用途和特点。根据具体的需求，选择合适的子类进行数据读取和处理。