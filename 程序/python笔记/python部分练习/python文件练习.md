### 代码解释与详细注释

以下是您提供的代码，它列出了当前工作目录中的所有文件，并检查每个文件的扩展名是否为 `.py`，如果是则打印文件名。下面是代码的详细解释和注释：

```python
import os
import os.path

# 获取当前工作目录的路径
path = os.getcwd()

# 列出当前工作目录中的所有文件和目录
file = os.listdir(path)
print(file)

# 遍历每个文件或目录
for fil in file:
    # 查找文件名中最后一个点的位置，通常用于分隔文件名和扩展名
    pos = fil.rfind(".")
    print(pos)
    
    # 检查从最后一个点之后的字符串（即文件扩展名）是否为 "py"
    if fil[pos + 1:] == "py":
        # 如果文件扩展名是 "py"，则打印文件名
        print(fil)
```

### 代码运行流程
1. **导入模块**:
   ```python
   import os
   import os.path
   ```
   这两行代码导入了 `os` 模块及其子模块 `os.path`，用于进行操作系统相关的操作和路径操作。

2. **获取当前工作目录路径**:
   ```python
   path = os.getcwd()
   ```
   `os.getcwd()` 函数返回当前工作的目录路径，并将其赋值给变量 `path`。

3. **列出当前目录中的所有文件和目录**:
   ```python
   file = os.listdir(path)
   print(file)
   ```
   `os.listdir(path)` 函数返回指定路径 `path` 下的所有文件和目录的列表，并将其赋值给变量 `file`。`print(file)` 将该列表打印出来。

4. **遍历每个文件或目录**:
   ```python
   for fil in file:
   ```
   这行代码使用 `for` 循环遍历 `file` 列表中的每个元素，即当前目录中的每个文件或目录。

5. **查找文件名中最后一个点的位置**:
   ```python
   pos = fil.rfind(".")
   print(pos)
   ```
   `fil.rfind(".")` 函数查找文件名 `fil` 中最后一个 `.` 字符的位置，并返回该位置的索引。如果文件名中没有 `.`，则返回 `-1`。`print(pos)` 将该索引位置打印出来。

6. **检查文件扩展名是否为 "py"**:
   ```python
   if fil[pos + 1:] == "py":
       print(fil)
   ```
   `fil[pos + 1:]` 从文件名中提取最后一个 `.` 之后的部分，即文件扩展名。如果扩展名为 `"py"`，则打印该文件名 `fil`。

### 示例输出
假设当前目录中有以下文件：
- `example.txt`
- `script.py`
- `README.md`

输出将如下所示：
```
['example.txt', 'script.py', 'README.md']
7
-1
10
script.py
7
```

### 注意事项
- `os.listdir()` 返回的列表包含当前目录中的所有文件和目录名。
- `fil.rfind(".")` 返回最后一个 `.` 的索引，如果没有找到 `.` 则返回 `-1`，这可能会导致 `fil[pos + 1:]` 返回整个文件名。这种情况下应检查 `pos` 是否大于 `0` 以避免错误。

这段代码主要用于列出当前目录中的所有文件，并识别并打印 `.py` 扩展名的文件。