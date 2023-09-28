以下是 `java.io.File` 类的常用方法和相关类的详细说明，以及一些代码演示示例：

#### 常用方法：

1. **构造方法：**
   - `File(String pathname)`：通过指定文件路径名来创建 `File` 对象。
   - `File(String parent, String child)`：通过指定父目录和子目录/文件名来创建 `File` 对象。
   - `File(File parent, String child)`：通过指定父目录和子目录/文件名来创建 `File` 对象。

   ```java
   // 构造方法示例
   File file1 = new File("C:\\example.txt"); // 使用绝对路径
   File file2 = new File("C:\\", "example.txt"); // 使用父目录和子目录/文件名
   File parentDir = new File("C:\\");
   File file3 = new File(parentDir, "example.txt");
   ```

2. **文件/目录信息获取：**
   - `String getName()`：获取文件或目录的名称。
   - `String getPath()`：获取文件或目录的路径。
   - `String getAbsolutePath()`：获取文件或目录的绝对路径。
   - `long length()`：获取文件的大小（字节数）。
   - `long lastModified()`：获取文件或目录的最后修改时间。
   - `boolean exists()`：判断文件或目录是否存在。
   - `boolean isFile()`：判断是否为文件。
   - `boolean isDirectory()`：判断是否为目录。
   - `boolean canRead()`：判断是否可读。
   - `boolean canWrite()`：判断是否可写。

   ```java
   // 获取文件信息示例
   File file = new File("C:\\example.txt");
   System.out.println("文件名: " + file.getName());
   System.out.println("文件路径: " + file.getPath());
   System.out.println("绝对路径: " + file.getAbsolutePath());
   System.out.println("文件大小: " + file.length() + " 字节");
   System.out.println("最后修改时间: " + new Date(file.lastModified()));
   System.out.println("是否存在: " + file.exists());
   System.out.println("是否为文件: " + file.isFile());
   System.out.println("是否为目录: " + file.isDirectory());
   System.out.println("是否可读: " + file.canRead());
   System.out.println("是否可写: " + file.canWrite());
   ```

3. **文件/目录操作：**
   - `boolean createNewFile()`：创建新文件（如果文件不存在的话）。
   - `boolean mkdir()`：创建单层目录。
   - `boolean mkdirs()`：创建多层目录。
   - `boolean delete()`：删除文件或目录。
   - `boolean renameTo(File dest)`：将文件或目录重命名为指定的目标文件或目录。

   ```java
   // 文件和目录操作示例
   File file = new File("C:\\example.txt");
   
   // 创建新文件
   if (file.createNewFile()) {
       System.out.println("文件创建成功");
   }
   
   File directory = new File("C:\\exampleDir");
   
   // 创建单层目录
   if (directory.mkdir()) {
       System.out.println("目录创建成功");
   }
   
   // 创建多层目录
   if (directory.mkdirs()) {
       System.out.println("多层目录创建成功");
   }
   
   // 删除文件或目录
   if (file.delete()) {
       System.out.println("文件删除成功");
   }
   
   // 重命名文件或目录
   File newFile = new File("C:\\new_example.txt");
   if (file.renameTo(newFile)) {
       System.out.println("文件重命名成功");
   }
   ```

4. **目录遍历：**
   - `String[] list()`：返回目录中所有文件和目录的名称数组。
   - `File[] listFiles()`：返回目录中所有文件和目录的 `File` 对象数组。
   - `File[] listFiles(FileFilter filter)`：返回目录中符合过滤条件的 `File` 对象数组。
   - `File[] listFiles(FilenameFilter filter)`：返回目录中符合文件名过滤条件的 `File` 对象数组。

   ```java
   // 目录遍历示例
   File directory = new File("C:\\exampleDir");
   
   // 获取目录中所有文件和目录的名称数组
   String[] names = directory.list();
   for (String name : names) {
       System.out.println(name);
   }
   
   // 获取目录中

所有文件和目录的File对象数组
   File[] files = directory.listFiles();
   for (File file : files) {
       System.out.println(file.getName());
   }
   ```

#### 相关类：

- `java.io.FileFilter`：用于过滤文件和目录的接口。
- `java.io.FilenameFilter`：用于过滤文件名的接口。

示例代码中演示了如何使用 `File` 类的方法来进行文件和目录的创建、删除、查询、重命名等操作。