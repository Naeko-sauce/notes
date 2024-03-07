元组是 Python 中的一种数据结构，类似于列表，但是元组是不可变的，意味着一旦创建就无法对其进行修改。元组使用圆括号 () 来表示，其中的元素可以是任意类型的数据，包括数字、字符串、列表、元组等。

以下是一些关于元组的常见操作：

1. 创建元组：
```python
my_tuple = (1, 2, 3, 4, 5)
```

2. 访问元组中的元素：
```python
print(my_tuple[0])  # 输出 1
```

3. 元组切片：
```python
print(my_tuple[1:4])  # 输出 (2, 3, 4)
```

4. 遍历元组：
```python
for item in my_tuple:
    print(item)
```

5. 元组拼接：
```python
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)
new_tuple = tuple1 + tuple2
print(new_tuple)  # 输出 (1, 2, 3, 4, 5, 6)
```

6. 元组解包：
```python
my_tuple = (1, 2, 3)
a, b, c = my_tuple
print(a, b, c)  # 输出 1 2 3
```

总之，元组是一种非常有用的数据结构，特别适合用于不希望被修改的数据集合。