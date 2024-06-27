### `shutil` 模块详细说明及示例

`shutil` 模块是 Python 标准库的一部分，提供了一些高级的文件操作和目录操作功能，包括文件复制、移动、删除、归档和解压缩等。以下是该模块中的一些常用功能及其示例。

#### 1. 复制文件和目录

- `shutil.copy(src, dst)`：复制文件，保留权限，返回目标路径。
- `shutil.copy2(src, dst)`：复制文件，保留权限和元数据，返回目标路径。
- `shutil.copytree(src, dst)`：递归地复制整个目录树。

```python
import shutil

# 复制文件 example.txt 到 backup.txt
shutil.copy('example.txt', 'backup.txt')

# 复制文件 example.txt 到目录 backup 目录中
shutil.copy2('example.txt', 'backup/example.txt')

# 复制整个目录树
shutil.copytree('source_directory', 'destination_directory')
```

#### 2. 移动和重命名文件及目录

- `shutil.move(src, dst)`：移动文件或目录，可以重命名。

```python
import shutil

# 移动文件 example.txt 到目录 backup 中
shutil.move('example.txt', 'backup/example.txt')

# 重命名文件
shutil.move('backup/example.txt', 'backup/renamed_example.txt')
```

#### 3. 删除文件和目录

- `shutil.rmtree(path)`：递归地删除目录树。

```python
import shutil

# 删除整个目录树
shutil.rmtree('directory_to_delete')
```

#### 4. 创建和解压归档文件

- `shutil.make_archive(base_name, format, root_dir)`：创建归档文件。
- `shutil.unpack_archive(filename, extract_dir)`：解压归档文件。

```python
import shutil

# 创建 zip 归档文件
shutil.make_archive('backup', 'zip', 'directory_to_archive')

# 解压归档文件
shutil.unpack_archive('backup.zip', 'extracted_directory')
```

#### 5. 磁盘使用情况

- `shutil.disk_usage(path)`：获取磁盘的总大小、已用空间和可用空间。

```python
import shutil

# 获取磁盘使用情况
total, used, free = shutil.disk_usage('/')
print(f"Total: {total // (2**30)} GiB")
print(f"Used: {used // (2**30)} GiB")
print(f"Free: {free // (2**30)} GiB")
```

#### 示例代码详解

下面是一段综合使用 `shutil` 模块中多个功能的示例代码：

```python
import shutil
import os

# 创建示例目录和文件
os.makedirs('example_dir/subdir', exist_ok=True)
with open('example_dir/file1.txt', 'w') as f:
    f.write('Hello, World!')
with open('example_dir/subdir/file2.txt', 'w') as f:
    f.write('Python is awesome!')

# 复制文件
shutil.copy('example_dir/file1.txt', 'example_dir/copy_of_file1.txt')

# 复制整个目录
shutil.copytree('example_dir', 'example_dir_backup')

# 移动文件
shutil.move('example_dir/copy_of_file1.txt', 'example_dir/subdir/moved_file.txt')

# 删除目录
shutil.rmtree('example_dir_backup')

# 创建归档文件
shutil.make_archive('example_archive', 'zip', 'example_dir')

# 解压归档文件
shutil.unpack_archive('example_archive.zip', 'unpacked_example_dir')

# 获取磁盘使用情况
total, used, free = shutil.disk_usage('/')
print(f"Total: {total // (2**30)} GiB")
print(f"Used: {used // (2**30)} GiB")
print(f"Free: {free // (2**30)} GiB")

# 清理示例目录和文件
shutil.rmtree('example_dir')
shutil.rmtree('unpacked_example_dir')
os.remove('example_archive.zip')
```

### 结论

`shutil` 模块提供了一系列实用的文件和目录操作函数，极大地方便了文件的复制、移动、删除以及归档操作。这些函数在编写需要处理文件系统的脚本和程序时非常有用。