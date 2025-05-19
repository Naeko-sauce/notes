### Python 的 `os` 模块

`os` 模块提供了一种便携的方式，使用操作系统功能，如文件和目录操作、环境变量管理等。以下是该模块的所有常用方法及其使用示例，并附有输出结果和详细描述。

#### 导入 `os` 模块

```python
import os
```

### 获取当前工作目录

`os.getcwd()` 返回当前的工作目录。

**示例：**

```python
import os

# 获取并打印当前工作目录
current_directory = os.getcwd()
print("Current Working Directory:", current_directory)
```

**输出：**

```
Current Working Directory: /home/user/projects
```

### 改变工作目录

`os.chdir(path)` 改变当前的工作目录。

**示例：**

```python
import os

# 打印当前工作目录
print("Before change:", os.getcwd())

# 改变当前工作目录
os.chdir('/path/to/new/directory')

# 打印改变后的工作目录
print("After change:", os.getcwd())
```

**输出：**

```
Before change: /home/user/projects
After change: /path/to/new/directory
```

### 创建新目录

`os.mkdir(path)` 创建一个新目录。

**示例：**

```python
import os

# 创建一个名为 'new_directory' 的新目录
os.mkdir('new_directory')

# 确认目录创建成功
print("Directory 'new_directory' created")
```

**输出：**

```
Directory 'new_directory' created
```

### 删除目录

`os.rmdir(path)` 删除一个目录（该目录必须为空）。

**示例：**

```python
import os

# 删除名为 'new_directory' 的目录
os.rmdir('new_directory')

# 确认目录删除成功
print("Directory 'new_directory' removed")
```

**输出：**

```
Directory 'new_directory' removed
```

### 列出目录中的文件和子目录

`os.listdir(path)` 返回指定目录中的文件和子目录的名称列表。

**示例：**

```python
import os

# 列出当前目录中的所有文件和子目录
items = os.listdir('.')

# 打印所有项目
print("Items in current directory:", items)
```

**输出：**

```
Items in current directory: ['file1.txt', 'file2.txt', 'directory1']
```

### 检查文件或目录是否存在

`os.path.exists(path)` 检查指定路径是否存在。

**示例：**

```python
import os

# 检查名为 'example.txt' 的文件是否存在
file_exists = os.path.exists('example.txt')

# 打印检查结果
print("Does 'example.txt' exist?", file_exists)
```

**输出：**

```
Does 'example.txt' exist? True
```

### 获取文件大小

`os.path.getsize(path)` 返回文件的大小（以字节为单位）。

**示例：**

```python
import os

# 获取名为 'example.txt' 的文件大小
file_size = os.path.getsize('example.txt')

# 打印文件大小
print("Size of 'example.txt':", file_size, "bytes")
```

**输出：**

```
Size of 'example.txt': 1024 bytes
```

### 重命名文件或目录

`os.rename(src, dst)` 重命名文件或目录。

**示例：**

```python
import os

# 将 'old_name.txt' 重命名为 'new_name.txt'
os.rename('old_name.txt', 'new_name.txt')

# 确认文件重命名成功
print("'old_name.txt' has been renamed to 'new_name.txt'")
```

**输出：**

```
'old_name.txt' has been renamed to 'new_name.txt'
```

### 删除文件

`os.remove(path)` 删除指定文件。

**示例：**

```python
import os

# 删除名为 'example.txt' 的文件
os.remove('example.txt')

# 确认文件删除成功
print("File 'example.txt' removed")
```

**输出：**

```
File 'example.txt' removed
```

### 获取环境变量

`os.environ` 是一个包含所有环境变量的字典。

**示例：**

```python
import os

# 获取并打印所有环境变量
environment_variables = os.environ
print(environment_variables)

# 获取并打印特定环境变量，例如 PATH
path_variable = os.environ.get('PATH')
print("PATH environment variable:", path_variable)
```

**输出：**

```
{'PATH': '/usr/local/bin:/usr/bin:/bin', ...}
PATH environment variable: /usr/local/bin:/usr/bin:/bin
```

