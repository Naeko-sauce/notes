### Python 的 `csv` 模块

`csv` 模块用于读取和写入 CSV（逗号分隔值）文件。它提供了易于使用的功能来解析和创建 CSV 文件。以下是主要组件和使用示例。

#### 导入 `csv` 模块

```python
import csv
```

#### 读取 CSV 文件

要读取 CSV 文件，可以使用 `csv.reader` 函数。该函数返回一个对象，该对象逐行迭代 CSV 文件。

**示例：**

```python
import csv

# 以读取模式 ('r') 打开CSV文件，并确保以默认的换行符读取文件
with open('example.csv', mode='r', newline='') as file:
    # 创建一个CSV读取器对象
    csv_reader = csv.reader(file)
    
    # 遍历CSV文件中的每一行
    for row in csv_reader:
        # 打印每一行内容，每行都是一个包含字符串的列表
        print(row)
```

在这个例子中：
- `open('example.csv', mode='r', newline='')` 以读取模式打开 CSV 文件。
- `csv.reader(file)` 创建一个读取器对象，该对象将逐行迭代给定文件。
- `for row in csv_reader` 循环遍历 CSV 文件中的每一行，每一行都作为字符串列表返回。

#### 写入 CSV 文件

要写入 CSV 文件，可以使用 `csv.writer` 函数。该函数返回一个用于写入 CSV 文件的对象。

**示例：**

```python
import csv

# 要写入CSV文件的数据，每个子列表代表CSV文件中的一行
data = [
    ['Name', 'Age', 'City'],
    ['Alice', '30', 'New York'],
    ['Bob', '25', 'Los Angeles'],
    ['Charlie', '35', 'Chicago']
]

# 以写入模式 ('w') 打开CSV文件，并确保以默认的换行符写入文件
with open('output.csv', mode='w', newline='') as file:
    # 创建一个CSV写入器对象
    csv_writer = csv.writer(file)
    
    # 写入多行数据到CSV文件中
    csv_writer.writerows(data)
```

在这个例子中：
- `open('output.csv', mode='w', newline='')` 以写入模式打开 CSV 文件。
- `csv.writer(file)` 创建一个写入器对象。
- `csv_writer.writerows(data)` 写入多行到 CSV 文件中。`data` 中的每个元素都是一个代表一行的列表。

#### 使用 `DictReader` 读取 CSV 文件

`csv.DictReader` 将 CSV 文件读取到字典中。每一行都是一个字典，键是列名。

**示例：**

```python
import csv

# 以读取模式 ('r') 打开CSV文件，并确保以默认的换行符读取文件
with open('example.csv', mode='r', newline='') as file:
    # 创建一个CSV字典读取器对象
    csv_reader = csv.DictReader(file)
    
    # 遍历CSV文件中的每一行
    for row in csv_reader:
        # 打印每一行内容，每行都是一个字典，键为列名，值为相应的单元格内容
        print(row)
```

在这个例子中：
- `csv.DictReader(file)` 将 CSV 文件读取到一个字典中，字典的键是文件的第一行。

#### 使用 `DictWriter` 写入 CSV 文件

`csv.DictWriter` 将字典中的数据写入 CSV 文件。

**示例：**

```python
import csv

# 要写入CSV文件的数据，每个字典代表CSV文件中的一行
data = [
    {'Name': 'Alice', 'Age': 30, 'City': 'New York'},
    {'Name': 'Bob', 'Age': 25, 'City': 'Los Angeles'},
    {'Name': 'Charlie', 'Age': 35, 'City': 'Chicago'}
]

# 以写入模式 ('w') 打开CSV文件，并确保以默认的换行符写入文件
with open('output.csv', mode='w', newline='') as file:
    # 定义CSV文件的列名
    fieldnames = ['Name', 'Age', 'City']
    
    # 创建一个CSV字典写入器对象，并指定字段名
    csv_writer = csv.DictWriter(file, fieldnames=fieldnames)
    
    # 写入表头（列名）
    csv_writer.writeheader()
    
    # 写入多行数据到CSV文件中
    csv_writer.writerows(data)
```

在这个例子中：
- `csv.DictWriter(file, fieldnames=fieldnames)` 创建一个写入器对象，并指定字段名。
- `csv_writer.writeheader()` 写入字段名作为第一行。
- `csv_writer.writerows(data)` 将 `data` 中的每个字典作为一行写入 CSV 文件。