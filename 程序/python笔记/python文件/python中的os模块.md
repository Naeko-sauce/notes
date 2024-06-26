### Python 的 `os` 模块

`os` 模块提供了一种便携的方式，使用操作系统功能，如文件和目录操作、环境变量管理等。以下是该模块的一些常用功能及其使用示例，并附有输出结果和详细描述。

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

### `os` 模块的作用

`os` 模块为 Python 提供了一个便携的接口，允许程序与操作系统交互。这包括文件和目录操作（创建、删除、重命名、列出等）、获取和设置环境变量、执行系统命令、检查文件路径等。它使得跨平台的文件和系统操作变得更加简单和一致。使用 `os` 模块，开发者可以编写更通用的代码，适用于不同的操作系统，如 Windows、Linux 和 macOS。