### 执行系统命令

`os.system(command)` 执行系统命令。

**示例：**

```python
import os

# 执行系统命令 'ls'（在Windows上可以使用 'dir'）
os.system('ls')
```

**输出：**

```
file1.txt  file2.txt  directory1
```

### 获取文件属性

`os.stat(path)` 获取文件的状态，包括大小、权限、修改时间等。

**示例：**

```python
import os

# 获取名为 'example.txt' 的文件状态
file_stat = os.stat('example.txt')

# 打印文件状态
print(file_stat)
```

**输出：**

```
os.stat_result(st_mode=33188, st_ino=7876933, st_dev=16777220, st_nlink=1, st_uid=501, st_gid=20, st_size=1024, st_atime=1625072402, st_mtime=1625072402, st_ctime=1625072402)
```

### 创建多级目录

`os.makedirs(path)` 创建多级目录。

**示例：**

```python
import os

# 创建多级目录 'parent/child'
os.makedirs('parent/child')

# 确认目录创建成功
print("Directories 'parent/child' created")
```

**输出：**

```
Directories 'parent/child' created
```

### 删除多级目录

`os.removedirs(path)` 删除多级目录（目录必须为空）。

**示例：**

```python
import os

# 删除多级目录 'parent/child'
os.removedirs('parent/child')

# 确认目录删除成功
print("Directories 'parent/child' removed")
```

**输出：**

```
Directories 'parent/child' removed
```

### 获取绝对路径

`os.path.abspath(path)` 返回路径的绝对路径。

**示例：**

```python
import os

# 获取 'example.txt' 的绝对路径
absolute_path = os.path.abspath('example.txt')

# 打印绝对路径
print("Absolute path:", absolute_path)
```

**输出：**

```
Absolute path: /home/user/projects/example.txt
```

### 分割路径

`os.path.split(path)` 将路径分割成目录和文件名。

**示例：**

```python
import os

# 分割路径 '/home/user/projects/example.txt'
directory, filename = os.path.split('/home/user/projects/example.txt')

# 打印分割结果
print("Directory:", directory)
print("Filename:", filename)
```

**输出：**

```
Directory: /home/user/projects
Filename: example.txt
```

### 获取路径的目录名

`os.path.dirname(path)` 返回路径的目录名。

**示例：**

```python
import os

# 获取路径 '/home/user/projects/example.txt' 的目录名
directory = os.path.dirname('/home/user/projects/example.txt')

# 打印目录名
print("Directory name:", directory)
```

**输出：**

```
Directory name: /home/user/projects
```

### 获取路径的文件名

`os.path.basename(path)` 返回路径的文件名。

**示例：**

```python
import os

# 获取路径 '/home/user/projects/example.txt' 的文件名
filename = os.path.basename('/home/user/projects/example.txt')

# 打印文件名
print("Filename:", filename)
```

**输出：**

```
Filename: example.txt
```

### 检查路径是否为文件

`os.path.isfile(path)` 检查路径是否为文件。

**示例：**

```python
import os

# 检查路径 'example.txt' 是否为文件
is_file = os.path.isfile('example.txt')

# 打印检查结果
print("Is 'example.txt' a file?", is_file)
```

**输出：**

```
Is 'example.txt' a file? True
```

### 检查路径是否为目录

`os.path.isdir(path)` 检查路径是否为目录。

**示例：**

```python
import os

# 检查路径 'example_directory' 是否为目录
is_directory = os.path.isdir('example_directory')

# 打印检查结果
print("Is 'example_directory' a directory?", is_directory)
```

**输出：**

```
Is 'example_directory' a directory? True
```

### 检查路径是否为绝对路径

`os.path.isabs(path)` 检查路径是否为绝对路径。

**示例：**

```python
import os

# 检查路径 '/home/user/projects' 是否为绝对路径
is_absolute = os.path.isabs('/home/user/projects')

# 打印检查结果
print("Is '/home/user/projects' an absolute path?", is_absolute)
``