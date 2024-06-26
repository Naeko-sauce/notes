
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

with open('example.csv', mode='r', newline='') as file:
    csv_reader = csv.reader(file)
    for row in csv_reader:
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

data = [
    ['Name', 'Age', 'City'],
    ['Alice', '30', 'New York'],
    ['Bob', '25', 'Los Angeles'],
    ['Charlie', '35', 'Chicago']
]

with open('output.csv', mode='w', newline='') as file:
    csv_writer = csv.writer(file)
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

with open('example.csv', mode='r', newline='') as file:
    csv_reader = csv.DictReader(file)
    for row in csv_reader:
        print(row)
```

在这个例子中：
- `csv.DictReader(file)` 将 CSV 文件读取到一个字典中，字典的键是文件的第一行。

#### 使用 `DictWriter` 写入 CSV 文件

`csv.DictWriter` 将字典中的数据写入 CSV 文件。

**示例：**

```python
import csv

data = [
    {'Name': 'Alice', 'Age': 30, 'City': 'New York'},
    {'Name': 'Bob', 'Age': 25, 'City': 'Los Angeles'},
    {'Name': 'Charlie', 'Age': 35, 'City': 'Chicago'}
]

with open('output.csv', mode='w', newline='') as file:
    fieldnames = ['Name', 'Age', 'City']
    csv_writer = csv.DictWriter(file, fieldnames=fieldnames)
    
    csv_writer.writeheader()  # 写入表头
    csv_writer.writerows(data)
```

在这个例子中：
- `csv.DictWriter(file, fieldnames=fieldnames)` 创建一个写入器对象，并指定字段名。
- `csv_writer.writeheader()` 写入字段名作为第一行。
- `csv_writer.writerows(data)` 将 `data` 中的每个字典作为一行写入 CSV 文件。
