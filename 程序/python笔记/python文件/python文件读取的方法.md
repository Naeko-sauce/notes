在 Python 中，有多种方法可以用于读取文本文件。每种方法都有其特定的用途和优点。以下是所有常用的文本文件读取方法的详细说明及示例：

### 1. `read()`

`read(size=-1)` 方法读取整个文件或指定大小的内容。

#### 用法：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    content = f.read()
    print(content)
```

- **优点**：适用于读取整个文件内容。
- **缺点**：对于大文件可能会占用大量内存。

#### 示例：
假设 `example.txt` 文件内容为：
```
Hello, world!
Welcome to Python.
```
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    content = f.read()
    print(content)
```
输出：
```
Hello, world!
Welcome to Python.
```

### 2. `readline()`

`readline(size=-1)` 方法读取文件中的一行或指定大小的内容。

#### 用法：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    line = f.readline()
    print(line)
```

- **优点**：适用于逐行读取文件内容。
- **缺点**：一次只能读取一行。

#### 示例：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    line = f.readline()
    print(line)
```
输出：
```
Hello, world!
```

### 3. `readlines()`

`readlines(hint=-1)` 方法读取文件中的所有行并返回一个列表。

#### 用法：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    lines = f.readlines()
    print(lines)
```

- **优点**：适用于一次读取所有行并处理。
- **缺点**：对于大文件可能会占用大量内存。

#### 示例：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    lines = f.readlines()
    print(lines)
```
输出：
```
['Hello, world!\n', 'Welcome to Python.\n']
```

### 4. 逐行迭代

可以直接对文件对象进行迭代来逐行读取文件内容。

#### 用法：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    for line in f:
        print(line, end='')
```

- **优点**：内存友好，适用于大文件。
- **缺点**：一次只能处理一行。

#### 示例：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    for line in f:
        print(line, end='')
```
输出：
```
Hello, world!
Welcome to Python.
```

### 5. `seek()` 和 `tell()`

`seek(offset, whence)` 方法用于移动文件指针到指定位置，`tell()` 方法用于返回文件指针的当前位置。

#### 用法：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    f.seek(7)  # 移动到第7个字节
    print(f.read(5))  # 读取接下来的5个字节
    print(f.tell())  # 获取当前位置
```

- **优点**：灵活定位文件读取位置。
- **缺点**：需要手动管理文件指针。

#### 示例：
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    f.seek(7)
    print(f.read(5))
    print(f.tell())
```
输出：
```
world
12
```

### 6. 使用 `contextlib.closing`

使用 `contextlib.closing` 确保文件在异常时也会被关闭。

#### 用法：
```python
from contextlib import closing

with closing(open('example.txt', 'r', encoding='utf-8')) as f:
    content = f.read()
    print(content)
```

- **优点**：自动关闭文件，确保资源释放。
- **缺点**：适用于需要确保文件关闭的特殊情况。

#### 示例：
```python
from contextlib import closing

with closing(open('example.txt', 'r', encoding='utf-8')) as f:
    content = f.read()
    print(content)
```

### 7. `readinto()`

`readinto(buffer)` 方法将文件内容读入可变缓冲区对象中，如 `bytearray`。

#### 用法：
```python
with open('example.txt', 'rb') as f:
    buffer = bytearray(10)
    f.readinto(buffer)
    print(buffer)
```

- **优点**：适用于需要将数据读入预先分配的缓冲区。
- **缺点**：仅适用于二进制模式。

#### 示例：
```python
with open('example.txt', 'rb') as f:
    buffer = bytearray(10)
    f.readinto(buffer)
    print(buffer)
```

### 8. `mmap` 模块

`mmap` 模块将文件内容映射到内存，可以像操作数组一样操作文件内容。

#### 用法：
```python
import mmap

with open('example.txt', 'r+b') as f:
    mm = mmap.mmap(f.fileno(), 0)
    print(mm[:10])  # 读取前10个字节
    mm.close()
```

- **优点**：适用于大文件，可以部分映射。
- **缺点**：适用于特定用途，可能需要处理低级别的细节。

#### 示例：
```python
import mmap

with open('example.txt', 'r+b') as f:
    mm = mmap.mmap(f.fileno(), 0)
    print(mm[:10])
    mm.close()
```

### 总结

这些方法提供了灵活的文本文件读取方式，可以根据不同的需求选择合适的方法。对于小文件，可以使用 `read()`、`readline()`、`readlines()` 等方法；对于大文件，建议使用逐行迭代或 `mmap` 模块，以优化内存使用和性能。