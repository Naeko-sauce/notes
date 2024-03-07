Python 中对列表进行排序有多种方法，包括使用 sort ()方法和 sorted ()函数。下面是对列表进行排序的所有方法：

1. 使用 sort ()方法对列表进行原地排序，即修改原始列表：
```python
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
my_list.sort()
print(my_list)  # 输出 [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
```

2. 使用 sorted ()函数对列表进行排序，生成一个新的已排序列表，不改变原始列表：
```python
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
sorted_list = sorted(my_list)
print(sorted_list)  # 输出 [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
```

3. 使用 key 参数对列表进行排序，可以指定一个函数来作为排序的关键字：
```python
my_list = ["apple", "Orange", "banana", "Peach"]
sorted_list = sorted(my_list, key=str.lower)
print(sorted_list)  # 输出 ['apple', 'banana', 'Orange', 'Peach']
```

4. 使用 reverse 参数对列表进行降序排序：
```python
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
my_list.sort(reverse=True)
print(my_list)  # 输出 [9, 6, 5, 5, 5, 4, 3, 3, 2, 1, 1]
```

5. 使用自定义函数对列表进行排序：
```python
my_list = [(1, 'b'), (3, 'a'), (2, 'c')]
sorted_list = sorted(my_list, key=lambda x: x[1])
print(sorted_list)  # 输出 [(3, 'a'), (1, 'b'), (2, 'c')]
```

这些方法提供了灵活的方式来对列表进行排序，可以根据具体需求选择合适的方法。